# # How to drop a table

Figure 17-6 shows how to use the DROP TABLE statement. When you use this statement, use it cautiously, especially when you’re working on a production database.

You can use the DROP TABLE statement to delete the definition of a table. In addition, the DROP TABLE statement deletes all data that’s stored in the table. In this figure, for instance, the first example drops the customers table. However, if the customers table doesn’t exist, this generates an error that stops a SQL script from continuing. To prevent this error, you can add the IF EXISTS keywords to the DROP TABLE statement as shown in the second statement.

If you have configured MySQL to enforce referential integrity for your database, MySQL checks whether other tables depend on the table you’re trying to drop. If so, MySQL won’t allow you to drop the table. For example, you can’t delete the customers table if a foreign key in the orders table refers to the customers table. In that case, you must drop the orders table before you can drop the customers table.

When you drop a table, MySQL also drops any indexes that have been defined for that table. In the next figure, you’ll learn how to work with the indexes of a table.