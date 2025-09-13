# 3. Mutations

Mutations are used to create, update, or delete data. Unlike queries, which only retrieve data, mutations alter it.

- There generally are three kinds of mutations:

  1. Creating new data
  2. Updating existing data
  3. Deleting existing data

## Defining Mutations

```graphql
type Mutation {
  createUser(name: String!, age: Int!): User
  updatePost(id: ID!, title: String!): Post
  deleteUser(id: ID!): User
  deletePost(id: ID!): Post
}
```

## _Usage Example:_

### 1. Create a new user

```graphql
mutation {
  createUser(name: "Bob", age: 25) {
    name
    age
  }
}
```

**_Output_:**

```json
{
  "data": {
    "createUser": {
      "name": "Bob",
      "age": 25
    }
  }
}
```

### 2. Update a post title

```graphql
mutation {
  updatePost(id: "101", title: "GraphQL for Beginners") {
    id
    title
  }
}
```

**_Output:_**

```json
{
  "data": {
    "updatePost": {
      "id": "101",
      "title": "GraphQL for Beginners"
    }
  }
}
```

### 3. Delete a User

```graphql
mutation {
  deletePost(id: "101") {
    id
    title
  }
}
```

**_Output:_**

```json
{
  "data": {
    "deleteUser": {
      "name": "Alice",
      "age": 30
    }
  }
}
```

### 4. Delete a post

```graphql
mutation {
  deletePost(id: "101") {
    id
    title
  }
}
```

**_Output_:**

```json
{
  "data": {
    "deletePost": {
      "id": "101",
      "title": "GraphQL Basics"
    }
  }
}
```

_Note:_

- Deletion mutations usually return the deleted object so the client knows what was removed.

- Some APIs may instead return a success flag, e.g., success: Boolean!.
