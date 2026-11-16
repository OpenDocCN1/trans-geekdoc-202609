# Introduction

+   - Chapter 21 looks at different ways to read a fairly basic XML file and present it to the browser as an HTML table. It also looks into the PHP APIs SAX, DOM, and PRAX that allow interaction with an XML document, and the Sablotron XSL support for PHP.

+   - Part 5 covers issues such as internationalizing, securing, and optimizing PHP applications. It also talks about the PHP extension libraries:

+   - Chapter 22 is an exploratory dive into internationalizing scripts in PHP. It also traverses some more real world code challenges that demonstrate work arounds to the regular approach, and some architectural suggestions for effective use of non-linear language constructs.

+   - Chapter 23 examines various aspects of security, from securing the server, securing the database and communications, and writing secure scripts, to choosing secure passwords.

+   - Chapter 24 concerns itself with tips, tricks and techniques that can be used to optimize PHP code and relational databases.

+   - Chapter 25 is all about the libraries that provide extensions to PHP's core language. It talks about using PDFLib to generate PDF documents, Ming to generate dynamic Shockwave Flash files, HAWHAW to allow wireless users to view our sites, and uses the GD library to create dynamic images, thus catering for the needs of almost any Internet user.

+   - Chapter 26 is a case study that demonstrates a general-purpose system for keeping track of user privileges.

The four appendices are a complete reference for PHP taken from a CVS snapshot in between versions 4.0.5 and 4.0.6. This reference goes beyond the documentation written by the creators of the various APIs, filling in gaps where appropriate on CVS related material where possible, and adding text as necessary:

+   - Appendix A is a list of all the extension functions

+   - Appendix B lists all the basic and standard extension functions

+   - Appendix C is a list of database functions

+   - Appendix D lists the various configuration directives

The appendices are available online at http://p2p.wrox.com/content/phpref/. We will keep this online resource updated to reflect subsequent version changes in PHP.

# What You Need to Use this Book

For server-side programming, you will need a web server on your machine. This can be IIS or Apache on a Windows platform, or Apache or Xitami for other operating systems.

For the client, you have a free choice. PHP is effective both on Internet Explorer and Netscape, as well as the other web browsers available today.

To run all the code in this book, you should have access to a relational database. Your choice for this is quite wide; we have chosen to keep MySQL as the underlying database theme. For PostgreSQL and ODBC aficionados we have also included detailed coverage on the same.