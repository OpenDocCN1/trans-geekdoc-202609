```
<?php
$sim = simplexml_load_file("products.xml");
foreach ($sim->children() as $child) {
    print $child->title . "<br />";
}
?>
```

Listing 29.6 The Use of "children()" ("simpleXML_methods.php")

# XPath

If the standard access is not powerful enough for you, you can use the XPath implementation of SimpleXML. This is done using the xpath(expression) method, which receives an XPath expression as a parameter and returns the first location found. Use a loop to go through all the locations found.

In the following example, we use XPath to read all title tags.

```
<?php
$sim = simplexml_load_file("products.xml");
foreach ($sim->xpath("*/title") as $title) {
    print "$title<br />";
}
?>
```

Listing 29.7 XPath with SimpleXML ("simpleXML_XPath.php")

The special thing about this is that title tags that are located elsewhere in the hierarchy are also delivered. This requires considerably more effort with normal SimpleXML access than with XPath.

# Writing

Last but not least, with SimpleXML you can not only read and search a document, but also write new content into it. To do this, simply access a tag and insert the new content. You can change attributes in the same way. You can also add new attributes to an element. You can see all three possible changes in the following script. Finally, return the modified XML as a string using the asXML() method. Figure 29.6 shows the modified file.

```
<?php
if ($sim = simplexml_load_file("products.xml")) {
    $sim->product[1]->title = "Coffee pot AB";
    $sim->product[1]->title["changed"] = date("d.m.Y");
    $sim->product[1]->price["currency"] = "Euro";
    print "<pre>" . htmlentities($sim->asXML()) . "</pre>";
}
?>
```

Listing 29.8 Modify XML with SimpleXML ("simpleXML_edit.php")