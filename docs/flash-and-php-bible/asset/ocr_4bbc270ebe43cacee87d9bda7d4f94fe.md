The contents of that dbconn.php file are seen here.

```
<?php
$host = "localhost";
$user = "username";
$pass = "password";
$database = "database name";

$link = mysql_connect($host, $user, $pass);
mysql_select_db($database, $link);

unset($host);
unset($user);
unset($pass);
unset($Database);

?>
```

Now you can determine which action is being requested. There are two possible options: getproducts, which returns an xml document of store items, or checkout, which loads the xml from Flash and displays it.

```
if($_GET['action'] == 'getproducts')
{
    print getProducts();
}
else if($_GET['action'] == 'checkout')
{
    $xml = new SimpleXMLElement($_GET['xml']);

    $nodeCount = count($xml->product);

    print "<table border=\"1\" width=\"500\">";
    print "<tr><td><strong>Quantity</strong></td>";
    print "<td><strong>Product</strong></td>";
    print "<td><strong>Price</strong></td></tr>";

    for($x=0; $x < $nodeCount; $x++)
    {
        print "<tr style=\"background-color:#eeeee\">";
        print "<td style=\"width:60px; text-align:center;\">"
        . $xml->product[$x]->quantity . "</td>";
        print "<td>" . $xml->product[$x]->name . "</td>";
        print "<td>" . $xml->product[$x]->price . "</td></tr>";
    }

    print "<tr>";
    print "<td colspan=\"3\">Total: <strong>"
```