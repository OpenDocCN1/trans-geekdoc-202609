# Part III: Using PHP in Practice

```
$php = $itemElements->item( 0 );
$beetroot = $itemElements->item( 1 );

// Move "beetroot" to the start of the list of items
$stockList->insertBefore($beetroot, $apple);

// Output the XML document, encoding markup characters as needed
echo htmlspecialchars($doc->saveXML());

?>
<pre>
<body>
</html>
```

The script stores the "apple" and "beetroot" item in two variables, $apple and $beetroot. It calls $stocklist->insertBefore() to insert $beetroot before $apple in the list. (By inserting a DOM node that is already somewhere in the document, the node is automatically moved from the location to the new.)

Other methods that you can use to move nodes include appendChild() and removeChild() earlier in the chapter — as well as replaceChild() (for replacing one node with another).

# Doing XML the Easy Way with SimpleXML

Although the DOM extension is a powerful way to work with XML documents, its huge number of classes, methods, and properties can be somewhat overwhelming. Furthermore, doing simple tasks, such as creating child elements and locating nodes within a document, can be tedious and time-consuming to use.

This is where SimpleXML steps in. This extension offers a more straightforward way to manipulate elements within an XML document. In many ways you can think of it as "DOM Lite." Whereas the DOM extension provides more than 15 classes and more than 100 methods and attributes, SimpleXML gives you just one class: SimpleMLElement. In addition, whereas the DOM extension lets you get right down to the node level, SimpleXML works at the somewhat element level, making element manipulation a much more straightforward process.

Here’s a list of common SimpleMLElement methods that you can use to manipulate XML documents: