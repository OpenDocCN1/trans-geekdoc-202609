As can be seen from Code Listing 23 and its output in Output 10, the result of using DB_FETCHMODE_OBJECT is that each call to fetchRow() returns an object. When no object_class is specified, as above, the resulting object is simply PHP’s default cast from an array to an object.

If you plan to use the DB_FETCHMODE_OJBECT fetchmode, it is likely that you are developing an object-oriented application in which you may plan to use OO objects to represent database data generally. If so, your data objects will likely need to be more complex than the simple stdClass object.

If you wish to implement such a scenario, you can specify the object_class in the setFetchMode() method as shown in Code Listing 24 and Output 11.

```
<?php
require_once( 'DB.php' );

class Employee
{
    var $first_name;
    var $last_name;
    var $id;
    var $full_name;

    // constructor is called by DB class with a
    data row array
    function Employee( &$arr )
    {
        $this->first_name = $arr['first_name'];
        $this->last_name  = $arr['last_name'];
        $this->id         = $arr['id'];

        $this->full_name  = $this->first_name . ' ' .
        $this->last_name;
    }

$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
false );
    if ( DB::isConnection( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_OBJECT );
```