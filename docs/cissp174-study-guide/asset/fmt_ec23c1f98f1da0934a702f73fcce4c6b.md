
| SSN | Vacation Time | Sick Time |
| --- | --- | --- |
| 343-53-4334 | 60 days | 90 days |
| 425-22-8422 | 10 days | 15 days |
| 737-54-2268 | 3 days | 1 day |
| 990-69-4771 | 15 days | 5 days |

### Referential, Semantic, and Entity Integrity

Databases must ensure the integrity of the data in the tables: this is called data integrity, discussed in the “[Database Integrity](#Ch009_459-508_B9780443187346000088.xhtml#s0240)” section below. There are three additional specific integrity issues that must be addressed beyond the correctness of the data itself: Referential, Semantic, and Entity Integrity. These are tied closely to the logical operations of the DBMS.

*Referential integrity* means that every foreign key in a secondary table matches a primary key in the parent table: if this is not true, referential integrity has been broken. *Semantic integrity* means that each attribute (column) value is consistent with the attribute data type. *Entity integrity* means each tuple has a unique primary key that is not null. The HR database table shown in [Table 9.2](#Ch009_459-508_B9780443187346000088.xhtml#t0015), seen previously, has referential, semantic, and entity integrity. [Table 9.3](#Ch009_459-508_B9780443187346000088.xhtml#t0020), on the other hand, has multiple problems: one tuple violates referential integrity, one tuple violates semantic integrity, and the last two tuples violate entity integrity.

[Table 9.3](#Ch009_459-508_B9780443187346000088.xhtml#B-t0020)

Database Table Lacking Integrity.

| SSN | Vacation Time | Sick Time |
| --- | --- | --- |
| 467-51-9732 | 7 days | 14 days |
| 737-54-2268 | 3 days | Nexus 6 |
| 133-73-1337 | 16 days | 22 days |
| 133-73-1337 | 15 days | 20 days |

The tuple with the foreign key `467-51-9732` has no matching entry in the employee database table. This breaks referential integrity: there is no way to link this entry to a name or title. Cell “Nexus 6” violates semantic integrity: the sick time attribute requires values of days, and “Nexus 6” is not a valid amount of sick days. Finally, the last two tuples both have the same primary key (primary to this table; foreign key to the parent employees table); this breaks entity integrity.

### Database Normalization

Database *normalization* seeks to make the data in a database table logically concise, organized, and consistent. Normalization removes redundant data, and improves the integrity and availability of the database. Normalization has three rules, called forms (see [http://www.informit.com/articles/article.aspx?p=30646](http://www.informit.com/articles/article.aspx?p=30646) for more information):

*   **First Normal Form (1NF):** Divide data into tables.
*   **Second Normal Form (2NF):** Move data that is partially dependent on the primary key to another table. The HR Database ([Table 9.2](#Ch009_459-508_B9780443187346000088.xhtml#t0015)) is an example of 2NF.
*   **Third Normal Form (3NF):** Remove data that is not dependent on the primary key [[26]](#Ch009_459-508_B9780443187346000088.xhtml#bb0135).

### Database Views

Database tables may be queried; the results of a query are called a *database view*. Views may be used to provide a *constrained user interface*: for example, non-management employees can be shown their individual records only via database views. [Table 9.4](#Ch009_459-508_B9780443187346000088.xhtml#t0025) shows the database view resulting from querying the employee table “Title” attribute with a string of “Detective.” While employees of the HR department may be able to view the entire employee table, this view may be authorized for the captain of the detectives, for example.

[Table 9.4](#Ch009_459-508_B9780443187346000088.xhtml#B-t0025)

Employee Table Database View “Detective.”

| SSN | Name | Title |
| --- | --- | --- |
| 425-22-8422 | Gaff | Detective |
| 737-54-2268 | Rick Deckard | Detective |

### The Data Dictionary

The *data dictionary* contains a description of the database tables. This is called *metadata*: data about data. The data dictionary contains database view information, information about authorized database administrators, user accounts including their names and privileges, and auditing information, among others. A critical data dictionary component is the *database schema*: it describes the attributes and values of the database tables. [Table 9.5](#Ch009_459-508_B9780443187346000088.xhtml#t0030) shows a very simple data dictionary that describes the two tables we have seen previously this chapter: employees and HR.

[Table 9.5](#Ch009_459-508_B9780443187346000088.xhtml#B-t0030)

Simple Database Schema.

| Table | Attribute | Type | Format |
| --- | --- | --- | --- |
| Employee | SSN | Digits | `###-##-####` |
| Employee | Name | String | `<30 characters>` |
| Employee | Title | String | `<30 characters>` |
| HR | SSN | Digits | `###-##-####` |
| HR | Sick Time | Digits | `### days` |
| HR | Vacation Time | Digits | `### days` |

### Database Query Languages

Database query languages allow the creation of database tables, read/write access to those tables, and many other functions. Database query languages have at least two subsets of commands: *Data Definition Language* (DDL) and *Data Manipulation Language* (DML). DDL is used to create, modify, and delete tables. DML is used to query and update data stored in the tables.

The most popular relational database query language is SQL (Structured Query Language), created by IBM in 1974. Many types of SQL exist, including MySQL, PostgreSQL, PL/SQL (Procedural Language/SQL, used by Oracle), T-SQL and ANSI SQL (used by Microsoft SQL), and many others.

Common SQL commands include:

*   **CREATE:** create a table
*   **SELECT:** select a record
*   **DELETE:** delete a record (or a whole table)
*   **INSERT:** insert a record
*   **UPDATE:** change a record

Tables are created with the `CREATE` command, which uses Data Definition Language to describe the format of the table that is being created. An example of a Data Manipulation Language command is `SELECT`, which is used to search and choose data from a table. The following `SELECT` command could be used to create the database view shown in [Table 9.4](#Ch009_459-508_B9780443187346000088.xhtml#t0025):

```
SELECT * FROM Employees WHERE Title = "Detective"
```

This means: show any (“*”) records where the Title is “Detective.”

### Hierarchical Databases

Hierarchical databases form a tree: the global Domain Name Service (DNS) servers form a global tree. The root name servers are at the “root zone” at the base of the tree; individual DNS entries form the leaves. `www.syngress.com` points to the `syngress.com` DNS database, which is part of the dot com (.com) top level domain (TLD), which is part of the global DNS (root zone). From the root, you may go back down another branch, down to the dot gov (.gov) TLD, to the `nist.gov` (National Institute of Standards and Technologies) domain, to `www.nist.gov`.

A special form of hierarchical database is the *network model* (referring to networks of people, not data networks): this allows branches of a hierarchical database to have two parents (two connections back to the root). Imagine an organization’s org chart is stored in a database that forms a tree, with the CEO as the root of the hierarchy. In this company, the physical security staff reports to both facilities (for facility issues) and IT (for datacenter physical security). The network model allows the physical security staff to have “two bosses” in the hierarchical database: reporting through an IT manager and a facilities manager.

### Object-Oriented Databases
