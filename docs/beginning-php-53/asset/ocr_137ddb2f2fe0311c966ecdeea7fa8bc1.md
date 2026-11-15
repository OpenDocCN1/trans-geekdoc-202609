```
$cdata = $doc->createCDATASection( "Carrots are crunchy" );
$description->appendChild( $cdata );

// Output the XML document, encoding markup characters as needed
echo htmlspecialchars( $doc->saveXML() );
?>
</pre>
</body>
</html>
```

This results in an XML document like this:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE stockList SYSTEM "http://www.example.com/dtds/stockList.dtd">
<stockList>
  <item type="fruit">
    <name>apple</name>
    <unitPrice>0.99</unitPrice>
    <quantity>412</quantity>
    <description><![CDATA[Apples are >>>yummy<<<]]></description>
  </item>
  <item type="vegetable">
    <name>beetroot</name>
    <unitPrice>1.39</unitPrice>
    <quantity>67</quantity>
    <description><![CDATA[Beetroots are lovely & purple]]></description>
  </item>
  <item type="vegetable">
    <name>carrot</name>
    <unitPrice>0.79</unitPrice>
    <quantity>31</quantity>
    <description><![CDATA[Carrots are crunchy]]></description>
  </item>
</stockList>
```

There are a few new properties and methods of note here. The line

```
$doc->preserveWhiteSpace = false;
```

ensures that the output is nicely formatted when using the saveXML() method. If the preserveWhiteSpace property is true (which is the default), any new nodes added to the existing document get written out as a single line of XML, rather than being nicely formatted.

The following lines retrieve the root stockList element from the document tree:

```
// Get the stockList root element
$stockListElements = $doc->getElementsByTagName( "stockList" );
$stockList = $stockListElements->item( 0 );
```