```
function getProducts()
{
    global $link;

    $result = mysql_query("SELECT * FROM flashStore_products 
    WHERE active=1", $link);

    $xml = "<products>\n";
    while($row = mysql_fetch_array($result))
    {
        $xml .= "<product id=\"" . $row['id'] . "\"
        \" name=\"" . $row['name'] . "\"
        \" desc=\"" . $row['description'] . "\"
        \" thumbnail=\"" . $row['thumbnail'] . "\" />\n";
        \" price=\"" . $row['price'] . "\" />\n";
    }
    $xml .= "</products>";

    return $xml;
}
```

The last function is actually a forgotten feature of SimpleXML. This function takes two arguments, the xml and the attribute name you are looking for. It first loops through all of the arguments and matches those arguments against the passed-in variable. It returns either the value of the attribute or false, depending on what the result is.

```
function getAttribute($xml, $name)
{
    foreach($xml->attributes() as $key=>$val)
    {
        if($key == $name)
        {
            return (string)$val;
        }
    }
    return false;
}
```

Now that all of the code is complete, here are the three classes and Timeline code provided in one place for easier viewing and comparison with your code.

# ## ShoppingCart

```
package
{
    import flash.display.MovieClip;
    import flash.text.TextField;
    import flash.events.MouseEvent;
}
```