```
```php
<?php
$xml = new XMLReader();
$xml->open("products.xml");

while ($xml->read()) {
    if ($xml->nodeType == XMLReader::ELEMENT) {
        if ($xml->localName == "title") {
            $xml->read();
            echo htmlspecialchars($xml->value) .
                "<br />";
        }
    }
}
?>
```
```

Listing 29.15 XSLT ("xslt.php")

![](bbox=[0.14, 0.395, 0.82, 0.56])

Figure 29.10 The Products as an HTML Table

# ## 29.3 XMLReader and XMLWriter

XMLReader and XMLWriter are new XML access variants that are modeled on the XmlReader and XmlWriter from the Microsoft .NET Framework. They are similar to access via SAX but are even easier to use.

> > **Note**
> >
> > XMLReader and XMLWriter have been integrated directly into the PHP core since PHP 5.1.

# ### 29.3.1 XMLReader

In contrast to the event-based SAX parser, XMLReader has a cursor-oriented parser, familiar from reading files. This means that the XML elements are run through individually. More detailed information on the respective element can then be obtained via