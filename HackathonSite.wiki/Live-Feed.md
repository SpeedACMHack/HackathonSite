#### *Create a new message
```javascript
POST /messages
Auth -> admin, staff
{
  "text": String    // markdown
}

HTTP/1.1 201 Created
{
  "_id": String,
  "created": Date,
  "text": String
}
```

#### Get a list of messages
```javascript
GET /messages

HTTP/1.1 200 OK
{
  "messages": [{
    "_id": String,
    "created": Date,
    "text": String    // markdown
  }]
}
```

#### Get a single message
```javascript
GET /messages/:id

HTTP/1.1 200 OK
{
  "_id": String,
  "created": Date,
  "text": String    // markdown
}
```

#### *Update a message
```javascript
PATCH /messages/:id
Auth -> admin, staff
{
  "text": String
}

HTTP/1.1 200 OK
{
  "_id": String,
  "created": Date,
  "text": String
}
```

#### *Delete a message
```javascript
DELETE /messages/:id
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "_id": String
}
```