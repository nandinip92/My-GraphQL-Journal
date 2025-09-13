## What is GraphQL?

GraphQL is a query language and runtime for APIs that allows clients to request exactly the data they need. Unlike traditional REST APIs, which often return too much or too little information, GraphQL prevents over-fetching (getting unnecessary data) and under-fetching (not getting enough data, requiring multiple requests).

**Query language:** Defines the syntax to specify exactly what data the client wants.

**Runtime:** The server-side engine that interprets queries, fetches the requested data, and assembles the response dynamically. This means GraphQL doesn’t return predefined responses like REST; it constructs the data on the fly.

#### Limitations of REST APIs:

- **Over-fetching:** REST endpoints often return more data than needed, wasting bandwidth and slowing down the app.
- **Under-fetching:** Sometimes, you need data from multiple endpoints, requiring multiple requests.
- **Fixed structure:** REST responses are predefined by the server, giving less flexibility for the client.

#### How GraphQL is different:

- **Precise queries:** Clients can request only the fields they need.
- **Single request** for multiple resources: Related data can be fetched in one query.
- **Flexible schema:** The API structure can evolve without breaking existing clients.

## GraphQL vs REST

GraphQL differs from REST in a few ways:

| Feature                   | REST                          | GraphQL                 |
| ------------------------- | ----------------------------- | ----------------------- |
| **Endpoints**             | Multiple (`/users`, `/posts`) | Single endpoint         |
| **Data structure**        | Fixed by server               | Client specifies fields |
| **Fetching related data** | Multiple requests needed      | Single request          |




#### Resource Links

- Official GraphQL documentation – Introduction to GraphQL on graphql.org
  👉[graphql.org](https://graphql.org/learn/?utm_source=chatgpt.com)
  👉[How to GraphQL](https://www.howtographql.com/basics/0-introduction/)
- GraphQL Specification (latest release) 👉[spec.graphql.org](https://spec.graphql.org/October2021/?utm_source=chatgpt.com)
- GraphQL FAQ, to understand how the spec is governed etc. 👉[graphql.org](https://graphql.org/faq/general/?utm_source=chatgpt.com)
- Wikipedia page on GraphQL for summary and history 👉[Wikipedia](https://en.wikipedia.org/wiki/GraphQL?utm_source=chatgpt.com)
