#### Download a CSV of all applied attendees
You can also add a query string to the URL that matches against the application model.
```javascript
GET /exports/attendees?checked=true

HTTP/1.1 200 OK
// CSV
```

#### Download a resume book
```javascript
GET /exports/resumes

HTTP/1.1 200 OK
// Downloads a ZIP of all resume files
```