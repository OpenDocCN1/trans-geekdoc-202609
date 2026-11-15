Several built-in XML operators were introduced in the SQL:2003 standard. One of the operators, xmlroot, could be used to modify the version and standalone properties of an XML expression, but this was removed in SQL/XML:2006 so we don't cover it here.

The first two SQL/XML operations we'll look at, xmlparse and xmlserialize, convert back and forth between structured and string representations of XML. The xmlparse operation takes an SQL string expression and produces the equivalent XML structure. A parameter defines whether the string expression is expected to represent a document or content. The basic syntax has remained consistent since SQL:2003.

```
xmlparse ( { document | content } stringexpression
[ { preserve | strip } whitespace ] )
```

The result of the operation could be assigned to a variable of type xml or stored in an xml column. The precise way in which whitespace is handled by xmlparse, which is subject to detailed rules that are not considered here.

The xmlserialize operation performs the inverse of xmlparse, producing a string version of a given XML expression. The SQL standard does not mandate the precise format of the resulting string, but does require that a subsequent xmlparse of a string produced by xmlserialize should reproduce the original XML expression. In other words, given an XML document called myXmlData, the following construct:

```
xmlparse ( document ( xmlserialize ( document myXmlData as varchar ( max ) ) ) )
```

should produce a result equal to myXmlData. The original SQL:2003 syntax of xmlserialize was extended in SQL/XML:2006.

```
xmlserialize ( { document | content } xmlexpression as SQLdatatype
[ version string ]
[ including xmldeclaration | excluding xmldeclaration ] )
```

The SQL datatype for the result could be any SQL string type (such as char, varchar), but serialized XML tends to be lengthy, so a character large object (clob) type is likely to be a common choice. Optionally, including xmldeclaration prepends the XML declaration “<?xml version="1.0" encoding="UTF-8"?>” to the result; the default is excluding xmldeclaration. The XML version can also be separately specified; at present, this will be limited to “1.0”.

The xmlconcat operation introduced in SQL:2003 was retained in SQL/XML:2006. It simply concatenates a list of XML expressions, producing a new XML expression.

```
xmlconcat ( xmlexpression [, ...] [ returning { content | sequence } ] )
```

The optional returning clause was added in SQL/XML:2006. If this is omitted, it is implementation-defined whether returning content or sequence is implicit.

The SQL:2003 standard defined several “publishing” functions to generate XML expressions from SQL expressions. These were extended in SQL/XML:2006, and new functions were added. Here, we cover only the SQL/XML:2006 definitions of the functions.