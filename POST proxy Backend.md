doPOST function to receive POST data from frontend app.  
Depending on the 'action' parameter received, different functions can be run to process the submitted data as needed.
```
function doPost(e) {
  if (e.parameter.action == "function1") {
    function1(e);
  } 
  if (e.parameter.action == "function2") {
    function2(e);
  }
    
}
```
