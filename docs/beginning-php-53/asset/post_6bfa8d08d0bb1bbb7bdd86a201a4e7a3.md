
If you want to insert only some values, leaving NULLs or other default values in the remaining fields, use:

```sql
INSERT INTO table ( field1, field2, ... ) VALUES ( value1, value2, ... );
```

Though the first approach is compact, and perfectly valid if you want to populate all the fields in the row, the second approach is generally more flexible and readable.

So how do you insert records using your PHP script? You pass INSERT statements to MySQL via PDO in much the same way as you pass SELECT statements. If you don’t want to pass data from any PHP variables, you can use the simpler PDO::query() method — for example:

```php
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";

try {
  $conn = new PDO( $dsn, $username, $password );
  $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
  echo "Connection failed: " . $e->getMessage();
}

$sql = "INSERT INTO members VALUES ( 8, 'derek', password('mypass'), 'Derek',
  'Winter', '2008-06-25', 'm', 'crime', 'derek@example.com', 'Watching TV,
  motor racing' )";

try {
  $conn->query( $sql );
} catch ( PDOException $e ) {
  echo "Query failed: " . $e->getMessage();
}
?>
```

Notice that, although the call to $conn->query() still returns a PDOStatement object, the object is discarded in this case. There’s no result set to examine, so there’s no need to hold onto the PDOStatement object.

However, chances are that you do want to insert data that is stored in PHP variables. For example, if a member has just registered using a registration form, you’ll want to pass the form data to the INSERT statement to add the member record. The safest way to do this is to create a prepared statement using PDO::prepare(), as you did with SELECT queries in the previous chapter. You can then use placeholders in the query string for each of the field values that you want to insert, and pass the data into the query using calls to PDOStatement::bindValue(). For example:

```php
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";

try {
$conn = new PDO( $dsn, $username, $password );
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
echo "Connection failed: " . $e->getMessage();
}

$id = 8;
$username = "derek";
$password = "mypass";
$firstName = "Derek";
$lastName = "Winter";
$joinDate = "2008-06-25";
$gender = "m";
$favoriteGenre = "crime";
$emailAddress = "derek@example.com";
$otherInterests = "Watching TV, motor racing";

$sql = "INSERT INTO members VALUES ( :id, :username, password(:password),
:firstName, :lastName, :joinDate, :gender, :favoriteGenre, :emailAddress,
:otherInterests )";

try {
$st = $conn->prepare( $sql );
$st->bindValue( ":id", $id, PDO::PARAM_INT );
$st->bindValue( ":username", $username, PDO::PARAM_STR );
$st->bindValue( ":password", $password, PDO::PARAM_STR );
$st->bindValue( ":firstName", $firstName, PDO::PARAM_STR );
$st->bindValue( ":lastName", $lastName, PDO::PARAM_STR );
$st->bindValue( ":joinDate", $joinDate, PDO::PARAM_STR );
$st->bindValue( ":gender", $gender, PDO::PARAM_STR );
$st->bindValue( ":favoriteGenre", $favoriteGenre, PDO::PARAM_STR );
$st->bindValue( ":emailAddress", $emailAddress, PDO::PARAM_STR );
$st->bindValue( ":otherInterests", $otherInterests, PDO::PARAM_STR );
$st->execute();
} catch ( PDOException $e ) {
echo "Query failed: " . $e->getMessage();
}

?>
```

In this example, the variable values are hard-coded in the script. In a real-world application, you would of course receive these values from outside the script, such as via submitted form values in the `$_POST` superglobal array.

Remember that, although using prepared statements and placeholders gives you some protection against SQL injection attacks, you should always check or filter user input before doing anything with it, such as storing it in a database. You can find out more about this and other security-related issues in Chapter 20.

## Updating Records

As you saw in Chapter 12, you can alter the data within an existing table row by using an SQL UPDATE statement:

```sql
mysql> UPDATE fruit SET name = 'grapefruit', color = 'yellow' WHERE id = 2;
Query OK, 1 row affected (0.29 sec)
Rows matched: 1 Changed: 1 Warnings: 0
```

```sql
mysql> SELECT * from fruit;
```

| id | name | color |
|----|------|-------|
| 1 | banana | yellow |
| 2 | grapefruit | yellow |
| 3 | plum | purple |

3 rows in set (0.00 sec)

As with inserting new records, updating records via your PHP script is simply a case of using PDO::query() if you're passing literal values in the UPDATE statement, or PDO::prepare() with placeholders if you're passing variable values. For example, the following script changes the email address field in the “Derek Winter” record that was added in the previous section:

```php
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";

try {
$conn = new PDO( $dsn, $username, $password );
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
echo "Connection failed: " . $e->getMessage();
}

$id = 8;
$newEmailAddress = "derek.winter@example.com";

$sql = "UPDATE members SET emailAddress = :emailAddress WHERE id = :id";

try {
$st = $conn->prepare( $sql );
$st->bindValue( ":id", $id, PDO::PARAM_INT );
$st->bindValue( ":emailAddress", $newEmailAddress, PDO::PARAM_STR );
$st->execute();
} catch ( PDOException $e ) {
echo "Query failed: " . $e->getMessage();
}

?>
```

## Deleting Records

Deleting rows of data via PHP is a similar process to updating. Chapter 12 showed you how to delete rows from a table using the SQL DELETE keyword:

```sql
mysql> DELETE FROM fruit WHERE id = 2;
Query OK, 1 row affected (0.02 sec)
```

To delete rows using PHP, you pass a DELETE statement directly via PDO::query(), or create the statement using PDO::prepare() with placeholders, passing in values (such as the criteria for the WHERE clause) with PDOStatement::bindValue() and running the query with PDOStatement::execute().

The following script deletes the member record with the ID of 8 from the members table:

```php
<?php
$dsn = "mysql:dbname=mydatabase";
$username = "root";
$password = "mypass";

try {
  $conn = new PDO( $dsn, $username, $password );
  $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );
} catch ( PDOException $e ) {
  echo "Connection failed: " . $e->getMessage();
}

$id = 8;

$sql = "DELETE FROM members WHERE id = :id";

try {
  $st = $conn->prepare( $sql );
  $st->bindValue( ":id", $id, PDO::PARAM_INT );
  $st->execute();
} catch ( PDOException $e ) {
  echo "Query failed: " . $e->getMessage();
}

?>
```

Incidentally, rather than binding the value of a variable to a placeholder with PDOStatement::bindValue(), you can instead use PDOStatement::bindParam() to bind the variable itself. If you then change the value of the variable after the call to bindParam(), the placeholder value is automatically updated to the new value (in other words, the variable is bound by reference rather than by value). This can be useful if you're not sure what value you're going to pass in at the time you prepare the statement. Find out more on bindParam() in the online PHP manual at http://www.php.net/manual/en/pdostatement.bindparam.php.

## Building a Member Registration Application

Now that you know how to insert records into a MySQL table via PHP, you can write a script that lets new members sign up for your book club. Rather than reinventing the wheel, you build on the object-oriented member viewer application that you created in Chapter 13, extending the classes to add new functionality and creating a script to register new members.

### Adding More Common Code

First, add some extra code to the common.inc.php file that's inside your book_club folder. Open this file in your editor.

Within this file, it makes sense to include the other common files that are used by the rest of the application. That way, scripts only need to include common.inc.php, and the other files will be included automatically. Add the following to the start of the common.inc.php file:

```php
require_once ("config.php");
require_once ("Member.class.php");
require_once ("LogEntry.class.php");
```

Now add the following line to the CSS declarations within the displayPageHeader() function:

```css
<style type="text/css">
th { text-align: left;
background-color: #bbb; }
th, td { padding: 0.4em; }
tr.alt td { background: #ddd; }
.error { background: #d33; color: white; padding: 0.2em; }
</style>
```

This line creates a CSS .error class that you'll use to highlight any problems with the registration form.

Finally, add three extra utility functions to help with displaying the registration form:

```php
function validateField( $fieldName, $missingFields ) {
if ( in_array( $fieldName, $missingFields ) ) {
echo ' class="error"';
}
}

function setChecked( DataObject $obj, $fieldName, $fieldValue ) {
if ( $obj->getValue( $fieldName ) == $fieldValue ) {
echo ' checked="checked"';
}
}

function setSelected( DataObject $obj, $fieldName, $fieldValue ) {
if ( $obj->getValue( $fieldName ) == $fieldValue ) {
echo ' selected="selected"';
}
}
```
