# Intro to Database Design SQL
SQL statements learned in my Intro to Database Design class

## Table of Contents
- [Table](#Table)
   - [Create](#Create)
   - [Copy](#Copy)
   - [Drop](#Drop)
   - [Insert](#Insert)
   - [Delete from](#Delete)
- [Select](#Select)
- [Constraints](#Constraints)
- [Tablespace](#Tablespace)

### Table
#### Create
###### Create a table
- **CREATE TABLE** *table_name* (*data* *data_type*);

      CREATE TABLE Person (

      PersonID number(10),

      LastName varchar2(255),

      );
---
#### Copy
###### Copy from an existing table
- **CREATE TABLE** *table_name* **AS** **SELECT** *columns* **FROM** *existing_table*

      CREATE TABLE TestTable AS
      SELECT customername, contactname
      FROM customers;
---
#### Drop
###### Drop an existing table
- **DROP TABLE** *table_name*;

      DROP TABLE table_name;
---
#### Insert
###### Insert records into an existing table
- **INSERT INTO** *table_name* **VALUES** *(val1, val2, val3, ...)*;

      INSERT INTO Persons VALUES (101, 'Person1', 'LastName1', '123 Main St.', 'Manchester');
---
#### Delete
###### Delete existing records from an existing table
- **DELETE FROM** *table_name* **WHERE** *PersonID = 101*;

      DELETE FROM Persons WHERE PersonID = 101;
---
### Select
###### Select data from the database
1. **SELECT FROM**
2. **WHERE**
3. **> < <> >= <= != =**
4. **AND** / **OR**
5. **LIKE**
6. **BETWEEN**
7. **NOT**
8. **IN**
9. **AS**
10. **DISTINCT**
11. **ORDER BY** .. **ASC** / **DESC**
12. **IS NULL** / **IS NOT NULL**

         1. SELECT column1, column2 FROM table_name;
         2. SELECT column1, column2 FROM table_name WHERE first_name = 'Alice';
         3. SELECT column1, column2 FROM table_name WHERE first_name != 'Alice';
         4. SELECT column1, column2 FROM table_name WHERE first_name > 'Alice' AND last_name <= 'Log';
         5. SELECT column1, column2 FROM table_name WHERE first_name LIKE 'Al_ce' OR first_name LIKE 'Al%';
         6. SELECT column1, column2 FROM table_name WHERE first_name BETWEEN 'Alice' AND 'Mary';
         7. SELECT column1, column2 FROM table_name WHERE first_name NOT BETWEEN 'Joe' AND 'Leroy';
         8. SELECT first_name FROM students WHERE age IN (5, 15, 20);
         9. SELECT first_name AS "first", last_name AS "last" FROM employee;
         10. SELECT DISTINCT first_name FROM students;
         11. SELECT first_name, last_name FROM employee ORDER BY last_name ASC, first_name DESC;
         12. SELECT first_name, salary FROM employee WHERE salary IS NULL OR last_name IS NOT NULL;
---
### CONSTRAINTS
###### Column constraints
- **Not null**: the column must have a value
- **Unique**: no two rows could have the same value for that column
- **Primary key**: by default, primary keys must be unique and not null
- **Foreign key**: must be a primary key in another table
- **Default** (not really a constraint): assigns a default value if no value is given
###### Unnamed
      CREATE TABLE Persons (
      PersonID int PRIMARY KEY,
      LastName varchar(255) NOT NULL UNIQUE,
      FirstName varchar(255),
      Address varchar(255),
      City varchar(255),
      Country varchar(50) DEFAULT 'USA',
      Balance number DEFAULT 100
      );
###### Named
      PersonID int CONSTRAINT person_pk PRIMARY KEY
###### Table level constraints
      CONSTRAINT constraintName PRIMARY KEY (columnNames),
      CONSTRAINT fk_emp_dept FOREIGN KEY (department_id) REFERENCES department(department_id)
---
### Select
###### Select data from the database
- **DELETE FROM** *table_name* **WHERE** *PersonID = 101*;
---
### Select
###### Select data from the database
- **DELETE FROM** *table_name* **WHERE** *PersonID = 101*;
---
### Select
###### Select data from the database
- **DELETE FROM** *table_name* **WHERE** *PersonID = 101*;
---
### Select
###### Select data from the database
- **DELETE FROM** *table_name* **WHERE** *PersonID = 101*;
---
### Tablespace
###### Create Tablespace (storage location where actual data can be kept)
- **CREATE TABLESPACE** *name* **DATAFILE** *db_file_name_and_location* **SIZE** *size* **AUTOEXTEND** *yes/no*

      CREATE TABLESPACE tablespace_name
      
      DATAFILE 'c:\users\me\oracle\test_tablespace.dbf'

      SIZE 50M

      AUTOEXTEND ON NEXT 10M MAXSIZE 250M;


