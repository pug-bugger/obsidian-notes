
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