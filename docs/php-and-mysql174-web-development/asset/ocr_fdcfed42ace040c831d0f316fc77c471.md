# CUSTOMERS

| CustomerID | Name | Address | City |
| --- | --- | --- | --- |
| 1 | Julie Smith | 25 Oak Street | Airport West |
| 2 | Alan Wong | 1/47 Haines Avenue | Box Hill |
| 3 | Michelle Arthur | 357 North Road | Yarraille |

# ORDERS

| OrderID | CustomerID | Amount | Date |
| --- | --- | --- | --- |
| 1 | 3 | 27.50 | 02-Apr-2007 |
| 2 | 1 | 12.99 | 15-Apr-2007 |
| 3 | 2 | 74.00 | 19-Apr-2007 |
| 4 | 2 | 6.99 | 01-May-2007 |

Figure 8.2 Each order in the Orders table refers to a customer from the Customers

The relational database for this relationship is foreign key. CustomerID is the primary key in Customers, but when it appears in another table, as Orders, it is referred to as a foreign key.

You might wonder why we chose to have two separate tables. Why not just Julie's address in the Orders table? We explore this issue in more detail in the next section.

# Schemas

The complete set of design tables for a database is called the database schema. It is akin to a blueprint for a database. A schema shows the tables with their columns, the primary key of each table and any foreign keys. A schema does not include any data, but you might want to sample data with your schema to explain what it is for. The schema can be shown in informal diagrams as we have done, in entity relationship diagrams (which are not covered in this book), or in a text form, such as

```
Customers(CustomerID, Name, Address, City)
Orders(OrderID, CustomerID, Amount, Date)
```

Underlined terms in the schema are primary keys in the relation in which they are underlined. Italic terms are foreign keys in the relation in which they appear italic.