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