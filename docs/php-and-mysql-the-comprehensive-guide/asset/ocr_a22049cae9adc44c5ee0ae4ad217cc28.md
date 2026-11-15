To access several or all tags, you can make do with loops. The following example goes through all products and outputs the title, price, and currency in an HTML table (see Figure 29.5).

```
<?php
$sim = simplexml_load_file("products.xml");
print '<table border="1" cellpadding="5" align="center">';
foreach ($sim->product as $product) {
print '<tr><td>';
print $product->title;
print '</td><td>';
print $product->price . ' ' . $product->price["currency"];
print '</td></tr>';
}
print '</table>';
?>
```

# Listing 29.5 SimpleXML in Use ("simpleXML.php")

![](bbox=[0.143, 0.413, 0.753, 0.573])

# Figure 29.5 An HTML Table from the XML File

> Tip
> The last example matches the result of the XSLT shown later in Listing 29.15. This raises the question of what you should use in practice. If it has to be done very quickly, SimpleXML is definitely easier. XSLT has the advantage that you have to rewrite not the entire conversion script when switching to another programming language, but only a few lines of code. However, with XSLT it is difficult to separate the content—usually the HTML template—from the conversion logic. With SimpleXML, on the other hand, you can work with any PHP template system, such as Smarty.

# Other Methods

The children() and attributes() methods do a little more work for you. They allow you to access the child nodes or attributes of an element directly. The first object is returned on the first call. You can then loop through all child nodes or attributes.