```
// Returns the first li child node of each ul node
$list = $xpath->query('//ul/li[1]');

// Returns all ul nodes containing an li node with the value "foo"bar"
$list = $xpath->query('//ul[li = "foo"bar]');
?>
```

+   Square brackets are used to delimit a conditional expression.

+   Element and attribute nodes are denoted the same way within a condition as they are outside of one. That is, elements are simply referred to by element name and attribute names are prefixed with @.

+   The = operator is used for equality comparisons. The converse, the != operator, checks for inequality. Other fairly standard comparison operators are also supported, including <, <=, >, and >=.

+   A condition comprised only of a single number is actually short for position() = # where # is the number used. position is a function that returns the position of each individual node within the current context.

# Resources

Only a fraction of what XPath offers has been covered here, mainly basic concepts and areas that are most likely to be applicable when using XPath to extract data from retrieved markup documents. Other functions and operators and more advanced concepts are detailed further in the resources cited at the end of the chapter. Review of those resources is highly recommended for more extensive and complex data extraction applications.

+   DOM documentation in the PHP manual: http://php.net/dom

+   An excellent overview of XML and XPath:
http://schlitt.info/opensource/blog/0704_xpath.html

+   More information on XML: http://en.wikibooks.org/wiki/XML:_Managing_Data_Exchange