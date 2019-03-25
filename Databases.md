# Databases

## Relational
* Relational databases are designed for transactional and strongly consistent online transaction processing (OLTP) applications and are good for online analytical processing (OLAP).
* The relational model normalizes data into tables that are composed of rows and columns.

## NoSQL
* NoSql is a non-relational database

### Types of NoSQL
* Key-Value: Highly partitionable adn allow horizontal scaling
    * Use cases: Gaming, ad Tech and IoT
* Document: Data is typically represented as JSON
    * DynamoDB and MongoDB are examples
* Graph: Purpose is to make it easy to build and ru application that work with highly connected datasets
    * Use Cases: Social networking, recommendation engines, fraud detection and knowledge graphs
    * AWS Neptune, Neo4J and Giraph
* In Memory: Purpose built data store that deliver microsecond response times
    * Use Cases: Leaderboards for gaming, session stores, and real-time analytics
    * Redis 

Sources: 
* [AWS NoSql](https://aws.amazon.com/nosql/)