## GetLastRowSpecial

The purpose of this function is to return the last row of the sheet that contains data.  This avoids getting the final row of the entire sheet returned as the last row due to full column arrays or calculation formulas being applied to a full row.

Check first column (typically timestamp of form submission) for last cell with data and return the row number as rowNum
**The row to be checked needs to be clear of full column array functions or other formula calculations that may make the system think that the row has data**

```
function getLastRowSpecial(range){
  var rowNum = 0;
  var blank = false;
  for(var row = 0; row < range.length; row++){
 
    if(range[row][0] === "" && !blank){
      rowNum = row;
      blank = true;
 
    }else if(range[row][0] !== ""){
      blank = false;
    };
  };
  return rowNum;
};
```
