Understanding these lines is easier if you recall the basic syntax of an INSERT statement in SQL:

```
INSERT INTO tbl_table
(field1, field2, field3)
VALUES
('value1', 'value2', 'value3')
```

The ASP, ColdFusion, and PHP code blocks are constructing SQL statements that use this syntax. But again, since they are replacing variables with actual values, you need to let each server know to evaluate these expressions before it inserts them into the database. As a consequence, you'll see quite a few pound signs in the ColdFusion version, and a lot of concatenation in the ASP and PHP versions.

> > **TIP** ASP and PHP users should use code coloring to their advantage. The coloring typically changes the moment you enter an error, making it easy to spot problems before you test the page. ASP: In all cases, Request.Form should be purple, while the form field name should always be green. The ampersands (&) used to concatenate should always be blue. PHP: In all cases, string literals (including all commas and single quotes) are red, $_POST is always light blue, while periods and square brackets are always dark blue.

> > **NOTE** ASP and PHP use both double quotes ("") and single quotes (''), which can be confusing. Content enclosed in double quotes is a part of ASP/PHP, specifically, string literals that ASP/PHP should pass without evaluating. Content enclosed in single quotes belongs to SQL, and represents the values being inserted into the database.

+   4) Insert the code that redirects the user to the master page once the insert is completed.

In ASP, before the closing %>:

```
Response.Redirect("admin_cp_master.asp")
```

In ColdFusion:

```
<cflocation url="admin_cp_master.cfm">
```

In PHP, before the closing ?>:

```
header("Location: admin_cp_master.php");
```

Because ASP, ColdFusion, and PHP will display an error message if they experience problems, the redirect line will only be executed if the insertion is successful.