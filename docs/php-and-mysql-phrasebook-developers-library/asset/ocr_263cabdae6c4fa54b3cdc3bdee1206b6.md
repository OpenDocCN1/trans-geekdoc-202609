DOMDocument object, and then you load() a file or loadXML() a string. The new object supports, among other functionality, the two methods getElementsByTagname() and getElementById() that return all nodes with a certain tag name or a specific element identified by its ID. Then each node exposes some properties such as the following:

+   - `firstChild` — First child node
+   - `lastChild` — Last child node
+   - `nextSibling` — Next node
+   - `previousSibling` — Previous node
+   - `nodeValue` — Value of the node

The preceding code uses DOM to access all quotes in the XML file and outputs them.

Note that the listings use instanceof so that the tag names are only evaluated in nodes of the type DOMElement. This is because whitespace is considered as a DOM node (however, of type DOMText).

# Using DOM to Write XML

```
```php
$dom->save('quotes.xml');

<?php
$dom = new DOMDocument();
$dom->load('quotes.xml');
$quote = $dom->createElement('quote');
$quote->setAttribute('year', $_POST['year']);
$phrase = $dom->createElement('phrase');
$phraseText = $dom->
->createTextNode($_POST['quote']);
$phrase->appendChild($phraseText);
```
```