### Overview
We are using [Socket.IO](http://socket.io/) to get live updates on resources coming from the API. This can be used for any apps that need to keep up to date on a given resource. The [staff frontend](https://github.com/hacksu/kenthackenough-ui-staff) and the "live" page on the [main site](https://github.com/hacksu/kenthackenough-ui-main) use web sockets heavily.

### Documentation
To connect from a  client to a given resource:
```javascript
io.connect(API_URL + '/resource');
```
This connection will work for any resources with public read access. To get live updates on resources that require authentication:
```javascript
io.connect(API_URL + '/resource', {
  query: 'authorization=BASE64_ENCODED_KEY_TOKEN'
});
```

Rather than documenting the entire socket API here, I've just added a bit of information to the main API docs. Any route that can be listened to on with a socket is preceded by an asterisk in the API docs. For example, in the [Live Feed](Live-Feed) docs, we have "*Create a new message", "*Update a message", and "*Delete a message". We can see on that page that we don't have to be authenticated to make a `GET` request to `/messages`. Therefore, we have public read access. If we want to set up a Socket.IO client that watches the messages resource, we just do the following:

```javascript
let io = require('socket.io'); // or however we are getting the socket client library
io.connect(API_URL + '/messages');

io.on('create', (message) => {
  // a new message has been created
});

io.on('update', (message) => {
  // the message has been updated
});

io.on('delete', (message) => {
  // the message has been deleted (we have message._id)
});
```
The `message` parameter passed to the client is an exact match to the response that you would get from the coordinating HTTP method.