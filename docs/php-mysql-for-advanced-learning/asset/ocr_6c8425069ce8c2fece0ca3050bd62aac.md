# MYSQL – Triggers

A SQL trigger is a set of SQL statements stored in the database. it is fired whenever an event associated with a table occurs e.g., insert, update or delete.

The main difference between a trigger and a stored procedure is that a trigger is called automatically when a data modification event is made against a table whereas a stored procedure must be called explicitly.

It is important to understand SQL trigger's advantages and disadvantages so that you can use it appropriately.

# Advantages of using SQL triggers

SQL triggers provide an alternative way to check the integrity of data.

SQL triggers provide an alternative way to run scheduled tasks.

SQL triggers are very useful to audit the changes of data in tables.

# Disadvantages of using SQL triggers

SQL triggers only can provide an extended validation and they cannot replace all the validations.

SQL triggers are invoked and executed invisible from the client applications; therefore, it is difficult to figure out what happen in the background.