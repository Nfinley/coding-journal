# GraphQL Cascadia JS Workshop

- Eve Porcello and Alex Banks from Moon Highway
- [Workshop github](https://github.com/graphqlworkshop/cascadiajs)
-

## Day 1

### Graphql Intro and Query Language

- REST architecture
  - HTTP requests that returns a ton of json and may not be in the space we want it to be in
- Query Language
  - How do we get data with GraphQL: `/graphql`
  - No more fields than we ask for and the data comes back the way we request it
  - Fewer http requests and less latency
  - We can move all the reshaping of the data and data transforming of data to server and then deliver the data to our phone
- Changing Data with graphql
  - Use a `MUTATION`(used for posting a data)
- Graphql can sit in front of any type of data soure, it can bring together all kinds of data
- No overfetching
- Queries - get data
- Mutations - change data
- Subscriptions: Sent using websockets (live likes on Facebook are powered by subscriptions)
- Use Graphql fragment to get allfields - but the idea is not to overfetch
  - All Fragments can only be created on the Types
  - Means of composition where you can put together different queries
  - They are very helpful to help compose and insert certain queries into main queries
- There are connections to connect types to eachother
  - To connect one type to another you add that type on a field

* Can you cascade mutations to other objects?
  - YES it is all driven by the schema and the resovler functions for the mutations

- Schema Definition LANGUAGE
  - Scalar Types
    - Int, Float, String, Boolean or ID
    - `id: ID!`, `name: String`
  - Object Types
    - `type Photo {}`
  - Nullable vs. Non-Nullable: If it has a `!` it cannot be null
  - Query Type, Root Queries
    - `type Query { totalUsers: Int!}`
  - Lists
    - `photos: [Photo]` # nullable list of nullable values
    - `photos: [Photo]!` # non-nullable list of nullable values
    - `photos: [Phot!]!` # non-nullable list of non-nullable values - it could return an empty array
  - Enumeration Type : Defines list of restricted options for a value
    - `enum PhotoCategory {}`
  - One-to-one connections
    - `type Photo { user: User}
  - One-to-many
  - Many-to-many
  - Custom Types
  - Through types
  - Root Mutation
  - Input Types: Organize mutation values
    - `input
  - Subscription type
  - Custom Scalars: For example with dates, something that has a little more substance than a string value
    - `scalar DateTime`

* To set up server tou need resolvers and a schema

Apollo Client is two things:

- Link for local data store
- Caching layer

GraphQL is used by huge players:

- NetFlix
- PayPal
- https://graphql.org/users/

QUESTIONS

- Future proofing, what about if you want to change your schema, effects?

## DAY 2

### Unions and Interfaces

- Interface

  - Collection of fields unique to a certain type
  - Then we can extends these interfaces for individual tpyes
  - `type Cat implements Pet`
  - When you create another Pet you must add all of keys from the interface onto the implemented piece and then you can add specific custom to that type
  - Help create custom objects based on the base class

- Inline Fragment
  - `...on CAT { sleepAmount }`
  - Allows us to return pieces of data only on that type
  - Use when you have unique fields on a type
- Named Fragments are only available on a TYPE

  - Use when you have common fields on a type

- Union Types
  - Allow us to return lists of different types
  - Inline fragments become really useful with Union types, allows us to access the fields
  - Union types don't have to share any of the same fields

* Introspection Queries
  - `__schema` for example allow us to look inward at the schema ahs shows us what is happening
  - [Article](https://moonhighway.com/five-introspection-queries)

- Apollo CLIENT
  - Apollo-boost is a package that bootrapps getting up and running with apollo client
