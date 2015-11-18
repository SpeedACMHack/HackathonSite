#### *Create a new ticket
```javascript
POST /tickets
{
  "subject": String,
  "body": String,
  "replyTo": String,
  "name": String
}

HTTP/1.1 201 Created
{
  "_id": String,
  "subject": String,
  "body": String,
  "replyTo": String,
  "name": String,
  "worker": String,
  "open": Boolean,
  "inProgress": Boolean,
  "created": Date
}
```

#### Get a list of tickets
```javascript
GET /tickets
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "tickets": [{
    "_id": String,
    "subject": String,
    "body": String,
    "replyTo": String,
    "name": String,
    "worker": String,
    "open": Boolean,
    "inProgress": Boolean,
    "created": Date
  }]
}
```

#### Get a ticket by ID
```javascript
GET /tickets/:id
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "_id": String,
  "subject": String,
  "body": String,
  "replyTo": String,
  "name": String,
  "worker": String,
  "open": Boolean,
  "inProgress": Boolean,
  "created": Date
}
```

#### *Partially update a ticket
```javascript
PATCH /tickets/:id
Auth -> admin, staff
{
  "open": false
}

HTTP/1.1 200 OK
{
  "_id": String,
  "subject": String,
  "body": String,
  "replyTo": String,
  "name": String,
  "worker": String,
  "open": Boolean,
  "inProgress": Boolean,
  "created": Date
}
```

#### *Delete a ticket
```javascript
DELETE /tickets/:id
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "_id": String
}
```