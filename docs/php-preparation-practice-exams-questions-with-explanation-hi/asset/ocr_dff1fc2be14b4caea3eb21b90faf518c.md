Explanation: A significant disadvantage of using the mysql_ functions in PHP is that they do not support prepared statements. This lack of support makes applications vulnerable to SQL injection attacks, as user input can directly influence the SQL query structure. This is a critical issue in modern web applications where security is paramount, leading to the recommendation to use the MySQLLi or PDO extensions instead.

# **Question 89.** When configuring error handling in a PHP application that connects to a MySQL database, what is the recommended practice to ensure that issues encountered during database interactions are properly logged and do not expose sensitive information to users?

+   A. Display detailed error messages directly to the user.

+   B. Use die() to terminate the script on error.

+   C. Implement custom error handling and log errors to a file without displaying them.

+   D. Ignore errors to avoid disrupting your user experience.

Correct Answer: C

Explanation: The recommended practice for error handling in a PHP application connecting to a MySQL database is to implement custom error handling that logs errors to a file while avoiding displaying detailed error messages to users. This approach protects sensitive information, maintains a clean interface, and allows developers to review and address issues without exposing vulnerabilities to potential attackers.

# **Question 90.** In the context of integrating PHP with a relational database, which of the following strategies is most effective for ensuring data consistency across multiple tables during complex transactions?

+   A. Using a single SQL query to update all tables simultaneously.

+   B. Relying on application logic to ensure data consistency.

+   C. Employing foreign keys and cascading actions alongside transactions.

+   D. Performing updates on one table at a time without transactions.

Correct Answer: C