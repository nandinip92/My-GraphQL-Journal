# Core Concepts of GraphQL

Following are the core concepts of the GraphQL

## 1. Schema

Before starting to build your server, GraphQL requires you to design a schema which in turn defines the API of your server.

In GraphQL, the schema is the backbone of your API. It acts as a contract between the client (frontend) and the server (backend), defining exactly what data can be queried and how.

**Purpose of the Schema:**

- The schema defines the structure of the API → it’s the blueprint of the GraphQL API.

- It specifies what data is available to the clients → it tells the client what types of objects (like `User`, `Post`) exist and what fields they can access.

  **_Example_**: if a schema defines `User` with `name` and `age`, clients cannot query a `password` field if it’s not exposed in the schema.

**Schema definition Language(SDL):**

GraphQL has its own type language that’s used the write GraphQL schemas: **_The Schema Definition Language (SDL)_**. In its simplest form, GraphQL SDL can be used to define types looking like this:

```graphql
type Person {
  name: String!
  age: Int!
}
```

This type has two fields, they’re called `name` and `age` and are respectively of type `String` and `Int`. The `!` following the type means that this field is required.

**Components Described by the Schema:**

The schema describes the types, queries, mutations, and subscriptions available in the API:

1. [Types](/CoreConcepts/1_Types.md) → Define the shape of the data (e.g., `User` has `id`, `name`, `email`).

2. [Queries](/CoreConcepts/2_Queries.md) → Define what clients can **read** from the API (e.g., `getUser`, `getPosts`).

3. [Mutations](/CoreConcepts/3_Mutations.md) → Define what clients can **write** or **change** in the API (e.g., `createUser`, `updatePost`).

4. [Subscriptions](/CoreConcepts/4_Subscriptions.md) → Enable clients to receive **real-time updates** when data changes.

```sql
Schema [Blueprint of API]
 ├── Types       [shape of data]
 ├── Query       [read data]
 ├── Mutation    [write/change data]
 └── Subscription [real-time updates]
```

## 2. Resolvers

**Resolvers** are **functions** that tell GraphQL **how to fetch or manipulate the data** for a specific field in your schema.

- Every field in a type can have a resolver.

- A resolver resolves the data requested in a query, mutation, or subscription.

- If you don’t provide a resolver, GraphQL uses a default resolver (simply returns the value if it exists in your data object).

#### 👉Click to learn more about [Resolvers](/CoreConcepts/Resolvers.md)

**_InSimpleaWords:_** Resolvers are the bridge between schema and data sources, defining how each field’s data is fetched or manipulated, whether using custom logic or the default behavior.

## 3. Root

Root (also called as RootType or RootValue) are the entry points for GraphQL operations:

- Query Root → entry point for all queries (Query type).

- Mutation Root → entry point for all mutations (Mutation type).

- Subscription Root → entry point for all subscriptions (Subscription type).

Think of them as the top-level “object” GraphQL uses to start execution.

- Each top-level field in Query or Mutation has a corresponding resolver.

- The root value is the object that contains these resolver functions.

#### 👉Click to learn more about [Root](/CoreConcepts/Root.md)

---

## Summary of Everything Together— Types,Queries and Resolvers

Following is the example with [Types](/CoreConcepts/1_Types.md), [Queries](/CoreConcepts/2_Queries.md) and [Mutations](/CoreConcepts/3_Mutations.md) everthing together:

```graphql
# Define a "User" type
type User {
  id: ID!
  name: String!
  email: String!
  posts: [Post!]!
}

# Define a "Post" type
type Post {
  id: ID!
  title: String!
  content: String
  author: User!
}

# Root Query type: defines what clients can request
type Query {
  getUser(id: ID!): User
  getPosts: [Post!]!
}

# Root Mutation type: defines what clients can change
type Mutation {
  createUser(name: String!, email: String!): User
  createPost(title: String!, content: String, authorId: ID!): Post
  updatePost(id: ID!, title: String!): Post
  deleteUser(id: ID!): User
  deletePost(id: ID!): Post
}
```

### Summary

```
Schema (Blueprint of API)
 ├── Types       (shape of data)
 ├── Query       (read data)
 ├── Mutation    (write/change data)
 └── Subscription (real-time updates)

Resolvers = Functions that fetch/modify data
Root Object = Entry point connecting schema fields to resolvers
```

---

**Resources**

👉[How to graphql](https://www.howtographql.com/basics/2-core-concepts/)

👉[GraphQL SDL](https://www.prisma.io/blog/graphql-sdl-schema-definition-language-6755bcb9ce51)

👉[GraphQL Server Basics (Part I): GraphQL Schemas, TypeDefs & Resolvers Explained](https://www.prisma.io/blog/graphql-server-basics-the-schema-ac5e2950214e)

---
