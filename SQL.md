# SQL Basics


- SQL stands for Structure Query Language and is a relational database
- Relational db is a collection of tables 

## Commands
## QUERYING - SELECT operator
To query a table you can use the keyword `SELECT` to select for example a column from a table: 
```
SELECT name // select the column name
FROM people; // from the people table
``` 

Its good practice to keep keywords uppercase and to include a colon at the end of the query which tells SQL where the query ends 

* To select multiple column separate the column names with commmas: 
  * `SELECT name, birthdate FROM people;`
* To select all columns use the `*` 
* To limit the number of rows returned you can use the keyword `LIMIT` like so: 
  * `SELECT * FROM people LIMIT 10;`
* Use `DISTINCT` when you want to find all unique values like all languages for films 
* `COUNT` function can be used to return the number of rows in one or more columns 
  * To count "non-missing" values you can call `COUNT()` on just that column 
  * You can also combine `COUNT()` with `DISTINCT` to count number of distinct values in a column `SELECT COUNT(DISTINC birthdate) FROM people;`


In SQL, the `WHERE` keyword allows you to filter based on both text and numeric values in a table. There are a few different comparison operators you can use:
```
= equal
<> not equal
< less than
> greater than
<= less than or equal to
>= greater than or equal to
```
## FILTERING 
### WHERE operator
* `WHERE` keyword can be used to filter 

e.g.: 
```
SELECT *
FROM films
WHERE budget > 10000;
```
* You can use the `AND` keyword to add to the filtering like so: 
```
SELECT title
FROM films
WHERE release_year > 1994
AND release_year < 2000;
```  

### OR operator
* For selecting ros based on multiple conditions where some but not all conditions need to be met use the `OR` operator
* When combining AND and OR, be sure to enclose the individual clauses in parentheses, like so:

```
SELECT title
FROM films
WHERE (release_year = 1994 OR release_year = 1995)
AND (certification = 'PG' OR certification = 'R');
```

### BETWEEN operator
* The `BETWEEN` keyword provides a useful shorthand for filtering values within a specified range.
  
```
SELECT title
FROM films
WHERE release_year
BETWEEN 1994 AND 2000;
``` 

### NULL and NOT NULL 
* In SQL, `NULL` represents a missing or unknown value. You can check for `NULL` values using the expression `IS NULL`
* Check for `NULL`

```
SELECT COUNT(*)
FROM people
WHERE birthdate IS NULL;
```

* Check for not null
```
SELECT name
FROM people
WHERE birthdate IS NOT NULL;
```

## Aggregate Function 

### Avg, Min, Max and SUM
* AVG() function calculates the average of a specified column
* MIN() calculates the min
* MAX() calclulates the max
* SUM() function calculates the sum of a specified column


## Sorting and Grouping

### ORDER BY 
* In SQL, the ORDER BY keyword is used to sort results in ascending or descending order according to the values of one or more columns.
* By default ORDER BY will sort in ascending order. If you want to sort the results in descending order, you can use the DESC keyword.

```
SELECT title
FROM films
ORDER BY release_year DESC; //sorts Z-A
```

### GROUP BY
* In SQL, GROUP BY allows you to group a result by one or more columns
* Commonly, GROUP BY is used with aggregate functions like COUNT() or MAX(). Note that GROUP BY always goes after the FROM clause!
* Note that you must always list the column in the GROUP BY that is listed in the SELECT statement, otherwise SQL will throw an error

```
SELECT sex, count(*)
FROM employees
GROUP BY sex;
```
### HAVING
* HAVING allows you to filter based on the result of an aggregate function
* Using a WHERE operator is invalid

```
SELECT release_year
FROM films
GROUP BY release_year
HAVING COUNT(title) > 10;
```
---
# Introduction to Relational Databases
* Notes from [DataCamp Intro to Relational Databases](https://learn.datacamp.com/courses/introduction-to-relational-databases-in-sql)

## Relational Database: 
* Real-life entities become tables
* reduced redundanct 
* data integrity by relationships

Three Concepts learn from course: 
* Contraints
* Keys
* Referentia Integrity

### Information Schema
* Information schema is a schema that gives you information about your tables: `information_schema.tables` or `information_schema.columns`
* `information_schema` has multiple tables you can query with the known SELECT * FROM syntax:

tables: information about all tables in your current database
columns: information about all columns in all of the tables in your current database

### Entity relation diagram 
* Entity diagrams represent the entity and their associated data

![Entity Diagram](assets/EntityDiagram.png)

## CREATE TABLE command
* Include the table name, column name and data type for each column 

```
CREATE TABLE table_name (
 column_a data_type,
 column_b data_type,
 column_c data_type
);
```
## ALTER TABLE command
* To add columns to a db you can use `ALTER TABLE` command
```
ALTER TABLE table_name
ADD COLUMN column_name data_type;
```

## INSERT DISTINCT INTO command
* Used to migrate data from one db to another and only copying distinct records
* Use the `DISTINCT` keyword to only mirgrate distinct values from one table to another ensuring no duplicates
```
INSERT INTO new_table_name
SELECT DISTINCT column_name 
FROM old_table_name
```

## INSERT INTO command
* The normal `INSERT` command used to insert data into a table 
```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

## RENAME COLUMN
* Allowing you to rename a column name
```
ALTER TABLE table_name
RENAME COLUMN old_name TO new_name;
```

## DROP command
* Straight forward when there is no data 
* Can be used to drop columns or entire tables (USE WITH CAUTION)

Column:
```
ALTER TABLE table_name
DROP COLUMN column_name;
```  
Table: 
```
DROP TABLE table_name;
```

## Integrity Contraints
There are three types of contraints:
1. Attribut contstraints, eg. data types on columns
2. Key constraints, eg primary keys
3. Referential integrity contraints, enforced through foreign keys

* Purpose of constraints:
  * Give data structure
  * Help with consistency and thus data quality
  * Data quality is business advantage/ data science prerequisite
  * Enforcing is difficult but SQL dbs can help

### Attribute Contraints 
* Data types as attribute constraints encforce data integrity
* Also restrict possible operations on the tables 
  ![Example of Postgres data types](assets/Postgres_dataTypes.png)

### Casting 
* If you want to do calculation for two columns with different types you can do CASTING on the fly
![Example of Casting](assets/CastingTypes.png)

---
# Databse Design
* Notes from [DataCamp Databse Design](https://campus.datacamp.com/courses/database-design) course

* Questions to be answered: How to oranganize our data? 
## OLTP and OLAP

__OLTP__: Online Transaction Processing
  - Oriented around transactions
  - Focuses on day-to-day transactions

When to use OLTP?
  - Finding the prices of a book
  - Update latest customer transaction
  - Keep track of employee hours

__OLAP__: Online Analytical Processing
  - Oriented around analytics 
  - Focuses on business desicion making 
  
 When to use OLAP
  - Calculate books with best profit margin
  - Find most loyal customer
  - Decide employee of the month 

### OLTP vs. OLTP
![OLTP vs OLAP Table]('./../assets/OLTP_vs_OLAP.png)

![Both work together](assets/working_together.png)

## Storing Data
Stored in three ways
1. Structed data
   1. Follows a schema
   2. Designed data types & relationships
2. Unstructured Data
   1. Media files and raw text
   2. Schemaless
3. Semi-structured data
   1. Does not follow larger schema
   2. Self-describing structure
   3. E.G JSON, XML and NoSql


### Traditional DBs
* Storing real-time relational structed data - OLTP

### Data Wharehouses
* For analyzing archived structed data - OLAP
* Optimized for read-only analytics - OLAP
* Usually read-only
* Contains data from multiple sources
* Massively parallel processing
* Typically uses a denormalized schema and dimensional modeling
  * EG Azure SQL Data Warehouse and Amazon Redshit
* Schema-on-write
### Data Lakes
* For storing data of all structures = flexibility and scalabilitty
* For analyzing big data
* Storage is cheaper
* Retains all data and can take up petabytes
* Schema-on-read
* Need to catalog data otherwise becomes a data swamp
* Run big data analytics using services like Apache Spark and Hadoop

When should you choose a data lake over a data warehouse? 
* To create accessible and isolated data repositories for other analysts

## Data Flows
![ETL vs ELT](assets/ETL_ELT.png)  
  
## What is DB design 
* Determines how data is logically stored
* Uses db models: hih-level specifications for the db structure
  * Most popular is relational model 
  * Others are: NoSQl, Object oriented or network model
* Uses Schemas: blueprint of the db 
  * defines tables, fields, relationships, indexes and views
  * When inserting dat in relational db, schemas must be respected

## Data Model 
* [Abstract model](https://en.wikipedia.org/wiki/Data_model) that organizes elements of data and standardizes how they relate to one another
* Process of creating a data model for the data to be stored
* Three levels of data modeling: 
    1. Conceptual data model: describes entities, relationships and attributes
       1. Tools: data structure diagrams e.g. entity-relational diamgrams and UML diagrams
    2. Locigal data model: defines tables, columns and relationships
       1. Tools: database models and schemas, e.g. relational model and star schmea
    3. Physical data model: describes physical storage 
       1. Tools: partitions, CPUs, indexes, backup systems and tablespaces

![Conceptual Diagram](assets/Conceptual%20Diagram_DBDesign.png)

![Other Design](assets/Other_ways_to_design.png)


### Dimensional modeling
It is the adaptation of the relational model for data warehouse design 
* Optimized for OLAP: queires: aggregate data, not updating
* Builting using star schema 
* Easy to interpret and extend 
* Dimensional modeling us two tables: 
  1. Fact tables
      * Decided by business use-case
      * Holds records of a metric
      * Changes Regularly
      * Connects to dimensions via foreign keys
  2. Dimension tables
      * Holds descriptions of attributes
      * Does not change as often
  
![Dimensional Elements](assets/Dimensional_Elements.png)

## Star and Snowflake Schema 
* Star is simmplest dimensional modeling type and is often called 'dimensional modeling'
* Snowflake schema is an extension of the star schema 
* 1[Star vs. Snow](assets/Star_vs_Snow.png)

### Data nomalization
* Database design technique
* Divides tables into smaller tables and connects them via relationships
* Goal: Reduce redundnacy and increase data integrity
* It happens via identify repeating groups of data and create new tables for them
* 