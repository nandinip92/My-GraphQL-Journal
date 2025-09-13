# 2. Queries

**Purpose:** They tell the API what information the client needs.

Queries are the entry points for reading data.They **only read data**; they do not change anything.

## Defining Query

```graphql
type Query {
  getUser(id: ID!): User
  getAllPosts: [Post!]!
}
```

**_Explaination:_**

- `getUser` fetches a `User` by their `id`.

- `getAllPosts` fetches all Post objects.

## _Usage Examples:_

You can request data based on these types.

### 1. Get the data of User and title of that users posts

```graphql
query {
  getUser(id: "1") {
    name
    age
    posts {
      title
    }
  }
}
```

**_What happens:_**

- Fetches a `User` with `id = 1`.

- Returns the `name`, `age`, and `titles` of all their posts.

- Output might look like:

  ```json
  {
    "data": {
      "getUser": {
        "name": "Alice",
        "age": 30,
        "posts": [
          { "title": "GraphQL Basics" },
          { "title": "Advanced GraphQL" }
        ]
      }
    }
  }
  ```

### 2. Get specific user by ID

```graphql
query {
  getUser(id: "1") {
    name
    age
  }
}
```

**_Output:_**

```json
{
  "data": {
    "getUser": {
      "name": "Alice",
      "age": 30
    }
  }
}
```

### 3. Get all posts

```graphql
query {
  getAllPosts {
    id
    title
  }
}
```

**_Output:_**

```json
{
  "data": {
    "getAllPosts": [
      { "id": "101", "title": "GraphQL Basics" },
      { "id": "102", "title": "Advanced GraphQL" }
    ]
  }
}
```
