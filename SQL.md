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

## Notes for how I installed and started a posgress service

THINGS I HAVE DONE FOR NOW THAT I AM NOT SURE ARE CORRECT
1. Option 1 

Host: Usually localhost for local development.
Port: By default, PostgreSQL listens on port 5432.
Database: The name of the database you created, e.g., myappdb.
Username: The PostgreSQL user, e.g., myuser.
Password: The password for the user, if applicable.