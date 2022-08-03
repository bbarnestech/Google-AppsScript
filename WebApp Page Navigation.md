
doGet function that returns evaluated named page if e.parameter.page = the pages name
Save 'property1' as user parameter for use elsewhere within the app
Else returns the landing page (in this example the landing pages name is 'landing_page')
```
function doGet(e) {
  Logger.log( Utilities.jsonStringify(e) );
  //If page parameter doesn't exist, load 'landing_page'
  if (!e.parameter.page) {
    return HtmlService.createTemplateFromFile('landing_page').evaluate();
  }
  //If page has additional parameters such as 'property1', set parameter as user property for use elsewhere within app
  if (e.parameter.page == 'page_with_parameters') {
    userProperties.setProperty('property1', e.parameter.property1);
    return HtmlService.createTemplateFromFile(e.parameter['page']).evaluate();
  } else {
    return HtmlService.createTemplateFromFile(e.parameter['page']).evaluate();
  }
}
```


getScriptUrl function to get and return the current webapps script URL for use with navigation buttons or links
The desired page name is appended to the URL in a link or button elsewhere in the app.  (ex. '<?!=url?>?page=another_page')
```
function getScriptUrl() {
  var url = ScriptApp.getService().getUrl();
  return url;
}
```


HTML sample of button (wrapped in anchor tags for url generation) that navigates to a page named 'another_page' if the page exists
```
<HTML>
<a <?var url = getScriptUrl();?> href='<?!=url?>?page=another_page';><button type="button">Navigate to Another Page</button></a>
```
