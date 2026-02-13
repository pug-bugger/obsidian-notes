
```
/*
This is the code that unarchives the messages
*/
List<Message__c> messages = [SELECT Id, Archived__c FROM Message__c WHERE Archived__c = true LIMIT 10000];
for(Message__c message : messages) {
    message.Archived__c = false;
}
update messages;

/*
This is the batch that archives the messages
*/
BATCH_ArchiveMessagesFiles batch = new BATCH_ArchiveMessagesFiles(180);
Database.executeBatch(batch, 100);


/*
Create a new messages
*/
List<Vehicle__c> vehicles = [SELECT Id, Name FROM Vehicle__c WHERE Name LIKE 'AUTO_GEN_%' LIMIT 9 OFFSET 18];
List<Message__c> messages = new List<Message__c>();
for(Vehicle__c vehicle : vehicles) {
  for(Integer i = 0; i < 1000; i++) {
    messages.add(new Message__c(
    	Truck__c = vehicle.Id,
      Message__c = 'Test' + i + ' ' + vehicle.Name,
      Type__c = (i & 1) == 0 ? 'SALESFORCE' : 'TABLET'
    ));
  }
}
insert messages;



// testing with fflib, relate not created yet records
// 1. Initialize UoW with the objects in order of dependency
fflib_SObjectUnitOfWork uow1 = new fflib_SObjectUnitOfWork(
    new List<SObjectType> { Message__c.SObjectType }
);
fflib_SObjectUnitOfWork uow2 = new fflib_SObjectUnitOfWork(
    new List<SObjectType> { Message__c.SObjectType }
);
// 2. Instantiate the Parent
Message__c newArchive = new Message__c(
    Truck__c = 'a03ba00000FxcmOAAR',
    Archive_JSON__c = '[{test: 1}]',
    Archive__c = true
);
uow1.registerNew(newArchive);

// 3. Instantiate the Child
Message__c msg = [SELECT Id FROM Message__c WHERE Id = 'a0Cba000031RKgqEAG' LIMIT 1];
// 4. RELATE THEM (The Magic Step)
// Parameters: (Child Record, Child Lookup Field, Parent Record)
uow2.registerRelationship(msg, Message__c.Archive_Message__c, newArchive);
// 5. Register the Child as New
// uow.registerNew(msg);
uow2.registerDirty(msg, new List<Schema.SObjectField>{ Message__c.Archive_Message__c });
// 6. Commit everything in one transaction
uow1.commitWork();
uow2.commitWork();



// Script to create Messages __c records
List<Vehicle__c> vehicles = [SELECT Id FROM Vehicle__c WHERE Name LIKE 'AUTO_GEN_%' LIMIT 10];
List<Message__c> messages = new List<Message__c>();
for(Vehicle__c vehicle : vehicles) {
  for(Integer i = 0; i < 100; i++) {
    messages.add(new Message__c(
      Truck__c = vehicle.Id,
      Message__c = 'Test' + i,
      Type__c = 'SALESFORCE',
      CreatedDate = Date.today().addDays(-170 - i)
    ));
  }
}
insert messages;


// Script to create Console_File__c records
List<Message__c> messages = [SELECT Id FROM Message__c LIMIT 10 OFFSET 105];
List<Console_File__c> consoleFiles = new List<Console_File__c>();
for (Message__c message : messages) {
  for(Integer i = 0; i < 2; i++) {
    consoleFiles.add(new Console_File__c(
      Message__c = message.Id,
      Name = 'Test' + i,
      Url__c = 'https://routical.transimeksa.com/api/aws/download/80a019bf-4c99-45b5-9a81-0378d6a2889b',
      CreatedDate = Date.today().addDays(-200 - i),
      LastModifiedDate = Date.today().addDays(-150 - i)
    ));
  }
}
insert consoleFiles;
```

