#### *Create a new email (and send it)
```javascript
POST /emails
Auth -> admin
{
  "subject": String,
  "body": String, // markdown formatted
  "recipients": {
    "nickname": String, // optional, a nickname for this group of people
    "emails": [String]
  }
}

HTTP/1.1 201 Created
{
  "_id": String
  "subject": String,
  "body": String, // markdown formatted
  "recipients": {
    "nickname": String, // optional, a nickname for this group of people
    "emails": [String]
  }
}
```

#### Get a list of sent emails
```javascript
GET /emails
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "emails": [{
    "_id": String,
    "subject": String,
    "sent": Date,
    "body": String, // markdown formatted
    "recipients": {
      "nickname": String, // if a nickname was provided
      "emails": [String] // if a nickname was not provided
    }
  }]
}
```

#### *Delete a sent email
```javascript
DELETE /emails/:id
Auth -> admin

HTTP/1.1 200 OK
{
  "_id": String
}
```