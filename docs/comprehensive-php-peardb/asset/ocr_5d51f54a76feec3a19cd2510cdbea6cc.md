As a developer, I personally recommend using sequences rather than automatically incrementing field types. Depending on the underlying database, some problems can arise with automatically incrementing fields.

# Prepare and Execute

The prepare and execute method of database querying is also generalized for all databases by using PEAR::DB. By using the prepare(), execute(), and executeMultiple() methods, more flexibility is afforded general query execution. Details of these methods will be given below, but as a high-level overview, a simple example is shown below in Code Listing 11.

```
```php
<?php
require_once( 'DB.php' );

// make a non-persistent connection to a MySQL
database
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
array( 'seqname_format' => 'seq_%s' ) );
if ( !DB::isError( $oDB ) )
{
$aInsertSQL = 'INSERT INTO Employees ( id ,
last_name , first_name , phone_ext , mgr_id ,
dept_id ) VALUES ( ?, ?, ?, ?, ?, ? )';
$hQuery = $oDB->prepare( $aInsertSQL );

$aData = array( $oDB->nextId( 'employees' ),
'Schwendiman', 'Ryan', '123', '1', '1' );
$result = $oDB->execute( $hQuery, $aData );
if ( DB::isError( $result ) )
print( $result->getMessage() );

$aData = array( $oDB->nextId( 'employees' ),
'Schwendiman', 'Scott', '234', '1', '1' );
$result = $oDB->execute( $hQuery, $aData );
if ( DB::isError( $result ) )
print( $result->getMessage() );

$aData = array( $oDB->nextId( 'employees' ),
'Schwendiman', 'Taylor', '323', '1', '1' );
```
```