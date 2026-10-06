# Chapter 19: Working with XML

![](bbox=[0.218, 0.072, 0.802, 0.535])

Figure 19-4

The script kicks off by calling the SimpleXML function simplexml_load_file() to load the root stockList in the stock_list.xml file as a SimpleMLElement object, $stockList.

You'll notice that the script passes two additional arguments to simplexml_load_file(). The first, "SimpleMLElement", is the class name for the resulting object. This allows you to inherit the base SimpleMLElement to create your own custom elements. However, in this case the script just passes in the default class name, "SimpleXML", to create a normal SimpleXMLCDATA constant. This ensures that the SimpleXML library reads the CDATA sections of the XML document and converts them to text nodes to make them easy to display with the print_r() function.

Once the XML is read into a SimpleMLElement object, it's simply a case of using print_r() to dump the object to the browser. To do this, the script passes a second argument of true to print_r(); this ensures that print_r() returns a string rather than outputting to the browser. The script then uses htmlspecialchars() to ensure the string is properly encoded as XHTML, sending the result to the browser.

You can see from the output that the $stockList object contains an array that contains the two item elements in the XML document. Each item element is itself stored as

609