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
### Differences
- [x] replace trip status display order (~0.5)
- [x] section headers always on top (~5)
- [x] redirect to selected section list top
- [x] add "Expand all Trips" switch button (~4)
- [ ] expand all map display updates
- [x] selected trip/task row hover style
- [x] hide/show task list on click on trip row (~4)
- [x] implement "Reorder Upcoming Trips" switch button in Upcoming Trips section (~10)
- [x] confirmation modal card to reorder Upcoming Trips (~3)
- [x] display tasks next to trip below (~15)
- [x] task details column (~15)
- [x] zoom to selected task mark point (~10)
- [ ] restrictions toggle fn in task details window
- [ ] storage expanded trip ids, remember in current session, helper field expandedTripIds and add and remove methods.
- [ ] task progress style update
- [ ] task row details parameters in custom settings
### To-do
- [x] Detect differences and list them in Differences section
- [x] Estimate each step time before start do anything