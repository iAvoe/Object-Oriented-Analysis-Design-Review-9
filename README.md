# Object-Oriented-Analysis-Design-Review-9

## Database Design

**Database**:
- An integrated collection of stored data that is centrally managed and controlled

**Database management system (DBMS)**
- A system software component that manages and controls one or more databases
- MySQL, Microsoft Access, SQL Server, FileMaker, Oracle, dBASE, etc.
- DBMSs have a way they communicate with each other

**Schema**:
- DB component that contains descriptive information about the data stored in the physical data store (sometimes called metadata)

**Structured Query Language (SQL)**:
- Language to access and update data in a relational DBMS

### Database Schema
- Organization of individual stored data items into higher level groups
- Associations among tables or classes 
- Details of physical data store organization, including types, lengths, locations, and indexing of data items
- Access and content controls, including allowable values for specific data items, value dependencies among multiple data items, and lists of users allowed to read or update data items

A complete information system comprises people, hardware, software, the database(s)/DBMS, application programs & procedures.

The database is part of a larger whole information system, which provides for data collection, storage and retrieval.
- **Waterfall development**: design and implement database first
- **Iterative development**:
  - DB is foundational, early iterations need to focus on data and key portions of the database. 
  - Important to consider database impacts of all subsystems

### DBMS Characteristics

- Simultaneous access by many users and many applications
- Direct access to data with a data interface
- Uniform and consistent access
- Integration and distribution of data across multiple servers
- Most DBMSs comes with an Open Database Connectivity driver that allows the DB to integrate/communicate with other DBs.

### Design and Administration

**Data Administrator (DA)**
- Person in charge of structure and integrity of the data
**Data standards**:
- naming, definition, data typing
**Data use**:
- ownership, accessibility, confidentiality
**Data quality**:
- validation rules, completeness, currency

DA manages the standards, ownership, quality of the application domain data

**Database Administrator (DBA)**
- Person in charge of safety and the operation of the database
- Manage multiple D B M S environment
- Protect the database and data – authentication
- Maintain high-performance level
- Backup data and define recovery procedures

DBA manages environment, sefity, performance and recovery of the DBMS

-----

## Database & Software Development

**Project Management/SDLC**:
- Important as they hold the data and info for a business or project

**Computer Application, and Information Systems**
- Usually require DBs to function

**Information system**
- A set of interrelated components that collects, processes, stores, and provides as output of the information
- Broader in scope than “app”
- Includes database and related manual processes
- **Cannot function without a database**:
  - DBMS ensure, running and managing data effectively in a business or project

Databases are very important to every business because they store and communicate information related to business transactions, product inventory, customer profiles, marketing activities, and overall business functions.

### Relational Databases

A database structure based on the relational model.

**Relational Model**:
- Tables with rows and columns
- One table corresponds to a single file in a DBMS
- **Attribute**: The value held in a singal table cell
- **Key**: an attribute or set of attributes, the values of which occur only once in all the rows of the table
- **Candidate Key**: an attribute or set of attributes that could server as the primary key
- **Primary key**: the key chosen by a database designer to represent relationships among rows in different tables
- **Foreign key**: an attribute that duplicates the primary key of a different (or foreign) table

###  Database Associations

**One-to-Many**
- Add primary key attribute of the “one” class to the “many” class as a foreign key
**Many-to-Many**
- *With Association Class*:
  - Add primary keys of endpoint classes as foreign keys and as candidate keys.   
  - May also become primary key
- *Without Association Class*:
  - Create new table
  - Add primary keys of endpoint classes as foreign keys and as candidate keys. 

### Designing Relational Databases

**Row**: A horizontal group of data attribute values
**Column**: A vertical group of data attribute values

1. Create a table for each class
2. Choose a primary key for each table (invent one, if necessary)
3. Add foreign keys to represent one-to-many associations
4. Create new tables to represent many-to-many associations
5. Represent classification hierarchies
6. Define referential integrity constraints
7. Evaluate schema quality and make necessary improvements
8. Choose appropriate data types
9. Incorporate integrity and security controls

**Referential integrity**:
- A consistent state among foreign key and primary key values
**Referential integrity constraint**:
- A constraint, stored in the schema, that the DBMS uses to automatically enforce referential integrity

### Normalization
Formal technique for evaluating and improving the quality of a relational database schema

A normalized relational database schema has these features:
- Flexibility or ease of implementing future data model changes
- Lack of redundant data
- Protects against insertion, deletion and update anomolies

**First normal form**
- A table is in first normal form if every field contains only one value. 
- Not multiple values in an attribute
- *Solution*: put multivalued attribute in a separate table.

**Second normal form**
- A table is in 2NF if it is 1NF and each non-key attribute is only *functionally dependent* on the entire primary key
- This situation only arises with tables that have multiple attribute keys

**Third normal form**
- A table is in 3NF if it is in 2NF and NO non-key attribute (or set) is functionally dependent on any other non-key attribute (or set)
- In other words, no FDs among any non-key attributes
- If a column is the sum of other columns, then it is redundant

-----

## Data Types

**Primitive data types**
- Data types supported directly by the DBMS

**Complex data types**
- Combinations or compositions of primitive data types. User defined

| Type(s)                    | Description                                    |
|----------------------------|------------------------------------------------|
| datetimeoffset             | Date, time, and time zone                      |
| int, small int, and bigint | Whole numeric values                           |
| float and real             | Numeric values with fractional quantities      |
| money                      | Currency values and related symbols (e.g., $ ) |
| nchar and nvarchar         | Fixed- and variable-length Unicode string      |
| varbinary                  | Variable-length byte sequence up to 2GB        |
| xml                        | XML document up to 2GB                         |

-----

## Distributed DB & DBMS

**Distributed database**
- A database in which data is stored across different physical locations
- A collection of multiple interconnected databases across various locations that communicate via a computer network
- Databases in the collection are logically interrelated with each other
- Data is physically stored across multiple sites. Data in each site can be managed by a DBMS independent of the other sites
- The processors in the sites are connected via a network
- A distributed database incorporates transaction processing

**Distributed DBMS**
- Manages the distributed database in a manner so that it appears as one single database to users

Decentralized database is stored at many locations but not requiring interconnectivity or synchronization

**Homogeneous distributed database**
- Stored at multiple locations
- All locations using the same DBMS. Coordinated with a global schema
- Access is through a common DBMS and schema

**Heterogeneous distribute database**
- Stored at multiple locations
- Different DBMS and may have local schemas
- Access is through distinct DBMSs. May have global and local schemas in operation

-----

## Protecting the Database

### Transaction Logging
- Log all updates including change, date, time, user
- Helps to prevent fraud
- Recovery mechanism for failures

Every database has a transaction log that records all transactions and the database modifications made by each transaction.

The transaction log is a critical component of the database. If there is a system failure, you will need that log to bring your database back to a consistent state.

### Concurrency and Update Controls
- **Transaction**
  - A piece of work with several steps, either all must complete or none must be accepted
- **Database lock**
  - A technique to apply exclusive control to a portion of the database to one user at a time
- **Shared or read lock**
  - A lock where multiple transactions (users) may read the data
- **Exclusive or write lock**
  - A lock where only one transaction (user) may access the locked portion of the database

#### Data Security

- The process of protecting digital data, such as those in a database, from destructive forces and from unauthorized users.
- Prevention of unauthorized access, use, disruption, modification or destruction of data in storage.

#### Information Security (InfoSec)
- The practice of protecting information by mitigating information risks.
- Prevention of unauthorized access, use, disruption, modification or destruction of information

Data security is a layer of Information Security. Data is a part, and information is the whole.

-----

## Quiz:

### Others

Every database in a DBMS consists of two separate data stores.​
- true

The domain data in a database is sometimes referred to as metadata.​
- false

A local business office with a small database which is only used by two or three users would most probably implement a desktop DBMS.​
- false

A phased database development and deployment (using iterative development) is usually the safest approach to deploying the best database solution.​
- false

In an iterative approach to software development, it is usually best to develop the database in the first few iterations.​
- true

To ensure that the database is designed correctly, an important member of the project team is the data administrator.​
- false

In a one-to-many association the primary key of the "many" class is placed as a foreign key in the "one" class.​
- false

Including a total amount field as the sum of other fields in a table is a violation of second normal form.​
- false

GUID stands for ______ ______ ______.​
- globally unique identifier

### DB Schema

A(n) ____________________ describes the structure, content, and access controls of a physical data store or database.​
- schema

A(n) ____ describes the structure, content, and access controls of a physical data store or database.​
- schema

### Distributed DB

Which of the following contains both global and local schemas with distinct DBMSs?​
- heterogeneous distributed database

In a distributed database when the data is divided so that separate rows of the same table are at distinct locations that is referred to as _________.​
- horizontal partitioning

A database that is stored at multiple locations but which does not need to be interconnected or synchronized is called a(n) ______ ______.​
- decentralized database

A distributed database configuration where all databases use the same DBMS and have a global schema is called a(n) ______ ______ ______.​
- homogeneous distributed database

A distributed database configuration which contains both global and local schemas and which allows purely local data is called a(n) ______ ______ ______.​
- heterogeneous distributed database

In a distributed database configuration when all the tables are copied to all locations that is called _____ ______​
- database synchronization

When it is necessary to update one database copy with changes made to the other database, it is called _________.​
- synchronization

A technique for protecting the database wherein every update to the database is recorded with audit information is called ______ ______.​
- transaction logging

​When there is a piece of work or an action that includes several steps and updates to the data and which all must complete to be valid, that piece or work is called a(n) _______.
- transaction

### DB locks

A write lock on a database allows other users to read the data, but they cannot update any data.​
- false

A database lock that does not allow another user to update the data is called what?​
- write lock

The technique of applying exclusive control to a part of the database to one user at a time is called a(n) ______ ______.​
- database lock

A lock on a portion of the database by one user, which allows other users to read the data is called a(n) ______ ______.​
- read lock

A lock on a portion of the database by one user, which does not allow other users to read or access the data is called a(n) ______ ______.​
- write lock

Another name for a read lock is a(n) ______ ______.​
- shared lock

Another name for a write lock is a(n) ______ ______.
- exclusive lock

### Referential integrity 

A constraint which is stored in the schema and which ensures that all foreign keys have associated primary keys is called a(n) ______ ______ ______.​
- referential integrity constraint

Referential integrity is a consistent relational database state in which every foreign key value also exists as a primary key value.
- true

The condition that requires that every value in a foreign key must have an equivalent value as the primary key in another table is called ________ ______.
- referential integrity

____ is a consistent relational database state in which every foreign key value also exists as a primary key value.​
- referential integrity

Referential integrity is normally enforced by the ____.​
- database management system

### Normalization

___________ is where the value in one field determines the value in another field in the same record.​
- functional dependency

Non-key ("bad") redundancy can be systematically identified and eliminated from a relational database by ____________________ of the database.​
- normalization

A relational database table is in ____________________ normal form if it has no repeating fields or groups of fields, i.e. if it has the same number of columns for every row.​
- first

A formal technique for transforming a relational schema to an equivalent one that eliminates data anomalies is called _______.​
- normalization

A database table is in _____ _____ _____ if all non-key attributes are functionally dependent on the entire key.
- first normal form

A database table is in _____ _____ _____ if no non-key attributes are functionally dependent on any other non-key attributes.​
- third normal form

A relational database table is in ____ if it has no repeating fields or groups of fields, and hence all rows have the same columns.​
- first normal form

A relational database table is in ____ if every non-key field is functionally dependent on the primary key.​
- second normal form

A relational database table is in ____ if no non-key field is functionally dependent on any other non-key field.​
- third normal form

What can be said about the following relational database table? [CourseSectionID, StudentID, Grade, StudentName]
- in first normal form

​What can be said about the following relational database table? [StudentID, Name, Major, CreditsCompleted, GPA, AcademicStanding]
- in first and second normal form

### Relational DB Concepts

A relation describes the structure, content, and access controls of a physical data store or database.​
- False

Every table in a relational database must have a foreign key.​
- false

A foreign key is a field or set of fields stored in one table that also exists as a primary key in another table.​
- true

Relationships in a relational database are usually represented by embedding a foreign key in each participating table.​
- false

Classes that participate in a classification hierarchy can be represented within a relational database as a set of tables with the primary key of the general class table replicated in the other tables.​
- true

Classes that participate in a classification relationship can only be represented within a relational database as a single table containing all the attributes in each class.​
- false

Problem domain modeling and database normalization are incompatible techniques for relational database design.​
- false

One-to-many and many-to-many relationships are both represented by foreign keys in a relational database.​
- true

Relationships between tables is usually indicated through the use of a foreign key.​
- true

### Relational Database Items

Data elements in a relational database are organized into ____.​
- tables

In a database a two-dimensional data structure consisting of columns and rows is called a(n) _______.​
- table

Each class on an class diagram is represented by a(n) ____ in a relational database.​
- table

All ____ in a table are guaranteed to be unique if the table's primary key is guaranteed to be unique.​
- columns

​In a database table a tuple is the same thing as a(n) ______.
- row

In a database table a column is the same thing as a(n) ______.​
- attribute

In a relational database, a row can be referred to as a(n) ____.​
- tuple

A relational database table is in third normal form (3NF) if it is in second normal form (2NF) and if every non-key field is functionally dependent on the primary key.
- false

A relational database table is in third normal form (3NF) if it is in second normal form (2NF) and if no non-key field is functionally dependent on any other non-key field.​
- true

____ are a critical element of relational database design because they are the bases for representing relationships among tables.​
- keys

An attribute or set of attributes that uniquely define the rows in a table is called a(n) ______.​
- key

A(n) ____ is a field or set of fields used to uniquely identify each row.​
- primary key

If there is more than one field in a database table that is unique for all rows only one of those fields will be identified as the ______ ______ for the table.​
- primary key

In a many-to-many association, the primary key of the created table consists of which of the following?
- the primary keys of the associated tables

If there is more than one field in a database table that is unique for all rows each one may be called a(n) ______ _____.​
- candidate key

A(n) ____________________ is a field or set of fields stored in one table that also exist as a primary key in another table.​
- foreign key

A(n) ____ is a field or set of fields stored in one table that also exists as a primary key in another table.​
- foreign key

​One column of a table in a relational database is called a(n) ____.
- attribute

​A separate relation must be created to store the attributes of a ____ relationship among two other classes.
- many to many

Which of the following is not a synonym of the others?​ [row, tuple, record, field]
- field

Which of the following is not a synonym of the others?​ [column, attribute, field, tuple]
- tuple

### DB management infrastructures

Which of the following is NOT a component or function of a typical database management system (DBMS)?​
- low level process management

A relational database management system stores data in tables.​
- True

Microsoft SQL Server is an example of what?​
- database management system

A _______ is an integrated collection of stored data that is centrally managed and controlled​
- database

A software system whose purpose is to manage and control the data in a database is called a(n) _______ _______ ______.​
- database management system

What does DBMS stand for?
- database management system

What does DBA stand for?​
- database administrator

The person who is in charge of the structure and integrity of the data is called the _____ _____.​
- data administrator

Which is not one of the responsibilities of the DA?​
- establish user authentication for data access

Which is NOT one of the responsibilities of the database administrator?​
- determine data confidentiality


The person who is in charge of the safety and operation of the DBMS is called the _____ _____.​
- database administrator

A specific type of DBMS that organizes the data into tables is called a(n) ______ ______ _____ _____.​
- relational database management system

​What does SQL stand for?
- structured query language

______ ______ ______ is a query language used to access and update the data in a relational database.​
- structured query language

### Data Types

A data type that is supported directly by computer hardware or a programming language is called a(n) _______.​
- primitive data type

A data type that is defined by extending or combining other data types is called a(n) ______.​
- complex data type

A field in a relational table called "address" would be an example of what?​
- complex data type

