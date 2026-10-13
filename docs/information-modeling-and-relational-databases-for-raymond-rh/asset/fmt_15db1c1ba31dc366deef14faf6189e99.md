
# SQL/XML Operations: xmlparse, xmlserialize, xmlconcat, and Publishing Functions

## xmlparse and xmlserialize

The first two SQL/XML operations we'll look at, `xmlparse` and `xmlserialize`, convert back and forth between *structured* and *string* representations of XML.

The `xmlparse` operation takes an SQL string expression and produces the equivalent XML structure. A parameter defines whether the string expression is expected to represent a document or content. The basic syntax has remained consistent since SQL:2003.

```
xmlparse ( { document | content } stringexpression [ { preserve | strip } whitespace ] )
```

The result of the operation could be assigned to a variable of type `xml` or stored in an `xml` column. The precise way in which whitespace is handled by `xmlparse` is subject to detailed rules that are not considered here.

The `xmlserialize` operation performs the inverse of `xmlparse`, producing a string version of a given XML expression. The SQL standard does not mandate the precise format of the resulting string, but does require that a subsequent `xmlparse` of a string produced by `xmlserialize` should reproduce the original XML expression. In other words, given an XML document called `myXmlData`, the following construct:

```
xmlparse ( document ( xmlserialize ( document myXmlData as varchar ( max ) ) ) )
```

should produce a result equal to `myXmlData`. The original SQL:2003 syntax of `xmlserialize` was extended in SQL/XML:2006.

```
xmlserialize ( { document | content } xmlexpression as SQLdatatype   [ version string ]   [ including xmldeclaration | excluding xmldeclaration ] )
```

The SQL datatype for the result could be any SQL string type (such as `char`, `varchar`), but serialized XML tends to be lengthy, so a character large object (`clob`) type is likely to be a common choice. Optionally, `including xmldeclaration` prepends the XML declaration `<?xml version="1.0" encoding="UTF-8"?>` to the result; the default is `excluding xmldeclaration`. The XML version can also be separately specified; at present, this will be limited to "1.0".

## xmlconcat

The `xmlconcat` operation introduced in SQL:2003 was retained in SQL:2006. It simply concatenates a list of XML expressions, producing a new XML expression.

```
xmlconcat ( xmlexpression [, …]  [ returning { content | sequence } ] )
```

The optional `returning` clause was added in SQL/XML:2006. If this is omitted, it is implementation-defined whether returning content or sequence is implicit.

## Publishing Functions

The SQL:2003 standard defined several "publishing" functions to generate XML expressions from SQL expressions. These were extended in SQL/XML:2006, and new functions were added. Here, we cover only the SQL/XML:2006 definitions of the functions.

### xmlelement

The `xmlelement` function is used to create an XML element from a given set of parameters. Recall that an XML element has the basic form:

```
<tagname optionalAttributes>  optionalElementContent </tagname>
```

So, for example, an element representing a customer might look something like:

```
<cust custid = "1234"> Widgets Inc </cust>
```

If required, the tagname can be further qualified by prefixing it with a namespace, in which case the namespace URI must also be specified. The `xmlelement` function constructs an individual XML element from the parameters provided and returns it as an `xml` value. The basic syntax for character strings is shown here. There is also a variant for binary strings that we won't consider.

The embedded `xmlnamespaces` and `xmlattributes` functions are optionally used in the context of a given element to add any required namespace declarations or attributes to the element. The element content is defined by a list of expressions that is optional, so it's possible to create an empty element. Also optional is the `returning` clause, which we've already seen.

```
xmlelement ( name xmlelementname   [ , xmlnamespaces (namespace-declaration-item [,…] ) ]   [ , xmlattributes ( attributevalue [as attributename ] [,…] )  [ , elementcontent [,…]  [ option { null on null | empty on null | absent on null | nil on null | nil on no content } ] ]  [ returning { content | sequence } ] )
```

The content option requires a little more explanation. In SQL, a missing optional value is explicitly marked as `null`. This is not a value recognized in XML, although `null` is legitimate for the SQL `xml` data type. Depending on the desired result, a missing value could be indicated in XML by simply omitting the relevant element or by including the element begin/end tags with no contained value. If an explicit indicator equivalent to `null` is required, a further option is the "nil" mechanism specified in the "XML Schema For Instances" namespace. The namespace is typically introduced with a declaration such as:

```
xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
```

The `xsi` prefix is used by convention, but some other prefix could be substituted. Once this is defined, the `nil` attribute defined in XMLSchema-instance can be set to True.

```
<myElement xsi:nil = "true"></myElement>
```

An element attributed in this way may not have any element content but may still carry other attributes. The SQL:2003 standard acknowledged the `xsi:nil` option, but did not prescribe how this should be specified in conjunction with operations such as `xmlelement`. SQL/XML:2006 provided close control over these choices, as summarized in Table 16.4.

**Table 16.4: Options for handling null and nil.**

| ![t16-04-9780443237904](images/B9780443237904000207/t16-04-9780443237904.jpg) |
| --- |

As a simple example of the use of `xmlelement`, consider a Customers table that is purely relational (it contains no XML). We could produce a result table containing a mixture of relational data and XML representing selected customer information in the following way:

```
select c.id, xmlelement( name "cust", xmlattributes (c.id as "custid"), custName) as Xcust from Customers as c where custid = 1234
```

which would produce a result such as:

| ![u16-02-9780443237904](images/B9780443237904000207/u16-02-9780443237904.jpg) |
| --- |

where the data contained in the *Xcust* column is of type `xml`. Calls to `xmlelement` can be nested so that elements can be created within elements, producing the characteristic hierarchical structure of XML.

### xmlforest

The `xmlforest` function is a convenient way of applying `xmlconcat` to a sequence of `xmlelement` results: it produces a sequence of elements from a list of expressions. The elements can be named explicitly or implicitly. As with `xmlelement`, calls to `xmlforest` can also be nested. The basic syntax is as follows:

```
xmlforest ( [ xmlnamespaces (namespace-declaration-item , ), ]elementvalue [ as elementname ] [,…] [ option { null on null | empty on null | absent on null | nil on null | nil on no content } ] ] [ returning { content | sequence } ] )
```

The parameters are used in the same way as `xmlelement`. For example,

```
select o.orderId, xmlelement ( name "order",  xmlforest ( o.custName as "customer", o.date ) ) as Xorder from Orders as o where orderid > 9800
```

would produce a result such as:

| ![u16-03-9780443237904](images/B9780443237904000207/u16-03-9780443237904.jpg) |
| --- |

If preservation of the case in SQL names is important, they should be aliased as delimited identifiers. Regular identifiers are likely to be mapped to all uppercase in some implementations. For example, the *date* element in the example just given could appear as `<DATE> … </DATE>` instead of `<date> … </date>`.

An equivalent result table could be produced in SQL Server as follows:

```
select o.orderId, (select o.custName 'customer', o.date 'date' from orders as o for xml path ('order'), type) as Xorder from orders as o where orderid > 9800
```
