```
Account acc = new Account(Name = 'Test Account');
Account customer = new Account(Name = 'Test Customer', Customer__c = true);
Account supplier1 = new Account(Name = 'Test Supplier 1', Supplier__c = true);
Account supplier2 = new Account(Name = 'Test Supplier 2', Supplier__c = true);
insert new List<Account>{ acc, customer, supplier1, supplier2 };
Contact contact = new Contact(User__c = UserInfo.getUserId(), FirstName = 'Test', LastName = 'Contact', Email = 'david@dreamcubator.club', AccountId = acc.Id);
Contact customerContact = new Contact(FirstName = 'Test', LastName = 'Customer', Email = 'david@dreamcubator.club', AccountId = customer.Id);
insert new List<Contact>{ contact, customerContact };
```
