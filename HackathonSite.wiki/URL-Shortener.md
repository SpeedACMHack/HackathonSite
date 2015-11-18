#### *Create a new shortened URL
```javascript
POST /urls
Auth -> admin, staff
{
  "full": String,   // the full length URL
  "short": String   // the shortened key
}

HTTP/1.1 201 Created
{
  "_id": String,
  "full": String,
  "short": String
}
```

#### Resolve a shortened URL
```javascript
GET /urls/go/:short

HTTP/1.1 301 Moved Permanently
```

#### Get a single URL
```javascript
GET /urls/:id
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "_id": String,
  "full": String,
  "short": String
}
```

#### Get a list of URLs
```javascript
GET /urls
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "urls": [{
    "_id": String,
    "full": String,
    "short": String
  }]
}
```

#### *Delete a URL
```javascript
DELETE /urls/:id
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "_id": String
}
```