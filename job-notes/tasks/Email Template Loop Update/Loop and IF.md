```
Hello there,

</br>

{LOOP Booking__c.Milestone__r[Automation_Implementation_Key__c='InformCustomersBookingUpdate']}

{IF {!this.Completed__c}=true}✅ {!this.Type__c} confirmed at {!this.Completed_Date__c}{/IF}

{IF {!Booking__c.Current_Milestone__c}=this.Type__c}🔄️ {!this.Type__c} confirmed at {!this.Completed_Date__c}{/IF}

{IF {!this.Completed__c}=false}{!this.Type__c} confirmed at {!this.Completed_Date__c}{/IF}

{/LOOP}
```
