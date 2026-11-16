# # 21 PHP XML

At the simplest level XML is structured text. We are surrounded by structured text. This book is structured text, as it contains chapters, sub-headings, and paragraphs. A letter is structured text, as it typically contains a date, salutation, and paragraphs. Each section of a book or letter is defined by the structure of that document. To make the structure visible, each of these sections can be noted with markup tags (similar to HTML). The tags used to mark up the document are the basics of XML. XML is a way of writing the structured text in a common human and machine-readable format.

XML can be used to describe any kind of structured text, including other markup languages. There are over a dozen markup languages based on XML. They are used to describe everything from graphics to mathematical equations. To try to keep this chapter under control, we are going to look at only the parts of XML that are implemented in PHP and are used to read and write an XML file. Specifically we will be looking at a basic XML file, a way of specifying parts of an XML file (XPath), and a simplified XML format called SML.

To learn more about the different XML standards, take a look at the World Wide Web Consortium (W3C). The W3C is the organization that manages Internet standards like XML. They are responsible for issuing and maintaining the XML family of specifications and recommendations. For more information visit their web site: http://www.w3.org/.

In this chapter we will look at:

+   - The basics of XML, SML, and XPath
+   - XML as a datastore and programmatic interaction
+   - The PHP APIs (SAX, DOM, and PRAX) that allow interaction with an XML document