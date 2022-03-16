Javascript that prevents forms from submitting via the normal html method.

```
// Prevent forms from submitting.
  function preventFormSubmit() {
    var forms = document.querySelectorAll('form');
    for (var i = 0; i < forms.length; i++) {
      forms[i].addEventListener('submit', function(event) {
      event.preventDefault();
      });
    }
  }
  window.addEventListener('load', preventFormSubmit);
```

Handles form submissions by passing form data to processForm function for processing.  From the processForm function you may manipulate and pass the data as needed.  For example data can be passed to a spreadsheet for logging.

```      
  function handleFormSubmit(formObject) {
    google.script.run.processForm(formObject);
    document.getElementById('myForm').reset();
    var form = document.getElementById('myForm');
    form.style.display='none';
  }
```
