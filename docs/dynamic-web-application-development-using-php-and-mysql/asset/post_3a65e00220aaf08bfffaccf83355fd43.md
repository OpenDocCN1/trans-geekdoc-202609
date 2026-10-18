
the browser. The DOM is a standard interface to the content, structure and style of a document, enabling applications to access and update that document. The programming language that is often used to interact with the DOM in a web browser is JavaScript (for example, in Ajax applications) and JavaScript errors are common in web applications. The problem is that the DOM represents the structure of the HTML document within the browser and JavaScript programs often need to navigate through the DOM to process various parts of the page. If the DOM is not well constructed due to poorly formed HTML, the JavaScript may be unable to find what it is looking for.

## Why HTML alone is not enough

The problem of poorly formed documents can be resolved by validating an HTML page against a DTD. However there is a further important issue with HTML, which is that HTML cannot be used to represent anything other than web page mark-up. This means that the content that we represent in web pages has no structure applied to it other than the specific structure of an individual web page. However the data that underlies a web application may need to be used in different pages, and in different ways, across many parts of the application, or even between different applications. Ideally we would like to be able to have a separate method of representing the underlying structure of our content regardless of the ways that it might be organized and presented in web pages.

In summary, HTML has many strengths as a simple, flexible language for creating web pages that combine content, structure and presentation. However, it does not have enough intrinsic structural and syntactic rules to enable applications other than browsers (which are only concerned with presentation) to process them effectively. Further, the syntax of HTML is fixed to a set of tags that are intended only for the rendering of web pages. It cannot be used to represent more general types of content. If we want to use mark-up to present content in a more rigorous and useful way, then we need some language other than HTML. That language is the *eXtensible Markup Language* (XML).

## 5.2 Semi-structured data

In this section, we look at the relationship between the eXtensible Markup Language (XML) and the concept of semi-structured data. We see how semi-structured data can be represented in an XML document using both elements and attributes, and explain how to choose between elements or attributes when structuring XML documents.

Semi-structured data contains no type information, is self-describing, and can have variations in its structure. Semi-structured data is self-describing because it contains labels; each piece of data contains some metadata that tells us about that data element. This means that a document of semi-structured data can support interoperability between systems, because when it is serialized (sent as a stream of data) between different applications it carries its own labels with it, helping the receiving system to process its content. This is the basis upon which XML web services work.

Perhaps the best way to explain semi-structured data is to start with an example of some structured data:

```
02 03 1959 15 08 1977 08 04 1994
```

If you look at this data you can see that it follows a repeating and consistent structure. There are three groups of numbers, and in each group there are two numbers of two digits followed by a third number of four digits. The different numbers are separated by spaces. The important feature of structured data is that it follows a consistent and predictable format. In this case, you can probably see that the data represents a series of dates, though there is nothing in the data to tell you that, other than the knowledge you already have about dates (that they have a day number, a month number and, particularly since the 'millennium bug' panic, a four-digit year.) If you look a bit more closely you might assume that the day number comes before the month number in each group, because '15' could not be a month number. However with just the structured data to go on this is just supposition. The data may not represent dates at all. Maybe it is a single part number from a catalogue, or some sports results. Without a bit of metadata to help us we do not really know.

Assuming that the data is, in fact, a series of dates, any application that processes this data needs to know that each data item is separated from its neighbours by spaces and that it occurs in groups of three, each group representing the day, month and year of the date in that order. That information is not carried with the data itself, so we have to 'just know' it. In contrast, semi-structured data is human-readable and self-describing. This example shows the same data in semi-structured format (this is not a 'real' syntax, just one used as an example.)

```
[dates
  [date [day: 03] [month: 02] [year: 1959] ]
  [date [day: 15] [month: 08] [year: 1977] ]
  [date [day: 08] [month: 04] [year: 1994] ]
]
```

In this version, the data is both human-readable and self-describing because the data describes itself using recognisable names. Thanks to the labels, we can clearly see that the data represents a series of dates, and that each date consists of the day, the month and the year.

### Variations in structure

One of the key features of semi-structured data is that it allows for variations in the structure of the data so that the order and number of elements can be varied. In this version of the data, we add a 'day-name' element to the first date but not to the other dates.

```
[dates
  [date [day-name: Tuesday] [day: 03] [month: 02] [year: 1959] ]
  [date [day: 15] [month: 08] [year: 1977] ]
  [date [day: 08] [month: 04] [year: 1994] ]
]
```

This type of structure would be very difficult, if not impossible, to process without the metadata provided by the labels. An application would have to check for the type of data at the beginning of every date to see if it was text (the day name) or a number (the day). Imagine, however, if we made the structure more complex, with many optional parts to the data. Eventually, it would be impossible to process this information without identifying labels. The point about semi-structured data is that the self-descriptiveness

The design goals for XML (Bray et al. 2006) were that it should:

- Be simple to use over the Internet.
- Support a wide variety of applications.
- Be compatible with SGML.
- Make it easy to write programs that process XML documents.
- Have the minimum possible number of optional features (ideally zero).
- Be human-legible and reasonably clear.
- Have its design prepared quickly.
- Have a formal and concise design.
- Make documents easy to create.
- Not consider terseness important.

Among many other uses, XML can be used as an alternative to HTML in creating web pages, but with a separation of content and presentation. Rather than combining, as HTML does, content, structure and presentation into a single language, XML is purely a data description (mark-up) language that manages content. It provides a definition of data structures and syntax, but not semantics (it does not specify what the data actually means). It performs a number of roles that go beyond the capabilities of HTML, for example the exchange of data between different applications (e.g. web services). Using XML as a communication mechanism between different systems avoids having to use many different file formats. Various industries have standardized on special XML-based languages, enabling them to exchange data using a common format. Examples of this type of format include the B2B (business to business) XML document specifications defined by the RosettaNet organisation, principally for the electronic component industry and HL7 (Health Level 7) for clinical and administrative data in health care. XML can be (and has been) used to represent a huge range of different types of information. The following example is a fragment of a much larger document from the universal protein knowledgebase (UniProt 2005), that describes the DNA of tuberculosis. Here, XML is being used to represent non-textual data.

```
<?xml version="1.0" encoding="UTF-8"?>
<organism key="2">
    <name type="scientific">Mycobacterium tuberculosis</name>
    <dbReference type="NCBI Taxonomy" id="1773" key="3"/>
</organism>
<sequence length="325" mass="34581" checksum="B993B5442FD5557D" modified="1993-07-01" version="1">
MTDVSRKI...
LQVPSPSMGRDIKVQFQSGGNNSPAVYLLDGLRAQDDYNGWDINTPAFEW
YYQSG...
ANRAVKPTGSAAIGLSMAGSSAMILAAYHPQQFIYAGSLSALLDPSQGMG
PSLIGLAM...
CGNGTPNELGGANIPAEFLENFVRSSNLKFQDAYNAAGGHNAVFNFPPNG
THSWEYWGAQLNAMKGDLQSSLGAG
</sequence>
</entry>
<copyright>
Copyrighted by the UniProt Consortium, see http://www.uniprot.org/terms
```
