#### *Add an email to the list
```javascript
POST /news
{
  "email": String
}

HTTP/1.1 201 Created
{
  "_id": String,
  "email": String,
  "created": String
}
```

#### Get a single email from the list
```javascript
GET /news/:id
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "_id": String,
  "email": String,
  "created": String
}
```

#### Get a list of emails on the list
```javascript
GET /news
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "news": [{
    "_id": String,
    "email": String,
    "created": String
  }]
}
```

#### *Delete an email from the list
```javascript
DELETE /news/:id
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "_id": String
}
```