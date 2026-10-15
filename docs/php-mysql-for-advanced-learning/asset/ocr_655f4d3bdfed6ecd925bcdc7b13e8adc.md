```
DELIMITER ;
```

```
//To Execute or Call procedure myproc
```

```
call myproc();
```

# Explanation:

+   - We use the delimiter to indicate the start or end of the stored procedure. The last command (DELIMITER; ) changes the delimiter back to the semicolon (;).
+   - We use the CREATE PROCEDURE state ment to create a new stored procedure. We specify the name of stored procedure after the CREATE PROCEDURE statement. We put the parentheses after the name of the stored procedure.
+   - The section between BEGIN and END is called the body of the stored procedure. You put the declarative SQL statements in the body to handle business logic.

# Store procedure with parameters

```
DELIMITER //

CREATE PROCEDURE proc(IN city1 VARCHAR(50))

BEGIN

SELECT * FROM users WHERE city = city1;

END //

DELIMITER ;
```