### POST proxy method of writing data to a protected spreadsheet without granting the app end user write access to the spreadsheet.

*2 separate Apps Scripts are required.*  

1. Front end app
    - https://github.com/bbarnestech/Google-AppsScript/blob/main/POST%20proxy%20Frontend.md
    - Contains the user front end app such as an HTML form.  The app submits form data by sending as a POST payload to the back end app.
    - App runs under the context of the end user.
  
2. Back end app
    - https://github.com/bbarnestech/Google-AppsScript/blob/main/POST%20proxy%20Backend.md
    - Contains doPost function to receive POST data from front end app.  Received data is processed under the context of a user with write access to the protected spreadsheet
    - App runs under the context of a user with write access to the protected spreadsheet

