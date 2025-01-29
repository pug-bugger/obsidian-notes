
**Today Plans**

1. Fix code review [Trigeris ant Service Exchange Rate'ams nustatyti](https://bcline.lightning.force.com/lightning/r/Task__c/a0NSZ00000AgMPl2AN/view)
2. Fix code review [Invoice Generavimas iš Planned Income](https://bcline.lightning.force.com/lightning/r/Task__c/a0NSZ00000AgIFh2AN/view)
3. Somehow fix spot quote tasks code review.
4. and then finish milestone post completed triggers (stakes and booking status)

**Now:**

Task: [Trigeris ant Service Exchange Rate'ams nustatyti](https://bcline.lightning.force.com/lightning/r/Task__c/a0NSZ00000AgMPl2AN/view)
- [x] Create cmp variable to identify trip recorf type is changed.
On service after update event to invoiceRoolup calculate add `&& cmp.hasRecordTypeChanged`

Task: [Invoice Generavimas iš Planned Income](https://bcline.lightning.force.com/lightning/r/Task__c/a0NSZ00000AgIFh2AN/view)
- [x] CR_  fix small comments @completed(2025-01-29T15:34:33+02:00)
- empty list check in service layer, not in domain.
- don't call schema in for loop.

Task: 