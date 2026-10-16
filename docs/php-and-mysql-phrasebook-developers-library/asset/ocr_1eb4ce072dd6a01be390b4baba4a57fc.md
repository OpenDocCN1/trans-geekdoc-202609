contains markup that transforms the quotes' XML into the well-known HTML bulleted list.

# Validating XML

```
$dom = new DOMDocument;
$dom->load('quotes.xml');
echo 'Validation ';
(($dom->relaxNGValidate('quotes.rng')) ? 'succeeded.' : 'failed.');
?>
```

Validating XML against relaxNG (validate-rng.php)

PHP can validate XML against three types of files: Document Type Definitions (DTDs), Schemas (.xsd), and relaxNG. For the last two, the following four methods of the DOM object are available:

+   - schemaValidate('file.xsd')—Validates against a Schema file
+   - schemaValidateSource('...')—Validates against a Schema string
+   - relaxNGValidate('file.rng')—Validates against a relaxNG file
+   - relaxNGValidateSource('...')—Validates against a relaxNG string

The preceding code uses relaxNGValidate() to validate a (well-formed) XML file against a nonmatching relaxNG file. If you change <element name="person"> to