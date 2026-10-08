# Core PHP Programming

Depending on the type of site, you should choose some sort of diagram that shows the subsystems and how they relate to each other. These are entity relationship diagrams. I almost always create a page-flow diagram. Each node in the graph is a page as experienced by the user. Lines linking connect the page to other pages on the site. Another useful diagram is one that shows the relationship between database tables. Nodes represent tables, and you may wish list the fields inside boxes for the tables. Lines connect tables and show how fields match. It's also helpful to indicate whether the relationship between the tables is one to one or to many.

The next phase of design is interface specification. This defines how subsystems communicate. It can be as simple as listing the URLs for each page. If the site has forms, all the fields should be enumerated. If you are tracking user sessions, you will want to specify how you are doing this, with cookies or form variables. Define acceptable values for the session identifier. If the site will be communicating with files or a database, this phase will define names of files or login information for databases.

The largest part of a design document is a detailed description of how each module works. At this point it's acceptable to specify exactly the method for implementing the module. For example, you may specify a list of catalog items presented using the UL tag. On the other hand, if it doesn't matter, I suggest leaving it out. The person writing the actual code will probably have the best idea for solving the problem.

I suggest pursuing a style guide, which may be part of the design document or may stay alone. This document specifies the style of the code in the project. You'll find an in Appendix G, but dont flipping there now. The style guide deals with issues how to name variables, or where to place curly braces. Many of these issues are arbitrary. What's important is that a decision is made and followed. A large body of code formatted according to a standard is easier to read.

For the rest of this chapter I'll present some design ideas you may choose to adopt, PHP's dynamic nature allows for designs that can't be achieved in plain HTML. It is a shame to waste this functionality by using PHP as a faster alternative to CGI. I encourage you to consider PHP as the engine that powers a completely dynamic Web site.

# Using CVS

CVS, Concurrent Version System, is an open-source system that allows developers to track all changes to a project. A central repository stores the files that make up the project. Developers check out copies, modify them, and check back in. The system records all changes, which allows team members to check out any previous version of any given file. The system also allows to merge differences if two developers make changes to the same file.

In the context of project management, I have come to believe CVS is essential. It allows developers to collaborate efficiently, even when they are in separate locations. Popular

IT-SC book 634