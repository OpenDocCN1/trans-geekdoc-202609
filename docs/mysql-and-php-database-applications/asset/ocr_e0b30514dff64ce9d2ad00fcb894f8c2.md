# Part I: Working with MySQL

In Chapter 2, we demonstrate how to create tables in MySQL. It's easy enough to create tables with all the columns necessary for primary keys and foreign keys. However, in MySQL foreign keys do not have the significance they have in most database systems.

In packages like Oracle, Sybase, or Postgres, tables can be created that explicitly define foreign keys. For instance, using the tables 1-3 and 1-4 with Oracle, the database system is aware that the company_id column in the Contacts table had a relationship to the Companies table. This is potentially a very good thing. If the database system is aware of a relationship, it can check to make sure the value being inserted into the foreign key exists in the referenced table. If it does not, the database system will reject the insert. This is known as referential integrity.

To achieve the same effect in MySQL, the application developer must add extra steps before inserting or updating records. For example, to be ultra-safe, the programmer needs to go through the following steps in order to insert a row in the Contacts table (1-4):

+   1. Get all of values for company_id in the Companies table.
2. Check to make sure the value for company_id you are going to insert into the Contacts table exists in the data you retrieved in step 1.
3. If it does, insert values.

The developers of MySQL argue that referential integrity is not necessary and including it would slow down MySQL. Further, they argue that it is the responsibility of applying interacting with the database to ensure that the inserted data is correct. There is logic to this way of thinking. In Parts III and IV of this book we present several applications that work without enforcing referential integrity or the method of checking shown above. In general, in these applications, all the possible values are pulled from a database anyway and there's very little opportunity for errors creep into the system.

For example, using PHP and HTML, the programmer might turn the Companies table into a drop-down box. That way the user can only choose a value.

# Transactions

In relational databases, things change in groups. As shown in a variety of applications in this book, many changes require that rows be updated in several tables concurrently. In some cases, tables may be dropped as part of a series of statements that get the data where it needs to. An e-commerce site may contain code like the following:

+   1. Insert customer into the Customers table.
2. Add invoice information into the Invoice table.
3. Remove a quantity of 1 ordered item from the Items table.