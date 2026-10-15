# Mysql – Stored Procedure:

Typically stored procedures help increase the performance of the applications. Once created, stored procedures are compiled and stored in the database. However MySQL implements the stored procedures slightly different. MySQL stored procedures are compiled on demand. After compiling a stored procedure, MySQL puts it to a cache.

Stored procedure helps reduce the traffic between application and database server because instead of sending multiple lengthy SQL statements, the application has to send only name and parameters of the stored procedure.

Stored procedures are secure. Database administrator can grant appropriate permissions to applications that access stored procedures in the database without giving any permission on the underlying database tables.

Note: do not create so many stored procedures as they took lot of memory.

# Example

```
```sql
DELIMITER //
CREATE PROCEDURE myproc()
BEGIN
SELECT * FROM users where city='gurgaon';
END //
```
```