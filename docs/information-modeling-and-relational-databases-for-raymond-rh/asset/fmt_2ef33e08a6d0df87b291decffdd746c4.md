
XML is a text format, and although it can be manipulated using text processing operations, it is more effective to use processing operations that are sensitive to the data structure being expressed. Database systems first started using XML as a text format, but recognition of its value led to its incorporation as a native data type in the SQL standard. Most database vendors have added features to store XML data, operate on XML data, and convert backward and forward between XML and relational table structures, sometimes including proprietary extensions that are not part of the official SQL standard.

JSON is a slightly younger language than XML. It was originally developed as a relatively lightweight communication language between web servers and browsers, using standard browser facilities instead of auxiliary plug-ins. This made JavaScript an obvious starting point for the definition of a markup language, and so JavaScript objects became the basis for the notation.

A major factor in the popularity of JSON is its simplicity and ease of processing compared to XML. It is a more compact format that reduces the bandwidth required for the transmission of data; this is an important factor given the reasons for its creation. It is also a better fit with web-related technology in general, relevant, for example, in application development. Against that, it is somewhat less expressive than XML. It has no support for namespaces, and it is unsuitable in applications where precise definition of data types is important. However, its adoption as the primary structuring principle in document databases and its incorporation into SQL as a native data type show that it is sufficiently robust to meet the demands of a wide range of real-world scenarios.

XML and JSON will continue to coexist for the foreseeable future because one is not a direct replacement for the other. It's tempting to caricature XML as heavyweight and JSON as lightweight solutions to data structuring outside of a data store, but this blurs some of the important features of each. It's certainly true that there is a large middle ground where either could be employed effectively, and any choice between them would be made on factors other than their data structuring capabilities.

### Chapter Notes

The SQL standard has been adopted by the International Standards Organization (ISO) as ISO/IEC 9075. Copies can be ordered from ISO or via national standards organizations such as ANSI. Because of its size (several thousand pages in total), the standard is split into several parts. Part 2 (Foundations) and Part 14 (SQL/XML) are the most relevant to this chapter.

The relevant XML standards are being progressed through the W3C. Full details, including the current versions of the standards themselves, can be found at [www.w3c.org](http://www.w3c.org). The standards documents are not particularly easy to read, but a large amount of more readable tutorial information is available. XQuery especially is still relatively unfamiliar to many database practitioners, but it seems likely to become progressively more important in utilizing heterogeneous data. Useful introductions can be found in [Walmsley (2015)](#Ch016_831-873_B9780443237904000207.xhtml#bb1310) and [Melton and Buxton (2006)](#Ch016_831-873_B9780443237904000207.xhtml#bb0985).

JSON arrived as a data format later than XML, but it is now established as an essential component in data management. A short introduction to JSON can be found in [Basset (2015)](#Ch016_831-873_B9780443237904000207.xhtml#bb0075). Because of its origins in JavaScript, its standardization falls under ECMA, the same body responsible for the specification of the JavaScript language (now sometimes referred to as ECMAScript). A comprehensive description of JavaScript is given in [Flanagan (2020)](#Ch016_831-873_B9780443237904000207.xhtml#bb0470). Copies of standards and further details can be found at [www.ecma-international.org](http://www.ecma-international.org). JavaScript and JSON are covered in standards ECMA-262 and ECMA-404, respectively. The latter has also been adopted as an ISO standard (ISO/IEC 21778). JSON Schema is still a work in progress, but the latest status can be found at [www.json-schema.org](http://www.json-schema.org). For further details on JSONPath, see [Gössner and Bormann (2021)](#Ch016_831-873_B9780443237904000207.xhtml#bb0490).

XML and JSON functionality is now included in major relational databases but because of variations between different implementations, the vendor's documentation is often the most useful resource. Most commercial systems provide online help that can be searched in various ways.

## References

*   [Basset L.](#Ch016_831-873_B9780443237904000207.xhtml#B-bb0075) *Introduction to JavaScript Object Notation.* O'Reilly Media; 2015.

*   [Crockford D.](#Ch016_831-873_B9780443237904000207.xhtml#B-bb0260) *The Application/JSON Media Type for JavaScript Object Notation (JSON).* Available at: [https://www.ietf.org/rfc/rfc4627.txt](https://www.ietf.org/rfc/rfc4627.txt). 2006.

*   [Flanagan D.](#Ch016_831-873_B9780443237904000207.xhtml#B-bb0470) *JavaScript—The Definitive Guide.* seventh ed. O'Reilly Media; 2020.

*   [Gössner S., Bormann C.](#Ch016_831-873_B9780443237904000207.xhtml#B-bb0490) *JSONPath—XPath for JSON.* Available at: [www.ietf.org/archive/id/draft-goessner-dispatch-jsonpath-00.html](http://www.ietf.org/archive/id/draft-goessner-dispatch-jsonpath-00.html). 2021.

*   [Melton J., Buxton S.](#Ch016_831-873_B9780443237904000207.xhtml#B-bb0985) *Querying XML: XQuery, XPath, and SQL/XML in Context.* Morgan Kaufmann; 2006.

*   [Walmsley P.](#Ch016_831-873_B9780443237904000207.xhtml#B-bb1310) *XQuery.* second ed. O'Reilly Media, Inc; 2015.

---

# 17 NoSQL and Other Nonrelational Databases

## Abstract

This chapter reviews alternatives to the dominant relational database paradigm. The motivations for such systems are discussed and the major database types are described individually. Methods for mapping from an information model to each of these database types are introduced. Some further ideas on future evolution are considered, including the potential impact of artificial intelligence.

### Keywords

NoSQL; Key-value database; Document database; Column-oriented database; Graph database; Logic database; AI

### Chapter Outline

*   17.1 **The Growth of the NoSQL Movement**
*   17.2 **Key-Value Stores**
*   17.3 **Column-Oriented Databases**
*   17.4 **Document Databases**
*   17.5 **Graph Databases**
*   17.6 **Other Nonrelational Databases**
*   17.7 **Summary**

## 17.1 The Growth of the NoSQL Movement

Following the publication of E.F. Codd's ground-breaking relational paper in 1970 ([Codd, 1970](#Ch017_875-933_B9780443237904000050.xhtml#bb0230)), it was not until the 1980s that commercial relational database systems became widely available. Since that time, they have become the dominant data storage model. Other data resources are used at smaller scales, such as spreadsheets, text files, and so on, but for large-scale data, relational systems have reigned supreme.

The NoSQL movement started to emerge in the 2010s in response to perceived shortcomings in the relational approach ([Leavitt, 2010](#Ch017_875-933_B9780443237904000050.xhtml#bb0925)). It's worth noting straight away that "NoSQL" is not a particularly good choice of name. The crucial point is not really an issue with the structured query language (SQL). In fact, some NoSQL vendors try very hard to provide languages that are as similar as possible to SQL. Instead, NoSQL approaches rely on data models that are nonrelational to provide their distinctive features. There are some suggestions that "NoSQL" should be interpreted as "Not Only SQL", but this would include every kind of database, rendering it completely meaningless.
