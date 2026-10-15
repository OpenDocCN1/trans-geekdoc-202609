approach: Subnodes are properties of their parent nodes/objects, and XML attributes turn into object attributes. This makes accessing XML very easy, including full iterator support, so foreach can be used.

```
<?php
$xml = simplexml_load_file('quotes.xml');
echo '<ul>';
foreach ($xml->quote as $quote) {
    $year = htmlspecialchars($quote['year']);
    $phrase = htmlspecialchars($quote->phrase);
    $author = htmlspecialchars($quote->author);
    echo "<li>$author: \"$phrase\" ($year)</li>";
}
echo '</ul>';
?>
```

*Parsing XML with SimpleXML (simplexml-read.php)*

This code loads a file using simplexml_load_file()—you can also use simplexml_load_string() for strings—and then reads all information in.

Compare this to the DOM approach. SimpleXML may be slower in some instances than DOM, but the coding is so much quicker.

NOTE
Writing can be done easily, as well. However, it is not possible to append elements without any external help, for instance by using DOM and loading this DOM into SimpleXML using simplexml_import_dom().