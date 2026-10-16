```
or die ("Couldn't execute query.");
$row = mysql_fetch_array($result,MYSQL_ASSOC);
if ( $userEntry == $row['password'] )
{
    echo "Login accepted<br>";
    statements that display Members Only Web pages
}
else
{
    echo "Invalid password<br>";
    statements that allow user to try another password
}
```

Note the following points about the preceding statements:

+   - The SELECT query requests only one field (password) from one row (row for gsmith).
+   - The mysql_fetch_array function returns an array called $row with column names as keys.
+   - The if statement compares the password that the user typed in ($userEntry) with the password obtained from the database ($row['password']) to see whether they are the same by using two equal signs (==).
+   - If the comparison is true, the passwords match, and the if block (which displays the Members Only Web pages) is executed.
+   - If the comparison is not true, the user did not enter a password that matches the password stored in the database, and the else block is executed. The user sees an error message stating that the password is not correct and is returned to the login Web page.

![](bbox=[0.12, 0.62, 0.2, 0.72])

PHP provides a shortcut that is convenient for using the variables retrieved with the mysql_fetch_array function. You can use the extract function, which splits the array into variables that have the same name as the key. For instance, you can use the extract function to rewrite the previous statements that test the password. Here's how:

```
$userEntry = "secret"; #password user entered into HTML form
$query = "SELECT password FROM Member
          WHERE loginName='gsmith'";
$result = mysql_query($query)
    or  die ("Couldn't execute query.");
$row = mysql_fetch_array($result,MYSQL_ASSOC);
extract($row);
if ( $userEntry == $password )
{
    echo "Login accepted<br>";
    statements that display Members Only Web pages
}
else
```