The **xmlelement** function is used to create an XML element from a given set of parameters. Recall that an XML element has the basic form:

```
<tagname optionalAttributes> optionalElementContent </tagname>
```

So, for example, an element representing a customer might look something like:

```
<cust custid = "1234"> Widgets Inc </cust>
```

If required, the tagname can be further qualified by prefixing it with a namespace, in which case the namespace URI must also be specified. The **xmlelement** function constructs an individual XML element from the parameters provided and returns it as an **xml** value. The basic syntax for character strings is shown here. There is also a variant for binary strings that we won't consider.

The embedded **xmlnamespaces** and **xmlattributes** functions are optionally used in the context of a given element to add any required namespace declarations or attributes to the element. The element content is defined by a list of expressions that is optional, so it's possible to create an empty element. Also optional is the **returning** clause, which we've already seen.

```
xmlelement ( name xmlelementname
 [ , xmlnamespaces (namespace-declaration-item [...] ) ]
 [ , xmlattributes ( attributevalue [as attributename ] [,...] )
 [ , elementcontent [...
 [ option { null on null | empty on null | absent on null | nil on null | nil on no content } ] ]
 [ returning { content | sequence } ] )
```

The content option requires a little more explanation. In SQL, a missing optional value is explicitly marked as **null**. This is not a value recognized in XML, although **null** is legitimate for the SQL **xml** data type. Depending on the desired result, a missing value could be indicated in XML by simply omitting the relevant element or by including the element begin/end tags with no contained value. If an explicit indicator equivalent to **null** is required, a further option is the “nil” mechanism specified in the “XML Schema For Instances” namespace. The namespace is typically introduced with a declaration such as:

```
xmlns:xsi = "http://www.w3.org/2001/XMLSchema-instance"
```

The xsi prefix is used by convention, but some other prefix could be substituted. Once this is defined, the **nil** attribute defined in XMLSchema-instance can be set to True.

```
<myElement xsi:nil = "true"></myElement>
```

An element attributed in this way may not have any element content but may still carry other attributes. The SQL:2003 standard acknowledged the xsi:nil option, but did not prescribe how this should be specified in conjunction with operations such as **xmlelement**. SQL/XML:2006 provided close control over these choices, as summarized in Table 16.4.