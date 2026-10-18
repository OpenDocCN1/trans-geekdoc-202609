The design goals for XML (Bray et al. 2006) were that it should:

+   - Be simple to use over the Internet.
+   - Support a wide variety of applications.
+   - Be compatible with SGML.
+   - Make it easy to write programs that process XML documents.
+   - Have the minimum possible number of optional features (ideally zero).
+   - Be human-legible and reasonably clear.
+   - Have its design prepared quickly.
+   - Have a formal and concise design.
+   - Make documents easy to create.
+   - Not consider terseness important.

Among other many other uses, XML can be used as an alternative to HTML in creating web pages, but with a separation of content and presentation. Rather than combining, as HTML does, content, structure and presentation into a single language, XML is purely a data description (mark-up) language that manages content. It provides a definition of data structures and syntax, but not semantics (it does not specify what the data actually means). It performs a number of roles that go beyond the capabilities of HTML, for example the exchange of data between different applications (e.g. web services). Using XML as a communication mechanism between different systems avoids having to use many different file formats. Various industries have standardized on special XML-based languages, enabling them to exchange data using a common format. Examples of this type of format include the B2B (business to business) XML document specifications defined by the RosettaNet organisation, principally for the electronic component industry and HL7 (Health Level 7) for clinical and administrative data in health care. XML can be (and has been) used to represent a huge range of different types of information. The following example is a fragment of a much larger document from the universal protein knowledgebase (UniProt 2005), that describes the DNA of tuberculosis. Here, XML is being used to represent non-textual data.

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
ANRAVKPTGSAAIGLSMAGSSAMILAAYHPQQFIYAGSL SALLDPSQGMG
PSLIGLAM... 
CGNGTPNELGGANIPAEFLENFV RSSNLKFQDAYNAAGGHNAVFNFPPNG
THSWEYWGAQLNAMKGDLQSSLGAG
</sequence>
</entry>
<copyright>
Copyrighted by the UniProt Consortium, see http://www.uniprot.org/terms
```