# SQL Cheat sheet 

1. Databases are a way of organizing data such that you can perform the CRUD opertations: Create, Read, Update, Delete

2. DBMS are a way of intaracting with a database using a graphical user interface or a textual language

```SQL

```

side note: 
here are advantages of postgreSQL over other relational databases:
    1. Can create its own datatypes 'object oriented' with specific properties
        - this inculdes supporting advanced features such as inheritance and polymorphism
    2. Runs fully ACID (atomicity, consitency, Isolation, Durability) compliant transactions -- but includes something called multiversion concurrency control to allow multiple transactions to run at the same time
    3. Supports other languages such as python and C and has a rubust ecosystem of extentions
    4. QUESTION: Note that Postgres supports arrays is this an option we would never want to use 
    5. Note we also can include json datatypes in postgres to handle unstructured data

## Notes for how I installed and started a postgress service

THINGS I HAVE DONE FOR NOW THAT I AM NOT SURE ARE CORRECT

1. Option 1 

Host: Usually localhost for local development.
Port: By default, PostgreSQL listens on port 5432.
Database: The name of the database you created, e.g., myappdb.
Username: The PostgreSQL user, e.g., myuser.
Password: The password for the user, if applicable.

## CREATING A TABLE 

--- 
## RELATIONSHIPS BETWEEN TABLES & SCHEMA DESING 

## INDEXING

- Indexing is a database object that improves the speed of data retrival of operations 

- Indexing is applied to columns that are frequently used in `JOIN` conditions, `WHERE` clauses or as part of `ORDER BY` AND `GROUP BY` statements


## SQL queeries 

1. `JOIN` examples

2. `IN` key word

2. Aggregate funcitons

3. `HAVING` is added `WHERE` keyword cannot

4. `FILTER` KEY WORD
4. **Conditional aggrecation**
    example:

        ```SQL
        SELECT user_id,
            COUNT(*) AS total_transactions,
            COUNT(CASE WHEN transaction_status = 'approved' THEN 1 END) AS approved_transactions
        FROM Transactions
        GROUP BY user_id;
        ```

NOTE: Understand the diffrence of using Join vs IN here is a breif note 

*Performance: Subqueries in the IN clause can be inefficient, especially with large datasets. The database needs to first resolve the subquery and then match the result set to the outer query, which can lead to poor performance in some systems.*
*Limited Flexibility: Harder to extend if additional columns from the Employee table are needed in the result set (e.g., additional employee info beyond just name).*

## Questions

??? Not very clear on the enum type



SQL Interview Question 6:

Products
    ProductID
    ProductName
    CategoryID
Sales
    SaleID
    ProductID
    SaleDate

Write a query to find the names of products that have been sold more than 5 times in the last month.

SELECT p.ProductName
FROM Products p 
JOIN (
    SELECT ProductID
    FROM Sales
    WHERE SaleDate >= CURRENT_DATE - INTERVAL 1 MONTH
    GROUP BY productID
    HAVING COUNT(*) > 5 

) s ON s.ProductID = p.ProductID


SELECT p.ProductName
FROM Products p 
JOIN Sales s ON s.ProductID = p.ProductID AND s.SaleDATE >= CURRENT_DATE - INTERVAL 1 MONTH
GROUP BY productID
HAVING COUNT(*) > 5 