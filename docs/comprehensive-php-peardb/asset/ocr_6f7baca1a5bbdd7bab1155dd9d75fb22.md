doesn’t pollute the main display window with error information. An example of the popup window is shown in Figure 4 on page 52.

```
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
```
```