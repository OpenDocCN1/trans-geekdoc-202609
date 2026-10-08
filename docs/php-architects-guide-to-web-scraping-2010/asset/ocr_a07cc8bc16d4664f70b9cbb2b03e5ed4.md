```
// Buffer DOM errors rather than emitting them as warnings
$oldSetting = libxml_use_internal_errors(true);

// Instantiate a container for the document
$doc = new DOMDocument;

// Load markup already contained within a string
$doc->loadHTML($htmlString);

// Load markup saved to an external file
$doc->loadHTMLFile($htmlFilePath);

// Get all errors if needed
$errors = libxml_get_errors();

// Get only the last error
$error = libxml_get_last_error();

// Clear any existing errors from previous operations
libxml_clear_errors();

// Revert error buffering to its previous setting
libxml_use_internal_errors($oldSetting);
?>
```

# Tree Terminology

Once a document is loaded, the next natural step is to extract desired data from it. However, doing so requires a bit more knowledge about how the DOM is structured. Recall the earlier mention of tree parsers. If you have any computer science background, you will be glad to know that the term “tree” in the context of tree parsers does in fact refer to the data structure by the same name. If not, here is a brief rundown of related concepts.

A **tree** is a hierarchical structure (think family tree) composed of **nodes**, which exist in the DOM extension as the `DOMNode` class. Nodes are to trees what elements are to arrays: just items that exist within the data structure.

Each individual node can have zero or more **child nodes** that are collectively represented by a `childNodes` property in the `DOMNode` class. `childNodes` is an instance of the class `DOMNodeList`, which is exactly what it sounds like. Other related proper-