SimpleXMLElement object that contains each of its child element values as properties, as well as the element’s attributes as an associative array. It’s this feature that makes SimpleXML a very easy way to read and extract data from XML files. For example, if you wanted to display the unit price of beetroots, you would simply write:

```
echo $StockList->item[1]->unitPrice;
```

You can also use the powerful xpath() method to search for elements within an XML document. This is great for finding a particular element within a large XML file, especially if you don’t know the position of the element beforehand. For example, the following code retrieves the unit price of beetroots, without needing to know that the “beetroot” item is the second child of stockList:

```
$UnitPriceElement =
$StockList->xpath( "child::item[name='beetroot']/child::unitPrice" );
echo $UnitPriceElement[0];
```

The string passed to xpath() is known as an XPath string. Translated into English, this string says, “Get me the child element called item that itself contains a name child element with the value beetroot, then retrieve the other child of the item element called unitPrice.” This returns a SimpleXMLElement object that represents the unitPrice element inside the “beetroot” item element, which is stored in $UnitPriceElement. It’s then simply a case of displaying the first array value in $UnitPriceElement, which is the text node containing the value you want (1.39).

XPath is a very powerful way of representing any node in any XML document as a string, but it takes some getting used to. You can read the full specification at http://www.w3.org/TR/xpath.

# Creating an XML Document

Though SimpleXML is great for reading XML documents, the DOM approach is your best bet if you need to create or modify XML documents. This is because the DOM classes let you tweak every aspect of an XML document; with SimpleXML you’re more limited in what you can do.

Nevertheless, it’s perfectly possible to create an XML document with SimpleXML, as this next example shows. This script creates the XML for the stock_list.xml file used in earlier examples, and displays the resulting XML in the browser window:

```
<!DOCTYPE html PUBLIC "--//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Creating an XML File with the SimpleXML Extension</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Creating an XML File with the SimpleXML Extension</h1>
<pre>
<?php
// Create the root "stockList" element
$StockList = new SimpleXMLElement( "<stockList/>" );
```