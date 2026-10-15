# Using XML

(including its author and the year the phrase was coined) is contained in a <quote> element.

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<quotes>
  <quote year="1991">
    <phrase>Hasta la vista, baby!</phrase>
    <author>Arnold Schwarzenegger</author>
  </quote>
</quotes>
```

# The sample XML file (quotes.xml; excerpt)

# Parsing XML with SAX

```
$sax = xml_parser_create();
```

SAX is an approach to parse XML documents, but not to validate them. The good thing is that you can use it with both PHP 4 and PHP 5 with no changes. In PHP 4, the SAX parsing is already available on all platforms, so no separate installation is necessary.

```
<?php
// ...
$sax = xml_parser_create();
xml_parser_set_option($sax, XML_OPTION_CASE_FOLDING, false);
xml_parser_set_option($sax, XML_OPTION_SKIP_WHITE, true);
xml_set_element_handler($sax, 'sax_start', 'sax_end');
xml_set_character_data_handler($sax, 'sax_cdata');
xml_parse($sax, file_get_contents('quotes.xml'), true);
xml_parser_free($sax);
?>
```