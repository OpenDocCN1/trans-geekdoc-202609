
# Introduction

We wrote the first edition of this book because we were tired of finding PHP books that were basically function references. These books are useful, but they don't help when your boss or client has "Go build me a shopping cart." In this book, we have done our best to make every example useful. You can use many of the code samples directly in your website, and can use many others with only minor modifications.

# What You Will Learn from This Book

Reading this book will enable you to build real-world, dynamic web applications. If you've built websites using plain HTML, you realize the limitations of this approach. Static content from a pure HTML website is just—static. It stays the same unless you update it. Your users can't interact with the site in any meaningful fashion.

Using a language such as PHP and a database as MySQL allows you to make your sites dynamic: to have them customizable and contain real-time information.

We have deliberately focused this book on real-world applications, even in the introductory chapters. We begin by looking at simple systems and work our way through the various parts of PHP and MySQL.

We then discuss aspects of security and authentication as they relate to building a real-world website and show you how to implement these aspects in PHP and MySQL. We also introduce you to integrating front-end and back-end technologies by discussing JavaScript and the role it plays in your application development.

In the final part of this book, we describe how to approach real-world projects and take you through the design, planning, and building of the following projects:

- User authentication and personalization
- Web-based email
- Social media integration

You should be able to use any of these projects as is, or you can modify them to suit your needs. We chose them because they represent the most common web applications built by programmers. If your needs are different, this book should help you along the way to achieving your goals.

# What Is PHP?

PHP is a server-side scripting language designed specifically for the web. Within an HTML page, you can embed PHP code that will be executed every time the page is visited. Your PHP code is interpreted by the web server and generates HTML or any output that you will see.

PHP was conceived in 1994 and was originally the work of one man, Rasmus Lerdorf. It was adopted by other talented people and has gone through several major rewrites to bring us to broad, mature product we see today. According to Google's Greg Michillie in May 2013, PHP ran more than three quarters of the world's websites, and that number had grown to over 82% by July 2016.

PHP is an open-source project, which means you have access to the source code and have the freedom to use, alter, and redistribute it.

PHP originally stood for Personal Home Page but changed in line with the GNU recursive naming convention (GNU = G's Not Unix) and now stands for PHP Hypertext Preprocessor.

The major version of PHP is 7. This version carries a complete rewrite of the Zend engine and some major improvements to the language. All of the code in this book has been tested and validated against the most recent release of PHP 7 at the time of writing, as well as the latest version in PHP 5.6 of releases, which is still officially supported.

The home page for PHP is available at http://www.php.net.

The home page for Zend Technologies is at http://www.zend.com.

# What Is MySQL?

MySQL (pronounced My-Ess-Que) is a very fast, robust, relational database management system (RDBMS). A database enables you to efficiently store, search, and retrieve data. The MySQL server controls access to your data to ensure that multiple users can work with it concurrently, to provide fast access to it, and to ensure that only authorized users can access often. Hence, MySQL is a multiuser server. It uses Structured Query Language (SQL), the standard database query language. MySQL has been publicly available since 1996 but has a development history going back to 1979. It is the world's most popular open-source database and has the Linux Journal Readers' Choice Award on a number of occasions.

MySQL is available under dual licensing scheme. You can use it under an open-source license (the GPL) free as long as you are willing to meet the terms of that license. If you want to distribute a non-GPL application including MySQL, you can buy a commercial license instead.

# Why Use PHP and MySQL?

When setting to build a website, you could use many different products.

You need to choose the following:

- Where to run your web servers: the cloud, virtual private servers, or actual hardware
- An operating system
- Web server software
- A database management system or other datastore
- A programming or scripting language

You may end up with a hybrid architecture with multiple datastores. Some of these choices are dependent on the others. For example, not all operating systems run on all hardware, not all web servers support all programming languages, and so on.

In this book, we do not pay attention to hardware, operating systems, or web server support. We don't need to. One of the best features of both PHP and MySQL is that they work with any operating system and many of the minor ones.

The majority of PHP code can be written to portable between operating systems and web servers. There are some PHP functions that specifically relate to the filesystem that are operating system dependent, but these are clearly marked as such in the manual and in this book.

Whatever hardware, operating system, and web server you choose, we believe you should seriously consider using PHP and MySQL.

# Some of PHP's Strengths

Some of PHP's main competitors are Python, Ruby (on Rails or otherwise), Node.js, Perl, Microsoft .NET, and Java.

In comparison to these products, PHP has many strengths, including the following:

- Performance
- Scalability
- Interfaces to many different database systems
- Built-in libraries for many common web tasks
- Low cost
- Ease of learning and use
- Strong object-oriented support
- Portability
- Flexibility of development approach
- Availability of source code
- Availability of support and documentation

A more detailed discussion of these strengths follows.

# Performance

PHP is very fast. Using a single inexpensive server, you can serve millions of hits per day. It scales down to the smallest email form and up to sites such as Facebook and Etsy.

# Scalability

PHP has what Rasmus Lerdorf frequently refers to as a “shared-nothing” architecture. This means that you can effectively and cheaply implement horizontal scaling with large numbers of commodity servers.

# Database Integration

PHP has native connections available to many database systems. In addition to MySQL, you can directly connect to PostgreSQL, Oracle, MongoDB, and MSSQL, among others. PHP 5 and 7 also have a built-in SQL interface to talk to flat files, called SQLite.

Using the Open Database Connectivity (ODBC) standard, you can connect to any database provides an ODBC driver. This includes Microsoft products and many others.

In addition to native libraries, PHP comes with a database abstraction layer called PHP Database Objects (PDOs), which allows consistent access and promotes secure coding practices.

# Built-in Libraries

Because PHP was designed for use on the Web, it has many built-in functions for performing many web-related tasks. You can generate images on the fly, connect to web services and other network services, parse XML, send email, work with cookies, and generate PDF documents, all with just a few lines of code.

# Cost

PHP is free. You can download the latest version at any time from http://php.net for charge.

# Ease of Learning PHP

The syntax of PHP is based on other programming languages, primarily C and Perl. If you already know C or Perl, or a C-like language such as C++ or Java, you will be productive using PHP almost immediately.

# Object-Oriented Support

PHP version 5 had well-designed object-oriented features, which continued to be refined and improved in PHP version 7. If you learned to program in Java or C++, you will find the features (and generally the syntax) that you expect, such as inheritance, private and protected attributes and methods, abstract classes and methods, constructors, and destructors. You will even find some common features such as iterators and traits.
