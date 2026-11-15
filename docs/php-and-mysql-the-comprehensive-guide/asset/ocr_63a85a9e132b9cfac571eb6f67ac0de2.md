```
'We can post childhood photos of you? On the other hand ... ')
COMMIT
GO
```

On COMMIT and GO, the changes are sent to the database. Most databases use autocommit; that is, all SQL commands are sent directly to the database. However, this behavior can be changed. The counterpart of COMMIT is ROLLBACK, which reverses the transaction steps that have already been carried out.

# 17.6.5 Stored Procedures

Another special feature that is not supported by many databases is stored procedures (embedded procedures). The idea behind this is that program logic is taken out of the application and placed in the database. Procedures—functions—are stored in the database. These can then be called from the outside. This is also practical with regard to the security of a web application: the PHP application does not have write access to the database but can execute predefined stored procedures. Here is an example of how to enter data into the database:

```
CREATE PROCEDURE sp_addentry (
    @user INT,
    @entry VARCHAR(50)
) AS
INSERT INTO entry (user_id, entry, date) VALUES
    (@user, @entry, getdate())

GO
```

The parameters for the stored procedure can be used within the procedure by their name.

> **Tip**
> The getdate() function used in the SQL command is a function integrated into some databases that returns the current date.

This has given you a first insight into database programming. The SQL commands shown in this chapter enable you to create standard applications and much more. You will find many of the elements shown here in the next chapters. There will also be a guestbook example again—but for the sake of simplicity, only with one table.