# PEAR::DB

The example above, recoded for PEAR::DB is shown in Code Listing 4.

```
```php
<?php
    require_once( 'DB.php' );

    $oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
true );
    if ( !DB::isError( $oDB ) )
    {
        $oDB->setFetchMode( DB_FETCHMODE_ASSOC );

        $query = "SELECT Employees.last_name as
emp_last_name, Employees.first_name as
emp_first_name, Employees.phone_ext as
emp_phone_ext, Departments.name as dept_name,
Employees_1.last_name as mgr_last_name,
Employees_1.first_name as mgr_first_name,
Employees_1.phone_ext as mgr_phone_ext FROM
(Departments INNER JOIN Employees ON Departments.id
= Employees.dept_id) LEFT JOIN Employees AS
Employees_1 ON Employees.mgr_id = Employees_1.id";

        $oRows = $oDB->query( $query );
        if ( !DB::isError( $oRows ) )
        {
            print( '<table>' );
            while ( $oRow = $oRows->fetchRow() )
            {
                print '<tr>';
                foreach ( $oRow as $col_value ) {
                    print "<td>$col_value</td>";
                }
                print '</tr>';
            }
            print( '</table>' );
        }
        else
        {
            print( 'Query failed: ' );
            print( $oDB->getMessage() );
            print( '<br>' );
        }
    }
    else
    {
        print( 'Unable to connect to database server: '
);
        print( $oDB->getMessage() );
        print( '<br>' );
    }
}
?>
```
```

Code Listing 4: PEAR::DB Database Access