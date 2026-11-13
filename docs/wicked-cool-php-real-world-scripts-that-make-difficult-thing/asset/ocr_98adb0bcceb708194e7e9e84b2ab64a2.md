The bottom line is that if you plan to run a number of web services queries based on WSDL at once, you either need a lot of hardware or some way to bypass most of this process by constructing SOAP queries by hand.

For these reasons, pure SOAP web services aren't as common as you might think. For example, the Amazon.com SOAP Web Service was added only recently, standing alongside a traditional REST service. Amazon.com documents the REST parameters but tells you to “look at the WSDL” for how to do it in SOAP. Another big company by the name of Google decided to discontinue SOAP support for its web search service. However, SOAP is not going away. In particular, you'll almost certainly need to deal with it whenever you encounter services based on Microsoft .NET.

# #73: Building a Web Service

To close out this chapter, let's take a quick look at how to build a REST web service. The idea is similar to almost any other kind of dynamic web page, but rather than worrying about how the page looks, all you need to do is properly construct an object, transform the object to XML, and print the result. After that, everything else is someone else’s problem (at least, in theory).

We'll use the data from the example table in the appendix. The web service takes a category parameter (as POST or GET) and returns an XML product listing such as this:

```
<?xml version="1.0" encoding="utf-8"?>
<Items>
<Item>
<Name>Cowboy Boots</Name>
<ID>12</ID>
<Price>19.99</Price>
</Item>
<Item>
<Name>Slippers</Name>
<ID>17</ID>
<Price>9.99</Price>
</Item>
</Items>
```

There are many ways to create XML in PHP, from using the DOM to using the xmlWriter functions. We'll use the SimpleXML class from earlier in this chapter. The first thing to do is initialize the database, tell the client that it is about to receive XML, and verify the category parameter. This is mainly busy work; you've seen plenty of code like this by now (don't worry about printerror(); we'll get to it in a bit):

```
<?php
$db = mysql_connect("localhost", "username", "passwd");
mysql_select_db("wcphp");

header("Content-type: text/xml");
```