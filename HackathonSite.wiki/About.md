#### *Create/update the about page
```javascript
PUT /about
Auth -> admin, staff
{
  "text": String    // markdown
}

HTTP/1.1 200 OK
{
  "_id": String,
  "updated": Date,
  "text": String
}
```

#### Retrieve the about page
```javascript
GET /about

HTTP/1.1 200 OK
{
  "_id": String,
  "text": String,
  "updated": Date
}
```