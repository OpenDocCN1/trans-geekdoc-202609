
# Part III: Using PHP Practice

By using XML documents, applications that know nothing about each other can still communicate effectively — they just have to exchange XML documents, and understand the meaning of the DTD or XSD against which those documents are validated. This is one of the main features that make XML so powerful.

# Major Parts of an XML Document

Broadly speaking, a well-formed XML document may contain the following:

- An XML declaration at the top of the document, possibly including a character encoding declaration. This declaration is a good idea, but it's not mandatory. If no XML declaration is given, version 1.0 is assumed. If no character encoding is specified, UTF-8 is assumed.
  example:
  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  ```

- An optional DTD or XSD, or a reference to one if they are stored externally. This must appear before the root element. For example, here's a reference to an external DTD:
  ```xml
  <!DOCTYPE stockList SYSTEM "http://www.example.com/dtds/stockList.dtd">
  ```

- XML documents must contain one — and only one — root element. This element usually contains one or more elements, each of which may optionally have one or more attributes. An element can contain child elements or data between its beginning and ending tag, or it may be empty.

XML documents may contain additional components such as processing instructions (PIs) that provide machine instructions for particular applications; CDATA sections, which may contain special characters that are not allowed in ordinary XML data; notations; comments; entity references (aliases for entities as special characters); text; and entities. You will look at some of these components later in the chapter.

Here's an enhanced version of the stockList example document used earlier that illustrates these major parts. First, the XML declaration:

```xml
<?xml version="1.0" encoding="UTF-8"?>
```

Next is the reference to a DTD that defines the allowed elements and attributes in the document:

```xml
<!DOCTYPE stockList SYSTEM "http://www.example.com/dtds/stockList.dtd">
```

Now the root element begins. Remember that there can be only one root element in an XML document:

```xml
<stockList>
```

# Chapter 19: Working with XML

The root element contains two item elements. Each element itself contains four children. The description elements contain CDATA sections to enclose their text data, because the data contains characters as >, < and & would otherwise be treated as markup:

```xml
<item type="fruit">
  <name>apple</name>
  <unitPrice>0.99</unitPrice>
  <quantity>412</quantity>
  <description><![CDATA[Apples are >>> yummy<<<]]></description>
</item>
<item type="vegetable">
  <name>beetroot</name>
  <unitPrice>1.39</unitPrice>
  <quantity>67</quantity>
  <description><![CDATA[Beetroots are lovely & purple]]></description>
</item>
```

Finally, the root element is closed:

```xml
</stockList>
```

# XML Syntax Rules

You now know what major components of an XML document are. In addition, a well-formed XML document must follow all other syntax rules of the XML specification, the most of which are designed to contain data; or empty:

- XML elements are declared to be non-empty, in which case they are designed to contain data; or empty, in which case they cannot contain data. For example, in particular, the <p> (paragraph) element is non-empty because it can contain text, whereas the <br> (line-break) element is empty because it cannot contain anything.
- Non-empty elements can be created from start and end tags (like the <p> ... </p> tags in XHTML). Empty elements should be created using the special empty-tag format (like the <br/> in XHTML). Unlike HTML, you cannot have a tag that isn't followed by an end tag.
- XML attributes are written inside the start tags of non-empty elements, or inside the empty tag of elements, and must be of the form name="value" or name='value'. No attribute name may appear more than once inside any given element. For example:

```xml
<item type="vegetable"> ... </item>
<emptyElement color='red' />
```

- XML elements must be properly nested, meaning given any element's start and end tags must be outside the start and end tags of elements inside it, and the start and end tags of its enclosing element. Here's an example:
<!-- Incorrect nesting -->
<parent><child></parent></child>
<!-- Correct nesting -->
<parent><child><child></child></child></parent>

# Part III: Using PHP Practice

Element names do not start with the characters "xml", "XML", or any upper- or lowercase combination of these characters in this sequence. Names must start with a letter, underscore, or a colon; but in practice, you should not use colons unless you're dealing with XML namespaces. Names are case-sensitive. Letters, numbers, the hyphen, the underscore, and the period are valid characters to use after the first character.

Comments are delimited in the same way as HTML comments (<!-- -->).

# Using XML Elements and Attributes

XML elements and their attributes form the hierarchical structure of an XML document, and contain the document's data. Although there can be only one root element, every element (including the root) may contain multiple elements (*referred to as child elements*). In addition, you're allowed to have multiple child elements all with the same name.

Each XML element may contain one or more attributes; however, an attribute may appear only once within any given element.

There is controversy about when to use an attribute and when to use a child element for containing data. There is no hard rule, but a good rule of thumb is:

- Use an element when you need to include the same field more than once in an element. For example, the `stockList` root element described earlier contains multiple child elements. It wouldn't be possible to do this with attributes, because you can't have more than one attribute with the same name for any given element.
- Use an attribute when you're sure the data will occur only once within the element, such as the `type` attribute for the `item` elements (an can be a fruit or a vegetable, but not both).

Another good rule of thumb is: use child elements for data that is core to the element, and use attributes for data that is peripheral to the element, or that uniquely identifies an element (such as an *id* attribute).

# Valid XML Documents: DTDs and XSDs

As explained earlier, a valid XML document is one that contains a reference to a DTD (document type definition) or an XSD (XML Schema definition), and whose content follows the general XML syntax rules (meaning if it is well-formed), and also the rules specified in the DTD or XSD (which means it is valid). The "stock list" XML document described earlier is both well-formed and (potentially) valid:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE stockList SYSTEM "http://www.example.com/dtd/stockList.dtd">
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
```

```xml
<quantity>67</quantity>
<description><![CDATA[Beetroots are lovely & purple]]></description>
</item>
</stockList>
```

# Chapter 19: Working with XML

The root element contains two item elements. Each element itself contains four children. The description elements contain CDATA sections to enclose their text data, because the data contains characters as >, < and & would otherwise be treated as markup:

```xml
<item type="fruit">
  <name>apple</name>
  <unitPrice>0.99</unitPrice>
  <quantity>412</quantity>
  <description><![CDATA[Apples are >>> yummy<<<]]></description>
</item>
<item type="vegetable">
  <name>beetroot</name>
  <unitPrice>1.39</unitPrice>
  <quantity>67</quantity>
  <description><![CDATA[Beetroots are lovely & purple]]></description>
</item>
```

Finally, the root element is closed:

```xml
</stockList>
```

# XML Syntax Rules

You now know what major components of an XML document are. In addition, a well-formed XML document must follow all other syntax rules of the XML specification, the most of which are designed to contain data; or empty:

- XML elements are declared to be non-empty, in which case they are designed to contain data; or empty, in which case they cannot contain data. For example, in particular, the <p> (paragraph) element is non-empty because it can contain text, whereas the <br> (line-break) element is empty because it cannot contain anything.
- Non-empty elements can be created from start and end tags (like the <p> ... </p> tags in XHTML). Empty elements should be created using the special empty-tag format (like the <br/> in XHTML). Unlike HTML, you cannot have a tag that isn't followed by an end tag.
- XML attributes are written inside the start tags of non-empty elements, or inside the empty tag of elements, and must be of the form name="value" or name='value'. No attribute name may appear more than once inside any given element. For example:

```xml
<item type="vegetable"> ... </item>
<emptyElement color='red' />
```

- XML elements must be properly nested, meaning given any element's start and end tags must be outside the start and end tags of elements inside it, and the start and end tags of its enclosing element. Here's an example:
<!-- Incorrect nesting -->
<parent><child></parent></child>
<!-- Correct nesting -->
<parent><child><child></child></child></parent>

Element names do not start with the characters "xml", "XML", or any upper- or lowercase combination of these characters in this sequence. Names must start with a letter, underscore, or a colon; but in practice, you should not use colons unless you're dealing with XML namespaces. Names are case-sensitive. Letters, numbers, the hyphen, the underscore, and the period are valid characters to use after the first character.

Comments are delimited in the same way as HTML comments (<!-- -->).

# Using XML Elements and Attributes

XML elements and their attributes form the hierarchical structure of an XML document, and contain the document's data. Although there can be only one root element, every element (including the root) may contain multiple elements (*referred to as child elements*). In addition, you're allowed to have multiple child elements all with the same name.

Each XML element may contain one or more attributes; however, an attribute may appear only once within any given element.

There is controversy about when to use an attribute and when to use a child element for containing data. There is no hard rule, but a good rule of thumb is:

- Use an element when you need to include the same field more than once in an element. For example, the `stockList` root element described earlier contains multiple child elements. It wouldn't be possible to do this with attributes, because you can't have more than one attribute with the same name for any given element.
- Use an attribute when you're sure the data will occur only once within the element, such as the `type` attribute for the `item` elements (an can be a fruit or a vegetable, but not both).

Another good rule of thumb is: use child elements for data that is core to the element, and use attributes for data that is peripheral to the element, or that uniquely identifies an element (such as an *id* attribute).

# Valid XML Documents: DTDs and XSDs

As explained earlier, a valid XML document is one that contains a reference to a DTD (document type definition) or an XSD (XML Schema definition), and whose content follows the general XML syntax rules (meaning if it is well-formed), and also the rules specified in the DTD or XSD (which means it is valid). The "stock list" XML document described earlier is both well-formed and (potentially) valid:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE stockList SYSTEM "http://www.example.com/dtd/stockList.dtd">
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
```

```xml
<quantity>67</quantity>
<description><![CDATA[Beetroots are lovely & purple]]></description>
</item>
</stockList>
```

# XHTML: An Example of DTDs In Action

As mentioned previously, anyone can author an XML document, and anyone can define a DTD or XSD against which to validate it. One well-known example of a DTD is XHTML, which is HTML reformulated as XML. The XHTML DTD is essentially similar to the existing HTML DTD, with very small modifications, and it defines all the elements, attributes, and other components allowed in an XHTML document. The main difference between HTML and XHTML is that the XHTML document at heart—must conform to the XML specification, whereas HTML documents are not required to do so.

To display an XHTML document as a regular web page, the document will be well-formed, and also validate against the XHTML DTD. In the next few seconds you examine a portion of the DTD for XHTML, learn how the DTD can be referenced in an XHTML document, explore XML namespaces, and learn to create an XHTML web page.

# The DTDs for XHTML

There are three DTDs for XHTML. They're located at:

+- www.w3.org/TR/xhtml/DTD/xhtmlml-strict.dtd
- www.w3.org/TR/xhtml/DTD/xhtmlml-transitional.dtd
- www.w3.org/TR/xhtml/DTD/xhtmlml-frameset.dtd
