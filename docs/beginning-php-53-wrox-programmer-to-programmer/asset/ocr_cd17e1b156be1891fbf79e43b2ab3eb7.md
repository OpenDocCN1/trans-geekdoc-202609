```
// Create the second "item" element (beetroot)
$item = $doc->createElement( "item" );
$item->setAttribute( "type", "vegetable" );
$stocklist->appendChild($item);

// Create the item's "name" child element
$name = $doc->createElement( "name", "beetroot" );
$item->appendChild($name);

// Create the item's "unitPrice" child element
$unitPrice = $doc->createElement( "unitPrice", "1.39" );
$item->appendChild($unitPrice);

// Create the item's "quantity" child element
$quantity = $doc->createElement( "quantity", "67" );
$item->appendChild($quantity);

// Create the item's "description" child element
$description = $doc->createElement( "description" );
$item->appendChild($description);
$cdata = $doc->createCDATA( "Beetroots are lovely & purple" );
$description->appendChild($cdata);
```

Finally, the script calls the document object's saveXML(); this method returns the document as an XML string. After passing the string through htmlspecialchars to encode the markup characters as "&lt;","&gt;", and "&amp;", the results are displayed on the page:
echo htmlspecialchars($doc->saveXML());

You'll notice that the final XML document doesn't include the DOCTYPE line. Although it is possible to add a DOCTYPE to an XML document using the DOM, it's outside the scope of this book. See the “DOM” section of the online PHP manual at http://php.net/manual/en/book.dom.php for details. The alternative, of course, is simply to insert the DOCTYPE line into the final XML document string.

# Manipulating XML Documents using the DOM

One of the great features of the DOM classes is that they make it easy to get right in and play with individual pieces, or nodes, of an XML document. For example, you can add new elements to an element, remove existing elements, change node or attribute values, move an element from one part of the tree to another, and so. The following sections explore some of these techniques.