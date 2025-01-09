[[Regex - Regular expressions]]
Script to generate text with template and send email
```
String bookingId = 'a00Pu00000BvnkGIAR';
DC_ImplementationMap implementations = DC_ImplementationMap.init('Email_Template_Map');
DC_EmailTemplateServiceInterface emailTemplateProvider = (DC_EmailTemplateServiceInterface) implementations.getExclusive();
List<DC_EmailTemplateDTO> emailTemplateDTOs = emailTemplateProvider.getAllTemplates('Test Table', bookingId);
String email = DC_StakeSelector.newInstance().selectCustomerEmailByBookingId(bookingId);
if (email == null) {
    return;
}
Messaging.SingleEmailMessage mail = new Messaging.SingleEmailMessage();
String[] toAddresses = new List<String>{ email };
mail.setToAddresses(toAddresses);
mail.setSenderDisplayName('Test Table');
mail.setSubject(emailTemplateDTOs[0].subject);
mail.setHtmlBody(emailTemplateDTOs[0].body);
Messaging.sendEmail(new List<Messaging.SingleEmailMessage>{ mail });
```

Email Template:
```
Dear Test,
<br/>
<br/>
Show table of this data:
<br/>
{LOOP Services__r [RecordTypeId='012Pu000000wuJjIAI'] [Service_Type__c,Local_Amount__c] LOOP}
<br/>
<b>Total Price: {!Booking__c.Planned_Income__c}

<br/>
```

gpt solution 1:
```
// Given string String objectName = 'Booking__c'; String fieldName = 'Service__c'; // Get the Describe result for the object Schema.SObjectType sObjectType = Schema.getGlobalDescribe().get(objectName); Schema.DescribeSObjectResult sObjectDescribe = sObjectType.getDescribe(); // Get the list of child relationships List<Schema.ChildRelationship> childRelationships = sObjectDescribe.getChildRelationships(); // Variable to hold the matching ChildRelationship Schema.ChildRelationship matchingChildRelationship; // Iterate through child relationships to find the matching field for (Schema.ChildRelationship childRel : childRelationships) { if (childRel.getField() != null && childRel.getField().getDescribe().getName() == fieldName) { matchingChildRelationship = childRel; break; } } // Output the matching ChildRelationship, if found if (matchingChildRelationship != null) { System.debug('Matching Child Relationship found: ' + matchingChildRelationship); System.debug('Child SObject: ' + matchingChildRelationship.getChildSObject()); System.debug('Field: ' + matchingChildRelationship.getField()); System.debug('Relationship Name: ' + matchingChildRelationship.getRelationshipName()); } else { System.debug('No matching Child Relationship found for the field: ' + fieldName); }
```


