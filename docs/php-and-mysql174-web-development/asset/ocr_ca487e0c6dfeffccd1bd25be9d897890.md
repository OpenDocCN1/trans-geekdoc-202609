# Relationships

Foreign keys represent a relationship between data in two tables. For example, the link from Orders to Customers represents a relationship between a row in the Orders table and a row in the Customers table.

Three basic kinds of relationships exist in a relational database. They are classified by the number of elements on each side of the relationship. Relationships can be one-to-one, one-to-many, or many-to-many.

A one-to-one relationship means that one of each thing is used in the relationship. For example, if you put addresses in a separate table from Customers, they would have a one-to-one relationship between them. You could have a foreign key from Addresses to Customers or the other way (both are not required).

In a many-to-many relationship, rows in one table are linked to many rows in another table. In this example, one Customer might place many Orders. In these relationships, the table that contains many rows has a foreign key to the table with one row. Here, we put the CustomerID into the Order table to show the relationship.

In a many-to-one relationship, many rows in one table are linked to one row in another. For example, if you have two tables, Books and Authors, you might find that one book was written by two coauthors, each of whom had written other books, on their own or with other authors. This type of relationship usually gets a table to itself, so you might have Books, Authors, and Books_Authors. This third table would contain only the keys of the other tables as foreign keys in pairs, to show which authors are involved with which books.

# Designing Your Web Database

Knowing when to need a new table and what the key should be is something of an art. You can read information about entity relationship diagrams and database normalization, which are beyond the scope of this book. Most of the time, however, you can follow a few basic design principles. Let's consider them in the context of Book-O-Rama.

# Think About the Real-World Objects You Are Modeling

When you create a database, you are usually modeling real-world items and relationships and storing information about those objects and relationships.

Generally, each class of real-world objects needs its own model. Think about it: You want to store the same information about all your customers. If a set of data has the same “shape,” you can easily create a table corresponding to that data.

In the Book-O-Rama example, you want to store information about customers, the books that you sell, and details of the orders. The customers all have names and addresses. Each order has a date, a total amount, and a set of books that were ordered. Each book has an International Standard Book Number (ISBN), an author, a title, and a price.