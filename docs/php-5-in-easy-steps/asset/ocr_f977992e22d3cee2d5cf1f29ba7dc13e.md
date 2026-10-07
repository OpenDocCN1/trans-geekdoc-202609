# ...cont'd

The full line of titles in this series can be explored in good book stores and online at www.ineasysteps.com.

![](bbox=[0.305, 0.078, 0.953, 0.568])

The DOM and SimpleXML provide complementary tools for processing XML data in PHP scripts. Conveniently, SimpleXML objects can be easily converted to DomDocument objects, and vice versa. This lets you use the tool best suited for the job in hand. The conversion functions work like this:

+   - $dom = dom_import simplexml($sx) - converts a SimpleXML object to a DomDocument object
- $sx = simplexml_import_dom($dom) - converts a DomDocument object to a SimpleXML object

The examples in this chapter utilize the most popular functions to process XML data. Details of other SimpleXML and DOM functions are provided in the PHP documentation, available online at www.php.net.

14. PHP and XML | 185