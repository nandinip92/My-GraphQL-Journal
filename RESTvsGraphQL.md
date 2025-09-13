# GraphQL Vs REST

| Feature                   | REST                                                                                                              | GraphQL                                                                             |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **Endpoints**             | Multiple endpoints for different resources (e.g., `/users`, `/posts`). Each endpoint returns a fixed set of data. | Single endpoint handles all queries and mutations, reducing the number of requests. |
| **Data structure**        | Server defines the response structure. Clients get all fields, even if they don’t need them.                      | Clients specify exactly which fields they want, avoiding over-fetching.             |
| **Fetching related data** | Requires multiple requests to gather related data from different endpoints.                                       | Can fetch multiple related resources in a single request.                           |
| **Flexibility**           | Changing or extending endpoints can break existing clients.                                                       | Schema evolves easily; new fields can be added without affecting existing queries.  |
| **Performance**           | Over-fetching or multiple requests may slow down applications.                                                    | Efficient queries reduce bandwidth usage and improve performance.                   |

### 1. Fetch Exactly What You Need

**REST:** Each endpoint returns a fixed structure of data. This can lead to:

- Over-fetching: Getting more data than needed.
- Under-fetching: Not getting enough data, requiring multiple requests.
  **GraphQL:** Clients specify exactly what fields they need.
  _Example:_ Request a user’s name and email without getting their full profile.

### 2. Single Endpoint

**REST:** With a REST API, you would typically gather the data by accessing multiple endpoints. (`/users`, `/users/1/posts`).

![REST-fetch-image](/Images/RESTvsGraphQL/REST-fetch.jpg)

**GraphQL:** In GraphQL on the other hand, you’d simply send a single query to the GraphQL server that includes the concrete data requirements. The server then responds with a JSON object where these requirements are fulfilled.

![GraphQL-fetch-image](/Images/RESTvsGraphQL/GraphQL-fetch.jpg)

### 3. Faster Data Retrieval

**REST:** Complex data often needs multiple round trips to the server.
**GraphQL:** Nested or related data can be fetched in a single request, reducing network calls.

### 4. Strongly Typed Schema

**REST:** No formal contract between client and server beyond documentation.

**_Explaination:_** REST APIs don’t have a built-in contract. The structure of the data returned depends on each endpoint, and developers often need to refer to documentation or communicate directly with backend teams to understand what data they can get.

**GraphQL:** A defined schema specifies types, queries, and mutations, providing clear expectations and enabling better tooling.

**_Explaination:_** GraphQL uses a strong type system to define exactly what data an API can provide. Every type of data and how it can be queried is written down in a schema using the GraphQL Schema Definition Language (SDL). This schema acts like a contract between the frontend and backend teams, clearly showing what data is available and how it can be accessed.

Because the schema is predefined:

- Frontend teams know exactly what the data will look like and can start building and testing their applications without waiting for the backend.
- They can mock the data according to the schema to simulate real responses.
- When the backend is ready, the frontend can simply switch to fetching data from the actual API, without any changes to the app.

### 5. Rapid Product Iterations on the Frontend

**REST** endpoints are often tied to app views, so changing the UI may require backend changes.

**GraphQL** allows clients to request exactly what they need, so frontend changes don’t require backend updates, enabling faster iterations.

### 6. Insightful Analytics on the Backend

With **REST APIs**, the server generally knows which endpoints are being called, but it doesn’t know exactly exactly which data fields are being used by clients. This makes it hard to tell which data is important or unused. Performance monitoring(—how fast or efficiently the server processes requests) is also basic, usually only at the endpoint level, so it’s hard to spot potential bottlenecks.

In contrast, **GraphQL** provides fine-grained analytics because each client query specifies exactly which fields it needs. This allows backend teams to see which data is used most, which is rarely used, helping to identify unused fields and safely deprecate them. GraphQL also uses resolver functions to fetch data, and these can be monitored to find exactly where the system might be slow.

**_In Short:_** In short: GraphQL allows for more detailed, actionable insights on data usage and system performance compared to REST, making API evolution and optimization easier.

### 7. Easier Evolution

**REST:** Versioning can be cumbersome (v1, v2) when the API changes.
**GraphQL:** Fields can be deprecated without breaking clients, reducing the need for versioning.

### 8. Better for Frontend Development

**REST:** Frontend may over-fetch or make multiple requests to assemble UI data.
**GraphQL:** Frontend developers can request precisely what the UI needs in one query.

---

---

**Resource links**

- GraphQL is better than REST 👉[How to GraphQL](https://www.howtographql.com/basics/1-graphql-is-the-better-rest/)
