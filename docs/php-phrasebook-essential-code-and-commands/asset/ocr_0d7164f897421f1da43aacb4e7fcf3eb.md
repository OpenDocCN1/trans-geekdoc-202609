# Using DOM in PHP 5 to Write XML

```
```php
$quote = $dom->createElement('quote');
$quote->setAttribute('year', $_POST['year']);
$phrase = $dom->createElement('phrase');
$phraseText = $dom->
createTextNode($_POST['quote']);
$phrase->appendChild($phraseText);
$author = $dom->createElement('author');
$authorText = $dom->
createTextNode($_POST['author']);
$author->appendChild($authorText);
$quote->appendChild($phrase);
$quote->appendChild($author);
$dom->documentElement->appendChild($quote);
$dom->save('quotes.xml');
echo 'Quote saved.';
?>
```
```

Creating XML with DOM (dom-write5.php; excerpt)

> > **NOTE**
> >
> > PHP 5's DOM extension does not offer something like PHP 5's `set_content()`, so you have to define the text values of the nodes using the `createTextNode()` method, as shown in the preceding code.

# Using SimpleXML

```
```php
$xml = simplexml_load_file('quotes.xml');
```
```

One of the greatest new features in PHP 5.1 is the SimpleXML extension, an idea borrowed from a Perl module in CPAN. The approach is as simple as it is ingenious. The most intuitive way to access XML is probably via an object-oriented programming (OOP)