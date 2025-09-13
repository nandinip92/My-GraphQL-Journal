# Resolvers

Resolvers are functions that contain the logic to fetch, manipulate, or compute the data. They tell GraphQL How to fetch, manipulate or Compute data for a specific field in your schema. They “resolve” a query, mutation, or subscription by returning the requested data.

## Key Points

### **1. Field-Level Logic:**

- Every field in a type can have its own resolver.

- The resolver defines how to fetch or modify the data for that field.

Example:

```graphql
type User {
  id: ID
  name: String
  email: String
}
```

```javascript
// Javascript resolver
const resolvers = {
  User: {
    email: (parent) => parent.email.toLowerCase(), // custom logic for the email field
  },
};
```

**2. Resolvers for Queries, Mutations, and Subscriptions:**

- **_Query Resolvers:_** Fetch data (e.g., get a user).

```graphql
type Query {
  getUser(id: ID!): User
}
```

```javascript
//javascript resolver
const resolvers = {
  Query: {
    getUser: (parent, args) => database.getUserById(args.id),
  },
};
```

- **_Mutation Resolvers:_** Modify data (e.g., create or delete a user).

```graphql
type Mutation {
  createUser(name: String!, email: String!): User
}
```

```javascript
//javascript resolver
const resolvers = {
  Mutation: {
    createUser: (parent, args) => database.addUser(args),
  },
};
```

- **_Subscription Resolvers:_** Handle real-time updates (e.g., notify clients when new data is available).

```graphql
type Subscription {
  userAdded: User
}
```

```javascript
//javascript resolver
const resolvers = {
  Subscription: {
    userAdded: {
      subscribe: () => pubsub.asyncIterator(["USER_ADDED"]),
    },
  },
};
```

**3. Default Resolver:**

- If no resolver is provided for a field, GraphQL uses a default resolver.(simply returns the value if it exists in your data object)

- The default resolver simply returns the value if it exists in the parent data object

```javascript
const user = { id: 1, name: "Nandini", email: "nandini@example.com" };
// If no resolver is defined for 'name', GraphQL will return "Nandini" by default
```