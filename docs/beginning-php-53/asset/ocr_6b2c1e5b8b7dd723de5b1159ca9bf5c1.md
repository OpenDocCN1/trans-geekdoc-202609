```
```php
$beetroot = $itemElements->item( 1 );

// Change the element's "type" attribute
$beetroot->setAttribute( "type", "rootVegetable" );

// Change the unit price of beetroot
if ( $child = $beetroot->firstChild ) {
    do {
        if ( $child->tagName == "unitPrice" ) {
            $child->firstChild->replaceData( 0, 10, "0.79" );
            break;
        }
    } while ( $child = $child->nextSibling );
}

// Output the XML document, encoding markup characters as needed
echo htmlspecialchars( $doc->saveXML() );

?>
</pre>
</body>
</html>
```
```

This script starts off in a similar fashion to the previous script — it displays the XHTML header and then identifies the “beetroot” item element. Once it’s done that, it uses the item element’s setAttribute() method to alter its type attribute:

```
`$beetroot->setAttribute( "type", "rootVegetable" );`
```

The next few lines of code change the beetroot element’s unitPrice text node. This code introduces a couple of new concepts along the way: the firstChild and nextSibling properties of the DOMNode class. Every node in a DOMDocument lets you access the first of its child nodes with the firstChild property (the property contains null if there are no children). Once you have the first child node, you can in turn use its nextSibling property to find the next child in the list, and so on. nextSibling contains null if there are no more siblings. (Similarly, you can use previousSibling to move backwards through the list, and lastChild to get the last child in the list.)

So the code retrieves the first child of the beetroot item element, if any, and stores it in $child:

```
`if ( $child = $beetroot->firstChild ) {`
```

It then loops through each child, using $child->nextSibling to retrieve the next child in the list. (If there are no more children, nextSibling contains null and the loop exits.)