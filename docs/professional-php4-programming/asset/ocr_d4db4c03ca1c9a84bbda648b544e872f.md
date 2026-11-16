The idea of a context node is important when we're working with relative paths. A relative path is relative to the context node. Using relative paths we can select all instances of City that are children of Travelpackage like //Travelpackage/City. Or if we want the second instance then //Travelpackage/City[2].

Let's look at some syntax examples:

| XPath | Description |
|---|---|
| //City | Selects all instances of the City node |
| /City/* | Selects all children of City |
| //City/text() | Selects the text node of all instances of a City node, (Cayo Coco, Varadero) |
| //@* | Selects all attributes within the document (name=a, name=b, an so on) |
| //Travelpackage[@name="a"]/* | Selects all the children of <Travelpackage name="a"> but not the grandchildren <Package_dateofdep> and <Package_price> |
| //* | Selects all nodes under root (it selects all nodes) |
| //Travelpackage/*/* | Selects all nodes under Travelpackage/any_other_node/, like Package_dateofdep and Package_price |

You can find a good summary of XPath at: http://www.zvon.org/HTMLonly/XPathTutorial/General/examples.html.

> It is best to use the XPath Tester to test XPath statements. XPath Tester is written in Java and is available as an open source application from FiveSight at http://www.fivesight.com/downloads/XPathtester.asp. You will need to have Java 2 for XPath Tester to run. With this application you can load an XML document and run XPath statements against the document to see what your statement will return.

# Reading XML with DOM

Let's now look at reading from an XML file and sending HTML out to the browser. Given the power of XPath, one could think that it is a simple matter of selecting all the nodes and sending them to the browser.

Here's the code that displays the XML file as HTML. First we create a new XML object, called $doc. Then we create a new context so we can use XPath to reference the nodes in the DOM tree:

```
<html>
<head>
<title>DOM Travel Packages</title>
</head>
```