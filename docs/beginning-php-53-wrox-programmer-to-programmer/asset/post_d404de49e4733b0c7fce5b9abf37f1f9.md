
# Creating an XML Document using the DOM

Now you know how to read an XML document with the DOM extension, and you've explored some common DOM classes, properties and methods along the way. You're now ready to creating an XML document from scratch using the DOM.

You already know how to create a bare-bones DOM document with new DOMDocument(). Once you've created your document, it's simply a case of creating nodes, adding each node to the document to build up the DOM tree.

To create a node, you call various methods of the DOM class. Common methods include:

| Method | Description |
| --- | --- |
| createElement( name [, value ] ) | Creates an element called name and optionally appends a text to it containing value |
| createcreateTextNode( content ) | Creates a text node that contains content |
| createCDATASection( data ) | Creates a character node that contains data |
| createComment( data ) | Creates a comment node that contains data |

Once you've created a node, you add it as a child of the existing node's appendChild() method:

```
$parentNode->appendChild($childNode);
```

In this way you can build a DOM tree containing the root element node, its children, its grandchildren, and so on.

You can also add elements to nodes. The easy way is to use the setAttribute() method of the DOMElement object:

```
$element->setAttribute("name", "value");
```

The more long winding way is to create a DOMAttr attribute node using the createAttribute() method of DOMDocument, set the attribute's value property, and then add the attribute to the element using the element's appendChild method:

```
$attribute = $doc->createAttribute("name");
$attribute->value = "value";
$element->appendChild($attribute);
```

Although the second approach is more tedious, it shows how you virtually everything in a DOM document is ultimately a node — even attributes are nodes.

# Part III: Using PHP Practice

# Try It Out Create an XML document using the DOM

Now you get to put this theory into practice. You're going to create a nearly identical version of the stock_list.xml file, entirely from scratch, using the DOM classes and methods.

Here's the script to do that:

```
<!DOCTYPE type PUBLIC "//W3C//DTD XHTML 1.0 Strict//EN"
   "http://www.w3.org/TR/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>Creating an XML file with the DOM Extension</title>
  <link rel="stylesheet" type="text/css" href="/common.css" />
</head>
<body>
  <h1>Creating an XML file with the DOM Extension</h1>
  <pre>
<?php
// Create a DOMDocument object and set nice formatting
$doc = new DOMDocument("1.0", "UTF-8");
$doc->formatOutput(true);

// Create the root "stockList" element
$stockList = $doc->createElement("stockList");
$doc->appendChild($stockList);

// Create the first "item" element (apple)
$item = $doc->createElement("item");
$item->setAttribute("type", "fruit");
$stockList->appendChild($item);

// Create the item "name" child element
$name = $doc->createElement("name", "apple");
$item->appendChild($name);

// Create the item "price" child element
$unitPrice = $doc->createElement("unitPrice", "0.99");
$item->appendChild($unitPrice);

// Create the item "quantity" child element
$quantity = $doc->createElement("quantity", "412");
$item->appendChild($quantity);

// Create the item "description" child element
$description = $doc->createElement("description");
$item->appendChild($description);
$cdata = $doc->createCDATASection("Apples are >>>yummy<<<");
$description->appendChild($cdata);

// Create the second "item" element (beetroot)
$item = $doc->createElement("item");
$item->setAttribute("type", "vegetable");
$stockList->appendChild($item);
</pre>
```

*

# Chapter 19: Working with XML

```php
// Create the item's "name" child element
$name = $doc->createElement("name", "beetroot");
$item->appendChild($name);

// Create the item's "unitPrice" child element
$unitPrice = $doc->createElement("unitPrice", "1.39");
$item->appendChild($unitPrice);

// Create the item's "quantity" child element
$quantity = $doc->createElement("quantity", "67");
$item->appendChild($quantity);

// Create the item's "description" child element
$description = $doc->createElement("description", "");
$item->appendChild($description);
$cdata = $doc->createCDATASection("Beetroots are lovely & purple");
$description->appendChild($cdata);

// Output the XML document, encoding markup characters as needed
echo htmlspecialchars($doc->saveXML());
```

```html
<pre>
</body>
</html>
```

Save this script as dom_create_document.php in your document root folder, and run it. You should see something like Figure 19-3.

![](img/ede05b7b77968b82cbd9a513122fb183_634_0.png)

# Creating an XML File with the DOM Extension

```xml
<xml version="1.0" encoding="UTF-8"?>
<stock>
  <item type="fruit">
    <name>apple</name>
    <unitPrice>0.39</unitPrice>
    <quantity>5</quantity>
    <description><![CDATA[Apples are >>>yummy]]></]]></description>
  </item>
  <item type="vegetable">
    <name>beetroot</name>
    <unitPrice>1.39</unitPrice>
    <quantity>6</quantity>
    <description><![CDATA[Beetroots are lovely & purple]]></description>
  </item>
</stock>
```

Figure 19-3

# Part III: Using PHP Practice

How It Works
If you've followed thus far, this script creates a new DOMDocument object, passing in optional arguments for the XML version (1.0) and the character encoding to use the XML (UTF-8). Next it sets the object's formatOutput property to true; this makes the XML is nicely formatted when it's outputted, rather than being all on one line:

```php
$doc = new DOMDocument("1.0", "UTF-8");
$doc->formatOutput = true;
```

Next, the script creates a new DOMElement to represent the root stockList, and adds this node as a child to the document:

```php
$stockList = $doc->createElement("stockList");
$doc->appendChild($stockList);
```

Now it's time to create the first item element, give it a type attribute with the value "fruit", and add the element to the stockList:

```php
$item = $doc->createElement("item");
$item->setAttribute("type", "fruit");
$stockList->appendChild($item);
```

The next few lines of code create all the children of the item element. Each element object is created and appended to it. The createElement() method allows you to pass in an optional second argument, which is used to create a DOMText object with the value of the argument and automatically append it to the newly created element. This saves you from manually create the DOMText object with createTextNode() each time:

```php
// Create the item's "name" child element
$name = $doc->createElement("name", "apple");
$item->appendChild($name);
```

```php
// Create the item's "unitPrice" child element
$unitPrice = $doc->createElement("unitPrice", "0.99");
$item->appendChild($unitPrice);
```

```php
// Create the item's "quantity" child element
$quantity = $doc->createElement("quantity", "412");
$item->appendChild($quantity);
```

However, to create the CDATA node for the description element, you have to do it the long way:

```php
// Create the item's "description" child element
$description = $doc->createElement("description");
$item->appendChild($description);
$cdata = $doc->createCDATASection("Apples are >>>yummy<<<");
$description->appendChild($cdata);
```

Next, the second item element is created in a similar fashion:

```php
// Create the second "item" element (beetroot)
$item = $doc->createElement("item");
$item->setAttribute("type", "vegetable");
$stockList->appendChild($item);

// Create the item's "name" child element
$name = $doc->createElement("name", "beetroot");
$item->appendChild($name);

// Create the item's "unitPrice" child element
$unitPrice = $doc->createElement("unitPrice", "1.39");
$item->appendChild($unitPrice);

// Create the item's "quantity" child element
$quantity = $doc->createElement("quantity", "67");
$item->appendChild($quantity);

// Create the item's "description" child element
$description = $doc->createElement("description");
$item->appendChild($description);
$cdata = $doc->createCDATASection("Beetroots are lovely & purple");
$description->appendChild($cdata);
```

# Manipulating XML Documents using the DOM

One of the great features of the DOM classes is that they make it easy to get right in and play with individual pieces, or nodes, of an XML document. For example, you can add new elements to an element, remove existing elements, change node or attribute values, move an element from one part of the tree to another, and so. The following sections explore some of these techniques.
