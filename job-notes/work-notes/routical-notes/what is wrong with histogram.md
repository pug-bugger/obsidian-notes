The black dots match unstyled SVG circles: default SVG `fill` is black, and the lavender fill / purple stroke only come from CSS. Panning updates `cx`/`cy`, which forces a repaint, so the same circles suddenly look correct.

---

## The driver-change dots (the bug you described)

Circles are created in `drawRectangles` with **class and position only**. Fill and stroke are not set as SVG attributes:

```257:267:force-app/main/default/consoleComponents/history/lwc/histogramTachoGraph/histogramTachoGraph.js
    this.driverChangeElements = this.driverChangeElements
      .enter()
      .append("circle")
      .attr("class", "driver-changed")
      .attr("r", 6)
      .attr("pointer-events", "none")
      .merge(this.driverChangeElements);

    this.driverChangeElements
      .attr("cx", (d) => this.x(d.from))
      .attr("cy", this.height / 2);
```

Color is CSS-only, and the variables have **no hex fallback**:

```36:40:force-app/main/default/consoleComponents/history/lwc/histogramTachoGraph/histogramTachoGraph.css
circle.driver-changed {
  fill: var(--rtcl-global-light-lavender);
  stroke: var(--rtcl-global-purple);
  stroke-width: 2;
}
```

Status **rects** do not have this problem because JS also sets `fill`:

```237:246:force-app/main/default/consoleComponents/history/lwc/histogramTachoGraph/histogramTachoGraph.js
    this.rectElements
      .attr("class", (d) => {
        const status = this.normalizeStatus(d.status);
        return `status-rect rect clickable ${status}`;
      })
      .attr("fill", (d) => this.getStatusFill(d.status))
      .attr("x", (d) => this.x(d.from))
```

If CSS has not applied yet, a rect still has a presentation `fill`. A circle has nothing, so the browser paints **black, no border**. After you pan, `zoomHandler` → `drawChart` → `attr("cx")` / `attr("cy")`, Chrome/Safari re-paints, and you get lavender fill `#95a0f3` plus purple stroke `#6a1b9a`.

This shows up when there are **many** driver changes because first load draws **every** circle in the full time domain (`getVisibleData()` only filters by the current x-domain, which starts as the whole range). Typical stack:

1. D3 appends many circles in one frame.
2. LWC scoped CSS (`lwc:dom="manual"`) and inherited `var(--rtcl-…)` often resolve **after** that first SVG paint.
3. Invalid/unresolved `var()` → CSS `fill` is ignored → SVG initial fill is black.
4. If the next automatic redraw sets the same `cx`/`cy`, the browser may skip a paint. A real pan changes geometry, so colors appear.

`tachoHistoryRow` avoids this by setting circle fill in JS: `.attr("fill", (d) => d.color)`.

**Fix (when you want it implemented):** set fill/stroke on enter, with fallbacks, same as rects:

```javascript
.attr("fill", "var(--rtcl-global-light-lavender, #95a0f3)")
.attr("stroke", "var(--rtcl-global-purple, #6a1b9a)")
.attr("stroke-width", 2)
```

and the same fallbacks in CSS. Presentation attributes still paint even if scoped CSS or custom properties miss the first frame.

---

## Tacho graph — other drawing gaps

**1. First domain is tacho data, not the main graph**

```142:147:force-app/main/default/consoleComponents/history/lwc/histogramTachoGraph/histogramTachoGraph.js
    this.x = this.d3
      .scaleTime()
      .domain(
        this.d3.extent([this.tachoData?.[0]?.from, this.tachoData?.at(-1)?.to])
      )
      .range([0, this.width]);
```

Until `zoomHandler` copies the main graph domain, tacho bars/dots can be stretched or shifted vs fuel/speed. Empty tacho data makes the domain `[undefined, undefined]`.

**2. No clustering**

Task icons cluster when they overlap. Driver dots do not (`r = 6` always). Many changes in a short window stack into one dark blob — worse while they are still black.

**3. Dots at the plot edge are clipped**

`cx = this.x(d.from)` with `r = 6`. A change at the start/end of the window is half outside the SVG. The tacho row is only `1.5rem`, so a missed style + clipping looks like a tiny black speck.

**4. `driver-available` has no CSS class**

JS sets that fill, but `histogramTachoGraph.css` only styles `rect.rest|drive|work`. If the JS `var()` fails the same way, those segments can flash default black.

**5. Visible-data join**

`getVisibleData()` keeps `driverChanged` items even when bar width is `0`, which is correct. `getItemKey` is `` `${d.from}-${d.to}` ``. Duplicate `from` values are already dropped in `parseTachoData`, so keys are fine. Zero-width driver-change rects still get a circle; that is intentional.

---

## Task graph — wrong until you move the graph

This is the same “broken until pan” pattern, for a different reason.

The getter maps tasks to `date` / `startdate` / `type`, but scaling still reads Salesforce field names that are not on those objects:

```73:86:force-app/main/default/consoleComponents/history/lwc/histogramTaskGraph/histogramTaskGraph.js
  createScaling() {
    const d3 = this.d3;
    this.x = d3
      .scaleTime()
      .domain(
        d3.extent([
          new Date(
            this.taskData[0]?.Task_Start_Time__c ??
              this.taskData[0]?.Task_Finish_Time__c
          ),
          new Date(this.taskData.at(-1)?.Task_Finish_Time__c)
        ])
      );
  }
```

`new Date(undefined)` is `Invalid Date`, so icons can sit at `left: NaNpx` or a nonsense scale. Pan runs `zoomHandler`, which overwrites the domain from the main graph (`detail.from` / `detail.to`) and they snap into place.

`zoomHandler` also falls back to `this.tachoData`, which **does not exist** on this component. That only blows up if `detail.from` is missing.

`drawChart` never rebuilds the domain — only `range`. After tasks load, positions stay wrong until a zoom/pan.

---

## Main graph — places lines/overlays can miss

**Lines depend on CSS variables as `stroke` attributes** (`percentItems` colors like `var(--rtcl-primary)`). Same first-paint risk as the dots, but each series is a single `path`, so it is rarer. The Debug series is hardcoded `#101010` and always looks almost black.

**`clip-path: url(#myClip)`** is a document-global SVG URL. Inside LWC shadow this often fails on first paint (Safari especially), so lines can overflow or vanish, then look fine after a redraw.

**Initial country flags are forced off:**

```844:851:force-app/main/default/consoleComponents/history/lwc/histogramMainGraph/histogramMainGraph.js
    this.parsedCrossings = (this.countryCrossings || []).map((cc) => {
      return {
        ...cc,
        style: `
        --padding: ${drawX(cc[DATE])}px;
        --show-cards: ${"none"};
        `,
      };
    });
```

They only appear after a zoom event computes spacing. Height-resize redraws skip this block entirely.

**X-axis is drawn 100ms later** on a normal `drawChart` (not `keepZoom`). First axis tick pass can be missing or in the wrong place.

**Empty telematics series** (`d3.max` → `undefined`) produce a broken y-domain; that line’s `d` becomes `NaN` and SVG stops drawing the rest of the path.

**Width from `style("width")`:** if D3 ever returns `"100%"` instead of `"800px"`, `Number(...)` is `NaN` and the whole plot collapses until resize/pan.

**Split mode:** overlay zoom/range is not recreated (`_overlaysReady` stays true) while plot SVGs are. Hover lines are rebuilt; a stale zoom node can desync split rows until you pan.

**`drawChart` waits `setTimeout(0)`** except during live height resize. First layout can run before the container has its final size (`width <= 0` is only guarded in the tacho graph, not here).

---

## Wrapper timing (why first paint is the dangerous one)

```51:70:force-app/main/default/consoleComponents/history/lwc/histogramGraphWrapper/histogramGraphWrapper.html
    <div class="graphs" lwc:if={data}>
      ...
        <c-histogram-tacho-graph tacho-data={data.tacho}></c-histogram-tacho-graph>
      ...
        <c-histogram-main-graph ...>
```

Tacho mounts and draws as soon as `data` exists. The main graph gets data **100ms later**, then ends `drawChart` with `zoomIdentity`, which should call `tacho.zoomHandler`. If that zoom maps dots to the **same pixels**, geometry does not change and black fills can stick until a real pan.

Height resize redraws tacho via `tacho.drawChart()` (position only, same CSS gap). Truck change calls `recreateChart()`, which wipes and re-appends every circle — same first-paint hole, worse with many driver changes.

---

## What to change first

| Priority | Where | Problem | Direction |
|---|---|---|---|
| High | Tacho circles | Black until pan | Set `fill` / `stroke` / `stroke-width` in D3, with hex fallbacks |
| High | Tacho CSS | `var()` with no fallback | Add `#95a0f3` / `#6a1b9a` (and `driver-available` rect rule) |
| High | Task `createScaling` | Reads fields that were mapped away | Domain from `startdate`/`date`, or from main graph |
| Medium | Tacho + task initial domain | Not synced until zoom | Same domain as main graph on first draw |
| Medium | Many overlapping driver dots | Unreadable blob | Cluster like the task graph, or cap min pixel gap |
| Medium | Main `url(#myClip)` | Clip can miss in shadow DOM | Unique clip id, or clip in CSS |
| Low | Country `--show-cards: none` | Flags hidden until move | Use the same overlap logic as `zoomGraph` |

The black dots are not a D3 join bug at `exit().remove()`. The join is fine. The circles are painted with SVG defaults because color lives only in CSS, and that CSS often misses the first paint when many nodes are inserted at once.

I am in Ask mode, so I cannot apply the fix here. Switch to Agent mode if you want this patched in the tacho graph first.