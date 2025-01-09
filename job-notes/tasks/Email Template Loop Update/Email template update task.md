Related with this task [[GPT solution of regex email template loop fn]]

```
// template code example:
<table>
<tr style="background-color: #D6EEEE;">
<th>Service</th>
<th>Price</th>
</tr>
{LOOP Booking__c.Services__r}
<tr style="border-bottom: 1px solid #D6EEEE;">
<td>ANNEX Certificate</td>
<td>90.00 €</td>
</tr>
{/LOOP}
</table>
```


Execute anonymous code:
```
/*String LOOP_REGEX = '\\{LOOP\\s*(\\w+\\.\\w+)\\}([\\s\\S]*?)\\{/LOOP\\}';
String LOOP_START_REGEX = '\\{LOOP\\s*(\\w+\\.\\w+)\\}';
String LOOP_END_REGEX = '\\{/LOOP\\}';

String test = '<table>\n'
    + '<tr style="background-color: #D6EEEE;">\n'
    + '<th>Service</th>\n'
    + '<th>Price</th>\n'
    + '</tr>\n'
    + '{LOOP Booking__c.Services__r}\n'
    + '<tr style="border-bottom: 1px solid #D6EEEE;">\n'
    + '<td>ANNEX Certificate</td>\n'
    + '<td>90.00 €</td>\n'
    + '</tr>\n'
    + '{/LOOP}\n'
    + '</table>';
System.debug(test);
// get loop block with regex
Matcher matcher = Pattern.compile(LOOP_REGEX).matcher(test);
while (matcher.find()) {
    System.debug(matcher.group());
}
// get loop start block with regex
matcher = Pattern.compile(LOOP_START_REGEX).matcher(test);
while (matcher.find()) {
    System.debug(matcher.group());
}
// get loop end block with regex
matcher = Pattern.compile(LOOP_END_REGEX).matcher(test);
while (matcher.find()) {
    System.debug(matcher.group());
}*/
String test = '<table>\n'
    + '<tr style="background-color: #D6EEEE;">\n'
    + '<th>Service</th>\n'
    + '<th>Price</th>\n'
    + '</tr>\n'
    + '{LOOP Booking__c.Services__r}\n'
    + '<tr style="border-bottom: 1px solid #D6EEEE;">\n'
    + '<td>ANNEX Certificate</td>\n'
    + '<td>90.00 €</td>\n'
    + '</tr>\n'
    + '{/LOOP}\n'
    + '</table>';
String testText = '{!Booking__c.RecordType.Name} {!Booking__c.Stakes__r[Purpose__c=\'Shipper\'].Account__r.Name}';
testText += test;
new DC_EmailTemplateServiceImpl().preselectFields(new List<String>{testText}, new Set<Id>{ 'a04Pt000001JUrRIAW' });
```

Email Template can have more than one loop pattern, so functionality should have map of parent object to map of related object to fields [[mapFieldsWithRegex.canvas|convas]]

How parse in this case: **Booking__c.Services__r.Service_Type__c**

{"Id":"a0DPt000003LjObMAK","Service_Type__c":"Air Freight","Price__c":"100"},{"Id":"a0DPt000003LjQDMA0","Service_Type__c":"Agent Fee","Price__c":"50"},{"Id":"a0DPt000003LjRpMAK","Service_Type__c":"COD (Change Of Destination)","Price__c":"123"}

{"RecordType":"[object Object]","Service_Type__c":"Air Freight","Price__c":"100"},{"RecordType":"[object Object]","Service_Type__c":"Agent Fee","Price__c":"50"}

Last Developer Console code:
```
/*
List<String> test = new List<String>();
String testt = String.join(test, ' or ');
System.debug(testt);
System.debug(testt == null);
System.debug(testt == '');
*/
/*
Set<Id> bookingIds = new Set<Id>{ 'a04Pt000001JUrRIAW' };
String test = '{!Booking__c.RecordType.Name} {!Booking__c.Stakes__r[Purpose__c=\'Shipper\'].Account__r.Name}\n'
    + '{!Booking__c.Services__r[RecordType.Name=\'Planned Income\'].Price__c}\n'
    + '<table>\n'
    + '<tr style="background-color: #D6EEEE;">\n'
    + '<th>Service</th>\n'
    + '<th>Price</th>\n'
    + '</tr>\n'
    + '{LOOP Booking__c.Services__r[RecordType.Name=\'Planned Income\']}'
    + '<tr style="border-bottom: 1px solid #D6EEEE;">\n'
    + '<td>{!this.Service_Type__c}</td>\n'
    + '<td>{!this.Price__c} €</td>\n'
    + '</tr>\n'
    + '{/LOOP}'
    + '</table>';
DC_EmailTemplateServiceImpl impl = new DC_EmailTemplateServiceImpl();
impl.preselectFields(new List<String>{ test }, bookingIds);
String test1 = impl.parseEmailTemplate(test, bookingIds);
System.debug(test1);
*/
Set<Id> accIds = new Set<Id>{ '001Pt00000FQ6VsIAL' };
String test = '{LOOP Account.Contacts[LastName=\'Test\']}FirstName: {!this.FirstName}, LastName: {!this.LastName}\n{/LOOP}';
DC_EmailTemplateServiceImpl impl = new DC_EmailTemplateServiceImpl();
impl.preselectFields(new List<String>{ test }, accIds);
String test1 = impl.parseEmailTemplate(test, accIds);
System.debug(test1);
```

