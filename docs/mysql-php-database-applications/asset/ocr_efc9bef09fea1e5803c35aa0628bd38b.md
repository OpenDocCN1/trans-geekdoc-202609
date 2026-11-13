![](bbox=[0.142, 0.085, 0.63, 0.485])

Figure 15–1: Netsloth21 home page with mock sample stories

# # Code Overview

The essential purpose of our application is to reach out across the Internet, grab an XML document, pick it apart, and reformat the chopped-up pieces into a form that’s acceptable for use in our Netsloth content-management suite. To accomplish these goals, this software will need to be able to look at an XML document, distinguish the tags from the tagged text (also known as character data), and separate them if necessary. The piece of code that does this is generically called an _XML parser_. XML parsers can be designed in a couple of different ways.

# # An introduction to parsers

If you’re going to work with XML, you need a parser. Parsers come in two different general varieties:

+   • Tree-style parsers (also called Document Object Model (DOM) parsers), which read through entire XML documents at once and convert the imported data into hierarchically organized objects representing whole documents at once. Microsoft’s MSXML parser is of this kind.