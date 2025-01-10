**(A+B)**
Create Booking__c record.
Create Account and Contact and then Stake__c record related to booking.
Create "Sea FCL Booking Update to Customer" type Email_Template__c record (as in test case)
**(A)**
Change booking related Milestone__c record Completed__c field to "true".
In email inbox should appear email notification form Salesforce.
**(B)**
Upload file to booking record, then open that file ContectVersion and fill Document_Type__c with "Export Declaration", and save changes.
Check email inbox.

**(C)**
Create Trip__c record.
Create Stake__c for this trip with Contact and Account records.
Create Email_Template__c record of "ShipsGo Tracking Link" type
Change trip Container_Status__c to "Sailing" and save.
Check email inbox.

**(GENERAL)**
After I created booking record I see two milestone record related to this booking record.
