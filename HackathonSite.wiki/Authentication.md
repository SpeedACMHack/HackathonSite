User authentication is an important aspect of the API. We are using HTTP Basic Authentication headers to send a key and a token to the backend. The first step is to get a key, token, refresh token, and expiration token. Then, clients should use the key and token to make requests to parts of the API that require verification. Be careful, because access tokens expire after a relatively short period of time. It is important to refresh tokens before they expire. Follow the steps below to implement authentication in your client.

## Step 1: Get an access token
Access tokens can come from two endpoints in the API: `POST /users` and `POST /users/token`. Here is an example of getting an access token by posting to `/users/token` (this is how users will log in).

```javascript
// Request:
POST /users/token HTTP/1.1
{
  client: String,   // your client ID
  email: String,    // the user's email address
  password: String  // the user's password
}

// Response:
HTTP/1.1 200 OK
{
  role: String,     // the user's role
  key: String,      // an access key
  token: String,    // an access token
  refresh: String,  // a refresh token
  expires: Date     // a timestamp representing the time at which the token expires
}
```

Store all of the data in this response on your client. You will be using the `key` and `token` to make future requests on behalf of the logged in user.

## Step 2: Make requests with the access token
Now that you have obtained a key and token, you can make requests on behalf of the user. To do this, you need to send an `Authorization` header. To set up the authorization header, just concatenate the key and token with a colon, then base-64 encode the result:

```
encoded = base64Encode(key + ":" + token)
```

Finally, add the header to your requests. Here's an example of a authorized request to `PATCH /users`:

```javascript
// Request:
PATCH /users HTTP/1.1
Authorization: Basic YWdpZXJnaWVyb2dpMjM0MjQ=
{
  "email": String
}
```

On the backend, that header will be parsed and used to ensure that the user is authorizing each request.

## Step 3: Refreshing a token
Every so often (e.g. a couple weeks), access tokens will expire. This is a security measure to ensure that stolen tokens don't last too long. On the client side, you will have to take measures to refresh tokens before they expire. In Step 1, we received a token expiration date. All you have to do is make sure you make the following request before that date passes.

```javascript
// Request:
POST /users/token/refresh HTTP/1.1
{
  client: String,   // your client ID
  key: String,      // the user's key
  refresh: String   // the refresh token
}

// Response:
HTTP/1.1 200 OK
{
  key: String,
  token: String,
  refresh: String,
  expires: Date
}
```

Just replace your currently saved values with the new values you receive from the token refresh.

## Deleting a token
If the user would like to completely logout of your application, it is safest to delete their access token. This is a very simple request:

```javascript
DELETE /users/token HTTP/1.1
Authorization: Basic YWdpZXJnaWVyb2dpMjM0MjQ=
{
  client: String   // your client ID
}
```