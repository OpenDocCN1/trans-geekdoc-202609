
# Core PHP Programming

PHP runs on UNIX, Windows 98, Windows NT, and the Macintosh. PHP is designed to integrate the Apache Web Server. Apache, another free technology, is the most popular Web server on the Internet and comes with source code for UNIX and Windows. Commercial flavors of Apache WebTen and Stronghold php, too. But PHP works with other servers, including Microsoft's Internet Information Server. Scripts may be moved between server platforms of tightly coupling with Microsoft Web servers. PHP ISAPI is allowed to give the performance benefits decoupling with Microsoft Web servers.

PHP is modifiable. PHP has been designed to allow extension of functionality. PHP is coded in C and provides a well-defined Application Programming Interface (API). Callable programmers may add new functionality easily. The rich set of functions available in PHP are expensive that they often do. Even if you aren't interested in changing the source code, you can inspect it. Doing so may give you greater confidence in PHP's robustness.

PHP was written for Web page creation. Perl, C, and Java are very good languages and are readily capable of driving Web applications. The unfortunate sacrifice these alternatives is the ease of communication with the Web experience. PHP applications may be rapidly and easily developed because the code is encapsulated in the Web pages themselves.

Support for PHP is free and readily available. Queries to the PHP mailing list are often answered within yours. A custom bug-tracking system on the PHP site shows each problem with its resolution. Numerous sites, as phpbuilder.com and zend.com, offer original content to PHP developers.

PHP is popular. Internet service providers find PHP to be an attractive way to allow their customers to code Web applications without the risks exposed by CGLs. Developers worldwide offer PHP programming. Sites coded in PHP will have the option of moving from one to another as well as a choice of developers to add functionality.

Programming skills developed in other structures can be applied to PHP. PHP takes inspiration from both Perl and C. Experienced Perl and C programmers learn PHP very quickly. Likewise, programmers who learn PHP as a first language may apply their knowledge toward not only Perl and C, but other C-like languages such as Java. This is very different from learning to code in a visual editor such as Microsoft Visual InterDev.

# Interfaces to External Systems

PHP is somewhat famous for interlacing with many different database systems, but it also has support for other external systems. Support comes in the form of modules called extensions. They compile directly into PHP or are loaded dynamically. New extensions are added to the PHP project regularly. The extensions expose groups of functions for using these external systems. As I've said, some of these are databases. PHP offers functions for talking natively with most database systems, as well as providing access to ODBC drivers. Other extensions give you the ability to send messages using a particular network protocol, such as LDAP or IMAP. These functions are described in detail in Section Two, but you might find the highlights listed here interesting. Because PHP developers are enthusiastic and industrious, you will undoubtedly have more extensions have been added since I wrote this.

Aspell is a system for checking spelling. An extension provides support for numbers of arbitrary precision. There is an extension for dealing with various calendar systems. An extension provides support for DBM-style databases. You can read from filePro databases. You can interact with Hyperwave. You can use the ICAP, IMAP, and LDAP protocols. The Interbase and Informix databases are supported natively, as are mSQL, Mysql, MS SQL, Sybase, Oracle and Postgres. You can also parse XML or create DDX databases.

# How PHP Works with the Web Server

The normal process a Web server goes through deliver a page to a browser is all. It begins when a browser makes a request for a Web page. Based on the URL, the browser resolves the address of the Web server, identifies the page it would like, and gives any other information the Web server may need. Some of this information is about the browser itself, like its name (Mozilla), its version (4.08), or the operating system (Linux). Other information given the Web server could include the text user typed into form fields.

If the request is for an HTML file, the Web server will find the file, tell the browser to expect some HTML text, and then send the contents of the HTML file. The browser gets the contents and rendering the page based on the HTML code. If you have programming HTML for any length of time, this will be clear to you.

Hopefully you have had some experience with CGI scripts. When a Web server gets a request, it passes the request to the CGI script, which processes the request and returns HTML to the browser. The browser then renders the HTML page. This is how basic CGI works. However, CGI can be slow because it starts a new process for every request. PHP is much faster because it runs as a module within the web server.

# Hardware and Software Requirements

One great advantage of Open Source software is that it provides the opportunity for adaptation. With regard to hardware, I have personally witnessed PHP running on 100-MHz Pentium machines. A site expected to receive thousands of requests a day would need faster hardware, although. Despite my example, you are not limited to Intel hardware. PHP works equally well on PowerPC and Sparc.

When choosing an operating system, the general choice between Windows and a UNIX-like OS. PHP will run on Windows 95 and 98, although those operating systems are not suited for high-traffic web servers. It will also run on Windows NT and its successor, Windows 2000. For UNIX operating systems, PHP works on Linux and Solaris, as well as others. If you have a PPC-based system, such as a Macintosh, you may choose LinuxPC, a version of Linux. Chad Cunningham has contributed patches for compiling in Apple's OS X. In 1999 Brian Hard added support for IBM's OS/2.

PHP still works best with the Apache web server. But it now works well with IIS. It also compiles as a module for the ifftpd web server. You can make PHP work well with any web server using the CGI version, but I don't recommend this setup for production sites. If you are using UNIX, I recommend compiling PHP as Apache module. If you are using Windows NT, pursue IIS.

# Installation on Apache for UNIX

If you are using Linux, you can find an RPM for Apache and PHP, but this installation may not include every PHP feature you want. I recommend this route as a very quick start. You can always pursue compiling Apache and PHP from scratch later. PHP will compile on most versions of UNIX-like operating systems, including Solaris and Linux. If you have ever compiled software you've found on the Net, you will have little trouble with this installation. If you don't have extracting files from a tar archive and executing files, you may wish to rely on your sysadmin or someone else experienced. You will need to have root privileges to completely install PHP.

The first step is to download the tar files and unpack them. The CDROM accompanies this book has recent versions of both PHP and Apache, but you may wish to check online for the newest versions, <http://www.php.net/> and respectively.

After unpacking the tar file, the first step is to configure Apache. This is done by running the configure script inside the Apache directory:
