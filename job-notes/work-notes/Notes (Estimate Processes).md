
**Today Plans**


**Now:**


### 01,02
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
* Added local storage functionality and default setting set.
* Deployed to bitbucket.
##### Task: [Truck dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view)
* Try to rebuild row display logic, try to implement a workaround.
* Try to use resizeObserver api.
* Researching how to handle truck row width change and hide items on reduce row width.
* Sent collected information to Paulius.
* The message:
```
Žodžiu norėjau padaryti kontainerio listeneri per ResizeObserver, bet LWC jis nepalaikomas Locker API, tai yra sprendimas dar saugoti biblioteką static resource ir importinti ir naudoti (https://salesforce.stackexchange.com/questions/366965/resizeobserver-is-not-a-constructor). Arba kas man atrodo perblogai, tai daryti listeneri iš pat resizer komponento į truckRow componentą, bet jeigu naršiklio lankas pasikeis tai jau truckRow width nepersiskaičiuos. 

Dar radau @container rule kur galima uždėti conditions kad row-container width daugiau nei kažkiek ir priklausomai nuo to keisti item'ų width. Galiu šitą išbandyti dar tada jeigu bus laiko.
```
#### 02-19
Answer: 2h to try @container.
##### Task: [Truck dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view)
* Try use @container css rule, seems it works
* Discussed this task job:
	* Move bubble to left a little bit (about 50%).
	* Hiding items one by one, but in items with text first text, and then entire item.
* Added @container rule, fixed last things (icon bubble position, ma/min width, last item left hide).
* Wrote test cases.
##### Task: [STT-16434 range marker tooltip](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BpGAr2AN/view "STT-16434 range marker tooltip")
* Reduce close button width/height from 48px to 24px and remove icon margin.
* Skipped this task now because it is the 28 sprint task.
* Paklaust Eligiju kur šitą pakeisti
##### Task: [STT-16408 csv format info](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BqDPS2A3/view "STT-16408 csv format info")
* Added stopPropagation and cursor changed to default.
* Created PR to partial.
* Assigned existing test case.
##### Task: [STT-16039 search highlight](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Bp6oE2AR/view "STT-16039 search highlight")
* Added search(...) method for group items where group are not filtered out.
* Create PR to partial.
* Assigned existing test case.
##### Task: [STT-16041 info box font change (first time)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BpGQz2AN/view "STT-16041 info box font change (first time)")
* Started task, asked QA how to reproduce.
* Researching this task functionality code.
#### 02-20
##### Task: [STT-16041 info box font change (first time)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BpGQz2AN/view "STT-16041 info box font change (first time)")
* Added font directly in context-menu.
* Try first generate context-menu element and then display it.
* Try use visibility instead of display: none
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view "Kuro kainos ir kiti papildymai adresų grupėms")
* Create endpoint class REST_GroupItems.
* I asked about this task, we discussed what needs to be done.
* Writing endpoint class.
##### Task: [Auto sattelite toggle button](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnHHV2A3/view "Auto sattelite toggle button")
* Added change theme on zoom and changing satellite_on_zoom.
* Fixing initial map selection.
* //from home
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view "Kuro kainos ir kiti papildymai adresų grupėms")
* Wrote postman test requests.
* I created the chat for specifying details about the task.
#### 02-21
##### Task: [Auto sattelite toggle button](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnHHV2A3/view "Auto sattelite toggle button")
* Fixed devbug task. 
* Tested and deployed to PR.
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view "Kuro kainos ir kiti papildymai adresų grupėms")
Schema of request body and map to sf records: [[grou-items-request.canvas]]
* Writing logic to create Account, Location_Group__c and Location_Group_Item__c records.
* It seems I need to create many of fflib layers during completing this task.
* Drawing canvas for own task explanation
*stand-up*
* Created couple of fields (Account.Fuel_Price__c, Location_Group_Item__c.Fuel_Price__c)
* Writing endpoint class logic with fflib.
*code reviewers meet:* [[code-review meet|here]]
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view "Kuro kainos ir kiti papildymai adresų grupėms")
* Created group, group item and account domain layer classes. Writing LocationGroupItemService implementation and testing with postman. for now only to create all records.
#### 02-24
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view "Kuro kainos ir kiti papildymai adresų grupėms")
* Sending http requests and try to debug error. 
*stand-up meet* ==discussed failing test task (made info-box always visible, but if not "opened", then hide by move over the screen, x: 0 and y: 0)== ✅
* Wrote functionality to create new accounts, groups and group items.
* Writing logic of upsert part. Issue with group item and account relationship, try to figure it out how it is should work.
* Call with Paulius, explain to me how it should work.
* Wrote validation method for type parameter to log wrong type values.
* Wrote validation for ids, log them and skip for upserting.
* Testing with postman.
* Writing test class.
#### 02-25
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view "Kuro kainos ir kiti papildymai adresų grupėms")
* Wrote tests and documentation of this endpoint.
* Retrieving all changes from sandbox, fields, permission sets to deploy to bitbucket.
* Fixing comments, updating documentation and endpoint code.
*stand-up meet*
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view "Kuro kainos ir kiti papildymai adresų grupėms")
* Fixed code and documentation comments.
* Remains to write test of REST_GroupItems endpoint class.
##### Task: [STT-16041 info box font change (first time)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BpGQz2AN/view "STT-16041 info box font change (first time)")
* Shift context-menu element over the edge of map container. Display container when are clicked on mad and x and y coordinates appeared from click.
* Can't reproduce the error, hope the bug is fixed🤞
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view)
* Fixed error occurred after I updated group and group item selectors. Replaced old group and group item selectors by new created with this task.
* Started working with design.
* ==Find out problem with endpoint response body, type in chat.== (answer: display "error" next to id and groupId fields of records with wrong ids)
* Some code conflict in sandbox, should I merge changes to one branch.
* Added fuel price column in Edit/Create Location Group window.
#### 02-26
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view)
* Modifying and testing csv.
* Added column to import price also from csv.
*stand-up meet*
* Finally fixed init data upload class. Error occurs because of decimal tries convert \r and empty strings.
* Adding label bubble next to mark.
* Added price display functionality. When price are filled and mark are not in cluster, then display price next to mark.
* Now decided to not display cluster lowest price, but pull mark with lowest price and display separately.
#### 02-27
##### Task: [Auto sattelite toggle button](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnHHV2A3/view "Auto sattelite toggle button")
* Fixed code review
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view)
* Assembled the pallet of colors. (#C42300-red,#BA6F00-orange,#F1A07E-tangerine,#A1BE13-apple,#51BD74-green,#00BCD4-brand_light,#147A89-brand,#27383E-brand_dark)
*went to dentist*
* Added options to Location_Group__c.Group_Color__c picklist. Try to display colors in picklist.
*stand-up meet*
* Added new mark colors in console. Testing and checking if all data displays after change color.
* Fixing markers color update and display price immediately.
* Try to add price comparison and display it.
*1-on-1* pažiūrėti dėl atostogu.
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view)
* Added price comparison in clusters and display lowest price
* Try to find the method of save records and fix fuel_price__c value display after save.
#### 02-28
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view)
* ==I need to learn how to fast and clear find and see the logic and code structure of lwc components (from vscode or dev tools)==
* Find place where marker element rerenders and mess the marker labelRight display code.
* Try to implement last functionality which display lowest price and mark it green color.
*stand-up meet*
* First I will try to display lowest price on load (and add display logic in clusters render), then will check what triggers checked and unchecked field and recalculate on this change.
* Find place where trigger from to update all markers.
### 03
#### 03-03
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view)
* Try to figure out how to update all markers labels after update price.
* Finally fixed price display updates after they was changes in group edit window.
* Finally find the reason why markers clusters does not updating together with markers.
* Searching reason why marker lost the lowest price parameter. debugging and try to find reason
#### 03-04
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view)
* Fixed fuel station price display styling in planner functionality.
* Testing all places where is price used.
* Wrote test cases.
* Fixing gearset.
##### Task: [Truck dalies draginimas pele](https://bcline.lightning.force.com/lightning/r/a0NSZ000008UIsX2AW/view "Truck dalies draginimas pele")
* Fixing code review.
* Fixed bug after testing in sandbox.
* Deployed changes to PR.
*stand-up meet*
##### Task [Reikia orderio grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CVQaP2AX/view "Reikia orderio grupėms")
* Added sort in groupPicker cmp controller.
* Created PR and deployed changes.
* Wrote test case.
##### Task: [resetSygic notification button](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CVRUr2AP/view)
- Searching for new best approach to create buttons more flexible.
- Found something with flow.
- Create "AssetPushNotificationFlow" flow.
- Wrote "AssetPushNotificationController" class with invocable method to call from flow. This class accepts selected asset ids and name of Push_Notification_Data__mdt metadata record api name. Metadata record takes json string to parse and get data.
- Created all metadata records.
- Preparing data and testing
#### 03-05 -
#### 03-06
##### Task: [resetSygic notification button](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CVRUr2AP/view)
- Asked how to test functionality.
- Update all push buttons to new url functionality
- Deployed all to bitbucket and updated labels to save type name (with prefix "Push").
- Created PR to partial.
- Writing test class.
*stand-up meet*
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Call with Paulius, discussed entire task, I found out about the new design and discussed STT (failed sprint task test cases).
- questionable [moving range with middle button](https://bcline.lightning.force.com/lightning/r/a2KSZ000002fL2C2AU/view "moving range with middle button")
- STT-12800 ✅
	- added **user-select: none**.
- STT-12797 🔄️
	- testing, discussed with QA one point.
	- *move to home workspace*
	- for me it happens then I click during moving mouse. Changed onclick by mousedown, maybe it will fix.
	- is to hard to rewrite zoom in functionality to avoid display entire clip. Just added opacity: 0 to hide entire graph.
	- adding minimum range validation. If range less 1 sec, then add extra 1 sec.
- Need to switch to dev19 sandbox to fix and test STT's.
#### 02-07
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- To fix STT-12797 4 and 5 points, required to handle selected range, and disable zoom in button then selected range is critically short for zoom funtionality.
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view "Kuro kainos ir kiti papildymai adresų grupėms")
1. Updated group color select for loop code.
- Fixing sandbox and deploying last changes what are already done.
*stand-up meet*
- Fixed sandbox, deployed own functionality. Run init data create script.
- Fixed groupDisplay code comments.
- Writing test class with fflib.
- Meet the problem with dto mocking in fflib. Solving with Vylius help, try use fflib_ArgumentCaptor and etc.
#### 03-10
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view "Kuro kainos ir kiti papildymai adresų grupėms")
- Finally fixed test class.
- Removed picklist check and logger method.
- Added error field to set error message and updated endpoint doc.
- Writing price value validation. Added validator handler to check if price is a number type value. 
*stand-up meet*
- Wrote price and names validation.
- Updated test methods. Fixed gearset.
- Fixed sidebar dragging task PR merge conflict.
##### Task: [resetSygic notification button](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CVRUr2AP/view)
- Removed old code in PR.
- Fixed Gearset error.
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Fixing STT-12797 last point.
#### 03-12
##### Task: [Kuro kainos ir kiti papildymai adresų grupėms](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnKGz2AN/view "Kuro kainos ir kiti papildymai adresų grupėms")
- Fixed code review comments (removed validator, changed dto type of price from string to decimal, request strings to variable of dto object, and updated clusters render method, join all calculations to one for loop)
- Tested in sandbox, deployed to bitbucket.
- Fixing gearset build error (error related with another task, I need to wait or fix it?)
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Debugging polylineClickHnadler and try to disable in range then button will work incorrect.
*stand-up meet*
- Try to disable zoom button if width is 0, but discussed with Paulius and decided that current solution is good.
- Started review new STT.
- Created new PR to partial to fix permission sets.
##### Task: [Pakoreguojam custom report checkboxų logiką](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CmkEY2AZ/view)
- Researching custom report component.
- Changed getter of selected trucks.
- Tested in dev19 sandbox (with logs)
- Wrote test case.
- Created PR to partial.
#### 03-13
*Fill performance review form*
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- STT-12779 - added z-index then colorGroup is SELECTED.
- STT-12776 - controller passes the sorted by sequence data, exploring/code review of backend. Here trip trigger just put new or updated trip to end of sequence of trips in truck. Here no logic to check date of trip or tasks of that trip.
*stand-up meet*
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Started main task part. Exploring transfer act design implementation.
*lunch*
- Create mini task detail window component
- Q: [[way to create mini task detail window]] 
  https://dreamcubatorteam.slack.com/archives/D01DT8M8HFS/p1741862551961019
  https://dreamcubatorteam.slack.com/archives/D01DT8M8HFS/p1741862784071999
- A: Use simplest way to display that component. Similar to transfer act compare approach.
- Creating c-task-display-mini component
#### 03-14
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Coping task details component design
##### Task: [resetSygic notification button](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CVRUr2AP/view "resetSygic notification button")
- Fix PR gearset 
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Creating task details mini component design.
*Meet - Performance Review*
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Discussed with Paulius that is the best way to pass selected task to task details mini component to display task details.
- Writing task pass by api functionality and coping task details display functionality from task details component.
- Need to check tasks from all trips in date range. 
#### 03-17
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Added task details top part.
- Adding document display section.
- Reached max time of 20 h (need extra 16 h) - logged time on meet task.
- Wrote simple test case before finished task.
- Changing get task info method and source to display info correctly.
- Researching getFinishedTasksByTrips method to fix task info display.
- Adding doc display section (try to figure out why component do not display files)
*stand-up meet*
##### Task: [❌(HISTOGRAM) interaktyvūs task burbulai grafike](https://bcline.lightning.force.com/lightning/r/a0NSZ000005H2Lt2AK/view)
- Do all one dev19 and one branch.
- Change previous task sandbox to dev16, and other histograms updates do on dev19.
- [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view "Histogramos duomenų parsinimo pakeitimai") do in dev19 sandbox in same branch like in this task.
- Researched how works select bubble functionality.
- Find and implement same functionality to this task.
- Next step in task description skipped because of one task with task details is in progress.
- Remains to create PR
#### 03-18
##### Task: [❌(HISTOGRAM) interaktyvūs task burbulai grafike](https://bcline.lightning.force.com/lightning/r/a0NSZ000005H2Lt2AK/view)
- Created PR to partial, wrote test case and developer notes.
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Files data received successfully.
- Fixing css styles to display files properly.
- Remains to check all buttons in task details mini component.
*stand-up meet*  Asked Paulius about task requirements. Checked currenct functionality and what I need to fix.
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Fixed image preview in task details mini window.
- Button of single file download works.
- Added functionality of selection and bulk download.
- Select all and cancel almost done (find bug when select some files and just open another task then snackbar don't hide and fiels from previous task remains selected)
- Fixed display style, snackbar display style and close button to hide entire task details mini window.
- Finish close button update/fix.
- Fixing snackbar and selection (hope the last issue, except snackbar design)
- Fixed snackbar selection on close or change selected task.
- Need to wrote test cases more properly.
- Discussed with Paulius about snackbar design, decided to wait for Erik answer.
#### 03-19
##### Task: [❌(HISTOGRAM) interaktyvūs task burbulai grafike](https://bcline.lightning.force.com/lightning/r/a0NSZ000005H2Lt2AK/view)
- code review fix, commit last task changes and fix error validation code in previous task before started this task code review comment fix.
##### Task: [(Patch) STT-21924 Validate Tooltip Functionality and Appearance](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CwtV62AJ/view)
- prepare sandbox to check this task bug.
*stand-up meet*
##### Task: [(Patch) STT-21924 Validate Tooltip Functionality and Appearance](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CwtV62AJ/view)
- Added overflow-wrap: anywhere style.
- Imported road record from partial to test in sandbox.
- Created PR to master
##### Task: [(Patch) STT-21220 map controller cmp closed/opened](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Cviob2AB/view)
- Testing in sandbox, map controller panel collapse and expand changes save in local storage correctly and after reload display correct state.
- Asked comments about this from QA.
==Deploy partial to sandbox and check==
##### Task: [(Patch) STT-21220 map controller cmp closed/opened](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Cviob2AB/view)
- Deploying all metadata from partial to sandbox.
- Very slow deploying.
- Deploying stuff to dev3 sandbox. Ask Paulius to refresh sandbox to quickly deploy partial changes.
##### Task: [(Patch) STT-21655 exsting accounts updated (group)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CzqSb2AJ/view)
- Removed mappingKey parameter.
- Will test when sandbox will be refreshed.
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Added test case.
- Deploying partial to dev3 sandbox
[[Refresh Sandbox With Latest Master and Partial changes]]
##### Task: [(Patch) STT-21655 exsting accounts updated (group)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CzqSb2AJ/view)
- Deployed all change from partial to dev4 sandbox.
- Fixed and tested [STT-21655](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CzqSb2AJ/view "(Patch) STT-21655 exsting accounts updated (group)"), [21924](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CwtV62AJ/view "(Patch) STT-21924 Validate Tooltip Functionality and Appearance"), [STT-21995](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CxJ1J2AV/view "(Patch) STT-21995 Immediate Update of Markers After Editing Group Items") patched.
- Added test cases to this tasks.
##### Task: [(Patch) STT-21220 map controller cmp closed/opened](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Cviob2AB/view)
- Changed `isCollapsed === "true"` to just `isCollapsed`.
##### Task: [(Patch) STT-21379 trip card (km left, task type, planned tasks number)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D0WDJ2A3/view)
- Reset min-width to 0 in mobile console css.
- Wrote test case
- Created PR to master
#### 03-20
##### Task: [(Patch) STT-21220 map controller cmp closed/opened](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Cviob2AB/view)
- Finishing all patch tasks, fill merge link (same PR for all patches).
- Checked if all patches have test cases.
##### Task: [(Patch) STT-21315 send message](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D0OAv2AN/view)
- Reading API_MessageLogicWrappers class changes.
- Maybe problem with android dto.
- Asked for help in slack. Maybe I should use tablet feature flag to backup last version of endpoint response.
*stand-up meet*
##### Task: [(Patch) STT-21315 send message](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D0OAv2AN/view)
- Figure out the problem reason: Console_Files__r expected object, but array.
- Tested in sf console, related record list json serializes differently. So I need to find way to back object type instead of array for Console_Fiel__r parameter in response.
- Problem with 
```
List<Object> msgList = new List<Object>();
Map<String, Object> msgMap = new Map<String, Object>(message.getPopulatedFieldsAsMap());
msgList.add(msgMap);
```
instead of 
```
List<Message__c> msgList = new List<Message__c>();
msgList.add(message);
```
- Tried to parse response with old Console_Files__r format.
- Discussed with TL and PM what to do, what side of functionality should be fixed.
- Attached script to debug and compare response of old and new parsing code.
##### Task: [(Patch) STT-21220 map controller cmp closed/opened](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Cviob2AB/view)
- changed status
##### Task: [(Patch) STT-21379 trip card (km left, task type, planned tasks number)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D0WDJ2A3/view)
- Changed all patches status.
- Checked PRs.
- Discussing issue of message in chat group.
##### Task: [Kai ištrinu taską planeryje editindamas trip, išsaugojus atidaro ištrintą taską](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CeuEH2AZ/view)
- Switch to histogram task
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Deployed last master changes to dev19 sandbox.
- Forget to switch to another task.
##### Task: [Kai ištrinu taską planeryje editindamas trip, išsaugojus atidaro ištrintą taską](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CeuEH2AZ/view)
- Prepare dev19 to test previous tasks in dev19 sandbox.
- Changed sandbox to dev22.
- Checking how works now.
- Retrieved sandbox access group from production and push to patch branch.
##### Task: [(Patch) STT-21513 all trucks are visable (zoomed out) when first loaded](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D2RW62AN/view)
- Asked QA about this task test case, how to test and what is this Sharing Group in general.
- Testing in dev4 sandbox.
#### 03-21
##### Task: [(Patch) STT-21513 all trucks are visable (zoomed out) when first loaded](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D2RW62AN/view)
- Looking for reason why map don't loaded before action.
- Fixed: added check for null wrapper value.
*stand-up meet*
##### Task: [(Patch) Tušti Fuel Price field'ai vis dar rodomi kaip NaN](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D5JVZ2A3/view)
- Added check for undefined or null num parameter.
##### Task: [Kai ištrinu taską planeryje editindamas trip, išsaugojus atidaro ištrintą taską](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CeuEH2AZ/view)
- Explore planner save method logic and page display logic on click save button
- Added changeVal selectedTask to display trip page on click save button.
- Wrote test case to test redirection to trip task list page.
##### Task: [STT-16434 range marker tooltip](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BpGAr2AN/view)
- Tested and fixed close button in map tooltip.
- Wrote test case.
- Created PR.
*code review meet*
##### Task: [Endpointas žinučių siuntimui](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnGQH2A3/view)
Plan of this task:
- [ ] Create new REST class
- [ ] Create Postman endpoint example with test
- [ ] Write test classes
- [ ] Test Cases
- Looking how it works in message component.
- Create REST_SendMessage class.
#### 03-24
##### Task: [Endpointas žinučių siuntimui](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnGQH2A3/view)
- Writing PostLogicWrapper inner class
*stand-up meet*
##### Task: [Endpointas žinučių siuntimui](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnGQH2A3/view)
- Wrote Test Case and postman endpoint first, before start writing endpoint code.
- Writing PostLogicWrapper.
- Created Message__c service and domain layers classes.
- Writing Message Service and Domain code.
*lunch time*
##### Task: [Endpointas žinučių siuntimui](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnGQH2A3/view)
- Discussed how should be worked endpoint to send message to tablet.
- imei should filter by imei and telematic in one time.
- Writing MessageServiceImpl class code.
*coding standards meet* [[Coding standards meets]]
##### Task: [Endpointas žinučių siuntimui](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnGQH2A3/view)
- Discussed fflib stuff in routical, old selectors with wrong naming left as it is but move to layouts/selector folder.
- Wrote service class with selectors and services layers.
- Tested with postman, looks like all works.
- Added screenshot to test case record.
- Wrote unit tests for Messages and ConsoleFiles domain classes.
- Writing unit test for MessageService class.
- Remains to finish MessageService_TEST and write REST_SendMessage_TEST class.
#### 03-25
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Updated snackbar component design according to the figma design.
- Added new icon.
- Wrote test case for snackbar design.
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Upload changes to branch.
- Waiting for sandbox refresh.
##### Task: [Endpointas žinučių siuntimui](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnGQH2A3/view)
- Deploying changes to refreshed sandbox. Merging master and changes code.
- Wrote test mock class.
- Fixed PR and added permissions, tested in postman.
##### Task: [(Hotfix) lūžta trip planeris ant Save, jei pasirenka iš buvusių task](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DBBlS2AX/view)
- Prepared sandbox and tested with test data.
- Changed Customer__c value assignment from address to Id.
- Create new PR to hotfix-pre-prod
- Wrote test case
==Review some examples of complex sidebar resize==
##### Task: [(Hotfix) info burbulas per aukštai truck liste; draginimo issues](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DBjNJ2A1/view)
- Setup sandbox and prepare to test and fix.
- Fixed default width set and collapse functionality.
- Changing resizer label pallet min-width.
- Updated sidebar drag display logic.
- Remains to solve question with logo and routical logo display. `Restrict draging until logo`.
#### 03-26
##### Task: [(Hotfix) info burbulas per aukštai truck liste; draginimo issues](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DBjNJ2A1/view)
- Editing minimum width.
- Create chat to ask for help to decide.
*stand-up meet*
##### Task: [(Hotfix) info burbulas per aukštai truck liste; draginimo issues](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DBjNJ2A1/view)
- Updated min-width value.
- Made dynamic group picklist component position depends on sidebar position/distance to window edge.
- Fixed info bubble display style, always next to truck row.
- Wrote test cases.
- Created PR to hotfix-pre-prod.
*lunch time*
##### Task: [STT-16434 range marker tooltip](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BpGAr2AN/view "STT-16434 range marker tooltip")
- Redeploying changes to sandbox.
*1-on-1 meet*
##### Task: [STT-16434 range marker tooltip](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BpGAr2AN/view "STT-16434 range marker tooltip")
- Changed sandbox, deployed and tested.
##### Task: [Kai ištrinu taską planeryje editindamas trip, išsaugojus atidaro ištrintą taską](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CeuEH2AZ/view)
- Redeploying.
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Redepoying.
- Fixed close button fn.
##### Task: [❌(HISTOGRAM) interaktyvūs task burbulai grafike](https://bcline.lightning.force.com/lightning/r/a0NSZ000005H2Lt2AK/view)
- Redeploying.
- Testing in sandbox.
- Quick test of Rest sendMessage endpoint in dev6 with postman.
##### Task: [(Hotfix) Truck too far away alertų siuntimas vadybininkams](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DEyMb2AL/view "(Hotfix) Truck too far away alertų siuntimas vadybininkams")
- Asked PM to explain this task.
- Created Truck Group Employee object and Email custom text field.
- Discussed this task logic with Paulius, finding out how exactly should work logic of send emails.
- Writing logic to group emails by additional employees.
==cusros prompt snippets/templates==
#### 03-27
##### Task: [(Hotfix) Truck too far away alertų siuntimas vadybininkams](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DEyMb2AL/view "(Hotfix) Truck too far away alertų siuntimas vadybininkams")
- Try to find out best way to get Employee and Vehicle relationship.
- Created master lookups from Truck_Group_Employee__c to Employee__c and Truck_Group__c objects.
- Created 2 selector classes for Truck_Group_Employee__c and Truck_Group_Item__c objects.
- Writing logic to group emails and send truck info according to the record relationships.
*stand-up chat + lunch*
##### Task: [(Hotfix) Truck too far away alertų siuntimas vadybininkams](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DEyMb2AL/view "(Hotfix) Truck too far away alertų siuntimas vadybininkams")
- Finished writing entire logic to group all data to default and additional emails and send directly.
- Deployed metadata (layouts, new object and fields, permissions)
- Wrote test case with script.
- Writing tests.
- Wrote tests with csv.
- Created PR to hotfix-pre-prod
	- Additional Comments: ==Kolkas iškeliam truck group employee į kitą metodą kad kai prisides kitą logiką tak būtų atskirta.== *2025-03-28*
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Fixing code review comments.
- Fixed last task data getting and display, enum, removed mobile parameter.
- Remains first two comments, with task file and ptvEta getter comments.
#### 03-28
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Solving code review comment of getter method
##### Task: [(Hotfix) prie tam tikros truck listo drago pozicijos bugina top ikonos](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DIQfi2AH/view)
- Importing changes from last master environment.
*lunch*
##### Task: [(Hotfix) prie tam tikros truck listo drago pozicijos bugina top ikonos](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DIQfi2AH/view)
- Fixed style and js controller to get picker position and shift according to the sidebar position.
##### Task: [(Hotfix) Truck too far away alertų siuntimas vadybininkams](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DEyMb2AL/view)
- Tested and fixed truck group item selector.
- Solve code review comments.
- Updated bitbucket branch.
##### Task: [(Hotfix) Navision nullpointer (HOTFIX)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DICRR2A5/view)
- Explore Navision inbound logic wrapper.
- Asked for entire email error log.
- I guess something wrong with relationship, maybe id is null/empty.
*dev-friday meet* [[DEV Friday]]
##### Task: [(Hotfix) Navision nullpointer (HOTFIX)](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DICRR2A5/view)
- Find out that account can be returned as null and can't be registered relationship.
- Created PR to pre hotfix prod branch
#### 03-31
##### Task: [(Hotfix) Truck too far away alertų siuntimas vadybininkams](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DEyMb2AL/view)
- Fixed code review.
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Rewrote ptvEta getter, simplify a little bit. ==read about getters and ad/dis of it==
- Added third level of selector with files to get last files in task details.
- Fixed rotation refresh in task details.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Discussed about this task, the issues and solutions, how try to implement items critical and prettier display calculations.
- Writing test case.
### 04
#### 04-01
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Updates after code review.
- lwc:if don't works in iteration div.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Switch to another task
##### Task: [Endpointas žinučių siuntimui](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnGQH2A3/view)
- Little updates after code review.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Writing noticed thing about lwc:if in chat. [[LWC IF in iterator]]
*stand-up meet + lunch*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Learning d3 library that are used in histogram wrapper.
- Completed task point of rpm data to see in boolean graph.
- Also added axle 1/2 sum graph. Temporary is just sum of ax1 and ax2 until I will know what parameter from http are ax1/2.
#### 04-02
##### Task: [❌(HISTOGRAM) interaktyvūs task burbulai grafike](https://bcline.lightning.force.com/lightning/r/a0NSZ000005H2Lt2AK/view)
- Redeployed
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Switch to task from code review
##### Task: [Endpointas žinučių siuntimui](https://bcline.lightning.force.com/lightning/r/a0NSZ00000BnGQH2A3/view)
- Fixed code review
##### Task: [(Hotfix) dėl naujos versijos užkėlimo konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DRukz2AD/view)
- Updated version from 27_1 to 27_2.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Added seconds display in info wrapper.
*stand-up meet*
##### Task: [Rodyti task attachment failus prie taskų histogramoje + stc iš 24 sprinto](https://bcline.lightning.force.com/lightning/r/a0NSZ000008e2T72AI/view)
- Need more sandboxes with working histogram component and data.
- Redeploying changes.
- Discussed with Paulius about selection drag out of histogram graph edges. It's okey to left it at it is.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Working on max and min range scale for each graph.
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Discussed with Paulius possible reason of this bug, how try to check and test.
- Import new account records and generate groups and group items in sandbox.
- Testing with test data in sandbox, JSON parsing and stringify takes 2 seconds.
- groupDisplay.drawMarkers takes entire array of location group items, this takes much of time (~6 s.) refactoring this to pass to this method only ids of group items/groups/selectAll/unselectAll and on edit update specific data. only first time (on loaded) get all data to work with it in future by ids.
#### 04-03
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Rewriting group display logic.
- Added initial data loading method.
- Wrote logic to pass selected/unselected item ids and check state value from groupSearch component.
*stand-up meet*
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Writing parent component data generation to take ids in groupDisplay.
- It already works better.
- Writing object hash key logic
- Separate draw marker fuctionality to three parts: create cluster, create marker and display or hide.
- Passing ids of items or groups to update display.
- Display changes works faster.
- Cleaning code, update some methods or logic to improve performance.
- Discussed result and decided to reduce getSelectedItemsLatLng array items to the 4 furthest points LatLng__c.
#### 04-04
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Added method to center zoom view according to 4 selected point.
- Added check/uncheck all.
- Writing lowest price calculation. Writing update custom set method.
*stand-up meet + lunch*
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Fixing lowest price display functionality.
- Discussed next task issue and how to complete next task.
- Completed price display part.
- Remains to check how works item edit functionality and how to make it quicker.
#### 04-07
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Check edit button on different groups. Group with the most items loads more time than small.
*stand-up meet*
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Fixing edit data and display updated in the map.
- Fixed all things after updated code structure of markers render.
- Created test case, created PR
*lunch time*
##### Task: [❌(HISTOGRAM) interaktyvūs task burbulai grafike](https://bcline.lightning.force.com/lightning/r/a0NSZ000005H2Lt2AK/view)
- Try to implement selector of selected task in histogram task graph.
#### 04-08
##### Task: [❌(HISTOGRAM) interaktyvūs task burbulai grafike](https://bcline.lightning.force.com/lightning/r/a0NSZ000005H2Lt2AK/view)
- Changed single task selection in histogram task graph functionality.
- Updated test case description.
- Upload changes to PR.
*code reviewing*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Changed sandbox from 19 to 18.
- Setup sandbox, importing test data and connect with vscode.
- Deploying last updated. 
*stand-up meet*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Noted steps to complete this task and estimated approximate time.
*lunch time*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Discussed task progress and plan to complete it.
- Max/Min scale get from axle1, 2 and 1/2 one for each graph.
- Use debug button to toggle round functionality and display dots of real points.
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Fixed lowest price in cluster display fn.
- Fixed group color correct display after edit.
- Fixing display of markers in trip planner, find reason why markers left in map (consoleLoader -> groupSearch method).
#### 04-09
##### Task:[(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Fixing toggleItems, uncheckSystem methods.
*stand-up meet*
##### Task:[(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Fixed last dev bug. Updated display system markers and hide them.
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Setup sandbox dev17.
- Exploring and updating refuelPlan component (added field, but not added link and address name yet to display prettier).
- Added column as url type.
- Writing queueable class to send request to endpoint and map response with appropriate point.
- Discussed task logic and details with Paulius.
#### 04-10
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Writing queueable class. Added selectors methods.
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Code review fixes.
*stand-up meet*
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Finished code review fixes.
##### Task: [Kai ištrinu taską planeryje editindamas trip, išsaugojus atidaro ištrintą taską](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CeuEH2AZ/view)
- PR merge conflict fixed
*lunch time*
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Wrote selector to get required data and pass to endpoint.
- Testing and view rezults.
- Create new field in task object Address_Account__c.
- Added fill logic of this new field.
- Updated selectors.
#### 04-11
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Switch to hotfix
##### Task: [(Hotfix) konsolėje paselectinus adresų grupę - lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Czpmf2AB/view)
- Fixing dev bug.
- Removed check if marker already exist.
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Writing logic to map received data and assign Cheaper_Fuel_Station__c field.
*stand-up*
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Wrote logic to map received near points with lowest price to task.
- Testing
*lunch time*
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Testing and fixing logic. (don't forget add logic to get point from next route if it have cheaper fuel station)
- Discussed code structure with Paulius. (use http wrapper, )
- Renamed old task service impl class to TaskServiceImplOld to separate code from my new class, maybe in future or now will rewrite and move all code from old class to new service class.
- Need to: little method logic update, use httpWrapperV2, write test classes, web console display cheaper fuel station
##### Task: [(Hotfix) nebeveikia planner account search pasirinkimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dk9dV2AR/view)
- Prepare sandbox.
#### 04-14
##### Task: [(Hotfix) nebeveikia planner account search pasirinkimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dk9dV2AR/view)
- Changed object structure.
- For testing deleted old data and created new.
- Assigned existing test case to this task.
- Created PR to hotfix-pre-prod
##### Task: [(Hotfix) importavus tai pačiai grupei vieną degaline su kaina kita be kainos, du](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dk81V2AR/view)
- Asked for csv file.
- Explore fileInputHandler.
*stand-up meet*
##### Task: [(Hotfix) importavus tai pačiai grupei vieną degaline su kaina kita be kainos, du](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dk81V2AR/view)
- Test upload accounts with search group component. It works.
- Waiting for help.
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Writing request in http wrapper
*lunch time*
##### Task: [(Hotfix) importavus tai pačiai grupei vieną degaline su kaina kita be kainos, du](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dk81V2AR/view)
- Fixed groupItems endpoint class (REST_GroupItems) logic implementation class. Added check if group are already declared and ready to commit.
- Created PR to hotfix-pre-prod.
##### Discussing new functionality task
- How functionality should work.
- About bounding box (in future task)
- Add distance calculation until new cheaper fuel station to reach real alternative refuel station.
##### Task: [(Hotfix) nebeveikia planner account search pasirinkimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dk9dV2AR/view)
- Fixed address display fn.
- Deployed changes to PR.
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Explaining new new functionality
- Wrote httpWrapper request.
- Now queueable class sends request for all routes of all trucks. I need to rewrite this part to separate routes by truck and execute logic for each separately.
#### 04-15
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Wrote logic for execute one by one trucks plan.
##### Task: [(Hotfix) nebeveikia planner account search pasirinkimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dk9dV2AR/view "(Hotfix) nebeveikia planner account search pasirinkimas")
- Reviewed dev bug. In sandbox all works.
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Tested, fixed some things, now works properly.
- Remains to write test classes and web console updates.
##### Task: [(Hotfix) nebeveikia planner account search pasirinkimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dk9dV2AR/view "(Hotfix) nebeveikia planner account search pasirinkimas")
- Testing in hotfix sandbox.
- Ask for hotfix sandbox login.
- Cursor IDE lagging.
- Deployed hotfix-pre-prod changes to dev11 and testing.
- Try to deploy and test account from hotfix sandbox in dev11.
*stand-up meet*
##### Task: [(Hotfix) nebeveikia planner account search pasirinkimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dk9dV2AR/view "(Hotfix) nebeveikia planner account search pasirinkimas")
- Imported accounts from hotfix sandbox and still cant reproduce error. Not all fields are included.
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Switch to hotfix task.
##### Task: [(Hotfix) nebeveikia planner account search pasirinkimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dk9dV2AR/view "(Hotfix) nebeveikia planner account search pasirinkimas")
- Imported new accounts from csv.
- Testing with many accounts.
- Fixed by change key in html to avoid key duplications.
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Discussed code architecture, how fflib should look like and what I should to change to improve code architecture. Also discussed queueable and batch approaches in this task context.
- Implement task route length and heap in execute context to control heap limits and continue left trucks in next execution context.
- Approach 1 (read): https://salesforce.stackexchange.com/questions/192109/soql-for-loop-heap-size-how-to-decide-between-speed-and-memory-mangament
#### 04-16
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Rewriting queueable class and service layer code architecture and prepare to testing with big data
*stand-up meet*
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Added address account save in console.
- Tested with one truck.
- Creating test records to test 50 trucks.
*lunch time*
- Created test data, tasks with Address_Account__c and try to execute and test.
*1-on-1 meet*
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Realized, that selector in for loop comes as variable (with full heap size). Use string and select in for loop with Database.query(...);
- Noted last update requirement to get fix functionality (break on truck, but not on trip - in middle of truck)
#### 04-17
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Figure out that query with more than 1 subquery level are not available in for loop.
- Fixed selector and mapping logic.
- Checking and testing
*stand-up meet*
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Find mistake in my code. Fixed and now functionality works good.
- Try to add notification next to task marker when task have filled Cheaper_Fuel_Station__c.
- Discussed test mock data and how to implement that.
- Discussed current task completed job and priority to complete first. Now added logic to check previous route and all next.
- Adding logic to check planned distance and check if truck can reach that alternative point.
*DC Birth Day*
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Exploring fuel calculation in web console.
- Created formula field in vehicle object to see how much km truck can to move.
- Adding logic to calculate possible distance to drive and check if suggested cheaper point are in reachable range and filter inf not
#### 04-18
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Wrote logic to get lowest price from current to last next planned tasks.
- Find out one problem possibly.
- Writing fuel calculation method to get drivable kms and use in planning logic code.
*stand-up meet*
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Discussed with Paulius the problem related with route encoded string, maybe it just in debug console displays that way.
- Wrote logic to track truck drivable distance km and check if point are reachable and can be added to alternative if it is are cheaper fuel station.
- Added logic to consider fuel stations what are in pass and fill trucks and add to drivable distance.
- Created test truck with test trip and tasks. Testing and try to figure out if all works logically.
- I will need to change live_fuel__c value calculation (this field represents procents, but not liters as I thought).
#### 04-22 (holiday)
- supebadge
#### 04-23
*stand-up meet*
##### Task: [(Bug) Map Layer mygtukų pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZLyD2AX/view)
- Added `?? fasle` to assign default false value and save in local storage.
- Created PR and wrote test case.
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Replaced live_fuel with fuel_level formula field of vehicle object.
- Tested with one small truck example. Seems like all works properly.
- Find bug candidate of truck sorting then selecting truck group and display truck with wrong sorting.
- Testing with biggest data. Need to update testing trucks live telematics fuel values.
- Meet/discussed next steps of cheaper fuel task series.
*lunch time*
- Testing with 58 test truck.
- Try to log step by step to see how my code calculates fuel in all process levels.
- Seems like now fuel calculates good.
- Remains to write tests.
#### 04-24
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Testing with other trucks, fixing then execute without pass truck ids.
- Preparing to code review.
*stand-up meet*
- For some reason trucks can take wrong cheaper point. Try to debug and fix it.
*lunch time*
##### Task: [Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Try to compare large test data and 4-5 truck data and figure out key problem.
- Discussed with Paulius how to check and test functionality.
- Discussed next tasks functionality.
- Find out problem reason - trip and tasks are sorted wrong.
#### 04-25
##### Task: [(Patch) Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Fixed sorting functionality by replace next setOrdering.
- Writing tests.
*stand-up meet + lunch time*
##### Task: [(Patch) Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Writing service layer test.
- Wrote simple integration test.
- Retrieving metadata
*dev Friday meet*
==Next week (Monday) new functionality things (fuel plan component, lwc updates, trigger), check PR==
#### 04-28
##### Task: [(Patch) Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Deployed fields and permissions to bitbucket
- Changed drivable formula to do not calculate fuel level under 20 percent.
- Added search reachable stations depth limit
- Added custom settings to set distance to polyline and interval in minutes of scheduler.
- Started writing fuel plan component updates.
*stand-up meet + lunch*
##### Task: [(Patch) Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Completed refuel plan updates. Added two columns with current and alternative fuel price with link to truck refuel page in console.
- Fixed custom settings default data get code.
- Discussed trigger coding place, decided to write in old trigger handler for now.
- Added compare wrapper statements, service method to reset cheaper fuel station for none refuel type tasks.
- On update task address_account__c, ptv_route1__c or type change from or to REFUEL, then that truck cheaper_refuel_station__c checks. If task type changes from refuel to any other type, then cheaper refuel station updates to null.
- Writing tests for trigger handler
#### 04-29
##### Task: [(Patch) Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Wrote tests
- Testing functionality, fixed one bug.
- Created PR to partial.
- Fixing merge conflicts.
*stand-up meet*
##### Task: [(Patch) Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- Fixing merge conflict
*lunch time*
- Fixing merge conflicts.
- Wrote Test cases.
- Fixed merge conflict.
- Fixed queue limit exception using IQueueChainable interface implementation.
##### Task: [(Patch) update dėl pigesnės degalinės lokacijos logikos; front end](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DoFFh2AN/view)
- Created new branch and pulled all functionality from 1022 previous task.
- Imported test data and created one custom truck with trip and tasks.
- Discussed new quick task.
- Created test data.
- Adding € symbol next to trip and task with cheaper refuel station.
#### 04-30
##### Task: [pigesnė kuro alternatyva - front end first part minimal](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EAnYr2AL/view)
- Setup branch and done first task part of truck fuel card tooltip info with "Cheaper fuel available".
- Added euro symbol icon and use for trips and tasks with cheaper fuel available.
- Exploring how works fuel trip select and how to add that trip tasks cheaper fuel account markers.
*stand-up meet + lunch time*
##### Task: [pigesnė kuro alternatyva - front end first part minimal](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EAnYr2AL/view)
- Researching fuelWindow and fuelGraphDisplay code.
- Wrote markers create function.
- Writing logic to display and hide on select trips or tasks.
- Complicated logic of cheaper fuel marker display
  - How to handle refuel stations display from group items and from fuel status display context?
  - Logic to display and hide according to selected trip and task.
- Need to fix markers display logic (create but not display until trip or task are not selected, and hide then trip or task are changed).
### 05
#### 05-02 (holiday)
#### 05-05
##### Task: [(Patch) Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view "https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view")
- Solving code review.
- Have question to Paulius about queueable class scheduling. Will try to figure out by live tacho code example.
- By pass selector refactoring to end of all code review comments.
*stand-up meet*
##### Task: [(Patch) Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view "https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view")
- Discussed with TL and decided to left scheduler as it is and change it in future with patch task.
- Fixed all code review comments, it remains to be completed comments of trip selector convert to task selector.
- Almost done, tested and fixing task selector, decided to finish this last code review comments after cut-off. Save to stash and switch to frontend task.
- Change task status to sandbox review.
##### Task: [pigesnė kuro alternatyva - front end first part minimal](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EAnYr2AL/view)
- Fixed display functionality only on select trip.
- Added listener to hide on unselect trip.
- Wrote logic to display and hide refuel station alternative on click on task also.
- Created PR to partial, wrote test case.
#### 05-06
##### Task: [(Patch) Pigesnės kuro degalinės įtraukimas į lentelę pagal maršrutą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DZJl32AH/view)
- This issue was reported based on a bug found in the developer sandbox. It is not related to this task’s assigned sandbox environment.
##### Task: [update dėl pigesnės degalinės lokacijos logikos; front end](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DoFFh2AN/view)
- setup new environment (sandbox). Deployed all new changes from previous task, imported test data.
*stand-up meet + lunch time*
##### Task: [update dėl pigesnės degalinės lokacijos logikos; front end](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DoFFh2AN/view)
- Added fn to display next.
- Try to add logic to display next task of next trip if exist, but have complexity with it. Seems like near to solution, but still far from it.
- Adding functionality to display around the route refuel stations.
- Almost added fuel stations around the route of selected task and next one.
- Need to fix paths generating and pass to showFuelStationsAlongRoute correct data.
#### 05-07
##### Task: [update dėl pigesnės degalinės lokacijos logikos; front end](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DoFFh2AN/view)
- Fixing display refuel stations around the route. Added parameter to bypass fuel stations hiding on select task. Fixed.
- Fixed next trip task display.
*stand-up meet*
- Fixed refuel stations display fn.
##### Task: [(Patch) Planneryje neveikia add destination butonas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ELMYX2A5/view)
- Fixed bug, deployed to PR to partial.
- Wrote test case.
##### Task: [update dėl pigesnės degalinės lokacijos logikos; front end](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DoFFh2AN/view)
- Added tooltip with text on euro icon with "Cheaper fuel available" text.
- Wrote test case for that functionality.
- Wrote method in context menu to change button display statement. Added to groupMenu open method to check before open context menu.
- Writing logic to get selected task type in Fuel Status window and display or hide Update Fuel Station button.
- Added selectedTaskId global wrapper variable to reach selected task from Fuel Status window in groupDisplay and pass to contextMenu.
#### 05-08
##### Task: [update dėl pigesnės degalinės lokacijos logikos; front end](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DoFFh2AN/view)
- Writing selected task in fuel status window send to vf context menu.
- Done button display functionality.
- Writing "Update Fuel Station" functionlaity.
- Wrote update fuel station functionality part. Need to fix/test:
	- task cheaper field clean,
	- task ptv update,
	- display selected task ptv without reset task selection
- Try reuse trip planner logic
*lunch time*
##### Task: [update dėl pigesnės degalinės lokacijos logikos; front end](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DoFFh2AN/view)
- Finally is almost works.
- Reused addTask method from tripPlanner, seems like all works like expected.
- Fixing cancel trip planner button to reset task marker coordinates.
- Fixed cancel button, but it still takes too long, fixing.
- Created PR.
- Preparing code to code review in bitbucket.
- After solved merge conflict something went wrong and map doesn't work. Will deploy all code to sandbox. Also need to write test case of last functionality.
- Fixed map after merge conflict solving.
- Fixing task marker reset on cancel button click.
#### 05-09
##### Task: [update dėl pigesnės degalinės lokacijos logikos; front end](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DoFFh2AN/view)
- Fixed functionality after merge conflict.
- Fixed marker location display after cancel in trip planner.
- Wrote test case for update fuel station functionality.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Try to remember what I have already done.
*stand-up meet*
- Switch to path tasks.
##### Task: [(Patch) STT-24709 does version number match sprint number](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EOXh72AH/view)
- Updated console version from 27_4 to 28. 
- Setup sandbox and deployed updates.
- Created PR to partial.
##### Task: [(Patch) STT-24770 clear search](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EOZm92AH/view)
- Testing.
- Used consoleLocalStorageWrapper.
- Wrote test case.
- Created PR to partial.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Working on dynamic graph height
##### Task: [(Patch) STT-25508 Task Details From Histogram](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EOjIT2A1/view)
- Deployed all changes from all patches to prepare testing environment for QA.
- Fixed histogramSelecteScreen. 
- Testing.
- Wrote test case. Created PR to partial.
#### 05-12
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixing histogram data fetching.
##### Task: [(Patch) STT-24709 does version number match sprint number](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EOXh72AH/view)
- Fixing PRs.
- Fixing PRs, Waiting for build status refreshing.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixing histogram data fetching.
*stand-up meet*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Switch to patch task.
##### Task: [(Patch) STT-25506 Fast update view in map on select accounts in location group](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ESV422AH/view)
- Debugging partial location group.
- Try to find reason of freeze.
- Imported location groups to dev22 sandbox. Try to test and reproduce bug in sandbox.
*lunch time*
##### Task: [(Patch) STT-25506 Fast update view in map on select accounts in location group](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ESV422AH/view)
- Fixing data loader.
*code standards meet*
##### Task: [(Patch) STT-25506 Fast update view in map on select accounts in location group](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ESV422AH/view)
- Logged loader method. Reason of long loading are not in connectedCallback, but in group line items rendering. When group have many of items, then rendering.
- Wrote logic to rendering items only then group are not collapsed.
- Writing logic to render only first time and hide/display with css.
- *reikia pasitarti su Andrium/Paulium kaip reikėtų daryti, on expand ilgai renderina.*
#### 05-13
##### Task: [(Patch) STT-24782 adding to route](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ESUSx2AP/view)
- Discussing about group search large data rendering issue.
- Fixed add to route functionality from fuel status window.
- Assign test case and created PR to partial.
##### Task: [(Patch) STT-25485 Immediate Update of Markers After Editing Group Items](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ESYuj2AH/view)
- Analyzing and debugging group edit code.
*stand-up meet*
##### Task: [(Patch) STT-25485 Immediate Update of Markers After Editing Group Items](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ESYuj2AH/view)
- Find wrong condition check, removed.
- Assign test case and created PR to partial
##### Task: [(Patch) Navigating to Transfer Acts window throws Error](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ESuqP2AT/view)
- Try to debug with dev tools. Discussed with Paulius, recommended to debug with console logs and set timeouts.
- Chatting with TL.
##### Task: [(Patch) STT-25220 select the truck which has tacho/telmtic history, change to th](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ET2Cs2AL/view)
- Discussing with Paulius about navigation to transfer acts window.
- Fixing PR and branch in VSCode.
##### Task: [(Patch) Navigating to Transfer Acts window throws Error](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ESuqP2AT/view)
- Updated PR code and wrote test cases.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Switch to patch task.
##### Task: [(Patch) Navigating to Transfer Acts window throws Error](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ESuqP2AT/view)
- Error tarted push errors in sandbox, so I find the reason, debugged and fixed by check type of mutation object firs and filter not 'attributes' type items.
#### 05-14
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Added dynamic graph scale.
- Adding 0 points hiding line to display only what are greater than 0.
- Writing/correcting test cases.
*stand-up meet*
##### Task: [(Patch) STT-25485 Immediate Update of Markers After Editing Group Items](https://bcline.lightning.force.com/lightning/r/a0NSZ00000ESYuj2AH/view)
- Testing. It works for me.
- Wait for QA.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Wrote filter method to hide 0 point lines.
- Wrote test case.
- Try to reuse compressed data for graph displaying in tooltip card.
- Exploring histogram data rendering and dependency of scale and zoom.
- Kind of solution, will ask Paulius if good solution.
#### 05-15
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Switching to path tasks
##### Task: [(Patch) STT-25248 Filtering Transfer Acts Within a Date Interval](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EWkIz2AL/view)
- Fixed sf cli.
- Deployed partial code to sandbox dev6.
- Testing and debugging. Try to figure out reason of error.
*stand-up meet*
##### Task: [(Patch) Component Errors yra metami keičiant Truck'us, kol Fuel Window yra open](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EX9Av2AL/view)
- Try to reproduce in sandbox.
*lunch time*
##### Task: [(Patch) Component Errors yra metami keičiant Truck'us, kol Fuel Window yra open](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EX9Av2AL/view)
- Testing and debugging.
- Don't find the source of wrong data is coming, but solved by writing temp solution.
- Fixed, deployed and created PR to partial. Assigned existing test case.
- Tested this task errors. Added ?. to handle null values (also quick solution).
- Created PR to partial and wrote test case record.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Discussed with Paulius about tooltip data display values. *add average values between points*
- Separating tooltip data with different scales.
##### Task: [(Patch) STT-25714 Display Alternative Refuel Station](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EYLLJ2A5/view)
- Find left console field set parameters and fixed one small thing, then next trip user select is have cheaper fuel station too and fuel station of previous trip left in map, so I clean that fuel station marker and display only last selected trip cheaper fuel station merkers.
- Created PR to partial and assigned existing test case.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Updating tooltip data display according to the graph but better. With exact time and smoothy rounded data between items.
#### 05-16
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Creating logic to generate that interpolated data of diagram data.
- Almost done, updating to increase performance.
*stand-up meet*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Added interpolatedData variable to display graphs data in tooltip.
- Writing rounding on zoom, changing rounding scale for particular data type.
*lunch time*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Implemented curveStepAfter for boolean values.
- Updating tooltip data display to ensure that tool tip display exactly what diagram displaying.
- Adding none compressed data display on max zoom.
##### Task: [(Patch) Reikia pakoreguoti dizainą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EZSkX2AX/view)
- Setup sandbox before start developing.
- Try first write test cases before start developing.
- Wrote test cases (~1h).
- Updating euro icon. Writing css to display that icon in orange circle.
#### 05-19
##### Task: [(Patch) Reikia pakoreguoti dizainą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EZSkX2AX/view)
- Updated euro icon circle.
- Updated style of alternative fuel station marker. (point 5)
- Added price label next to task marker.
- Updating fuel card bubble styling depending to cheaper fuel station available parameter
*stand-up meet*
##### Task: [(Patch) Reikia pakoreguoti dizainą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EZSkX2AX/view)
- Updated fuel card bubble style.
- Updated marker price label style, and light green color updated.
- Adding fuel price to task details screen. Added address account to field set, displaying fuel price and address account name next to fuel field in task details.
*lunch time*
##### Task: [(Patch) Reikia pakoreguoti dizainą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EZSkX2AX/view)
- Updated fuel task details fuel field.
- Updated fuel task marker price label, display always.
- Wrote test cases.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Writing zoom compression updates. Writing data compression in dataParser, because of in histogramHelpers it work but a little bit strange.
#### 05-20
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Updated data display on zoom. Added RAW data.
- Tried to increase data display, I need to more compress speed diagram.
- Trying to complete last point with virtual points.
*stand-up meet*
##### Task: [(Patch) Reikia pakoreguoti dizainą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EZSkX2AX/view)
- Updated task fuel price display and in task details.
- Updated lowest price label style.
*lunch time*
##### Task: [(Patch) Reikia pakoreguoti dizainą](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EZSkX2AX/view)
- Fixed little thing (PM_V commented in slack)
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Discussed with Paulius what way to smooth li ne in graph.
- Added new list of RAW data, and modified ALL, last one have smoothed shapes to display more aligned lines in graph.
- Wrote this task comments to PM, waiting for agreements of max time increase.
#### 05-21
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Testing and fixing smooth calculations. Adding fake points to display sharp changes.
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Need discuss first case with Paulius and Vytenis in office.
- I think there need to discuss also, because of in case 2 task account (price: 1.0048) have cheaper fuel station (price: 1.0026). But maybe need to correct trigger to remove that cheaper fuel station when task status changes from planned to any else. Trigger don't have clear functionality after task status changes from planned to any other status.
*stand-up meet*
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Setup dev4 sandbox.
- Added check for task status change from Planned to remove Cheaper_Fuel_Station__c data.
- Wrote test case.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Switch to hotfix task.
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Meet with Paulius and Vytenis.
  1. Check if in this task truck really was able to reach that refuel station. If not, then check service layer code, is it checks fuel level for 20%.
  2. Check why on polyline update cheaper fuel station was not reset to null.
- Fixed code and cheaper fuel station in trigger handler.
- Added new test case and assigned old one.
- Created PR to hotfix-pre-prod branch.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Testing and writing fake point functionality.
*1-on-1 meet*
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Checking bug of task markers and polylines in task fuel window.
- I guess it happened after trip updates in planned component, maybe something with planner draft data before save or after save.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Testing. Switch to hotfix.
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- New functionalities:
  1. Add to route button fix (cheaper fuel station marker in fuel window).
  2. Display button in fuel window.
- Discussed 3 new functionality point, seems like here was problem with markers display, when sometimes expensive fuel station marker displays on top of cheaper.
- Adding cheaper fuel station context menu fn.
#### 05-22
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Writing context menu functionality for cheaper fuel station markers.
- Rewrote cheaper fuel station marker display approach. Deciding to reuse group display functionality. Adding custom styling for cheaper fuel station.
*stand-up meet + lunch time*
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Completed context menu new functionality part.
- Trying to implement expand of critical fuel level trip by default, but have some bug's to fix before.
- Don't forget to retrieve task console field set.
#### 05-27
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Uploaded metadata to the bitbucket.
- Debugging and fixing fuel status auto expand trip (with critical fuel level or alternative fuel station).
*stand-up meet*
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Added setScale for price field value in account domain class.
- Fixing truck fuel window functionality.
- Fixed selection of trip with critical fuel level.
- Adding alternative price criteria and fixing selected trip visual part bug (on select another trip, default selected trip lefts selected and expanded).
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Preparing to code review.
- Fixed default selected trip unselect functionality.
- Wrote test cases.
- Added display fuel station always on calculate fuel toggle on. Done new functionality and wrote new test case.
##### Task: [update dėl pigesnės degalinės lokacijos logikos; front end](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DoFFh2AN/view)
- Checking changes and deploying to refreshed sandbox.
- Fixed style and context menu update in sandbox.
- Tested and updated test case screenshots.
- Need to check again after hot fix merged.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Testing with parameters, try to configure big increasing display functionality.
#### 05-28
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixing increase detect functionality.
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Fixed little code review comments.
- Updated TaskServiceImpl truck type data validation.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Testing with configurations and try to fix increasing detection functionality.
*stand-up meet + lunch time*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Writing logic to display increasing and decreasing data values in graph.
- Separate logic of smoothing of data changes and after smooth adding logic to detect data huge changes.
- The histogram endpoint server is having internet issues. I’m writing as much code as I can, but I’ll have to stop if I need to verify it with the endpoint.
- Wrote detectAndModifySharpChanges method to modify an array of data. Hardest place is to detect and check if data pass condition of big changes and log start and stop indexes.
- Now can't to check if all works, because of data fetching is failing. 
#### 05-29
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Testing fake point functionality.
- Fixed decrease part of fake points.
- Testing and fixing interpolated data display in tooltip card.
*lunch time*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixed displaying of interpolated data on zoom.
- Checking all done work.
- Wrote test cases.
- Fixed 0 points hide fn.
- Created PR to partial.
- Solved merge conflicts.
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Fixed one dev bug. Added check parameters to prevent alternative fuel station marker from remove from map.
- Asked PM about second dev bug and how it should work.
##### Task: [pasiimti/atvaizduoti Anatolijaus atiduodamą telefono nr. Prie vardo pavardės](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dq6mc2AB/view)
- Setup sandbox.
- Created driver mobile number formula field and added to console field set.
- Adding to TruckDriverHeader component.
==Discussed hotfix dev bug. Reikia prideti tikrinima ar tripas yra paselektintas, ir ar range yra pa selektintas, jei nei vienas is situ parametru nera paselektinti, tada notification modalas atsiranda "reikia pasirinkti range'a arba trip'a"==
#### 05-30
##### Task: [pasiimti/atvaizduoti Anatolijaus atiduodamą telefono nr. Prie vardo pavardės](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dq6mc2AB/view)
- Implemented an adaptive style to move the mobile number to the next line if there’s no space in the first line.
- Created PR to partial and wrote test case.
##### Task: [Meet'ai (David) - Dreamcubator](https://bcline.lightning.force.com/lightning/r/a0N5J0000051YxRUAU/view "Meet'ai (David) - Dreamcubator")
- Asked for increase max time.
##### Task: [(Hotfix) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EfO6N2AV/view)
- Fixed dev bug: added check for selected trip also and allows to add point to route if user are selected range or just trip from fuel window component.
- Added parameter to hide alternative fuel station on exit the fuel window. When marker was displayed because of it is an alternative fuel station, then after exit fuel window, marker will be hidden.
*stand-up meet*
##### Task: [failų prikabinimas siunčiant masines žinutes](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DSkjZ2AT/view)
- Adding attachment functionality to global messages component. Added button to add attachments.
- Fixed file cards text line height (added 1 pixel) to display full height of text.
- Edit messageWindow.sendMessages method, removed condition of global message and standardized method of messages with files sending functionality.
- Testing. Messages with only text context displays as always, it didn't break.
- Message with files sent successfully, no errors, but don't see console files in salesforce database.
### 06
#### 06-02
##### Task: [failų prikabinimas siunčiant masines žinutes](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DSkjZ2AT/view)
- Testing and fixing global file sending functionality. Fixing consoleFilesUploader and MessageController code.
*stand-up meet*
- After some fixes records successfully creates in salesforce database, but not displays in global message chat window.
- Forget to start task (from 10:20)
- Exploring message data loading functionality. I need to update filter to get also global messages with files.
*lunch time*
- Find messages with files filtering reason. Added global id to messages with files. Seems like all works. Testing with 100 trucks. Will check test class.
- Fixed test class.
- Fixed on first load data of global messages window. Added data fetching and mapping files with messages.
- Writing test case. Done.
- Created PR to partial.
##### Task: [pasiimti/atvaizduoti Anatolijaus atiduodamą telefono nr. Prie vardo pavardės](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dq6mc2AB/view)
- Updated endpoint of Tachograph. Added new parameter of mobile number.
- Not tested yet.
#### 06-03
##### Task: [pasiimti/atvaizduoti Anatolijaus atiduodamą telefono nr. Prie vardo pavardės](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dq6mc2AB/view)
- Testing, wrote test case.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Checking dev bugs comments and search solutions.
- Created new channel to ask questions about dev bugs.
*stand-up meet + Discussed hotfix changes*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Discussed left to drive to finish in progress task find alternative fuel station. And use geofencing and new boolean field to find new fuel station after left existing fuel station radius.
- About altitude data display: don't smooth line, just set step of change to display new line.
- Display boolean with true/false values.
- Writing the functionality to display raw data to compare processed data and see differences.
#### 06-04
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Writing debug mode data display in dots.
- Discussing with PM about hotfix task.
*stand-up meet*
##### Task: [update dėl pigesnės degalinės lokacijos logikos; front end](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DoFFh2AN/view)
- Merged code after hot fix.
- Find reason of left alternative fuel station in map after select another truck.
- Fixed new functionality bug - added alternative fuel stations hide method even when truck don't have critical or alternative fuel stations.
- Wrote test case for new functionality.
*1-on-1 meet*
##### Task: [(Hotfix) in progress tasko skaičiavimo alternatyviom degalinėm](https://bcline.lightning.force.com/lightning/r/a0NSZ00000F2fxi2AB/view)
- Task test case writing (~45 min)
- Setup sandbox, create test data.
- Generated Account.Near_To_Task_Truck__c custom field with cursor AI chat.
- Updating GeofencingHandler code to update Near_To_Task_Truck__c field. And account trigger handler to remove Cheaper_Fuel_Station__c.
*preparing workplace*
#### 06-05
##### Task: [(Hotfix) in progress tasko skaičiavimo alternatyviom degalinėm](https://bcline.lightning.force.com/lightning/r/a0NSZ00000F2fxi2AB/view)
- Wrote GeofencingHandler logic to update Near_To_Task_Truck__c.
- Prepared test data to test functionality.
- Writing trigger handler after account Near_To_Task_Truck__c field update to execute queueable class.
*stand-up meet*
##### Task: [(Hotfix) in progress tasko skaičiavimo alternatyviom degalinėm](https://bcline.lightning.force.com/lightning/r/a0NSZ00000F2fxi2AB/view)
- Created account service layer to find truck ids and execute search of cheaper fuel queueable class.
- Writing account service unit tests.
- Wrote Sliced Polyline endpoint wrapper, added to task service implementation class and use for accepted and job_started tasks.
- Testing. executePointsAroundPolyRouteDTO method works properly. But updateVisitedTasks fixing in progress.
- Testing and fixing. For some reason after left account, the task doesn't removed cheaper account. Fixed.
- Now seems like all works as required.
- Writing unit tests.
#### 06-06
##### Task: [(Hotfix) in progress tasko skaičiavimo alternatyviom degalinėm](https://bcline.lightning.force.com/lightning/r/a0NSZ00000F2fxi2AB/view)
- Writing tests. Wrote AccountService_TEST, Accounts.
- Writing GeofencingHandler class unit test.
*stand-up meet*
- Rewrote account field to task object logic. Removed account service layer logic and account trigger changes. Removed account custom field and created task Truck_Near_To_Cheaper_Fuel_Station__c with permission sets.
- Prepared PR to gear set building.
- Updated unit tests.
##### Task: [(Bug) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000F5jiD2AR/view)
- Testing in production, searching for cases to reproduce bug in loom.
- Don't find bug.
##### Task: [failų prikabinimas siunčiant masines žinutes](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DSkjZ2AT/view)
- Added search by file name functionality in global messenger.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Adding debug button to see raw data in graph. Added new icon and button in buttons column container next to graph.
#### 06-09
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Writing debug mode fn.
##### Task: [(Hotfix) in progress tasko skaičiavimo alternatyviom degalinėm](https://bcline.lightning.force.com/lightning/r/a0NSZ00000F2fxi2AB/view "(Hotfix) in progress tasko skaičiavimo alternatyviom degalinėm")
- Fixing code review.
##### Task: [(Bug) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000F5jiD2AR/view)
- Still do not have information.
##### Task: [failų prikabinimas siunčiant masines žinutes](https://bcline.lightning.force.com/lightning/r/a0NSZ00000DSkjZ2AT/view)
- Changed status of dev bug.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Lost stashes changes and mixed them, need to fix this.
- Try to write custom function to display boolean data in diagram as I need.
*stand-up meet*
##### Task: [(Hotfix) in progress tasko skaičiavimo alternatyviom degalinėm](https://bcline.lightning.force.com/lightning/r/a0NSZ00000F2fxi2AB/view "(Hotfix) in progress tasko skaičiavimo alternatyviom degalinėm")
- Fixing PR code review. Asked about task statuses.
- Fixing code review comments.
- For some reason final static list not exist in class, but are initialized.
- Added callout counter to track callouts in one apex code transaction.
##### Task: [(Backpropagated) Pigiausio kuro skaičiavimai pagrybauja](https://bcline.lightning.force.com/lightning/r/a0NSZ00000F3KBF2A3/view)
- Checked code, seems like all code changes are in partial, so do not need to create PR to partial.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixed percent display value rounding.
- Editing debug mode data display to check result.
- Seems like made good variant of debug mode data display feature.
#### 06-10
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Testing and fixing debug mode fn. It works not too good with huge data.
- Increase compressed data display ranges, now it displays rather than before.
- Try to display debug data to compare raw and processed data.
*stand-up meet + back propagated task prepare*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Discussed task details tested current done functionality with Paulius.
- [ ] Made group display filter, separate different trend of data.
- [ ] Add fake point to not display null.
- [x] Debug mode fix.
- Debugging, searching for reason of lagging, seems like find the reason, try to fix. Fixed.
- Fixing debug data display mode.
#### 06-11
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixed debug mode data display functionality. Displaying raw data to compare changes.
- Fixing null lines hiding functionality. Added fake points next to fist last point with value to set contrast change. Adding same for averaged data.
*lunch time*
##### Task: [pasiimti/atvaizduoti Anatolijaus atiduodamą telefono nr. Prie vardo pavardės](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dq6mc2AB/view)
- Increased Mobile_Number__c field length to 30 characters.
- Updated number display style.
##### Task: [(Hotfix) in progress tasko skaičiavimo alternatyviom degalinėm](https://bcline.lightning.force.com/lightning/r/a0NSZ00000F2fxi2AB/view)
- Testing and discussing with QA and reproducing errors.
- Try to debug.
- Asked help to recognize error message.
- Selected all accounts with wrong Longitude__c values and changed to valid.
- Tested, now all works good.
- Change consoleSettings.fuelAlongTheRouteRadiusKm custom settings value to set correct distance of displaying near fuel station from route.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixed step function to not display bottom null lines.
- Writing speed and fuel diagrams "vibe" view function...
#### 06-12
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Seems like rpm > 0 tooltip displays correct data.
- Reuse custom smooth functionality, seems like looks better, need to discuss some details.
- Adding listener for 10 min of data change trend and separate from each other. It should make "vibe" effect better.
*lunch time*
- Writing smoothing functionality, added additional configuration feature for each array of raw and averaged data. Adding 10 min data trend detection.
##### Task: [pasiimti/atvaizduoti Anatolijaus atiduodamą telefono nr. Prie vardo pavardės](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dq6mc2AB/view)
- Discussed dev bug requirements.
- Fixed dev bug, replaced phone number to another place with shift item styling. Added css to avoid wrapping in truck name for no reason.
##### Task: [(Hotfix) Calculate Fuel ilgesniam poly along the route degalinės neatsiranda](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKJ132AH/view)
- Fixed init PR and create new PR to hotfix-pre-prod brunch.
- Using dev17 with previous hotfix changes.
- Tried to reproduce in sandbox, checked logs, have nothing to work with.
##### Task: [(Hotfix) Siūlo pigesnę tą pačią degalinę, kuri jau yra suplanuota](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EnEo92AF/view)
- Added updates to prevent select cheaper fuel station like address account.
- Added rounding
- Wrote test case
##### Task: [(Hotfix) Calculate Fuel ilgesniam poly along the route degalinės neatsiranda](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKJ132AH/view)
- Debugging error in production with one truck (NFB373 / Focus) trip.
- Find what this path parameter are not valid, too small I guess. (consoleLoader -> handleFuelAlongRoute)
- ![[Pasted image 20250612162336.png]]
#### 06-16
##### Task: [(Hotfix) Calculate Fuel ilgesniam poly along the route degalinės neatsiranda](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKJ132AH/view)
- Added if condition to bypass small array of path.
*stand-up meet*
- Create PR to hotfix branch.
- Wrote test case.
##### Task: [pasiimti/atvaizduoti Anatolijaus atiduodamą telefono nr. Prie vardo pavardės](https://bcline.lightning.force.com/lightning/r/a0NSZ00000Dq6mc2AB/view)
- Added console field set to PR.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Switch to hotfix comments fixing.
##### Task: [(Hotfix) Calculate Fuel ilgesniam poly along the route degalinės neatsiranda](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKJ132AH/view)
- Wrote wrapper for routeBoxer to handle error case.
- Adding custom bounding box for cases when path array length are less than 4 items.
*lunch time*
- Added custom bounding functionality. Tested, all works good.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixed path PR with new versioning.
- Discussed requirements and done job with Paulius, we have formed the requirements that I need to be corrected.
- Changed 10min, hour and 12hour to 2, 5, 10 and 30 min sets.
- Adding logic to calculate average with no losing max and min values.
#### 06-17
##### Task: [(Patch) STT-28043 does version number match sprint number](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FQRlV2AX/view)
- Version was updated in https://bitbucket.org/dcsid/tms-console-package/pull-requests/2547
##### Task: [Meet'ai (David) - Dreamcubator](https://bcline.lightning.force.com/lightning/r/a0N5J0000051YxRUAU/view)
- Waiting for decision.
##### Task: [Kai paspaudi "X" išėjimas iš planerio lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D8wDq2AJ/view "Kai paspaudi \"X\" išėjimas iš planerio lagina")
- Testing in sandbox, compare with production. Seems like not only planner, but other windows has same problem when huge count of trucks are displaying in truck list.
- Decided to skip for now.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Writing averaging functionality and step displaying in averaged data.
*stand-up meet*
##### Task: [(Patch) STT-28043 does version number match sprint number](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FQRlV2AX/view "(Patch) STT-28043 does version number match sprint number")
- Updated version. Created PR to partial. Assigned existing test case.
##### Task: [(Patch) STT-28753 Validate Tooltip Functionality and Appearance](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FRLED2A5/view)
- Setup sandbox.
- Added style to address marker context menu, fixed button style.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixing contras of change functionality.
*lunch time*
- Switch to another task.
##### Task: [(Hotfix) Calculate Fuel ilgesniam poly along the route degalinės neatsiranda](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKJ132AH/view)
- Created new PR with updated version
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixed step display of big change (for fuel item)
- Writing new custom average functionality.
#### 06-18
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Added detectAndModifySharpChanges functionality to all sets, added new fake point before last increased or decreased point to display changes.
##### Task: [(Hotfix) Calculate Fuel ilgesniam poly along the route degalinės neatsiranda](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKJ132AH/view)
- Try to figure out reason why test in gear set failing.
*stand-up meet + windows updates*
- Updated PR, waiting for gearset build status update.
- Fixed PR.
*lunch time*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixed fake point fn. Preparing code to write new averaging functionality.
- Prepared to work on custom average method. Made sumData\[ALL\] as averaged by 1 min. Now all calculations will be executed on this data.
- Fixed max/min scaling set, max data are not too near to top border. Altitude now displays line under 0 point.
- Fixing round to minute range average.
*1-on-1 David (Performance Review Follow-up)*
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Fixing 1 min average set calculation. Problem with items where are to small/wide interval.
#### 06-19
##### Task: [(Patch) STT-28513 global checkbox value](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FRs8X2AT/view)
- Setup new dev22 sandbox.
- Replaced updateAllSelectionValue method after the location items changes.
- Created PR.
- Remains to write or assign existing test case.
*stand-up meet*
##### Task: [(Patch) STT-28513 global checkbox value](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FRs8X2AT/view)
- Added test case.
##### Task: [(Patch) STT-28067 navigating range left and right](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FTv8j2AD/view)
- Reuse dev16, deployed last changes.
- Researching move to left and right range change event handler and try to find approach to reset selections and on change range by moving to left of right in histogramSelectionScreen.
*lunch time*
##### Task: [(Patch) STT-28067 navigating range left and right](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FTv8j2AD/view)
- Added this.rangeSelector.hideItems(); on range selection change.
- Tested, assigned test case.
- Created PR to partial.
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- For some reason averaging works but not always. Fixed it, problem was in this line `partialTimeDistance -= oneMinute`, changed to this `partialTimeDistance -= Math.floor(partialTimeDistance / oneMinute) * oneMinute;`.
- Fixed tooltip display interpolated data.
- Writing custom average calculation function. Implementing described logic on the paper.
#### 06-20
##### Task: [Histogramos duomenų parsinimo pakeitimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000CrSwv2AF/view)
- Writing logic to average with no min/max data loss.
*stand-up meet*
- Discussed done parts of task and remains requirements.
- Wrote much of code and logic, but it is not work. Something wrong.
- Debugging and try to find reason where is not working.
#### 06-25
##### Task: [Adblue įtraukimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKcoT2AT/view)
- Setup new sandbox.
- Created new custom field Adblue_Price__c for Account object.
*stand-up meet*
- Try to update accountsInsert apex class and csv file to create accounts with adblue price.
- Just deployed changed csv to sandbox, now works good.
- Added adbluePrice parameter to **groupItems** endpoint, updated shared google document of endpoint documentation: https://docs.google.com/document/d/1qs3Vi2rnLNRpIB9eyqeCypZ1Wy9UfqUE-pEruFGkLcw/edit?tab=t.0
- Created Fuel Price Last Updated and Adblue Price Last Updated date fields.
- Writing test cases.
- Added adblue max price finding in findCheaperFuelStations method, edited account selector.
- Added new fields to field sets and layouts.
- Don't forget about near to cheaper adblue station.
==Father's Holiday==
### 07
#### 07-28
##### Task: [Meet'ai (David) - Dreamcubator](https://bcline.lightning.force.com/lightning/r/a0N5J0000051YxRUAU/view "Meet'ai (David) - Dreamcubator") (completed tasks testing)
- Remembering tasks, testing assigned to me tasks.
- Prepare doc about father's vacation.
*stand-up meet + waiting for task max time increasing*
##### Task: [Adblue įtraukimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKcoT2AT/view)
- Investigating changes and testing in sandbox.
*lunch time*
##### Task: [Adblue įtraukimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKcoT2AT/view)
- Tested this task. Didn't find any inconsistencies.
##### Task: [Keletas issues su pigiausia degaline](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FsAPx2AN/view)
- Tested this task, Didn't find any inconsistencies.
##### Task: [Kažkodėl duodam pigiausią degalinę jau nuvažiuotam maršrutui](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FwpKr2AJ/view)
- Testing and researching changes. Try to test, but for some reason is not work as expected. Try to figure out how why.
#### 07-29
##### Task: [Keletas issues su pigiausia degaline](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FsAPx2AN/view)
- Tested cheaper fuel price finder functionality. Added task test case for [Kažkodėl duodam pigiausią degalinę jau nuvažiuotam maršrutui](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FwpKr2AJ/view) task
- Renamed queueable class name. Removed scheduler from partial to deploy new named scheduler.
- Edited location group item fuel price formula field and replacing to use it in code and hide if not valid or expired price.
*stand-up meet*
##### Task: [Adblue įtraukimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKcoT2AT/view)
- Updating expire price display logic.
*lunch time*
##### Task: [Keletas issues su pigiausia degaline](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FsAPx2AN/view)
- Updated and fixed expired price display functionality.
- Wrote new test case.
- Waiting for opinion about fuel and adblue price display next to markers logic.
##### Task: [Kai paspaudi "X" išėjimas iš planerio lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D8wDq2AJ/view)
- Setup sandbox, preparing to check with debug tools.
- Switch to another task.
##### Task: [Keletas issues su pigiausia degaline](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FsAPx2AN/view)
- Updated test case.
- Updated label display next to fuel marker logic according to the PM answer in chat.
##### Task: [kuro kainų atvaizdavimas, pigiausių rodymo update + konfigūruojama](https://bcline.lightning.force.com/lightning/r/a0NSZ00000E5T4X2AV/view)
- Lowest price label style captures values up to a difference of 0.02€
- Fixed fuel and adblue price formula fields precision in 3 numbers after dots.
- improving code readability.
#### 07-30
##### Task: [kuro kainų atvaizdavimas, pigiausių rodymo update + konfigūruojama](https://bcline.lightning.force.com/lightning/r/a0NSZ00000E5T4X2AV/view)
- Discussed with dev how to implement last point of this task - configurable lowest price threshold. Decided to create new class (same as ConsoleSettings.cls) and import to lwc and send to groupDisplay in initial method.
- Testing and fixing bugs (default loaded markers disappears on close fuel window component)
*stand-up meet (chat)*
##### Task: [kuro kainų atvaizdavimas, pigiausių rodymo update + konfigūruojama](https://bcline.lightning.force.com/lightning/r/a0NSZ00000E5T4X2AV/view)
- Initially loaded and displayed markers disappearing on close fuel window. Fixing this bug.
*lunch time*
- Fixed bug with display of local stored selected groups.
- Update test case.
##### Task: [Pigiausios degalinės patobulinimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EpmAb2AJ/view)
- Added fields with saving on alternative price. Need to discuss with PM about this logic, how to display and visualize difference to show real information.
- Testing and fixing taskServiceImpl.findCheaperFuelStations code.
#### 07-31
##### Task: [Pigiausios degalinės patobulinimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EpmAb2AJ/view)
- Code readability improvements. Tested and fixed calculation to correct compare the 1.188 and 1.19 prices. 
- Renamed task domain method.
- Waiting for ideas how to display saving.
##### Task: [Kai paspaudi "X" išėjimas iš planerio lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D8wDq2AJ/view)
- Learning browser devtools to find freeze ui reason on close window in console.
- Read long executed code.
- I see what taskProgress are using getBoundingClientRect in each bubble element, what can cause increase of execution time. Scrollbar also use getBoundingClientRect, need to test it.
#### 08-01
##### Task: [Kai paspaudi "X" išėjimas iš planerio lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D8wDq2AJ/view)
- Researching long executable code.
- I think taskProgress has a renderedCallback with an outdated implementation. getBoundingClientRect is resource-intensive, and this component uses it excessively. This part of the logic needs to be rewritten.
##### Task: [Pigiausios degalinės patobulinimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EpmAb2AJ/view)
- Meet with Paulius, discussed how saving price calculation should be displayed.
- Tried to add custom tooltip element to refuelPlanTable component header, but unfortunately not success, seems like it request to rewrite entire refuelPlanTable component and use entirely custom header.
- Updating logic according to the task description updates. Working on nearest point find functionality. Implementing RouticalRoutinApiWrp class to get leftDistance and compate with planned task left distance.
- I think js already have functionality to calculate left to drive, need to check this and implement.
#### 08-05
##### Task: [firebase token bugo prevencijai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKW9Z2AX/view)
- Added limitation handler in asset trigger handler. Wrote test case.
##### Task: [Pigiausios degalinės patobulinimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EpmAb2AJ/view)
- Investigating fuel calculation functionality.
*stand-up meet + lunch time*
##### Task: [Pigiausios degalinės patobulinimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EpmAb2AJ/view)
- Writing low price calculation display fn.
- Discussed with Paulius how to display tooltip, in last queue do this. Try add css before and hover to override header style to display tooltip.
- Added scrollbar in fuel-window.
- Writing logic to get nearest point and calculate difference in price for fact liters.
#### 08-06
##### Task: [Pigiausios degalinės patobulinimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EpmAb2AJ/view)
- Created new custom fields to save distance from planned task to alternative fuel and adblue points.
- Writing logic to save alternative distances and use it in Refuel Plan
*stand-up meet (chat)*
##### Task: [Pigiausios degalinės patobulinimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EpmAb2AJ/view)
- Updated and tested custom fields.
- Wrote logic to save distance to alternative fuel or adblue stations. Tested.
- Updating Refuel Plan component, rewriting logic of saving price calculation.
#### 08-07
##### Task: [Pigiausios degalinės patobulinimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EpmAb2AJ/view)
- Writing Refuel Plan component savings columns calculation functionality. Remains write calculation for tank level then truck will arrive point and calculate liters are available to fill.
*stand-up meet (chat)*
##### Task: [Pigiausios degalinės patobulinimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EpmAb2AJ/view)
- Finished Refuel Plan component updates.
- Added tooltip to saving headers by hacking css styles with ::before and :hover help.
- Wrote test cases.
- Remains to made little changes.
#### 08-08
##### Task: [Pigiausios degalinės patobulinimai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000EpmAb2AJ/view)
- Renamed css file. Tested and checked
##### Task: [Keletas issues su pigiausia degaline](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FsAPx2AN/view)
- Fixing fuel marker hiding on unselect specific task.
*stand-up meet*
##### Task: [Keletas issues su pigiausia degaline](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FsAPx2AN/view "Keletas issues su pigiausia degaline")
- Fixed markers loading from local storage.
##### Task: [Adblue įtraukimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKcoT2AT/view "Adblue įtraukimas")
- Fixed price update date.
- Fixed alternative station display fn, hide when price are expired (older than 5 days). Created two new formula fields.
##### Task: [firebase token bugo prevencijai](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKW9Z2AX/view)
- Fixed code review.
#### 08-11
##### Task: [Adblue įtraukimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKcoT2AT/view)
- Added permissions, fixed gearset
##### Task: [Kai paspaudi "X" išėjimas iš planerio lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D8wDq2AJ/view)
- Try to debug, comment checkAll method in mainFrame, testing performance, not sure is big problem with this.
*stand-up meet*
##### Task: [custom reportus padaryti pasiekiamus konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000H1fLv2AJ/view)
- Setup sandbox. Discussed task with Paulius. Added and replaces new svg's in navigation.
- Writing logic to display custom report component in modal window in console. 
- Added new option with custom report template. Updating css and make if looks native and more comfortable to use.
#### 08-12
##### Task: [custom reportus padaryti pasiekiamus konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000H1fLv2AJ/view)
- Finished styling, fixing bugs and check performance.
*stand-up meet*
##### Task: [custom reportus padaryti pasiekiamus konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000H1fLv2AJ/view)
- Fixed close button in footer and added little style updates
- Writing test cases.
- Discussed with Paulius: 
  - Custom Report - try replace custom report component theme to dark on ark console mode.
  - "X" close button - try debug post message.
*lunch time*
##### Task: [custom reportus padaryti pasiekiamus konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000H1fLv2AJ/view)
- Remove footer from custom report modal window in web console.
- Researching theme implementation in custom report. Decided to skip this part.
- Wrote test cases.
##### Task: [Kai paspaudi "X" išėjimas iš planerio lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D8wDq2AJ/view)
- Tried to comment and debug postMessages. Nope.
- Debugging with Paulius. Find that cards impact to lagging.
- Need to debug and research cards, tooltip, getters, icon providers and check what exactly takes a long time to load.
#### 08-13
##### Task: [Kai paspaudi "X" išėjimas iš planerio lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D8wDq2AJ/view)
- Debugging and try to optimize card rendering.
*lunch time*
##### Task: [custom reportus padaryti pasiekiamus konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000H1fLv2AJ/view)
- Replaced tacho icon with new one.
- Combining colors and replace default to console style.
*routical coding standards MEET*
>1. general test cases, smulkmenos, bet pasimeta/pasimirštama.
>2. browser adequate zoom range
>3. console design differences - is not possible now to draw entire design, so it is not that important thing to spent much time.
>4. General test cases (component always should be visible in different themes/modes)
>5. Scheduler now should be started with custom runner.
##### Task: [custom reportus padaryti pasiekiamus konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000H1fLv2AJ/view)
- Writing dark and light mode for custom report in console.
#### 08-14
##### Task: [custom reportus padaryti pasiekiamus konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000H1fLv2AJ/view)
- Deployed all to dev17 sandbox to test dark mode with generated data.
- Testing and fixing css styling in dark mode.
- Updated test case.
*stand-up meet (chat) + lunch time*
##### Task: [custom reportus padaryti pasiekiamus konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000H1fLv2AJ/view)
- Fixed all comments from Paulius: wrong styling, colors and icons.
- Working on default loaded data to display last loaded data after close window.
#### 08-15 *holiday*
#### 08-18
##### Task: [custom reportus padaryti pasiekiamus konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000H1fLv2AJ/view)
- Fixing bugs - select rows in console.
- Working on default loaded data to display last loaded data after close window.
*stand-up meet*
- Fixed init data loading after close and open custom reports in console.
- Updated test cases
##### Task: [Adblue įtraukimas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000FKcoT2AT/view "Adblue įtraukimas")
- Fixed code review comments.
##### Task: [Kai paspaudi "X" išėjimas iš planerio lagina](https://bcline.lightning.force.com/lightning/r/a0NSZ00000D8wDq2AJ/view)
- Debugging and testing to optimize how cards load in truck rows.
- Working on refining the re-rendering logic to make it more precise for all cards.
==Reikia daryti mini refactor'inima su lazy loading, ir tuo pačiu ne passinti wrapper kaip api, bet padavinėti tik tai, ką reikia, atskirai parametrus==
#### 08-19
##### Task: [Transport Manager Group search funkcionalumas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000GoNbJ2AV/view)
- Added search-bar to group-picker component. Added css (left bug with search bar input field icon z-index, need to fix)
- Writing filter and display in list component functionality.
*stand-up meet*
##### Task: [custom reportus padaryti pasiekiamus konsolėje](https://bcline.lightning.force.com/lightning/r/a0NSZ00000H1fLv2AJ/view)
- Fix code review.
##### Task: [Transport Manager Group search funkcionalumas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000GoNbJ2AV/view)
- Writing filter functionality and its display logic.
*lunch time*
##### Task: [Transport Manager Group search funkcionalumas](https://bcline.lightning.force.com/lightning/r/a0NSZ00000GoNbJ2AV/view)
- Writing filter logic: hide filtered truck groups, highlighting matched text.
- Display icon with text when result in not found.
- Fixed clean icon visible when group picker is closed.
- Remains to write logic of checkAll functionality.