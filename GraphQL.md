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
 * Increased mobile usage created need for better data loading
 * Variety of different frontend frameworks and platforms on client side - language agnostic, each client can access precisely the data it needs
 * Fast dev speed and expectation for rapid feature development makes REST needing to be updated much more frequently: With REST APIs, the way data is exposed by the server often needs to be modified to account for specific requirements and design changes on the client-side. This hinders fast development practices and product iterations. 
 
 ### Why is it better than REST? 
 * There are great ideas in REST: Stateless servers and structured access to resources
 * Developed to cope with need for more flexibility and efficiency of REST (To display a username, with their posts and followers would take 3 calls to REST endpoints)
    * ie: 
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
 * GraphQL only has one endpoint - in same scenario you would only send one request that describes all data requirements the client needs
 
 
 
### Core Concepts

 
 Pros
* Can be used with any language and framework
* No more under or over fetching data - only get the data you need
* Uses a Schema and Type system allowing for rapid development and setting a contract upfront with front and backend developers to know what is expected 
* Front end can easily mock up responses from the server in order to test after the Schema is defined 
* Flexible nature allows rapid iterations on front end without changes to the API
* Provide insightful analysis to measure performance of API

Cons 

