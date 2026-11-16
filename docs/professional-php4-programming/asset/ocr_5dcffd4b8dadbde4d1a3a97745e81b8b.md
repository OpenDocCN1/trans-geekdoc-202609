```
<body>
<h1>Travel Packages</h1>
<table>
<?php
$doc = xmldoc(implode("", file("travel.xml")));
$context = xpath_new_context($doc);
```

Then we retrieve a root object:

```
$root = $doc->root();
```

We'll create a $expr variable to store the XPath statement. It's easier to change here than in the xpath_eval() statement. The XPath statement /* will find all child nodes under the root node:

```
$expr = "/*";
```

The xpath_eval() function is used to run the XPath statement against the context of the document. The xpath_eval() statement returns either true if the XPath syntax is valid and finds a result, or false if the syntax is not valid or doesn't return a result. So we can wrap xpath_eval() in a conditional if statement. If there are nodes that match the XPath statement, they are returned and stored in $tmpArray. The key of $tmpArray corresponds to the name of the node and the value of the array corresponds to the content of the node. Then we can loop through the array and print out the XML as HTML:

```
if ($path = xpath_eval($context, $expr)) {
    $tmpArray = $path->nodeset;
    while (list() = each($tmpArray)) {
        $i++;
        echo("<tr><td>");
        echo($tmpArray[$i]->name);
        echo("</td><td>");
        echo($tmpArray[$i]->content);
        echo("</td></tr>\n");
    }
} else {
    echo("expression: $expr, is invalid\n");
}
?
</table>
</body>
</html>
```

This code does output the contents of the XML file to the browser, but it's not in the format that we want. Notice how each Travelpackage element is followed by the values of the attributes of its elements, as is the case with Package. What this indicates is that the nesting of the elements isn't maintained when the tree is either built or parsed: