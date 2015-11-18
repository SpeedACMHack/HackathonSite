#### *Add a new event
```javascript
POST /events
Auth -> admin
{
  "title": String,       // required
  "description": String,
  "start": Date,         // required
  "end": Date,           // required
  "type": String,
  "icon": String,
  "location": String,
  "group": String,
  "notify": Boolean
}

HTTP/1.1 201 Created
{
  "_id": String,
  "title": String,
  "description": String,
  "start": Date,
  "end": Date,
  "type": String,
  "icon": String,
  "location": String,
  "group": String,
  "notify": Boolean
}
```

#### Get an event by ID
```javascript
GET /events/:id

HTTP/1.1 200 OK
{
  "_id": String,
  "title": String,
  "description": String,
  "start": Date,
  "end": Date,
  "type": String,
  "icon": String,
  "location": String,
  "group": String,
  "notify": Boolean
}
```

#### Get a list of events
Add the query string `?icons=true` at the end to fetch a list of pre-built icon URLs.
```javascript
GET /events

HTTP/1.1 200 OK
{
  "events": [{
    "_id": String,
    "title": String,
    "description": String,
    "start": Date,
    "end": Date,
    "type": String,
    "icon": String,
    "location": String,
    "group": String,
    "notify": Boolean
  }]
}
```

#### *Partially update an event
```javascript
PATCH /events/:id
Auth -> admin
{ // all fields optional
  "title": String,
  "description": String,
  "start": Date,
  "end": Date,
  "type": String,
  "icon": String,
  "location": String,
  "group": String,
  "notify": Boolean
}

HTTP/1.1 200 OK
{
  "_id": String,
  "title": String,
  "description": String,
  "start": Date,
  "end": Date,
  "type": String,
  "icon": String,
  "location": String,
  "group": String,
  "notify": Boolean
}
```

#### *Delete an event
```javascript
DELETE /events/:id
Auth -> admin

HTTP/1.1 200 OK
{
  "_id": String
}
```