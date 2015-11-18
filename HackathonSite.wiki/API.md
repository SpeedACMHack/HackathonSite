## Overview

### URLs
Development: Local VM

Staging: http://api.khe.pdilyard.com/v1.0

Production: https://api.khe.io/v1.0

### Routes, methods, and responses
The API is designed to stick as closely to the REST guidelines as possible, e.g.:
```javascript
POST /messages

HTTP/1.1 201 Created
```
This example uses the `POST` method to create a new `message` resource, and receives a `201 Created` status code in response. Check out the rest of the docs for more information.

### Error Handling
Every time an error occurrs, the response header will match the appropriate HTTP error code. The body of the response will contain an array of errors.

All errors are in the form of:
```javascript
HTTP 500 Internal Server Error
{
  "errors": [String]
}
```
Client errors are `4xx`, server errors are `5xx`.