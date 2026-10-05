A. Transactions automatically commit after each statement execution.

B. Using transactions helps ensure data integrity by allowing rollback in case of errors.

C. Transactions are only applicable in MySQL databases and not in others.

D. Transactions cannot be used with prepared statements.

Correct Answer: B

Explanation: The statement that transactions help ensure data integrity by allowing rollback in case of errors is true. Transactions enable the execution of multiple SQL statements as a single unit, ensuring that all operations are successful; if any operation fails, all changes can be rolled back to maintain the database's integrity.

# Question 100. When using PHP to execute a database query that returns multiple rows, which of the following methods is appropriate to fetch all the resulting rows into an array for further processing?

+   A. mysqli_fetch_array()

+   B. mysqli_fetch_all()

+   C. mysqli_fetch_assoc()

+   D. mysqli_fetch_object()

Correct Answer: B

Explanation: The mysqli_fetch_all() function retrieves all result rows from a query as an array, which can then be easily processed or iterated over in PHP. This function is particularly useful when handling queries that return multiple rows, allowing developers to access all data in one operation efficiently.