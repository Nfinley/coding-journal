# SQL Basics


- SQL stands for Structure Query Language and is a relational database
- Relational db is a collection of tables 

## Commands
### QUERYING
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