#### *Create an application
```javascript
POST /users/application
Auth
{
  "name": String,           // full name
  "school": String,         // name of school
  "phone": String,          // phone number
  "shirt": String,          // t-shirt size
  "demographic": Boolean,   // allowed to use demographic info?
  "first": Boolean,         // is this your first hackathon?
  "dietary": String,        // food restrictions seperated by |
  "year": String,           // the year in school
  "age": Number,            // person's age
  "gender": String,         // gender
  "major": String,          // degree
  "conduct": Boolean,       // agree to MLH code of conduct?
  "travel": Boolean,        // need travel reimbursement?
  "waiver": Boolean,        // agreed to waiver?
  "resume": String,         // the filename of their resume
  "link": String            // a github/linkedin link
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
    "dietary": [String],
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
    "door": Boolean,
    "resume": String,
    "link": String
  }
}
```

#### Get the logged in user with their application
```javascript
GET /users/me/application
Auth

HTTP/1.1 200 OK
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
    "dietary": [String],
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
    "door": Boolean,
    "resume": String,
    "link": String
  }
}
```

#### Get a user by ID with their application
```javascript
GET /users/:id/application
Auth -> admin, staff

HTTP/1.1 200 OK
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
    "dietary": [String],
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
    "door": Boolean,
    "resume": String,
    "link": String
  }
}
```

#### Get a list of users with their applications
```javascript
GET /users/application
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "users": [{
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
      "dietary": [String],
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
      "door": Boolean,
      "resume": String,
      "link": String
    }
  }]
}
```

#### *Update the logged in user's application
```javascript
PATCH /users/me/application
Auth
{
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
  "resume": String,
  "link": String
}

HTTP/1.1 200 OK
{
  "_id": String,
  "email": String,
  "role": String,
  "created": String,
  "application": {
    "name": String,
    "school": String,
    "phone": String,
    "shirt": String,
    "demographic": Boolean,
    "first": Boolean,
    "dietary": [String],
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
    "door": Boolean,
    "resume": String,
    "link": String
  }
}
```

#### *Partially update a user's application by ID
```javascript
PATCH /users/:id/application
Auth -> admin, staff
// All fields optional
{
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
  "resume": String,
  "link": String
}

HTTP/1.1 200 OK
{
  "_id": String,
  "email": String,
  "role": String,
  "created": String,
  "application": {
    "name": String,
    "school": String,
    "phone": String,
    "shirt": String,
    "demographic": Boolean,
    "first": Boolean,
    "dietary": [String],
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
    "door": Boolean,
    "resume": String,
    "link": String
  }
}
```

#### *Delete the logged in user's application
```javascript
DELETE /users/me/application
Auth

HTTP/1.1 200 OK
{
  "_id": String
}
```

#### *Delete a user's application by ID
```javascript
DELETE /users/:id/application
Auth -> admin, staff

HTTP/1.1 200 OK
{
  "_id": String
}
```

#### Upload a resume
```javascript
POST /users/application/resume
{
  "resume": File   // A PDF or .docx
}

HTTP/1.1 200 OK
{
  "filename": String   // use this to update the user's application object
}
```

#### Download a resume
```javascript
GET /users/application/resume/:filename

HTTP/1.1 200 OK
// Response will be the file download
```