# Subscriptions (Optional but important)

Subscriptions provide real-time updates when data changes.

- While queries fetch data and mutations modify data, subscriptions allow clients to listen for events on the server and receive updates automatically.

- Useful for chat apps, live feeds, notifications, or any data that changes in real time.

- Using subscriptions makes your GraphQL API reactive, so the frontend always has the latest data without manually polling the server.

Think of it like a _websocket connection_ where the client subscribes to an event and gets notified whenever that event occurs.

**_Explaination:_**
Another important requirement for many applications today is to have a realtime connection to the server in order to get immediately informed about important events. For this use case, GraphQL offers the concept of subscriptions.

When a client subscribes to an event, it will initiate and hold a steady connection to the server. Whenever that particular event then actually happens, the server pushes the corresponding data to the client. Unlike queries and mutations that follow a typical “request-response-cycle”, subscriptions represent a stream of data sent over to the client.

## Defining a Subscription

Using our `Post` example

```graphql
type Subscription {
  postAdded: Post
  postDeleted: Post
}
```

**_Explanation:_**

- `postAdded` triggers when a new `Post` is created.

- `postDeleted` triggers when a `Post` is deleted.

- The client automatically receives the data for these events as they happen.

## Usage Example

### 1. Subscribe to new posts

```graphql
subscription {
  postAdded {
    id
    title
    content
  }
}
```

Whenever a new post is created using `createPost` mutation, the server sends the post data to **all subscribed clients**.

**_Example Real-Time Response:_**

```json
{
  "data": {
    "postAdded": {
      "id": "103",
      "title": "GraphQL Subscriptions",
      "content": "Learn how to use real-time updates in GraphQL"
    }
  }
}
```

### 2. Subscribe to deleted posts

```graphql
subscription {
  postDeleted {
    id
    title
  }
}
```

When a post is deleted using `deletePost`, the client automatically receives the info about the deleted post.
