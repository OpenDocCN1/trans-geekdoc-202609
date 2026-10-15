# Using DOM in PHP 4 to Read XML

Unfortunately, if you use PHP 4, be aware that the DOM access changed between versions and is not that stable on some systems. Windows users have to use extension=php_domxml.dll in php.ini and may have to copy iconv.dll in the Windows system32 folder. Other systems have to reconfigure PHP using --with-dom=/path/to/libxml. Then domxml_open_file() opens a file—using the absolute path! A more portable way is to use domxml_open_mem that reads in a string. The return value of both functions offers access to the two methods get_elements_by_tagname() and get_element_by_id() that return all nodes with a certain tag name or a specific element identified by its ID. Then each node exposes some methods such as the following:

+   - `first_child()`—First child node
+   - `last_child()`—Last child node
+   - `next_sibling()`—Next node
+   - `previous_sibling()`—Previous node
+   - `node_value()`—Value of the node

The preceding code uses DOM to access all quotes in the XML file and outputs them.

# Using DOM in PHP 5
to Read XML

If you use PHP 5, the main advantage is that libxml2 is used, a much better library than libxml. It is bundled with PHP, so no installation is required. However, the API has changed drastically. First, you instantiate a DOMDocument object, then you load() a file or loadXML() a string. All method names have changed to studly