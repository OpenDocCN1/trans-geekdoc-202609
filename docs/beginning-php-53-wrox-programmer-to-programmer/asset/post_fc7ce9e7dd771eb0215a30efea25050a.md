
# Part III: Using PHP in Practice

- http://example.com/hello/there.html
- www.example.com/hello/there.html
- https://www.example.com

2. Enhance the find_links.php script created earlier in the chapter to display not just the URL of each link, but also the link text (the text between the `<a>` and `</a>` tags).

# Working with XML

XML — Extensible Markup Language — lets you create documents that can hold data in a structured way. It was originally designed to be a human-readable means of exchanging structured data, but it has also gained very quickly as a means of storing structured data. XML is different from a database in many ways, both XML and databases offer ways to format and store structured data, and both technologies have advantages and drawbacks.

XML isn't really a language but rather a specification for creating your own markup languages. It is a subset of Standard Generalized Markup Language (SGML, the parent of HTML). XML is intended to allow different applications to exchange data easily. If you're familiar with HTML, you'll notice similarities in the way HTML and XML documents are formatted. Although HTML has a fixed set of elements and attributes defined in the HTML specification, XML lets you create your own elements and attributes, giving you the capability to define your language in XML (or to use someone else's definition). Essentially, you can format any data you want using XML.

In addition, the definition of an XML-based language can be placed online for any person or application to read. So two applications that know nothing about each other can exchange data as long as both have the ability to read and write XML.

For these reasons XML is rapidly becoming the exchange standard, and many useful technologies have been created on top of XML, such as:

- Web Services, including languages such as SOAP for exchanging information in XML format over HTTP; XML-RPC (SOAP's simpler ancestor), and the Web Services Description Language (WSDL), for describing Web Services
- Application file formats, such as Open OpenDocument Format (ODF) and Microsoft's Office XML (OOXML) that are used to store word processing documents, spreadsheets, and so on
- RSS and Atom news feeds that allow Web applications to publish news stories in a universal format that can be read by many types of software, from news readers and clients through to other Web applications

# Part III: Using PHP Practice

PHP has many features and functions that make working with XML data fast and efficient, as well as intuitive. In this chapter you learn the basics of XML, and how to create XML documents from scratch. You then move onto using PHP's XML Parser extension to read and parse XML documents programmatically.

Once you've mastered XML, explore PHP's DOM extension that gives you a lot of power to read, create, and manipulate XML documents; then you take a look at SimpleXML — a nice, easy way to read and perform simple operations on XML data. Finally, you take a look at another aspect of XML called XSL, and examine PHP's XSLProcessor class for transforming XML documents into other formats.

# What Is XML?

XML is a specification for creating your own markup languages. In turn, you use these markup languages to create documents. Like HTML, an XML document contains elements and attributes in the form of tags.

Though XML documents are human-readable, many applications are designed to parse XML documents automatically and work efficiently with their content. PHP has many XML-related functions that can be easily used to work with XML documents, or transform non-XML data into XML documents.

You can make your own XML document as follows:

```
<xml version="1.0" ?>
<stockList>
  <item type="fruit">
    <name>apple</name>
    <unitPrice>0.99</unitPrice>
    <quantity>412</quantity>
  </item>
  <item type="vegetable">
    <name>beetroot</name>
    <unitPrice>1.39</unitPrice>
    <quantity>67</quantity>
  </item>
</stockList>
```

The first line of the document is called the XML declaration; it indicates that the following lines comprise an XML document, and specifies the version of XML that is used to create the document. The second line defines the root element of the document named stockList. There can be only one root element for an XML document. The third line defines a child element of the root element, named item, and it contains an attribute type that is set to the value fruit.

From reading this XML document, you can tell that:

- It stores a list of stock items
- There are 412 apples available, and an apple is a fruit and costs $0.99
- There are 67 beets available, and a beetroot is a vegetable and costs $1.39

# Chapter 19: Working with XML

Like HTML, XML documents are composed primarily of elements and attributes. Each element may optionally contain one or more child elements; in the example document shown there are two item elements inside the stockList element, and each item element itself contains three children. An element may also contain plain text rather than child elements (as the text apple inside the first name element in the example document).

It's also possible for an XML element to contain both child elements and plain text, though this usage isn't common in practice.

Each element can optionally have one or more attributes; these are specified in the format name="value" inside the element's opening tag (such as `<item type="fruit">` in the example document).

Anyone can write XML documents, and many folks design applications to handle XML documents — reading existing documents and creating new ones. The XML specification is free for use; the World Web Consortium at w3.org authored and maintains the latest versions.

Although you can write XML documents by creating arbitrary elements and attributes — as shown in the stocklist example — often you want to specify the elements and attributes that are allowed in a document, as well as their meaning and structure. This is so, when you exchange data with another person or application, both parties to the transaction know exactly what the element and attribute mean. To do this, you use either a type definition (DTD) or an XML Schema (XSD); DTDs are discussed in a later chapter.

When you create XML documents, you'll either use a publicly available DTD or one you've written yourself. Once you write a DTD, you can publish it on the Web. This means anyone who needs to read or write an XML document compatible with your system has the capability to access the DTD to make sure the document is valid.

# Document Structure

Two terms that you hear when discussing XML are well-formed and valid. A well-formed XML document follows the basic syntax rules (to be discussed in a moment), and a valid document follows the rules imposed by a DTD or an XSD. In other words:

- All documents must be well-formed — A well-formed XML document uses correct XML syntax. It may contain any elements, attributes, or other constructs allowed by the XML specification, but there are no rules about what the names of those elements and attributes can be (other than the basic naming rules, which are not really much of a restriction) or about what their content can be. It is in this extensibility that XML really derives a lot of power and usefulness; so long as you follow the basic rules of the XML specification, there's no limit to what you can add or change
- An XML document can also be valid — A well-formed document does not need to be valid, a valid document must be well-formed. A well-formed document contains a reference to a DTD or XSD, the document can be checked against the DTD or XSD to determine if it's valid. An XML document is valid if its elements, attributes, and other contents follow the rules in the DTD or XSD.
