### Insert image from Google Drive when generating PDF from HTML template

PDF_Template.html
```
<!DOCTYPE html>
<html>
  <head>
    <base target="_top">
  </head>
  <body>
    <img src='data:<?= imageData ?>' width='106' height='50' alt='SampleImage'/>
  </body>
</html>
```

Function to inject image and create PDF from template file as email attachment
```
function generatePDF() {
  var htmlTemplate = HtmlService.createTemplateFromFile("PDF_Template");
  var fileIdOfImage = "ID of image file stored in google drive";
  var imageBlob = DriveApp.getFileById(fileIdOfImage).getBlob();
  htmlTemplate.imageData = imageBlob.getContentType() + ';base64,' + Utilities.base64Encode(imageBlob.getBytes());
  var htmlContent = htmlTemplate.evaluate().getContent();
  var blob = Utilities.newBlob(htmlContent,MimeType.HTML);
  blob.setName("test.pdf");
  MailApp.sendEmail({
    to: "recipeint@email.address",
    subject: "PDF Image Generation",
    htmlBody: "Please see attached PDF file",
    attachments: [blob.getAs(MimeType.PDF)],
    noReply: true
  });
}
```
