![](bbox=[0.27, 0.095, 0.7, 0.25])

Formulate the following as single queries in relational algebra.

+   (a) List the customerNr of each customer who has been charged less than the list price for at least one software item, but has been sold no word processor.
+   (b) List the name of each customer who was sold at least one copy of all the spreadsheets on the stock list.
+   (c) List the customerNr of each customer who has purchased a copy of all the word processors that are in stock but who has never purchased a database.
+   (d) List the customerNr of those customers who purchased both a spreadsheet and word processor on the same invoice.

# 12.2 Relational Database Systems

We may now define a relational DBMS as a DBMS that has the relational table as its only essential data structure and supports the selection, projection, and join operations without needing specification of physical access paths. A relational system that supports all eight table operations of the relational algebra is said to be relationally complete. This doesn’t entail eight distinct operators for these tasks; rather, the eight operations must be expressible in terms of the table operations provided by the system.

The two main relational languages are SQL and QBE, with SQL being the most important. Most SQL systems are relationally complete. A system that supports all aspects of the relational model, including domains and the two basic integrity rules (entity integrity and referential integrity), is sometimes said to be “fully relational”. The relational model of data itself is evolving.

For Version 1 of the relational model, Codd proposed 12 basic rules to be satisfied by a relational DBMS. These may be summarized as follows:

+   1. All information is represented in relational tables.
+   2. All data is accessible using the table name, primary key value, and column name.
+   3. Systematic support for missing information (null values, independent of data type) must be provided.
+   4. The relational schema itself is represented in tables and is accessible in the same way as the database.