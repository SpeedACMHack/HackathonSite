#### *Create a new user
```javascript
POST /users
{
  "email": String,
  "password": String
}

HTTP/1.1 201 Created
{
  "key": String,
  "token": String,
  "role": String
}
```

#### *Quickly create a fully applied user (for registering at the door)
```javascript
POST /users/quick
Auth -> admin, staff
{
  "name": String,   // full name
  "email": String,  // email address
  "phone": String   // phone number
}

HTTP/1.1 201 Created
{
  "_id": String,
  "email": String,
  "role": String,
  "created": Date,
  "application": {
    "name": String,
    "school": String,
    "phone": String,
    "shirt": String,
    "demographic": Boolean,
    "first": Boolean,
    "dietary": String,
    "year": String,
    "age": Number,
    "gender": String,
    "major": String,
    "conduct": Boolean,
    "travel": Boolean,
    "waiver": Boolean,
    "status": String,
    "going": Boolean,
    "checked": Boolean,
    "created": Date,
    "door": Boolean
  }
}
```

#### Get a key and token
```javascript
POST /users/token
{
  "email": String,
  "password": String
}

HTTP/1.1 201 Created
{
  "key": String,
  "token": String,
  "role": String
}
```

#### Remove a token
```javascript
DELETE /users/token
Auth

HTTP/1.1 200 OK
```

#### Get a list of all users
```javascript
GET /users
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "users": [{
    "_id": String,
    "email": String,
    "role": String,
    "created": Date
  }]
}
```

#### Get a user by ID
```javascript
GET /users/:id
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "_id": String,
  "email": String,
  "role": String,
  "created": Date
}
```

#### *Partially update the logged in user
```javascript
PATCH /users
Auth
{
  "email": String,
  "password": String
}

HTTP/1.1 200 OK
{
  "_id": String,
  "email": String
}
```

#### *Partially update a user by ID
```javascript
PATCH /users/:id
Auth -> admin
{
  "role": 'attendee'|'staff'|'admin'
}

HTTP/1.1 200 OK
{
  "_id": String,
  "email": String,
  "role": String,
  "created": String
}
```

#### *Delete a user
```javascript
DELETE /users/:id
Auth -> admin

HTTP/1.1 200 OK
{
  "_id": String
}
```

#### Reset a password
This will send an email with a randomly generated new password to the user
```javascript
POST /users/reset
{
  "email": String
}

HTTP/1.1 200 OK
{}
```