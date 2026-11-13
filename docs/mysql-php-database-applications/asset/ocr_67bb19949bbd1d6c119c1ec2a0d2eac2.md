# Chapter 15

# XML Parsing

# IN THIS CHAPTER

+   - Learning how to work with XML documents
+   - Examining an XML document retrieved from a URL

What HTML is to web pages, the eXtensible Markup Language, or XML, is to data. Whereas HTML is about presenting your information to the world — handling typefaces, sizes, colors, layout, and so on — XML concerns itself purely with structuring and identifying that information. Given the number of new and different Web platforms that seem to pop up each week — desktop computers, laptops, cell phones, televisions, wristwatches, car stereos — this separation of content from presentation is the great holy goal of Web programmers. Both languages are wildly successful because at heart they’re both very simple, yet allow for a huge range of applications. They even look alike — which they should, considering they’re both based on the Standard Generalized Markup Language (SGML).

In an XML document containing meteorological-observation data, for example, distinct tags can identify certain numbers as wind-velocity values and other numbers as wind-direction values. The question of how to represent these values visually — if they are to be displayed visually at all, rather than just read into a database or other processing environment — is a separate issue.

The other great thing about XML is that it’s an excellent format for transmitting information not just data, but the kinds of queries and responses you might normally associate with a regular programming language (like PHP itself). This is because it’s lightweight — it’s just ASCII (or Unicode), after all — and transparent. You can look at an XML document for the first time and stand a good chance of understanding it right away. Yet it’s also suitable for interpretation by machines, which are notoriously dim when it comes to understanding.

In this chapter we’ll explore XML and the capabilities of PHP when it comes to processing it. We’ll read a document in from a URL and reformat its contents for use in Netsloth, our content-management application.