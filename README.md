SQL Introduction
Database: A data base is container that store data. This database can be accessed by multiple personas such as Humana(manual query using SQL), Applications (via the code), Tools like power bi.
SQL: SQL stands for Structured Query Language. SQL is a standard programming language used to manage and manipulate relational databases. It allows users to interact with databases to perform various operations.
A Database Management System (DBMS) is software that allows users to define, create, maintain, and control access to a database
 
DBMS: Software layer which check before giving it to database 
 
 
Schema - it is blueprint before creating a table we cannot create it randomly.


Create database SQL_learning; -- Syntax for creating database
Commands
•	Data definition language (DDL)- it deals with the database functionalities. [commands: CREATE, DROP, ALTER, TRUNCATE, RENAME]
•	Data manipulation language (DML)- it works on table to modify. [commands: INSERT, DELETE, UPDATE]
•	Data query language (DQL)- to print or retrieve data. [commands: SELECT]
•	Transaction control language (TCL)- to control DML commands.[commands: COMMIT, ROLLBACK, SAVEPOINT]
•	Data Control Language (DCL)- Access control. [commands: GRANT, REVOKE]
DDL commands and Syntax
1. Create -  to create database/ database objects
use SQL_learning;
create table student_info
 (
 student_name varchar(20),
 student_id int
 );
2. drop - to drop tables/ database
DROP table student_info;
DROP database SQL_learning;
3. Alter - to modify the structure of table
Alter table student_info
Add column address 
varchar(30);
4. Rename - it is used to change the names of DB objects
Rename table student_info to student_details
5. Truncate - it is used to remove the values in the table, the table remains same but the values in the table will be removed.
TRUNCATE TABLE table_name;
