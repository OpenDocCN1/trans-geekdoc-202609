;extension=php_xsl.dll
and restart the Web server. (If you've installed MAMP on Mac OS X, the XSL extension should already be installed.)

![](bbox=[0.253, 0.185, 0.823, 0.563])

Figure 19-5

That's the basis of using XSLTProcessor to transform XML files; however, you can do a lot more with this class, including calling PHP functions from the XSLT style sheet, and outputting the resulting XML from a transformation as DOMDocument object or as a file. For more information, see http://www.php.net/manual/en/class.xsltprocessor.php.

# # Summary

In this chapter you explored the concept of XML, and learned how to manipulate XML documents using PHP. You learned the basics of XML and looked at why it's useful. You then explored the various components that make up an XML document, such as:

+   - Elements and attributes, including the concept of the root element
- XML declarations and character encodings
- Document type definitions (DTD) and XML Schema definitions (XSD)
- Other components such as CDATA sections and comments