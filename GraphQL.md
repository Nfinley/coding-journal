# GraphQL

## What is it?

- It is a query language for APIs
- API Standard that provides a more efficient, powerful, and flexible alternative to REST
- At its core, GraphQL enables declarative data fetching where a client can specify exactly what data it needs from an API.
- Instead of multiple endpoints that return fixed data structures, a GraphQL server only exposes a single endpoint and responds with precisely the data a client asked for.
- Exposes single endpoint and returns explicitly what client asks for
- More efficient alt to REST
- Netflix open-sourced their solution called Falcor

### A more efficient alt to REST

- Increased mobile usage created need for better data loading
- Variety of different frontend frameworks and platforms on client side - language agnostic, each client can access precisely the data it needs
- Fast dev speed and expectation for rapid feature development makes REST needing to be updated much more frequently: With REST APIs, the way data is exposed by the server often needs to be modified to account for specific requirements and design changes on the client-side. This hinders fast development practices and product iterations.

### Why is it better than REST?

- There are great ideas in REST: Stateless servers and structured access to resources
- Developed to cope with need for more flexibility and efficiency of REST (To display a username, with their posts and followers would take 3 calls to REST endpoints)
  - ie:
  ```
  query{
      User(id: '19509094') {
          name
          posts {
              title
          }
      }
  }
  ```
- GraphQL only has one endpoint - in same scenario you would only send one request that describes all data requirements the client needs

### Core Concepts

#### Schema Definition Language (SDL)

- Simple `Type` of Person

```
type Person {
  name: String!
  age: Int!
}
```

- The `!` following the value means it is required
- It is also possible to express relationships between Types, for example in a blog application a person could be associated with a Post:

```
type Post {
 title: String!
 person: Person!
}
```

- Conversely the other end of the relationship needs to be placed on the Person Type

```
type Person {
  name: String!
  age: Int!
  posts: [Post!]! #one to many relationship because the posts are an array
}
```

- only has one endpoint to call because the data returned is not fixed like REST
- This means the client must send more information to the server to express its data needs via a `query`
- A query could look like the below, where `allPersons` is the root field and everything else is the payload

```
query {
  allPersons {
    name,
    age
  }
}
```

- Query responses are shaped how the request was sent

#### Writing Data with Mutations

- To make changes to data you use `mutations` and there are three kinds
  - creating new data
  - updating existing
  - deleting data
- Follow same structure as a query but must start with `mutation`

```
mutation {
  createPerson(name: "Bob", age: 36) {
    name
    age
  }
}
```

- The above is updating name and age but also returning those fields in the same server trip
- GraphQL generates IDs by the server when new objects are created and its a pattern to use them as ids on objects

#### Subscriptions

- Allows for realtime connections to a server in order to immediate information
- When a client subscribes to an event it will initiate and hold a steady connection to the server
- They represent a `stream` of data sent to the client
- Syntax is similar to query and mutation:

  ```
    subscription {
        newPerson {
            name
            age
        }
    }

  ```

- Subscriptions are a GraphQL feature that allows a server to send data to its clients when a specific event happens
- They are usually implemented with websockets

- Whenever a mutation is performed on the above `Person` object the server sends the information

#### Defining a Schema

- Defines the capabilites of the API by speciding how a client can request the data
- It is the contract between the server and client
- Collection of Grapql types
- Root Types which include:

```
type Query { ... }
type Mutation { ... }
type Subscription { ... }
```

- These are the entry points for the request sent by the client
- Putting all together:

```
type Query {
  allPersons(last: Int): [Person!]!
}

type Mutation {
  createPerson(name: String!, age: Int!): Person!
}

type Subscription {
  newPerson: Person!
}

type Person {
  name: String!
  age: Int!
  posts: [Post!]!
}

type Post {
  title: String!
  author: Person!
}
```

### Big Picture Architecture

- GraphQL is only a specification which means it is only long document describing detailed behavior of a GraphQL Server

### Use Cases

1. GraphQL with a Connected DB

- Most common for greenfield
- It is Transport layer agnostic (TCP, websocket or any other transport)
- Doesn't care about the type of DB

2. That is a thing layer in front of a number of third party or legacy system and integrates them through a single GraphQL API layer

- Can be used to unify existing systems and hide their complexity behind a nice API.
- Helpful for developing new features
- Server doesn't care about the data sources

3. Hybrid approach of a connected DB and legacy system integration all accessed through single endpoint
   - When a query is received by the server, it will resolve it and either retrieve the required data from the connected database or some of the integrated APIs.

### Resolver Functions

- Each field has one resolver function
- The sole purpose of a resolver function is to fetch the data for its field
- When server receives a query it fires off all of the resolver functions for each field, once all of the resolvers have returned the server packages up the data in the format described by the query and sends it back to the client

### GraphQL Clients

- Great for frontend developers
- Client doesn't care where the data is coming from
- Purely declarative approach
- Examples include Apollo and Relay

###### Major Difference between REST and GraphQL is going from imperative to declarative:

- In REST sample steps may include:
  1. Construct and send HTTP request
  2. Receive and parse server response
  3. Store data locally (memory or persistent)
  4. Display data in the UI

###### VS. GraphQL you shouldn't be doing more than two steps:

1. Describe data requirements
2. Display the data

- All lower level tasks and storing data should be abstracted away and that is where Apollo and Relay come in

Pros

- Can be used with any language and framework
- No more under or over fetching data - only get the data you need
- Uses a Schema and Type system allowing for rapid development and setting a contract upfront with front and backend developers to know what is expected
- Front end can easily mock up responses from the server in order to test after the Schema is defined
- Flexible nature allows rapid iterations on front end without changes to the API
- Provide insightful analysis to measure performance of API
- - It is Transport layer agnostic (TCP, websocket or any other transport)
  - Doesn't care about the type of DB

Cons
