```
// Also returns a DOMNodeList with only the body node
$list = $xpath->query('/​/body');
?>
```

+   * In the first two examples, note that the root element (html) is referenced in the expression even though it is assumed to be the context node (since no other node is specified as the second parameter in either query call).

+   * A **single forward slash** / indicates a parent-child relationship. */html/body addresses all body nodes that are children the document’s root html element (which in this case only amounts to a single result).

+   * A **double forward slash** // indicates an ancestor-descendant relationship. //body addresses all body nodes that are descendants of the context node (which again only amounts to a single result).

The single and double forward slash operators can be used multiple times and in combination with each other as shown below.

```
<?php
// Returns all ul nodes that are descendants of the body node
$list = $xpath->query('//body/ul');

// Returns all li nodes that are children of the ul nodes
$list = $xpath->query('/​/body/ul/li');
?>
```

# Namespaces

If you attempt to address nodes by their element name and receive no results when it appears you should, it’s possible that the document is namespacing nodes. The easiest way to get around this is to replace the element name with a condition.
For example, if you are using the expression ul, an equivalent expression that disregards the namespace would be *[name()="ul"] where * is a wildcard for all nodes and the name function compares the node name against a given value.