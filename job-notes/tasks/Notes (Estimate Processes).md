
**Today Plans**


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
- 
