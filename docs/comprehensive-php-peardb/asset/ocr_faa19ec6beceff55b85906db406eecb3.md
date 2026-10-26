# Comprehensive PHP PEAR::DB

```
```php
// create a new DB storage object against the
// Employees table
$oEmp = new DB_storage( 'Employees', 'id', $oDB
);

// create a new Employee with ID = 50
$result = $oEmp->insert( 50 );

if ( ! DB::isError( $result ) )
{
    // set other Employee information with set()
    method
        $oEmp->set( 'first_name', 'Jim' );
        $oEmp->set( 'last_name', 'Murphy' );
        $oEmp->set( 'mgr_id', 1 );
        $oEmp->set( 'dept_id', 1 );

    // save this object to the database
    $oEmp->store();
}
else
{
    var_dump( $result );
}

$oDB->disconnect();
}
else
{
    var_dump( $oDB );
}
?>
```
```

**Code Listing 62: Using insert().**

➜ Returns a DB_Error object on failure or NULL on success.

# DB_storage::toString

*string toString( void )*

The **toString()** method returns a short string describing the DB_storage object.

```
```php
<?php
    error_reporting( E_ALL );
    require_once( 'DB.php' );
    require_once( 'DB/storage.php' );

    $oDB = DB::connect(
    'mysql://bt_user:bt_pass@207.44.182.3/book_test',
    true );
    if ( ! DB::isConnection( $oDB ) )
    {
```
```