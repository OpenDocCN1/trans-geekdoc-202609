By using valid XML documents, applications that know nothing about each other can still communicate effectively — they just have to exchange XML documents, and understand the meaning of the DTD or XSD against which those documents are validated. This is one of the main features that make XML so powerful.

# Major Parts of an XML Document

Broadly speaking, a well-formed XML document may contain the following:

+   - An XML declaration at the top of the document, possibly including a character encoding declaration. This declaration is a good idea, but it's not mandatory. If no XML declaration is given, version 1.0 is normally used. If no character encoding is specified, UTF-8 is assumed. For example:
+   <?xml version="1.0" encoding="UTF-8" ?>

+   - An optional DTD or an XSD, or a reference to one of these if they are stored externally. This must appear before the document's root element. For example, here's a reference to an external DTD:
+   <!DOCTYPE stockList SYSTEM "http://www.example.com/dtds/stockList.dtd">

+   - All XML documents must contain one — and only one — root element. This element usually contains one or more child elements, each of which may optionally have one or more attributes. An element can contain other child elements or data between its beginning and ending tag, or it may be empty

+   - XML documents may contain additional components such as processing instructions (PIs) that provide machine instructions for particular applications; CDATA sections, which may contain special characters that are not allowed in ordinary XML data; notations; comments; entity references (aliases for entities such as special characters); text; and entities. You look at some of these components later in the chapter

Here's an enhanced version of the stockList example document used earlier that illustrates each of these major parts. First the XML declaration:

```
<?xml version="1.0" encoding="UTF-8" ?>
```

Next is the reference to a DTD that defines the allowed elements and attributes in the document:

```
<!DOCTYPE stockList SYSTEM "http://www.example.com/dtds/stockList.dtd">
```

Now the root element begins. Remember that there can be only one root element in an XML document:

```
<stockList>
```