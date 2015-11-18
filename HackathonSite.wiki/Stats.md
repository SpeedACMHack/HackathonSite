#### Number of people registered each month
```javascript
GET /stats/registrations
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "months": [{
    "name": String,  // the name of the month
    "count": Number  // the number of registrations in that month
  }]
}
```

#### Get the t-shirt size distribution
```javascript
GET /stats/shirts
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "small": Number,
  "medium": Number,
  "large": Number,
  "xlarge": Number 
}
```

#### Get the distribution of dietary restrictions
```javascript
GET /stats/dietary
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "restrictions": [{
    "name": String,  // the name of a dietary restriction
    "count": Number  // the number of people with that restriction
  }]
}
```

#### Get a gender comparison
```javascript
GET /stats/gender
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "male": Number,
  "female": Number,
  "other": Number
}
```

#### Get a distribution of schools
```javascript
GET /stats/schools
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "schools": [{
    "name": String,
    "count": Number
  }]
}
```

#### Get the number of applied attendees
```javascript
GET /stats/count
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "count": Number
}
```

#### Queries
You can also query all of the `/stats` routes by adding your query to the request URI, like this:
```
GET /stats/gender?checked=true
```
The above will return the gender distribution of attendees who are checked in. You can run queries against any property in the Application model.