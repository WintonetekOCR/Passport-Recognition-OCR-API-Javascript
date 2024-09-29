## Features
- Extracts vital passport details, including passport number, name, nationality, date of birth, and expiration date.
- MRZ (Machine Readable Zone) support for multiple passport types.
- Lightweight and fast, optimized for deployment in both browser and Node.js environments.
- Provides a simple RESTful API for easy integration into web applications.
- Cross-platform: works in browser, Node.js, and other environments that support JavaScript.
- Easily extendable to recognize other identity documents.

## Technologies Used

- **JavaScript/TypeScript**: Backend and API implementation.
- **Tesseract.js**: JavaScript-based OCR engine.
- **Express.js**: Lightweight framework to create the API (if using Node.js).
- **Jimp**: Image processing for better OCR results.
- **Docker**: For easy deployment in production environments.

## How to Use
```
const crypto = require('crypto');
const FormData = require('form-data');
const $ = require('jquery');

var key = "M***********g";
var secret = "3***********6";
var timestamp = Date.now();

var token = crypto.createHash('md5').update(key + "+" + timestamp + "+" + secret).digest('hex');

var form = new FormData();
form.append("key", key);
form.append("typeId", "13");
form.append("timestamp", String(timestamp));
form.append("token", token);
form.append("img", "/9j");

var settings = {
 "url": "https://flyocr.com/api/recogliu.do",
 "method": "POST",
 "timeout": 0,
 "processData": false,
 "mimeType": "multipart/form-data",
 "contentType": false,
 "data": form,
 "success": function(response) {
     console.log(response);
 },
 "error": function(xhr, status, error) {
     console.error(status, error);
 }
};

$.ajax(settings);
```
