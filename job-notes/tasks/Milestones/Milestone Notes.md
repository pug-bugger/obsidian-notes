How to create milestone:
1. Create implementation tuples for **post completion** (function to check if milestone id completed) and **completion automation** (function to execute then milestone are completed) fields if required.



***Namings***
Implmentation Map -> Implementation Map Tuple:
* Milestone Template Map
		Milestone Templates
* Milestone Map (map to Milestone service layer)
		Milestone Provider (to milestone service layer impl class with two methods)
* Milestone Map (change to Milestone Post Completion Map)
		Milestone Test (Tuple to post completion implementation)
* Milestone Automation Map (change to Milestone Automation Map)
		Milestone Test (Tuple of automation implementation)


Milestone Template:
* Templates of Milestone records.
		Used By Object
		Controlling Field
		Affected Field Values
		Post Completion Automation (Milestone Post Completion Map)
		Completion Automation (Milestone Automation Map)

Name of generic service layer: ???


1. Milestone kurimas pagal Milestone Template provider

2. Milestone tikrinimas.
Booking'o ir galimai Trip'o triggeris turi turėti milestone check funcionalumą. Jis select'iną visus to object'o milestone'us ir execute'ina post completion automation.
Jeigu Milestone__c.Completed__c pasikeičia į true, tuomet prasideda milestone trigger'io dalies veikimas, pasileisdžia completionAutomation iš onAfterUpdate.
Dar milestone completed gali buti iškar po to, kai tarkim bookingas jau iškart turi kriterijas kuris completeina milestone.