# Part III: Using PHP Practice

The next calls use addChild() and addAttribute() methods to add the various elements to the tree. As you can see, the code is actually compact when compared with its DOM equivalent, earlier in this chapter. This SimpleXML makes it so easy to add child elements and attributes to an element. However, you'll notice the script creates the contents of the description elements as nodes, rather than CDATA sections. This is because SimpleXML can't create CDATA sections. In fact, text elements are the only type of element that you can add with SimpleXML.

Another limitation of SimpleXML is that xml() doesn't format the resulting XML string in a nice way, so your entire XML document ends up on one line. For better formatting, you'll need to use the DOM approach.

# Converting Between SimpleXML and DOM Objects

By now you probably realize that SimpleXML is great for, simple things like reading an XML document, but the DOM is better for advanced tasks such as creating and manipulating documents. Fortunately, it's easy to convert a SimpleXElement and a DOMElement object, meaning you can work with SimpleXML if you prefer, switch to the DOM when you need to do something SimpleXML can't. The two key functions are:

| Function | Description |
| simplexml_import_dom( node ) | Converts the supplied DOM node, node, into a SimpleXMLElement object |
| dom_import_simplexml( element ) | Converts the supplied SimpleXMLElement object, element, into a DOM node |

For example, earlier you learned that SimpleXML can't create CDATA sections; however, the DOM classes can. For the stockList described earlier, you could add the "item"s description element, and associate "Apples >>>yummy<<" CDATA section, to SimpleXML document as follows:

```
// The item's "description" child element
$itemDOM = dom_import_simplexml($item);
$description = $itemDOM->ownerDocument->createElement("description");
$itemDOM->appendChild($description);
$cdata = $itemDOM->ownerDocument->createCDATASection("Apples are\n>>>yummy<<<\<");
$description->appendChild($cdata);
```

The first lines create a DOM node, from SimpleXML, from the SimpleXMLElement object (this process implicitly creates a DOMObject to hold the node). The next two lines create a $description DOM node — accessing the $itemDOM node DOMDocument object via the ownerDocument property — and add it as a child to the $itemDOM node. By adding these nodes in the DOM, the new element is automatically added to the $item SimpleXMLElement object.

612