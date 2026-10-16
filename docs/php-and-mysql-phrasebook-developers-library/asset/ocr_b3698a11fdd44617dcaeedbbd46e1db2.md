One of the best guarded secrets of SimpleXML is that the extension has a built-in support for XPath, the XML query language. Using it is easy: After creating a SimpleXML object, you can use the xpath() method and get all matching nodes in return.

# Transforming XML with XSL

```
$xslt = new XSLTProcessor();
```

```
```php
<?php
$xml = new DOMDocument();
$xml->load('quotes.xml');
$xsl = new DOMDocument();
$xsl->load('quotes.xsl');
$xslt = new XSLTProcessor();
$xslt->importStylesheet($xsl);
$result = $xslt->transformToDoc($xml);
echo $result->saveXML();
?>
```
```

*Using XSLT with PHP (xslt.php)*

Transforming XML into another format is usually done by XSLT (XSL Transformation). In PHP, XSLT is done by libxslt and can be enabled using php_xslt.dll (in php.ini) on Windows and the switch --with-xslt on other platforms. Writing the XSL file may be hard, but the PHP code afterward is quite simple: Load both the XML and the XSLT (which is an XML document, as well) into a DOM object, and then instantiate an XsltProcessor object. Call importStylesheet(), and then transformToDoc().

The preceding phrase contains the code for these steps, the file quotes.xsl in the download repository