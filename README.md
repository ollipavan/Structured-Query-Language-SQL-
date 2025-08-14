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

Data manipulation language - It is used to change the values in the table
1. Insert
-- the below inserting operation is called implicitng inserting because we filled the values for every column.
insert into student_details values ('Pavan', 390, 'kakinada'),
('Vinay', 391, 'Chennai'),
('Venkat', 392, 'Bangalore'),
('Sai', 393, 'mumbai'),
('Jai', 394, 'hyderbad');

-- If we want to insert values in a specific column then it is called as explicit inserting

Insert into student_details(Student_name,student_id) values('Peter', 395);

2. Update - it is used to modify any exisitng value in the table 
/* In the initial time of running update statement sql will throught safety mode error because if we try to update the data
the old data will be changed in order to remaind us it will through  an error. For this scenario we need to run the below statement first*/

Update student_details set address =  'Vizag' where student_name = 'Peter';
set SQL_safe_updates = 0;
insert into student_details(address) values('guntur');

select * from student_details;
update student_details set student_name = 'Raju', student_id = 397, address = 'Tirupati' where address = 'guntur';
-- to turn on the safety mode we need to run the below statement
set SQL_safe_updates = 1;
3. Delete - to delete the records in the table either single or multiple or all records

delete from student_details where student_id = 394;

Data types


Constraints:
Regular constraints:  

Null: it is used to represent unknown values and it is not equal to zero, also can be used for all data types


Not Null: if any value that should be mandatory 

CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);
Default: The default value will be taken which was given while creating column

CREATE TABLE settings (
    id INT PRIMARY KEY,
    theme VARCHAR(20) DEFAULT 'light'
);
Check: it is used like a conditional statement. If we want people above age 18 we need to use check constraint.
ex; check (age >=18)

CREATE TABLE accounts (
    id INT PRIMARY KEY,
    balance DECIMAL(10, 2) CHECK (balance >= 0)
);

Key constrainst:
Unique key: Value should be unique and doesn’t allow duplicates but allows single null values because it also considers a null value as unique.

CREATE TABLE employees (
    id INT PRIMARY KEY,
    email VARCHAR(100) UNIQUE
);
Pirmary key: Combination on unique and not null. Will not allow null values

CREATE TABLE users (
    id INT PRIMARY KEY,
    name VARCHAR(100)
);
Foreign key: Ensures the value in a column matches a value in another table's primary key.  Maintains referential integrity between related tables.

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
Auto_increment: it will generate sequence of value generated automatically

-- MySQL
CREATE TABLE customers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100)
);

-- PostgreSQL
CREATE TABLE customers (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);

DQL commands -- classes in query  -- Select from where groupby having orderby limit -- select is used to specify columns -- from is used to specify the table -- where is used to filter data present in table -- select * from emp_exe where age in (28,32,45,56) -- group by is used divide groups based oon aggregations -- select city, count(*) from customers group by city; -- having is used to filter data of an aggregated column data -- select city, count(*) from customers group by city having count(*) > 1; -- orderby is used to sort the data in asc/desc order based on any column  -- select * from customers order by customer_id desc; -- select  customer_id, postalcode from customers order by customer_id asc; -- limit is used to limit the number of record -- Joins 
inner join - it will give only the matching records from both tables 
Syntax:  
select b.account_id, b.fullname, b.branch, b.gender, t.transaction_id, t.transaction_type, 
t.transaction_amount  
from bank_info as b join transactioninfo as t  
on b.account_id = t.account_id; 
outer join - both matached and unmatached records will be printed. there are three types in 
outer joins -- left join  
select b.account_id, fullname, b.branch,t.transaction_id, transaction_amount, 
transaction_time 
from bank_info as b left join transactioninfo as t  
on b.account_id = t.account_id -- right join  
select b.account_id, fullname, b.branch,t.transaction_id, transaction_amount, 
transaction_time 
from bank_info as b right join transactioninfo as t  
on b.account_id = t.account_id -- full join  
select * from bank_info as b left join transactioninfo as t on b.account_id = t.account_id 
union 
select * from bank_info as b right join transactioninfo as t on b.account_id = t.account_id; 
 -- cross join - this join is also called as cartesian product because it will provide output as all 
possible combinations. 
Syntax: 
select * from bank_info, transactioninfo;

