# Root

The root (or rootValue) is an object that acts as the starting point for resolving queries. When a query or mutation is sent to the GraphQL server, it refers to the resolvers defined in the root to execute the operation.

In GraphQL, the root (also called RootValue or RootType) is the entry point for executing queries, mutations, or subscriptions. Think of it as the object that contains all the top-level functions (resolvers) that GraphQL can call when a query starts.

- RootValue is usually an object whose keys are the top-level fields in your schema.

- Each key points to a function (resolver) that knows how to get the data for that field.

## Simple Example

Suppose we have a GraphQL schema like this:

```graphql
type Query {
  hello: String
  user(id: ID!): User
}

type User {
  id: ID
  name: String
}
```

Here:

- `Query` is the root type for queries.

- `hello` and `user` are top-level fields.

- The **resolvers** for these fields live in the root object.

## Resolver / RootValue Example in Express.js

```javascript
const { graphqlHTTP } = require("express-graphql");
const { buildSchema } = require("graphql");
const express = require("express");

const schema = buildSchema(`
  type Query {
    hello: String
    user(id: ID!): User
  }

  type User {
    id: ID
    name: String
  }
`);

// RootValue object (top-level resolvers)
const root = {
  hello: () => {
    return "Hello, GraphQL!";
  },
  user: ({ id }) => {
    const users = [
      { id: "1", name: "Alice" },
      { id: "2", name: "Bob" },
    ];
    return users.find((user) => user.id === id);
  },
};

const app = express();
app.use(
  "/graphql",
  graphqlHTTP({
    schema: schema,
    rootValue: root, // <-- This is where root is used
    graphiql: true,
  })
);

app.listen(4000, () =>
  console.log("Server running on http://localhost:4000/graphql")
);
```

## How it works?

1. Client sends a query:

```graphql
{
  hello
  user(id: "1") {
    name
  }
}
```
2. GraphQL looks at the rootValue:

- Calls root.hello() → returns "Hello, GraphQL!"

- Calls root.user({ id: "1" }) → returns { id: "1", name: "Alice" }

3. Response sent back:

```json
{
  "data": {
    "hello": "Hello, GraphQL!",
    "user": {
      "name": "Alice"
    }
  }
}
```

---

**References**

https://graphql.org/learn/execution/
