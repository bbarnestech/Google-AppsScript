Create a unique ID number for each form submission in a Google Forms repsonse Sheet.

&nbsp;
For the purposes of this example a common item number prefix is stored in cell S1 (FY01-) and a number stored in cell T1 (0001).  The number of digits for the number in T1 can be controlled via cell formatting.

&nbsp;
The getLastRowSpecial function can be found [HERE - GetLastRow_Special](https://github.com/bbarnestech/Google-AppsScript/blob/main/GetLastRow_Special)


```
function onFormSubmit()
{
  let ss = SpreadsheetApp.getActiveSpreadsheet();
  let sheet = ss.getSheetByName("Form Responses 1");
  let columnToCheck = sheet.getRange("A:A").getValues();
  let lastRow = getLastRowSpecial(columnToCheck);
	
  //bugCount is next available request number
	let bugCount = ss.getRange("T1").getDisplayValue();
  //requestPrefix is the request number prefix such as FY##-
  let requestPrefix = ss.getRange("S1").getDisplayValue();
	
  //set unique ID to last cell in the second column of the sheet and increment number in cell T1
	sheet.getRange(lastRow,2).setValue(requestPrefix + bugCount);
  bugCount++;
	sheet.getRange("T1").setValue(bugCount);
};
```
This code should produce unique number FY01-0001 and increment the number in T1 to 0002 for next usage. 
