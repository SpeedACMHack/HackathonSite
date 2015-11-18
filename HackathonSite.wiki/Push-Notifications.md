### Overview

We are using [Google Cloud Messaging](https://developers.google.com/cloud-messaging/) for push notifications. The API for push notifications is designed to be as close to the API for web sockets as possible, which is in turn designed to be as close to the HTTP API as possible :) Hopefully this means they're all fun to work with.

In order to keep it simple, we're using the [topic messaging](https://developers.google.com/cloud-messaging/topic-messaging) features of GCM. **Only resources with public read access are allowed to have a GCM topic** (because there isn't a great way to authorize subscriptions to a GCM topic). Currently, that means there are two topics: `messages` and `events`.

So, to get push notifications for messages, you need to [subscribe to the messages topic](https://developers.google.com/cloud-messaging/topic-messaging#subscribe-to-a-topic). When a GCM push is sent, it gets data attached. The data contains two important keys: `action` and `document`. The `action` tells you what you should do with the `document` (create, update, delete, notify). The `document` is the full JSON document of the resource being acted on.

### Documentation

#### Messages
```javascript
topic: "/topics/messages"
action: "create|update|delete"
document: {Message}
```

#### Events
```javascript
topic: "/topics/events"
action: "create|update|delete|notify"
document: {Event}
```