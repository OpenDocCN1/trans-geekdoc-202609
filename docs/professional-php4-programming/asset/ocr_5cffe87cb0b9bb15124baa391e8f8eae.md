And these disadvantages:

+   - DBMSs are slower than files
+   - DBMSs require additional software
+   - Commercial DBMSs may be expensive

PHP is great for database programming. It has support for most of the DBMSs available today, such as Oracle, MySQL, PostgreSQL, Sybase, and DB2 (see Chapters 17-19 for more details). It has an established strategy to build or use a database abstraction class that can handle all the regular database operations. You can easily change the database without greatly changing the code written for a particular platform.

Building a true data layer for the application will result in no code changes to the application logic and the presentation layer (increasing code maintainability). However, abstraction is the best way to go to be completely scalable in terms of data storage.

> It is best to consider PEAR (PHP Extension and Add-on Repository) or PHPlib to find a database abstraction class for your DBMS. PEAR is an effort from PHP developers to build a common repository for reusable pieces of code, similar to Perl's CPAN. You can obtain more information about what is PEAR and how to write or use PEAR code from http://pear.php.net/. However, we will look at writing our own custom abstraction class in Chapter 17. It's not advisable to use native PHP functions for direct database connectivity with applications.

# XML Model

XML (Extended Markup Language), a recognized standard from the W3C (World Wide Web Consortium), is an excellent data modeling language. XML stored data is modeled by a set of DTDs or schemas that define the structure of XML documents in an industry or task-based way.

Today there are hundreds of applications and systems built using XML, both for interchanging and storing data. Since XML is a great standard for converting data from one format to another, it is fast becoming a cornerstone for application interaction. Even if applications do not have to interact with other systems, the use of XML can standardize internal structures, simplifying the development process.

Let's consider this single XML file for the polls application:

```
<pollsapp>
<poll>
<question>Which is your favorite color?</question>
<option>
<name>blue</name>
<votes>6</votes>
</option>
<option>
<name>green</name>
```