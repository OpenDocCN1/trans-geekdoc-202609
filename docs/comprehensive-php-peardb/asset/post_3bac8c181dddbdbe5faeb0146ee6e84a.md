
This method is used to communicate an error and invoke error callbacks etc. It is basically a wrapper for PEAR::raiseError without the message string.

The **raiseError()** method is mostly used internally, but you may wish to use it in your programs. For more information about this method, investigate the PEAR::raiseError method.

The *code* parameter is an integer error code or a PEAR error object. If an object, all other parameters are ignored. The *mode* and *options* parameters are specific to the PEAR::raiseError implementation and are not discussed here. The *userinfo* and *native* parameters are used to represent the database specific error message and native error code, respectively.

- Returns a PEAR error object.

Most of the examples in this book show generally how to use the **DB_Error** object as it is returned. In most production environments, only the very basic information about failures will likely be displayed. However, for development, it is handy to have detailed information displayed in the event of an error.

In fact, the **DB_Error** object contains so much information that it's hard not to be compelled to use it in all cases. The example shown in Code Listing 20 illustrates how to use the **DB_Error** object to provide detailed information about errors. The script may be a little hard to read because it's a PHP script that generates a Javascript script on the fly, but its effect is very cool. Whenever the **errorPopup** function is called, a new popup window is displayed containing detailed error information. This is nice because it doesn’t pollute the main display window with error information. An example of the popup window is shown in Figure 4 on page 52.

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<html>
<head>
    <title>Untitled</title>
</head>
<body>
<?php
    require_once( 'DB.php' );

    function formatArg( $aArgument )
    {
        switch ( gettype( $aArgument ) )
        {
            case 'boolean' : return ( $aArgument ? 'true' : 'false' );
            case 'integer' :
            case 'double' : return $aArgument;
            case 'string' : return "'" . $aArgument . "'";
            case 'array' : return '[array]';
            case 'object' : return '[object]';
            case 'resource' : return '[resource]';
            case 'NULL' : return 'null';
        }
    }

    function formatArgs( $aArguments )
    {
        if ( count( $aArguments ) == 0 )
            return '';

        $nCount = 0;
        $result = '';
        foreach ( $aArguments as $aArgument )
        {
            if ( $nCount != 0 )
                $result .= ', ';

            $result .= formatArg( $aArgument );

            $nCount++;
        }

        return $result;
    }

    function formatBacktraceElem( $aElement )
    {
        $result = '';

        $result .= '&middot; Line ' . $aElement['line']
        . ' of ';
$result .= str_replace( '\\', '\\\\',
$aElement['file'] ) . '<ul>';

$result .= $aElement['class'] .
$aElement['type'] . ' ' . $aElement['function'];
$result .= '{ ' . formatArgs( $aElement['args']
) . ' }</ul>';

return $result;
}

function errorPopup( $dbError )
{
// just to be safe, make sure the parameter is
a DB Error
if ( DB::isError( $dbError ) )
{
$output = '<table>';
$output .= ' <tr>';
$output .= ' <td>';
$output .= ' Error Message: ';
$output .= ' </td>';
$output .= ' <td>';
$output .= ' ' . $dbError->message;
$output .= ' </td>';
$output .= ' </tr>';
$output .= ' <tr>';
$output .= ' <td>';
$output .= ' User Information: ';
$output .= ' </td>';
$output .= ' <td>';
$output .= ' ' . $dbError->userinfo;
$output .= ' </td>';
$output .= ' </tr>';
$output .= '</table>';
$output .= '<br><br>';
$output .= '<p>Stack Trace</p>';
$output .= '<table>';

if ( count( $dbError->backtrace ) > 0 )
{
foreach ( $dbError->backtrace as $aElement
)
{
$output .= ' <tr>';
$output .= ' <td>';
$output .= formatBacktraceElem( $aElement
);
$output .= ' </td>';
$output .= ' </tr>';
}
}

$output .= '</table>';

print( ' <script>' ); print( "\n" );
print( ' <!--' ); print( "\n" );
print( ' debugWin = window.open(
"about:blank", "", "width=600, height=300,
status=no, location=no, resizable=yes,
scrollbars=yes" );' ); print( "\n" );
105 print( '      debugWin.document.write( '\n<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">' );  print( "\n" );
106 print( '      debugWin.document.write( '\n<html>' );  print( "\n" );
107 print( '      debugWin.document.write( '\n<head>' );  print( "\n" );
108 print( '      debugWin.document.write( '\n<title>Debug Output</title>' );  print( "\n" );
109 print( '      debugWin.document.write( '\n<style type="text/css"><!-- ' );  print( "\n" );
110     print( '      debugWin.document.write( 'TD {' );  print( "\n" );
111     print( '      debugWin.document.write( ' font\n: normal 11px Verdana;' );  print( "\n" );
112     print( '      debugWin.document.write( '\nvertical-align : top;' );  print( "\n" );
113     print( '      debugWin.document.write( '}' );  print( "\n" );
114     print( '      debugWin.document.write( 'P {' );  print( "\n" );
115     print( '      debugWin.document.write( ' font\n: normal 11px Verdana;' );  print( "\n" );
116     print( '      debugWin.document.write( '}' );  print( "\n" );
117     print( '      debugWin.document.write( 'UL {' );  print( "\n" );
118     print( '      debugWin.document.write( ' font\n: normal 11px Verdana;' );  print( "\n" );
119     print( '      debugWin.document.write( '}' );  print( "\n" );
120     print( '      debugWin.document.write( '-->' );  print( "\n" );
121     print( '      debugWin.document.write( '\n</style>' );  print( "\n" );
122     print( '      debugWin.document.write( '\n</head>' );  print( "\n" );
123     print( '      debugWin.document.write( '\n<body>' );  print( "\n" );
124     print( '      debugWin.document.write( ' <p>' );  print( "\n" );
125     print( '      debugWin.document.write( ' </p>' );  print( "\n" );
126     print( '      debugWin.document.write( ' <p>' . str_replace( "\"", "\"", $output ) . ' </p>' );  print( "\n" );
127     print( '      debugWin.document.write( '\n</body>' );  print( "\n" );
128     print( '      debugWin.document.write( '\n</html>' );  print( "\n" );
129     print( '      //-->' ); print( "\n" );
130     print( ' </script> ' ); print( "\n" );
131 }
133 $oDB = DB::connect(
'mysql://bt_user:wrongpass@207.44.182.3/book_test',
false );
135 if ( DB::isError( $oDB ) )
136 {
137     errorPopup( $oDB );
138 }
139
140 ?>
141
142 </body>
143 </html>
```

## Code Listing 20: Using DB_Error

![](img/73cfc83029178a27381cd5f89348f7bf_61_0.png)

Figure 4: Popup window created by errorPopup function

## DB_common::setFetchMode

```
void setFetchMode( integer $fetchmode, string $object_class = null )
```

Sets which fetch mode should be used by default on queries on this connection. Valid values for the fetchmode parameter are
DB_FETCHMODE_ORDERED,
DB_FETCHMODE_ASSOC (possibly bit-wise OR'ed with DB_FETCHMODE_FLIPPED) and DB_FETCHMODE_OBJECT. If fetchmode is DB_FETCHMODE_OBJECT, then object_class specifies the class of the object to be returned by the fetch methods. If DB_FETCHMODE_OBJECT is used and object_class is null, a default cast to object from the associative array will be done.

The default fetchmode is DB_FETCHMODE_ORDERED. The example in Code Listing 21 illustrates this.

```php
<?php
require_once( 'DB.php' );
$oDB = DB::connect(
'mysql://bt_user:bt_pass@207.44.182.3/book_test',
false );
if ( DB::isConnection( $oDB ) )
{
  $sSQL = 'select id, first_name, last_name from Employees limit 3';
  $oRows = $oDB->query( $sSQL );
  if ( !DB::isError( $oRows ) )
  {
    while ( $aData = $oRows->fetchRow() )
    {
      print( '<pre>' );
      print_r( $aData );
      print( '</pre><br><br>' );
    }
  }
  $oDB->disconnect();
}
?>
```

### Code Listing 21: DB_common::setFetchMode -- DB_FETCHMODE_ORDERED (default)

The output of Code Listing 21 is shown in Output 8.

```
Array
(
    [0] => 1
    [1] => Blake
)
```
