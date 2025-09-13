## What is GraphQL?

GraphQL is a query language and runtime for APIs that allows clients to request exactly the data they need. Unlike traditional REST APIs, which often return too much or too little information, GraphQL prevents over-fetching (getting unnecessary data) and under-fetching (not getting enough data, requiring multiple requests).

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

| Feature                   | REST                                                                                                              | GraphQL                                                                             |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **Endpoints**             | Multiple endpoints for different resources (e.g., `/users`, `/posts`). Each endpoint returns a fixed set of data. | Single endpoint handles all queries and mutations, reducing the number of requests. |
| **Data structure**        | Server defines the response structure. Clients get all fields, even if they don’t need them.                      | Clients specify exactly which fields they want, avoiding over-fetching.             |
| **Fetching related data** | Requires multiple requests to gather related data from different endpoints.                                       | Can fetch multiple related resources in a single request.                           |
| **Flexibility**           | Changing or extending endpoints can break existing clients.                                                       | Schema evolves easily; new fields can be added without affecting existing queries.  |
| **Performance**           | Over-fetching or multiple requests may slow down applications.                                                    | Efficient queries reduce bandwidth usage and improve performance.                   |
