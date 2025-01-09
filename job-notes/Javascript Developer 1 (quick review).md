**Another modules functionalities available from one main place**
Make another modules functions easily available throughout the project, create passthrough module named 'pass.js' in the main project folder.
``` 
export { parseData } from './utilities/dataUtil.js';
export { compose } from './utilites/util.js';
export {normalizeData} from './utilities/commonUtils.js';
```

**Promise.race(\[...\])**
The Promise.race method returns a promise as soon as one of the promises passed to it is fulfilled or rejected.

**Don't use the cache**
1. Access the Network panel and check the 'Disable cache' checkbox.
2. With DevTools opened, long-press the reload button and select Hard Reload


**Browser and Events**

```
<table>
<tr style="background-color: #D6EEEE;">
<th>Service</th>
<th>Type</th>
<th>Weight (kg)</th>
<th>Volume (m3)</th>
<th>Quantity of Packages</th>
<tr></tr>
{LOOP Booking__c.Containers__r}
<tr style="border-bottom: 1px solid #D6EEEE;">
<td>{!this.Name}</td>
<td>{!this.Type__c}</td>
<td>{!this.Weight_kg__c}</td>
<td>{!this.Volume_m3__c}</td>
<td>{!this.Quantity_of_Packages__c}</td>
</tr>
{/LOOP}
</table>
```


<table>  
<tr style="background-color: #D6EEEE; padding: 5px 10px;">  
<th>Service</th>  
<th>Type</th>  
<th>Weight (kg)</th>  
<th>Volume (m3)</th>  
<th>Quantity of Packages</th>  
</tr> 
<tr style="border-bottom: 1px solid #D6EEEE; padding: 5px 10px;">  
<td>Test Name</td>  
<td>Type</td>  
<td>15 kg</td>  
<td>0.3 m3</td>  
<td>5</td>  
</tr>
<tr style="border-bottom: 1px solid #D6EEEE; padding: 5px 10px;">  
<td>Test Name</td>  
<td>Type</td>  
<td>15 kg</td>  
<td>0.3 m3</td>  
<td>5</td>  
</tr>
</table>

