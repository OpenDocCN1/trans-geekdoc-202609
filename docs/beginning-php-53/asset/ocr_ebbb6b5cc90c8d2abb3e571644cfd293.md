Finally, the method closes the database connection, then returns the data to the calling code in the form of a two-element array. The first element contains the array of `Member` objects, and the second element contains the calculated total number of rows:

```
return array( $members, $row["totalRows"] );
```

Of course, after the try block comes the corresponding catch block. This simply closes the connection and uses PHP's `die()` function to abort the script with an error message.

The next method, `getMember()`, works in a similar fashion to `getMembers()`. It retrieves a single record from the members table, as a `Member` object. The ID of the record to retrieve is specified by the argument passed to the method.

This method creates a prepared statement, much like `getMembers()` did, to retrieve the record:

```
$sql = "SELECT * FROM " . TBL_MEMBERS . " WHERE id = :id";
```

Next, the `$id` parameter's value is bound to the `:id` placeholder, and the query is run:

```
$st->bindValue( ":id", $id, PDO::PARAM_INT );
$st->execute();
```

If the query returned a row, it is retrieved using the `PDOStatement::fetch()` method, which retrieves a single row from the result set as an associative array of field names and values. This associative array is then passed to the `Member` constructor to create and populate a `Member` object, which is then returned to the calling code after closing the connection:

```
$row = $st->fetch();
parent::disconnect( $conn );
if ( $row ) return new Member( $row );
```

The final two convenience methods are used to return the `Member` object's gender and `favoriteGenre` fields as human-friendly strings, ideal for displaying in a Web page. `getGenderString()` simply returns "Female" if gender is set to "f", and "Male" otherwise. `getFavoriteGenreString()` looks up the field value in the `$genres` array property created at the start of the class in order to return a human-readable form of the value.

# Building the LogEntry Class

The `LogEntry` class is another data class, much like `Member`, although it's a fair bit simpler. It retrieves rows of data from the `accessLog` table.

Save the following script as `LogEntry.class.php` in the `book_club` folder:

```
<?php

require_once "DataObject.class.php";

class LogEntry extends DataObject {

	protected $data = array(
```