# 1. Types

This is the blueprint. It doesn’t fetch or modify data by itself.

Types define the shape of the data-> fields and their types

```graphql
type User {
  name: String!
  age: Int!
  posts: [Post!]!
}

type Post {
  id: ID!
  title: String!
  content: String
}
```

**_Explanation:_**

- `User` and `Post` are types.

  - A `User` has a `name`, `age`, and a list of `posts`.

  - A `Post` has `id`, `title`, and optional `content`.

- Each field has a type, such as `String`, `Int`, or `ID`.

- `!` indicates that a field is required (cannot be null).

- `[Post!]!` means that `posts` is a list of `Post` objects, cannot be null, and each `Post` inside the list is also required.
