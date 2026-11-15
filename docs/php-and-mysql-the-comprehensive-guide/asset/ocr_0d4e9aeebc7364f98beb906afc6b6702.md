```
print $title->textContent . "<br />";
}
}
?>
```

# Listing 29.12 XPath with DOM (dom_XPath.php)

# DOM and SimpleXML

We talked about the conversion between DOM and SimpleXML in Section 29.2.2.

# Classes

The API of the DOM extension is completely object-oriented. The document itself is a DOMDocument object. There is also DomNode for a node, DomElement with all methods and properties for a tag, and a few more. What is new is that you can add functionality to the underlying classes. The easiest way to do this is to write your own classes that inherit from DOMDocument and the like. This can then be a common task, for example, which you pack into a method.

# 29.2.4 Validation

Validation is about checking whether the structure of an XML document is correct. If you have full control over the appearance of your XML, you do not necessarily need to validate it. The situation is different if you have specified a certain structure but do not know whether this is always adhered to. In this case, a DTD or a schema is necessary.

The following listing shows a document with (internal) DTD.

```
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<!DOCTYPE products [
  <!ELEMENT products (product+)>
  <!ELEMENT product (title+, price+)>
  <!ELEMENT title (#PCDATA)>
  <!ELEMENT price (#PCDATA)>
  <!ATTLIST price currency CDATA #REQUIRED>
]>
<products>
<product>
  <title>Vacuum cleaner XY</title>
  <price currency="Euro">4.80</price>
</product>
<product>
  <title>Teapot AB</title>
```