# Physical schema

Physical schema: an implementation of a logical schema into a specific DBMS (database management system), showing how data is stored, indexed or accessed.

Physical schema includes specifics of storage devices, access methods, indexing, partitioning, access methods, views and configuration of the database on the storage media. It translates the logical schema into an implementation that fits the requirements of a specific database management system.

In the previous example:

Tables:

```
Products
ProductID: INT PRIMARY KEY AUTO_INCREMENT
ProductName: VARCHAR(100) NOT NULL
Price: REAL NOT NULL
INDEX on ProductName for faster access based on the product name
```

```
Orders
OrderID: INT PRIMARY KEY AUTO_INCREMENT
OrderDate: DATE NOT NULL
CustomerID: INT FOREIGN KEY NOT NULL
ProductID: INT FOREIGN KEY NOT NULL
INDEX on CustomerID and ProductID for faster joins
```

```
Customers
CustomerID: INT PRIMARY KEY AUTO_INCREMENT
LastName: VARCHAR(100) NOT NULL
FirstName: VARCHAR(100) NOT NULL
EmailAddress: VARCHAR(100) NOT NULL UNIQUE
INDEX on LastName for faster access based on the last name
```

Storage parameters:

+   - Use indices described above for fast retrieval of data.
+   - Partition large tables like Orders by OrderID to improve query performance.

# A3.2.2 Entity-relationship diagrams

Entity-relationship diagram: a visual representation of the entities in a database and the relationship between them.

An entity-relationship diagram (ERD) is a visual representation of the entities in the database and the relationship between them.

Besides providing a clear overview of the database structure, ERDs facilitate communication between stakeholders; act as documentation for the database design; support future development and maintenance of the database; and ensure data integrity and consistency through constraints and well-defined relationships.

For the sales system with Products, Orders and Customers entities, the ERD looks like this:

![](bbox=[0.285, 0.745, 0.89, 0.88])