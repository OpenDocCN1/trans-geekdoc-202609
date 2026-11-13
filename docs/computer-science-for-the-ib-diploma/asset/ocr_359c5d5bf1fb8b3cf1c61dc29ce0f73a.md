III ROLLBACK: Used to undo all changes made during the current transaction. It reverts the database to the state it was in before the transaction began.

In the example below, the two UPDATE statements are reversed, and so the table would reach its state prior to the updates being made.

```
BEGIN TRANSACTION;
UPDATE Employees SET Salary = Salary + 100 WHERE EmployeeID = 1;
UPDATE Employees SET Salary = Salary - 100 WHERE EmployeeID = 5;
ROLLBACK;
```

# TOK

# How has the development of database technology influenced the way we acquire and process knowledge?

The development of database technology has profoundly influenced the ways in which we acquire and process knowledge, touching on key areas such as the nature of knowledge, how it is shared and the ethical considerations involved.

Databases store vast amounts of data, but this raw data only becomes useful when it is processed into information and then interpreted as knowledge. This raises questions about the nature of knowledge itself. How do we distinguish between data, information and knowledge? How does the structure of a database influence what we consider to be true or valuable knowledge?

Databases rely on structured query languages (SQL) and other forms of data communication. The precision and clarity required in database queries contrast with the ambiguity and richness of natural language. This might lead to a more structured, but potentially limited, way of knowing. How does the structured nature of database queries influence our understanding of complex or ambiguous information?

# REVIEW QUESTIONS

+   1. Discuss whether a view is physically stored in a database.
+   2. Define the term “database transaction”.
+   3. Identify a reason a transaction may need to be rolled back by giving an example.
+   4. State the effect of rolling back a transaction.
+   5. Describe the four properties that describe a transaction.