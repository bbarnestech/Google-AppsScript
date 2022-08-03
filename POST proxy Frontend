```
function processFormData(e) {
  //Create the payload to send via POST request
  var payload = {
  "contentType" : "application/x-www-form-urlencoded",
  "user" : "users name"
  "formdata" : "form data to be submitted"
  };
  //Get OAuth token
  var auth = ScriptApp.getOAuthToken();
  //Set options for POST request
  var options = {
    "method" : "POST",
    "payload" : payload,
    "headers" : {authorization: "Bearer " + auth}
  };
  //Send post request
  response = UrlFetchApp.fetch("url of backend app", options);
  
  //DO NOT REMOVE DRIVEAPP.GETFILES BELOW.  USED FOR API SCOPING PURPOSES
  //DriveApp.getFiles();
}
```  
