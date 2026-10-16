One of the greatest new features in PHP 5.1 is the SimpleXML extension, an idea borrowed from a Perl module in CPAN. The approach is as simple as it is ingenious. The most intuitive way to access XML is probably via an object-oriented programming (OOP) approach: Subnodes are properties of their parent nodes/objects, and XML attributes turn into object attributes. This makes accessing XML very easy, including full iterator support, so foreach can be used.

This code loads a file using simplexml_load_file()—you can also use simplexml_load_string() for strings—and then reads all information in.

Compare this to the DOM approach. SimpleXML may be slower in some instances than DOM, but the coding is so much quicker.

> NOTE: Writing can be done easily, as well. However, it is not possible to append elements without any external help (for instance, by using DOM and loading this DOM into SimpleXML using simplexml_import_dom()).

# Using XPath with SimpleXML

# $xml->xpath()

```
<?php
$xml = simplexml_load_file('quotes.xml');
foreach ($xml->xpath('*/quote') as $quote) {
    echo '<p>' . htmlspecialchars($quote) . '</p>';
}
?>
```

Using XPath with SimpleXML (xpath.php)