
**Today Plans**

1. finish milestone post completed triggers (stakes and booking status)
Exploring

**Now:**



#### 01-29
##### Task: [Trigeris ant Service Exchange Rate'ams nustatyti](https://bcline.lightning.force.com/lightning/r/Task__c/a0NSZ00000AgMPl2AN/view)
- [x] Create cmp variable to identify trip recorf type is changed.   [completion:: 2025-01-30]
On service after update event to invoiceRoolup calculate add `&& cmp.hasRecordTypeChanged`

##### Task: [Invoice Generavimas iš Planned Income](https://bcline.lightning.force.com/lightning/r/Task__c/a0NSZ00000AgIFh2AN/view)
- [x] CR_  fix small comments @completed(2025-01-29T15:34:33+02:00)   [completion:: 2025-01-30]
- empty list check in service layer, not in domain.
- don't call schema in for loop.

##### Task: [Trigeris, kai Quote tampa Approved ir susikuria Booking](https://bcline.lightning.force.com/lightning/r/Task__c/a0NSZ000009XZ9t2AG/view)
- [x] code review fixes   [completion:: 2025-01-30]
- add sequence parameter in createPointFromPointTypeAndQuote method to pass sequence value according to trip record type and point sequence in this trip.
- Gearset does not pass because of I try to change `Service__c.Service_Type__c` picklist from local custom picklist to global `Service_Type`. Try to fix this by change it in partial manually (created global value set according to global picklist in sandbox and refresh the Gearset by push cahnges to PR).

---
#### 01-30
##### Task: [Spot Quote mapinimas](https://bcline.lightning.force.com/lightning/r/a0NSZ000009XYYn2AO/view "Spot Quote mapinimas")
- fixed test class method. Set value gearset still throws error, can't change value.

##### Task: [Trigeris ant Service Exchange Rate'ams nustatyti](https://bcline.lightning.force.com/lightning/r/a0NSZ00000AgMPl2AN/view "Trigeris ant Service Exchange Rate'ams nustatyti")
- [x] Fix code review   [completion:: 2025-01-30]
- forget to deploy changes 

##### Task: [Reikia sukurti Milestone Post Complete klases](https://bcline.lightning.force.com/lightning/r/a0NSZ00000AgU3y2AF/view "Reikia sukurti Milestone Post Complete klases")
- Test Case Trigger category don't have Stake subcategory.
- Writing trigger, testing and fixing.
- Error during create/update stake for thip with two bookings (after insert loop limit)
  Fixing: added 
- Writing test class. Additionally writing fflib method doc for myself to use in future.
- Edit test class name and have problem with deploying it, fixing manually in sandbox.
- I don't know why, but for some reason test class don't see mocks, can't figure out why 😡
  Fixing: nope, waiting for Vilius help.
- Updating milestone postcompleted DC_InformCustomerSeaFCLBookingUpdates class to update booking status. Done.
- Waiting for Vilius help to found out test class error reason.

#### 01-30
##### Task: Code Review
* Review Routical task.
* Replay to comments in my code.
##### Task: [Spot Quote mapinimas](https://bcline.lightning.force.com/lightning/r/a0NSZ000009XYYn2AO/view "https://bcline.lightning.force.com/lightning/r/a0NSZ000009XYYn2AO/view")
* count cork time on this task to fix gearset error with global picklist edit issue.
##### Task: [Invoice Generavimas iš Planned Income](https://bcline.lightning.force.com/lightning/r/a0NSZ00000AgIFh2AN/view "Invoice Generavimas iš Planned Income")
* added check to don't pass invoiced planned incomes by throwing error.
  code checks if selected planned income payer stake have Actual_Service__c field filled.
##### **Daily Stand-Up**
* Yesterday. Worked on milestone post completed, had issues with writing tests. Finished trigger booking status new functionality subtask. Not wrote test case for booking status yet.
* Today. Created PR to fix spot quote PR gearset error. Fixed all code review and testing failed tasks.
##### Task: [Nuotraukų zoominimas](https://bcline.lightning.force.com/lightning/r/a0NSZ000005H31p2AC/view "Nuotraukų zoominimas")
* Fixing testing failed subtasks.
	* added resize action after rotate image
	* changed event name to close preview component only on close button click event.
* Try to add validation for url or find some method or event what will throw error on wrong file type and handle that cases.
* Find open-failed event method, use it to stop loading and display default file "none" icon then image has not opened. Left close button and navigation buttons active to handle open failed cases.
* Display None file icon and text "File type not supported" then file is not the image.
* Deployed changes to bitbucket.
##### Task: [Reikia sukurti Milestone Post Complete klases](https://bcline.lightning.force.com/lightning/r/a0NSZ00000AgU3y2AF/view "Reikia sukurti Milestone Post Complete klases")
* Found the reason why test not working, it's because in implementation class I initialized selector by wrong way. Insert of Trip__c.SObject pass TripSelector.class, like in test class.
#### 02-03
##### Task: Code review
* nothing to code reviewing
##### Task: [Spot Quote mapinimas](https://bcline.lightning.force.com/lightning/r/a0NSZ000009XYYn2AO/view "Spot Quote mapinimas")
* Fixing testing failed subtask, for some reason validation turned off and trash button don't works properly, don't tested.
* Fixed validation functionality (just forget return the required code after testing in sandbox)
* Fixed handleDelete method, changed currentRouteNumberNewQuote variable to currentRouteNumberFullRoute, for some reason here was wrong variable.
* Fixed Quote service inplementation on quote status approved status change. Added price and service record type according to the filled Cost_Price__c or Sales_Price__c in quote line item record.
* Fixing [Loading/Unloading Place neturi assigned Points approvinus Quote](https://bcline.lightning.force.com/lightning/r/a1RSZ000001WZBl2AO/view), ask TL how to fix this and that logic shold be implemented in this case.
##### Task: [Trigeris ant Service Exchange Rate'ams nustatyti](https://bcline.lightning.force.com/lightning/r/Task__c/a0NSZ00000AgMPl2AN/view)
* checking development bug, ask TL should I ask for new functionality and add max time.
* TL approved request of change development bug to new functionality. Estimated time to 2h, including testing and write test case.
* Wrote before update logic to fill left null currency field. Added trigger before update listener. Wrote tests and edit test case.
##### Task: [Spot Quote mapinimas](https://bcline.lightning.force.com/lightning/r/a0NSZ000009XYYn2AO/view "Spot Quote mapinimas")
* Started fixing new development bugs.
* Required fields left empty in collapsed section, then validation don't see these fields. 
  Fixing: Added method in dcQuoteInitializers.js to check if all fields in array are filled and returns true or false.
* Started fixing fields display solution. Discussed with TL need I to fix that and how. After a couple of attempts, found the reason and solution.
* Fixed date display value bug.
* Fixing buttons and maps components display bugs and testing validation functionality.
#### 02-04
##### Task: [Trigeris, kai Quote tampa Approved ir susikuria Booking](https://bcline.lightning.force.com/lightning/r/a0NSZ000009XZ9t2AG/view)
* Fixed PR merge conflict.
* Fixed gearset error.
##### Task: [Spot Quote mapinimas](https://bcline.lightning.force.com/lightning/r/a0NSZ000009XYYn2AO/view)
* After yesterday I will continue to fix inputs display fixing in rates section (next page) and fixing google input component display bug.
* Fixed and tested:
  * Fixed date display value.
  * Fixed and tested google map value display.
  * check entire gazelle component and added validation for collapsed required fields also, and quantity field 0 value handle.
  * Fixed default currentRouteNumber value set.
* Tested entire spot quote functionality, emails sent successfully, records with right values and relationships are created, email activity created.
##### Task: [Trigeris ant Service Exchange Rate'ams nustatyti](https://bcline.lightning.force.com/lightning/r/a0NSZ00000AgMPl2AN/view)
* Fixed merge conflict.
* Fixed by remove service trigger tests from services layer test class.
##### Task: [Code Review](https://bcline.lightning.force.com/lightning/r/a0N5J000004r4DaUAI/view)
* Code reviewing.
* Fixing gearset errors of [Invoice Generavimas iš Planned Income](https://bcline.lightning.force.com/lightning/r/a0NSZ00000AgIFh2AN/view) task. added read permission for service_type field and some places with service type.
##### Task: [Nuotraukų zoominimas](https://bcline.lightning.force.com/lightning/r/a0NSZ000005H31p2AC/view "Nuotraukų zoominimas")
* change close button background color to transparent and hover color to blue primary (--console-cur-main-bg)
* Add listener on Escape button to close viewer.
* Try to add event listener on double click to reset zoom. Use canvas-double-click but need to fix first click prevent.
* Finished subtasks. Added convas-click event handler to prevent zoom in execution
##### Task: [Trigeris, kai Quote tampa Approved ir susikuria Booking](https://bcline.lightning.force.com/lightning/r/a0NSZ000009XZ9t2AG/view)
* Try to figure out why bookings etd and eta with wrong values. I think something wrong with trip trigger. Problem was in my impl class, swapped etd with eta.
* removed related service dynamic list from booking flexi page.
#### 02-05
##### Task: [(Bug) Truckų scrollas nepatogiai veikia kai dragini su pele](https://bcline.lightning.force.com/lightning/r/a0NSZ00000B4Jgr2AF/view "(Bug) Truckų scrollas nepatogiai veikia kai dragini su pele")
* Started but task. Try to figure out, why it stops scrolling only then scrolling by dragging and cursor goes out to right side, but in messenger works good.
* explore scrollbar component, check event prevent reason
* Scrollbar have .scrollbar-thumb-area and visible then dragging the thumb. for some reason for navigation it not works.
* Fixed by cahnge navigation bar css position to static.
* Created test case
##### Task: [Trigeris, kai Quote tampa Approved ir susikuria Booking](https://bcline.lightning.force.com/lightning/r/a0NSZ000009XZ9t2AG/view)
* Discussed with TL how functionality should work.
* Fixing trigger to map points planned_date__c to booking etd and eta.
* Booking trigger sort points and get point with null planned date field value.
* Fixing merge conflict and test classes
##### Task: [❓trcuk dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view "❓trcuk dalies draginimas pele")
- Explained to me the routical task.
- Create container with moveable side to change container width.
    - [x] Container with moveable side by dragging.
    - [ ] Save width in cache.
    - [x] max/min width range.
* Update truck row layout
	- [x] update paddings/gaps between items.
	- [ ] don't display items if don't fit.
- Update ToolWrapper component
	- [ ] ~~updated~~
- Add speed item
	- [ ] added
- Some questions:
  - pločio keitimas yra dėl to kad paslėpti žemėlapį ar kad atvaizduoti sau tiek item'ų kiek reikia? (nuo šito priklauso ar pagal rem ar pagal procentus sidebar width nustatinėti)
- Wrote functionality to resize sidebar. set max and min container width. Working on mouse top event and make design properly.
#### 02-06
##### Task: [❓trcuk dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view)
* Added `user-select: none` to prevent text selection during sidebar resizing.
* Added event listener to stop resizing then mouse cursor is entered to map wrapper.
* Working on styling of truck row items.
* Changed truck row cards display to flex, removed @media functionality to always display items text.
* TODO
  - [ ] add speed item card
  - [ ] hide item then no pace. (in progress)
  - [ ] localStorage
- No more need to implement same functionality to toolwrapper.
- Working on items hiding
##### Task: [(Patch) Update'ai Spot Quote'ui (reikalinga iki 2025-02-06)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BePNx2AN/view "(Patch) Update'ai Spot Quote'ui (reikalinga iki 2025-02-06)")
* fixing partial spot quote
  * [x] free days picklist combined display
  * [x] hide where from and to map input fields
  * [x] price valid default value
  * [x] convert currency
  * [x] replace dot by comma
  * [x] in final page display new created quote id
* In new sandbox deployed partial code and fixed a, b, e and f points.
* c - set default value, additionally agreed how should be displayed price valid in summary page.
* d - fixed total calculated values, adding dynamic exchange rate according to selected currency.
#### 02-07
##### Task: [(Patch) Update'ai Spot Quote'ui (reikalinga iki 2025-02-06)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BePNx2AN/view "(Patch) Update'ai Spot Quote'ui (reikalinga iki 2025-02-06)")
* Created PR to partial, deployed a, b, e and f.
* Working on total calculations with todays exchange rate. Finished with spot quote, but 
* Finished all task initial points + some changes from chat discussion. 
* I guess this is not dev bug, but it is new functionality maybe. (patched task)
* Deployed permissions set for Service__c.Service_Type field.
* Writing logic for stake relationships on quote approve.
Gal jeigu cost arba price quantity yra 0 tada tiesiog nekurti quote line item?
#### 02-10
##### Task: [(Patch) Update'ai Spot Quote'ui (reikalinga iki 2025-02-07)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BePNx2AN/view "(Patch)  Update'ai Spot Quote'ui (reikalinga iki 2025-02-07)")
* Quote Spot part. Changed sequence in DC_Application and quote line item has related with stake properly.
* Quote trigger on status change to approved. Updating stake domain method to relate stake to service in one method with booking.
* Added default payer lookup field fill value from customer lookup field in first page.
* Writing unit tests and test cases.
***lunch***
* Wrote test case, deployed last changes and fixed PR gearset status.
##### Task: [(Patch) trigeris prie quote](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BmKCe2AN/view "(Patch)  trigeris prie quote")
* Created quote line item trigger.
* Created QLI trigger handler, CW, TEST Classes. Wrote basic trigger handler logic to get quote line item ids and pass them to quote line item service layer class.
* Created service layer files. 
* Created Selector class to select quote line item records with required fields by ids.
* Writing service impl class logic, wrote method to select all quote line items by set of id and manipulate quote line item records (!! not moved manipulation code to domain layer)
* Writing test class 
*Test functionality in sandbox, write unit tests and test case.*
#### 02-11
##### Task: [(Patch) trigeris prie quote](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BmKCe2AN/view)
* Testing functionality in sandbox.
* Wrote small test and fixing small errors.
* Tested and fixed last things, wrote simple tests and created PR to partial
##### Task: [(Patch) Quote Email Template](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BpK6P2AV/view "(Patch) Quote Email Template")
* Writing email template for text from document.
* Fixing service generate fn.
* Fixing PM commented things in slack.
* Deployed last changes to spot-quote-partial branch.
##### Task: [❓trcuk dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view "❓trcuk dalies draginimas pele")
* according to last notes about this task remains to:
	* ~~hide wrapped items~~
	* ~~save sets to local storage~~ 
	* ~~add speed item card~~
* Discussed about task updates
* Updates:
	* items can be consist of 2 or 3 parts (icon - number - icon). After resizing sidebar this items width will reduce step by step, first right icon, then number ant only then entire item.
	* button to minimize sidebar.
	* increase text area width for license plate.
* to be continued...
##### Task: [(Patch) STT-16461 file rotated as in desktop console](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BqJg92AF/view "(Patch) STT-16461 file rotated as in desktop console")
* Hidden close X button and left the Done button to close in mobile console.
##### Task: [❓trcuk dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view "❓trcuk dalies draginimas pele")
* Added appearing button on sidebar border on hover and on click listener, writing logic to minimize sidebar.
#### 02-12
##### Task: [Truck dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view "❓trcuk dalies draginimas pele")
* Updates resizer design
* Writing functionality to wrap the sidebar by clicking on the minimizer button.
* Testing and fixing small things. Adding listeners and remove them on control events and resizer usability.
* Try to separate js controller of resizing functionality. Adding speed item to truck row.
* Created speed card and display live_speed__c value. Added permission set and custom permission to display item.
##### 1-on-1
* Use notes to better control the task flow and debug
##### Task: [Truck dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view)
* Writing local storage functionality (use consoleLocalStorageWrapper)
* Something wrong with default set from local storage, fixing and testing
#### 02-13
##### Task: [Truck dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view)
* Wrote local storage functionality, on load component width and collapsing data sets by default.
* Discussed about code refactoring, decided to separate functionality to new component to make it reusable and control in one place and less dependency from children component.
* Created new resizerWrapper component and use to resize sidebar.
* Adding extra area place to be able to resize to right side and end resizing on left that area.
* **stand-up**
* Fixed components fn and design after replaced the code to the new component.
* Added extra area of resizing listener, modifying design of collapse button.
* Fixing scrollbar and resizer conflict. Fixed by adding z-index: 1 dynamically on mousedown event.
* Working on truck label and items aligning and flex wight calculation. Almost find the solution.
#### 02-14
##### Task: [(Hotfix) Nuotraukų zoominimas mobile konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BxQWP2A3/view "(Hotfix) Nuotraukų zoominimas mobile konsolėje")
* setup sandbox, login from mobile, testing
* Fixed new functionality and close "Done" button in messenger, fixing and testing image swipe.
* Fixed zoom and navigation gestures conflict. Navigation works only on the image is zoomed out.
* Deployed to sprint-26-hotfix-1 branch.
* Wrote test cases.
##### Task:  [Truck dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view "Truck dalies draginimas pele")
* Deploying all changes to refreshed sandbox.
* Done with truck row aligning to right side of sidebar.
* Fixed scrollbar bug from production.
* Adding fuel sorting logic to sort each groups of sorted lists. Waiting for answer from Paulius.
* remains to add bubble and separate items. (not big deal)
#### 02-17
##### Task: [Truck dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view "Truck dalies draginimas pele")
* Asked about task. 
* **Stashed last changes** and switch to hotfix !
##### Task: [(Hotfix) Nuotraukų zoominimas mobile konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BxQWP2A3/view "(Hotfix) Nuotraukų zoominimas mobile konsolėje")
* Fixed code review comment (replace class selector by ref)
* Tested on the mobile phone.
**stand-up**
##### Task: [Truck dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view "Truck dalies draginimas pele")
* Get back stashed code. Working on fuel sorting fn.
* Comments: 
	* Collapse button make more like pill shape and with invisible area to help reach that button. ✅
	* Don't lock resizer then sidebar is collapsed. ✅
	* Minimum width should be like label text width. ✅
* Updated fuel sort fn.
* Added refuel task counting code, created new roll-up field.
* Updating bubble display logic according to comments after the last adjustment.
* Done with fuel task count bubble subtask.
* Fixed all bugs what had find out.
* Try to complete last new functionality subtask.
*don't forget retrieve new created field metadata* ✅
#### 02-18
##### Task: [Auto sattelite toggle button](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnHHV2A3/view "Auto sattelite toggle button")
* Get satellite on zoom icon from figma, added circle in svg and set scale.
* Added button to map controller.
* Writing toggle functionality to set auto map change on zoom functionality.
* Remains to save changes in local storage and preset settings on load the page.
* 