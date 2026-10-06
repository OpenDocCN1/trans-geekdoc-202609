
# Part III: Using PHP Practice

These three DTDs complement your HTML counterparts, are, in fact, quite similar. If you enter these URLs in your browser, you'll actually see the DTD in plain text. (You might need to download the DTD file and open it in your editor)

Here is a portion of the XHTML Strict DTD showing how the img (image) element is declared:

```
<--
To avoid accessibility problems for people who aren't
able to see the image, you should provide a text
description using the alt and longdesc attributes.
In addition, the use of server-side image maps.
Note that in this DTD there is no name attribute. That
is only available in the transitional and frameset DTD.
-->

<!ELEMENT img EMPTY>
<!ATTLIST img
%attrs;
  src           #REQUIRED
  %Text          #REQUIRED
  alt           #IMPLIED
  longdesc      #IMPLIED
  height        #IMPLIED
  width         #IMPLIED
  usemap        %URI#IMPLIED
  ismap         (ismap)#IMPLIED
>
<!-- usepoints to map a map element which may be in this document
or or an external document, although the latter is not widely supported -->
```

On the first line following the comment, the img element is declared EMPTY (that is, it contains no
content, only attributes). Following the ELEMENT line is a list of attributes that may be included inside the
img tag in an XHTML document. Those of you with HTML and XHTML do not recognize
tsrc attribute in an XML document that specifies the location of the image file; this attribute is REQUIRED.

On this portion of the DTD for XML documents, it is possible to include img elements
in documents. If the DTD is referenced in an XML document, the document includes an img
element with an optional src attribute, the document could be said to be valid (at least as far as
im is considered). However, if you tried to use an element name imge or image or images,
validating XML parser would produce an error, because according to the DTD such elements are not
declared, and the document is not valid.

# Referencing DTDs

To reference an external DTD, you use DOCTYPE declaration. This declaration indicates the name and
t location of the DTD. For example, this line shows how to reference the XHTML Strict DTD:

```
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml/xhtml-strict.dtd">
```

# Chapter 19: Working with XML

The html after the <!DOCTYPE> in the first line signifies that the root element is named html. The declaration also includes the URI of the DTD at the www.w3.org Web site. If the DTD is an external document, it can be located anywhere, and identified by any URI that the application reading understands and has access to, not just a URL over the Internet.

# Specifying Namespaces

An XML namespace indicates the source of names for elements and attributes. Being able to specify the source of an element or attribute name means you can use the same name to represent different things within a single document. An XML document may reference multiple namespaces, if required.

A namespace can be identified in an XML document by referencing it via a special XML keyword: the xmlns (XML Namespace) attribute. When applied to an element, the namespace is then valid for that element and its children.

For example, all elements in an XHTML document must be in an XHTML namespace. The simplest way to do this is to use the xmlns attribute on the root element (html) of the XHTML document. Defining the root element also serves to define the namespace for all of its children — that is, the rest of the elements and attributes in the document

```
<html xmlns="http://www.w3.org/1999/xhtml">
```

# Creating an XHTML Document

Now that you understand how to create a valid XML document, you can apply this knowledge to create an XHTML document.

To do this, start by identifying the version of XML you're using, and provide a DOCTYPE declaration referencing the DTD. Create the root element — html and include the xmlns attribute to declare the XHTML namespace for this element (and all its children). Finally, you can include all child elements under the root element — in other words, the content of your XHTML page.

Here's an example:

```
<xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/DTD/xhtml-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
<title>An XML example</title>
</head>
<body>
<p>This is an example of an XHTML document. It can contain images
<img src="http://www.example.com/image.gif" alt="image" /> as
links as <a href="http://example.com/">example</a> and any other
HTML elements, provided they conform to the XML syntax rules.</p>
</body>
</html>
```

Of course, this document looks very like an ordinary HTML document, and will be displayed just like any page written in HTML browsers. However, unlike an HTML document it conforms to the XML specification, and is not only well-formed but also valid.

# Reading XML Documents with PHP

Recently, the XML specification has gained prominence as a mechanism of exchanging and storing data.

# How Parser Works

The process of parsing XML involves several steps:

- Create a new parser using `xml_parser_create()`.
- Register event handlers using `xml_set_element_handler()` and `xml_set_character_data_handler()`.
- Parse the XML document using `xml_parse()`.
- Destroy the parser resource using `xml_parser_free()`.

# Creating a New Parser

The process of creating a new parser is easy. Simply call `xml_parser_create()` to generate a new parser, and store the resource in a variable:

```php
$parser = xml_parser_create();
```

You can optionally add an argument that specifies the encoding in which character data is passed to your event handlers. By default, the parser sends UTF-8, but you can change this to ISO-8859-1 or US-ASCII if you prefer. For example:

```php
$parser = xml_parser_create("US-ASCII");
```

# Creating Event Handlers

Now that you have a parser to work with, you need to create functions to handle the start of an element, the end of an element, and character data.

The function that deals with the start of an element needs to accept three arguments: the parser resource, the element name, and an associative array of any attributes in the element. For example:

```php
function startElementHandler($parser, $element, $attributes) {
    // (process the start of the element)
}
```

The end-element handler is similar, but it doesn't have to deal with attributes:

```php
function endElementHandler($parser, $element) {
    // (process the end of the element)
}
```

Finally, the character data handler needs to accept the parser resource, and a string containing the character data.

```php
function characterDataHandler($parser, $data) {
    // (process the character data)
}
```

Obviously the example handlers don't do any processing of the elements or data. You will write real handlers in a moment.

Once you've created your three event handlers, you register them with the parser. To register the start and end handlers use `xml_set_element_handler()`, passing in the parser resource, followed by the names of the start element handler and end element handler functions as strings. For example:

```php
xml_set_element_handler($parser, "startElementHandler", "endElementHandler");
```

To register the character data handler call `xml_set_character_data_handler()`, passing in the parser resource followed by the handler function's name as a string:

```php
xml_set_character_data_handler($parser, "characterDataHandler");
```
