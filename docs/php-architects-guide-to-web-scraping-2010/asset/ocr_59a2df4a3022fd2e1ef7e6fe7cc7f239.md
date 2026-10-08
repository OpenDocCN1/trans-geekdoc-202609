# ## DOM Interoperation

One nice feature of the XMLReader extension is the expand() method, which returns an object of the equivalent DOM extension class for the node to which the iterator currently points. Element nodes, for example, cause this method to return a DOMElement instance.

The example below illustrates a modification to the previous example and provides another alternative to the readString() method for getting at the contents of table cells by taking advantage of this DOM interoperability.

```
```php
<?php
if ($doc->localName == 'td' && $inTable) {
    $node = $doc->expand();
    $tableData[$row][] = $node->nodeValue;
}
?>
```
```

# ## Closing Documents

Once all necessary read operations have been conducted on a document, the close() method of the XMLReader instance should be called to cleanly terminate file access or otherwise indicate that access to the original data source is no longer needed.

# ## Wrap-Up

Hopefully this chapter has given you an idea of how pull parsers work in general and when it's better to use one like XMLReader over a tree parser. For more information on XMLReader, check out its section in the PHP manual at http://www.php.net/manual/en/book.xmlreader.php.