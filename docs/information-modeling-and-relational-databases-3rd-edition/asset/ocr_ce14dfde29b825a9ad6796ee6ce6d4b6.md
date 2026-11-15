# Using XQuery

One of the most important aspects introduced in SQL/XML:2006 was the ability to integrate XQuery into the established relational database framework–a key motivator in moving SQL/XML to the XQuery data model. One point of caution: if you have a background in SQL, you will need to remember that, unlike SQL, XQuery is case-sensitive, and so care is needed in specifying expressions. It’s also important to keep in mind that in SQL/XML, we will be operating on XML values and not their serialized representations. So, for example, we’re not trying to textually process “angle brackets”, although these may be useful in denoting structures for human readability.

Finally, we’ll look at some mechanisms provided in SQL/XML that help integrate XQuery into the relational framework. The most important of these is the xmlquery function, which allows an XQuery expression to be evaluated from within an SQL context. SQL alone cannot operate on parts of an XML document: the whole document is treated as a single value. With the xmlquery function, it’s possible to query inside an XML document so that XML data can participate in SQL queries and SQL processing can be applied to returned XML values (for instance, using order by to order the results). The basic syntax of xmlquery is as follows. The arguments are used in a similar way to the equivalents we have already seen in other functions.

```
xmlquery ( XQuery-expression
[ passing [ { by ref | by value } ] XML-query-argument [...] ]
[ returning { content | sequence } ]
[ { by ref | by value } ]
[ { null on empty | empty on empty } ] )
```

Another function, xmltable, provides a useful way to integrate XQuery results back into SQL. Normally, an XQuery expression would return a sequence, but by using xmltable, we can execute an XQuery expression and return values as a table instead. The returned table can contain columns of any SQL data type, including XML, although values inserted into xml columns in xmltable must be well-formed with a single root node. The basic syntax is:

```
xmltable ( [ xmlnamespaces ( namespace-declaration-item [...], ]
row-pattern [ passing [ { by ref | by value } ] XMLQuery-argument [...] ]
columns { { colname for ordinality |
colname datatype [ by ref | by value ] path column-pattern }[...] } )
```

The row-pattern defines an expression that produces a sequence of elements. Each element in this sequence will become a row in the resulting table. The columns clause lists the column definitions and the path expression used to find the column value within each element of the row-pattern. The for ordinality option creates a column with an automatic ordinal reference to the row, so the first row is 1, the second row 2, and so on. An example is shown here. This assumes that we have an xml value called movieXML, the contents of