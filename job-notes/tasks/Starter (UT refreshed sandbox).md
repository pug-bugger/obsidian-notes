

```
Account customer = new Account(
    Name = 'Test Customer',
    Customer__c = true,
    Email__c = 'david@dreamcubator.club'
);
Account agent = new Account(Name = 'Test Agent');
Account supplier1 = new Account(Name = 'Test Supplier 1', Supplier__c = true);
Account supplier2 = new Account(Name = 'Test Supplier 2', Supplier__c = true);
Account shipper = new Account(Name = 'Test Shipper', Supplier__c = true);

insert new List<Account>{customer, agent, supplier1, supplier2, shipper};

Contact contactTest = new Contact(
    FirstName = 'David',
    LastName = 'Test',
    Email = 'david@dreamcubator.club',
    User__c = UserInfo.getUserId(),
    AccountId = customer.Id
);
Contact agentContact = new Contact(
    FirstName = 'Agent',
    LastName = 'Test',
    Email = 'david@dreamcubator.club',
    AccountId = agent.Id
);
Contact supplier1Contact = new Contact(
    FirstName = 'Supplier 1',
    LastName = 'Test',
    Email = 'david@dreamcubator.club',
    AccountId = supplier1.Id
);
Contact supplier2Contact = new Contact(
    FirstName = 'Supplier 2',
    LastName = 'Test',
    Email = 'david@dreamcubator.club',
    AccountId = supplier2.Id
);
insert new List<Contact>{contactTest, agentContact, supplier1Contact, supplier2Contact};
```