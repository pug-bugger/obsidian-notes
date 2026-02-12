---
title: Current Trip Display
date: 2025-11-05
tags:
  - DC
---
SF task: [Tripų skaidymas, kad būtų matomi taskai iš karto ir kad nereikėtų papildomo clic](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKsgL2AT/view)
Canvas: [[trip-display cmp structure.canvas|trip-display cmp structure]]

### Notes
Canvas contains current/old design version and new from figma.
Experimenting with this noting structure.
- [ ] scroll smoothy
### Differences
- [x] replace trip status display order (~0.5)
- [x] section headers always on top (~5)
- [x] redirect to selected section list top
- [x] add "Expand all Trips" switch button (~4)
- [x] expand all map display updates
- [x] selected trip/task row hover style
- [x] hide/show task list on click on trip row (~4)
- [x] implement "Reorder Upcoming Trips" switch button in Upcoming Trips section (~10)
- [x] confirmation modal card to reorder Upcoming Trips (~3)
- [x] display tasks next to trip below (~15)
- [x] task details column (~15)
- [x] zoom to selected task mark point (~10)
- [x] restrictions toggle fn in task details window
- [ ] storage expanded trip ids, remember in current session, helper field expandedTripIds and add and remove methods.
- [x] task progress style update
- [x] task row details parameters in custom settings

- [x] scroll to current trip circle button
- [x] link truck from refuel plan
- [x] histogram icon in finish trip/task row
- [x] truck trip icon click handler
- [x] display edited trip view after finish editing
- [x] trip and task name linked to salesforce record page
- [x] update design according to new figma
### To-do
- [x] Detect differences and list them in Differences section
- [x] Estimate each step time before start do anything
- [x] Note QA comments #1

### QA Comments #1
- [x] When no Finished/Current trips, sections headers should stay
- [x] Scroll to selected section of current and upcomming trips hides part of first trip row
- [x] On reordering mode turn of selection fn
- [x] According to the figma (frame 1910), task row without padding in left side ==(discuss)==
- [x] After cancel trip edit all trips are collapsed, but task stay selected, fix
- [x] Confirmation question ==discuss== (CANCELED)
- [x] Accepted task are editable, fix
- [x] On top of the all trips section Upcomming trips are not visible ==(discuss)==
- [x] Trip selection discuss (to select another expanded trip, first collapse and then select/expand again to select - current implementation) ==(discuss)== (CANCELED)

#### task display
