
We can also work with XML values using a standard programming language. Library functions are available for most languages to allow an XML processor to be incorporated into a program. Two types are available. The first, usually known as a DOM processor, loads the complete Document Object Model into an internal program structure. From there, various functions can be used to navigate through the model to extract tags and attributes as individual items or lists within the program. Because the whole DOM is in memory, this is convenient and reasonably efficient, but there is going to be some upper limit on the size of the XML file that can be loaded.

The alternative is usually referred to as a SAX processor (Simple API for XML). This uses a different event-based strategy to process an XML file. As the XML document is read, each significant item (such as a start tag) is sent to the program where it can be stored for later use or processed immediately. The important distinction is that the entire document does not need to be stored in memory, and so there is no upper limit on document size. The disadvantage is that it is more difficult to carry out operations that require references back and forth between various parts of the model.

### SQL/XML

SQL:2003 introduced XML as a new built-in data type. XML data is strongly typed, as XML values are assumed to be tree-like data structures that are distinct from their representation in the form of a text string. The XML type can be used wherever other SQL types are allowed, such as in table columns, as parameters of a routine, as variables, and so on. Although relational data and XML data are both structured, there are some significant differences between them. [Table 16.3](#Ch016_831-873_B9780443237904000207.xhtml#t0020) (repeated from Table 16.1) identifies some key points.

[Table 16.3](#Ch016_831-873_B9780443237904000207.xhtml#B-t0020)

Some differences between relational and XML structured data.

| ![t16-03-9780443237904](images/B9780443237904000207/t16-03-9780443237904.jpg) |

| --- |

XML data can be stored in a database either in a text column (i.e., `char`, `varchar`, or `clob`) or in a column of data type `xml`. A textual representation might be preferred if it is important to retain the textual fidelity of a document (which may include text that has no relevance to the data structure) or if the XML is always entered and retrieved as a complete document. However, storing the data in an XML column allows efficient processing of the XML data in the database, rather than in a middle-tier application.

In addition to the XML data type, the SQL:2003 standard also introduced some related features, such as new XML operators, functions, and rules for mapping between SQL concepts and XML concepts. Most vendors broadly support these features or their equivalents, but the need to integrate the additional XML features into different preexisting frameworks has inevitably resulted in some differences in syntactic detail. The fact that XML support is an area of keen competition for vendors is also likely to produce a variety of nonstandard extensions. The picture is further complicated by the need for interoperability with other standards, such as XQuery. Fortunately, this competition is limited to the variety of operators, functions, and so on that are provided to integrate XML with SQL. The standards governing the structure of XML data are defined outside SQL, and so the XML values themselves are reasonably consistent from one database system to another.

In 2006, the part of the SQL standard dealing with XML (Part 14) was revised and extended to consolidate the features of SQL/XML, as it has come to be called. (The standard is sometimes referred to as SQL:2006, although this is a little misleading because only the XML part was revised in 2006.) Here, we will use SQL/XML:2006 to specifically distinguish the more recent version where necessary.

In SQL/XML:2006, the `xml` data type is based on the XQuery data model.^([^(17)](#fn17))

A sequence containing exactly one document node is termed *XML content*, with the type modifier `xml(content)`. A special type of content is where the document node contains exactly one element node (plus, possibly comment and processing instruction nodes), and this is termed an *XML document*, with the type modifier `xml(document)`.

A secondary modifier can be added for `xml(content)` and `xml(document)` to indicate whether the content or document can contain both typed and untyped elements (`any`), only untyped elements (`untyped`), or elements defined by a schema (`schema` name). If a schema is defined, the element and attribute nodes are guaranteed to be valid according to the schema. These distinctions are summarized in [Fig. 16.3](#Ch016_831-873_B9780443237904000207.xhtml#f0020). If the type `xml` is specified without a modifier, any default assumption about these more specialized subtypes is implementation-dependent.

![Fig. 16.3 XML data type modifiers.](images/B9780443237904000207/f16-03-9780443237904.jpg)

[Fig. 16.3](#Ch016_831-873_B9780443237904000207.xhtml#B-f0020) XML data type modifiers.

The SQL:2003 standard introduced the predicate `is document` to test whether an XML expression is a document. The basic syntax is:

```
xmlexpression is [ not ] document
```

Although the syntax of the predicate remained unchanged from SQL:2003, the meaning shifted somewhat because of the realignment of SQL/XML:2006 with the XQuery data model. Three more predicates were added: `is content`, `xmlexists`, and `is valid`. The `is content` predicate tests whether an XML expression is legitimate XML content, using the syntax:

```
xmlexpression is [ not ] content
```

To test whether an expression contains valid XML, the `xmlexists` predicate can be used. The syntax, simplified a little, is as follows:

```
xmlexists ( XQuery-expression  [ passing value-expression  [ as identifier ] [ { by ref | by value } ] ] [,...] )
```

If the XQuery evaluation is of a value that turns out to be null (perhaps passed as an argument from SQL), then the predicate result is unknown. For nonnull values, if the XQuery evaluation returns an empty sequence, the predicate’s value is false; otherwise, the result is true. The following example shows the use of `xmlexists` in a select statement to retrieve “id” values for customers in a given city, with the customer details being stored in a column of the `xml` type.

```
select c.custId from customer as cwhere xmlexists ( ‘ $d/*:customerinfo/*:addr [ *:city = “Salt Lake City” ] ’passing info as “d” )
```

The `is valid` predicate checks to see if an XML value is valid according to a given XML schema. The details of validity assessment are a little complex and are not covered here. The simplified syntax is:

```
xml-value-expression is [ not ] valid   [ identity-constraint-option ]   [ according to xmlschema { uri | registered-name } ]   [ valid-element-clause ]
```

The xml-value-expression is checked according to the schema identified by the choice of namespace. If none is specified, each element is validated according to the schema associated with its namespace. If specified, the schema can be identified either by URI or by its registered name. The optional identity-constraint-option and valid-element-clause parameters provide for a more detailed specification of exactly how schema checking should be done.

Several built-in XML operators were introduced in the SQL:2003 standard. One of the operators, `xmlroot`, could be used to modify the version and standalone properties of an XML expression, but this was removed in SQL/XML:2006 so we don’t cover it here.
