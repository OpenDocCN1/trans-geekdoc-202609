# Part III: Using PHP in Practice

```
$beetroot = $itemElements->item( 1 );

// Change the element's "type" attribute
$beetroot->setAttribute("type", "rootVegetable");

// Change the unit price of beetroot
if ($child = $beetroot->firstChild ()) {
    do {
        if ($child->tagName == "unitPrice") {
            $child->firstChild->replaceData(0, 10, "0.79");
            break;
        }
    } while ($child = $child->nextSibling);
}

// Output the XML document, encoding markup characters as needed
echo htmlspecialchars($doc->saveXML());

?>
<pre>
</body>
</html>
```

This script starts off in a similar fashion to the previous script — it displays the XHTML header and identifies the "beetroot" element. Once it is done that, it uses the item element's setAttribute method to alter its type attribute:

```
$beetroot->setAttribute("type", "rootVegetable");
```

The few lines of code change the beetroot unitPrice text node. This introduces a couple of new concepts along the way: the firstChild and nextSibling properties of the DOMNode class. Every node in a DOMDocument lets you access to its child nodes with the firstChild property (the property contains null if there are no children). Once you have the first child node, you can use in turn its nextSibling property to find the next child in the list, and so on. nextSibling contains null if there are no more siblings. (Similarly, you can use previousSibling to move backwards through the list, and lastChild to get the last child in the list.)

The code retrieves the change of the beetroot item element, if any, and stores it in $child:

```
if ($child = $beetroot->firstChild ) {
```

It loops through each child, $child->nextSibling to retrieve the next child in the list. (If there are no more children, nextSibling contains null and the loop exits.)

604