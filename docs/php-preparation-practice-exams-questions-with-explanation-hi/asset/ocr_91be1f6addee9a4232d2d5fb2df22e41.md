B. CREATE TABLE users (id INT AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(100), email VARCHAR(100));

C. CREATE TABLE users (id INT UNIQUE, name VARCHAR(100),
email VARCHAR(100) NOT NULL);

D. CREATE TABLE users (id INT, name TEXT, email TEXT);

Correct Answer: B

Explanation: The correct SQL statement is CREATE TABLE users (id INT
AUTO_INCREMENT PRIMARY KEY, name VARCHAR(100), email
VARCHAR(100)); This statement properly defines a table users with id as
an integer that automatically increments with each new record, while also
designating it as the primary key. The fields name and email are defined
with appropriate data types, ensuring effective data storage.

Question 68. In PHP, what is the primary purpose of using transactions
when executing multiple SQL queries against a database, and how does this
hance data consistency?

+   A. To improve query performance.
B. To ensure all queries are executed as a single unit of work.
C. To automatically create backups of the database.
D. To simplify SQL syntax.

Correct Answer: B

Explanation: The primary purpose of using transactions in PHP when
executing multiple SQL queries is to ensure that all queries are executed as
a single unit of work. This means that if one query fails, all other changes
made during the transaction can be rolled back, maintaining data
consistency and integrity. Transactions are crucial in scenarios where
multiple related operations need to succeed or fail together.

Question 69. When working with databases in PHP, how can the
PDO::FETCH_OBJ fetch style be advantageous, and what does it return
when fetching data from the database?

+   A. It returns a numeric array of column values.
B. It returns an associative array of column names and values.