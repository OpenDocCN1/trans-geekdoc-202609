
# ...cont'd

```
Date: <?php echo $orgdate; ?><td></td></tr>
<tr><td colspan="2">Comments:</td></tr>
<?php echo $row["comments"]; ?><td></td></tr>
</table>
<br>
<?php ?>

</body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_174_0.png)

Even with ten entries added to the guestbook database table, the script generates HTML tables for only the last three entries. The visitor's email address is formatted as a link with the "mailto:" protocol to make email response simpler.

Clicking a hyperlink that uses the mailto protocol will open your default client application with the target address already completed – just type a reply then send the email response.

![](img/7faa63a7fa0add8f53300594ebae949f_174_1.png)

| Name: Sally | Email: sal@some-mail-server.com |
|---|---|
| Date: Saturday June 18th, 2005 11:47 AM | |
| Comments: Interaction keeps your visitors invited | |
| Name: Joe Bloggs | Email: joe@someplace.com |
|---|---|---|
| Date: Saturday June 18th, 2005 11:40 AM | |
| Comments: Now you too can use PHP to build better websites | |
| Name: Tony | Email: tony@abc.com |
|---|---|---|
| Date: Saturday June 18th, 2005 11:12 AM | |
| Comments: PHP is great! | |

13. A PHP guestbook | 177

# Saving the guestbook

The mysqldump program, located in MySQL’s bin directory, can be used to save any MySQL database or table as a text file.

To save the guestbook table created in this chapter, first navigate from a command prompt to MySQL’s bin directory. Type “mysqldump --help” to see a list of options. The command syntax to save a simple table is:

```
mysqldump [ options ] database-name table-name > file-name
```

Use a “-t” option (to suppress the table creation info) followed by the “my_database” name and “guestbook” table name. Finally, use the “>” character to direct output to a file named “guestbook.txt”.

![](img/7faa63a7fa0add8f53300594ebae949f_175_0.png)

![](img/7faa63a7fa0add8f53300594ebae949f_175_1.png)

![](img/7faa63a7fa0add8f53300594ebae949f_175_2.png)

The text file gets created in the directory unless a path precedes specifies the filename, as > C:\guestbook.txt

PHP 5 in easy steps

# PHP and XML

This chapter demonstrates how PHP can be used with XML documents. It shows how to selectively extract data from them for output to a web browser, and how PHP scripts can add data to an XML document.

# Covers

- Introducing XML | 176
- Reading from the DOM | 178
- Writing to the DOM | 180
- Querying with XPath | 182
- Using SimpleXML | 184
- More PHP resources | 186

# Introducing XML

PHP version 5 introduces enhanced support for object oriented programming and completely new support features for the increasingly important XML (eXtensible Markup Language). Its XML support is now compliant with the W3C (World Wide Web Consortium) specifications – unlike in previous releases.

PHP 5 supports DOM (Document Object Model) according to the W3C standard, and the XPath query language. It also incorporates the PHP-specific "SimpleXML" extension. Examples of DOM, XPath and SimpleXML are given in this chapter.

XML is a popular means of storing data, which adopts a strict syntax. It looks very much like HTML, complete with tags, attributes, and values, but XML has no predefined tags and is not used to create web pages. Instead, XML lets you create your markup tags and define how these tags may.

In XML each opening tag must have a matching tag, and tag pairs must be correctly nested. XML documents that meet these requirements are said to be "well-formed". The advantage for applications handling well-formed data is that they do not allow for incorrect syntax – unlike web browsers handling HTML documents, which include a lot of code.

All XML documents begin with a declaration tag, which announces that the document is using XML. This typically includes attributes that describe the version and character encoding, like this:

```
<?xml version="1.0" encoding="iso-8859-1"?>
```

The declaration specifies that this document is written with XML version 1.0 in the common Latin set. All XML documents must have a main tag that encloses all other tags. This tag is more called the "root" element.

![](img/7faa63a7fa0add8f53300594ebae949f_177_0.png)

```
<?xml version="1.0" encoding="iso-8859-1"?>
<root>
  <greeting>Hello World</greeting>
</root>
```

# ...cont'd

In the well-formed XML document hello.xml, listed opposite, the root element is actually named “root”. The nested element named “greeting” contains text content of “Hello World”.

In practice most XML documents contain many tags, describing a deal of data. For instance, the books.xml document, listed below, contains data describing some books. Within the “books” root element each “title” element contains nested tags for “topic”, the “series” name, and the name of the book within an element called “pic”.

![](img/7faa63a7fa0add8f53300594ebae949f_178_0.png)

```
<?xml version="1.0" encoding="iso-8859-1"?>
<books>
  <title>
    <topic>JavaScript</topic>
    <series>in easy steps</series>
    <pic>js.gif</pic>
  </title>
  <title>
    <topic>C++ Programming</topic>
    <series>in easy steps</series>
    <pic>c++.gif</pic>
  </title>
  <title>
    <topic>HTML</topic>
    <series>in easy steps</series>
    <pic>html.gif</pic>
  </title>
  <title>
    <topic>SQL</topic>
    <series>in easy steps</series>
    <pic>sql.gif</pic>
  </title>
</books>
```

![](img/7faa63a7fa0add8f53300594ebae949f_178_1.png)

> HOT TIP Opening a XML document in a web browser, such as Internet Explorer, displays the tags in “tree” if the document is well-formed. Otherwise, an error message indicates the cause of the error.

This XML document is used by some examples in this chapter to demonstrate support features in PHP 5.

# Reading from the DOM

PHP 5 has built-in support for the Document Object Model (DOM) as specified by the W3C standard. This provides a “DomDocument” template class containing predefined variables and methods (or functions).

A DomDocument object can be created in a PHP script using the “new” keyword to assign an instance of the class to a variable. For example, $dom = new DomDocument creates a DomDocument object in the $dom variable.

The variable properties and the methods of an object can be referenced using the special class operator “->”. For instance, the DomDocument object has a load() method to load an XML file, so that $dom -> load(“books.xml”) loads the data from the file “books.xml” into the $dom object.

Each element of the XML document is described as a “node”.

The root element of the XML document can be accessed using the DomDocument’s “documentElement” property, and its tag name can be referenced from its inherent “nodeName” part. For example, $dom -> documentElement -> nodeName.

Specific nested elements of the XML document can be addressed using the DomDocument’s “getElementsByTagName()” method, which takes the name of the required element as a parameter. This method returns a “NodeList”, which a script can easily loop through using the foreach() function. The textual data of each node can be referenced by the “textContent” property, which PHP provides.

The textContent property is not an actual W3C standard – it is a PHP convenience property, to access all text nodes of an element quickly.

The script creates a DomDocument object, then loads the “books.xml” document (listed on the previous page). It proceeds to generate HTML output stating the XML document’s root element name and a list of all the text contained within its “topic” elements.

![](img/7faa63a7fa0add8f53300594ebae949f_179_0.png)

# ...cont'd

```
<html><head><title>Read DOM</title></head><body>
```

```php
<?php

# load an xml document into the DOM
$dom = new DomDocument();
$dom -> load("books.xml");

# print the root element name
echo("Root element name is: ");
echo($dom -> documentElement -> nodeName);
echo("<hr>");

## print a list of all topics
echo("Topics include:<ul>");
$topics = $dom -> getElementsByTagName("topic");
foreach($topics as $node) {
	echo("<li>" . $node -> textContent . "</li>");
}
echo("</ul>");

?>

</body></html>
```

![](img/7faa63a7fa0add8f53300594ebae949f_180_0.png)

![](img/7faa63a7fa0add8f53300594ebae949f_180_1.png)
