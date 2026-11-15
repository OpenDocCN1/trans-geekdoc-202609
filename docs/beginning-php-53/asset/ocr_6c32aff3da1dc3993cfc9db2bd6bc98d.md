# # Working with XSL and XSLT

XSL (Extensible Stylesheet Language) is actually a group of languages that allow you to convert an XML document into another format. The main language within this group is XSLT (XSL Transformations), a language that lets you use a series of rules to transform the data in an XML document into another form. This new form might be another machine-readable XML document, or it might be a human-readable XHTML document (that is, a Web page).

PHP provides you with a class called XSLTProcessor that you can use to carry out XSLT transformations. In this section you learn how to use it to convert the `stock_list.xml` file into a nice, human-readable Web page.

Here’s the XSLT style sheet that contains the rules for the transformation:

```
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet
    version="1.0"
    xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
    xmlns="http://www.w3.org/1999/xhtml">

<xsl:output method="html"/>

<xsl:template match="/StockList">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <title>Transforming XML to XHTML</title>
    <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
    <h1>Stock List</h1>
    <ul style="list-style: none;">
    <xsl:apply-templates select="item" />
    </ul>
</body>
</html>
</xsl:template>

<xsl:template match="item">
    <li>
    <dl>
        <dt>Name:</dt>
        <dd><xsl:value-of select="name"/></dd>
        <dt>Quantity:</dt>
        <dd><xsl:value-of select="quantity"/> left</dd>
        <dt>Unit Price:</dt>
        <dd>$<xsl:value-of select="unitPrice"/></dd>
        <dt>Description:</dt>
        <dd><xsl:value-of select="description"/></dd>
    </dl>
    </li>
</xsl:template>

</xsl:stylesheet>
```