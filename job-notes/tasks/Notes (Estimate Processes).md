
**Today Plans**

1. finish milestone post completed triggers (stakes and booking status)
Exploring

**Now:**



#### 2025-01-29
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
#### 2025-01-30
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

#### 2025-01-30
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
#### 2025-02-03
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
#### 2025-01-04
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