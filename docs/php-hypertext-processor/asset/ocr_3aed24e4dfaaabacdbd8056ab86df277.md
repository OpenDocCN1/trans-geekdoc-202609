```
<html>
<head>
<title>Writing a file using PHP</title>
</head>
<body>
<?php
if ( file_exist( $filename ) )
{
   $filesize = filesize( $filename );
   $msg = "File created with name $filename ";
   $msg .= "containing $filesize bytes";
   echo ($msg );
}
else
{
   echo ( "File $filename does not exit" );
}
?>
</body>
</html>
```

It will produce the following result:

![](bbox=[0.117, 0.59, 0.882, 0.773])

We have covered all the function related to file input and out in the PHP File System Function chapter.