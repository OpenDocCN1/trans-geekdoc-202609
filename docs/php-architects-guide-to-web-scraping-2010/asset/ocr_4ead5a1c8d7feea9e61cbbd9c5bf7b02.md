Note when reading this table that CSS selectors begin set indices at 0 whereas XPath begins them at 1.

# # Content Filters

Where basic filters are based mainly on the type of node or its position in the result set, content filters are based on node value or surrounding hierarchical structure.

+   - `a:contains("About Us");` selects all a nodes where the node value contains the substring “About Us”.
- `img:empty` selects all img nodes that contain no child nodes (including text nodes).
- `li:has(a:contains("About Us"))` selects all li nodes that contain an a node with the substring “About Us” in its node value.
- `li:parent` selects all li nodes that contain child nodes (including text nodes).

| **Selector** | **CSS** | **XPath** |
|---|---|---|
| nodes containing text | `a:contains("About Us")` | `//a[contains(text(), "About Us")]` |
| nodes without children | `img:empty` | `//img[not(node())]` |
| nodes containing a selector match | `li:has(a:contains("About Us"))` | `//li[//a[contains(text(), "About Us")]]` |
| nodes with children | `li:parent` | `//li[node()]` |

# # Attribute Filters

Filters up to this point have been specific to element nodes, but they also exist for attribute nodes. Attribute filters are surrounded by square brackets in both CSS and XPath, but differ in that CSS uses mostly operators for conditions while XPath uses mostly functions. Unlike other filters described in this chapter, support for attribute filters is fairly universal between different libraries.