
For a usage example, see Code Listing 60 on page 123.

- Returns no value but creates output on standard output.

## DB_storage::create

```
object create( string $table, array $data )
```

The internal documentation for the **create()** method indicates that **create()** is a static method used to create new DB_storage objects.

However, from my interpretation of the code inside the **create()** method, it does not appear that this method can be used statically (there is a reference to *$this*). Additionally, it appears that even if an object *could* be created it would not be sufficiently initialized to be useful.

> > I will accept comments regarding this method’s use via the forums or personal messages at **http://www.intechra.net/**. Otherwise, I suggest avoiding this method entirely.

## DB_storage::set

```
mixed set( string $property, mixed $newvalue )
```

The **set()** method is the primary mechanism for updating properties of the DB_storage object which, in turn, updates the columns of the database row represented by the object.

The `store()` method should typically be called to realize any changes to the database, but it is important to note that the DB_storage destructor will call the `store()` procedure if there are any changes to the object.

- Returns TRUE on success or a DB_Error object on failure.

## DB_storage::get

`mixed get( string $property )`

The `get()` method fetches the current value of a property of the object. If the named property does not exist, `get()` returns NULL.

```php
<?php
error_reporting( E_ALL );
require_once( 'DB.php' );
require_once( 'DB/storage.php' );

function MyValidator( $sTable, $sProperty,
    $mNewValue, $mOldValue, $oEmp )
{
    print ( "MyValidator( $sTable, $sProperty,
        $mNewValue, $mOldValue, $oEmp ) <br>" );

    if ( ( $sTable == "Employees" ) && ( $sProperty
        == 'phone_ext' ) )
    {
        // valid phone extensions range from 200 to
        // 4999
        if ( ( $mNewValue >= 5000 ) || ( $mNewValue <
            200 ) )
        {
            return false;
        }
    }
    return true;
}

$oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
if ( DB::isConnection( $oDB ) )
{
    // create a new DB_storage object against the
    // Employees table
    $oEmp = new DB_storage( 'Employees', 'id',
        $oDB, 'MyValidator' );
}
```

```php
// load the employee with ID = 1
$oEmp->setup( 1 );
$oEmp->dump();

// get a property
$iMgrId = $oEmp->get( 'mgr_id' );

if ( $iMgrId == 3 )
{
    // set some properties
    $oEmp->set( 'first_name', 'Joe' );
    $oEmp->set( 'phone_ext', '9987' );

    $oEmp->store();
}
$oEmp->dump();

$oDB->disconnect();
}
else
{
    var_dump( $oDB );
}
?>
```

Code Listing 64: Using set() and get().

The example in Code Listing 64 illustrates the use of both set() and get(). These methods are simple enough to understand.

Code Listing 64 also illustrates using a custom validation callback function to validate data provided through the set() method. The last argument to the DB_storage constructor (line 26) specifies the callback function for data validation. In this case, it is simply a function called MyValidator. It could be a method of a class, in which case it would be specified as an array containing the class name and method name as elements as with any callback function in PHP.

In the example, the validation function prints a line showing its arguments. It also validates any proposed changes to the phone_ext property to ensure that the new value falls within an acceptable range.

The remove() method actually removes the row of data represented by the DB_storage object from the database.

```php
<?php
error_reporting( E_ALL );
require_once( 'DB.php' );
require_once( 'DB/storage.php' );

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
if ( DB::isConnection( $oDB ) )
{
    // create a new DB_storage object against the Employees table
    $aEmp = new DB_storage( 'Employees', 'id', $oDB
);

$aEmp->setup( 50 );
$aEmp->remove();

$oDB->disconnect();
}
else
{
    var_dump( $oDB );
}
?>
```

Code Listing 65: Using remove().

The example in Code Listing 65 shows how to use remove() to delete a row in the database.

- Returns DB_OK or a DB_Error object.

## Database Support

PEAR::DB provides support for the databases listed in Table 1 on page 19. This section of the book is provided to show how a single script can be used to access several database back ends while only changing the DSN in the script.

Several factors are assumed in the example script. First, it is assumed that the database is running and PHP is configured with the appropriate code/drivers to access the database. Second, it is assumed that the user specified in the DSN has appropriate database privileges to perform the tasks in the script. Third, it is assumed that a database called *book_test* exists on the target database server. This section of the book is intended to primarily provide very high-level information about each of the supported databases and not to be a primer on installing and configuring each database. As appropriate, I may mention some interesting configuration or setup information identified in my testing. For the most part, this book was developed running PHP on Windows, so little of the database-specific information will be based on Linux (or other unix-like) operating systems.

The test program is divided into three files. The first file is the main script shown in Code Listing 66. The second file is the included file, *err_popup.php* which is just the functions from the example shown in Code Listing 20 on page 52. These functions popup a separate browser window and display the DB_Error object information. The third file (*db_specific.php*) is a set of database specific strings shown in Code Listing 67.

It should be obvious to any reader that not all SQL servers provide the same features or even the same syntax for SQL statements. The *db_specific.php* file contains those SQL statements that create the *Employees* table since table creation is typically very different between database servers. Other information stored in the *db_specific.php* file includes the DSN information and the full name of the database server for display.

The discussion of various parts of Code Listing 66 is given immediately below the listing itself.

```php
<?php
$aInsertQueries[] = "INSERT INTO Employees VALUES
(1, 'Schwendiman', 'Joe', '2204', 3, 1)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(2, 'Cox', 'Jeffrey', '225', 0, 1)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(3, 'McNulty', 'Kate', '214', 3, 2)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(4, 'Schwendiman', 'Ryan', '128', 1, 1)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(51, 'Murphy', 'Jim', '', 1, 1)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(58, 'Schwendiman', 'Scott', '234', 1, 1)";
$aInsertQueries[] = "INSERT INTO Employees VALUES
(59, 'Schwendiman', 'Taylor', '323', 1, 1)";

$aSelectQueries[] = "SELECT * from Employees
order by last_name, first_name";
$aSelectQueries[] = "SELECT * from Employees
where ( mgr_id = 3 )";
$aSelectQueries[] = "SELECT * from Employees
where ( dept_id = 2 )";

$aUpdateQueries[] = "UPDATE Employees set mgr_id
= 2 where ( mgr_id = 3 )";
$aUpdateQueries[] = "UPDATE Employees set dept_id
= 3 where ( mgr_id = 2 )";

$aDeleteQueries[] = "DELETE FROM Employees where
( phone_ext < 300 )";
?>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0
Transitional//EN">

<html>
<head>
    <title>PEAR::DB General Test</title>
</head>

<body>

<?php
error_reporting( E_ALL );
require_once( 'DB.php' );
require_once( 'err_popup.php' );
require_once( 'db_specific.php' );

$sDBType = 'mssql';

function DisplayHeader( $aRow )
{
    print( '<tr>' );
    print( '<td>&nbsp;</td>' );
    foreach ( $aRow as $aName => $aValue )
    {
```
