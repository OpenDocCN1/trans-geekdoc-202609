The `store()` method should typically be called to realize any changes to the database, but it is important to note that the DB_storage destructor will call the `store()` procedure if there are any changes to the object.

+   - Returns TRUE on success or a DB_Error object on failure.

# DB_storage::get

`mixed get( string $property )`

The `get()` method fetches the current value of a property of the object. If the named property does not exist, `get()` returns NULL.

```
```php
<?php
error_reporting( E_ALL );
require_once( 'DB.php' );
require_once( 'DB/storage.php' );

function MyValidator( $sTable, $sProperty,
    $mNewValue, $mOldValue, $oEmp )
{
    print ( "MyValidator( $sTable, $sProperty,
        $mNewValue, $mOldValue, $oEmp <br>" );

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
```