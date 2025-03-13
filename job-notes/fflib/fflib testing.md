
# fflib_ApexMocksUtils

## makeRelationship

```
List<Quote> quotesWithQuoteLineItems = 
	(List<Quote>) fflib_ApexMocksUtils.makeRelationship(
		List<Quote>.class,
		new List<Quote>{ quoteRec },
		QuoteLineItem.QuoteId,
		new List<List<QuoteLineItem>>{ 
			new List<QuoteLineItem>{ plannedIncomeQLI, plannedCostQLI }
		}
	);
```


```
// Then verify new SObjects were created ... 
((fflib_SObjectUnitOfWork)mocks.verify(mockUow,mocks.times(1)
     .description('two accounts sb created')))
                .registerNew(fflib_Match.sObjectsWith(
                  new List<Map<SObjectField,Object>> {
                    new Map<SObjectField,Object> {
                       Account.Name => 'A0',
                       Account.Website => 'www.salesforce.com'
                    },
                    new Map<SObjectField,Object> {
                       Account.Name => 'A1',
                       Account.Website => 'www.google.com'
                    }
                 }
                ));
```