accessing XML data was ruthlessly complicated; as a result, a myriad of parsing systems appeared, such as DOM and SAX. If you've ever been confused by the 27,000 different XML extensions available in PHP, you now know why.

The good news is that somewhere along the way, people realized that most of the time they were just parsing the XML data into a tree composed of a bunch of nested arrays, so that programmers could use normal data-access tools such as operators and indexes. A new generation of parsers appeared to serve this purpose; PHP 5 includes such an extension, called SimpleXML.

Here's some sample XML to get us started with SimpleXML:

```
<?xml version="1.0" encoding="utf-8"?>
<preaching>
<sins>
    <sin type="deadly">gluttony</sin>
    <sin type="minor">bad puns</sin>
    <sin type="required">flatulence</sin>
</sins>
</preaching>
```

This XML contains nested nodes, data, and attributes, so it covers most of what you'll ever encounter. To parse it with SimpleXML, load the data into a string and create a SimpleXMLElement object from the string:

```
$xs = file_get_contents("test.xml");
$data = new SimpleXMLElement($xs);
```

**NOTE** _You can use simplexml_load_file() to create the object from a file instead of using this two-step process._

If you don't get an overly verbose error message, the XML is now in the $data object. To look at the first sin in the <sins> node, use a combination of object- and array-access syntax:

```
print $data->sins->sin[0];
```

The output is gluttony; if you wanted to access the bad puns node, you'd look at $data->sins->sin[1]. If you omit the array index ($data->sins->sin), you'll get the first element of the array; this is handy if you know that there is a single element.

You can look at a node's attributes using array indexes as well, except this time the indexes are keys instead of numbers. For example, to find out what type of sin bad puns is, use the following:

```
print $data->sins->sin[1]["type"];
```

Probably the best thing about the array syntax is that you iterate over nodes.