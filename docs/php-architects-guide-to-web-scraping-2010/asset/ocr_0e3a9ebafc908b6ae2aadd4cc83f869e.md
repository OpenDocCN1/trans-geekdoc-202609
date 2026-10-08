# ## Chapter 12

# # XMLReader Extension

The previous two chapters have covered two available XML extensions that implement tree parsers. This chapter will focus on the XMLReader extension, which implements a pull parser.

As mentioned in the chapter on the DOM extension, pull parsers differ from tree parsers in that they read documents in a piecewise fashion rather than loading them into memory all at once. A consequence of this is that pull parsers generally only traverse documents once in one direction and leave you to collect whatever data is relevant to you along the way.

Before getting started, a noteworthy point is that XMLReader’s underlying library, libxml, uses UTF-8 encoding internally. As such, encoding issues will be mitigated if any document you imported (particularly one that’s been cleaned using the tidy extension) is encoded appropriately to avoid issues with conflicting encodings.

> **XML Parser**

The XML Parser extension, as it is referred to in the PHP manual, is a predecessor of XMLReader and an alternative for PHP 4 environments. Its API is oriented to a more event-driven style of programming as opposed to the iterative orientation of the XMLReader extension. For more information on the XML Parser extension, see http://php.net/manual/en/book.xml.php.