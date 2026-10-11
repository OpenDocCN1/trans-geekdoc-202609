 

PHP Tutorials

\- Herong's Tutorial Examples

![](Images/image00228.jpeg)

v5.16, 2022

Herong Yang

© 2003-2022 Herong Yang. All rights reserved.

 

This PHP tutorial book is a collection of notes and sample codes written by the author while he was learning PHP himself. Topics include PHP script syntax; data types, variables, array, expressions, statements and functions; Web server integration; HTTP requests and controlling HTTP responses; sessions, cookies, and file uploads/downloads; MySQL database server access; files, directories, and ZIP archives; parsing HTML Documents; processing image files; SOAP extension; managing non-ASCII characters; classes and objects; using PHP on Windows, macOS and Linux; executing external programs on operating system. Updated in 2022 (Version v5.16) with minor changes. For latest updates and free sample chapters, visit https://www.herongyang.com/PHP.

Table of Contents

> [About This Book](#part0002.xhtml)
> 
> [Introduction and Installation of PHP 7.3](#part0003.xhtml)
> 
> [What Is PHP](#part0004.xhtml)
> 
> [Downloading and Installing PHP 7.3 for Windows](#part0005.xhtml)
> 
> ["php -help" - Command Line Options](#part0006.xhtml)
> 
> ["php -m" - Built-in Modules](#part0007.xhtml)
> 
> ["php -i" - PHP Engine Information](#part0008.xhtml)
> 
> [php.ini - PHP Runtime Configuration](#part0009.xhtml)
> 
> [Hello.php - My First PHP Script](#part0010.xhtml)
> 
> ["php -a" - PHP Interactive Shell](#part0011.xhtml)
> 
> [Downloading and Installing PHP Documentation](#part0012.xhtml)
> 
> [PHP Script File Syntax](#part0013.xhtml)
> 
> [PHP Script Source Code File Format](#part0014.xhtml)
> 
> [PHP Script Processing Rules](#part0015.xhtml)
> 
> [PHP Statement Delimiter and Comments](#part0016.xhtml)
> 
> [PHP Data Types and Data Literals](#part0017.xhtml)
> 
> [Data Types Supported in PHP](#part0018.xhtml)
> 
> [Data Literals Supported in PHP](#part0019.xhtml)
> 
> [Data Literals Examples for Integer, String and Other Data Types](#part0020.xhtml)
> 
> [Overflow of Integer and Float Values](#part0021.xhtml)
> 
> [Variables, References, and Constants](#part0022.xhtml)
> 
> [Variables and Assignment Operations](#part0023.xhtml)
> 
> [References and Variables](#part0024.xhtml)
> 
> [Variable Variable Name - Name Variables with Expressions](#part0025.xhtml)
> 
> [Constant and define() Function](#part0026.xhtml)
> 
> [Expressions, Operations and Type Conversions](#part0027.xhtml)
> 
> [What Is an Expression](#part0028.xhtml)
> 
> [What Is an Operation](#part0029.xhtml)
> 
> [Precedence of Operations](#part0030.xhtml)
> 
> [Data Type Automatic Conversion](#part0031.xhtml)
> 
> [Conditional Statements - "if" and "switch"](#part0032.xhtml)
> 
> ["if" Statements](#part0033.xhtml)
> 
> ["if" Statement Examples](#part0034.xhtml)
> 
> ["switch" Statements](#part0035.xhtml)
> 
> ["switch" Statement Examples](#part0036.xhtml)
> 
> [Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)
> 
> ["while" Statements](#part0038.xhtml)
> 
> ["while" Statement Examples](#part0039.xhtml)
> 
> ["for" Statements](#part0040.xhtml)
> 
> ["for" Statement Examples](#part0041.xhtml)
> 
> ["do ... while" Statements](#part0042.xhtml)
> 
> ["break" and "continue" Statements](#part0043.xhtml)
> 
> [Function Declaration, Arguments, and Return Values](#part0044.xhtml)
> 
> [What Is a Function](#part0045.xhtml)
> 
> ["function" Statements - Defining Functions](#part0046.xhtml)
> 
> [Function Call Operations](#part0047.xhtml)
> 
> [Passing Arguments to Functions](#part0048.xhtml)
> 
> [Example of Passing Arguments by Values](#part0049.xhtml)
> 
> [Using Pass-by-Value Arguments for References](#part0050.xhtml)
> 
> [Example of Passing Arguments by References](#part0051.xhtml)
> 
> [Variable-Length Argument Lists](#part0052.xhtml)
> 
> [Providing Default Values to Argument Variables](#part0053.xhtml)
> 
> [Returning Values from Functions](#part0054.xhtml)
> 
> [Returning References from Functions](#part0055.xhtml)
> 
> [Usage Examples of Functions](#part0056.xhtml)
> 
> [Arrays - Ordered Maps](#part0057.xhtml)
> 
> [What Is an Array](#part0058.xhtml)
> 
> [Creating Arrays - Examples](#part0059.xhtml)
> 
> [Array Related Built-in Functions](#part0060.xhtml)
> 
> [Usage Examples of Array Functions](#part0061.xhtml)
> 
> [Interface with Operating System](#part0062.xhtml)
> 
> [$argv\[\] - Command Line Arguments](#part0063.xhtml)
> 
> [Options to Execute External Programs](#part0064.xhtml)
> 
> [\`command\` - Backtick Operator](#part0065.xhtml)
> 
> [exec() - Execute External Programs](#part0066.xhtml)
> 
> [system() - Execute External Programs](#part0067.xhtml)
> 
> [passthru() - Execute External Programs](#part0068.xhtml)
> 
> [popen() - Execute External Programs](#part0069.xhtml)
> 
> [proc\_open() - Execute External Programs](#part0070.xhtml)
> 
> [memory\_get\_usage() - Memory Usage Info](#part0071.xhtml)
> 
> [set\_time\_limit() - max\_execution\_time](#part0072.xhtml)
> 
> [Introduction of Class and Object](#part0073.xhtml)
> 
> [What Is a Class](#part0074.xhtml)
> 
> [What Is an Object](#part0075.xhtml)
> 
> [What Is a Constructor](#part0076.xhtml)
> 
> [What Is a Static Method](#part0077.xhtml)
> 
> [What Is a Static Variable](#part0078.xhtml)
> 
> [What Is a Superclass and a Subclass](#part0079.xhtml)
> 
> [What Is an Abstract Class](#part0080.xhtml)
> 
> [What Is an Abstract Method](#part0081.xhtml)
> 
> [What Is an Interface](#part0082.xhtml)
> 
> [What Is a Trait](#part0083.xhtml)
> 
> [What Is an Overloaded Property](#part0084.xhtml)
> 
> [What Is an Overloaded Method](#part0085.xhtml)
> 
> [What Is Object Property Iteration](#part0086.xhtml)
> 
> [What Is Object Cloning](#part0087.xhtml)
> 
> [What Is Object Serialization](#part0088.xhtml)
> 
> [What Is in an Object Variable](#part0089.xhtml)
> 
> [Updating Variables Who Share an Object](#part0090.xhtml)
> 
> [Passing Objects as Function Arguments](#part0091.xhtml)
> 
> [Integrating PHP with Apache Web Server](#part0092.xhtml)
> 
> [Downloading Apache 2.4.37 Binary for Windows](#part0093.xhtml)
> 
> [Installing Apache 2.4.37 on Windows Systems](#part0094.xhtml)
> 
> [Publishing HTML Documents as Web Pages](#part0095.xhtml)
> 
> [Starting and Stopping Apache Server](#part0096.xhtml)
> 
> [Configuring Apache for PHP CGI Scripts](#part0097.xhtml)
> 
> [Publishing PHP Scripts as Web Pages](#part0098.xhtml)
> 
> [Permission Error on php-cgi.exe](#part0099.xhtml)
> 
> [Configuring Apache PHP Load Module](#part0100.xhtml)
> 
> [Retrieving Information from HTTP Requests](#part0101.xhtml)
> 
> [Predefined Variables Related to HTTP Requests](#part0102.xhtml)
> 
> [Operating System Information in $\_SERVER](#part0103.xhtml)
> 
> [Web Server Information in $\_SERVER](#part0104.xhtml)
> 
> [Information in $\_GET and $\_REQUEST](#part0105.xhtml)
> 
> [Registering $\_REQUEST Keys as Global Variables](#part0106.xhtml)
> 
> [Creating and Managing Sessions in PHP Scripts](#part0107.xhtml)
> 
> [What Is a Session](#part0108.xhtml)
> 
> [How Sessions Are Supported in PHP](#part0109.xhtml)
> 
> [SessionPage\*.php - Session Test Script Pages](#part0110.xhtml)
> 
> [Running Session Test Script Pages](#part0111.xhtml)
> 
> [Managing Session IDs without Cookies](#part0112.xhtml)
> 
> [Where Is Session Data Stored](#part0113.xhtml)
> 
> [Sending and Receiving Cookies in PHP Scripts](#part0114.xhtml)
> 
> [What Is a Cookie](#part0115.xhtml)
> 
> [Sending and Receiving Cookies](#part0116.xhtml)
> 
> [Sending and Receiving Cookies - Example](#part0117.xhtml)
> 
> [ob\_start() - Output Buffering Function](#part0118.xhtml)
> 
> [Persistent Cookies Saved on Hard Disk](#part0119.xhtml)
> 
> [Other Cookie Properties - Domain and Path](#part0120.xhtml)
> 
> [Controlling HTTP Response Header Lines in PHP Scripts](#part0121.xhtml)
> 
> [What Is an HTTP Response](#part0122.xhtml)
> 
> [HTTP Response Header Lines](#part0123.xhtml)
> 
> [header() - Inserting a Raw Header Lines](#part0124.xhtml)
> 
> [HttpRequestGet.php - Viewing Header Lines](#part0125.xhtml)
> 
> [Response Header Lines of Static Files](#part0126.xhtml)
> 
> [HttpHeaderLines.php - Examples of Inserting Header Lines](#part0127.xhtml)
> 
> [Location: - Forcing the Browser to Redirect to Another URL](#part0128.xhtml)
> 
> [Content-Type: - Generating Non-HTML Response Body](#part0129.xhtml)
> 
> [Content-Disposition: - Sending Files for Downloading](#part0130.xhtml)
> 
> [Managing File Upload](#part0131.xhtml)
> 
> [File Upload Web Form](#part0132.xhtml)
> 
> [File Upload PHP Script](#part0133.xhtml)
> 
> [MySQL Server Connection and Access Functions](#part0134.xhtml)
> 
> [Configuring PHP for MySQL Server Access](#part0135.xhtml)
> 
> [mysqli\_connect() and Other MySQL Functions](#part0136.xhtml)
> 
> [MySqlLoop.php - MySQL Functions Test](#part0137.xhtml)
> 
> [Functions to Manage Directories, Files and Images](#part0138.xhtml)
> 
> [opendir() and Directory Management Functions](#part0139.xhtml)
> 
> [file\_exists() and File Testing Functions](#part0140.xhtml)
> 
> [FileExistsTest.php - File Testing Examples](#part0141.xhtml)
> 
> [fopen() and File Input/Output Functions](#part0142.xhtml)
> 
> [File\_Input\_Output\_Test.php - File Input/Output Examples](#part0143.xhtml)
> 
> [readfile() and Special File Handling Functions](#part0144.xhtml)
> 
> [ShowPhoto.php - Simple Slid Show Script](#part0145.xhtml)
> 
> [SOAP Extension Function and Calling Web Services](#part0146.xhtml)
> 
> [PHP Implementations of SOAP](#part0147.xhtml)
> 
> [Turning on the Default SOAP Extension](#part0148.xhtml)
> 
> [Hello\_There.php - First Example of SOAP](#part0149.xhtml)
> 
> [SoapClient - SOAP Client Class and Functions](#part0150.xhtml)
> 
> [Hello\_There\_Dump.php - Debugging SOAP Messages](#part0151.xhtml)
> 
> [What Is WSDL](#part0152.xhtml)
> 
> [Using SOAP Extension in non-WSDL Mode](#part0153.xhtml)
> 
> [SOAP Server Functions and Examples](#part0154.xhtml)
> 
> [SoapServer - SOAP Server Class and Functions](#part0155.xhtml)
> 
> [HelloServer.php - First SOAP Server Application](#part0156.xhtml)
> 
> [HelloServer12.php - First SOAP 1.2 Server Application](#part0157.xhtml)
> 
> [HelloServerWsdl.php - SOAP 1.2 Server Application in WSDL Mode](#part0158.xhtml)
> 
> [Localization Overview of Web Applications](#part0159.xhtml)
> 
> [What Is Localization / Internationalization](#part0160.xhtml)
> 
> [Localization of Web Based Applications](#part0161.xhtml)
> 
> [Character String Traveling Paths](#part0162.xhtml)
> 
> [Output ASCII Character Strings from PHP Scripts](#part0163.xhtml)
> 
> [Using Non-ASCII Characters in HTML Documents](#part0164.xhtml)
> 
> [Basic Rules of Using Non-ASCII Characters in HTML Documents](#part0165.xhtml)
> 
> [French Characters in HTML Documents - UTF-8 Encoding](#part0166.xhtml)
> 
> [French Characters in HTML Documents - ISO-8859-1 Encoding](#part0167.xhtml)
> 
> [Chinese Characters in HTML Documents - UTF-8 Encoding](#part0168.xhtml)
> 
> [Chinese Characters in HTML Documents - GB2312 Encoding](#part0169.xhtml)
> 
> [Characters of Multiple Languages in HTML Documents](#part0170.xhtml)
> 
> [Using Non-ASCII Characters as PHP Script String Literals](#part0171.xhtml)
> 
> [Basic Rules of Using Non-ASCII Characters in HTML Documents](#part0172.xhtml)
> 
> [French Characters in String Literals - UTF-8 Encoding](#part0173.xhtml)
> 
> [French Characters in HTML Documents - ISO-8859-1 Encoding](#part0174.xhtml)
> 
> [Chinese Characters in String Literals - UTF-8 Encoding](#part0175.xhtml)
> 
> [Chinese Characters in String Literals - GB2312 Encoding](#part0176.xhtml)
> 
> [Characters of Multiple Languages in String Literals](#part0177.xhtml)
> 
> [Receiving Non-ASCII Characters from Input Forms](#part0178.xhtml)
> 
> [Basic Rules of Receiving Non-ASCII Characters from Input Forms](#part0179.xhtml)
> 
> [Receiving Non-ASCII Characters with GET Method](#part0180.xhtml)
> 
> [Receiving Non-ASCII Characters with POST Method](#part0181.xhtml)
> 
> [Receiving Non ASCII Characters in UTF-8 Encoding](#part0182.xhtml)
> 
> [Decoding HTML Entities](#part0183.xhtml)
> 
> ["mbstring" Extension and Non-ASCII Encoding Management](#part0184.xhtml)
> 
> ["mbstring" - Multi-Byte String Extension](#part0185.xhtml)
> 
> [mb\_convert\_encoding() and Other mbstring Functions](#part0186.xhtml)
> 
> [Examples of Using "mbstring" Functions](#part0187.xhtml)
> 
> [Managing HTTP Input and Output Encoding](#part0188.xhtml)
> 
> [Managing Non-ASCII Character Strings with MySQL Servers](#part0189.xhtml)
> 
> [Storing Non-ASCII Characters in Database](#part0190.xhtml)
> 
> [Transmitting Non-ASCII Characters with Database](#part0191.xhtml)
> 
> [MySqlUnicode.php - MySQL Unicode UTF-8 Encoding Example](#part0192.xhtml)
> 
> [Parsing and Managing HTML Documents](#part0193.xhtml)
> 
> [DOM Extension for HTML Documents](#part0194.xhtml)
> 
> [Parse and Traverse HTML Documents](#part0195.xhtml)
> 
> [Build New HTML Documents](#part0196.xhtml)
> 
> [Load HTML Documents with LIBXML\_NOBLANKS](#part0197.xhtml)
> 
> [Remove Whitespaces in HTML Documents](#part0198.xhtml)
> 
> [DOCTYPE Element in HTML Documents](#part0199.xhtml)
> 
> [Remove Dummy Elements in HTML Documents](#part0200.xhtml)
> 
> [Install DOM Extension on CentOS](#part0201.xhtml)
> 
> [Configuring and Sending Out Emails](#part0202.xhtml)
> 
> [Using Local Windows System as a Mail Server](#part0203.xhtml)
> 
> [Sending Out Emails from PHP Scripts](#part0204.xhtml)
> 
> [Sending Out Emails on Linux Systems](#part0205.xhtml)
> 
> [Install PHPMailer on CentOS Systems](#part0206.xhtml)
> 
> [Send Local Emails with PHPMailer](#part0207.xhtml)
> 
> [Send Remote Emails with PHPMailer](#part0208.xhtml)
> 
> [Use SMTPS Protocol with PHPMailer](#part0209.xhtml)
> 
> [PHP 5.6 and PHPMailer 5.2](#part0210.xhtml)
> 
> [Install PHPMailer from Source Code](#part0211.xhtml)
> 
> [Image and Picture Processing](#part0212.xhtml)
> 
> [GD Library of Image Functions](#part0213.xhtml)
> 
> [GD Library - Draw Graphical Elements](#part0214.xhtml)
> 
> [GD Library - Print 2 Pictures on 1 Page](#part0215.xhtml)
> 
> [GD Library - Create Transparent Image](#part0216.xhtml)
> 
> [Transparent Image Over Text Web Page](#part0217.xhtml)
> 
> [GD Library - Pad Transparent Image](#part0218.xhtml)
> 
> [Managing ZIP Archive Files](#part0219.xhtml)
> 
> [The ZipArchive Class](#part0220.xhtml)
> 
> [Create New ZIP Archive](#part0221.xhtml)
> 
> [Exact Files from ZIP Archive](#part0222.xhtml)
> 
> [Create ZIP Archive with Directory](#part0223.xhtml)
> 
> [Create ZIP Archive for Download](#part0224.xhtml)
> 
> [Managing PHP Engine and Modules on macOS](#part0225.xhtml)
> 
> [PHP Version Pre-Installed on macOS](#part0226.xhtml)
> 
> [Upgrade PHP Engine on macOS](#part0227.xhtml)
> 
> [Managing PHP Engine and Modules on CentOS](#part0228.xhtml)
> 
> [PHP Version Pre-Installed on CentOS](#part0229.xhtml)
> 
> [Install PHP Extensions on CentOS](#part0230.xhtml)
> 
> [PHP Version Pre-Installed on CentOS 6](#part0231.xhtml)
> 
> [Use PHP Composer on CentOS Computers](#part0232.xhtml)
> 
> [Archived Tutorials](#part0233.xhtml)
> 
> [Archived: Downloading and Installing PHP 7.0 for Windows](#part0234.xhtml)
> 
> [Archived: Downloading and Installing PHP 5.6.6 for Windows](#part0235.xhtml)
> 
> [Archived: Downloading and Installing PHP 5.4.3 for Windows](#part0236.xhtml)
> 
> [Archived: Downloading and Installing PHP 5.2.2 for Windows](#part0237.xhtml)
> 
> [Archived: Downloading and Installing PHP 5.0.4 for Windows](#part0238.xhtml)
> 
> [Archived: Adding PHP to IIS as CGI](#part0239.xhtml)
> 
> [Archived: Downloading Apache HTTP Server 2.4.12 for Windows](#part0240.xhtml)
> 
> [Archived: Installing Apache HTTP Server 2.4.12 on Windows](#part0241.xhtml)
> 
> [Archived: Publishing PHP Scripts as Web Pages](#part0242.xhtml)
> 
> [Archived: Configuration for php\_mysql.dll Library](#part0243.xhtml)
> 
> [Archived: mysql\_connect() using php\_mysql.dll Library](#part0244.xhtml)
> 
> [Archived: MySqlLoop.php using php\_mysql.dll Library](#part0245.xhtml)
> 
> [Archived: Get\_Temperature.php - First Example of SOAP](#part0246.xhtml)
> 
> [Archived: Get\_Temperature\_Dump.php - Dumping Debugging Information](#part0247.xhtml)
> 
> [Archived: MySqlUnicode.php using php\_mysql.dll Library](#part0248.xhtml)
> 
> [References](#part0249.xhtml)

**Keywords:** PHP, Tutorial, Examples, Web

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟About This Book

This section provides some detailed information about this book - PHP Tutorials - Herong's Tutorial Examples.

**Title:** PHP Tutorials - Herong's Tutorial Examples

**Author:** Herong Yang - Contact by email via herong\_yang@yahoo.com.

**Category:** COMPUTERS / Programming Languages / PHP

**Version/Edition:** v5.16, 2022

**Number of pages:** 472

**Description:** This PHP tutorial book is a collection of notes and sample codes written by the author while he was learning PHP himself. Topics include PHP script syntax; data types, variables, array, expressions, statements and functions; Web server integration; HTTP requests and controlling HTTP responses; sessions, cookies, and file uploads/downloads; MySQL database server access; files, directories, and ZIP archives; parsing HTML Documents; processing image files; SOAP extension; managing non-ASCII characters; classes and objects; using PHP on Windows, macOS and Linux; executing external programs on operating system. Updated in 2022 (Version v5.16) with minor changes.

**Keywords:** Apache, class, cookie, HTML, HTTP, image, MySQL, PHP, redirect, SOAP, Unicode, XML, ZIP.

**Copyright:**

*   This book is under © 2003-2022 Herong Yang. All rights reserved.
*   Material in this book may not be published, broadcasted, rewritten or redistributed in any form.
*   The example codes is provided as-is, with no warranty of any kind.

**Revision history:**

*   Version 5.16, 2022. Minor updates.
*   Version 5.10, 2020. Added ZIP archive tutorials.
*   Version 5.00, 2019. Updated with PHP 7.
*   Version 4.00, 2015. Added class, object and Apache tutorials.
*   Version 3.00, 2009. Third edition.
*   Version 2.00, 2007. Second edition.
*   Version 1.00, 2003. First edition.

**Web version:** [https://www.herongyang.com/PHP](https://www.herongyang.com/PHP) - Provides free sample chapters, latest updates and readers' comments. The Web version of this book has been viewed a total of:

*   2,479,704 times as of December 2018.
*   2,381,664 times as of December 2018.
*   2,301,842 times as of December 2018.
*   2,241,750 times as of December 2018.
*   2,180,865 times as of December 2017.
*   2,119,742 times as of December 2016.
*   2,054,798 times as of December 2015.
*   1,916,316 times as of December 2014.
*   1,557,001 times as of December 2013.
*   1,368,846 times as of December 2012.
*   1,203,837 times as of December 2011.
*   1,017,118 times as of December 2010.

**PDF/EPUB version:** [https://www.herongyang.com/PHP/PDF-Full-Version.html](https://www.herongyang.com/PHP/PDF-Full-Version.html) - Provides information on how to obtain the full version of this book in PDF, EPUB, or other format.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Introduction and Installation of PHP 7.3

This chapter provides tutorial notes and example codes on PHP installation. Topics include quick introduction of PHP, downloading and installing PHP engine, PHP command line options, writing first PHP script.

> [What Is PHP](#part0004.xhtml)
> 
> [Downloading and Installing PHP 7.3 for Windows](#part0005.xhtml)
> 
> ["php -help" - Command Line Options](#part0006.xhtml)
> 
> ["php -m" - Built-in Modules](#part0007.xhtml)
> 
> ["php -i" - PHP Engine Information](#part0008.xhtml)
> 
> [php.ini - PHP Runtime Configuration](#part0009.xhtml)
> 
> [Hello.php - My First PHP Script](#part0010.xhtml)
> 
> ["php -a" - PHP Interactive Shell](#part0011.xhtml)
> 
> [Downloading and Installing PHP Documentation](#part0012.xhtml)

Takeaways:

*   PHP is becoming the most popular Web server-side scripting language now.
*   Downloading and installing the standard PHP build for Windows systems is easy.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction and Installation of PHP 7.3](#part0003.xhtml)

∟What Is PHP

This section describes what is PHP language and what are main features supported in PHP.

**What Is PHP?** PHP stands for PHP: Hypertext Preprocessor, a recursive acronym. It is mainly a Web server side scripting language. But it can also be used for other purposes.

PHP was originally created by Rasmus Lerdorf in 1995 as a simple Web page generation tool named as PHP/FI (Personal Home Page/Forms Interpreter). Today it becomes the number one of server side scripting languages. Here is a comparison of number of matches on Google for different popular script key words:

```
Key words             Number of matches

"PHP scripting"         400,000
"perl scripting"        371,000
"ASP.NET scripting"      40,100
"ASP scripting"          30,900
"JSP scripting"          17,500
```

Main features of PHP:

*   Web application features - PHP support most commonly used Web application features like: HTTP Cookie, Session, File Upload, etc.
*   CLI (Command-Line Interface)- PHP is commonly used to write Web applications to be integrated to Web servers using the Common Gateway Interface (CGI). But PHP can also be used to write standalone applications to be executed by the CLI (Command-Line Interface).
*   Data types - PHP supports many data types like other programming languages: signed and unsigned integers, floating numbers, strings, resources, null, etc.
*   File I/O - PHP supports most commonly used file I/O features like local file and path management, remote resource access using Internet protocols like HTTP and FTP.
*   Safe mode - PHP supports a safe mode with many built-in functions restricted or disabled.
*   Pre-compilation - PHP Web applications are usually deployed in source code, which will be interpreted on-the-fly when Web requests arrive to the server. But PHP Web applications can also be pre-compiled and deployed in executable format to speed up Web requests response time.
*   Object-oriented programming - PHP supports object-oriented programming features like object references, private and protected member variables and methods, abstract and final classes and methods, constructors and destructors, interfaces, etc.
*   Built-in modules - The standard PHP build comes with many free and open source libraries included as built-in modules for calendar dates handling, FTP protocol support, XML processing, encryption and decryption, ODBC support, ZIP support, regular expression support, etc.
*   Extensions - A large collection of PHP extensions are available to add functionalities to the standard PHP build. Examples of PHP extensions are Windows API, process management on Unix OS, multibyte string support, cURL (client-side URL transfer), image manipulation, data compression, database access, Web service, etc.

PHP major releases:

```
7.0   3 December 2015
6.x   Not released
5.6   28 August 2014
5.4   1 March 2012
5.3   30 June 2009
5.0   13 July 2004
4.0   22 May 2000
3.0   6 June 1998
2.0   1 November 1997
1.0   8 June 1995
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction and Installation of PHP 7.3](#part0003.xhtml)

∟Downloading and Installing PHP 7.3 for Windows

This section provides a tutorial example on how to download and install the PHP engine 7.0 on a Windows system.

1\. Go to [windows.php.net/download/](http://windows.php.net/download/) and download the ""VC15 x64 Thread Safe (2018-Dec-06 04:31:24)" binary version for Windows. You will get a file called "php-7.3.0-Win32-VC15-x64" of 21,846,474 bytes.

2\. Unzip "php-7.3.0-Win32-VC15-x64" to \\php folder.

3\. Open a command window, and try the following commands:

```
herong> \php\php -v
```

4\. If see an error message saying: "The program can't start because VCRUNTIME150.dll is missing from your computer. Try reinstalling the program to fix this problem.", you need to install "Visual Studio 2015 x86".

*   Go to "Microsoft Visual C++ Redistributable for Visual Studio 2015" page at [microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145).
*   Click the "Download" button.
*   Save the download file "vc\_redist.x86.exe" to desktop.
*   Double-click on "vc\_redist.x86.exe" to run it.
*   Follow instruction to finish installation.

5\. Open a command window, and try the following commands again:

```
herong> \php\php -v

PHP 7.3.0 (cli) (built: Dec  6 2018 01:54:19)
   (ZTS MSVC15 (Visual C++ 2017) x64)
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.0-dev, Copyright (c) 1998-2018 Zend Technologies
```

Cool, both Command Line Interface (CLI) and Common Gateway Interface (CGI) of PHP are working!

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction and Installation of PHP 7.3](#part0003.xhtml)

∟"php -help" - Command Line Options

This section provides a tutorial example on how to see all command line options supported by the PHP engine: php -help.

If you want to know what command line options are supported by the PHP engine, you can run PHP with the "-help" option:

```
herong> \php\php -help

Usage: php [options] [-f] <file> [--] [args...]
   php [options] -r <code> [--] [args...]
   php [options] [-B <begin_code>] -R <code> [-E <end_code>] [--] [args...]
   php [options] [-B <begin_code>] -F <file> [-E <end_code>] [--] [args...]
   php [options] -- [args...]
   php [options] -a

  -a               Run interactively
  -c <path>|<file> Look for php.ini file in this directory
  -n               No php.ini file will be used
  -d foo[=bar]     Define INI entry foo with value 'bar'
  -e               Generate extended information for debugger/profiler
  -f <file>        Parse and execute <file>.
  -h               This help
  -i               PHP information
  -l               Syntax check only (lint)
  -m               Show compiled in modules
  -r <code>        Run PHP <code> without using script tags <?..?>
  -B <begin_code>  Run PHP <begin_code> before processing input lines
  -R <code>        Run PHP <code> for every input line
  -F <file>        Parse and execute <file> for every input line
  -E <end_code>    Run PHP <end_code> after processing all input lines
  -H               Hide any passed arguments from external tools.
  -S <addr>:<port> Run with built-in web server.
  -t <docroot>     Specify document root <docroot> for built-in web server.
  -s               Output HTML syntax highlighted source.
  -v               Version number
  -w               Output source with stripped comments and whitespace.
  -z <file>        Load Zend extension <file>.

  args...          Arguments passed to script. Use -- args when first argument
                   starts with - or script is read from stdin

  --ini            Show configuration file names

  --rf <name>      Show information about function <name>.
  --rc <name>      Show information about class <name>.
  --re <name>      Show information about extension <name>.
  --rz <name>      Show information about Zend extension <name>.
  --ri <name>      Show configuration for extension <name>.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction and Installation of PHP 7.3](#part0003.xhtml)

∟"php -m" - Built-in Modules

This section provides a tutorial example on how to get a list of all modules that are pre-compiled in the PHP engine: php -m.

The Windows binary version of PHP 7.3 engine comes with many modules pre-compiled into the engine. The "-m" option can give you a list of all built-in modules:

```
herong> \php\php -m

[PHP Modules]
bcmath
calendar
Core
ctype
date
dom
filter
hash
iconv
json
libxml
mysqlnd
pcre
PDO
Phar
readline
Reflection
session
SimpleXML
SPL
standard
tokenizer
wddx
xml
xmlreader
xmlwriter
zip
zlib

[Zend Modules]
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction and Installation of PHP 7.3](#part0003.xhtml)

∟"php -i" - PHP Engine Information

This section provides a tutorial example on how to get more information about the PHP engine and its execution environment: php -i

If you want to know more information about the PHP engine and its execution environment you run the php.exe program with the "-i" option:

```
herong> \php\php -i

phpinfo()
PHP Version => 7.3.0

System => Windows NT Local 6.1 build 7601 (Windows 7 Professional ...
Build Date => Dec  6 2018 01:48:44
Compiler => MSVC15 (Visual C++ 2017)
Architecture => x64
Configure Command => cscript /nologo configure.js  "--enable-snaps...
Server API => Command Line Interface
Virtual Directory Support => enabled
Configuration File (php.ini) Path => C:\windows
Loaded Configuration File => (none)
Scan this dir for additional .ini files => (none)
Additional .ini files parsed => (none)
PHP API => 20180731
PHP Extension => 20180731
Zend Extension => 320180731
Zend Extension Build => API320180731,TS,VC15
PHP Extension Build => API20180731,TS,VC15
Debug Build => no
Thread Safety => enabled
Zend Signal Handling => disabled
Zend Memory Manager => enabled
Zend Multibyte Support => disabled
IPv6 Support => enabled
DTrace Support => disabled

Registered PHP Streams => php, file, glob, data, http, ftp, zip, ...
Registered Stream Socket Transports => tcp, udp
Registered Stream Filters => convert.iconv.*, mcrypt.*, mdecrypt....

This program makes use of the Zend Scripting Language Engine:

...
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction and Installation of PHP 7.3](#part0003.xhtml)

∟php.ini - PHP Runtime Configuration

This section describes the PHP runtime configuration file, php.ini.

PHP runtime behavior can be controlled by a runtime configuration file called php.ini in the \\php folder. The PHP installation package provides 2 versions of php.ini:

```
php.ini-development   - More secure and better performance
php.ini-production    - More verbose in error messages
```

Since we are running PHP on a local machine to learn the PHP language, we should use the php.ini-development version. So let's copy php.ini-development to php.ini:

```
>copy \php\php.ini-development \php\php.ini
        1 file(s) copied.

>type \php\php.ini | more
[PHP]

;;;;;;;;;;;;;;;;;;;
; About php.ini   ;
;;;;;;;;;;;;;;;;;;;
; PHP's initialization file, generally called php.ini, is responsible
; for configuring many of the aspects of PHP's behavior.
; ...

; Name for user-defined php.ini files. Default is ".user.ini"
;user_ini.filename = ".user.ini"

; To disable this feature set this option to empty value
;user_ini.filename =

; TTL for user-defined php.ini files (time-to-live) in seconds.
; Default is 300 seconds (5 minutes)
;user_ini.cache_ttl = 300

; Enable the PHP scripting language engine under Apache.
engine = On

...
```

As you can see the php.ini file is very easy to use. The ";" character at the beginning of the line indicates a comment line. Configuration settings are provided in the format of "name = value". The default version of php.ini comes with lots of comments to help you understaning what is the meaning of each setting.

For example, if I want to set a default timezone in runtime environment, I can edit php.ini and change the "date.timezone" setting:

```
>edit \php\php.ini

; Defines the default timezone used by the date functions
date.timezone = Europe/Paris
```

Now the PHP engine will be running with Europe/Paris as the default timezone.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction and Installation of PHP 7.3](#part0003.xhtml)

∟Hello.php - My First PHP Script

This section provides a tutorial example on how to write the first PHP script, Hello.php, and run it with PHP CLI and PHP CGI.

Use any text editor like notepad, and enter the first PHP script, Hello.php:

```
Hello <?php echo "world!"; ?>
```

Run it with PHP CLI first:

```
herong> \php\php Hello.php

Hello world!
```

Then run it with PHP CGI:

```
herong> \php\php-cgi Hello.php

X-Powered-By: PHP/7.3.0
Content-type: text/html; charset=UTF-8

Hello world!
```

As expected, both versions of the PHP engine worked nicely. PHP CGI version did generate the HTTP response header for me.

But note that the "Content-type" in PHP 7.3 is set to "UTF-8", which is different than PHP 5.6. See output from PHP 5.6:

```
>\php5.6\php-cgi Hello.php
Content-type: text/html
X-Powered-By: PHP/5.6.6

Hello world!
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction and Installation of PHP 7.3](#part0003.xhtml)

∟"php -a" - PHP Interactive Shell

This section provides a tutorial example on how to run the PHP engine as an interactive shell, php -a, which lets you to type in a PHP statement and see the result immediately on the screen.

In previous tutorial, I learned how to run the PHP engine to execute a PHP script stored in a file.

The PHP engine can also be used as an interactive shell, taking PHP script from the console and execute it one line at a time. interactively.

Here is a session of running the PHP engine as an interactive shell:

```
herong> \php\php -a

Interactive shell

php > print "I am tossing a coin...\n";
I am tossing a coin...
php > $coin = rand(0,1);
php > if ($coin==1) {
php {    print "   Head\n";
php { } else {
php {    print "   Tail\n";
php { }
   Head
php > exit

C:\herong>
```

Cool. This is really a good tool to help leaning PHP. Just typing in a PHP statement, and watching the result displayed immediately on the screen.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction and Installation of PHP 7.3](#part0003.xhtml)

∟Downloading and Installing PHP Documentation

This section provides a tutorial example on how to download and install PHP documentation in HTML format.

To help learning the PHP language and built-in extensions, we should also download the PHP documentation:

1\. Go to [php.net/download-docs.php](http://php.net/download-docs.php) and download the "tar.gz" format of the "English" and "Many HTML files" version. You will get a file called "php\_manual\_en.tar.gz" of 11,269,511 bytes.

2\. Unzip "php\_manual\_en.tar.gz" to \\php\\html folder.

3\. Open \\php\\html\\index.html in a Web browser and bookmark it.

![PHP Documentation - HTML Version](Images/image00229.jpeg)

PHP Documentation - HTML Version

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟PHP Script File Syntax

This chapter provides tutorial notes and example codes on PHP script file syntax. Topics include what tags to use to include a PHP code segment in a script file; script file processing rules; how to split 1 statement in multiple lines, how to enter comments into PHP scripts.

> [PHP Script Source Code File Format](#part0014.xhtml)
> 
> [PHP Script Processing Rules](#part0015.xhtml)
> 
> [PHP Statement Delimiter and Comments](#part0016.xhtml)

Takeaways:

*   PHP processing tags <?php ... ?> are used to include PHP code segments into PHP script files.
*   All non-PHP text segments are converted into PHP print statements before PHP execution.
*   All PHP code segments and converted print statements are merged into a single PHP code block for execution.
*   Semicolon ";" are used as PHP statement delimiters.
*   Comments can be entered in Perl, Java or C style into PHP code segments.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[PHP Script File Syntax](#part0013.xhtml)

∟PHP Script Source Code File Format

This section describes the PHP script source code file format - A text file with PHP code segments mixed into non-PHP text. The most common way to mix PHP codes is to use the PHP processing tag '?php'.

Like any other scripting language, PHP is used to transform text information from an input to an output by mixing PHP code segments in the input text. This input of mixed PHP code and non-PHP text is called PHP script source code, which is usually stored as a text file.

Since multiple PHP code segments can be mixed with non-PHP text, a PHP script source code will look like this:

```
text PHP_code text PHP_code text PHP_code ...
```

When you ask the PHP to process a PHP script source code, it will separate PHP code segments from the non-PHP text using following 3 default rules:

1\. PHP processing tag: <?php PHP\_code ?> - Everything included in the "?php" tag will be processed as PHP code. For example:

```
Hello <?php
   $name = "Herong";
   echo $name;
?>
, Nice to meet you!
```

2\. PHP processing tag shorthand: <? PHP\_code ?> - Everything included in the "?" tag will be processed as PHP code. For example:

```
Hello <?
   $name = "Herong";
   echo $name;
?>
, Nice to meet you!
```

3\. HTML "script" tag: <script language="php">PHP\_code</script> - Everything between the "script" starting tag and the "script" ending tag will be processed as PHP code. For example:

```
Hello <script language="php">
   $name = "Herong";
   echo $name;
</script>
, Nice to meet you!
```

The PHP processing tag is the most commonly used way to mixed PHP codes into non-PHP text to create a PHP script source code file. Since most PHP scripts are designed to generate Web pages, non-PHP text in a PHP script source code is made of mostly HTML tags. Here is an example of a PHP script source code that generates a simple Web page:

```
<html>
<head>
<title>Welcome Page</title>
</head>
<body>
<p>
Hello <?php
   $name = "Herong";
   echo $name;
?>
, Nice to meet you!
</p>
</body>
</html>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[PHP Script File Syntax](#part0013.xhtml)

∟PHP Script Processing Rules

This section describes the PHP script source code processing rules - all non-PHP text segments are converted into print statements and merged with PHP code segments to form a single code block.

As I mentioned in the previous section, a PHP script source code is a sequence non-PHP text segments and PHP code segments. The PHP engine will process the source code in 3 logical steps:

*   Converting each non-PHP text segment into a PHP code segment with a print statement.
*   Joining all PHP code segments into a single final PHP code block.
*   Executing the final PHP code block.

In other words, a PHP script source code can be viewed as a single PHP code block. All non-PHP text segments are just PHP print statements written in a special way.

PHP's processing rules are very similar to Active Server Page (ASP)'s processing rules.

Now let's see an example PHP script source code file:

```
<?php
/* HeadOrTail.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
*/ ?>
I am tossing a coin now. Guess what the result will be?
<?php $coin = rand(0,1); ?>
<?php if ($coin==1) { ?>
   Head
<?php } else { ?>
   Tail
<?php } ?>
```

If you process this script with the PHP engine, you will get:

```
herong> \php\php HeadOrTail.php

I am tossing a coin now. Guess what the result will be?
   Tail
```

Based on the PHP engine processing rules, the above script is identical to this script from the PHP engine process point of view:

```
<?php
/* HeadOrTailModified.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
*/
print "I am tossing a coin now. Guess what the result will be?\n";
$coin = rand(0,1);
if ($coin==1) {
   print "   Head\n";
} else {
   print "   Tail\n";
} ?>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[PHP Script File Syntax](#part0013.xhtml)

∟PHP Statement Delimiter and Comments

This section provides a tutorial example on how to write PHP statements and comment in PHP source code files. PHP uses semicolon ';' as the statement delimiter. Comments can be entered in Perl, Java, or C styles.

PHP uses semicolon ";" as the statement delimiter. PHP statements can be written in the source code file in different ways:

*   The most common way is to write one statement per one code line.
*   But you can split one statement into multiple code lines if you have a long statement.
*   You can also write multiple statements in one code line, if you want to.

If you want to enter comments into the PHP source code, you can do it in 3 ways:

*   Perl style: Using "#"
*   Java style: Using "//"
*   C style: Using "/\*" and "\*/"

Here is a tutorial example on how to write PHP statements and comments:

```
<?php
/* StatementSamples.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
*/

# The next 1 statement is written in 2 code lines.
print "I am tossing a coin now. "
   . "Guess what the result will be?\n";

/* I am using the rand() function to simulate the randomness of
tossing a coin. The rand(min,max) function returns a random integer
between the specified minimum number and maximum number.
-- This is a sample of C style comment
*/

# The next 1 statement is written in 1 code line.
$count = 0;
while ($count < 7) {
   # Next 2 statements are written in 1 code line.
   $count++; print "Round # $count:\n";

   $coin = rand(0,1);
   if ($coin==1) {
      print "   Head\n"; // Java style comment
   } else {
      print "   Tail\n"; # Perl style comment
   }
}
?>
```

There is no surprises in the output:

```
herong> \php\php StatementSamples.php

I am tossing a coin now. Guess what the result will be?
Round # 1:
   Tail
Round # 2:
   Tail
Round # 3:
   Head
Round # 4:
   Tail
Round # 5:
   Tail
Round # 6:
   Head
Round # 7:
   Tail
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟PHP Data Types and Data Literals

This chapter provides tutorial notes and example codes on PHP data types and data literals. Topics include 8 data types supported in PHP; data literals to provide data values in PHP code for different data types; integer and float value overflow conditions.

> [Data Types Supported in PHP](#part0018.xhtml)
> 
> [Data Literals Supported in PHP](#part0019.xhtml)
> 
> [Data Literals Examples for Integer, String and Other Data Types](#part0020.xhtml)
> 
> [Overflow of Integer and Float Values](#part0021.xhtml)

Takeaways:

*   PHP supports 8 data types: boolean, integer, float, string, array, object, resource, null.
*   PHP integer data type uses the 32-bit signed integer storage format.
*   PHP float data type uses the 64-bit floating-point number storage format, the IEEE 754 double-precision standard.
*   PHP sting data type uses the 8-bit byte storage format.
*   PHP array data type uses key-value pairs to manage array elements. PHP arrays are really associate arrays, maps or hash tables in other programming languages.
*   PHP handles integer value overflow conditions by automatically converting results to float data type.
*   PHP handles float value overflow conditions by automatically converting results to "infinite" or 0.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[PHP Data Types and Data Literals](#part0017.xhtml)

∟Data Types Supported in PHP

This section describes all 8 data types supported in PHP with a tutorial example showing how to use them: boolean, integer, float, string, array, object, resource, null.

PHP supports 8 data types:

*   boolean: It has only two literal values: 'true' and 'false'. I am not sure what is the storage size of a boolean data item.
*   integer: It is stored as signed integers with 32 bits. That means an integer data item can hold an integer value in the range of -2,147,483,648 and 2,147,483,647. Integer literals have 3 forms: decimal, octal (prefixed with '0'), and hexadecimal (prefixed with '0x').
*   float: It is stored as IEEE double floating point numbers with 64 bits. Float literals have the standard floating point number form.
*   string: It is a sequence of 8-bit characters. String literals have 3 forms: single quoted, double quoted, and heredoc syntax. These forms are very similar to Perl.
*   array: It stores an ordered map of pairs of keys and values. This is quite different than the array type used in other languages. Arrays in PHP are similar to associate arrays in Perl.
*   object: It stores an instance of a class.
*   resource: It represents an external resource like a file, or a database connection.
*   null: It represents a status of a variable in which no value is assigned the variable. Null type has only one literal value: 'null'.

Here is a tutorial sample PHP script that shows you all 8 data types:

```
<?php
/* DataTypeSamples.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
*/

$isValid = '1'==1; // boolean data type
print "\n Boolean data type - '1'==1 evaluation result: ".$isValid;

$yearDays = 365; // integer data type
print "\n Integer data type - Days in a year: ".$yearDays;

$equatorLength = 3.14159*2*6371; // float data type
print "\n Float data type - Length of the equator: ".$equatorLength;

$greetingMessage = "Hello Herong!"; // float data type
print "\n String data type - Greeting message: ".$greetingMessage;

$monthDays = array("Jan"=>31,"Feb"=>28,"Mar"=>31); // array data type
print "\n Array data type - Days in each month: "
   .$monthDays['Jan'].", ".$monthDays['Feb'].", ".$monthDays['Mar']
   ."...";

$currentTime = new DateTime(); // object data type
print "\n Object data type - Current time: "
   .$currentTime->format(DATE_ATOM);

$currentDirectory = opendir("."); // resource data type
print "\n Resource data type - First item in the current directory: "
   .readdir($currentDirectory);
closedir($currentDirectory);

$nothing = null; // null data type
print "\n Null data type - Null means nothing:".$nothing;
?>
```

If you run this sample script, you should get:

```
herong> \php\php DataTypeSamples.php

 Boolean data type - '1'==1 evaluation result: 1
 Integer data type - Days in a year: 365
 Float data type - Length of the equator: 40030.13978
 String data type - Greeting message: Hello Herong!
 Array data type - Days in each month: 31, 28, 31...
 Object data type - Current time: 2005-02-12T21:19:47-05:00
 Resource data type - First item in the current directory: .
 Null data type - Null means nothing:?>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[PHP Data Types and Data Literals](#part0017.xhtml)

∟Data Literals Supported in PHP

This section describes data literals to specify values for different data types: reserved key words; decimal, octal and hexadecimal numbers; floating point number format; single quoted, double quoted, and heredoc strings.

Data literals are ways to provide values for different data types in PHP source code. PHP data literals rules are summarized below:

1\. boolean data literals: Data literals for boolean data type are two reserved key words: true and false. Note that true and false are case in-sensitive - TRUE and FALSE are also valid boolean literals.

2\. integer data literals: Data literals for integer data type have 3 forms:

*   Decimal form: A sequence of decimal digits, 0 to 9, with the first digit being > 0. Integer data literals in decimal form can be prefixed with or without positive or negative signs. For example: 366, -42, 6371, ...
*   Octal form: A sequence of octal digits, 0 to 7, with the first digit being 0. Integer data literals in octal form can be prefixed with or without positive or negative signs. For example: 0556, -052, 014343, ...
*   Hexadecimal form: 0x followed by a sequence of hexadecimal digits, 0 to 9 and A to F, with the first digit being 0. Integer data literals in hexadecimal form can be prefixed with or without positive or negative signs. For example: 0x16E, -0x2A, 0x18E3, ...

3\. float data literals: Data literals for float data type are numeric values represented in signs and decimal digits with a decimal point and or exponential part. For example: 3.14159, 3e8, -1.25e-2, ...

4\. string data literals: Data literals for string data type have 3 forms:

*   Singled quoted form: A sequence of 8-bit characters enclosed in a pair of single quotes ''. String data literals in single quoted form are subject to 2 escape sequences (backslash substitutions), \\' and \\\\, to represent ' and \\. For example: 'Today\\'s Special:', 'Item Price Unit', 'Apples 3.49 kg', ...
*   Double quoted form: A sequence of 8-bit characters enclosed in a pair of double quotes "". String data literals in double quoted form are subject to a different set of escape sequences (backslash substitutions): \\", \\\\, \\t, \\r, \\n, \\$, \\ddd and \\xHH. \\ddd is used to represent any character in its octal value. \\xHH is used to represent any character in its hexadecimal value. String data literals in double quoted form are also subject to variable substitutions: $variableName, {$variableName}, or {$variableName\[$i\]\[$j\]}. For example: "Today's Special:", "Item\\tPrice\\tUnit", "Apples\\t3.49\\t\\x6B\\x67", "Eggs\\t$price\\tdoz\\145\\156", ...
*   Heredoc form: <<< followed by an identifier and a new line, then a sequence of 8-bit characters in one or more lines, and then the same identifier to end the literal. See the example given in the next tutorial.

5\. array data literals: There are no data literals for array data type. Arrays are created by using the array constructor, array() function, or the array element notation, $arrayName\[$key\].

6\. object data literals: There are no data literals for object data type. Objects are created by class constructors.

7\. resource data literals: There are no data literals for resource data type. Resources are created by using PHP built-in functions.

8\. null data literal: Data literal for null data type is 1 reserved key words: null. Note that null is case in-sensitive - NULL is the same as null.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[PHP Data Types and Data Literals](#part0017.xhtml)

∟Data Literals Examples for Integer, String and Other Data Types

This section provides a tutorial example on how to use data literals for various data types: TRUE, FALSE, and NULL; decimal, octal and hexadecimal numbers; floating point number format; single quoted, double quoted, and heredoc strings.

To help us understand better on how to use data literals for various data types, I wrote the following tutorial sample script:

```
<?php
/* DataLiteralSamples.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
*/

print "\n\n Boolean data literals: ";
$isGood = TRUE;
$isBad = false;
print "\n    TRUE: ".$isGood;
print "\n    false: ".$isBad;

print "\n\n Integer data literals in decimal form: ";
$leapYearDays = 366;
$supercoolWater = -42;
$earthRadius = 6371;
print "\n    366: ".$leapYearDays;
print "\n    -42: ".$supercoolWater;
print "\n    6371: ".$earthRadius;

print "\n\n Integer data literals in octal form: ";
$leapYearDays = 0556;
$supercoolWater = -052;
$earthRadius = 014343;
print "\n    0556: ".$leapYearDays;
print "\n    -052: ".$supercoolWater;
print "\n    014343: ".$earthRadius;

print "\n\n Integer data literals in hexadecimal form: ";
$leapYearDays = 0x16E;
$supercoolWater = -0x2A;
$earthRadius = 0x18E3;
print "\n    0x16E: ".$leapYearDays;
print "\n    -0x2A: ".$supercoolWater;
print "\n    0x18E3: ".$earthRadius;

print "\n\n Float data literals in hexadecimal form: ";
$pi = 3.14159;
$lightSpeed = 3e8;
$gdpGrowth = -1.25e-2;
print "\n    3.14159: ".$pi;
print "\n    3e8: ".$lightSpeed;
print "\n    2.7322e1: ".$gdpGrowth;

print "\n\n String data literals in single quoted form: ";
$title = 'Today\'s Special:';
$headers = 'Item\tPrice\tUnit';
$apples = 'Apples\t3.49\tkg';
$eggs = 'Eggs\t1.99\tdozen';
print "\n    ".$title;
print "\n    ".$headers;
print "\n    ".$apples;
print "\n    ".$eggs;

print "\n\n String data literals in double quoted form: ";
$title = "Today\'s Special:";
$headers = "Item\tPrice\tUnit";
$apples = "Apples\t3.49\t\x6B\x67";
$price = 1.99;
$eggs = "Eggs\t$price\tdoz\145\156";
print "\n    ".$title;
print "\n    ".$headers;
print "\n    ".$apples;
print "\n    ".$eggs;

print "\n\n String data literals in heredoc form: ";
$todaySpecial = <<<EOS
    Today's Special:
    Item        Price   Unit
    Apples      3.49    kg
    Eggs        1.99    dozen
EOS;
print "\n".$todaySpecial;

print "\n\n Null data literals: ";
$nothing = NULL;
$void = null;
print "\n    NULL: ".$nothing;
print "\n    null: ".$void;
?>
```

If you run this sample script, you should get:

```
herong> \php\php DataLiteralSamples.php

 Boolean data literals:
    TRUE: 1
    false:

 Integer data literals in decimal form:
    366: 366
    -42: -42
    6371: 6371

 Integer data literals in octal form:
    0556: 366
    -052: -42
    014343: 6371

 Integer data literals in hexadecimal form:
    0x16E: 366
    -0x2A: -42
    0x18E3: 6371

 Float data literals in hexadecimal form:
    3.14159: 3.14159
    3e8: 300000000
    2.7322e1: -0.0125

 String data literals in single quoted form:
    Today's Special:
    Item\tPrice\tUnit
    Apples\t3.49\tkg
    Eggs\t1.99\tdozen

 String data literals in double quoted form:
    Today\'s Special:
    Item        Price   Unit
    Apples      3.49    kg
    Eggs        1.99    dozen

 String data literals in heredoc form:
    Today's Special:
    Item        Price   Unit
    Apples      3.49    kg
    Eggs        1.99    dozen

 Null data literals:
    NULL:
    null:
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[PHP Data Types and Data Literals](#part0017.xhtml)

∟Overflow of Integer and Float Values

This section describes what an arithmetic overflow condition, how the PHP 5 engine handles integer and float value overflow, how to write a PHP code to detect overflow conditions.

**What is overflow?** Overflow or arithmetic overflow is a condition that occurs when a calculation produces a result that is greater in magnitude than what a given data type can store or represent.

When applying this definition to PHP integer data type, we can say that: PHP integer value overflow is a condition when an integer operation produces an integer outside the signed 32-bit integer value range.

When applying this definition to PHP float data type, we can say that: PHP float value overflow is a condition when a float operation produces a float value outside the 64-bit floating point number value range.

According to the PHP manual, here is how the PHP 5 engine handles arithmetic overflow conditions:

*   When integer value overflow happens at the upper limit of the integer value range, the resulting integer value will be automatically converted to float data type.
*   When integer value overflow happens at the lower limit of the integer value range, the resulting integer value will be automatically converted to float data type.
*   When float value overflow happens at the upper limit of the exponent value range, the resulting float value will be automatically converted to a special value called "infinite".
*   When float value overflow happens at the lower limit of the exponent value range, the resulting float value will be automatically converted to 0. This is also called underflow.

Note that in all arithmetic overflow cases, PHP will not abandon the operation and raise any runtime errors. So if you are writing a PHP code dealing with numbers that close to integer or float value range limits, you need to be very careful and write extra code to detect overflow conditions yourself.

To help us understand what are integer and float value range and how to detect arithmetic overflow conditions, I wrote this tutorial sample PHP script:

```
<?php
/* NumericOverflow.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
*/
print "\n Signed 32-bit integer positive overflow test:\n";
$integerLimit =  0x7FFFFFFF;
$integerOverflow = $integerLimit + 1;
print "    Integer upper limit: "; var_dump($integerLimit);
print "   Upper limit overflow: "; var_dump($integerOverflow);

print "\n Signed 32-bit integer positive overflow test:\n";
$integerLimit =  -0x7FFFFFFF - 1;
$integerOverflow = $integerLimit - 1;
print "    Integer lower limit: "; var_dump($integerLimit);
print "   Lower limit overflow: "; var_dump($integerOverflow);

print "\n 64-bit floating point number overflow test:\n";
$floatLimit = 1.0;
$floatOverflow = $floatLimit*10;
while (!is_infinite($floatOverflow)) {
   $floatLimit *= 10;
   $floatOverflow = $floatLimit*10;
}
print "   Float high limit: "; var_dump($floatLimit);
print "     Float overflow: "; var_dump($floatOverflow);

print "\n 64-bit floating point number underflow test:\n";
$floatLimit = 1.0;
$floatUnderflow = $floatLimit/10;
while (!$floatUnderflow==0) {
   $floatLimit /= 10;
   $floatUnderflow = $floatLimit/10;
}
print "   Float low limit: "; var_dump($floatLimit);
print "   Float underflow: "; var_dump($floatUnderflow);
?>
```

If you run this sample script, you should get:

```
herong> \php\php NumericOverflow.php

 Signed 32-bit integer positive overflow test:
    Integer upper limit: int(2147483647)
   Upper limit overflow: float(2147483648)

 Signed 32-bit integer positive overflow test:
    Integer lower limit: int(-2147483648)
   Lower limit overflow: float(-2147483649)

 64-bit floating point number overflow test:
   Float high limit: float(1.0E+308)
     Float overflow: float(INF)

 64-bit floating point number underflow test:
   Float low limit: float(9.88131291682E-324)
   Float underflow: float(0)
```

The result tells me that on my computer:

*   PHP integer value range is from -2147483648 to 2147483647.
*   PHP float value range is from 9.88131291682E-324 to 1.0E+308 approximately.
*   Of course, float values have another valid range on the negative side. It should be from -1.0E+308 to -9.88131291682E-324 approximately.

Exercise: Modify my sample script to find out the negative float value range.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Variables, References, and Constants

This chapter provides tutorial notes and example codes on PHP variables, references, and constants. Topics include how to name variables; assigning data values to variables; creating the reference of a variable; using variable variable names; using string expressions as variable names; defining constant names to values; retrieving the value from a constant.

> [Variables and Assignment Operations](#part0023.xhtml)
> 
> [References and Variables](#part0024.xhtml)
> 
> [Variable Variable Name - Name Variables with Expressions](#part0025.xhtml)
> 
> [Constant and define() Function](#part0026.xhtml)

Takeaways:

*   PHP variables are typeless. Values of different data types can be assigned to the same variable.
*   PHP variable names starts with $ sign.
*   & operator returns the reference of a variable.
*   The reference of a variable can be assigned to a new variable to make an alias to the original variable.
*   A variable name can represented as a string expression. This is called variable variable name.
*   Functions define() defines a constant with the constant name and the constant value.
*   Only scalar data type values can be used as constant values.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Variables, References, and Constants](#part0022.xhtml)

∟Variables and Assignment Operations

This section describes what is a variable, variable names prefixed with $, 'set' and 'unset' states of a variable, assigning data to variables, var\_dump($var) to print variable information.

**What is a variable?** A variable is an identifier for a piece of data stored in memory during the program execution. In PHP, variables are used under these basic rules:

1\. A variable name in PHP must be prefixed with a "$" sign. Perl has a similar rule for scale variables.

2\. Variable names are case sensitive. So $address and $Address refer to two different variables.

3\. Variables in PHP are typeless. Therefor there is no variable type declaration statements in PHP. Any variable can be used as the identifier for any data type.

4\. A variable has 2 states: "set" and "unset". A variable is in the "set" state, if a piece of data has been assigned to it. A variable is in the "unset" state, if there is no data assigned to it.

5\. Assignment operations (coded by the assignment operator, =) can be used to assign data to variables.

6\. The unset($var) function can be used to remove the assigned data from the given variable.

7\. Variables can used in any operations like data literals in PHP source code. If a variable with data assigned is used in an operation, the assigned data value will be used for the operation. If a variable with no data assigned is used in an operation, NULL will be used for the operation.

8\. There are some special characters that you should not use them as part of a variable name, ' ', '$', '\[', '\]', '{', '}', ...

PHP has a nice built-in function, var\_dump($var), that prints out detailed information about the specified variable.

To show you some of variable rules mentioned above, I wrote the following PHP script, VariableTest.php:

```
<?php
#  VariableTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "\nVariable assignments:\n";

   $u; # Not assigning to any data
   print "\n   \$u: "; var_dump($u);

   $b = TRUE; # Assigning a boolean
   print "\n   \$b: "; var_dump($b);

   $i = 777; # Assigning an integer
   print "\n   \$i: "; var_dump($i);

   $f = 3.14; # Assigning a float
   print "\n   \$f: "; var_dump($f);

   $s = "Hello Herong"; # Assigning a string
   print "\n   \$s: "; var_dump($s);

   $a = array("Jan"=>31,"Feb"=>28); # Assigning an array
   print "\n   \$a: "; var_dump($a);

   $o = new DateTime(); # Assigning an object
   print "\n   \$o: "; var_dump($o);

   $r = opendir("."); # Assigning a resource
   print "\n   \$r: "; var_dump($r);

   $n = NULL; # Assigning NULL
   print "\n   \$n: "; var_dump($n);
?>
```

If you run this sample script, you should get:

```
herong> \php\php VariableTest.php

Variable assignments:

   $u: NULL

   $b: bool(true)

   $i: int(777)

   $f: float(3.14)

   $s: string(12) "Hello Herong"

   $a: array(3) {
  ["Jan"]=>
  int(31)
  ["Feb"]=>
  int(28)
  ["Mar"]=>
  int(31)
}

   $o: object(DateTime)#1 (0) {
}

   $r: resource(4) of type (stream)

   $n: NULL
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Variables, References, and Constants](#part0022.xhtml)

∟References and Variables

This section describes what is a reference, creating references with & operator, assigning references to variables, removing reference links with unset($var) function.

**What is a reference?** A reference is an alias of a variable. PHP supports references in a very similar way as the Perl language. Here are some basic rules about using references in PHP:

1\. To create a reference of a given variable, you need to use the reference operator: &. For example, &$title creates a reference of variable $title.

2\. Reference can be assigned to another variable using the assignment operator: =. For example, $subject = &$title assigns the reference of variable $title to variable $subject.

3\. The variable holding the reference is an alias of the original variable and behaves the same way as the original variable. For example, $subject = &$title; var\_dump($subject); prints information of the data assigned to variable $title.

4\. If the original variable is assigned to a new data, the reference variable is automatically assigned to that new data. For example, $subject = &$title; $title = "New String"; assigns "New String" to both $subject and $title.

5\. If the reference variable is assigned to a new data, the original variable is automatically assigned to that new data. For example, $subject = &$title; $subject = "New Text"; assigns "New Text" to both $subject and $title.

6\. Multiple reference variables can be created by assigning the reference to multiple variables. For example, $subject = &$title; $topic = &$title; assigns the reference of $title to both $subject and $topic.

7\. Actually, original variable and its reference variables can all be viewed as references to the assigned data shared by all of them. For example, $subject = &$title; $topic = &$title; $topic = "New Message"; creates 3 variables referring to the same data "New Message".

8\. To remove the reference link between a variable and its assigned data, you need to use the unset($var) function. For example; $title = "New String"; unset($title); removes the reference link between $title and "New String". $title is in the "unset" states now.

9\. If multiple variables are referencing the same data, removing the reference link on one variable does not affect other variables. For example, $subject = &$title; $topic = &$title; $topic = "New Message"; unset($topic); removes the reference link on $topic, but $subject and $title are still referring to "New Message".

10\. If multiple variables are referencing the same data, assigning a new reference to a new data to one variable does not affect other variables. For example, $subject = &$title; $topic = &$title; $topic = "New Message"; $topic = &$name; assigns the reference of $name to $topic, but $subject and $title are still referring to "New Message".

To show you some of reference rules mentioned above, I wrote the following PHP script, ReferenceTest.php:

```
<?php
#  ReferenceTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $title;
   print "\n \$title is not assigned to anything:\n";
   print "    \$title: "; var_dump($title);

   $subject = &$title;
   print "\n \$subject is an alias of $title:\n";
   print "    \$subject: "; var_dump($subject);
   print "    \$title: "; var_dump($title);

   $subject = "Herong's PHP Book";
   print "\n \$subject is assigned with a string:\n";
   print "    \$title: "; var_dump($title);
   print "    \$subject: "; var_dump($subject);

   $title = "Herong's Programming Book";
   print "\n \$title is reassigned with a new string:\n";
   print "    \$title: "; var_dump($title);
   print "    \$subject: "; var_dump($subject);

   $topic = &$subject;
   print "\n \$topic is added as the third reference variable:\n";
   print "    \$title: "; var_dump($title);
   print "    \$subject: "; var_dump($subject);
   print "    \$topic: "; var_dump($topic);

   unset($subject);
   print "\n \$subject's reference link is removed:\n";
   print "    \$title: "; var_dump($title);
   print "    \$subject: "; var_dump($subject);
   print "    \$topic: "; var_dump($topic);


   $name = "Herong's Tutorial Book";
   $title = &$name;
   print "\n \$title is assigned to a new reference:\n";
   print "    \$title: "; var_dump($title);
   print "    \$subject: "; var_dump($subject);
   print "    \$topic: "; var_dump($topic);
   print "    \$name: "; var_dump($name);
?>
```

If you run this sample script in PHP 7 and higher, you should get output with some "Notice" messages. This is because now the default message level is set to E\_NOTICE. You can change the setting or modify the code to make sure all variables are defined before using them.

```
herong> \php-7.3\php ReferenceTest.php

 $title is not assigned to anything:
    $title: PHP Notice:  Undefined variable: title in
       C:\herong\ReferenceTest.php on line 7

Notice: Undefined variable: title in
   C:\herong\ReferenceTest.php on line 7
NULL

 $subject is an alias of :
    $subject: NULL
    $title: NULL

 $subject is assigned with a string:
    $title: string(17) "Herong's PHP Book"
    $subject: string(17) "Herong's PHP Book"

 $title is reassigned with a new string:
    $title: string(25) "Herong's Programming Book"
    $subject: string(25) "Herong's Programming Book"

 $topic is added as the third reference variable:
    $title: string(25) "Herong's Programming Book"
    $subject: string(25) "Herong's Programming Book"
    $topic: string(25) "Herong's Programming Book"

 $subject's reference link is removed:
    $title: string(25) "Herong's Programming Book"
    $subject: PHP Notice:  Undefined variable: subject in
       C:\herong\ReferenceTest.php on line 33

Notice: Undefined variable: subject in
   C:\herong\ReferenceTest.php on line 33
NULL
    $topic: string(25) "Herong's Programming Book"

 $title is assigned to a new reference:
    $title: string(22) "Herong's Tutorial Book"
    $subject: PHP Notice:  Undefined variable: subject in
       C:\herong\ReferenceTest.php on line 41

Notice: Undefined variable: subject in
   C:\herong\ReferenceTest.php on line 41
NULL
    $topic: string(25) "Herong's Programming Book"
    $name: string(22) "Herong's Tutorial Book"
```

If you run this sample script in PHP 5 and lower, you should get output without any "Notice" message:

```
herong> \php-5.6\php ReferenceTest.php

 $title is not assigned to anything:
    $title: NULL

 $subject is an alias of :
    $subject: NULL
    $title: NULL

 $subject is assigned with a string:
    $title: string(17) "Herong's PHP Book"
    $subject: string(17) "Herong's PHP Book"

 $title is reassigned with a new string:
    $title: string(25) "Herong's Programming Book"
    $subject: string(25) "Herong's Programming Book"

 $topic is added as the third reference variable:
    $title: string(25) "Herong's Programming Book"
    $subject: string(25) "Herong's Programming Book"
    $topic: string(25) "Herong's Programming Book"

 $subject's reference link is removed:
    $title: string(25) "Herong's Programming Book"
    $subject: NULL
    $topic: string(25) "Herong's Programming Book"

 $title is assigned to a new reference:
    $title: string(22) "Herong's Tutorial Book"
    $subject: NULL
    $topic: string(25) "Herong's Programming Book"
    $name: string(22) "Herong's Tutorial Book"
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Variables, References, and Constants](#part0022.xhtml)

∟Variable Variable Name - Name Variables with Expressions

This section describes what is a variable variable name, storing the variable name in another variable, naming variables with expressions, using any expressions as variable names.

What is a **Variable Variable Name:** A variable variable name is a variable name that is stored inside another variable. Normally, a variable name is a static string. But sometimes, you want to store a variable name inside another variable to be able to participate in operations. PHP supports variable variable names with following basic rules:

1\. If the name of the original variable is stored in a different variable, you can use the $$var notation to identify the original variable in your PHP source code. For example, $variableName = "title"; $$variableName represents the variable $title.

2\. If the name of the original variable can be calculated by an expression, you can use the ${exp} notation to identify the original variable in your PHP source code. For example, $variableName = "title"; ${$variableName."\_1"} represents the variable $title\_1.

3\. Variables with variable names can be assigned with new data like normal variables. For example, $variableName = "title"; $$variableName = "Herong's PHP Book"; assigns "Herong's PHP Book" to $title.

4\. Variables with variable names can be used in any operations like normal variables. $variableName = "title"; $$variableName = "Herong's PHP Book"; print($$variableName." is free"); prints "Herong's PHP Book is free".

5\. If you use an expression as the variable name, the result of the expression will be automatically converted to a string, which will be used as the variable name. With this automatic conversion, anything can be used as a variable name. Even an empty string can be used as a variable name, ${""} is a perfect variable expression.

Now let's look at my tutorial example below to confirm some rules mentioned above:

```
<?php
#  VariableVariableName.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $variableName = "title";
   $$variableName = "Herong's PHP Book";
   print "\n \$\$variableName is assigned to a message:\n";
   print "    \$variableName: "; var_dump($variableName);
   print "    \$\$variableName: "; var_dump($$variableName);
   print "    \$title: "; var_dump($title);

   $variableName = "";
   $$variableName = "Herong's Programming Book";
   print "\n \$variableName contains an empty string:\n";
   print "    \$variableName: "; var_dump($variableName);
   print "    \$\$variableName: "; var_dump($$variableName);
   print "    \${''}: "; var_dump(${''});

   $variableName = NULL;
   $$variableName = "Herong's Tutorial Book";
   print "\n \$variableName contains the NULL:\n";
   print "    \$variableName: "; var_dump($variableName);
   print "    \$\$variableName: "; var_dump($$variableName);
   print "    \${NULL}: "; var_dump(${NULL});

   $variableName = 1.0/3.3;
   $$variableName = "Herong's Free Book";
   print "\n \$variableName contains a float number:\n";
   print "    \$variableName: "; var_dump($variableName);
   print "    \$\$variableName: "; var_dump($$variableName);
   print "    \${1.0/3.3}: "; var_dump(${1.0/3.3});
?>
```

If you run this sample script, you should get:

```
herong> \php\php VariableVariableName.php

 $$variableName is assigned to a message:
    $variableName: string(5) "title"
    $$variableName: string(17) "Herong's PHP Book"
    $title: string(17) "Herong's PHP Book"

 $variableName contains an empty string:
    $variableName: string(0) ""
    $$variableName: string(25) "Herong's Programming Book"
    ${''}: string(25) "Herong's Programming Book"

 $variableName contains the NULL:
    $variableName: NULL
    $$variableName: string(22) "Herong's Tutorial Book"
    ${NULL}: string(22) "Herong's Tutorial Book"

 $variableName contains a float number:
    $variableName: float(0.30303030303)
    $$variableName: string(18) "Herong's Free Book"
    ${1.0/3.3}: string(18) "Herong's Free Book"
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Variables, References, and Constants](#part0022.xhtml)

∟Constant and define() Function

This section describes what is a constant, define() function defines a constant name to a value, constant value can retrieved by the name directly or by the constant() function, any string can be used as constant name.

**What Is a Constant**? A constant is an identifier for a data value. Once defined, the data value identified by a constant can not be changed. PHP supports constants with following basic rules:

1\. A constant must be defined with the define(name, value) function. For example, define("PI", 3.14159); defines a constant named as PI to a value of 3.14159.

2\. To retrieve the value defined in a constant, you can use the constant name directly in any expression. For example, define("PI", 3.14159); $area = PI \* $radius \* $radius; uses the value define in PI to calculate the area.

3\. You are allowed to use any string for the constant name. For example, define("LONG PI", 3.14159265359); defines a constant named as 'LONG PI' to a value of 3.14159265359. But using special characters in constant names are not recommended.

4\. If a constant name contains special characters, you need to use the constant(name) function to retrieve the value defined in the constant. For example, define("LONG PI", 3.14159265359); $area = constant("LONG PI") \* $radius \* $radius; uses the value defined in "LONG PI" to calculate the area.

5\. If you want to know if there is a constant defined for a given constant name, you can use the define(name) function. For example, define("LONG PI", 3.14159265359); defined("LONG PI"); returns TRUE. And defined("LONG RI") returns FALSE.

6\. Constants can be defined with only value of scalar data types: boolean, integer, float, and string.

7\. The PHP engine provides a number of pre-defined (built-in) constants. For example, \_\_FILE\_\_, \_\_LINE\_\_, PHP\_OS, PHP\_VERSION, PHP\_INT\_MAX, DIRECTORY\_SEPARATOR, ...

Now let's look at my tutorial example below to confirm some rules mentioned above:

```
<?php
#  ConstantTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "\n PI is not defined as a constant:\n";
   print "    PI: "; var_dump(PI);

   define("PI", 3.14159);
   print "\n PI is defined to a constant now:\n";
   print "    PI: "; var_dump(PI);

   define("LONG PI", 3.14159265359);
   print "\n LONG PI is defined to a constant now:\n";
   print "    LONG PI: "; var_dump(constant("LONG PI"));

   print "\n LONG RI is not defined as a constant:\n";
   print "    LONG PI: "; var_dump(defined("LONG PI"));
   print "    LONG RI: "; var_dump(defined("LONG RI"));

   print "\n Trying to define DAYS to an array:\n";
   define("DAYS", array("Jan"=>31,"Feb"=>28));
   print "    DAYS: "; var_dump(DAYS);

   print "\n PHP built-in constants:\n";
   print "    __FILE__: "; var_dump(__FILE__);
   print "    __LINE__: "; var_dump(__LINE__);
   print "    PHP_OS: "; var_dump(PHP_OS);
   print "    PHP_VERSION: "; var_dump(PHP_VERSION);
   print "    PHP_INT_MAX: "; var_dump(PHP_INT_MAX);
   print "    DIRECTORY_SEPARATOR: "; var_dump(DIRECTORY_SEPARATOR);
?>
```

If you run this sample script, you should get:

```
herong> \php\php ConstantTest.php

 PI is not defined as a constant:
    PI: string(2) "PI"

 PI is defined to a constant now:
    PI: float(3.14159)

 LONG PI is defined to a constant now:
    LONG PI: float(3.14159265359)

 LONG RI is not defined as a constant:
    LONG PI: bool(true)
    LONG RI: bool(false)

 Trying to define DAYS to an array:

Warning: Constants may only evaluate to scalar values in
C:\herong\ConstantTest.php on line 20
    DAYS: string(4) "DAYS"

 PHP built-in constants:
    __FILE__: string(43) "C:\herong\ConstantTest.php"
    __LINE__: int(25)
    PHP_OS: string(5) "WINNT"
    PHP_VERSION: string(5) "5.0.4"
    PHP_INT_MAX: int(2147483647)
    DIRECTORY_SEPARATOR: string(1) "\"
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Expressions, Operations and Type Conversions

This chapter provides tutorial notes and example codes on PHP expressions and operations. Topics include writing expressions with data literals, variables, and operations; bitwise, arithmetic, comparison, logical, string, and assignment operations; precedence of operations; data type automatic conversions.

> [What Is an Expression](#part0028.xhtml)
> 
> [What Is an Operation](#part0029.xhtml)
> 
> [Precedence of Operations](#part0030.xhtml)
> 
> [Data Type Automatic Conversion](#part0031.xhtml)

Takeaways:

*   PHP supports 6 basic types of operations: bitwise, arithmetic, comparison, logical, string, and assignment operations.
*   PHP performs automatic type conversion, if an operand has a data type that does match the operator.
*   Write your expressions properly with operand data types match operators to avoid automatic type conversion.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Expressions, Operations and Type Conversions](#part0027.xhtml)

∟What Is an Expression

This section provides an introduction of what is an expression. A data literal or a variable is a simple expression. A single operation or a group of multiple operations is a complex express.

**What Is an Expression?** Giving a precise single definition of an expression is not an easy task. So I will try to define it in a recursive way:

1\. A simple expression is a presentation of a data value like, a literal, a variable, an element of an array, or a function call.

2\. A complex expression is a presentation of a data value returned from an operation represented by an operator, and one or two expressions as operands. The operation will result a new data value.

If you apply rule #2 recursively, an expression may contain multiple operations in a sequence. When this happens, operations must be carried out in an order defined by the following rules:

A. The operation enclosed in a pair of parentheses must be carried out before an operation outside the parentheses.

B. The operation with a higher precedence must be carried out before an operation with lower precedence.

C. The operation on the left must be carried out before the operation on the right.

D. Rule A must be applied before Rule B, which must be applied before Rule C.

Examples of expressions:

```
   "Hello world!"   # Simple expression - a String literal
   777              # Simple expression - an Integer literal
   $author          # Simple expression - a variable
   getdate()        # Simple expression - a function call

   7*9.99              # Complex expression - an arithmetic operation
   "Hello ".$author    # Complex expression - a string concatenation
   (7+2)*9.99 > 50     # Complex expression - multiple operations
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Expressions, Operations and Type Conversions](#part0027.xhtml)

∟What Is an Operation

This section describes what is an operation - a process that takes one or two operands and returns a result based on certain processing rule represented by the operator.

**What Is an Operation?** An operation is a process that takes one or two operands and returns a result based on certain processing rule represented by the operator. PHP supports most types of operations used in other programming languages:

1\. Bitwise Operations: and ($a & $b), or ($a | $b), xor ($a ^ $b), not (~ $a), shift left ($a << $s), and shift right ($a >> $s).

2\. Incrementing/Decrementing Operations: pre-increment (++$a), post-increment ($a++), pre-decrement (--$a), and post-decrement ($a--).

3\. Arithmetic Operations: negation (-$a), addition ($a + $b), subtraction ($a - $b), multiplication ($a \* $b), division ($a / $b), and modulus ($a % $b).

4\. Comparison Operations: equal ($a == $b), identical ($a === $b), not equal ($a != $b, $a <> $b), not identical ($a !== $b), less than ($a < $b), greater than ($a > $b), less than or equal ($a <= $b), and greater than or equal ($a >= $b).

5\. Logical Operations: and ($a and $b, $a && $b), or ($a or $b, $a || $b), xor ($a xor $b), and not (!$a).

6\. String Operation: concatenation ($a . %b).

7\. Assignment Operations: assignment ($a = %b), addition with assignment ($a += $b), subtraction with assignment ($a -= $b), multiplication with assignment ($a \*= $b), division with assignment ($a /= $b), modulus with assignment ($a %= $b), and concatenation with assignment ($a .= %b).

To help us understand different types of operations, I wrote the following PHP script, OperationTest.php:

```
<?php
#  OperationTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "\n Bitwise Operations:\n";
   print "    0x00FF & 0x3210: " . (0x00FF & 0x3210) . "\n";
   print "    0x0001 | 0x0010: " . (0x0001 | 0x0010) . "\n";
   print "    0x0001 << 4: " . (0x0001 << 4) . "\n";
   print "    0x0100 >> 4: " . (0x0100 >> 4) . "\n";

   print "\n Incrementing/Decrementing Operations:\n";
   $a = 10; $b = ++$a * 2;
   print "    \$b = ++\$a * 2: $a, $b\n";
   $a = 10; $b = $a++ * 2;
   print "    \$b = \$a++ *2: $a, $b\n";

   print "\n Arithmetic Operations:\n";
   $a = 9; $b = 4;
   print "    \$a * \$b: ". $a * $b . "\n";
   print "    \$a * \$b: ". $a / $b . "\n";
   print "    \$a * \$b: ". $a % $b . "\n";

   print "\n Comparison Operations:\n";
   $a = 9; $b = 4;
   print "    \$a > \$b: ". ($a > $b) . "\n";
   print "    \$a < \$b: ". ($a < $b) . "\n";

   print "\n Logical Operations:\n";
   $a = 9; $b = 4; $c = 1;
   print "    \$a > \$b && \$b > \$c: ". ($a > $b && $b > $c) . "\n";

   print "\n String Operation:\n";
   $name = "Herong"; $greeting = "Hello";
   print "    \$greeting . \$name: ". ($greeting . $name) . "\n";

   print "\n Assignment Operation:\n";
   print "    \$name=\"Herong\": ". ($name="Herong") . "\n";
?>
```

If you run this sample script, you should get:

```
herong> \php\php OperationTest.php

 Bitwise Operations:
    0x00FF & 0x3210: 16
    0x0001 | 0x0010: 17
    0x0001 << 4: 16
    0x0100 >> 4: 16

 Incrementing/Decrementing Operations:
    $b = ++$a * 2: 11, 22
    $b = $a++ *2: 11, 20

 Arithmetic Operations:
    $a * $b: 36
    $a * $b: 2.25
    $a * $b: 1

 Comparison Operations:
    $a > $b: 1
    $a < $b:

 Logical Operations:
    $a > $b && $b > $c: 1

 String Operation:
    $greeting . $name: HelloHerong

 Assignment Operation:
    $name="Herong": Herong
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Expressions, Operations and Type Conversions](#part0027.xhtml)

∟Precedence of Operations

This section provides the order of precedence for operations commonly used in PHP. Operations in a complex expression must be evaluated according to the order of operation precedence.

In the previous section, we learned that operations in a complex expression must be evaluated according to the order of operation precedence. The following table shows you the relative order of precedence for some commonly used operations:

```
Precedence   Operations       Notes
16           (...)            Operation group
15           ++ --            Increment/decrement
14           ~ -              Unary negation
13           !                Logical not
12           * / %            Multiplication, Division, ...
11           + -              Addition and Subtraction
10           .                String concatenation
9            << >>            Bitwise shift
8            < > <= >=        Comparisons
7            == != <> === !== Comparisons
6            &                Bitwise and
5            ^                Bitwise xor
4            |                Bitwise or
3            && And           Logical and
2            xor              Logical xor
1            || Or            Logical or
0            = += -= ...      Assignments
```

Remember that:

*   Operations with higher precedence values must be evaluated first.
*   Operations of the same precedence value must be evaluated from left to right.

To show you some of reference rules mentioned above, I wrote the following PHP script, PrecedenceTest.php:

```
<?php
#  PrecedenceTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "\n Arithmetic, comparison and logical Operations:\n";
   print "    : ". (1 + 2 * 3 / 4) ."\n";
   print "    : ". (1 + 2 * 3 / 4 < 5 != FALSE) ."\n";
   print "    : ". (1 + 2 * 3 / 4 < 5 != FALSE || 6 < 7) ."\n";

   print "\n Operations with groups:\n";
   print "    : ". (((1 + (2 * 3 / 4) < 5) != FALSE) || 6 < 7) ."\n";
   print "    : ". ((1 + (2 * 3 / 4) < 5) != (FALSE || 6 < 7)) ."\n";

   print "\n Bitwise Operations:\n";
   print "    : " . (0x0001 | 0x00FF & 0x3210 << 4) . "\n";
   print "    : " . ((0x0001 | 0x00FF) & 0x3210 << 4) . "\n";
   print "    : " . (0x0001 | (0x00FF & 0x3210) << 4) . "\n";
   print "    : " . (0x0001 | 0x00FF & (0x3210 << 4)) . "\n";
?>
```

If you run this sample script, you should get:

```
herong> \php\php PrecedenceTest.php

 Arithmetic, comparison and logical Operations:
    : 2.5
    : 1
    : 1

 Operations with groups:
    : 1
    :

 Bitwise Operations:
    : 1
    : 0
    : 257
    : 1
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Expressions, Operations and Type Conversions](#part0027.xhtml)

∟Data Type Automatic Conversion

This section provides rules on how operands are converted to data types required by the operation. PHP always finds a way to convert data from any type to any other type.

When the PHP evaluating an operation, it will automatically convert the data type of an operand if it does not match the data type required by the operator. Here are some basic data type automatic conversion rules:

*   For logical operations, NULL, 0, or "" will be converted to FALSE. Any strings that can be parsed to 0 will also be converted to FALSE. Other values will be converted to TRUE.
*   For arithmetic operations, strings will be parsed into numeric values. TRUE will be converted to 1. FALSE will be converted to 0.
*   For comparison operations, if one operand is a numeric value, the other operand will be converted to a numeric value for a numeric comparison. If both operands are strings, it will be a string comparison.
*   For string operations, NULL will be converted to "". TRUE will be converted to "1". FALSE will be converted to "". Numeric values will be converted to decimal presentations.

To show you some of these rules, I wrote the following sample PHP script, TypeAutoConversion.php:

```
<?php
#  TypeAutoConversion.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "\n Logical operations:\n";
   print "    NULL==FALSE: "; var_dump(NULL==FALSE);
   print "    0==FALSE: "; var_dump(0==FALSE);
   print "    \"\"==FALSE: "; var_dump(""==FALSE);
   print "    \"0\"==FALSE: "; var_dump("0"==FALSE);
   print "    \"0 - zero\"==TRUE: "; var_dump("0 - zero"==TRUE);
   print "    \"zero\"==TRUE: "; var_dump("zero"==TRUE);

   print "\n Logical operations:\n";
   print "    3.14 * \"2.0\": "; var_dump(3.14 * "2.0");
   print "    3.14 * \"2.0%\": "; var_dump(3.14 * "2.0%");
   print "    3.14 * \"\$2.0\": "; var_dump(3.14 * "$2.0");
   print "    3.14 * TRUE: "; var_dump(3.14 * TRUE);
   print "    3.14 * FALSE: "; var_dump(3.14 * FALSE);

   print "\n Conparison operations:\n";
   print "    3.14 < \"Hello\": "; var_dump(3.14 < "Hello");
   print "    3.14 > \"Hello\": "; var_dump(3.14 > "Hello");
   print "    \"3.14\" > \"Hello\": "; var_dump("3.14" > "Hello");

   print "\n String operations:\n";
   print "    \"Hello \" . TRUE: "; var_dump("Hello " . TRUE);
   print "    \"Hello \" . FALSE: "; var_dump("Hello " . FALSE);
   print "    \"Hello \" . NULL: "; var_dump("Hello " . NULL);
   print "    \"Hello \" . 1.0/3.0: "; var_dump("Hello " . 1.0/3.0);
?>
```

If you run this sample script in PHP 7 and higher, you should get output with some messages. This is because now the default message level is set to E\_NOTICE. You can change the setting or modify the code to make sure all variables are defined before using them.

```
herong> \php-7.3\php TypeAutoConversion.php

 Logical operations:
    NULL==FALSE: bool(true)
    0==FALSE: bool(true)
    ""==FALSE: bool(true)
    "0"==FALSE: bool(true)
    "0 - zero"==TRUE: bool(true)
    "zero"==TRUE: bool(true)

 Logical operations:
    3.14 * "2.0": float(6.28)
    3.14 * "2.0%": PHP Notice:  A non well formed numeric value
       encountered in C:\herong\TypeAutoConversion.php on line 14

Notice: A non well formed numeric value encountered in
   C:\herong\TypeAutoConversion.php on line 14
float(6.28)
    3.14 * "$2.0": PHP Warning:  A non-numeric value encountered in
       C:\herong\TypeAutoConversion.php on line 15

Warning: A non-numeric value encountered in
   C:\herong\TypeAutoConversion.php on line 15
float(0)
    3.14 * TRUE: float(3.14)
    3.14 * FALSE: float(0)

 Conparison operations:
    3.14 < "Hello": bool(false)
    3.14 > "Hello": bool(true)
    "3.14" > "Hello": bool(false)

 String operations:
    "Hello " . TRUE: string(7) "Hello 1"
    "Hello " . FALSE: string(6) "Hello "
    "Hello " . NULL: string(6) "Hello "
    "Hello " . 1.0/3.0: string(22) "Hello 0.33333333333333"
```

If you run this sample script in PHP 5 and lower, you should get output without any message:

```
herong> \php5.6\php TypeAutoConversion.php

 Logical operations:
    NULL==FALSE: bool(true)
    0==FALSE: bool(true)
    ""==FALSE: bool(true)
    "0"==FALSE: bool(true)
    "0 - zero"==TRUE: bool(true)
    "zero"==TRUE: bool(true)

 Logical operations:
    3.14 * "2.0": float(6.28)
    3.14 * "2.0%": float(6.28)
    3.14 * "$2.0": float(0)
    3.14 * TRUE: float(3.14)
    3.14 * FALSE: float(0)

 Conparison operations:
    3.14 < "Hello": bool(false)
    3.14 > "Hello": bool(true)
    "3.14" > "Hello": bool(false)

 String operations:
    "Hello " . TRUE: string(7) "Hello 1"
    "Hello " . FALSE: string(6) "Hello "
    "Hello " . NULL: string(6) "Hello "
    "Hello " . 1.0/3.0: string(20) "Hello 0.333333333333"
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Conditional Statements - "if" and "switch"

This chapter provides tutorial examples and notes about conditional statements. Topics include 4 forms of 'if' statements, 'switch' statements, examples of controlling code executions with conditional statements.

> ["if" Statements](#part0033.xhtml)
> 
> ["if" Statement Examples](#part0034.xhtml)
> 
> ["switch" Statements](#part0035.xhtml)
> 
> ["switch" Statement Examples](#part0036.xhtml)

Takeaways:

*   "if" must be followed by a condition.
*   "elseif" and "else if" are equivalent.
*   "switch" must be followed by a test expression.
*   "default" clause will be executed, if no "case" clause matches the test expression.
*   Once a "case" is matched, all remaining statement blocks will be executed.
*   "break" statement should be used in "case" clauses to stop execution.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Conditional Statements - "if" and "switch"](#part0032.xhtml)

∟"if" Statements

This section describes 4 forms of 'if' statements supported in PHP. The more complex form is 'if ... elseif ... else'.

There are 4 forms of "If" statements supported in PHP:

1\. Single-statement "if":

```
   if (condition) statement
```

where "condition" is a Boolean value, and "statement" specify another statement. The specified statement will be executed, if and only if the specified condition is evaluated to "TRUE".

2\. Multi-statement "if":

```
   if (condition) {
      statement;
      statement;
      ...
   }
```

The specified multi-statement block will be executed, if and only if the specified condition is evaluated to "TRUE".

3\. "if ... else" Statement:

```
   if (condition) {
      statement;
      statement;
      ...
   } else {
      statement;
      statement;
      ...
   }
```

Two statement blocks are specified. But only one statement block will be executed based on the value of the specified condition. If the specified condition is "TRUE", the first block will be executed. If the specified condition is "FALSE", the second block will be executed.

4\. "if ... elseif" Statement:

```
   if (condition_1) {
      statement;
      statement;
      ...
   } elseif (condition_2) {
      statement;
      statement;
      ...
   } elseif (condition_3) {
      statement;
      statement;
      ...
   ...
   } else {
      statement;
      statement;
      ...
   }
```

Many statement blocks are specified. But only one statement block will be executed based on the value of the condition specified for that block.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Conditional Statements - "if" and "switch"](#part0032.xhtml)

∟"if" Statement Examples

This section provides a tutorial example on how to use different types of 'if' statements to control code executions.

To help us understand how "if" statements work, I wrote the following the tutorial example PHP script:

```
<?php
#  IfStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#

   print("\n Single-statement \"if\":\n");
   $isNewYear = TRUE;
   if ($isNewYear) print("    Happy New Year!\n");

   print("\n Multi-statement \"if\":\n");
   $hasError = TRUE;
   if ($hasError) {
      print("    Open the log file.\n");
      print("    Write an error message.\n");
      print("    Close the log file.\n");
   }

   print("\n \"if ... else\" statement:\n");
   $login = "Herong";
   if ($login == "Admin") {
      print("    Display the delete button.\n");
      print("    Display the edit button.\n");
   } else {
      print("    Display the view button.\n");
   }

   print("\n \"if ... elseif\" statement:\n");
   $dateInfo = getdate();
   $wDay = $dateInfo["wday"];
   $weekDay = $dateInfo["weekday"];
   $openHours = "open";
   if ($wDay == 0) {
      $openHours = "closed";
   } elseif ($wDay >= 1 && $wDay <= 5) {
      $openHours = "open from 9:00am to 9:00pm";
   } elseif ($wDay == 6 ) {
      $openHours = "open from 9:00am to 5:00pm";
   } else {
      $openHours = "not at here";
   }
   print("    Today is: $weekDay\n");
   print("    The library is $openHours\n");
?>
```

If you run this sample script, you should get:

```
herong> \php\php IfStatements.php

 Single-statement "if":
    Happy New Year!

 Multi-statement "if":
    Open the log file.
    Write an error message.
    Close the log file.

 "if ... else" statement:
    Display the view button.

 "if ... elseif" statement:
    Today is: Sunday
    The library is closed
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Conditional Statements - "if" and "switch"](#part0032.xhtml)

∟"switch" Statements

This section describes how 'switch' statements work. Execution will start at the 'case' clause whose expected value matches the test expression. Execution will continue with all remaining 'case' clauses.

"switch" statement is an alternative way of executing statements selectively based on certain conditions. Here is the syntax of "switch" statements:

```
   switch (test_expression) {
      case expected_value_1:
         statement_block_1;
         break;
      case expected_value_2:
         statement_block_2;
         break;
      ...
      default:
         last_statement_block;
   }
```

where "test\_expression" is an expression used to test against with expected values specified in "case" clauses, and "expected\_value\_\*" are expected values.

The execution of a "switch" statement goes like this:

*   Each "case" clause will be visited sequentially from top to bottom.
*   If the result of the test expression matches the expected value in a "case" clause, the statement block in that clause will be executed.
*   One a statement block is executed, all remaining statement blocks will also be executed.
*   If no "case" clause is executed, the "default" clause will be executed.
*   To stop executing remaining statements, you can use the "break" statement.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Conditional Statements - "if" and "switch"](#part0032.xhtml)

∟"switch" Statement Examples

This section provides a tutorial example on how to use 'switch' statements to select one block of statements based on the equal condition of an expected value.

To help us understand how "switch" statements work, I wrote the following the tutorial example script:

```
<?php
#  SwitchStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   date_default_timezone_set("Europe/Paris");
   $dateInfo = getdate();
   $wDay = $dateInfo["wday"];
   $weekDay = $dateInfo["weekday"];
   $openHours = "open";

   print "\nLibrary Hours with \"switch\" statements:\n";
   print "   Today is: $weekDay\n";
   switch ($weekDay) {
      case "Monday":
      case "Tuesday":
      case "Wednesday":
      case "Thursday":
      case "Friday":
         $openHours = "open from 9:00am to 9:00pm";
         break;
      case "Saturday":
         $openHours = "open from 9:00am to 5:00pm";
         break;
      case "Sunday":
         $openHours = "closed";
         break;
      default:
         $openHours = "not at here";
   }
   print "   The library is $openHours\n";
?>
```

If you run this sample script, you should get:

```
herong> \php\php SwitchStatements.php

Library Hours with "switch" statements:
   Today is: Sunday
   The library is closed
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Loop Statements - "while", "for", and "do ... while"

This chapter provides tutorial examples and notes about loop statements. Topics include 'while, 'for', and 'do ... while' statements; examples of controlling code executions with loop statements.

> ["while" Statements](#part0038.xhtml)
> 
> ["while" Statement Examples](#part0039.xhtml)
> 
> ["for" Statements](#part0040.xhtml)
> 
> ["for" Statement Examples](#part0041.xhtml)
> 
> ["do ... while" Statements](#part0042.xhtml)
> 
> ["break" and "continue" Statements](#part0043.xhtml)

Takeaways:

*   "while" statement is the most commonly used loop statement in PHP.
*   "for" statement is the most complex loop statement in PHP.
*   "do ... while" statement is just a variation of "while" statement.
*   "break" statement takes an optional parameter to break multiple level of loops.
*   "continue" statement takes an optional parameter to break and continue on the specified level of loops.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟"while" Statements

This section describes how 'while' statements works in PHP. One or more statements are repeatedly executed as long as the specified condition is true.

The "while" statement is the most commonly used loop statement in PHP. There are 3 forms of "while" statements supported in PHP:

1\. Single-statement "while":

```
   while (condition) statement;
```

2\. Multi-statement "while":

```
   while (condition) {
      statement;
      statement;
      ...
   }
```

3\. Multi-statement "while ... endwhile":

```
   while (condition):
      statement;
      statement;
      ...
   endwhile;
```

All forms of "while" statements are executed like this:

Step 1: Evaluate "condition" as a Boolean value.

Step 2: If "condition" returns TRUE, continue with Step 4.

Step 3: If "condition" returns "FALSE", terminate the loop.

Step 4: Execute the statement or statements enclosed in the loop.

Step 5: Continue with Step 1.

Of course, you can use the "break" statement inside the loop to terminate the loop immediately.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟"while" Statement Examples

This section provides a tutorial example on how to use 'while' statements to repeat execution of one or more statements while a specified condition is true.

To help us understand how "while" statements work, I wrote the following the tutorial example PHP script:

```
<?php
#  WhileStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $upperLimit = 20;
#
   print("\n Single-statement \"while\":\n");
   $sum = 0; $i = 0;
   while ($i<$upperLimit) $sum += ++$i;
   print("    Sum of 1 to 20: $sum\n");
#
   print("\n Multi-statement \"while\":\n");
   $i = 3;
   while ($i<$upperLimit) {
      $isPrime = true;
      $j = 2;
      while ($j<$i) {
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
         $j++;
      }
      if ($isPrime) print "   $i is a prime number.\n";
      $i++;
   }
#
   print("\n Multi-statement \"while ... endwhile\":\n");
   $i = 3;
   while ($i<$upperLimit):
      $isPrime = true;
      $j = 2;
      while ($j<$i):
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
         $j++;
      endwhile;
      if ($isPrime) print "   $i is a prime number.\n";
      $i++;
   endwhile;
?>
```

If you run this sample script, you should get:

```
herong> \php\php WhileStatements.php

 Single-statement "while":
    Sum of 1 to 20: 210

 Multi-statement "while":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.

 Multi-statement "while ... endwhile":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟"for" Statements

This section describes how 'for' statements works in PHP. One or more statements are repeatedly executed as long as the specified condition is true. 'for' statements has extra expressions for loop initialization and loop control update.

The "for" statement is the most complex loop statement in PHP. There are 4 forms of "while" statements supported in PHP:

1\. Empty-statement "for":

```
   for (initial_expression; stop_condition; repeating_expression);
```

2\. Single-statement "for":

```
   for (initial_expression; stop_condition; repeating_expression)
      statement;
```

3\. Multi-statement "for":

```
   for (initial_expression; stop_condition; repeating_expression) {
      statement;
      statement;
      ...
   }
```

4\. Multi-statement "for ... endfor":

```
   for (initial_expression; stop_condition; repeating_expression):
      statement;
      statement;
      ...
   endfor;
```

All forms of "for" statements are executed like this:

Step 1: "initial\_expression" is evaluated unconditionally. The "initial\_expression" is usually used to assign the initial value to a loop control variable, like $i=0.

Step 2: Evaluate "stop\_condition" as a Boolean value. The "stop\_condition" is usually a comparison expression against the loop control variable, like $i<100.

Step 3: If "stop\_condition" returns TRUE, continue with Step 5.

Step 4: If "stop\_condition" returns "FALSE", terminate the loop.

Step 5: Execute the statement or statements enclosed in the loop.

Step 6: Evaluate "repeating\_expression". The "repeating\_expression" is usually an expression to increment the value of the loop control variable, like $i++.

Step 7: Continue with Step 2.

If you want to terminate the loop early, you can use the "break" statement inside the loop, which will terminate the loop immediately.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟"for" Statement Examples

This section provides a tutorial example on how to use 'for' statements to repeatedly execute zero, one or more statements.

To help us understand how "for" statements work, I wrote the following the tutorial example script:

```
<?php
#  ForStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $upperLimit = 20;
#
   print("\n No-statement \"for\":\n");
   for ($sum = 0, $i = 0; $i<$upperLimit; $sum += ++$i);
   print("    Sum of 1 to 20: $sum\n");

   print("\n Single-statement \"for\":\n");
   for ($sum = 0, $i = 0; $i<$upperLimit; $i++) $sum += $i;
   print("    Sum of 0 to 19: $sum\n");
#
   print("\n Multi-statement \"for\":\n");
   for ($i=3; $i<$upperLimit; $i++) {
      $isPrime = true;
      for ($j=2; $j<=$i/2; $j++) {
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
      }
      if ($isPrime) print "   $i is a prime number.\n";
   }
#
   print("\n Multi-statement \"for ... endfor\":\n");
   for ($i=3; $i<$upperLimit; $i++):
      $isPrime = true;
      for ($j=2; $j<=$i/2; $j++):
         $isPrime = $i%$j > 0;
         if (!$isPrime) break;
      endfor;
      if ($isPrime) print "   $i is a prime number.\n";
   endfor;
?>
```

If you run this sample script, you should get:

```
herong> \php\php ForStatements.php

 No-statement "for":
    Sum of 1 to 20: 210

 Single-statement "for":
    Sum of 0 to 19: 190

 Multi-statement "for":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.

 Multi-statement "for ... endfor":
   3 is a prime number.
   5 is a prime number.
   7 is a prime number.
   11 is a prime number.
   13 is a prime number.
   17 is a prime number.
   19 is a prime number.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟"do ... while" Statements

This section describes how 'do ... while' statements works in PHP. One or more statements are repeatedly executed as long as the specified condition is true.

PHP also supports a variation of the "while" statement called "do ... while" statement. with 2 forms:

1\. Single-statement "do ... while":

```
   do statement while (condition);
```

2\. Multi-statement "do ... while":

```
   do {
      statement;
      statement;
      ...
   } while (condition);
```

All forms of "do ... while" statements are executed like this:

Step 1: Execute the statement or statements enclosed in the loop.

Step 2: Evaluate "condition" as a Boolean value.

Step 3: If "condition" returns TRUE, continue with Step 1.

Step 4: If "condition" returns "FALSE", terminate the loop.

Of course, you can use the "break" statement inside the loop to terminate the loop immediately.

I will leave it to you to write some sample scripts for "do ... while" statements as exercises.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Loop Statements - "while", "for", and "do ... while"](#part0037.xhtml)

∟"break" and "continue" Statements

This section describes how 'break' and 'continue' statements works in PHP. 'break' statement breaks the statement block and the loop. 'continue' statement breaks the statement block, but continues on the next iteration of the loop.

In order to help us control the execution flow better, PHP provides two special statements, "break" and "continue", for statement blocks:

1\. "break" statement with no option: It breaks the current statement block and the current loop where the "break" statement is located. The remaining statements in the current statement block will not be executed. If current statement block is running as a loop, the loop will also be terminated.

```
   any_block {
      ...
      any_block {
         ...
         any_block {
            ...
            break;
            ...
         }
         ...
      }
      ...
   }
```

2\. "break" statement with an option of integer, n: It breaks statement blocks and loops n levels backward. The remaining statements in all n levels of statement blocks will not be executed. If any of those statement blocks are loops, those loops will also be terminated.

```
   any_block {
      ...
      any_block {
         ...
         any_block {
            ...
            break n;
            ...
         }
      }
   }
```

3\. "continue" statement with no option: It breaks the current statement block and continues on the next iteration of the current loop where the "continue" statement is located. The remaining statements in the current statement block will not be executed. But the loop will continue on the next iteration, if current statement block is running as a loop.

```
   any_block {
      ...
      any_block {
         ...
         any_block {
            ...
            continue;
            ...
         }
         ...
      }
      ...
   }
```

4\. "continue" statement with an option of integer n: It breaks statement blocks and loops n levels backward. The remaining statements in all n levels of statement blocks will not be executed. But the n-th level loop will be continued on the next iteration, if the n-th level statement block is running as a loop.

```
   any_block {
      ...
      any_block {
         ...
         any_block {
            ...
            continue n;
            ...
         }
         ...
      }
      ...
   }
```

I will leave it to you to write some sample scripts for "break" and "continue" statements as exercises.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Function Declaration, Arguments, and Return Values

This chapter provides tutorial examples and notes about user-defined functions. Topics include defining function with arguments, calling functions in expressions, passing arguments by values or by references, variable-length argument list, providing default values for arguments, returning data by value or by reference.

> [What Is a Function](#part0045.xhtml)
> 
> ["function" Statements - Defining Functions](#part0046.xhtml)
> 
> [Function Call Operations](#part0047.xhtml)
> 
> [Passing Arguments to Functions](#part0048.xhtml)
> 
> [Example of Passing Arguments by Values](#part0049.xhtml)
> 
> [Using Pass-by-Value Arguments for References](#part0050.xhtml)
> 
> [Example of Passing Arguments by References](#part0051.xhtml)
> 
> [Variable-Length Argument Lists](#part0052.xhtml)
> 
> [Providing Default Values to Argument Variables](#part0053.xhtml)
> 
> [Returning Values from Functions](#part0054.xhtml)
> 
> [Returning References from Functions](#part0055.xhtml)
> 
> [Usage Examples of Functions](#part0056.xhtml)

Takeaways:

*   A "function" statement defines a function with or without argument variables.
*   A "return" statement in a function stops the execution of the function and returns a value to the calling code.
*   Function call option can provide more arguments than what are defined in the function.
*   "func\_get\_arg()", "func\_get\_args()", and "func\_num\_args()" allows us to access arguments without using argument variables.
*   An argument can be passed by references if you add "&" to the argument variable.
*   A function can return the reference of a variable, if you add "&" to the function name.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟What Is a Function

This section describes what is a function. A quick example is provided showing how to define and call a function.

**What Is a Function?** A function is a definition of a block of statements. The block of statements in a function will be executed only when the function is invoked. PHP provides a long list of built-in (predefined) functions. PHP supports user-defined functions - You define your own functions in PHP source code.

To learn how to use user-defined functions in PHP, we need to pay attentions in following areas:

1\. How to define a function?

2\. How to call a function to execute its statements?

3\. How to pass input values into a function?

4\. How to return a result from a function?

5\. How to share variables with a function?

Here is a simple example script of defining a function, calling a function, passing data into a function, and returning result from a function:

```
   function square($x) {
      $y = $x * $x;
      return $y;
   }

   $radius = 2.0;
   $area = M_PI * square($radius);
   echo($area);
```

Notice that in this example script:

*   A function is defined with a "function" statement and named as "square".
*   The function is called to execute as an operand in an expression in its name.
*   One input value is passed into the function at the calling time.
*   The result is returned using the "return" statement.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟"function" Statements - Defining Functions

This section describes the 'function' statement, which can be used to define your own function with a function name, argument list, function body.

A "function" statement defines a function with the following syntax:

```
   function function_name($argument_1, $argument_2, ...) {
      statement_1;
      statement_2;
      ...
   }
```

where "function\_name" is the name of the function, and "$argument\_1, $argument\_2, ..." is a list of variables acting as arguments of the function. "statement\_1; statement\_2; ..." is a block of statements that becomes the body of the function.

The "function\_name" is the identifier of the function, it must follow PHP identifier naming conventions. The general rule is that don't use any special characters in function names.

The argument list is optional. If not needed, define your function with no arguments but keep the argument parentheses like this:

```
   function function_name() {
      statement_1;
      statement_2;
      ...
   }
```

When a function is called in an expression, it will always return a value for the expression. The returning value can be controlled in 3 ways:

1\. If the function body is executed to the last statement without hitting any "return" statement, the default value, NULL, will be returned to the calling expression.

2\. If an empty "return" statement is reached during the function body execution, the remaining part of the function body will not be executed and the default value, NULL, will be returned to the calling expression.

3\. If a "return" statement with an expression, like "return expression", is reached during the function body execution, the remaining part of the function body will not be executed and the resulting value of the specified expression will be returned to the calling expression.

To help us understand how to use "function" statements, I wrote the following the tutorial example PHP script:

```
<?php
#  FunctionStatements.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#

#  Defining a real dummy function
   function dummy() {}

#  Defining a function with no arguments
   function showMyFooter() {
      print("Copyright: Herong Yang\n");
      print("Last Modified: 2019\n");
   }

#  Defining a function with arguments, but doing nothing
   function doNothing($a, $b, $c, $d, $e, $f, $g, $h, $i, $j, $k) {}

#  Defining a function with arguments and doing something
   function showAnyFooter($author) {
      print("Copyright: $author\n");
      print("Last Modified: 2019\n");
   }

#  Defining a function that returns a value
   function f2c($fahrenheit) {
      $celsius = ($fahrenheit - 32.0 ) / 1.8;
      return $celsius;
   }

#  Defining a function that returns a random value
   function getValue() {
      $i = rand(1, 6);
      if ($i==1) {
         return TRUE;
      } elseif ($i==2) {
         return 9;
      } elseif ($i==3) {
         return 9.99;
      } elseif ($i==4) {
         return "Hello";
      } elseif ($i==5) {
         return;
      }
   }
?>
```

If you run this sample script, you will get no output, because this script only defines those functions. There is no expression that calls any of those functions.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟Function Call Operations

This section describes the function call operation, which triggers the execution of the called function with arguments provided on the call.

Calling a function in PHP is simple. All you have to do is to just use the function name with an argument list in any expression:

```
   ... function_name(argument_1, argument_2, ...) ...
```

When the execution reaches this function call operation, it will:

*   Evaluate all calling arguments to values or variable references.
*   Assign argument values and references to argument variables defined in the "function" statement.
*   Start to execute the first statement of the function body.
*   Continue to execute the function body until the end of the function body or a "return" statement.
*   If a "return" statement is reached with a value specified, that value is returned as this function call operation.
*   If a "return" statement is reached with a no value specified, NULL is returned as this function call operation.
*   If no "return" statement is reached, NULL is returned as this function call operation.

Here is a simple example script showing us how to use function call operations:

```
<?php
#  FunctionCallOperations.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#

#  Defining a function that returns a value
   function f2c($fahrenheit) {
      $celsius = ($fahrenheit - 32.0 ) / 1.8;
      return $celsius;
   }

#  Defining a function that returns NULL
   function showAnyFooter($author) {
      print("    Copyright: $author\n");
      print("    Last Modified: 2015\n");
   }

   print("\n Function call as a standalone expression:\n");
   showAnyFooter("Herong Yang");

   print("\n Function call as an operand of another operation:\n");
   if (f2c(20.0)<0.0) print("    It's cold here!\n");

   print("\n Function call as an argument of another call:\n");
   print("    How is the temperature? ");
   print(f2c(110.0));
?>
```

If you run this sample script, you should get:

```
herong> \php\php FunctionCallOperations.php

 Function call as a standalone expression:
    Copyright: Herong Yang
    Last Modified: 2019

 Function call as an operand of another operation:
    It's cold here!

 Function call as an argument of another call:
    How is the temperature? 43.3333333333
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟Passing Arguments to Functions

This section describes rules on how arguments can be passed from the calling code into the called function by value (the default) or by reference.

As shown in examples in previous sections, passing arguments to a function seems to be a simple job. But it may cause confusion if you don't following the rules. PHP has the following rules on passing arguments to function and subroutine procedures:

1\. By default, a function argument is passed by value. In this case, the argument variable contains a copy of the data provided by the calling code.

2\. But, a function argument can be passed by reference, if you define the argument variable as &$variable\_name. In this case, the argument variable contains a reference of the original variable in the calling code. In another word, the argument variable is an alias of the original variable.

3\. A pass-by-value argument variable is safer to use, because it will be assigned with a copy of the data from the calling code at the time of call. If the argument variable is re-assigned with a new data in the function, there will be no impact to the calling code.

4\. A pass-by-reference argument variable offers an advantage and a risk. The advantage is that it can be used as an output channel for the function to send data back to the calling code. The risk is that if the argument variable is re-assigned with a new data in the function by a mistake, there will be some negative impact on the calling code.

5\. An argument variable can be defined with a default value. Arguments with default values must be positioned at the end of the argument list.

6\. If you want to use the default value of an argument variable, you can skip that argument in the function call operation.

7\. Arguments passed in the function call be retrieved without using argument variables. You can use func\_num\_args(), func\_get\_arg(), and func\_get\_args() functions to access arguments. This feature can be used to support variable-length argument lists.

8\. If an array is passed by value, a copy of the original array will be passed to the function. If an array is passed by reference, the function and the calling code is sharing the same array.

9\. If a reference of a variable is passed by value, a copy of the reference will be passed to the function. But the copy and the reference are both referring to the same original variable. So passing a reference by value is equivalent to passing a variable by reference.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟Example of Passing Arguments by Values

This section provides a tutorial example on how to use pass-by-value arguments, which allows the function to re-assign new values to original variables in the calling code.

As we learned from the previous section, PHP functions use pass-by-value arguments by default. If an argument is defined as an pass-by-value argument, the calling operation can provide an expression for this argument. That expression will be assigned to this argument variable when function is called. For example, if we have "function f($var) {...}" defined, "f(exp)" is equivalent to "{$var=exp; ...}".

To see how passing arguments by values works, I wrote this tutorial example, PassByValue.php:

```
<?php
#  PassByValue.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
function swap($left, $right) {
   $temp = $left;
   $left = $right;
   $right = $temp;
   print("    Swapped in function: ".getString($left, $right)."\n");
}

   date_default_timezone_set("Europe/Paris");

   print("\n 1. Passing two literals:\n");
   print("    Before call: ". getString("Apple", "Orange") ."\n");
   swap("Apple", "Orange");

   print("\n 2. Passing two variables:\n");
   $x = "Dog"; $y = "Cat";
   print("    Before call: ". getString($x, $y) ."\n");
   swap($x, $y);
   print("    After call: ". getString($x, $y) ."\n");

   print("\n 3. Passing two arrays:\n");
   $x = array("Mon", "Tue"); $y = array("Jan", "Feb");
   print("    Before call: ". getString($x, $y) ."\n");
   swap($x, $y);
   print("    After call: ". getString($x, $y) ."\n");

   print("\n 4. Passing two objects:\n");
   $x = new DateTime("2005-01-01"); $y = new DateTime("2006-01-01");
   print("    Before call: ". getString($x, $y) ."\n");
   swap($x, $y);
   print("    After call: ". getString($x, $y) ."\n");

function getString($left, $right) {
   if (is_scalar($left)) {
      return "$left | $right";
   } elseif (is_array($left)) {
      return "($left[0], $left[1]...) | ($right[0], $right[1]...)";
   } elseif (is_object($left) && get_class($left)=="DateTime") {
      return $left->format("Y")." | ".$right->format("Y");
   } else {
      return NULL;
   }
}
?>
```

If you run this sample script, you should get:

```
herong> \php\php PassByValue.php

 1. Passing two literals:
    Before call: Apple | Orange
    Swapped in function: Orange | Apple

 2. Passing two variables:
    Before call: Dog | Cat
    Swapped in function: Cat | Dog
    After call: Dog | Cat

 3. Passing two arrays:
    Before call: (Mon, Tue...) | (Jan, Feb...)
    Swapped in function: (Jan, Feb...) | (Mon, Tue...)
    After call: (Mon, Tue...) | (Jan, Feb...)

 4. Passing two objects:
    Before call: 2005 | 2006
    Swapped in function: 2006 | 2005
    After call: 2005 | 2006
```

The output confirms that:

*   My swap() function is very powerful. It swapped anything received from the argument list.
*   Pass-by-value arguments can be used for scalars, arrays and objects.
*   Pass-by-value arguments are safe to use. The swap() function has no impact on calling code.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟Using Pass-by-Value Arguments for References

This section provides a tutorial example on how to references on pass-by-value arguments. Using a reference expression as a pass-by-value argument allows you to modify the original variable in the calling code.

In the previous section, we tested on passing regular variables to functions using the pass-by-value mode. But what will happen if we pass references to functions using the pass-by-value mode? To find out the answer, I wrote this tutorial example script:

```
<?php
#  PassByValueWithReference.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
function swap($left, $right) {
   $temp = $left;
   $left = $right;
   $right = $temp;
   print("    Swapped in function: ".getString($left, $right)."\n");
}

   print("\n 1. Passing two variables:\n");
   $x = "Dog"; $y = "Cat";
   print("    Before call: ". getString($x, $y) ."\n");
   swap($x, $y);
   print("    After call: ". getString($x, $y) ."\n");

   print("\n 2. Passing two references:\n");
   $y = "Bob"; $y = "Tom";
   print("    Before call: ". getString($x, $y) ."\n");
   swap(&$x, &$y);
   print("    After call: ". getString($x, $y) ."\n");

   print("\n 3. Passing two references in variables:\n");
   $a = "One"; $b = "Two";
   $x = &$a; $y = &$b;
   print("    Before call: ". getString($a, $b) ."\n");
   print("    Before call: ". getString($x, $y) ."\n");
   swap($x, $y);
   print("    After call: ". getString($a, $b) ."\n");
   print("    After call: ". getString($x, $y) ."\n");

function getString($left, $right) {
   if (is_scalar($left)) {
      return "$left | $right";
   } else {
      return NULL;
   }
}
?>
```

If you run this tutorial example with older version of PHP, you will get:

```
herong> \php\php PassByValueWithReference.php

 1. Passing two variables:
    Before call: Dog | Cat
    Swapped in function: Cat | Dog
    After call: Dog | Cat

 2. Passing two references:
    Before call: Dog | Tom
    Swapped in function: Tom | Dog
    After call: Tom | Dog

 3. Passing two references in variables:
    Before call: One | Two
    Before call: One | Two
    Swapped in function: Two | One
    After call: One | Two
    After call: One | Two
```

Do you see anything interesting in the output?

There is nothing strange in test 1. Pass-by-value on regular variables left no changes on original variables.

But in test 2, pass-by-value on references caused original variables to be swapped. I think I know why. The swap() function received copies of references, &$x and &$y, swapping references actually swapped the original variables, $x and $y.

But in test 3, pass-by-value on references stored in variables caused original variables un-touched. Initially, I thought test 3 should behave like test 2. But by following the pass-by-value logic, I think I know why it behaves differently. In the call, swap($x, $y), copies of values of $x and $y are passed. Since $x and $y are reference variables, values of $x and $y are values of $a and $b, "One" and "Two". So copies of "One" and "Two" are passed into the function. Of course, swapping these copies will have no impact on original values of $a and $b (or $x and $y, since they are aliases of $a and $b).

Conclusion, If you call a function with a reference expression as a pass-by-value argument, you are equivalently using this argument as a pass-by-reference argument. Changes on this argument inside the function will be applied to the original variable in the calling code.

If you run this tutorial example with PHP 5, you will get a fatal error:

```
herong> \php-5.6\php PassByValueWithReference.php

PHP Fatal error:  Call-time pass-by-reference has been removed;
If you would like to pass argument by reference, modify the declaration
of swap() in C:\herong\PassByValueWithReference.php on line 20.
```

If you run this tutorial example with PHP 7, you will get a parsing error:

```
herong> \php-7.3\php PassByValueWithReference.php
PHP Parse error:  syntax error, unexpected '&'
in C:\herong\PassByValueWithReference.php on line 20
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟Example of Passing Arguments by References

This section provides a tutorial example on how to pass auguments to a function as references. This is very useful if you want to the caller to get the updated value from the function.

As we learned from the previous section, PHP supports pass-by-reference arguments if they are defined with a & prefix on the argument variables. If an argument is defined as an pass-by-reference argument, the calling operation can provide a variable, for this argument. The reference of that variable will be taken and assigned to this argument variable when function is called. For example, if we have "function f(&$var) {...}" defined, "f($arg)" is equivalent to "{$var=&$arg; ...}".

To see how passing arguments by references works, I wrote this tutorial example, PassByReference.php:

```
<?php
#  PassByReference.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
function swap(&$left, &$right) {
   $temp = $left;
   $left = $right;
   $right = $temp;
   print("    Swapped in function: ".getString($left, $right)."\n");
}

   date_default_timezone_set("Europe/Paris");

#   print("\n 1. Passing two literals:\n");
#   print("    Before call: ". getString("Apple", "Orange") ."\n");
#   swap("Apple", "Orange");

   print("\n 2. Passing two variables:\n");
   $x = "Dog"; $y = "Cat";
   print("    Before call: ". getString($x, $y) ."\n");
   swap($x, $y);
   print("    After call: ". getString($x, $y) ."\n");

   print("\n 3. Passing two arrays:\n");
   $x = array("Mon", "Tue"); $y = array("Jan", "Feb");
   print("    Before call: ". getString($x, $y) ."\n");
   swap($x, $y);
   print("    After call: ". getString($x, $y) ."\n");

   print("\n 4. Passing two objects:\n");
   $x = new DateTime("2005-01-01"); $y = new DateTime("2006-01-01");
   print("    Before call: ". getString($x, $y) ."\n");
   swap($x, $y);
   print("    After call: ". getString($x, $y) ."\n");

function getString($left, $right) {
   if (is_scalar($left)) {
      return "$left | $right";
   } elseif (is_array($left)) {
      return "($left[0], $left[1]...) | ($right[0], $right[1]...)";
   } elseif (is_object($left) && get_class($left)=="DateTime") {
      return $left->format("Y")." | ".$right->format("Y");
   } else {
      return NULL;
   }
}
?>
```

If you run this sample script, you should get:

```
herong> \php\php PassByReference.php

 2. Passing two variables:
    Before call: Dog | Cat
    Swapped in function: Cat | Dog
    After call: Cat | Dog

 3. Passing two arrays:
    Before call: (Mon, Tue...) | (Jan, Feb...)
    Swapped in function: (Jan, Feb...) | (Mon, Tue...)
    After call: (Jan, Feb...) | (Mon, Tue...)

 4. Passing two objects:
    Before call: 2005 | 2006
    Swapped in function: 2006 | 2005
    After call: 2006 | 2005
```

The output confirms that:

*   My swap() function is very powerful. It swapped references of any types of variables received from the argument list.
*   Pass-by-reference arguments can be used for scalar, array and object variables.
*   Pass-by-reference arguments allow functions to reassign data values to original variables in the calling code.
*   Pass-by-reference arguments can only take variables from the calling code. If you open test #1 in my sample script, the execution will fail with a message, "Fatal error: Only variables can be passed by reference".

Exercise: Try to test pass-by-reference arguments with:

```
   swap("Apple", "Orange");
   swap(array("Mon", "Tue"), array("Jan", "Feb"));
   swap(new DateTime("2015-01-01"), new DateTime("2016-01-01"));
   swap(&$a, &$b);
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟Variable-Length Argument Lists

This section provides a tutorial example on how to access arguments in a function without using argument variables and how to pass arguments more than what are defined in the function statement.

As I mentioned earlier, PHP also allows you to access arguments provided in the function call operation without using argument variables. Here is how:

1\. func\_get\_arg(position) - It returns the value of the specified argument provided in the function call operation. "position" is the position index of the specified argument. The position index of the first argument is 0. For example, if "func\_get\_arg(2)" is used in a function, it will return the value of the 3rd argument.

2\. func\_num\_args() - It returns the total number of arguments provided in the function call operation. For example, if "func\_num\_args()" returns 1, you know that there is only 1 argument provided by calling code.

3\. func\_get\_args() - It creates and returns an array which contains values of all arguments provided in the function call operation. For example, if "$args = func\_get\_args()" is used in a function, $args will be array containing all arguments.

With all these 3 functions, we say that PHP supports variable-length argument lists with some basic rules:

*   The function call can provide more arguments than the number of argument variables defined in the function statement.
*   You can pass arguments to a function that has no argument variable defined.

To help us understand how use variable-length argument list feature, I wrote this tutorial example:

```
<?php
#  ArgumentList.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   function f2c($fahrenheit) {
      $celsius = (func_get_arg(0) - 32.0) / 1.8;
      return $celsius;
   }

   print("\n Calling a function that uses func_get_arg():\n");
   if (f2c(20.0)<0.0) print("    It's cold here!\n");

   function myMax() {
      $max = NULL;
      if (func_num_args()>0) $max = func_get_arg(0);
      for ($i=1; $i<func_num_args(); $i++) {
         if ($max < func_get_arg($i)) $max = func_get_arg($i);
      }
      return $max;
   }

   print("\n Calling a function that uses func_num_args():\n");
   print("    ".myMax()."\n");
   print("    ".myMax(3)."\n");
   print("    ".myMax(3, 1, 4)."\n");
   print("    ".myMax(3, 1, 4, 1, 5, 9, 2, 6, 5)."\n");

   function myMin() {
      $list = func_get_args();
      $min = NULL;
      if (count($list)>0) $min = $list[0];
      for ($i=1; $i<count($list); $i++) {
         if ($min > $list[$i]) $min = $list[$i];
      }
      return $min;
   }

   print("\n Calling a function that uses func_get_args():\n");
   print("    ".myMin()."\n");
   print("    ".myMin(5)."\n");
   print("    ".myMin(5, 6, 2)."\n");
   print("    ".myMin(5, 6, 2, 9, 5, 1, 4, 1, 3)."\n");
?>
```

If you run this sample script, you should get:

```
herong> \php\php ArgumentList.php

 Calling a function that uses func_get_arg():
    It's cold here!

 Calling a function that uses func_num_args():

    3
    4
    9

 Calling a function that uses func_get_args():

    5
    2
    1
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟Providing Default Values to Argument Variables

This section provides a tutorial example on how to provide default values to argument variables.

PHP also allows us to provide default values to argument variables using the following syntax on the function definition statement:

```
   function function_name($arg_1, $arg_2, ... $arg_n=exp) {
   ...
   }
```

where argument variable, $arg\_n, has been assigned with a default value, evaluated from the specified expression, "exp".

Assigning default values to argument variables has several simple rules:

*   Only scalar values and arrays can be used as argument variable default values. Objects can not be used as argument variable default values.
*   If argument variable has default value defined, the function call operation use that default value by skipping that argument.

To help us understand how use argument variable default values, I wrote this tutorial example:

```
<?php
#  ArgumentDefaultValues.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   function hello($name="Herong") {
      print("    Hello " . $name . "!\n");
   }

   print("\n Argument with a scalar default value:\n");
   hello();
   hello("World");
   hello(NULL);

   function showList($list=array("Apple", "Orange")) {
      print("    List: " . $list[0] . ", " . $list[1] . "\n");
   }

   print("\n Argument with an array default value:\n");
   showList();
   showList(array("Cat", "Dog"));

#   function showDate($object=new DateTime()) {
#      print("    Year: " . $object->format("Y"));
#   }
?>
```

If you run this sample script, you should get:

```
herong> \php\php ArgumentDefaultValues.php

 Argument with a scalar default value:
    Hello Herong!
    Hello World!
    Hello !

 Argument with an array default value:
    List: Apple, Orange
    List: Cat, Dog
```

If you open last 3 commented-out statements, you will get an execution error: "Parse error: syntax error, unexpected T\_NEW in C:\\herong\\php\\ArgumentDefaultValues.php on line 21",

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟Returning Values from Functions

This section provides a tutorial example on how to return values from functions - using the 'return' statement.

PHP supports function return values with some basic rules:

*   If a function is executed without reaching a return statement, it will return NULL.
*   A function can use a "return" statement to return all 8 types of values: boolean, integer, float, string, array, object, resource, null.
*   If you use a "return" statement to return a variable, a copy of the data in the variable will be returned to the calling code.

To help us understand these rules, I wrote this tutorial example:

```
<?php
#  FunctionReturnValues.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   date_default_timezone_set("Europe/Paris");

   function returnType($arg) {
      if (is_null($arg)) return "NULL";
      elseif (is_bool($arg)) return "BOOLEAN";
      elseif (is_int($arg)) return "INTEGER";
      elseif (is_float($arg)) return "FLOAT";
      elseif (is_string($arg)) return "STRING";
      elseif (is_array($arg)) return "ARRAY";
      elseif (is_object($arg)) return "OBJECT";
      elseif (is_resource($arg)) return "RESOURCE";
      else return "UNKNOWN";
   }
   print("\n Returning a scalar value:\n");
   print("    1: " . returnType(1) . "\n");
   print("    1.0: " . returnType(1.0) . "\n");
   print("    array(1.0): " . returnType(array(1.0)) . "\n");

   function createArray() {
      return func_get_args();
   }
   print("\n Returning an array value:\n");
   print("    createArray(): ".returnType(createArray(3,6,9))."\n");

   function currentDate() {
      return new DateTime();
   }
   print("\n Returning an object value:\n");
   print("    currentDate(): " . returnType(currentDate()) . "\n");

   function noReturn() {
   }
   print("\n Function without return statements:\n");
   print("    noReturn(): " . returnType(noReturn(3,1,4)) . "\n");
?>
```

If you run this sample script, you should get:

```
herong> \php\php FunctionReturnValues.php

 Returning a scalar value:
    1: INTEGER
    1.0: FLOAT
    array(1.0): ARRAY

 Returning an array value:
    createArray(): ARRAY

 Returning an object value:
    currentDate(): OBJECT

 Function without return statements:
    noReturn(): NULL
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟Returning References from Functions

This section provides a tutorial example on how to return references from functions - prefix the function name with & in both definition and call statements.

PHP supports function return references using this syntax:

```
   function &function_name() {
      ...
      return $var_1;
   }

   $var_2 = &function_name();
```

When you use a function to return a reference, you need follow these rules:

*   To declare a function that returns a reference, the function name must be prefixed with '&' in the function definition statement.
*   If a function is declared to return a reference, it should use the 'return' statement to return a variable.
*   To call a function that returns a reference, the function name must be prefixed with '&' in the function call operation.
*   The returning reference from a function should be assigned to another variable.

To help us understand these rules, I wrote this tutorial example:

```
<?php
#  FunctionReturnReferences.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   function pvrv($arg) {
      $arg = "Two";
      return $arg;
   }
   print("\n 1. Pass by value and return by value:\n");
   $x = "One";
   $y = pvrv($x);
   $y = "Three";
   print("    x: $x\n");
   print("    y: $y\n");

   function prrv(&$arg) {
      $arg = "Two";
      return $arg;
   }
   print("\n 2. Pass by reference and return by value:\n");
   $x = "One";
   $y = prrv($x);
   $y = "Three";
   print("    x: $x\n");
   print("    y: $y\n");

   function &pvrr($arg) {
      $arg = "Two";
      return $arg;
   }
   print("\n 3. Pass by value and return by reference:\n");
   $x = "One";
   $y = &pvrr($x);
   $y = "Three";
   print("    x: $x\n");
   print("    y: $y\n");

   function &prrr(&$arg) {
      $arg = "Two";
      return $arg;
   }
   print("\n 4. Pass by reference and return by reference:\n");
   $x = "One";
   $y = &prrr($x);
   $y = "Three";
   print("    x: $x\n");
   print("    y: $y\n");
?>
```

If you run this sample script, you should get:

```
herong> \php\php FunctionReturnReferences.php

 1. Pass by value and return by value:
    x: One
    y: Three

 2. Pass by reference and return by value:
    x: Two
    y: Three

 3.Pass by value and return by reference:
    x: One
    y: Three

 4. Pass by reference and return by reference:
    x: Three
    y: Three
```

Test 4. proves that the main code received the reference from prrr() correctly. $y is assigned with the reference of $arg. But $arg is an alias of $x, because $x is passed as a reference. So $y becomes an alias of $x.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Function Declaration, Arguments, and Return Values](#part0044.xhtml)

∟Usage Examples of Functions

This section provides usage examples of functions.

Here is a PHP script that provides usage examples of functions:

```
<?php
#  FunctionTips.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#

function msg() {
  print("Hello world!\n");
}
msg();
print("\n");

function hello($f) {
  print("Hello $f!\n");
}
hello("Bob");
print("\n");

function getYear() {
  $year = date("Y");
  return $year;
}
print("This year is: ".getYear()."\n");
print("\n");

function f2c($f) {
  return ($f - 32.0)/1.8;
}
print("Celsius: ".f2c(100.0)."\n");
print("Celsius: ".f2c(-40.0)."\n");
print("\n");

function swap($a, $b) {
  $t = $a;
  $a = $b;
  $b = $t;
}
$x = "PHP";
$y = "JSP";
print("Before swapping: $x, $y\n");
swap($x, $y);
print("After swapping: $x, $y\n");
print("\n");

# Passing arguments by value with references not allowed any more
# $x = "PHP";
# $y = "JSP";
# print("Before swapping: $x, $y\n");
# swap(&$x, &$y);
# print("After swapping: $x, $y\n");
# print("\n");

function ref_swap(&$a, &$b) {
  $t = $a;
  $a = $b;
  $b = $t;
}
$x = "PHP";
$y = "JSP";
print("Before swapping: $x, $y\n");
ref_swap($x, $y);
print("After swapping: $x, $y\n");
print("\n");

function average($array) {
  $sum = array_sum($array);
  $count = count($array);
  return $sum/$count;
}
$numbers = array(5, 7, 6, 2, 1, 3, 4, 2);
print("Average: ".average($numbers)."\n");
print("\n");

function shrink($array) {
  array_splice($array,1);
}
$numbers = array(5, 7, 6, 2, 1, 3, 4, 2);
print("Before shrinking: ".join(",",$numbers)."\n");
shrink($numbers);
print("After shrinking: ".join(",",$numbers)."\n");
print("\n");

# Passing arguments by value with references not allowed any more
# $numbers = array(5, 7, 6, 2, 1, 3, 4, 2);
# print("Before shrinking: ".join(",",$numbers)."\n");
# shrink(&$numbers);
# print("After shrinking: ".join(",",$numbers)."\n");
# print("\n");

function ref_shrink(&$array) {
  array_splice($array,1);
}
$numbers = array(5, 7, 6, 2, 1, 3, 4, 2);
print("Before shrinking: ".join(",",$numbers)."\n");
ref_shrink($numbers);
print("After shrinking: ".join(",",$numbers)."\n");
print("\n");

function powerBall() {
  $array = array(rand(1,55), rand(1,55), rand(1,55),
                 rand(1,55), rand(1,55), rand(1,42));
  return $array;
}
$numbers = powerBall();
print("Lucky numbers: ".join(",",$numbers)."\n");
print("\n");

function myPassword() {
  $password = "U8FIE8W0";
  print("Defined inside the function? ". isset($password)."\n");
}
myPassword();
print("Defined outside the function? ". isset($password)."\n");
print("\n");

$login = "fyicenter";
function myLogin() {
  print("Defined inside the function? ". isset($login)."\n");
}
myLogin();
print("Defined outside the function? ". isset($login)."\n");
print("\n");

$intRate = 5.5;
function myAccount() {
  global $intRate;
  print("Defined inside the function? ". isset($intRate)."\n");
}
myAccount();
print("Defined outside the function? ". isset($intRate)."\n");
print("\n");

$favor = "Blue";
function getFavor() {
  global $favor;
  return $favor;
}
$myFavor = getFavor();
print("Favorite tool: $myFavor\n");
$favor = "Pink";
print("Favorite tool: $myFavor\n");
print("\n");

$favor = "Blue";
function &getFavorRef() {
  global $favor;
  return $favor;
}
$myFavor = &getFavorRef();
print("Favorite tool: $myFavor\n");
$favor = "Pink";
print("Favorite tool: $myFavor\n");
print("\n");

function printKey($key="download") {
  print("PHP $key\n");
}
printKey();
printKey("hosting");
print("\n");

function myAverage() {
  $count = func_num_args();
  $args = func_get_args();
  $sum = array_sum($args);
  return $sum/$count;
}
$average = myAverage(102, 121, 105);
print("Average 1: $average\n");
$average = myAverage(102, 121, 105, 99, 101, 110, 116, 101, 114);
print("Average 2: $average\n");
print("\n");
?>
```

If you run this sample script, you should get:

```
herong> \php\php FunctionTips.php

Hello world!

Hello Bob!

This year is: 2019

Celsius: 37.777777777778
Celsius: -40

Before swapping: PHP, JSP
After swapping: PHP, JSP

Before swapping: PHP, JSP
After swapping: JSP, PHP

Average: 3.75

Before shrinking: 5,7,6,2,1,3,4,2
After shrinking: 5,7,6,2,1,3,4,2

Before shrinking: 5,7,6,2,1,3,4,2
After shrinking: 5

Lucky numbers: 48,16,54,26,2,30

Defined inside the function? 1
Defined outside the function?

Defined inside the function?
Defined outside the function? 1

Defined inside the function? 1
Defined outside the function? 1

Favorite tool: Blue
Favorite tool: Blue

Favorite tool: Blue
Favorite tool: Pink

PHP download
PHP hosting

Average 1: 109.33333333333
Average 2: 107.66666666667
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Arrays - Ordered Maps

This chapter provides tutorial examples and notes about arrays. Topics include creating arrays with the array constructor, using integer keys or string keys in arrays, accessing values through keys, array related built-in functions.

> [What Is an Array](#part0058.xhtml)
> 
> [Creating Arrays - Examples](#part0059.xhtml)
> 
> [Array Related Built-in Functions](#part0060.xhtml)
> 
> [Usage Examples of Array Functions](#part0061.xhtml)

Takeaways:

*   An array can be created with the array constructor, array().
*   A pair of key and value can be specified as key=>value as an argument in the constructor.
*   A value stored in an array can be accessed as $array\_variable\["key"\].
*   An array can be used as a stack through array\_push() and array\_pop() functions.
*   "foreach () {}" statement can be used to loop through all values in an array.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Arrays - Ordered Maps](#part0057.xhtml)

∟What Is an Array

This section describes what is an array - an ordered pairs of keys and values. If sequential integer keys are used, an array is a simple indexed list. If string keys are used, an array is a map.

**What Is an Array?** An array is a data type that represents an ordered pairs of keys and values. Arrays in PHP are different than arrays in most of other languages. Basic rules for PHP's arrays are:

1\. An array can be constructed by the array constructor, like:

```
   $myArray = array(k1=>v1, k2=>v2, ..., kn=>vn);
```

where k1, k2, ..., and kn are keys of integer type or string type. v1, v2, ..., and vn are values of any data types.

2\. The value of a given key in an array can be expressed by the array variable followed by the key in square brackets, like:

```
   print $myArray[kn];
```

3\. The value of a given key in an array can be modified by an assignment statement, like:

```
   $myArray[kn] = new_value.
```

4\. A new pair of key and value can be added to an array by an assignment statement, like:

```
   $myArray[kx] = vx
```

5\. If a string key represents an integer, it will be used as an integer key. So $myArray\['7'\] is the same as $myArray\[7\].

6\. If the key is missing in an array assignment or an array constructor, an integer key of 0, or the highest integer key plus 1, will be provided. So $myArray\[\] = "Last" assigns "Last" to a new integer key.

7\. An empty string is also a valid string key, like:

```
   $myArray[''] = vy;
```

8\. A pair of key and value can be removed by using the unset() function, like:

```
   unset($myArray[kn]);
```

9\. Pairs of keys and values are ordered in an array like a queue. New pairs are always added at the end of the array.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Arrays - Ordered Maps](#part0057.xhtml)

∟Creating Arrays - Examples

This section provides a tutorial example on how to create arrays in different ways.

Here is a tutorial example PHP script to show you some of array rules described in the previous section:

```
<?php
#  ArrayTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "\nLibrary hours:\n";
   $libraryHours = array(
      'Monday - Friday'=>'09:00 - 21:00',
      'Saturday'=>'09:00 - 17:00',
      'Sunday'=>'closed');
   print_r($libraryHours);
#
   print "\nPrime numbers:\n";
   $primeNumbers = array(3, 5, 7, 11);
   $primeNumbers[] = 13;
   print_r($primeNumbers);
#
   print "\nFruits:\n";
   $fruits[] = 'Apple';
   $fruits[] = 'Orange';
   $fruits[''] = 'Peach';
   $fruits[''] = 'Banana';
   $fruits['G'] = 'Grape';
   $fruits['7'] = 'Pear';
   $fruits[] = 'Fig';
   print_r($fruits);
#
   print "\nFruits array modified:\n";
   unset($fruits[1]);
   $fruits[1] = 'Orange';
   print_r($fruits);
?>
```

If you run this sample script, you should get:

```
herong> \php\php ArrayTest.php

Library hours:
Array
(
    [Monday - Friday] => 09:00 - 21:00
    [Saturday] => 09:00 - 17:00
    [Sunday] => closed
)

Prime numbers:
Array
(
    [0] => 3
    [1] => 5
    [2] => 7
    [3] => 11
    [4] => 13
)

Fruits:
Array
(
    [0] => Apple
    [1] => Orange
    [] => Banana
    [G] => Grape
    [7] => Pear
    [8] => Fig
)

Fruits array modified:
Array
(
    [0] => Apple
    [] => Banana
    [G] => Grape
    [7] => Pear
    [8] => Fig
    [1] => Orange
)
```

The behavior of the $fruits array is very interesting. Review it carefully.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Arrays - Ordered Maps](#part0057.xhtml)

∟Array Related Built-in Functions

This section provides a summary of built-in functions related arrays and some examples of how to use them.

PHP offers a number of interesting built-in functions to work with arrays:

*   array() - Creates a new array with default keys or with given keys.
*   array\_combine() - Combines two arrays into a new array with the first array as keys and the second as values.
*   array\_count\_values() - Counts the frequencies of values in an array and returns them as an array.
*   array\_key\_exists() - Searches for a key in an array.
*   array\_keys() - Returns an array with all keys of an array.
*   array\_merge() - Merges two arrays into a single array.
*   array\_pad() - Returns a copy of the array padded to size specified by size with value value.
*   array\_pop() - Treats the array like a stack and pops the last value from the stack.
*   array\_push() - Treats the array like a stack and pushes extra values to the end of the stack.
*   array\_rand() - Returns the key for a random entry.
*   array\_search() - Searches for a value in an array.
*   array\_slice() - Extracts a slice of an given array.
*   array\_shift() - Shifts the first value of the array off and returns it, shortening the array by one element and moving everything down.
*   array\_values() - Returns an array with all values of an array.
*   count() - Returns Counts the elements of an array.
*   each() — Returns the current key and value pair from an array and advance the array cursor.
*   explode() - Splits a string into an array by a string. Deprecated in PHP 7.2.
*   min() - Returns the lowest value in that array.
*   max() - Returns the highest value in that array.
*   ksort() - Sorts an array by keys.
*   list() - Assigns array elements to variables.
*   range() - Creates an array containing a range of elements.
*   reset() - Rewinds array's internal pointer to the first element and returns the value of the first array element.
*   sort() - Sorts an array by values.
*   split() - Splits a string into an array by regular expression. Removed in PHP 7.3.

PHP also offers special loop statements to iterate over arrays:

```
foreach($myArray as $value) {}
foreach($myArray as $key=>$value) {}
```

Here is a simple script with a "foreach" statement:

```
<?php
#  ArrayLoop.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "\nLibrary hours:\n";
   $libraryHours = array(
      'Monday - Friday'=>'09:00 - 21:00',
      'Saturday'=>'09:00 - 17:00',
      'Sunday'=>'closed');
   foreach($libraryHours as $day=>$hours) {
      print "   $day: $hours\n";
   }
?>
```

Here is the output:

```
herong> \php\php ArrayLoop.php

Library hours:
   Monday - Friday: 09:00 - 21:00
   Saturday: 09:00 - 17:00
   Sunday: closed
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Arrays - Ordered Maps](#part0057.xhtml)

∟Usage Examples of Array Functions

This section provides usage examples of some commonly used array functions.

Here a PHP script that provides usage examples of some commonly used array functions:

```
<?php
#  ArrayTips.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#

print("Empty array:\n");
$emptyArray = array();
print_r($emptyArray);
print("\n");

print("Array with default keys:\n");
$indexedArray = array("PHP", "Perl", "Java");
print_r($indexedArray);
print("\n");

print("Array with specified keys:\n");
$mappedArray = array("Zero"=>"PHP", "One"=>"Perl", "Two"=>"Java");
print_r($mappedArray);
print("\n");

print("Array with default keys:\n");
$indexedArray = array("PHP", "Perl", "Java");
$value = $indexedArray["1"];
print("The second value: $value\n");
print("\n");

print("Array with specified keys:\n");
$mappedArray = array("Zero"=>"PHP", "One"=>"Perl", "Two"=>"Java");
$value = $indexedArray["2"];
print("The third value: $value\n");
print("\n");

$languages = array();
$languages["Zero"] = "PHP";
$languages["One"] = "Perl";
$languages["Two"] = "Java";
print("Array with inserted values:\n");
print_r($languages);
print("\n");

$mixed = array();
$mixed["Zero"] = "PHP";
$mixed[1] = "Perl";
$mixed["Two"] = "Java";
$mixed["3"] = "C+";
$mixed[""] = "Basic";
print("Array with mixed keys:\n");
print_r($mixed);
print("\$mixed[3] = ".$mixed[3]."\n");
print("\$mixed[\"3\"] = ".$mixed["3"]."\n");
print("\$mixed[\"\"] = ".$mixed[""]."\n");
print("\n");

$mixed = array();
$mixed["Zero"] = "PHP";
$mixed[1] = "Perl";
$mixed["Two"] = "Java";
$mixed["3"] = "C+";
$mixed[""] = "Basic";
$mixed[] = "Pascal";
$mixed[] = "FORTRAN";
print("Array with default keys:\n");
print_r($mixed);
print("\n");

$oldArray = array("Zero"=>"PHP", "One"=>"Perl", "Two"=>"Java");
$newArray = $oldArray;
$refArray = <$oldArray;
$newArray["One"] = "Python";
$refArray["Two"] = "C#";
print("\$newArray[\"One\"] = ".$newArray["One"]."\n");
print("\$oldArray[\"One\"] = ".$oldArray["One"]."\n");
print("\$refArray[\"Two\"] = ".$refArray["Two"]."\n");
print("\$oldArray[\"Two\"] = ".$oldArray["Two"]."\n");
print("\n");

$array = array("Zero"=>"PHP", "One"=>"Perl", "Two"=>"Java");
$array["3"] = "C+";
$array[""] = "Basic";
$array[] = "Pascal";
$array[] = "FORTRAN";
print("Loop on value only:\n");
foreach ($array as $value) {
  print("$value, ");
}
print("\n\n");
print("Loop on key and value:\n");
foreach ($array as $key=>$value) {
  print("[$key] => $value\n");
}
print("\n");

$mixed = array();
$mixed["Two"] = "Java";
$mixed["3"] = "C+";
$mixed["Zero"] = "PHP";
$mixed[1] = "Perl";
$mixed[""] = "Basic";
$mixed[] = "Pascal";
$mixed[] = "FORTRAN";
$mixed["Two"] = "";
unset($mixed[4]);
print("Order of array values:\n");
print_r($mixed);
print("\n");

$var = array(0,0,7);
print("Test 1: ". is_array($var)."\n");
$var = array();
print("Test 2: ". is_array($var)."\n");
$var = 1800;
print("Test 3: ". is_array($var)."\n");
$var = true;
print("Test 4: ". is_array($var)."\n");
$var = null;
print("Test 5: ". is_array($var)."\n");
$var = "PHP";
print("Test 6: ". is_array($var)."\n");
print("\n");

$array = array("PHP", "Perl", "Java");
print_r("Size 1: ".count($array)."\n");
$array = array();
print_r("Size 2: ".count($array)."\n");
print("\n");

$array = array("Zero"=>"PHP", "One"=>"Perl", "Two"=>"Java");
print("Is 'One' defined? ".array_key_exists("One", $array)."\n");
print("Is '1' defined? ".array_key_exists("1", $array)."\n");
print("Is 'Two' defined? ".isset($array["Two"])."\n");
print("Is '2' defined? ".isset($array[2])."\n");
print("\n");

$array = array("Perl", "PHP", "Java", "PHP");
print("Search 1: ".array_search("PHP",$array)."\n");
print("Search 2: ".array_search("Perl",$array)."\n");
print("Search 3: ".array_search("C#",$array)."\n");
print("\n");

$mixed = array();
$mixed["Zero"] = "PHP";
$mixed[1] = "Perl";
$mixed["Two"] = "Java";
$mixed["3"] = "C+";
$mixed[""] = "Basic";
$mixed[] = "Pascal";
$mixed[] = "FORTRAN";
$keys = array_keys($mixed);
print("Keys of the input array:\n");
print_r($keys);
print("\n");

$mixed = array();
$mixed["Zero"] = "PHP";
$mixed[1] = "Perl";
$mixed["Two"] = "Java";
$mixed["3"] = "C+";
$mixed[""] = "Basic";
$mixed[] = "Pascal";
$mixed[] = "FORTRAN";
$values = array_values($mixed);
print("Values of the input array:\n");
print_r($values);
print("\n");

$mixed = array();
$mixed["Zero"] = "PHP";
$mixed[1] = "Perl";
$mixed["Two"] = "Java";
$mixed["3"] = "C+";
$mixed[""] = "Basic";
$mixed[] = "Pascal";
$mixed[] = "FORTRAN";
sort($mixed);
print("Sorted by values:\n");
print_r($mixed);
print("\n");

$mixed = array();
$mixed["Zero"] = "PHP";
$mixed[1] = "Perl";
$mixed["Two"] = "Java";
$mixed["3"] = "C+";
$mixed[""] = "Basic";
$mixed[] = "Pascal";
$mixed[] = "FORTRAN";
ksort($mixed);
print("Sorted by keys:\n");
print_r($mixed);
print("\n");

$old = array();
$old["Zero"] = "PHP";
$old[1] = "Perl";
$old["Two"] = "Java";
$old["3"] = "C+";
$old[""] = "Basic";
$old[] = "Pascal";
$old[] = "FORTRAN";
$keys = array_keys($old);
$values = array_values($old);
print("Combined:\n");
$new = array_combine($keys, $values);
print_r($new);
print("\n");

print("Combined backward:\n");
$new = array_combine($values, $keys);
print_r($new);
print("\n");

$array = array("Google", "Yahoo", "Netscape");
list($first, $second, $third) = $array;
print("Test 1: The third site = $third\n");

# split() was DEPRECATED in PHP 5.3.0, and REMOVED in PHP 7.0.0
# list($month, $date, $year) = split("/","1/1/2006");
list($month, $date, $year) = explode("/","1/1/2006");
print("Test 2: Year = $year\n");
$array = array("Zero"=>"PHP", 1=>"Basic", "One"=>"Perl",
  0=>"Pascal", 2=>"FORTRAN", "Two"=>"Java");
list($first, $second, $third) = $array;
print("Test 3: The third language = $third\n");
print("\n");

$lang = array("Perl", "PHP", "Java",);
$os = array("i"=>"Windows", "ii"=>"Unix", "iii"=>"Mac");
$mixed = array_merge($lang, $os);
print("Merged:\n");
print_r($mixed);
print("\n");

$waitingList = array();
array_push($waitingList, "Jeo");
array_push($waitingList, "Leo");
array_push($waitingList, "Kim");
$next = array_shift($waitingList);
array_push($waitingList, "Kia");
$next = array_shift($waitingList);
array_push($waitingList, "Sam");
print("Current waiting list:\n");
print_r($waitingList);
print("\n");

$waitingList = array();
array_push($waitingList, "Jeo");
array_push($waitingList, "Leo");
array_push($waitingList, "Kim");
$next = array_pop($waitingList);
array_push($waitingList, "Kia");
$next = array_pop($waitingList);
array_push($waitingList, "Sam");
print("Current waiting list:\n");
print_r($waitingList);
print("\n");

# each() was DEPRECATED as of PHP 7.2.0
# $array = array("Zero"=>"PHP", "One"=>"Perl", "Two"=>"Java");
# print("Loop with each():\n");
# reset($array);
# while (list($key, $value) = each($array)) {
#   print("[$key] => $value\n");
# }
# print("\n");

print("Loop with current():\n");
reset($array);
while ($value = current($array)) {
  print("$value\n");
  next($array);
}
print("\n");

print("Integers:\n");
$integers = range(1, 20, 3);
print_r($integers);
print("\n");

print("Characters:\n");
$characters = range("X", "c");
print_r($characters);
print("\n");

$array = array("Zero"=>"PHP", "One"=>"Perl", "Two"=>"Java");
$array = array_pad($array, 6, ">>");
$array = array_pad($array, -8, "---");
print("Padded:\n");
print(join(",", array_values($array)));
print("\n\n");

$array = array("Zero"=>"PHP", "One"=>"Perl", "Two"=>"Java");
$removed = array_splice($array, -2, 2);
print("Remaining chunk:\n");
print_r($array);
print("\n");
print("Removed chunk:\n");
print_r($removed);
print("\n");

$array = array(5, 7, 6, 2, 1, 3, 4, 2);
print("Minimum number: ".min($array)."\n");
print("Maximum number: ".max($array)."\n");
$array = array("Zero"=>"PHP", "One"=>"Perl", "Two"=>"Java");
print("Minimum string: ".min($array)."\n");
print("Maximum string: ".max($array)."\n");
print("\n");

$array = array("Hello!", "Hi!", "Allo!", "Hallo!", "Coucou!");
$key = array_rand($array);
print("Random greeting: ".$array[$key]."\n");
print("\n");
?>
```

Output of the above script:

```
herong> \php\php ArrayTips.php

Empty array:
Array
(
)

Array with default keys:
Array
(
    [0] => PHP
    [1] => Perl
    [2] => Java
)

Array with specified keys:
Array
(
    [Zero] => PHP
    [One] => Perl
    [Two] => Java
)

Array with default keys:
The second value: Perl

Array with specified keys:
The third value: Java

Array with inserted values:
Array
(
    [Zero] => PHP
    [One] => Perl
    [Two] => Java
)

Array with mixed keys:
Array
(
    [Zero] => PHP
    [1] => Perl
    [Two] => Java
    [3] => C+
    [] => Basic
)
$mixed[3] = C+
$mixed["3"] = C+
$mixed[""] = Basic

Array with default keys:
Array
(
    [Zero] => PHP
    [1] => Perl
    [Two] => Java
    [3] => C+
    [] => Basic
    [4] => Pascal
    [5] => FORTRAN
)

$newArray["One"] = Python
$oldArray["One"] = Perl
$refArray["Two"] = C#
$oldArray["Two"] = C#

Loop on value only:
PHP, Perl, Java, C+, Basic, Pascal, FORTRAN,

Loop on key and value:
[Zero] => PHP
[One] => Perl
[Two] => Java
[3] => C+
[] => Basic
[4] => Pascal
[5] => FORTRAN

Order of array values:
Array
(
    [Two] =>
    [3] => C+
    [Zero] => PHP
    [1] => Perl
    [] => Basic
    [5] => FORTRAN
)

Test 1: 1
Test 2: 1
Test 3:
Test 4:
Test 5:
Test 6:

Size 1: 3
Size 2: 0

Is 'One' defined? 1
Is '1' defined?
Is 'Two' defined? 1
Is '2' defined?

Search 1: 1
Search 2: 0
Search 3:

Keys of the input array:
Array
(
    [0] => Zero
    [1] => 1
    [2] => Two
    [3] => 3
    [4] =>
    [5] => 4
    [6] => 5
)

Values of the input array:
Array
(
    [0] => PHP
    [1] => Perl
    [2] => Java
    [3] => C+
    [4] => Basic
    [5] => Pascal
    [6] => FORTRAN
)

Sorted by values:
Array
(
    [0] => Basic
    [1] => C+
    [2] => FORTRAN
    [3] => Java
    [4] => PHP
    [5] => Pascal
    [6] => Perl
)

Sorted by keys:
Array
(
    [] => Basic
    [Two] => Java
    [Zero] => PHP
    [1] => Perl
    [3] => C+
    [4] => Pascal
    [5] => FORTRAN
)

Combined:
Array
(
    [Zero] => PHP
    [1] => Perl
    [Two] => Java
    [3] => C+
    [] => Basic
    [4] => Pascal
    [5] => FORTRAN
)

Combined backward:
Array
(
    [PHP] => Zero
    [Perl] => 1
    [Java] => Two
    [C+] => 3
    [Basic] =>
    [Pascal] => 4
    [FORTRAN] => 5
)

Test 1: The third site = Netscape
Test 2: Year = 2006
Test 3: The third language = FORTRAN

Merged:
Array
(
    [0] => Perl
    [1] => PHP
    [2] => Java
    [i] => Windows
    [ii] => Unix
    [iii] => Mac
)

Current waiting list:
Array
(
    [0] => Kim
    [1] => Kia
    [2] => Sam
)

Current waiting list:
Array
(
    [0] => Jeo
    [1] => Leo
    [2] => Sam
)

Loop with current():
PHP
Basic
Perl
Pascal
FORTRAN
Java

Integers:
Array
(
    [0] => 1
    [1] => 4
    [2] => 7
    [3] => 10
    [4] => 13
    [5] => 16
    [6] => 19
)

Characters:
Array
(
    [0] => X
    [1] => Y
    [2] => Z
    [3] => [
    [4] => \
    [5] => ]
    [6] => ^
    [7] => _
    [8] => `
    [9] => a
    [10] => b
    [11] => c
)

Padded:
---,---,PHP,Perl,Java,>>,>>,>>

Remaining chunk:
Array
(
    [Zero] => PHP
)

Removed chunk:
Array
(
    [One] => Perl
    [Two] => Java
)

Minimum number: 1
Maximum number: 7
Minimum string: Java
Maximum string: Perl

Random greeting: Hello!
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Interface with Operating System

This chapter provides tutorial notes and example codes on PHP interface with the operating system. Topics include $argv\[\] for command line arguments; \`command\`, shell\_exec(), exec(), and system() for external program executions; popen() and proc\_open() to map external program input/output as file handles; resetting maximum execution time and memory.

> [$argv\[\] - Command Line Arguments](#part0063.xhtml)
> 
> [Options to Execute External Programs](#part0064.xhtml)
> 
> [\`command\` - Backtick Operator](#part0065.xhtml)
> 
> [exec() - Execute External Programs](#part0066.xhtml)
> 
> [system() - Execute External Programs](#part0067.xhtml)
> 
> [passthru() - Execute External Programs](#part0068.xhtml)
> 
> [popen() - Execute External Programs](#part0069.xhtml)
> 
> [proc\_open() - Execute External Programs](#part0070.xhtml)
> 
> [memory\_get\_usage() - Memory Usage Info](#part0071.xhtml)
> 
> [set\_time\_limit() - max\_execution\_time](#part0072.xhtml)

Takeaways:

*   Built-in array $argv\[\] can be used to retrieve command line arguments when PHP script files are executed with the 'php' command.
*   Backtick operator, \`command\`, runs a command and returns its output.
*   shell\_exec("command") does the same job as \`command\`.
*   exec("command", $output, $rc) function runs a command and returns its output in $output.
*   passthru("command", $rc) function runs a command and shares its stdout with the calling script.
*   system("command", $rc) function runs a command and shares its stdout with the calling script. But the its stdout is flushed at each output line.
*   $fh = popen("command", "w/r") function runs a command and maps its stdin or stdout to the returning file handle.
*   $ph = proc\_open("command", $io\_spec, $pipes) function runs a command and maps its stdin, stdout and stderr to file handles according the given specs.
*   ini\_set('memory\_limit', '256M') resets maximum memory limit to 256 MB for running the remaining statements of the current script.
*   set\_time\_limit(3600) function resets the maximum execution time to 1 hour = 3600 seconds for running the remaining statements of the current script.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Interface with Operating System](#part0062.xhtml)

∟$argv\[\] - Command Line Arguments

This section provides a tutorial example on how to use the built-in array, $argv\[\], to retrieve command line arguments when PHP script files are executed with the 'php' command.

If a PHP script file is executed through the "php" command, additional command line arguments can be passed to the script through the built-in array: $argv.

For example, if "php test.php arg1 arg2 ..." is used to execute the script file called test.php, the built-in array, $argv, will be populated the following values:

```
$argv[0]: test.php
$argv[1]: arg1
$argv[2]: arg2
$argv[.]: ...
```

Here is an example PHP script that echoes it's command line arguments:

```
herong$ more command-line-arguments.php
<?php
for ($i=0; $i<count($argv); $i++) {
  echo "\$argv[$i] = $argv[$i]\n";
}
?>

herong$ php command-line-arguments.php arg1 arg2 arg3
$argv[0] = command-line-arguments.php
$argv[1] = arg1
$argv[2] = arg2
$argv[3] = arg3

herong$ php command-line-arguments.php "arg1 arg2" arg3
$argv[0] = command-line-arguments.php
$argv[1] = arg1 arg2
$argv[2] = arg3
```

Note that how quotes are used to protect space character as part of a single argument.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Interface with Operating System](#part0062.xhtml)

∟Options to Execute External Programs

This section describes different options to execute external programs on the operting system from PHP scripts: exec(), system(), passthru(), shell\_exec() and open\_process().

If you want to execute an external program on the operating system in a PHP script, you have several options:

**1\. \`\` Backtick Operator** - The Backtick Operator \`command\` function allows you to execute an external program by a given command and return its output.

```
`command`
   returns the program output

stdin:  The standard input is shared with the calling script.
stdout: The standard output from the program is returned.
stderr: The standard error is shared with the calling script.
rc:     The return code from the program is trashed.
```

**2\. shell\_exec() Function** - The shell\_exec() function allows you to execute an external program by a given command and return its output. It works the same way as the Backtick Operator \`\`.

```
shell_exec(string $command)
   returns the program output

stdin:  The standard input is shared with the calling script.
stdout: The standard output from the program is returned.
stderr: The standard error is shared with the calling script.
rc:     The return code from the program is trashed.
```

**3\. exec() Function** - The exec() function allows you to execute an external program by a given command and captures its output into array of lines:

```
exec(string $command[, array &$output[, int &$return_var]])
   returns the last line of the program's standard output

stdin:  The standard input to the program is shared with the calling script.
stdout: The standard output from the program is captured and passed to
        "output" as an array.
stderr: The standard error is shared with the calling script.
rc:     The return code from the program is passed to "return_var".
```

**4\. system() Function** - The system() function allows you to execute an external program by a given command and flush its output to same standard output of the calling script line by line.

```
system(string $command[, int &$return_var])
   returns the last line of the program's standard output

stdin:  The standard input to the program is shared with the calling script.
stdout: The standard output from the program is merged with standard output
        of the calling script. And every output line is flushed.
stderr: The standard error is shared with the calling script.
rc:     The return code from the program is passed to "return_var".
```

**5\. passthru() Function** - The passthru() function allows you to execute an external program by a given command and direct its output to same standard output of the calling script.

```
passthru(string $command[, int &$return_var])
  returns void

stdin:  The standard input to the program is shared with the calling script.
stdout: The standard output from the program is merged with standard output
        of the calling script.
stderr: The standard error is shared with the calling script.
rc:     The return code from the program is passed to "return_var".
```

**6\. popen() Function** - The popen() function allows you to execute an external program by a given command and control its stand input or output as a file handle.

```
$fh = popen(string $command, string $mode);
  returns a file handle represents the standard input or output
  depending on "mode"

pclose($fh);

stdin:  The standard input to the program is mapped to "fh", if "mode" = 'w'.
stdout: The standard output from the program is mapped to "fh",
        if "mode" = 'r'.
stderr: The standard error is shared with the calling script.
rc:     The return code from the program is trashed.
```

**7\. proc\_open() Function** - The proc\_open() function allows you to execute an external program by a given command and have full control of all input and output streams of the program.

```
$ph = proc_open(mixed $command, array $descriptorspec, array &$pipes
   [, string $cwd=NULL[, array $env=NULL[, array $other_options=NULL]]]);
   returns a process handle

$rc = proc_close($ph)
   returns the return code from the program.

descriptorspec: An array to describe how stdin, stdout and stderr
   should be mapped to their source or destinations.

pipes: An array to hold file handles for stdin, stdout and stderr.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Interface with Operating System](#part0062.xhtml)

∟\`command\` - Backtick Operator

This section provides a tutorial example on how to use the shell\_exec() function and the backtick operator \`command\` to invoke an external program. The program's standard output, stdout, is returned as the result of the operator.

The simplest option to execute a program on the operating system from a PHP script is probably to use the Backtick Operator \`command\`, which supports the following features:

*   The command line that invokes the external program can be entered in the backtick quotes directly.
*   The standard output of the program, stdout, is captured and returned by the operator.
*   The standard input of the program, stdin, is shared with the calling script.
*   The standard error of the program, stderr, is shared with the calling script.
*   The return code of the program is trashed.
*   It behaves the same way as the shell\_exec("command") function.

Here are some examples of using the Backtick Operator \`command\` and shell\_exec() function:

```
herong$ php -a
Interactive shell

php > print(`whoami`);
herong

php > $now = `date`;
php > print($now);
Sun Mar  3 08:43:56 CST 2020

php > print(shell_exec('whoami'));
herong

php > $now = shell_exec('date');
php > print($now);
Sun Mar  3 08:43:56 CST 2020

php > $out = `sort`;
Apple
Orange
Banana
<Ctrl>-D

php > echo $out;
Apple
Banana
Orange
```

Note that is to end the standard input, stdin, stream.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Interface with Operating System](#part0062.xhtml)

∟exec() - Execute External Programs

This section provides a tutorial example on how to the exec() function to invoke an external program. The program's standard output, stdout, is returned in an array argument and the last line of stdout is returned as the return value.

The second option to execute a program on the operating system from a PHP script is to use the exec() function:

```
$line = exec(string $command[, array &$output[, int &$rc]])
```

*   The first argument, $command, specifies the command line that invokes the external program.
*   The second optional argument, $output, specifies an array to store the standard output of the program, stdout.
*   The third optional argument, $rc, specifies a string to store the return code of the program.
*   The return value is a string of the last line of the stdout.
*   The standard input of the program, stdin, is shared with the calling script.
*   The standard error of the program, stderr, is shared with the calling script.

Here are some examples of using the exec() function:

```
herong$ php -a
Interactive shell

php > echo exec("whoami");
herong

php > exec("sort", $out, $rc);
Apple
Orange
Banana
<Ctrl>-D

php > var_dump($out);
array(3) {
  [0]=>
  string(5) "Apple"
  [1]=>
  string(6) "Banana"
  [2]=>
  string(6) "Orange"
}

php > echo $rc; ;
0
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Interface with Operating System](#part0062.xhtml)

∟system() - Execute External Programs

This section provides a tutorial example on how to the system() function to invoke an external program. The program's standard output, stdout, and input, stdin, are shared with the calling script. The last line of stdout is returned as the return value.

The third option to execute a program on the operating system from a PHP script is to use the system() function:

```
$line = system(string $command[, int &$rc]]);
```

*   The first argument, $command, specifies the command line that invokes the external program.
*   The second optional argument, $rc, specifies a string to store the return code of the program.
*   The return value is a string of the last line of the stdout.
*   The standard input of the program, stdin, is shared with the calling script.
*   The standard output of the program, $output, is shared with the calling script. But the stdout stream buffer is flushed per each output line. This is perfect for Web server to display output partial output as quickly as possible.
*   The standard error of the program, stderr, is shared with the calling script.

Here are some examples of using the system() function:

```
herong$ php -a
Interactive shell

php > echo system("whoami");
herong
herong

php > system("cat", $rc);
Apple
Apple
Orange
Orange
Banana
Banana
<Ctrl>-D

php > echo $rc; ;
0
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Interface with Operating System](#part0062.xhtml)

∟passthru() - Execute External Programs

This section provides a tutorial example on how to the passthru() function to invoke an external program. The program's standard output, stdout, and input, stdin, are shared with the calling script.

The next option to execute a program on the operating system from a PHP script is to use the passthru() function:

```
passthru(string $command[, int &$rc]])
```

*   The first argument, $command, specifies the command line that invokes the external program.
*   The second optional argument, $rc, specifies a string to store the return code of the program.
*   The return value is null;
*   The standard input of the program, stdin, is shared with the calling script.
*   The standard output of the program, $output, is shared with the calling script. The stdout stream buffer is not flushed.
*   The standard error of the program, stderr, is shared with the calling script.

Here are some examples of using the passthru() function:

```
herong$ php -a
Interactive shell

php > passthru("whoami");
herong

php > passthru("cat", $rc);
Apple
Apple
Orange
Orange
Banana
Banana
<Ctrl>-D

php > echo $rc; ;
0
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Interface with Operating System](#part0062.xhtml)

∟popen() - Execute External Programs

This section provides a tutorial example on how to the popen() function to invoke an external program. The program's standard output, stdout, or input, stdin, is mapped to a file handle to reading or writing.

If you want to execute a program on the operating system and write to the standard input, stdin, or read the standard output, stdout, from the program, you can use the popen() function:

```
$fh = popen(string $command, string $mode);
...
pclose($fh);
```

*   The first argument, $command, specifies the command line that invokes the external program.
*   The second argument, $mode, specifies "w", or "r", to create a file handle to communicate with the program.
*   The return value is the file handle;
*   The standard input of the program, stdin, is mapped to the file handle if $mode="w". Otherwise, it is shared with the calling script.
*   The standard output of the program, $output, is mapped to the file handle if $mode="r". Otherwise, it is shared with the calling script.
*   The standard error of the program, stderr, is shared with the calling script.

Here is an example of using the popen() function to execute an external program, with stdout mapped to a file handle:

```
herong$ more popen-for-output.php
<?php
$fh = popen("sort", "w");
fwrite($fh,"Apple\n");
fwrite($fh,"Orange\n");
fwrite($fh,"Banana\n");
fclose($fh);
?>

herong$ php popen-for-output.php
Apple
Banana
Orange
```

Here is another example of using the popen() function to execute an external program, with stdin mapped to a file handle:

```
herong$ more popen-for-input.php
<?php
$fh = popen("sort", "r");
$out = fread($fh, 2048);
fclose($fh);
echo $out;
?>

herong$ php popen-for-input.php
Apple
Orange
Banana
<Ctrl>-D

Apple
Banana
Orange
?>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Interface with Operating System](#part0062.xhtml)

∟proc\_open() - Execute External Programs

This section provides a tutorial example on how to the proc\_open() function to invoke an external program. The program's stdin, stdout and stderr can be mapped as file handles to any input and output resources.

If you want to execute a program on the operating system and write to the standard input, stdin, or read the standard output, stdout, from the program, you can use the popen() function:

```
$ph = proc_open(mixed $command, array $descriptorspec, array &$pipes
   [, string $cwd=NULL[, array $env=NULL[, array $other_options=NULL]]]);
...

$rc = proc_close($ph);
```

*   The first argument, $command, specifies the command line that invokes the external program.
*   The second argument, $descriptorspec, specifies an array to describe how stdin, stdout and stderr should be mapped to their source or destinations.
*   The third argument, $pipes, specifies an array to hold file handles for stdin, stdout and stderr.
*   The return value of proc\_open() is the process handle.
*   The return value of proc\_close() is the return code of the program.

Here is an example of using the proc\_open() function:

```
herong$ more proc_open-test.php
<?php
$descriptorspec = array(
   0 => array("pipe", "r"),  // stdin is a pipe that the child will read from
   1 => array("pipe", "w"),  // stdout is a pipe that the child will write to
   2 => array("pipe", "w")   // stderr is a pipe that the child will write to
);
$ph = proc_open('sort', $descriptorspec, $pipes);

$fh = $pipes[0];
fwrite($fh,"Apple\n");
fwrite($fh,"Orange\n");
fwrite($fh,"Banana\n");
fclose($fh);

$fh = $pipes[1];
$out = fread($fh, 2048);
fclose($fh);

$rc = proc_close($ph);

echo $out."\n";
echo $rc."\n";
?>

herong$ php proc_open-test.php
Apple
Banana
Orange

0
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Interface with Operating System](#part0062.xhtml)

∟memory\_get\_usage() - Memory Usage Info

This section provides a tutorial example on how to the memory\_get\_usage() function to get memory usage information. ini\_set('memory\_limit', '256M') can be used increase memory limit. unset($o) can be used from objects from memory.

If you are running PHP scripts that use large objects, repeating loops, and/or recursive calls, you may experience system memory issues. There are several functions that allows you to query and manage system memories:

*   ini\_get('memory\_limit') - Returns the current memory upper limit, which is defaulted to 128M.
*   ini\_set('memory\_limit', '256M') - Changes the memory upper limit to 256M.
*   memory\_get\_usage(True) - Returns the total memory allocated to the PHP process. This can be expanded automatically up to the memory upper limit.
*   memory\_get\_usage(False), or memory\_get\_usage() - Returns the memory currently used by the PHP process.
*   unset($o) - Removes a given object from memory.

Here is simple PHP script to demonstrate above functions:

```
<?php
# memory-test.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.

echo "Memory usage report:"."\n";
$total = memory_get_usage(True);
$used = memory_get_usage(False);
echo "   Total memory: ".$total."\n";
echo "   Used memory: ".$used."\n";

echo "Memory test on string object (10Ki) allocatin:"."\n";
$before = memory_get_usage();
$o = str_repeat("Hello PHP!", 1024); # 10,240 byte-string
$after = memory_get_usage();
unset($o);
$final = memory_get_usage();
echo "   Memory used before allocation: ".$before."\n";
echo "   Memory used used by the string: ".($after-$before)."\n";
echo "   Memory freed up by the string: ".($after-$final)."\n";

echo "Increase memory upper limit:"."\n";
$before = ini_get('memory_limit');
ini_set('memory_limit', '256M');
$after = ini_get('memory_limit');
echo "   Memory limit before: ".$before."\n";
echo "   Memory limit after: ".$after."\n";
?>
```

Below is the output of the above script on my Linux computer:

```
herong$ php memory-test.php
Memory usage report:
   Total memory: 262144
   Used memory: 227512

Memory test on string object (10Ki) allocatin:
   Memory used before allocation: 227600
   Memory used used by the string: 10536
   Memory freed up by the string: 10264

Increase memory upper limit:
   Memory limit before: 128M
   Memory limit after: 256M
```

Note that:

*   The system only allocated about 262144 bytes to start the script.
*   The footprint of the PHP engine is about 227512 bytes, very small.
*   A 10240-byte string object used 10264 bytes. So the object overhead is 24 bytes.

If you get a memory overflow error message, you should view the reported memory size and object size that caused the overflow. For example, the following error message says that PHP engine failed to allocate an object of 12,288 bytes (a small object) at line 1,291. So the code before this line has consumed almost the entire memory of 134,217,728 bytes. You need to review the code to ensure there is no memory leaks.

```
Allowed memory size of 134,217,728 bytes exhausted (tried to allocate
12288 bytes) in some-script.php on line 1291.
```

However, the following error message says that PHP engine failed to allocate an object of 331,776 bytes (a large object) at line 1,291. So maybe this time, this large object is questionable. Why this object is so big?

```
Allowed memory size of 268435456 bytes exhausted (tried to allocate
331776 bytes) in other-script.php on line 159.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Interface with Operating System](#part0062.xhtml)

∟set\_time\_limit() - max\_execution\_time

This section provides a tutorial example to demonstrate the maximum execution time limit, which is defaulted to 30 seconds only. You can change the default with a set\_time\_limit() call, or 'max\_execution\_time' setting in php.ini.

If you are running PHP scripts that take longer time to finish, you may experience the "Maximum execution time of 30 seconds exceeded" error.

By default, PHP does not allow any script to run for more than 30 seconds. But you can change this behavior in several ways:

*   Call set\_time\_limit(60\*60) inside script - Resets the maximum execution time to 1 hour = 60\*60 seconds for running this script only.
*   Call set\_time\_limit(0) inside script - Removes the maximum execution time limit, so that the script can run forever. This applies to this script only.
*   Update max\_execution\_time = 3600 inside php.ini - Sets the maximum execution time to 1 hour = 3600 seconds for all scripts.
*   Update max\_execution\_time = 0 inside php.ini - Removes the maximum execution time limit for all scripts.

The following PHP script, Execution\_Time.php, is designed to calculate the execution time and trigger the "Maximum execution time of 10 seconds exceeded" error.

```
<?php
#- Execution_Time.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.

  set_time_limit(10);
  date_default_timezone_set('Europe/Paris');

  $limit = 1000000;
  $step = 1000;
  $time_0 = time();
  $sleep = 0;
  $work = 0;
  for ($i=$step; $i<$limit; $i+=$step) {

    $time_1 = time ();
    $count = find_primes($i);
    $time_2 = time ();
    $work += $time_2-$time_1;

    sleep(1);
    $sleep++;

    print("Total time: ".(time()-$time_0)
      . ", working: ".$work.", sleeping: ".$sleep
      . ". Primes: $count, within: $i\n");
  }

function find_primes($limit) {
  $count = 0;
  $i = 3;
  while ($i<$limit) {
    $isPrime = true;
    $j = 2;
    while ($j<$i) {
      $isPrime = $i%$j > 0;
      if (!$isPrime) break;
      $j++;
    }
    if ($isPrime) $count++;
    $i++;
  }
  return $count;
}
?>
```

If you run it, you will get the "Maximum execution time of 10 seconds exceeded" error sooner or later, depending on your CPU speed.

```
herong$ php Execution_Time.php

Total time: 1, working: 0, sleeping: 1. Primes: 167, within: 1000
Total time: 2, working: 0, sleeping: 2. Primes: 302, within: 2000
Total time: 3, working: 0, sleeping: 3. Primes: 429, within: 3000
Total time: 4, working: 0, sleeping: 4. Primes: 549, within: 4000
Total time: 5, working: 0, sleeping: 5. Primes: 668, within: 5000
Total time: 6, working: 0, sleeping: 6. Primes: 782, within: 6000
Total time: 7, working: 0, sleeping: 7. Primes: 899, within: 7000
Total time: 8, working: 0, sleeping: 8. Primes: 1006, within: 8000
Total time: 10, working: 1, sleeping: 9. Primes: 1116, within: 9000
Total time: 11, working: 1, sleeping: 10. Primes: 1228, within: 10000
Total time: 12, working: 1, sleeping: 11. Primes: 1334, within: 11000
Total time: 14, working: 2, sleeping: 12. Primes: 1437, within: 12000
Total time: 15, working: 2, sleeping: 13. Primes: 1546, within: 13000
Total time: 17, working: 3, sleeping: 14. Primes: 1651, within: 14000
Total time: 18, working: 3, sleeping: 15. Primes: 1753, within: 15000
Total time: 20, working: 4, sleeping: 16. Primes: 1861, within: 16000
Total time: 22, working: 5, sleeping: 17. Primes: 1959, within: 17000
Total time: 24, working: 6, sleeping: 18. Primes: 2063, within: 18000
Total time: 26, working: 7, sleeping: 19. Primes: 2157, within: 19000
Total time: 28, working: 8, sleeping: 20. Primes: 2261, within: 20000
Total time: 30, working: 9, sleeping: 21. Primes: 2359, within: 21000

PHP Fatal error:  Maximum execution time of 10 seconds exceeded
  in /Users/herong/Execution_Time.php on line 36
```

As you can see from the output, the maximum execution time limit applies to accumulated execution time only, not the elapsed time.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Introduction of Class and Object

This chapter provides tutorial notes and example codes on class and object. Topics include introduction of class and object; static variables and methods; superclass and subclass; abstract class and method; interface and trait; overloaded properties and methods; object cloning and serialization; references or aliases of object variables.

> [What Is a Class](#part0074.xhtml)
> 
> [What Is an Object](#part0075.xhtml)
> 
> [What Is a Constructor](#part0076.xhtml)
> 
> [What Is a Static Method](#part0077.xhtml)
> 
> [What Is a Static Variable](#part0078.xhtml)
> 
> [What Is a Superclass and a Subclass](#part0079.xhtml)
> 
> [What Is an Abstract Class](#part0080.xhtml)
> 
> [What Is an Abstract Method](#part0081.xhtml)
> 
> [What Is an Interface](#part0082.xhtml)
> 
> [What Is a Trait](#part0083.xhtml)
> 
> [What Is an Overloaded Property](#part0084.xhtml)
> 
> [What Is an Overloaded Method](#part0085.xhtml)
> 
> [What Is Object Property Iteration](#part0086.xhtml)
> 
> [What Is Object Cloning](#part0087.xhtml)
> 
> [What Is Object Serialization](#part0088.xhtml)
> 
> [What Is in an Object Variable](#part0089.xhtml)
> 
> [Updating Variables Who Share an Object](#part0090.xhtml)
> 
> [Passing Objects as Function Arguments](#part0091.xhtml)

Takeaways:

*   A class is a user defined datatype which is associated with a predefined set of properties and operations (also called methods).
*   An object is a data entity that is created as an instance of a class.
*   A static variables and methods are declared at the class level and can be accessed without any object of the class.
*   A superclass and a subclass is a pair of classes that the second class extends from the first class to inherit all properties and operations from the fist class.
*   An abstract class is considered to be not fully completed and is required to be extended into subclasses to complete the definition.
*   An abstract method only has its calling signature declared with no implementation code and is required to be implemented in subclasses.
*   An interface is a like a "half" abstract class that only declares some abstract methods and has no properties. Any class who wants to implement an interface must implement its abstract methods.
*   A trait is a pseudo class that defines a set of properties and operations. Any class can use a trait to inherit its properties and operations.
*   An overloaded property is indirectly provided through implementations of \_\_set(), \_\_get(), \_\_isset(), and \_\_unset() methods.
*   An overloaded method is indirectly provided through the implementation of the \_\_call() or the \_\_callStatic() method.
*   Object cloning can be done easily by using the "clone" operator.
*   Object serialization and un-serialization can be easily done calling serialize() and unserialize() functions.
*   An object variable actually stores the identifier that points to the object.
*   A variable alias can be created by taking the reference of of the variable.
*   Object variables can be passed as function arguments using pass-by-value mode or pass-by-reference mode.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is a Class

This section describes what is a class - a user defined datatype which is associated with a predefined set of properties and operations (also called methods).

**What Is a Class?** A class is a user defined datatype which is associated with a predefined set of properties and operations (also called methods).

In PHP, a class is declared with the "class" statement block:

```
class class_name {
   public $var_name;
   ...

   function __construct() {
      ...
   }
   public function method_name() {
      ...
   }
   ...
}
```

Notice that:

*   "public $var\_name" is used to declare a property that is publicly accessible.
*   "function \_\_construct() {...}" is used to declare a constructor method that will be executed whenever a new object is instantiated from this class.
*   "public function method\_name() {...}" is used to declare a method that publicly accessible.

Here is a simple PHP class that has no properties and only one public operation:

```
<?php
class HelloClass {
   public function show() {
      echo "Hello world!\n";
   }
}
?>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is an Object

This section describes what is an object - a data entity that is created as an instance of a class. Objects are created with the 'new' operator.

**What Is an Object?** An object is a data entity that is created as an instance of a class.

In PHP, an object is created with the "new" operator, which returns an identifier to the object. For example, the following statement create an object of the "HelloClass" class and assigned the identifier of the object to variable $h:

```
   $h = new HelloClass();
```

In order to retrieve a property value or invoke an operation of object, we need to use the "->" operator attached to the object identifier. For example, the following statement invokes the "show()" operation on the object identified by "$h":

```
   $h->show();
```

Here is a complete PHP script that defines a class, creates an object and invoke an operation on the object:

```
<?php
/* HelloClassDemo.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class HelloClass {
   public function show() {
      echo "Hello world!\n";
   }
}

   $h = new HelloClass();
   $h->show();
?>
```

If you run the above tutorial example, you will get:

```
herong> \php\php HelloClassDemo.php

Hello world!
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is a Constructor

This section describes what is a constructor - a special method to be invoked automatically when a new object is created from a class. The main purpose of the constructor is to provide initial values to object properties.

**What Is a Constructor?** A constructor is a special method to be invoked automatically when a new object is created from a class. The main purpose of the constructor is to provide initial values to object properties.

In PHP, the constructor method must be named as "\_\_construct()". For example, the following class provides a constructor to initialize two properties of the new object:

```
<?php
/* MyMessage.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyMessage {
   public $text;
   public $length;

   function __construct($t) {
      $this->text = $t;
      $this->length = strlen($t);
   }
   public function show() {
      echo $this->text . "\n";
      echo "Number of bytes in the message: " . $this->length . "\n";
   }
}

   $msg = new MyMessage("Hello there!");
   $msg->show();
?>
```

Notice that:

*   "$this" is used as a built-in variable referencing the current object.
*   "$this->text" is used like a variable for both assigning values and retrieving values from the "$text" property.
*   The constructor method can receive parameters from the "new" operation.

If you run the above tutorial example, you will get:

```
herong> \php\php MyMessage.php

Hello there!
Number of bytes in the message: 12
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is a Static Method

This section describes what is a static method - a special method to be invoked without any object to perform a generic operation.

**What Is a Static Method?** A static method is a special method to be invoked without any object to perform a generic operation.

In PHP, a static method is declared with the keyword "static" and invoked with the "::" operator with the class name. For example, the following tutorial example provides a class with two static methods called encode() and mixer():

```
<?php
/* MyEncoder.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyEncoder {
   public static function encode($str) {
      return bin2hex(self::mixer($str));
   }
   private static function mixer($str) {
      $tmp = base64_encode($str);
      $arr = str_split($tmp);
      shuffle($arr);
      $tmp = implode($arr);
      return base64_decode($tmp);
   }
}

  echo MyEncoder::encode("Hello world!");
?>
```

Notice that "self" is used as a keyword to represent the current class.

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MyEncoder.php

f06f52815c9bb21d8641b746
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is a Static Variable

This section describes what is a static variable - a special variable declared at the class level to be shared by all objects of the class.

**What Is a Static Variable?** A static variable is a special variable declared at the class level to be shared by all objects of the class.

In PHP, a static variable is declared with the keyword "static" and invoked with the "::" operator with the class name. For example, the following tutorial example provides a class with a static variable called $count:

```
<?php
/* MyPassGenerator.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyPassGenerator {
   public static $count = 0;
   public $sequence;
   private $password;

   public function __construct() {
      self::$count += 1;
      $this->sequence = self::$count;
      $words = array_merge(range('a', 'z'), range('A', 'Z'));
      shuffle($words);
      $this->password = substr(implode($words), 0, 6);
   }
   public function getPass() {
      return $this->password;
   }
}

  $first = new MyPassGenerator();
  $second = new MyPassGenerator();

  echo "Total # of objects: ". MyPassGenerator::$count ."\n";
  echo "First object: \n";
  echo "   Sequence: " . $first->sequence ."\n";
  echo "   Password: " . $first->getPass() ."\n";
  echo "Second object: \n";
  echo "   Sequence: " . $second->sequence ."\n";
  echo "   Password: " . $second->getPass() ."\n";
?>
```

Notice that "self" is used as a keyword to represent the current class.

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MyPassGenerator.php

Total # of objects: 2
First object:
   Sequence: 1
   Password: BOYXpv
Second object:
   Sequence: 2
   Password: KRzZOS
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is a Superclass and a Subclass

This section describes what is a Superclass and a Subclass - a pair of classes that the second class extends from the first class. An object of subclass inherits all properties and operations from the superclass.

**What Is a Superclass and a Subclass?** A superclass and a subclass is a pair of classes that the second class extends from the first class. An object of subclass inherits all properties and operations from the superclass.

In PHP, a subclass is declared with the keyword "extends" followed by the superclass name. For example, the following tutorial example provides a class MySquare which is extended from class MyRectangle. In this case, MyRectangle is the superclass and MySquare is subclass.

```
<?php
/* MySquare.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyRectangle {
   public $width;
   public $height;

   public function __construct($w,$h) {
      $this->width = $w;
      $this->height = $h;
   }
   public function getArea() {
      return $this->width * $this->height;
   }
}

class MySquare extends MyRectangle {
   public $length;

   public function __construct($l) {
      parent::__construct($l,$l);
      $this->length = $l;
   }
   public function getArea() {
      return $this->length**2;
   }
}

  $object = new MySquare(2.0);

  echo "MySquare object: \n";
  echo "   Class name: ".  get_class($object) ."\n";
  echo "   Length: " . $object->length ."\n";
  echo "   Width: " . $object->width ."\n";
  echo "   Height: " . $object->height ."\n";
  echo "   Area: " . $object->getArea() ."\n";
  echo "   Is subclass of MyRectangle: "
     . is_subclass_of($object, 'MyRectangle') ."\n";
  echo "   Is subclass of MySquare: "
     . is_subclass_of($object, 'MySquare') ."\n";
?>
```

Notice that:

*   "parent" is used as a keyword to represent the superclass.
*   Operations of superclass can be overridden in the subclass. For example getArea() MyRectangle is overridden by getArea() in MySquare.

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MySquare.php

MySquare object:
   Class name: MySquare
   Length: 2
   Width: 2
   Height: 2
   Area: 4
   Is subclass of MyRectangle: 1
   Is subclass of MySquare:
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is an Abstract Class

This section describes what is an abstract class - a class whose definition is considered to be not fully completed and is required to be extended into subclasses to complete the definition. No objects are allowed to be created from an abstract class directly.

**What Is an Abstract Class?** An abstract class is a class whose definition is considered to be not fully completed and is required to be extended into subclasses to complete the definition. No objects are allowed to be created from an abstract class directly.

In PHP, an abstract class is declared with the keyword "abstract". For example, the following tutorial example provides an abstract class MyShape which is extended by subclass MyCircle.

```
<?php
/* MyCircle.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

abstract class MyShape {
   public $x;
   public $y;
   public $type;

   public function __construct($x,$y,$t) {
      $this->x = $x;
      $this->y = $y;
      $this->type = $t;
   }
   public function showType() {
     echo "   Type: " . $this->type ."\n";
   }
   public function showCenter() {
     echo "   Center: " . $this->x .", " . $this->y ."\n";
   }
}

class MyCircle extends MyShape {
   public $radius;

   public function __construct($x,$y,$r) {
      parent::__construct($x,$y,"Circle");
      $this->radius = $r;
   }
   public function showArea() {
      echo "   Area: " . 3.1459*$this->radius**2 ."\n";
   }
}

  $object = new MyCircle(1.0,2.0,0.5);

  echo "MyCircle object: \n";
  $object->showType();
  $object->showCenter();
  $object->showArea();
?>
```

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MyCircle.php

MyCircle object:
   Type: Circle
   Center: 1, 2
   Area: 0.786475
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is an Abstract Method

This section describes what is an abstract method - a method which only has only the calling signature declared with no implementation code. An abstract method must be fully implemented in subclasses. This means that any class with an abstract method must be declared as an abstract class.

**What Is an Abstract Method?** An abstract method is a method which only has only the calling signature declared with no implementation code. An abstract method must be fully implemented in subclasses. This means that any class with an abstract method must be declared as an abstract class.

In PHP, an abstract method is declared with the keyword "abstract". For example, the following tutorial example provides an abstract class MyShape2 with an abstract method showArea() which is required to be implemented by subclasses.

```
<?php
/* MyCircle2.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

abstract class MyShape2 {
   public $x;
   public $y;
   public $type;

   public function __construct($x,$y,$t) {
      $this->x = $x;
      $this->y = $y;
      $this->type = $t;
   }
   public function showType() {
     echo "   Type: " . $this->type ."\n";
   }
   public function showCenter() {
     echo "   Center: " . $this->x .", " . $this->y ."\n";
   }
   abstract public function showArea();
}

class MyCircle2 extends MyShape2 {
   public $radius;

   public function __construct($x,$y,$r) {
      parent::__construct($x,$y,"Circle");
      $this->radius = $r;
   }
   public function showArea() {
      echo "   Area: " . 3.1459*$this->radius**2 ."\n";
   }
}

  $object = new MyCircle2(1.0,2.0,0.5);

  echo "MyCircle object: \n";
  $object->showType();
  $object->showCenter();
  $object->showArea();
?>
```

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MyCircle2.php

MyCircle object:
   Type: Circle
   Center: 1, 2
   Area: 0.786475
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is an Interface

This section describes what is an interface - An interface is a like a 'half' abstract class that only declares some abstract methods and has no properties. Classes that implement an interface must implement all abstract methods declared in the interface.

**What Is an Interface?** An interface is a like a "half" abstract class that only declares some "abstract" methods and has no properties. Classes that implement an interface must implement all abstract methods declared in the interface.

In PHP, an interface is declared with the "interface" statement block. For example, the following tutorial example provides an interface PowerSwitch with one method declared turnSwitch().

```
<?php
/* MyTelevision.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

Interface PowerSwitch {
   public function turnSwitch();
}

class MyTelevision implements PowerSwitch {
   public $status;
   public $size;

   public function __construct($size) {
      $this->size = $size;
      $this->status = "Off";
   }
   public function turnSwitch() {
      if ($this->status=="On") {
         $this->status = "Off";
      } else {
         $this->status = "On";
      }
   }
   public function showInfo() {
      echo "   Size in inches: " . $this->size ."\n";
      echo "   Power status: " . $this->status ."\n";
   }
}

  $object = new MyTelevision(50.0);
  $object->turnSwitch();
  $object->turnSwitch();
  $object->turnSwitch();

  echo "MyTelevision object: \n";
  $object->showInfo();
?>
```

Notice that "implements" is used as a keyword to indicate that a class wants to implement an interface in the "class" declaration.

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MyTelevision.php

MyTelevision object:
   Size in inches: 50
   Power status: On
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is a Trait

This section describes what is a trait - A trait is a pseudo class that defines a set of properties and operations. A trait can not be instantiated to create new objects. It can only be 'used' by one or more classes for the purpose of code sharing.

**What Is a Trait?** A trait is a pseudo class that defines a set of properties and operations. A trait can not be instantiated to create new objects. It can only be "used" by one or more classes for the purpose of code sharing.

In PHP, a trait is declared with the "trait" statement block. classes can share the code defined in a trait with the "use" statement. For example, the following tutorial example provides two traits "MySize" and "MyType" and one class "MyImage" that uses both traits.

```
<?php
/* MyImage.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

trait MySize {
   protected $width;
   protected $height;
   public function showSize() {
      echo "   Size: " . $this->width .", ". $this->height ."\n";
   }
}
trait MyType {
   public $type;
   public function showType() {
      echo "   Type: " . $this->type ."\n";
   }
}

class MyImage {
   use MySize;
   use MyType;
   protected $image;
   public function __construct($w,$h,$t) {
      $this->width = $w;
      $this->height = $h;
      $this->type = $t;
      $this->image = imagecreatetruecolor($this->width,$this->height);
   }
   public function showImage() {
      ob_start();
      imagepng($this->image);
      $buffer = ob_get_contents();
      ob_end_clean();
      echo "   Image: " . base64_encode($buffer) ."\n";
   }
}

  $object = new MyImage(8,8,"JPEG");
  echo "MyImage object: \n";
  $object->showSize();
  $object->showType();
  $object->showImage();
?>
```

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MyImage.php

MyImage object:
   Size: 8, 8
   Type: JPEG
   Image: iVBORw0KGgoAAAANSUhEUgAAAAgAAAAICAIAAABLbSncAAAA
DElEQVQImWNgGB4AAADIAAH4XVuUAAAAAElFTkSuQmCC
```

Note that this tutorial requires cairo graphics library from [cairographics.org](http://cairographics.org).

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is an Overloaded Property

This section describes what is an overloaded property - A class property that is not directly declared at all or not declared as publicly accessible, but it is provided indirectly through implementations of \_\_set(), \_\_get(), \_\_isset(), and \_\_unset() methods.

**What Is an Overloaded Property?** An overloaded property is a class property that is not directly declared at all or not declared as publicly accessible, but it is provided indirectly through implementations of \_\_set(), \_\_get(), \_\_isset(), and \_\_unset() methods.

In PHP, any class can implement the following special methods to support overloaded properties:

*   \_\_set($name, $value) - To be invoked when writing data to an inaccessible property, like "$object->name = $value".
*   \_\_get($name) - To be invoked when reading data from an inaccessible property, like "$value = $object->name".
*   \_\_isset($name) - To be invoked when testing the existence of an inaccessible property, like "isset($object->name)";
*   \_\_unset($name) - To be invoked when removing an inaccessible property from the object, like "unset($object->name)";

For example, the following tutorial example provides class "MyPropertyBag" that shows how to use \_\_set(), \_\_get(), \_\_isset(), and \_\_unset() methods to support overloaded properties.

```
<?php
/* MyPropertyBag.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyPropertyBag {
   public $size = 0;
   private $propertyBag = array();
   public function __set($name, $value) {
      $this->propertyBag[$name] = $value;
      $this->size = count($this->propertyBag);
   }
   public function __get($name) {
      if (array_key_exists($name, $this->propertyBag)) {
         return $this->propertyBag[$name];
      } else {
         return "__undefined__";
      }
   }
   public function __isset($name) {
      return isset($this->propertyBag[$name]);
   }
   public function __unset($name) {
      unset($this->propertyBag[$name]);
      $this->size = count($this->propertyBag);
   }
}

  $object = new MyPropertyBag();
  $object->type = "Book";
  $object->title = "PHP Tutorials";

  echo "MyPropertyBag object: \n";
  echo "   Size: ". $object->size ."\n";
  echo "   Type: ". $object->type ."\n";
  echo "   Title: ". $object->title ."\n";
  echo "   Author: ". $object->author ."\n";
  echo "   isset(Author): ". isset($object->author) ."\n";
?>
```

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MyPropertyBag.php

MyPropertyBag object:
   Size: 2
   Type: Book
   Title: PHP Tutorials
   Author: __undefined__
   isset(Author):
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is an Overloaded Method

This section describes what is an overloaded method - A static method or an instance method that is not directly declared at all or not declared as publicly accessible, but it is indirectly provided through the implementation of the \_\_call() or the \_\_callStatic() method.

**What Is an Overloaded Method?** An overloaded method is a static method or an instance method that is not directly declared at all or not declared as publicly accessible, but it is indirectly provided through the implementation of the \_\_call() or the \_\_callStatic() method.

In PHP, any class can implement the following special methods to support overloaded methods:

*   \_\_call($name, $arguments) - To be invoked when an inaccessible instance method is invoked, like "$object->name($arg1,...)".
*   \_\_callStatic($name, $arguments ) - To be invoked when an inaccessible static method is invoked, like "ClassName::name($arg1,...)".

For example, the following tutorial example provides class "MyPizzaOrder" that shows how to use \_\_call() method to support overloaded methods.

```
<?php
/* MyPizzaOrder.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyPizzaOrder {
   private $size = 0;
   private $toppings = array();
   public function __call($name, $arguments) {
      if (substr($name,0,3) == "add") {
         $value = substr($name,3);
         array_push($this->toppings, $value);
      } else {
         echo "ERROR: Method ".$name."() not supported.\n";
      }
   }
   public function setSize($size) {
      $this->size = $size;
   }
   public function showOrder() {
      echo "   Size: ". $this->size ."\n";
      echo "   Toppings: ". implode(",",$this->toppings) ."\n";
   }
}

   $order = new MyPizzaOrder();
   $order->setSize("Large");
   $order->addSausage();
   $order->addBacon();
   $order->addOnions();
   $order->addMushrooms();
   $order->addPepperoni();

   echo "MyPizzaOrder object: \n";
   $order->showOrder();
   $order->noCheese();
?>
```

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MyPizzaOrder.php

MyPizzaOrder object:
   Size: Large
   Toppings: Sausage,Bacon,Onions,Mushrooms,Pepperoni
ERROR: Method noCheese() not supported.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is Object Property Iteration

This section describes what is property iteration - A PHP built-in feature to access properties of an object in 'foreach' statement in the same as an associative array.

**What Is Object Property Iteration?** Object property iteration is a PHP built-in feature to access properties of an object in "foreach" statement in the same as an associative array.

For example, the following tutorial example provides class "MyCar" that shows how to use "foreach" statement to iterate through all accessible properties of an object.

```
<?php
/* MyCar.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyCar {
   public $maker = "BMW";
   public $model = "i8";
   public $year = "2015";
   public $color = "Silver";
   public $engine = "1.5L 3-cylinder";
   public $horsepower = "357 HP";
   private $price = 136500.0;
}

   $car = new MyCar();
   echo "MyCar object: \n";
   foreach($car as $key => $value) {
      echo "   $key: $value\n";
   }
?>
```

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MyCar.php

MyCar object:
   maker: BMW
   model: i8
   year: 2015
   color: Silver
   engine: 1.5L 3-cylinder
   horsepower: 357 HP
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is Object Cloning

This section describes what is object cloning - An easy way of creating a new object and copying all properties from an old object. PHP also allows you to implement \_\_clone() method to modify properties of the newly created object.

**What Is Object Cloning?** Object cloning is an easy way of creating a new object and copying all properties from an old object. PHP also allows you to implement \_\_clone() method to modify properties of the newly created object.

PHP uses the "clone" operator to clone an object and applies the following rules:

*   "clone $old\_object" operation returns the identifier of a new object cloned from $old\_object.
*   "clone $old\_object" operation copy values of all primitive type properties from $old\_object.
*   "clone $old\_object" operation copy identifiers of all object type properties from $old\_object.
*   If "\_\_clone()" method is available on new object, it will be called after all properties are copied to allow you to modify any property values.

For example, the following tutorial example provides class "MyCarQuote" that shows how to use "\_\_clone" method to alter the behavior of "clone" operation (The quote will go up by $400.00 each time you clone the object).

```
<?php
/* MyCarQuote.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class MyCarQuote {
   public $maker = "BMW";
   public $model = "i8";
   public $year = "2015";
   public $color = "Silver";
   public $engine = "1.5L 3-cylinder";
   public $horsepower = "357 HP";
   private $quote = 123400.0;
   private $cost = 120000.0;
   public function __clone() {
      $this->quote += 400.00;
   }
   public function getQuote() {
      return $this->quote;
   }
}

   $car1 = new MyCarQuote();
   echo "First car specs: \n";
   foreach($car1 as $key => $value) {
      echo "   $key: $value\n";
   }
   $q = $car1->getQuote();
   echo "   -- quote: \$".intval($q/1000).",".($q%1000).".00\n";

   $car2 = clone $car1;
   echo "Second car specs: \n";
   foreach($car2 as $key => $value) {
      echo "   $key: $value\n";
   }
   $q = $car2->getQuote();
   echo "   -- quote: \$".intval($q/1000).",".($q%1000).".00\n";
?>
```

If you run the above tutorial example, you will get something like this:

```
herong> \php\php MyCarQuote.php

First car specs:
   maker: BMW
   model: i8
   year: 2015
   color: Silver
   engine: 1.5L 3-cylinder
   horsepower: 357 HP
   -- quote: $123,400.00
Second car specs:
   maker: BMW
   model: i8
   year: 2015
   color: Silver
   engine: 1.5L 3-cylinder
   horsepower: 357 HP
   -- quote: $123,800.00
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is Object Serialization

This section describes what is object serialization - a process of converting an object into a binary string to be saved in a file, stored in database, passed to another system. The string representing the object can be converted back to a new object that has same property values as the original object using the un-serialization process

**What Is Object Serialization?** Object serialization is a process of converting an object into a binary string to be saved in a file, stored in database, passed to another system. The string representing the object can be converted back to a new object that has same property values as the original object using the un-serialization process.

In PHP, object serialization and un-serialization can be done by calling serialize() and unserialize() functions:

*   "$string = serialize($object)" - Returns the binary string that contains the class name and property name-value pairs.
*   "$object = unserialize($string)" - Returns a new object that has same property values as the original object.

Note that serialize() and unserialize() functions can also be used to serialize and unserialize other types of variables like boolean, integer, float, string, or array.

For example, the following tutorial example shows how to use serialize() function to save an object into a string and unserialize() function to rebuild a copy of the object:

```
<?php
/* ObjectSerilizationTest.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/
class MyCarQuote {
   public $maker = "BMW";
   public $model = "i8";
   public $year = "2015";
   public $color = "Silver";
   public $engine = "1.5L 3-cylinder";
   public $horsepower = "357 HP";
   private $quote = 123400.0;
   private $cost = 120000.0;
   public function getQuote() {
      return $this->quote;
   }
}

   $car1 = new MyCarQuote();
   $string = serialize($car1);
   echo "String from serialized car1: \n".$string."\n";

   $car2 = unserialize($string);
   echo "Car2 rebuilt from the serialization string: \n";
   foreach($car2 as $key => $value) {
      echo "   $key: $value\n";
   }
   $q = $car2->getQuote();
   echo "   -- quote: \$".intval($q/1000).",".($q%1000).".00\n";

   echo "\$car1 == \$car2: ". (($car1==$car2)?"Yes":"No") ."\n";
   echo "\$car1 === \$car2: ". (($car1===$car2)?"Yes":"No") ."\n";
?>
```

If you run the above tutorial example, you will get something like this:

```
herong> \php\php ObjectSerilizationTest.php

String from serialized car1:
O:10:"MyCarQuote":8:{s:5:"maker";s:3:"BMW";s:5:"model";s:2:"i8";
s:4:"year";s:4:"2015";s:5:"color";s:6:"Silver";s:6:"engine";
s:15:"1.5L 3-cylinder";s:10:"horsepower";s:6:"357 HP";
s:17:" MyCarQuote quote";d:123400;s:16:" MyCarQuote cost";d:120000;}

Car2 rebuilt from the serialization string:
   maker: BMW
   model: i8
   year: 2015
   color: Silver
   engine: 1.5L 3-cylinder
   horsepower: 357 HP
   -- quote: $123,400.00
$car1 == $car2: Yes
$car1 === $car2: No
```

The output is interesting:

*   serialize($car1) actually returns a text string. I thought it will return a binary string, may be with compression, to save space.
*   All properties, public or private, are listed with their values are listed in clear text in the serialization string.
*   "$car1 == $car2: Yes" confirms that the object rebuilt from the serialization string has same properties as the original object.
*   "$car1 === $car2: No" confirms that the object rebuilt from the serialization string is a different object than the original object.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟What Is in an Object Variable

This section describes what is in an object variable - An object variable actually contains the object identifier that points to where the object is stored.

**What Is in an Object Variable?** An object variable actually contains the object identifier that points to where the object is stored.

Don't confuse object variables with variable references. They are totally different concepts. If they are used together with objects, you should expect the following behaviors:

*   The content of an object variable, $a, is an identifier to an object
*   When assigning a variable $a to a new variable $b, using ($b = $a), the content of $a is copied to $b as $b's content. If $a's content is an identifier to an object, $b's content is copy of the same identifier to the same object.
*   A variable reference, &$x, returns an alias to the original variable.
*   When assigning a variable reference &x to a new variable $y using ($y = &$x), the new variable become an alias in the alias group of original variable. All aliases are sharing the same content.

To help us understand the relations of objects, identifiers, variables and references, let's consider the following PHP code:

```
$a = new C();
$b = $a;
$x = new C();
$y = &$x;
$z = &$y;
$o = $z;
```

After execution, we should have the following in memory:

```
Variable       Variable               Object
List           Contents               List

   $a -------> Identifier #1 -------> Object #1
                                |
   $b -------> Identifier #1 ---

   $x -------> Identifier #2 -------> Object #2
         |                      |
   $y ---                       |
         |                      |
   $z ---                       |
                                |
   $o -------> Identifier #2 ---
```

As you can see from the above illustration, an object can be shared by two variables in two ways:

*   "Soft Sharing" - Two variables can share an object with the same identifier stored in their own contents, like $a and $b sharing Object #1.
*   "Hard Sharing" - Two variables can share an object with the identifier stored in their shared content, like $x and $y sharing Object #2.

The picture provides a better illustration of the above code and the execution result in memory:

![PHP - Objects, Identifiers, Variables, References](Images/image00230.jpeg)

PHP - Objects, Identifiers, Variables, References

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟Updating Variables Who Share an Object

This section describes what is in an object variable - An object variable actually contains the object identifier that points to where the object is stored.

From previous section, we learned that an object can be shared by two variables in two ways. Now let's see what will the impact on the other variable, if we updating one variable who shares an object with the other object. Here is my understanding:

*   "No Sharing" - Two variables have different identifiers stored in their own contents. Updating the object of one variable will NOT impact the other variable. Updating the content of one variable will NOT impact the other variable.
*   "Soft Sharing" - Two variables have the same identifier stored in their own contents. Updating the object of one variable will impact on the other variable. Updating the content of one variable will NOT impact on the other variable.
*   "Hard Sharing" - Two variables have the same identifier stored in their shared content. Updating the object of one variable will impact on the other variable. Updating the content of one variable will impact on the other variable.

The tutorial example below shows those types object sharing and how updating one variable impacts the other variable:

```
<?php
/* SharedObjectTest.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/

class C {
   public $size;
   public function __construct($s = "Medidum") {
      $this->size = $s;
   }
}
   echo "Test on No Sharing:\n";
   $i = new C();
   $j = new C();
   echo "   (i,j)=(".$i->size.",".$j->size.") before updating \$j\n";
   $j->size = "Large";
   echo "   (i,j)=(".$i->size.",".$j->size
      .") after updating the object of \$j\n";
   $j = new C("Small");
   echo "   (i,j)=(".$i->size.",".$j->size
      .") after updating the content of \$j\n";

   echo "Test on Soft Sharing:\n";
   $a = new C();
   $b = $a;
   echo "   (a,b)=(".$a->size.",".$b->size.") before updating \$b\n";
   $b->size = "Large";
   echo "   (a,b)=(".$a->size.",".$b->size
      .") after updating the object of \$b\n";
   $b = new C("Small");
   echo "   (a,b)=(".$a->size.",".$b->size
      .") after updating the content of \$b\n";

   echo "Test on Hard Sharing:\n";
   $x = new C();
   $y = &$x;
   echo "   (x,y)=(".$x->size.",".$y->size.") before updating \$y\n";
   $y->size = "Large";
   echo "   (x,y)=(".$x->size.",".$y->size
      .") after updating the object of \$y\n";
   $y = new C("Small");
   echo "   (x,y)=(".$x->size.",".$y->size
      .") after updating the content of \$y\n";
?>
```

If you run the above tutorial example, you will get something like this:

```
herong> \php\php SharedObjectTest.php

Test on No Sharing:
   (i,j)=(Medidum,Medidum) before updating $j
   (i,j)=(Medidum,Large) after updating the object of $j
   (i,j)=(Medidum,Small) after updating the content of $j
Test on Soft Sharing:
   (a,b)=(Medidum,Medidum) before updating $b
   (a,b)=(Large,Large) after updating the object of $b
   (a,b)=(Large,Small) after updating the content of $b
Test on Hard Sharing:
   (x,y)=(Medidum,Medidum) before updating $y
   (x,y)=(Large,Large) after updating the object of $y
   (x,y)=(Small,Small) after updating the content of $y
```

The output confirms the my understanding presented earlier.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Introduction of Class and Object](#part0073.xhtml)

∟Passing Objects as Function Arguments

This section describes how to pass objects as function arguments - There are two ways to pass an object into as a function argument: Pass-by-Value and Pass-by-Reference. They follow same rules as the assignment statement.

There are two ways to pass an object into as a function argument: Pass-by-Value and Pass-by-Reference. They follow same rules as the assignment statement.

1\. Pass-by-Value - The function argument variable is declared as pass-by-value, which works like an assignment statement assigning the value of the calling expression to the argument variable. In other words, when the function is called, the calling statement provides a variable (or an expression) whose value is the identifier of the object, and a copy of the value is assigned to the function argument variable. For example:

```
   function f($aa) {...}
   $a = new C();
   f($a);
#     f() receives a copy of the value in $a similar to $aa=$a
```

2\. Pass-by-Reference - The function argument variable is declared as pass-by-reference, which works like an assignment statement assigning the reference of the calling expression to the argument variable. In other words, when the function is called, the calling statement provides a variable (or an expression) whose value is the identifier of the object, and a reference to the variable is assigned to the function argument variable to make it as an alias of the variable. For example:

```
   function f(&$bb) {...}
   $b = new C();
   f($b);
#     f() receives a reference of $b similar to $bb=&$b
```

The tutorial example below shows how to pass objects as function arguments:

```
<?php
/* PassingObjectAsArguments.php
#- Copyright 2015 (c) HerongYang.com. All Rights Reserved.
*/
class C {
   public $size;
   public function __construct($s = "Medidum") {
      $this->size = $s;
   }
}

function updateObject($aa,&$bb) {
   $aa->size = "Large";
   $bb->size = "Large";
   return $aa;
}
function updateContent($aa,&$bb) {
   $aa = new C("Large");
   $bb = new C("Large");
   return $aa;
}

   echo "Test on updating object identified by variable content:\n";
   $a = new C();
   $b = new C();
   $z = updateObject($a,$b);
   echo "   a: ".$a->size."\n";
   echo "   b: ".$b->size."\n";
   echo "   z: ".$z->size."\n";

   echo "Test on updating variable content:\n";
   $a = new C();
   $b = new C();
   $z = updateContent($a,$b);
   echo "   a: ".$a->size."\n";
   echo "   b: ".$b->size."\n";
   echo "   z: ".$z->size."\n";
?>
```

If you run the above tutorial example, you will get something like this:

```
herong> \php\php PassingObjectAsArguments.php

Test on updating object identified by variable content:
   a: Large
   b: Large
   z: Large
Test on updating variable content:
   a: Medidum
   b: Large
   z: Large
```

The output confirms the my understanding presented earlier.

Also note that:

*   The "return" statement only supports the pass-by-value mode. There is no way to return a reference of a variable.
*   Call-time pass-by-reference is no longer supported in PHP. $x = f(&$a) is not valid anymore.
*   Only variables can be passed by references in the calling statement. $x = f("Hello") is not allowed, if f() is declared as f(&$aa).

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Integrating PHP with Apache Web Server

This chapter provides tutorial notes on installing Apache Web server on Windows systems. Topics include downloading and installing Apache 2.4.12 binary distribution; configuring Apache to run PHP as CGI scripts and with Apache PHP load module; testing PHP scripts on Apache server.

> [Downloading Apache 2.4.37 Binary for Windows](#part0093.xhtml)
> 
> [Installing Apache 2.4.37 on Windows Systems](#part0094.xhtml)
> 
> [Publishing HTML Documents as Web Pages](#part0095.xhtml)
> 
> [Starting and Stopping Apache Server](#part0096.xhtml)
> 
> [Configuring Apache for PHP CGI Scripts](#part0097.xhtml)
> 
> [Publishing PHP Scripts as Web Pages](#part0098.xhtml)
> 
> [Permission Error on php-cgi.exe](#part0099.xhtml)
> 
> [Configuring Apache PHP Load Module](#part0100.xhtml)

Takeaways:

*   Apache HTTP Server is the most commonly used open source Web server on the Internet. It is very easy to install and setup on Windows systems.
*   Installation of Apache Web server on Windows is so easy. You just need to download the distribution ZIP file and unzip it.
*   You should select Apache VC15 and 64-bit build to match the PHP engine build that was installed earlier to avoid any compatibility issues.
*   Integrating Apache Web server with PHP engine to run PHP scripts with php-cgi.exe requires several changes in the Apache configuration file.
*   Running PHP scripts as Web pages using Apache PHP load module is more efficient and more secure.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Integrating PHP with Apache Web Server](#part0092.xhtml)

∟Downloading Apache 2.4.37 Binary for Windows

This section describes how to download Apache 2.4.37 binary distribution for Windows. You should select the VC15 and 64-bit build to match the PHP engine build.

In order to serve PHP scripts as Web pages, you need to have a Web server running and integrated with the PHP engine. The most popular Web server today is Apache (HTTP Server). Here is what I did to download Apache 2.4.37 binary distribution for Windows:

1\. Go to Apache Lounge Website at [apachelounge.com/](https://www.apachelounge.com/).

2\. Click "Downloads" from the left side menu. You see the download page.

3\. Click "VC15" from the left side menu, because I downloaded and installed PHP VC15 (Visual C++ v15) build.

4\. Select "httpd-2.4.37-win64-VC15.zip" under the Apache 2.4.37 Win64 heading, because I downloaded and installed PHP 64-bit build to start downloading.

5\. Save the downloaded file, httpd-2.4.37-win64-VC15.zip, 17,764,403 bytes, in a temporary directory.

You should select the VC15 and 64-bit build to match the PHP engine build that was installed earlier.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Integrating PHP with Apache Web Server](#part0092.xhtml)

∟Installing Apache 2.4.37 on Windows Systems

This section describes how to install Apache 2.4.37 binary distribution on Windows systems. The server root directory setting needs to be changed to match the installation directory.

After downloaded Apache HTTP Server 2.4.37, I continued to install it on my Windows system:

1\. Unzip httpd-2.4.37-win64-VC15.zip. You see a sub-directory called ".\\Apache24".

2\. Copy and rename the ".\\Apache24" sub-directory to \\apache.

3\. Open \\apache\\conf\\httpd.conf in an text editor and change the server root directory to match my installation directory by commenting out the original setting and copying it a new setting:

```
# Define SRVROOT "c:/Apache24"
Define SRVROOT "c:/apache"
```

4\. Start Apache Web server by running the following command:

```
herong> \apache\bin\httpd
```

4\. Open a Web browser with http://localhost. You should see the Apache server default home page saying:

```
It works!
```

Congratulations, Apache Web server is stalled and working!

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Integrating PHP with Apache Web Server](#part0092.xhtml)

∟Publishing HTML Documents as Web Pages

This section describes how to publish a HTML document on the Apache HTTP server.

With Apache server running, I am ready to publish HTML documents as static Web pages. Here is a simple HTML document, hello.html, created with a text editor:

```
<html>
<body>
Hello world!
</body>
</html>
```

To publish this HTML document as a Web page, I copied it to the Apache document directory \\apache\\htdocs:

```
herong> copy hello.html \apache\htdocs
```

Then I viewed the page at: http://localhost/hello.html, and got the page content displayed correctly.

```
Hello world!
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Integrating PHP with Apache Web Server](#part0092.xhtml)

∟Starting and Stopping Apache Server

This section describes how to start and stop the Apache server using start and stop scripts. Windows Task Manager can also be used to stop the Apache server.

1\. The normal way to start and stop the Apache server is to use the ApacheMonitor program by running the following command:

```
herong> \apache\bin\ApacheMonitor.exe
```

2\. Check the task bar area. You will see an Apache monitor icon showing up.

3\. Click on the Apache monitor icon. You will see 3 sub menu items: Start, Stop and Restart. You can use them any time to start and stop the Apache server.

4\. Another way to know if the Apache server is running or not is to use Windows Task Manager. Run Windows Task Manager, and click the Processes tab. If you see "httpd.exe" is listed as a running process, you know that your Apache server is running.

4\. Of course, Windows Task Manager can also be used to stop the Apache server. Select "httpd.exe" on Processes tab on Windows Task Manager, and click the "End Process" button. Then click "Yes" on the warning message to terminate "httpd.exe". Repeat the process again if see more than one instances of "httpd.exe".

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Integrating PHP with Apache Web Server](#part0092.xhtml)

∟Configuring Apache for PHP CGI Scripts

This section describes how to configure Apache server to support PHP CGI scripts.

With both PHP engine and Apache Web server installed on my Windows system, I continued to configure the Apache server to support PHP CGI scripts:

1\. Open the Apache configuration file, \\apache\\conf\\httpd.conf, in a text editor

2\. First I have to define a CGI script directory alias, mapping an Apache document directory to a real directory where php-cgi.exe is located. Go to alias\_module section and add one line:

```
<IfModule alias_module>
...
   ScriptAlias /cgi-bin-php/ "/local/php/"
</IfModule>
```

3\. Then I need to add an access control section for this directory as:

```
<Directory "/local/php/">
     AllowOverride None
     Options None
     Require all granted
</Directory>
```

4\. Next, I have to define a new MIME type to support the .php file extension. Go to mime\_module section and one line:

```
<IfModule mime_module>
...
    AddType application/x-httpd-php .php
</IfModule>
```

5\. The last setting is to tell Apache to serve the new MIME type with php-cgi.exe located in the directory alias /cgi-bin-php/: At the root level below the LoadModule section, define an "Action" entry:

```
#LoadModule xml2enc_module modules/mod_xml2enc.so

Action application/x-httpd-php "/cgi-bin-php/php-cgi.exe"
```

6\. The configuration changes are done. Now restart the Apache server by closing the following command line window and re-enter it again:

```
herong> \apache\bin\httpd
```

Another way to integrate Apache with PHP is to set PHP as a load module. This is more efficient than the CGI script interface. But for my personal testing purpose, the CGI script interface is good enough.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Integrating PHP with Apache Web Server](#part0092.xhtml)

∟Publishing PHP Scripts as Web Pages

This section describes how to publish PHP scripts as Web pages on the Apache server.

The verify my Apache and PHP integration, here what I did to publish a PHP script as a Web page on the Apache server:

1\. I wrote this simple PHP script, hello.php, with a text editor:

```
<html>
<body>
<?php echo "Hello world!"; ?> - PHP script.
</body>
</html>
```

2\. Copied this script file to Apache document directory, \\apache\\htdocs:

```
herong> copy hello.php \apache\htdocs
```

3\. View it with a Web browser at http://localhost/hello.php. The Web page resulted from the PHP script shows up correctly:

```
Hello world! - PHP script.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Integrating PHP with Apache Web Server](#part0092.xhtml)

∟Permission Error on php-cgi.exe

This section describes the error of 'You don't have permission to access /cgi-bin-php/php-cgi.exe/hello.php on this server.' It is caused by the syntax change in the PHP directory access permission configuration settings.

Note that Apache Web server configuration setting has changed the directory access control syntax between 2.2 and 2.4.

If you are still using the old syntax on the PHP directory:

```
<Directory "/local/php/">
    AllowOverride None
    Options None
    Order allow,deny
    Allow from all
</Directory>
```

You will see the following error in the Web browser:

```
Forbidden
You don't have permission to access
   /cgi-bin-php/php-cgi.exe/hello.php on this server.
```

You must use the new syntax to grant access permission to the PHP directory:

```
<Directory "/local/php/">
   AllowOverride None
   Options None
   Require all granted
</Directory>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Integrating PHP with Apache Web Server](#part0092.xhtml)

∟Configuring Apache PHP Load Module

This section describes how to configure Apache to use Apache PHP load module to run PHP scripts as Web pages. Apache PHP load module is more secure than CGI scripts.

Running PHP pages as CGI scripts is ok for testing purpose. But you should run PHP pages with Apache PHP load module. It's more efficient and more secure.

Here what I did to try to configure the Apache 2.4 server to use the Apache PHP load module. Note that I was using PHP 7.0.

1\. Open on \\apache\\conf\\httpd.conf and remove all changes I did for supporting PHP CGI scripts to my Apache server secure.

2\. Go to the LoadModule section and add:

```
LoadModule php7_module "C:/local/php/php7apache2_4.dll"
PHPIniDir "C:/local/php"
```

3\. Go to mime\_module section and add a mime type as:

```
<IfModule mime_module>
...
    AddType application/x-httpd-php .php
</IfModule>
```

4\. Restart the Apache server and run the PHP script again http://localhost/hello.php. The Web page resulted from the PHP script shows up correctly:

```
Hello world! - PHP script.
```

Congratulation, PHP scripts can be executed on the Apache server by the Apache PHP load module now!

Note that if you are still running PHP 5, you need to use the following setting:

```
LoadModule php5_module "C:/local/php/php5apache2_4.dll"
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Retrieving Information from HTTP Requests

This chapter provides tutorial examples and notes about HTTP request. Topics include retrieving information from $\_GET, $\_POST, $\_COOKIE, $\_REQUEST, $\_SERVER; promoting and registering $\_REQUEST keys and values as global variables.

> [Predefined Variables Related to HTTP Requests](#part0102.xhtml)
> 
> [Operating System Information in $\_SERVER](#part0103.xhtml)
> 
> [Web Server Information in $\_SERVER](#part0104.xhtml)
> 
> [Information in $\_GET and $\_REQUEST](#part0105.xhtml)
> 
> [Registering $\_REQUEST Keys as Global Variables](#part0106.xhtml)

Takeaways:

*   $\_GET contains information submitted with the GET method.
*   $\_POST contains information submitted with the POST method.
*   $\_COOKIE contains information stored as cookies.
*   $\_REQUEST is the sum of $\_GET, $\_POST, and $\_COOKIE.
*   $\_SERVER contains information from the HTTP request, the Web server and the operating system.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Retrieving Information from HTTP Requests](#part0101.xhtml)

∟Predefined Variables Related to HTTP Requests

This section describes predefined variables, $\_GET, $\_POST, $\_COOKIE, $\_REQUEST, and $\_SERVER, that contains information included in the HTTP request received by the PHP engine from the Web server.

When the PHP engine is used on a Web server to handle a HTTP request, it converts information submitted in the HTTP request as predefined variables and pass them to PHP script.

1\. $\_GET - Associate array of HTTP request information submitted with the GET method. By default, all browsers submit HTTP requests with the GET method. Input information collected from Web page forms will be organized into pairs of names and values, which will be attached to the end of the URL in the first line of the HTTP request.

When the PHP engine receives a HTTP request, it will take those pairs of names and values from the end of the request URL and store them in the $\_GET array as keys and values.

2\. $\_POST - Associate array of HTTP request information submitted with the POST method. If a Web page uses the POST method to submit input information collected from its form. The browser will organize input into names and values and attach them as the HTTP request body.

When the PHP engine receives a HTTP request, it will take those pairs of names and values from the request body and store them in the $\_POST array as keys and values.

3\. $\_COOKIE - Associate array of submitted as cookies in the HTTP request. If a browser has cookies received previously from a Web server, it will automatically attach them in the next HTTP request to the same Web server.

When the PHP engine receives a HTTP request, it will take cookie names and cookie values from the request and store them in the $\_POST array as keys and values.

4\. $\_REQUEST - Associate array of all elements from $\_GET, $\_POST, and $\_COOKIE. To help you to get HTTP request input information in a single place, the PHP engine automatically combines all keys and values from $\_GET, $\_POST, and $\_COOKIE into $\_REQUEST.

5\. $\_SERVER - Associate array of information from the Web server and the HTTP request. When the PHP engine receives a HTTP request, it will take other information included in the request and store it in the $\_SERVER array as keys and values. For example, the following keys and values represent information received from the HTTP request:

```
   REDIRECT_HANDLER = application/x-httpd-php
   REDIRECT_STATUS = 200
   HTTP_HOST = localhost
   HTTP_CONNECTION = keep-alive
   HTTP_UPGRADE_INSECURE_REQUESTS = 1
   HTTP_USER_AGENT = Mozilla/5.0 (Windows NT 6.1; Win64; x64) ...
   HTTP_ACCEPT = text/html,application/xhtml+xml,application/xml;..
   HTTP_REFERER = http://localhost/
   HTTP_ACCEPT_ENCODING = gzip, deflate, br
   HTTP_ACCEPT_LANGUAGE = en-US,en;q=0.9
   ......
```

The PHP engine also gathers additional information from the Web server and store it in the $\_SERVER array as keys and values. For example, the following keys and values represent information received from the Web server:

```
   SERVER_SIGNATURE =
   SERVER_SOFTWARE = Apache/2.4.37 (Win64)
   SERVER_NAME = localhost
   SERVER_ADDR = ::1
   SERVER_PORT = 80
   REMOTE_ADDR = ::1
   DOCUMENT_ROOT = C:/apache/htdocs
   REQUEST_SCHEME = http
   CONTEXT_PREFIX = /cgi-bin-php/
   CONTEXT_DOCUMENT_ROOT = /local/php/
   ......
```

The PHP engine also gathers additional information from the operating system where the PHP engine is running and store it in the $\_SERVER array as keys and values. For example, the following keys and values represent information received from the operating system:

```
   SystemRoot = C:\windows
   COMSPEC = C:\windows\system32\cmd.exe
   PATHEXT = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC
   WINDIR = C:\windows
   ...
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Retrieving Information from HTTP Requests](#part0101.xhtml)

∟Operating System Information in $\_SERVER

This section provides a tutorial example on how to dump operating system information stored in the $\_SERVER array.

To help us understand how predefined variables, $\_GET, $\_POST, $\_COOKIE, $\_REQUEST, and $\_SERVER, work, I wrote the following tutorial example script:

```
<?php
#  HttpRequestDetails.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "<pre>\n";
   print "\nContents of \$_GET:\n";
   foreach ($_GET as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_POST:\n";
   foreach ($_POST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_COOKIE:\n";
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_REQUEST:\n";
   foreach ($_REQUEST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_SERVER:\n";
   foreach ($_SERVER as $k => $v) {
      print "   $k = $v\n";
   }
   print "</pre>\n";
?>
```

If you run this example script standalone without using any Web server, you should get:

```
<pre>

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:

Contents of $_REQUEST:

Contents of $_SERVER:
   ALLUSERSPROFILE = C:\ProgramData
   CommonProgramFiles = C:\Program Files\Common Files
   CommonProgramFiles(x86) = C:\Program Files (x86)\Common Files
   CommonProgramW6432 = C:\Program Files\Common Files
   ComSpec = C:\windows\system32\cmd.exe
   configsetroot = C:\windows\ConfigSetRoot
   FP_NO_HOST_CHECK = NO
   ProgramData = C:\ProgramData
   ProgramFiles = C:\Program Files
   ProgramFiles(x86) = C:\Program Files (x86)
   ProgramW6432 = C:\Program Files
   PROMPT = $P$G
   ......
</pre>
```

Note that $\_GET, $\_POST, $\_COOKIE, and $\_REQUEST are all empty, because we executed the script without any HTTP request. $\_SERVER contains only information gathered from the operating system.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Retrieving Information from HTTP Requests](#part0101.xhtml)

∟Web Server Information in $\_SERVER

This section provides a tutorial example on how to dump Web server information stored in the $\_SERVER array.

Now, let's run HttpRequestDetails.php on the local Apache Web server. First copy HttpRequestDetails.php to \\apache\\htdocs, then run Internet Explorer (IE) with http://localhost/HttpRequestDetails.php. You should get:

```
Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:

Contents of $_REQUEST:

Contents of $_SERVER:
   REDIRECT_HANDLER = application/x-httpd-php
   REDIRECT_STATUS = 200
   HTTP_HOST = localhost
   HTTP_CONNECTION = keep-alive
   HTTP_UPGRADE_INSECURE_REQUESTS = 1
   HTTP_REFERER = http://localhost/
   HTTP_ACCEPT_ENCODING = gzip, deflate, br
   HTTP_ACCEPT_LANGUAGE = en-US,en;q=0.9
   SystemRoot = C:\windows
   COMSPEC = C:\windows\system32\cmd.exe
   PATHEXT = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC
   WINDIR = C:\windows
   SERVER_SIGNATURE =
   SERVER_SOFTWARE = Apache/2.4.37 (Win64)
   SERVER_NAME = localhost
   SERVER_ADDR = ::1
   SERVER_PORT = 80
   REMOTE_ADDR = ::1
   DOCUMENT_ROOT = C:/apache/htdocs
   ......
```

Note that $\_GET, $\_POST, $\_COOKIE, and $\_REQUEST are still all empty, because HTTP request contains no information submitted using the GET or POST method. And there are no cookies in the HTTP request.

However, other information contained in the HTTP request and gathered from the Web server is stored in the $\_SERVER array now. For example, "DOCUMENT\_ROOT = c:/apache/htdocs" is piece of information from the Web server telling us that the Web server picks up HTTP documents and scripts from the c:/apache/htdocs directory.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Retrieving Information from HTTP Requests](#part0101.xhtml)

∟Information in $\_GET and $\_REQUEST

This section provides a tutorial example on how to dump information stored in the $\_GET array and the $\_REQUEST array.

Now try this URL, http://localhost/HttpRequestDetails.php?lang=PHP&search. You should get:

```
Contents of $_GET:
   lang = PHP
   search =

Contents of $_POST:

Contents of $_COOKIE:

Contents of $_REQUEST:
   lang = PHP
   search =

Contents of $_SERVER:
   ......
   QUERY_STRING = lang=PHP&search
   ......
```

Notice that:

*   "?lang=PHP&search" attached at the end of the URL represents information submitted with the GET method.
*   "?lang=PHP&search" is parsed by the PHP engine into 2 pairs of names and values and stored in the $\_GET array.
*   The PHP engine copied the same information from $\_GET to $\_REQUEST.

Note that if you are migrating scripts older than PHP 5.4.0, you may see a sudden change on how quotes are passed in $\_POST, $\_COOKIE, and $\_REQUEST.

Before PHP 5.4.0, the PHP engine has a default option called "magic\_quotes\_gpc", which turns on the "magic\_quotes" state for GPC GPC (Get/Post/Cookie) operations. When "magic\_quotes" state is on, all ' (single-quote), " (double quote), \\ (backslash) are escaped with a backslash automatically.

So scripts older than PHP 5.4.0 are using stripslashes() function calls to clean up values received in $\_POST, $\_COOKIE, and $\_REQUEST.

Now you must remove those stripslashes() function calls from older script. If not removed, values received from client side may get damaged. For example, "\\\\" will be received as "\\".

Exercise: Try to find a way to test how to provide information with the POST method and how to provide cookies.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Retrieving Information from HTTP Requests](#part0101.xhtml)

∟Registering $\_REQUEST Keys as Global Variables

This section provides a tutorial example on how to promote (or register) keys and values in the $\_REQUEST array as global variables so that you don't have to use the array notation to access their values.

To access information stored in the $\_REQUEST array, you can use the normal array element notation, $\_REQUEST\[$key\]. For example, $\_REQUEST\["lang"\] would return "PHP" in the example script used in the previous section.

But key-value pairs in $\_REQUEST can also be promoted (or registered) as standalone global variables using one of two ways described below:

1\. To register $\_REQUEST key-value pairs as global variables on the entire server, edit \\php\\php.ini and set:

```
register_globals = on
```

With this setting, the PHP engine will automatically create a global variable for each key in $\_REQUEST with the key name as the variable name. Of course, the value associated with the key will be copied to the variable at the same time. For example, if $\_REQUEST\["lang"\] contains "PHP", $lang will be created with the value "PHP".

2\. To register $\_REQUEST key-value pairs as local variables for the current script execution only, use the following function:

```
import_request_variables("GPC",$prefix);
```

where "GPC" indicates that key-value pairs copied from $\_GET, $\_POST and $\_COOKIE will be registered as local variables. $prefix defines a prefix string that are to be added to variable names.

To test this, I turned on the register\_globals setting in php.ini and wrote this sample script, RequestVariables.php:

```
<?php
#  RequestVariables.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "<pre>\n";
   print "\nContents of \$_REQUEST:\n";
   foreach ($_REQUEST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nLocal imported variables from the request:\n";
   import_request_variables("GPC","r_");
   print "   \$r_lang = $r_lang\n";
   print "   \$r_search = $r_search\n";
#
   print "\nGlobally imported variables from the request:\n";
   print "   \$lang = $lang\n";
   print "   \$search = $search\n";
   print "</pre>\n";
?>
```

Open this script with http://localhost/RequestVariables.php?lang=PHP&search, you will get:

```
Contents of $_REQUEST:
   lang = PHP
   search =

Local imported variables from the request:
   $r_lang = PHP
   $r_search =

Globally imported variables from the request:
   $lang = PHP
   $search =
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Creating and Managing Sessions in PHP Scripts

This chapter provides tutorial examples and notes about session. Topics include understanding of the session concept; writing scripts to create and use a session; storing data in the current session; managing session IDs as cookies and URL transparent parameters.

> [What Is a Session](#part0108.xhtml)
> 
> [How Sessions Are Supported in PHP](#part0109.xhtml)
> 
> [SessionPage\*.php - Session Test Script Pages](#part0110.xhtml)
> 
> [Running Session Test Script Pages](#part0111.xhtml)
> 
> [Managing Session IDs without Cookies](#part0112.xhtml)
> 
> [Where Is Session Data Stored](#part0113.xhtml)

Takeaways:

*   A session ID must be passed between HTTP requests and responses to link them into a single sequence.
*   Passing the session ID as a cookie value is more secure.
*   Passing the session ID as a transparent URL variable is less secure, because the session ID will be displayed in the Web page address field.
*   You must call the built-in function, session\_start(), at the beginning of the PHP script to start a new session, or continue with an existing session.
*   The built-in array, $\_SESSION, can be used to pass information from one script to another script that shares the same session as the first script.
*   Session data is persisted to the hard disk permanently on the server side.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Creating and Managing Sessions in PHP Scripts](#part0107.xhtml)

∟What Is a Session

This section describes the session concept used by Web server side applications. A Web session represents a series of HTTP requests and responses exchanged between a browser and a Web server. Usually, a cookie is used to carry the ID of a Web session.

**What Is a Session?** A session is an abstract concept to represent a series of HTTP requests and responses exchanged between a specific Web browser and a specific Web server. The session concept is very useful for Web based applications to pass and share information from one Web page (request) to another Web page (request).

Since the current design of HTTP protocol does not support session concept, all Web server side scripting technologies, including PHP, have designed their own ways to support the session concept. The key design element of session support is about how to identify a session with an ID (identification) and how to maintain the session ID. One common way to maintain the session ID is use the cookie technology. The following diagram shows you how to do this:

```
           Server                Browser
ID created  | <-- Request #1  --- |
            | --- Response #1 --> | ID kept as cookie
            | <-- Request #2  --- | ID send back to server
            | --- Response #2 --> |
            | <-- Request #3  --- | ID send back to server
            | --- Response #3 --> |
            |     ......          |
```

The session concept should be managed by the server. When the first request comes from a browser on a client host, the server should create a new session, and assigns a new session ID. The session ID will be then sent back to the same browser as a cookie. The browser will remember this ID, and send the ID back to the server in subsequent requests. When the server receives a request containing the same session ID, it knows that this request is a continuation of an existing session.

When the server receives a request from a browser on a new client host (request without a session ID), the server should not only create a new session ID, it should also create a new session object associated with the new session ID. This session object should become the storage place for different requests of the same session to store and share information between requests containing the same session ID.

If there is no subsequent request coming back for a long time for a particular session ID, that session should be timed out. After the session has been timed out, if the browser comes back again with the same session ID, the server should give an invalid session error.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Creating and Managing Sessions in PHP Scripts](#part0107.xhtml)

∟How Sessions Are Supported in PHP

This section describes how sessions are supported in PHP. Session IDs are passed as cookies or GET/POST variables. session\_start() is the built-in function to start a session. $\_SESSION is the built-in array to manage session data.

PHP supports Web sessions with following main elements in the configuration file, php.ini:

1\. session.use\_cookies = 1/0 - A setting to determine if the session ID should be stored and managed as a cookie.

*   session.use\_cookies = 1 (the default setting) - Managing the session ID as a cookie. The session ID is stored in a cookie with a default name of "PHPSESSID". This "PHPSESSID" cookie will be automatically inserted into HTTP responses and retrieved from HTTP requests by the PHP engine.
*   session.use\_cookies = 0 - Stop storing the session ID as a cookie.

2\. session.use\_trans\_sid = 1/0 - A setting in the configuration file, php.ini, to control if the session ID should be stored and managed transparently as a parameter in the URL.

*   session.use\_trans\_sid = 1 - Managing the session ID as an extra transparent parameter in the URL. The extra URL parameter contains the session ID value with a default name of "PHPSESSID". This "PHPSESSID" parameter will be automatically inserted into all links in the HTTP response, and retrieved from HTTP requests by the PHP engine.
*   session.use\_trans\_sid = 0 (the default setting) - Stop storing the session ID as a URL transparent parameter.

3\. session.save\_handler = files/mm/user - A setting in the configuration file, php.ini, to control how session data should be stored.

*   session.save\_handler = files (the default setting) - Storing session data as files in a directory defined in the session.save\_path = "/tmp" setting.
*   session.save\_handler = mm - Storing session data in shared memory.
*   session.save\_handler = user - Storing session data through user-defined functions.

4\. session\_start() - A built-in function to create a new session or resume an existing session. When session\_start() is called, the PHP engine will check the current HTTP request to see if an existing session ID is included or not.

*   If no session ID is found, the PHP engine will create a new session with a new session ID.
*   If a session ID is found, the PHP engine will restore the session identified by this session ID. If the restored session has been timed out, an error will be issued.

5\. $\_SESSION - A built-in array attached to the current session acting as a storage. You can store any number of key-value pairs in $\_SESSION in a PHP script and retrieve them later in another script if it shares the same session as the first script.

6\. session\_name() - A built-in function to set and get the name of the current session.

7\. session\_id() - A built-in function to set and get the session ID of the current session.

8\. session\_destroy() - A built-in function to destroy the current session. When the current session is destroyed, information stored in $\_SESSION will be removed.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Creating and Managing Sessions in PHP Scripts](#part0107.xhtml)

∟SessionPage\*.php - Session Test Script Pages

This section provides a tutorial example on how to write multiple script pages and use the session concept to make them work together.

To help us testing the session concept, I wrote 3 PHP scripts.

1\. SessionPage1.php:

```
<?php
#  SessionPage1.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   session_start();
   $quantity = 3;
   $_SESSION['quantity'] = $quantity;
   if (isset($_SESSION['count'])) {
      $count = $_SESSION['count'];
   } else {
      $count = 0;
   }
   $count++;
   $_SESSION['count'] = $count;
#
   print "<pre>\n";
   print "\nI am buying $quantity PHP books.\n";

   print "\n<a href=SessionPage2.php>Next</a>\n";
   print "\nCounter = $count\n";
   print "Session name = ".session_name()."\n";
   print "Session id = ".session_id()."\n";
#
   print "\nContents of \$_GET:\n";
   foreach ($_GET as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_POST:\n";
   foreach ($_POST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_COOKIE:\n";
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }
   print "</pre>\n";
?>
```

2\. SessionPage2.php:

```
<?php
#  SessionPage2.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   session_start();
   $quantity = $_SESSION['quantity'];
   $price = 9.99;
   $_SESSION['price'] = $price;
   $count = $_SESSION['count'];
   $count++;
   $_SESSION['count'] = $count;
#
   print "<pre>\n";
   print "\nI am buying $quantity PHP books.\n";
   print "The unit price is $price per book.\n";
#
   print "\n<a href=SessionPage3.php>Next</a> ";
   print " <a href=SessionPage1.php>Prev</a>\n";
   print "\nCounter = $count\n";
   print "Session name = ".session_name()."\n";
   print "Session id = ".session_id()."\n";
#
   print "\nContents of \$_GET:\n";
   foreach ($_GET as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_POST:\n";
   foreach ($_POST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_COOKIE:\n";
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }
   print "</pre>\n";
?>
```

3\. SessionPage3.php:

```
<?php
#  SessionPage3.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   session_start();
   $quantity = $_SESSION['quantity'];
   $price = $_SESSION['price'];
   $total = $quantity * $price;
   $count = $_SESSION['count'];
   $count++;
   $_SESSION['count'] = $count;
#
   print "<pre>\n";
   print "\nI am buying $quantity PHP books.\n";
   print "The unit price is $price per book.\n";
   print "The total price is $total.\n";
#
   print "\n<a href=SessionPage2.php>Prev</a>\n";
   print "\nCounter = $count\n";
   print "Session name = ".session_name()."\n";
   print "Session id = ".session_id()."\n";
#
   print "\nContents of \$_GET:\n";
   foreach ($_GET as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_POST:\n";
   foreach ($_POST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_COOKIE:\n";
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }
   print "</pre>\n";
?>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Creating and Managing Sessions in PHP Scripts](#part0107.xhtml)

∟Running Session Test Script Pages

This section provides a tutorial example on how to run multiple script pages that are connected by the session concept. Page outputs prove that the session concept is working.

If you run http://localhost/SessionPage1.php, you should get:

```
I am buying 3 PHP books.

Next

Counter = 1
Session name = PHPSESSID
Session id = o9oipjgc4r3fqmfk8mlldl5sl5

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:
```

If you click "Next" on the first page, you will be running http://localhost/SessionPage2.php, and should get:

```
I am buying 3 PHP books.
The unit price is 9.99 per book.

Next  Prev

Counter = 2
Session name = PHPSESSID
Session id = o9oipjgc4r3fqmfk8mlldl5sl5

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:
   PHPSESSID = o9oipjgc4r3fqmfk8mlldl5sl5
```

If you click "Next" on the second page, you will be running http://localhost/SessionPage3.php, and should get:

```
I am buying 3 PHP books.
The unit price is 9.99 per book.
The total price is 29.97.

Prev

Counter = 3
Session name = PHPSESSID
Session id = o9oipjgc4r3fqmfk8mlldl5sl5

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:
   PHPSESSID = o9oipjgc4r3fqmfk8mlldl5sl5
```

As you can see, the session concept is working. Several points should be noted here:

*   Data can be stored into the session in one page, and retrieve it in another page. For example, the quantity is stored into the session in the first page, and retrieved in the second and third page.
*   The session name is a string defined in the php.ini file.
*   The session ID is created by PHP, and managed as a cookie.
*   You can use the session object to manage a count of pages visited in a particular session. But you can not use the session object to manage a count of pages visited in all sessions. To manage information across versions, you need a new concept higher than session. For example, the application and the server concept is higher than the session concept.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Creating and Managing Sessions in PHP Scripts](#part0107.xhtml)

∟Managing Session IDs without Cookies

This section describes what is an array - an ordered pairs of keys and values. If sequential integer keys are used, an array is a simple indexed list. If string keys are used, an array is a map.

If don't like to use the cookie technology to manage the session ID, you can try to use the URL transparent parameter to manage the session ID. Here is what I did to test the URL transparent parameter.

1\. Open and edit the configuration file, \\php\\php.ini:

```
session.use_cookies = 0
session.use_trans_sid = 1
```

2\. Re-run http://localhost/SessionPage1.php, I got:

```
I am buying 3 PHP books.

Next

Counter = 1
Session name = PHPSESSID
Session id = mg04r204ctuloo2uegmih14ri5
Session module = files

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:
```

3\. Click "Next" on the first page, the URL address on the browser was changed to: http://localhost/SessionPage2.php?PHPSESSID=mg04r204ctuloo2uegmih14ri5. The browser displayed:

```
I am buying 3 PHP books.
The unit price is 9.99 per book.

Next  Prev

Counter = 2
Session name = PHPSESSID
Session id = mg04r204ctuloo2uegmih14ri5

Contents of $_GET:
   PHPSESSID = mg04r204ctuloo2uegmih14ri5

Contents of $_POST:

Contents of $_COOKIE:
```

4\. Click "Next" on the second page, the URL address on the browser was changed to: http://localhost/SessionPage3.php?PHPSESSID=mg04r204ctuloo2uegmih14ri5. The browser displayed:

```
I am buying 3 PHP books.
The unit price is 9.99 per book.
The total price is 29.97.

Prev

Counter = 3
Session name = PHPSESSID
Session id = mg04r204ctuloo2uegmih14ri5

Contents of $_GET:
   PHPSESSID = mg04r204ctuloo2uegmih14ri5

Contents of $_POST:

Contents of $_COOKIE:
```

Output shows that the session concept still worked correctly. But a couple of interesting things happened here:

*   If you ask PHP to use transparent session ID management, it will modify all the links to include the session ID as part of URL addresses. See the source code of the first page in the browser, you should see that the URL of "Next" button was modified as href=SessionPage2.php?PHPSESSID=mg04r204ctuloo2uegmih14ri5.
*   Outputs show that now the session ID is stored in the $\_GET array.
*   Since the session ID is stored in the URL field of the browser, everyone can see it. So this is less secure that storing the session ID a cookie.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Creating and Managing Sessions in PHP Scripts](#part0107.xhtml)

∟Where Is Session Data Stored

This section provides a tutorial example on how to find out where the PHP engine stores session data. The session.save\_path setting specifies the directory name for session data.

Where does PHP store session data? The answer is not so obvious.

Since I am running the PHP engine in CGI mode, PHP script pages are running with individual instances of the PHP executable program. So there is no easy to store session data in memory and share it between different PHP script pages. If not stored in memory, session data can be stored on hard disk and share it between PHP pages. Let's see if we can find where session data is stored on the hard disk.

First run http://localhost/SessionPage1.php again:

```
I am buying 3 PHP books.

Next

Counter = 1
Session name = PHPSESSID
Session id = mg04r204ctuloo2uegmih14ri5
Session module = files

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:
```

Then use the Windows find tool to search for file names with "mg04r204ctuloo2uegmih14ri5". No surprise, you should get \\tmp\\sess\_mg04r204ctuloo2uegmih14ri5. Open this file in a text editor, you should see:

```
quantity|i:3;count|i:1;
```

The file format is so simple, session data is stored in clear text, with ";" as delimiters. If you want to change where session data is stored, you can modify the session.save\_path setting in \\php\\php.ini. For example:

```
session.save_path = "\herong\temp"
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Sending and Receiving Cookies in PHP Scripts

This chapter provides tutorial examples and notes about cookie. Topics include understanding of the cookie concept; sending cookies with the setcookie() function; receiving cookies with the $\_COOKIE array; enabling output buffering; creating persistent cookies; specifying cookie domain and path.

> [What Is a Cookie](#part0115.xhtml)
> 
> [Sending and Receiving Cookies](#part0116.xhtml)
> 
> [Sending and Receiving Cookies - Example](#part0117.xhtml)
> 
> [ob\_start() - Output Buffering Function](#part0118.xhtml)
> 
> [Persistent Cookies Saved on Hard Disk](#part0119.xhtml)
> 
> [Other Cookie Properties - Domain and Path](#part0120.xhtml)

Takeaways:

*   setcookie() must be called before any output to the HTTP response. The main reason is that PHP is not buffering the HTTP response. But you can alter this behavior by using the ob\_start() functions.
*   A persistent cookie is stored in a cookie file on the browser's local machine.
*   A persistent cookie can have an expiration time expressed in number of seconds since epoch.
*   Web browser will only send back a cookie when both domain and path match the requested domain and path.
*   To make a cookie available for all sub domains of a top level domain, set the domain property to the top level domain name.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Sending and Receiving Cookies in PHP Scripts](#part0114.xhtml)

∟What Is a Cookie

This section describes what is a cookie - a piece of information sent by a Web server to a browser. The server expects the browser to send all cookies back to the server.

**What Is a Cookie?** A cookie is a piece of information sent by a Web server to a Web browser, saved by the browser, and sent back to the server later. Cookies are transmitted inside the HTTP header.

Cookies move from server to browser and back to server as shown in the following diagram:

```
Web         Web         Local       Web           Web
Server      Browser     System      Browser       Server

Send        Receive     Save        Send back     Receive
cookies --> cookies --> cookies --> cookies   --> cookies
```

As you can see from the diagram, cookies are actually saved by the local system in memory or on the hard disk of Web browser user's machines. Many users are concerned about this. But I think it is pretty safe to allow your browser to save cookies.

If you are really concerned, you can change your browser's settings to reject cookies. But this may cause many Web based applications fail to run on your browser.

Cookies are mainly used to pass information from one PHP script to the next script.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Sending and Receiving Cookies in PHP Scripts](#part0114.xhtml)

∟Sending and Receiving Cookies

This section describes how PHP supports cookies. setcookie() is the function to set a cookie to the HTTP response. $\_COOKIE is the array containing cookies received in the next HTTP request.

PHP supports cookies with following elements:

1\. setcookie() - A built-in function that defines a cookie to be sent in the HTTP response as a header line. Like other header lines, cookies must be sent before any output from your script (this is a protocol restriction). This requires that you place calls to this function prior to any output, including <html> and <head> tags as well as any whitespace. If output exists prior to calling this function, setcookie() will fail and return FALSE.

The syntax of calling setcookie() is:

```
bool setcookie(string name, string value, int expire)
```

*   "name" is the name of this cookie.
*   "value" is the value of this cookie. "value" is optional. If "value" is not provided, this cookie will be set in the HTTP response without any value.
*   "expire" is the time when this cookie should be expired. "expire" is optional. If "expire" is not provided, this cookie will saved in browser memory only. If "expire" is provided, it represents a time in number of seconds since the epoch. If the provided time is a future time, this cookie will be saved on the hard disk of the browser system.

For example, setcookie("user", "Herong") will set a cookie named as "user" in the HTTP response.

2\. $\_COOKIE - A built-in array that stores cookies returned back from the browser in the next HTTP request. Cookie names will be used as array keys. For example, $\_COOKIE\["user"\] returns the cookie value, "Herong", included in the HTTP request.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Sending and Receiving Cookies in PHP Scripts](#part0114.xhtml)

∟Sending and Receiving Cookies - Example

This section provides a tutorial example on how to set and send a cookie with the setcookie() function, and how to receive a cookie with the $\_COOKIE array.

To help us understand how to send and receive cookies, I wrote the following PHP tutorial example script page, CookieTest.php:

```
<?php
#  CookieTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $numCookies = count( array_keys($_COOKIE) );
   $numCookies++;
   $cookieName = "Cookie_$numCookies";
   $cookieValue = "My cookie value";
   setcookie($cookieName, $cookieValue);

   print("<pre>\n");
   print("Cookies added by the server:\n");
   print("   $cookieName: $cookieValue\n");

   print("\nCookies received by the server:\n");
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }

   print "</pre>\n";
?>
```

When I ran run this script with a browser, I got:

```
Cookies added by the server:
   Cookie_1: My cookie value

Cookies received by the server:
```

When I click the refresh button of the browser, the page changed with:

```
Cookies added by the server:
   Cookie_2: My cookie value

Cookies received by the server:
   Cookie_1 = My cookie value
```

What happened here was that when I opened the page the first time, the server received no cookie from the browser's HTTP request. So my page added the first cookie named as "Cookie\_1" to the HTTP response.

When I clicked the refresh button, the browser sent my first cookie back to the server in the HTTP request. Then my page added the second cookie named as "Cookie\_2" in the response.

If I keep clicking the refresh button, more and more cookies would be added to the request and response. But there is a limit. The browser will only take up to 20 cookies from one Web server.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Sending and Receiving Cookies in PHP Scripts](#part0114.xhtml)

∟ob\_start() - Output Buffering Function

This section describes how to use the ob\_start() function to turn on output buffering, which allows HTTP response header lines to be added after response body has been added.

As you can see from setcookie() definition, the PHP engine provides no buffer for the HTTP response body. That means as soon the PHP script starts to send output to the HTTP response body, the HTTP header block will be finalized, and not allowed to change any more.

But this default behavior can be altered by calling output control functions:

*   setcookie() must be called before any output to the HTTP response. The main reason is that PHP is not buffering the HTTP response. But you can alter this behavior by using ob\_\*() functions.
*   ob\_start() - A built-in function that turns on output buffering.
*   flush() - A built-in function that flushes out the contents of the output buffer to the HTTP response body.

Of course, default behavior can also be altered by the configuration file, php.ini. Open php.ini and set the following line:

```
output_buffering = 4096
```

The above configuration line tells the PHP engine to turn on output buffering, and set the buffer size to 4096 bytes. Once "output\_buffering" is turned on, you don't have to call ob\_start() in your scripts.

To test the PHP engine default behavior, I modified CookieTest.php into CookieOutputBuffer.php:

```
<?php
#  CookieOutputBuffer.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print("<pre>\n");
   print("Adding cookies by the server:\n");

   $numCookies = count( array_keys($_COOKIE) );
   $numCookies++;
   $cookieName = "Cookie_$numCookies";
   $cookieValue = "My cookie value";
   print("   $cookieName: $cookieValue\n");

   setcookie($cookieName, $cookieValue);

   print("\nCookies received by the server:\n");
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }

   print "</pre>\n";
?>
```

I then opened php.ini and set the following line:

```
output_buffering = 0
```

Running IE on CookieOutputBuffer.php gave me this:

```
Adding cookies by the server:
   Cookie_2: My cookie value

Cookies received by the server:
   User = Herong Yang

PHP Warning: Cannot modify header information - headers already
sent by (output started at ...\CookieOutputBuffer.php:4) ...
```

Now I truly beblieve that PHP engine's default behavior is no output buffering. Make sure to change "output\_buffering" back to 4096 before continuing to the next test.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Sending and Receiving Cookies in PHP Scripts](#part0114.xhtml)

∟Persistent Cookies Saved on Hard Disk

This section describes what is a persistent cookie - A cookie with an expiration time in the future and saved in a cookie file on the hard disk of the browser computer.

There are two kinds of cookies: persistent cookies and temporary cookies.

A persistent cookie is stored in a file on your computer's hard disk. It remains there after you close your Web browser. A persistent cookie will be picked up by the browser and included in HTTP requests for the Web server, where the cookie came from.

A temporary or session cookie is stored in memory only for your current browsing session. A temporary cookie will be deleted when you close your browser.

The default behavior of setcookie(name,value) is to set a cookie as a temporary cookie. To set a persistent cookie, we need to add another parameter to the setcookie() function call using the following syntax:

```
bool setcookie(string name, string value, int expire)
```

where "expire" specifies when this cookie should be expired. If the expiration time is a future time, like 30 days from today, this cookie will be set as a persistent cookie. Note that "expire" should be represented in number of seconds since the epoch. The best way to set "expire" is use the time() function, which represents the current time in number of seconds since the epoch. Example, 30 days from today can be expressed as "time()+60\*60\*24\*30".

If "expire" is not given, a temporary cookie will be created.

To show you how to set a persistent cookie, and how the cookie is store in a file, I wrote the following PHP script page, CookiePersisted.php:

```
<?php
#  CookiePersisted.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $cookieName = "User";
   $cookieValue = "Herong Yang";
   $expiration = time()+60*60*24*30;
   setcookie($cookieName, $cookieValue, $expiration);

   print("<pre>\n");
   print("Cookies added by the server:\n");
   print("   $cookieName: $cookieValue\n");
   print("   Expires at: $expiration\n");
   print "</pre>\n";
?>
```

I opened this page with IE (Internet Explorer), I got:

```
Cookies added by the server:
   User: Herong Yang
   Expires at: 1134531525
```

To find out in which file this cookie is stored in my computer, I clicked at IE's "Tools" menu, selected "Internet Options...". and clicked the "Settings..." button in the "Temporary Internet files" section of the "General" tab. I saw where is my "Temporary Internet files folder". So I went to that folder, and saw a cookie file named something like "Cookie:user@localhost/". I double clicked on that file, and managed to open it in notepad:

```
User
Herong+Yang
localhost/
1024
3801469056
29753439
3934260416
29747404
*
```

Actually, I saw a lots of other cookie files created by other Web sites that I have visited in the past. I deleted all of them.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Sending and Receiving Cookies in PHP Scripts](#part0114.xhtml)

∟Other Cookie Properties - Domain and Path

This section describes what is an array - an ordered pairs of keys and values. If sequential integer keys are used, an array is a simple indexed list. If string keys are used, an array is a map.

A cookie also has two other properties:

1\. "domain" - A property that defines the domain of Web servers to which this cookie should be made available. Web browsers will send a cookie back to a Web server when the Web server matches its defined domain. Web browsers will never send back a cookie to a domain other than its defined domain.

For example, if a cookie's domain is www.google.com, the browser will send back this cookie to the server only when the browser is visiting www.google.com. The browser will never send back this cookie to www.yahoo.com.

To make a cookie available for all sub domains of a top level domain, set the domain property to the top level domain name. For example, if a cookie's domain is set to ".google.com", this cookie will be available to all google sub domains, like groups.google.com and gmail.google.com.

2."path" - A property that defines a Web server path to which this cookie should be made available. Web browsers will send a cookie back to a Web server when the Web server matches its defined domain, and the requested page matches its defined path. Web browsers will never send back a cookie to requested path other than its defined path.

Note that the defined path also includes all its sub paths. For example, if a cookie's domain is "www.amazon.com", and path is "/order/", then a browser will send back this cookie for requests like "http://www.amazon.com/order/checkout.html", and "http://www.amazon.com/order/report/invoice.html". But a browser should not send back this cookie for requests like "http://www.amazon.com/catelog/book.html".

The setcookie() function offers two more parameters to allow you to set "domain" and "path" properties on a cookie as in the following syntax:

```
bool setcookie(string name, string value, int expire, string path,
   string domain)
```

where "path" specifies the cookie's path property, and "domain" specifies the cookie's domain property. If "path" is not given, the cookie will have "/" as the default path. If "domain" is not given, the cookie will have the current domain as the default domain.

Okay. Let's play the properties with the following script, CookieProperties.php:

```
<?php
#  CookieProperties.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print("<pre>\n");
   print("\nAdding a cookie with default properties:\n");

   $cookieName = "User";
   $cookieValue = "Herong Yang";
   $expiration = time()+60*60*24*30;
   setcookie($cookieName, $cookieValue, $expiration);
   print("   Name: $cookieName\n");
   print("   Value: $cookieValue\n");
   print("   Expiration: $expiration\n");

   print("\nAdding a cookie with non-default properties:\n");
   $cookieName = "Book";
   $cookieValue = "Herong's Tutorial Notes on PHP";
   $expiration = time()+60*60*24*30;
   $path = "/";
   $domain = "localhost";
   setcookie($cookieName, $cookieValue, $expiration, $path, $domain);
   print("   Name: $cookieName\n");
   print("   Value: $cookieValue\n");
   print("   Expiration: $expiration\n");
   print("   Path: $path\n");
   print("   Domain: $domain\n");

   print("\nCookies received by the server:\n");
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }

   print "</pre>\n";
?>
```

Ran this script in IE, I got:

```
Adding a cookie with default properties:
   Name: User
   Value: Herong Yang
   Expiration: 1134622043

Adding a cookie with non-default properties:
   Name: Book
   Value: Herong's Tutorial Notes on PHP
   Expiration: 1134622043
   Path: /
   Domain: localhost
```

Clicked the refresh button on IE, I got:

```
Adding a cookie with default properties:
   Name: User
   Value: Herong Yang
   Expiration: 1134622059

Adding a cookie with non-default properties:
   Name: Book
   Value: Herong's Tutorial Notes on PHP
   Expiration: 1134622059
   Path: /
   Domain: localhost

Cookies received by the server:
   User = Herong Yang
```

Apparently, my script did not set the properties correctly. The browser should have sent back my second cookie also. So either the "path=/" or "domain=localhost" did not match my local IIS environment. I could not figure it out why.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Controlling HTTP Response Header Lines in PHP Scripts

This chapter provides tutorial examples and notes about HTTP response header line. Topics include understanding of HTTP response structure and standard header lines; controling header lines using the header() function; dumping HTTP responses to view header lines; IIS and PHP engine added header lines for static files and PHP scripts; Location, Content-Type, and Content-Disposition header lines.

> [What Is an HTTP Response](#part0122.xhtml)
> 
> [HTTP Response Header Lines](#part0123.xhtml)
> 
> [header() - Inserting a Raw Header Lines](#part0124.xhtml)
> 
> [HttpRequestGet.php - Viewing Header Lines](#part0125.xhtml)
> 
> [Response Header Lines of Static Files](#part0126.xhtml)
> 
> [HttpHeaderLines.php - Examples of Inserting Header Lines](#part0127.xhtml)
> 
> [Location: - Forcing the Browser to Redirect to Another URL](#part0128.xhtml)
> 
> [Content-Type: - Generating Non-HTML Response Body](#part0129.xhtml)
> 
> [Content-Disposition: - Sending Files for Downloading](#part0130.xhtml)

Takeaways:

*   HTTP response header lines must be generated before any other outputs from the script, unless you have the output\_buffering turned on.
*   Setting header lines in PHP is simple - one built-in function, header(), does everything for you.
*   "Location" is a interesting header line. It tells the browser to redirect itself to a new URL.
*   "Content-disposition" tells the browser to prepare for downloading the entity body.
*   I like the powerful function, readfile(), reading the content of a file and sending it to the HTTP response directly.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Controlling HTTP Response Header Lines in PHP Scripts](#part0121.xhtml)

∟What Is an HTTP Response

This section describes what is an HTTP response - The message returned from a Web server to the client machine in response to an HTTP request from that client machine.

**What Is an HTTP Response?** A HTTP response is the message a Web server needs to return back to a Web client machine in response to an HTTP request from the same client machine. Based on the HTTP/1.1 protocol, after receiving and interpreting an HTTP request from a client machine, a Web server must responds with an HTTP response message with the following structure:

```
status-line
header-line
...
header-line

entity-body
```

Note that:

*   Response must have one status-line.
*   Response can have zero, one, or many header lines.
*   Response can only have zero or one entity-body.
*   There is a blank line between header lines and the entity body.
*   Status line, header line, and blank line must be ended with CRLF ("/r/n") characters.
*   Entity body is the actual data requested by the client request.
*   Header lines can be in any order.

Below is a sample HTTP response with two header lines:

```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 38

<html><body>Hello world!</body></html>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Controlling HTTP Response Header Lines in PHP Scripts](#part0121.xhtml)

∟HTTP Response Header Lines

This section describes HTTP response header lines in 3 groups. Commonly used header lines are Date, Cache-Control, Last-Modified, Content-Length, Connection, Content-Type, Expires, Set-Cookie, Server, etc.

HTTP/1.1 response header lines allow the server to passes additional information about the response which cannot be placed in the status line. Header lines can be divided into three groups:

1\. General header lines - Information about the transmission of the entire response message:

```
   Cache-Control
   Connection
   Date
   Pragma
   Trailer
   Transfer-Encoding
   Upgrade
   Via
   Warning
```

2\. Response header lines - Information about the response:

```
   Accept-Ranges
   Age
   ETag
   Location
   Proxy-Authenticate
   Retry-After
   Server
   Vary
   WWW-Authenticate
```

3\. Entity header lines - Information about the data requested by the client:

```
   Allow
   Content-Encoding
   Content-Language
   Content-Length
   Content-Location
   Content-MD5
   Content-Range
   Content-Type
   Expires
   Last-Modified
```

As examples, here is a list of all header lines from an HTTP response returned from the Yahoo Web serer:

```
Date: Sun, 13 Nov 2018 04:34:17 GMT
P3P: policyref="http://info.yahoo.com/w3c/p3p.xml", CP="CAO DSP CO...
Cache-Control: private
Vary: User-Agent
X-XRDS-Location: http://open.login.yahooapis.com/openid20/www.yaho...
Last-Modified: Sun, 13 Nov 2018 04:31:16 GMT
Accept-Ranges: bytes
Content-Length: 9490
Connection: close
Content-Type: text/html; charset=utf-8
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Controlling HTTP Response Header Lines in PHP Scripts](#part0121.xhtml)

∟header() - Inserting a Raw Header Lines

This section describes how to use the header() function to insert a raw HTTP response header line to reset the status line, replace an existing header line, or add a new header line.

When a PHP page is requested, the PHP engine will add some basic header lines in the HTTP response. But if you want to add new header lines or change those inserted by the PHP engine, you can use the header() function. Here are some rules on how to use the header() function:

1\. The syntax of header() is:

```
void header(string $line, bool $replace, int $code)
```

2\. $line specifies a complete header line string like "Content-Type: text/html".

3\. $replace specifies a Boolean value controlling whether to replace a previously defined header line of the same identifier or not. If $replace = TRUE, the specified header line will replace any existing header lines with the same identifier. If $replace = FALSE, the specified header line will not replace any existing header lines with the same identifier. If $replace is not provided, PHP will assume $replace = TRUE.

4\. $code specifies an integer to be used as the HTTP response status code. If $code is not provided, the PHP engine will decide the status code.

5\. header() must be called before any output to the entity body, if the output buffering is turned off.

6\. If header() is called to set "Location" header line, the status line will be set to "HTTP/1.0 302".

7\. When header() is called multiple times, the status line will be always generated first. Other header lines will be generated in same order as their calling statements.

Here a sample PHP script code segment that generates some header lines using the header() function:

```
   header("HTTP/1.1 200 OK"); // Reset the status line
   header("Cache-Control: no-cache, must-revalidate");
   header("Expires: Mon, 26 Jul 2017 05:00:00 GMT"); // Past time ok
   header("Content-Type: text/html; charset=utf-8");
   header("Content-Length: 9490");
   header("My-Header: SID=909494909", FALSE); // Allow duplicates
   header("My-Header: UID=Herong", FALSE); // Allow duplicates
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Controlling HTTP Response Header Lines in PHP Scripts](#part0121.xhtml)

∟HttpRequestGet.php - Viewing Header Lines

This section provides a tutorial example script, HttpRequestGet.php, on how to dump the entire HTTP response including all header lines from a Web server.

When a client program receives an HTTP response, it will look at header lines first. Based on the information contained in header lines, the client program will decide what to do with the actual response data in the entity body.

If you use a Web browser as an HTTP client program, it will process the data in the entity body differently depending on mainly the "Content-Type" entity header line: displaying the data as it is, rendering the data as an HTML document and displaying the resulting information, or passing the data to another registered program to handle it.

Once the Web browser finishes processing the entity body, you can get some limited information from the header lines. For example, you can click the right mouse button and select the properties command on Internet Explorer, it will display some general properties about this response in a pop up window. Properties displayed are not always identical to response header lines. The "Modified" property is probably identical to the "Last-Modified" entity header line. The "Type" property is sometime related to the "Content-Type" entity header line, and sometimes related to server side resource that generated the response.

How to view all header lines received in an HTTP response? I couldn't easily find any existing tools to do this. So I wrote the following program to dump the entire response including all header lines received from a Web server:

```
<?php
#  HttpRequestGet.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $path = "/index.html";
   $port = 80;
   $host = "localhost";
   if (count($argv) > 1) $path = $argv[1];
   if (count($argv) > 2) $port = $argv[2];
   if (count($argv) > 3) $host = $argv[3];

   $address = gethostbyname($host);
   $socket = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
   socket_connect($socket, $address, $port);
   $in = "GET $path HTTP/1.0\r\n\r\n";
   socket_write($socket, $in, strlen($in));
   while ($out = socket_read($socket, 2048)) {
      echo $out;
   }
   socket_close($socket);
?>
```

Note that:

*   $argv is built-in array that contains all command line arguments, with $argv\[0\] representing the PHP file name, if you run your PHP file as "php file\_name.php ...".
*   You need to make sure that "extension=php\_sockets.dll" or "extension=sockets" is turned on in your php.ini configuration file to use socket related functions.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Controlling HTTP Response Header Lines in PHP Scripts](#part0121.xhtml)

∟Response Header Lines of Static Files

This section provides a tutorial example on how to test and view HTTP response header lines returned by IIS on 3 types of static files: HTML document, GIF image file, and PDF document.

Since I am using Apache as the Web server, static files will be served directly by Apache server. It will set the status line and header lines for you based on the information collected from the static file the HTTP request is asking. For example, the "Content-Type" header line will be set based on the file name extension and the MIME settings of the server configuration. The "Content-Length" header line will be set to the size of the file.

Let's look at 3 examples of different types of static files. All of them are stored on my local machine at c:\\inetpub\\wwwroot, where the IIS is serving documents from.

1\. Command: "php HttpRequestGet.php /hello.html" gives us:

```
HTTP/1.1 200 OK
Date: Sat, 26 Jan 2019 22:32:24 GMT
Server: Apache/2.4.37 (Win64)
Last-Modified: Sat, 18 Nov 2015 05:31:16 GMT
ETag: "26-405d03f0d1100"
Accept-Ranges: bytes
Content-Length: 38
Connection: close
Content-Type: text/html

<html><body>Hello world!</body></html>
```

Couple of interesting notes here:

*   Content-Type was set to "text/html", because the file name extension was "html".
*   The request was marked as HTTP/1.0 in HttpRequestGet, but IIS responded with a higher version, HTTP/1.1.
*   I also tried to use HTTP/1.1 in my request, but IIS returned with an error. Why IIS could not support HTTP/1.1 request?
*   Notice that there was a blank line to separate the header lines and the entity body as required by the HTTP specification.

2\. Command: "php HttpRequestGet.php /dot.gif" gives us:

```
HTTP/1.1 200 OK
Date: Sat, 26 Jan 2019 22:36:08 GMT
Server: Apache/2.4.37 (Win64)
Last-Modified: Sat, 26 Jan 2019 22:35:47 GMT
ETag: "2b-5806410a1577b"
Accept-Ranges: bytes
Content-Length: 43
Connection: close
Content-Type: image/gif

GIF89a......
```

As you can see, Content-Type was set correctly to "image/gif" for file name extension "gif", as defined in the MIME settings. I could not include the entire entity body here because it contains binary data.

3\. Command: "php HttpRequestGet.php /hello.pdf" gives us:

```
HTTP/1.1 200 OK
Date: Sat, 26 Jan 2019 22:38:19 GMT
Server: Apache/2.4.37 (Win64)
Last-Modified: Sun, 27 Jul 2003 21:22:12 GMT
ETag: "38d-3c37707f2a900"
Accept-Ranges: bytes
Content-Length: 909
Connection: close
Content-Type: application/pdf

%PDF-1.3
% ...
4 0 obj
......
```

Again, Content-Type was set correctly to "application/pdf" for file name extension "pdf", as defined in the MIME settings. I truncated the entity body to save some space.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Controlling HTTP Response Header Lines in PHP Scripts](#part0121.xhtml)

∟HttpHeaderLines.php - Examples of Inserting Header Lines

This section provides a tutorial example on how to insert HTTP response header lines using the header() function.

Now let's see how the PHP engine defines header lines and how you can control them. First create this simple script, hello.php, and copy it to c:\\inetpub\\wwwroot.

```
Hello <?php echo "world!"; ?>
```

Then obtain the response with "php HttpRequestGet.php /hello.php":

```
HTTP/1.1 200 OK
Date: Sat, 26 Jan 2019 22:40:01 GMT
Server: Apache/2.4.37 (Win64)
X-Powered-By: PHP/7.3.0
Connection: close
Content-Type: text/html; charset=UTF-8

Hello world!
```

Comparing with the static files described in the previous section, the output shows:

*   PHP engine added its own header line, "X-Powered-By".
*   IIS maintained the header line, "Server".
*   "ETag" was removed. I don't know what is ETag anyway.
*   PHP defaulted "Content-Type" to "text/html; charset=UTF-8".
*   "Content-Length" is not provided. This is not a good behavior, if the client relies on this value.

Now, I am ready to instruct the PHP how to define header lines. Here is my testing script, HttpHeaderLines.php:

```
<?php
#  HttpHeaderLines.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $text = "<html><body>Hello world!</body></html>";
   print($text);
   header("Content-Type: text/xml;charset=utf-8");
   header("Content-Length: ".strlen($text));
   header("Version: Unknown");
   header("Version: 2019");
   header("Key-Word: PHP");
   header("Key-Word: HTTP", false);
?>
```

Here is the output with "php HttpRequestGet.php /HttpHeaderLines.php":

```
HTTP/1.1 200 OK
Date: Sat, 26 Jan 2019 22:44:26 GMT
Server: Apache/2.4.37 (Win64)
X-Powered-By: PHP/7.3.0
Version: 2019
Key-Word: PHP, HTTP
Content-Length: 38
Connection: close
Content-Type: text/xml;charset=utf-8

<html><body>Hello world!</body></html>
```

Okay. What can we say about the output?

*   I was able to call header() after I started to output the entity body, because I had the output buffer turned on. I entered "output\_buffering = 4096" in php.ini.
*   "Content-Type" defined ok.
*   "Content-Length" defined ok. But it was outputted after "X-Powered-By". Not sure why.
*   The "replace" flag worked. There is only one "Version", because by default replace is turned on. There are two "Key-Word", because I set "replace" to "false" in my second header() call.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Controlling HTTP Response Header Lines in PHP Scripts](#part0121.xhtml)

∟Location: - Forcing the Browser to Redirect to Another URL

This section provides a tutorial example on how to insert the 'Location:' header line in a HTTP response to tell the browser to do a URL redirect - Send a HTTP request to the specified ULR immediately.

The PHP manual document says we can use header("Location: ...") to tell the browser to make a new HTTP request to a given URL. This is called "redirect". Here is my testing script, HttpRedirect.php:

```
<?php
#  HttpRedirect.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $text = "<html><body>Moved!</body></html>";
   print($text);
   header("Content-Type: text/xml;charset=utf-8");
   header("Content-Length: ".strlen($text));
   header("Location: https://www.herongyang.com/");
?>
```

The output from Apache 2.4 and PHP 7:

```
HTTP/1.1 302 Found
Date: Sat, 26 Jan 2019 22:47:11 GMT
Server: Apache/2.4.37 (Win64)
X-Powered-By: PHP/7.3.0
Content-Length: 32
Location: https://www.herongyang.com/
Connection: close
Content-Type: text/xml;charset=utf-8

<html><body>Moved!</body></html>
```

The output from IIS and PHP 5:

```
HTTP/1.1 302 Object Moved
Server: Microsoft-IIS/5.1
Date: Sat, 19 Nov 2005 03:46:58 GMT
Content-Type: text/html
X-Powered-By: PHP/5.0.4
Content-Length: 32
Location: https://www.herongyang.com/

<head><title>Document Moved</title></head>
<body><h1>Object Moved</h1>This document may be
 found <a HREF="https://www.herongyang.com/">here</a></body>
```

I am a little bit surprised by the output:

*   My entity body has been totally replaced by a short HTML document generated by the PHP engine. This is not mentioned in the PHP documentation at all!
*   The status line is changed to "HTTP/1.1 302 Object Moved".
*   The "Content-Length" still had my value, the number of bytes of my original HTML message, not the replacing message.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Controlling HTTP Response Header Lines in PHP Scripts](#part0121.xhtml)

∟Content-Type: - Generating Non-HTML Response Body

This section provides a tutorial example on how to change the 'Content-Type:' header line in a HTTP response to tell the browser to handle the response entity body as different document types, like ext/html, image/gif, application/pdf, application/msword, etc.

Sometimes, you may want to send back information in the response entity body that is not in the HTML format, for example, a PDF document, or a MS Word Document. In this case, we have to set Content-Type, Content-Length and other header lines carefully to provide correct information about the entity body for the client program. Here is a sample PHP script that shows you how to set header lines for different types of data in the entity body.

```
<?php
#  GetFile.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $ok = array_key_exists('QUERY_STRING', $_SERVER);
   if ($ok) {
      $p = $_SERVER['QUERY_STRING'];
      $ok = strlen($p)>0 && file_exists($p);
   }
   if ($ok) {
      if (strpos($p,".html")!=false) {
         header("Content-Type: text/html");
      } else if (strpos($p,".gif")!=false) {
         header("Content-Type: image/gif");
      } else if (strpos($p,".pdf")!=false) {
         header("Content-Type: application/pdf");
      } else if (strpos($p,".doc")!=false) {
         header("Content-Type: application/msword");
      } else {
         $ok = false;
      }
   }
   if ($ok) {
      header("Content-Length: ".filesize($p));
      readfile($p);
   } else {
      print("<html><body>Bad request.</body></html>");
   }
?>
```

Ideas used in this script:

*   The objective is to send back the content of the requested file in entity body, and set the Content-Type and Content-Length header lines correctly.
*   The requested file name is given in the query string of the HTTP request. array\_key\_exists() is used to make sure the query string is provided to avoid array index error.
*   The extension of the requested file name is checked to determine the Content-Type header line. strpos() is used as a Boolean value to check the file name extension.
*   Then the requested file size is checked to set the Content-Length header line.
*   Then the requested file is outputted to the HTTP response with a single function readfile(). This function name is a little bit misleading, but the function is very useful.
*   If any thing goes wrong, a HTML entity is returned with an error message. A Boolean variable $ok is used to monitor the error condition.

Now let's see how this page works. Assuming I have GetFile.php, hello.html, dot.gif, hello.pdf, and hello.doc copied to c:\\apache\\htdocs directory. Of course, my Apache server is configured to the PHP engine.

1\. Use IE (Internet Explorer) to request: http://localhost/GetFile.php?hello.html, you should see the hello message properly displayed as a HTML document.

2\. Use IE to request: http://localhost/GetFile.php?dot.gif, you should see a tiny dot displayed as an image.

3\. Use IE to request: http://localhost/GetFile.php?hello.pdf, you should see IE calling Adobe Reader to display the hello message as a PDF document.

4\. Use IE to request: http://localhost/GetFile.php?hello.doc, you should see IE calling MS Word to display the hello message as a MS Word document.

5\. Use IE to request: http://localhost/GetFile.php?any.file, you should see IE displaying an error message. The reason, of course, is that the requested file doesn't exist.

6\. Use IE to request: http://localhost/GetFile.php you should see IE displaying an error message. The reason is that there is no query string in the HTTP request.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Controlling HTTP Response Header Lines in PHP Scripts](#part0121.xhtml)

∟Content-Disposition: - Sending Files for Downloading

This section provides a tutorial example on how to insert the 'Content-Disposition:' header line in a HTTP response to tell the browser to prompt the user the download and save the response entity body as a file.

In the previous section, the requested file is delivered to the browser for opening immediately. HTTP does also support another header line called "Content-Disposition" which tells the browser to not open the file immediately, but prepare for downloading the entity body. The following script will show you how to do this:

```
<?php
#  Download.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $ok = array_key_exists('QUERY_STRING', $_SERVER);
   if ($ok) {
      $p = $_SERVER['QUERY_STRING'];
      $ok = strlen($p)>0 && file_exists($p);
   }
   if ($ok) {
      if (strpos($p,".html")!=false) {
         header("Content-Type: text/html");
      } else if (strpos($p,".gif")!=false) {
         header("Content-Type: image/gif");
      } else if (strpos($p,".pdf")!=false) {
         header("Content-Type: application/pdf");
      } else if (strpos($p,".doc")!=false) {
         header("Content-Type: application/msword");
      } else {
         $ok = false;
      }
   }
   if ($ok) {
      header("Content-Length: ".filesize($p));
      header("Content-disposition: attachment; filename=".$p);
      readfile($p);
   } else {
      print("<html><body>Bad request.</body></html>");
   }
?>
```

In this page, another header line, "Content-Disposition", is added to the response, in which I am telling the client program that the entity data is an attachment, with file name specified.

Now try to use IE to request http://localhost/Download.php?hello.pdf, you will see IE prompting you to save the attachment instead of calling Adobe Reader to display the data.

Try to use IE to request http://localhost/Download.php?other\_existing\_file, you will see IE display the "Bad request" message. The script is working correctly.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Managing File Upload

This chapter provides tutorial examples and notes about managing file upload with PHP. Topics include creating Web form for user to select and submit uploaded files; creating PHP script to process uploaded files on the Web server.

> [File Upload Web Form](#part0132.xhtml)
> 
> [File Upload PHP Script](#part0133.xhtml)

Takeaways:

*   Web form for file upload requires <form method="POST" enctype="multipart/form-data", ...> to ensure the HTTP request being generated correctly to send files.
*   Web form for file upload also needs to have <input type="file" ...> fields to allow users to select one or more files from the local computer to be uploaded to the Web server.
*   Web server side PHP script can use retrieve information from $\_FILES\[\] to inspect and process uploaded files, which are stored in temporary location by the PHP engine.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing File Upload](#part0131.xhtml)

∟File Upload Web Form

This section provides a tutorial example on how to write Web form to upload files. type='file' attribute of the 'input' displays 'Choose File' button for user to select a local file to upload.

To manage file uploads with PHP scripts, you need to build a Web form for users to file, select and submit files from their local computers. Here are some guidelines on building file upload forms:

1\. Using <form method="POST" ...> to ensure that uploaded files are included in the HTTP request body.

2\. Using <form enctype="multipart/form-data" ...> to ensure that uploaded files are properly encoded as multiple attachments.

3\. Using <input type="hidden" name="MAX\_FILE\_SIZE" value="nnnnn"/> before any <input type="file" .../> elements to limit the upload file size to the given number of bytes.

4\. Using <input type="file" ...> to display a "Choose File" button to allow the user to search and select a local file to upload.

Here is an example of a Web form, file-upload-form.html, for file upload.

```
<html>
<!-- file-upload-form.html
- Copyright (c) 2009 HerongYang.com. All Rights Reserved.
-->
<body>
  <h4>File Upload Form</h4>
  <form action="file-upload-handler.php" method="POST"
    enctype="multipart/form-data">
    <p>1st file to upload: <input type="file" name="file_one"/></p>
    <p>2nd file to upload: <input type="file" name="file_two"/></p>
    <p>Click to upload: <input type="submit" name="submit" value=Upload></p>
  </form>
</body>
</html>
```

Put the Web form file, file-upload-form.html, to the Apache Web server on the local computer. Then open this form with a Web browser using http://localhost/file-upload-form.html.

Click "Choose File" buttons to select two different files, Hello.php and dot.gif:

![Web Form for File Upload](Images/image00231.jpeg)

Web Form for File Upload

See the next tutorial on how to write file-upload-handler.php to received the uploaded files on the Web server.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing File Upload](#part0131.xhtml)

∟File Upload PHP Script

This section provides a tutorial example on how to write PHP script to process uploaded files on the Web server. $\_FILES\[\] built-in hash table has infomation of all uploaded files prepared for you by the PHP engine.

After the user selecting files and submitting the upload form, the Web browser will send selected files to the Web server to process. If the Web server passes this job to a PHP script, the PHP engine will parse those uploaded files and provide the following interface functionalities to the PHP script:

1\. File Size Validation - If any file is larger than the specified MAX\_FILE\_SIZE value, it will be rejected.

2\. Populting $\_FILES\[\] - Each uploaded file will be stored in temporary directory on the Web server with a temporary name. A new entry will be added to the built-in hash table $\_FILES\[\] with the following information:

*   $\_FILES\[$field\_name\] = $file\_info\[\] - The hash key, $field\_name, is the name given the <input> field of the web form.
*   $file\_info\['name'\] - Stores the original name of the uploaded file on the client machine.
*   $file\_info\['type'\] - The mime type of the uploaded file, if the browser provided this information. An example would be "image/gif". This mime type is however not checked on the PHP side and therefore don't take its value for granted.
*   $file\_info\['size'\] - The size, in bytes, of the uploaded file.
*   $file\_info\['tmp\_name'\] - The temporary filename of the file in which the uploaded file was stored on the server.
*   $file\_info\['error'\] - The error code associated with this file upload.

3\. Providing move\_uploaded\_file() Function - A nice tool to move the uploaded file to a more permanent location.

4\. Providing is\_uploaded\_file() Function - A nice tool to ensure the uploaded file was indeed uploaded from a HTTP POST request. This is needed to preventing some upload attacks that play tricks on upload file names.

5\. Providing getallheaders() Function - A tool to access HTTP request headers just in case you want know more about the client.

6\. No functionality to access the HTTP POST request body raw data, since it is encoded as "multipart/form-data", a requirement for uploading files. The 2 options of access POST body raw data: php://input and $HTTP\_RAW\_POST\_DATA are both not available with enctype="multipart/form-data".

Here is an example of a PHP script, file-upload-handler.php, to process uploaded files.

```
<?php
# file-upload-handler.php
# Copyright (c) 2009 HerongYang.com. All Rights Reserved.
#
  print "<html><body><pre>\n";
  dumpFileInfo();
  processFiles();
  dumpRequest();
  print "</pre></body></html>\n";

function dumpFileInfo() {
  print "\nDumping \$_FILES[] - ".count($_FILES)." entries:\n";
  foreach ($_FILES as $input_name => $file_info) {
    print "   Field name = ".$input_name."\n";
    print "      Error code = ".$file_info['error']."\n";
    print "      Temp name = ".$file_info['tmp_name']."\n";
    print "      File name = ".$file_info['name']."\n";
    print "      File size = ".$file_info['size']."\n";
    print "      File type = ".$file_info['type']."\n";
  }
}

function processFiles() {
  print "\nProcessing uploaded files - ".count($_FILES)." entries:\n";
  foreach ($_FILES as $input_name => $file_info) {
    print "   Field name = ".$input_name."\n";
    $errorCode = $file_info['error'];
    if ($errCode==UPLOAD_ERR_OK) {
      $fileName = $file_info['name'];
      $tempName = $file_info['tmp_name'];
      print "      File $fileName uploaded successfully.\n";
      if (is_uploaded_file($tempName)) {
        # remove potential risk path like: "../../*"
        $fileName = basename($fileName);
        move_uploaded_file($tempName, "/tmp/$fileName");
      } else {
        print "      Upload attack: $tempName.\n";
      }
    } else {
      print "      Upload failed with error code = $errorCode.\n";
    }
  }
}

function dumpRequest() {
  print "\nDumping HTTP request:\n";

  print "   Request headers:\n";
  foreach (getallheaders() as $name => $value) {
    print "      $name: $value\n";
  }

  print "   \$_POST[] entries:\n";
  foreach ($_POST as $name => $value) {
    print "      $name: $value\n";
  }

  print "   Request body:\n";
  $fh = fopen("php://input", "r");
  rewind($fh);
  $req = fread($fh, 4096);
  fclose($fh);
  print "$req\n";
}
?>
```

Put the PHP script file, file-upload-handler.php, to the Apache Web server in the same place as file-upload-form.html. Then open the form again with a Web browser using http://localhost/file-upload-form.html.

Click "Choose File" buttons to select two different files, Hello.php and dot.gif.

Click "Upload" button to submit the form. The file-upload-handler.php script will be called to process uploaded files and display the following:

```
Dumping $_FILES[] - 2 entries:
   Field name = file_one
      Error code = 0
      Temp name = /private/var/tmp/phpHfgiwZ
      File name = Hello.php
      File size = 29
      File type = text/php
   Field name = file_two
      Error code = 0
      Temp name = /private/var/tmp/phpSXU4AT
      File name = dot.gif
      File size = 43
      File type = image/gif

Processing uploaded files - 2 entries:
   Field name = file_one
      File Hello.php uploaded successfully.
   Field name = file_two
      File dot.gif uploaded successfully.

Dumping HTTP request:
   Request headers:
      Host: localhost
      Content-Type: multipart/form-data; boundary=----WebKitFormBoundary...
      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
      Accept-Encoding: gzip, deflate
      Connection: keep-alive
      Upgrade-Insecure-Requests: 1
      Origin: http://localhost
      User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_6) ...
      Referer: http://localhost/local/file-upload-form.html
      Content-Length: 496
      Accept-Language: en-us
   $_POST[] entries:
      submit: Upload
   Request body:
```

If you really want to see how the HTTP POST request body looks like, you can open the browser's developer console and open the request body on the "Network" tab.

```
------WebKitFormBoundary3nhoB7aVAMQTQVI7
Content-Disposition: form-data; name="file_one"; filename="Hello.php"
Content-Type: text/php


------WebKitFormBoundary3nhoB7aVAMQTQVI7
Content-Disposition: form-data; name="file_two"; filename="dot.gif"
Content-Type: image/gif


------WebKitFormBoundary3nhoB7aVAMQTQVI7
Content-Disposition: form-data; name="submit"

Upload
------WebKitFormBoundary3nhoB7aVAMQTQVI7--
```

For some reason, the actually content of each uploaded file is still not included in the Safari browser.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟MySQL Server Connection and Access Functions

This chapter provides tutorial examples and notes about MySQL server connection with PHP. Topics include configuring the PHP engine to use the MySQL extension library, commonly used MySQL functions, running SQL statements to create table, insert rows and fetch rows.

> [Configuring PHP for MySQL Server Access](#part0135.xhtml)
> 
> [mysqli\_connect() and Other MySQL Functions](#part0136.xhtml)
> 
> [MySqlLoop.php - MySQL Functions Test](#part0137.xhtml)

Takeaways:

*   PHP supports MySQL through an extension library, php\_mysqli.dll.
*   Configuring the PHP engine to work with a MySQL server is simple - just turn on the extension=php\_mysqli.dll in php.ini.
*   A database connection resource must be created with the mysqli\_connect() function.
*   You can execute any SQL statements using the mysqli\_query() function.
*   php\_mysql.dll was removed as of PHP 7.0.0 and replaced by php\_mysqli.dll.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[MySQL Server Connection and Access Functions](#part0134.xhtml)

∟Configuring PHP for MySQL Server Access

This section provides a tutorial example on how to configure the PHP engine for MySQL server connection access. Setting, extension=php\_mysql.dll, needs to be turned in the configuration file php.ini.

To use PHP with MySQL servers, of course you need to install a MySQL server on you system first. On my local system, I have a MySQL server installed in \\mysql directory. If you need help on installing a MySQL server on your system, please read my other tutorial book, "Herong's Notes on SQL".

To make sure my MySQL server is running on my local system, I executed commands below to start my MySQL server and check its status:

```
herong> \mysql\bin\mysqld

herong> \mysql\bin\mysqladmin ping
mysqld is alive
```

Note that php\_mysql.dll was removed as of PHP 7.0.0 and replaced by php\_mysqli.dll. So I need to edit \\php\\php.ini with:

```
# for PHP 7
extension=mysqli

# for PHP 5
extension=php_mysqli.dll
```

Then I added \\php\\ext to the PATH system environment variable, because php\_mysqli.dll is located in the \\php\\ext directory.

When I was ready to test the configuration, I ran this script:

```
<?php
#  MySqlTest.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $con = mysqli_connect('localhost');
   print "MySQL server info = ".mysqli_get_server_info($con)."\n";
   print "MySQL status = ".mysqli_stat($con)."\n";
   mysqli_close($con);
?>
```

I got this output:

```
herong> php MySqlTest.php

MySQL server info = 5.6.28
MySQL status = Uptime: 1167  Threads: 1  Questions: 5  Slow queries...
  Flush tables: 1  Open tables: 0  Queries per second avg: 0.004
```

Cool, this confirmed that my PHP engine configured to access my MySQL server.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[MySQL Server Connection and Access Functions](#part0134.xhtml)

∟mysqli\_connect() and Other MySQL Functions

This section describes functions supported by the MySQL extension library, php\_mysql.dll. mysql\_connect() creates a connection to the specified MySQL server.

PHP's MySQL support comes from an extension library, php\_mysql.dll, which offers a number of functions:

*   mysqli\_connect() - Connects to a MySQL server, and returns a connection resource. In most cases, you need to call it with 3 arguments like mysqli\_connect($server, $username, $password). $server specifies the network address of machine where the MySQL server is running. $username specifies the user login name on the MySQL server. $password specifies the password for the login name.
*   mysqli\_close() - Closes a MySQL connection resource. Usually, you call it with 1 parameter like mysqli\_close($connection), where $connection represents the connection resource to be closed.
*   mysqli\_get\_server\_info() - Returns a string of server information.
*   mysqli\_status() - Returns a string of server status.
*   mysqli\_query() - Sends a query to the server, and returns a result set resource. For example, mysqli\_query('SELECT \* FROM MyTable WHERE ID = 10').
*   mysqli\_affected\_rows() - Returns the number of effected rows of the given result set, if the executed query is an INSERT or UPDATE statement.
*   mysqli\_num\_rows() - Returns the number of rows of the given result set, if the executed query is a SELECT statement.
*   mysqli\_fetch\_array() - Fetches a row from a given result set, and returns the row as an array with both numeric index, and column name map. It will return boolean false, if there is no row left in the result set.
*   mysqli\_free\_result() - Frees the given result set.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[MySQL Server Connection and Access Functions](#part0134.xhtml)

∟MySqlLoop.php - MySQL Functions Test

This section provides a tutorial example on how to use MySQL functions to connect to a MySQL server, and run SQL statements to create a table, insert rows and fetch rows with the MySQL server.

To show you how some of those MySQL functions should be used, I wrote this simple script, MySqlLoop.php:

```
<?php
#  MySqlLoop.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $con = mysqli_connect("localhost", "root", "");
   $rs = mysqli_query($con,'DROP DATABASE MyBase');
   $rs = mysqli_query($con,'CREATE DATABASE MyBase');
   if (!$rs) {
      echo "Error: Unable to create the database.\n";
      echo mysqli_connect_errno()." - ".mysqli_connect_error()."\n";
      exit;
   }
   $rs = mysqli_query($con,'USE MyBase');
   print "Creating a table...\n";
   $rs = mysqli_query($con,'CREATE TABLE MyTable (ID INTEGER,'
      .' Value INTEGER)');
   $n = 100;
   $i = 0;
   print "Inserting some rows to the table...\n";
   while ($i < $n) {
      $rs = mysqli_query($con,'INSERT INTO MyTable VALUES ('.$i.', '
         .rand(0,$n-1).')');
      $i++;
   }
   print "Query some rows from the table...\n";
   $rs = mysqli_query($con,'SELECT * FROM MyTable WHERE ID < 10');
   print "   ".mysqli_field_name($rs,0)."   "
      .mysqli_field_name($rs,1)."\n";
   while ($row = mysqli_fetch_array($rs)) {
      print "    ".$row[0].'   '.$row[1]."\n";
   }
   mysqli_free_result($rs);
   mysqli_close($con);

function mysqli_field_name($result, $field_offset) {
   $properties = mysqli_fetch_field_direct($result, $field_offset);
   return is_object($properties) ? $properties->name : null;
}
?>
```

Note that if the connection resource is not specified in a query call, the last connection resource will be used. If you run this script, you will get something like:

```
Creating a table...
Inserting some rows to the table...
Query some rows from the table...
   ID   Value
    0   14
    1   91
    2   84
    3   16
    4   88
    5   51
    6   12
    7   19
    8   39
    9   5
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Functions to Manage Directories, Files and Images

This chapter provides tutorial examples and notes about functions to manage directories, files, and images. Topics include directory management functions like mkdir(), file testing functions like is\_file(), file input and output functions like fopen().

> [opendir() and Directory Management Functions](#part0139.xhtml)
> 
> [file\_exists() and File Testing Functions](#part0140.xhtml)
> 
> [FileExistsTest.php - File Testing Examples](#part0141.xhtml)
> 
> [fopen() and File Input/Output Functions](#part0142.xhtml)
> 
> [File\_Input\_Output\_Test.php - File Input/Output Examples](#part0143.xhtml)
> 
> [readfile() and Special File Handling Functions](#part0144.xhtml)
> 
> [ShowPhoto.php - Simple Slid Show Script](#part0145.xhtml)

Takeaways:

*   PHP supports directory management functions similar to Unix commands like chdir(), mkdir() and rmdir().
*   To navigate through the directory tree, you can use opendir() and is\_dir() functions.
*   To obtain detailed information about a file, you can use the stat() function.
*   To read data from a file, you can use fopen() and fread() functions.
*   To write data to a file, you can use fopen() and fwrite() functions.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Functions to Manage Directories, Files and Images](#part0138.xhtml)

∟opendir() and Directory Management Functions

This section describes opendir() and other directory management functions. A tutorial example is provided on how to open a directory as a directory resource handle and read its entries with the readdir() function in a loop.

PHP offers the following built-in functions to manage directories of file systems:

*   chdir($path) - This "change directory" function changes the current directory to the specified path. If the specified path is invalid, it returns FALSE. For example, chdir("/herong/php") changes the current directory to /herong/php.
*   getcwd() - This "get current working directory" function returns the path name of the current directory.
*   opendir($path) - This "open directory" function creates and returns a directory resource handle that represents the directory of the specified path. The returned directory resource handle contains a current entry pointer initially set to the position before the first entry of the directory. If the specified path is invalid, it returns FALSE. For example, $dir = opendir("/herong/php") assigns a directory resource handle to $dir represents /herong/php.
*   closedir($dir) - This "close directory" function closes the specified directory resource handle.
*   readdir($dir) - This "read directory" function moves the internal pointer to the next entry in the directory represented by the specified directory resource handle and returns the entry as a string. If the internal pointer is currently pointing to the end of the directory, it returns FALSE, because there is no next entry.
*   rewinddir($dir) - This "rewind directory" function resets its internal pointer to the position before the first entry.
*   scandir($path,$order) - The "scan directory" function returns all entries in the directory of the specified path as an array sorted in the specified order. If $order is not specified or $order=0, entries are sorted alphabetically in ascending order. If $order=0, entries are sorted alphabetically in descending order.
*   dir($path) - This "directory" class constructor returns a directory object representing the directory of the specified path.
*   mkdir($path) - This "make directory" function creates a new directory with the specified path.
*   rmdir($path) - This "remove directory" function removes the directory of the specified path.

To show you how to use some of these functions should be used, I wrote this simple script:

```
<?php
#  OpendirTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $path = "/php";

   print "\n First 10 entries in $path:\n";
   $dir = opendir($path);
   $i = 0;
   while (FALSE !== ($entry = readdir($dir)) && $i<10) {
      $i++;
      print "   $entry\n";
   }

   print "\n First 10 entries in $path again:\n";
   $dir = dir($path);
   $i = 0;
   while (FALSE !== ($entry = $dir->read()) && $i<10) {
      $i++;
      print "   $entry\n";
   }
?>
```

If you run this script, you should get:

```
 First 10 entries in /php:
   .
   ..
   deplister.exe
   dev
   ext
   extras
   glib-2.dll
   gmodule-2.dll
   icudt63.dll
   icuin63.dll

 First 10 entries in /php again:
   .
   ..
   deplister.exe
   dev
   ext
   extras
   glib-2.dll
   gmodule-2.dll
   icudt63.dll
   icuin63.dll
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Functions to Manage Directories, Files and Images](#part0138.xhtml)

∟file\_exists() and File Testing Functions

This section describes some built-in file testing functions. file\_exists() allows you test if a directory or file exists or not. is\_file() returns true if the given path is a file, not a directory.

PHP offers a lots of nice built-in functions to test and manage files:

*   disk\_total\_space($path) - The "disk total space" function returns the total disk space of the specified path in number of bytes. For example, disk\_total\_space("/herong") returns the total disk space where /herong is located.
*   disk\_free\_space($path) - The "disk free space" function returns the disk free space of the specified path in number of bytes. For example, disk\_free\_space("/herong") returns the disk free space where /herong is located.
*   pathinfo($path) - This "path information" function returns information of the specified path in an array with element keys of dirname, basename, extension, and filename.
*   realpath($path) - This "real path" function returns the absolute path name of $path.
*   dirname - This "directory name" function returns the directory part of the specified path name. For example, dirname("/herong/html/index.php") returns "/herong/html".
*   basename($path, $suffix) - This "base name" function returns the file name part of the specified path name with the specified suffix removed. For example, basename("/herong/html/index.php", ".php") returns "index".
*   file\_exists($file) - This "file exists" function returns TRUE, if the specified file exists.
*   fileatime($file) - This "file access time" function returns the time of when the specified file was last accessed.
*   filemtime($file) - This "file modified time" function returns the time of when the specified file was last modified.
*   fileperms($file) - This "file permissions" function returns permission settings of the specified file.
*   filesize($file) - This "file size" function returns the size of the specified file in number of bytes.
*   filetype($file) - This "file type" function returns the type of the specified file.
*   stat($path) - This 'statistics" functions returns file information of the specified path in an array with element keys of dev, ino, mode, nlink, uid, gid, rdev, size, atime, mtime, ctime, blksize, and blocks.
*   is\_dir($path) - This "is directory" function returns TRUE, if the specified path is a directory.
*   is\_file($path) - This "is file" function returns TRUE, if the specified path is a file.
*   is\_executable($path) - This "is executable" function returns TRUE, if the specified path is an executable program.
*   is\_readable($path) - This "is readable" function returns TRUE, if the specified path is a readable file.
*   is\_writable($path) - This "is writable" function returns TRUE, if the specified path is a writable file.
*   copy($source, $dest ) - This "copy" function copies a file specified as the source to a new file specified as the destination.
*   rename($old\_name, $new\_name) - This "rename" function renames a file or a directory.
*   unlink($path) - This "un link" function removes the link to an actual file of the specified path. If this is the last link, the actual file will be removed. unlink() removes the actual file on Windows systems, since links are not supported on Windows systems.

See the next section for example PHP scripts.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Functions to Manage Directories, Files and Images](#part0138.xhtml)

∟FileExistsTest.php - File Testing Examples

This section provides a tutorial example script on how to use file testing functions like file\_exists(), is\_dir(), and stat(). The example script displays detailed information of any given file.

To show you how to use some of those file testing functions described in the previous section, I wrote this simple script:

```
<?php
#  FileExistsTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   if (count($argv) > 1) {
      $path = $argv[1];
   } else {
      print("\n Please specify a file path name.\n");
      exit();
   }

   if (file_exists($path)) {
      print("\n Very good. $path does exists!.\n");

      if (is_dir($path)) {
         print("\n   $path is a directory.\n");
      } else if (is_file($path)) {
         print("\n   $path is a file.\n");

         $type = filetype($file);
         $fileInfo = stat($path);
         print("\n   filetype() returns $type\n");
         print("\n   stat()[size] returns ".$fileInfo['size']."\n");
         print("\n   stat()[atime] returns ".$fileInfo['atime']."\n");
         print("\n   stat()[mtime] returns ".$fileInfo['mtime']."\n");
         print("\n   stat()[ctime] returns ".$fileInfo['ctime']."\n");
      } else {
         print("\n   $path is not a directory or a file.\n");
         exit();
      }
   } else {
      print("\n Too bad. $path does not exists!.\n");
      exit();
   }
?>
```

If you run this sample script with different path names, you should get:

```
herong> \php\php FileExistsTest.php \php

 Very good. \php does exists!.

   \php is a directory.


herong> \php\php FileExistsTest.php \php\php.exe

 Very good. \php\php.exe does exists!.

   \php\php.exe is a file.
   filetype() returns
   stat()[size] returns 32821
   stat()[atime] returns 1236906289
   stat()[mtime] returns 1178148192
   stat()[ctime] returns 1178148192


herong> \php\php FileExistsTest.php \php\something

 Too bad. \php\something does not exists!.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Functions to Manage Directories, Files and Images](#part0138.xhtml)

∟fopen() and File Input/Output Functions

This section describes some file input and output built-in functions. fopen() opens a file for reading and writing. fclose() closes an opened file. fread() reads data from input files. fwrite() writes data to output files.

PHP offers a number of built-in functions to read and write files:

*   fopen($path,$mode) - This "file open" function opens a file at the specified path to read or write data and returns a file resource handle. The $mode argument specifies "r", "w", or "a" as the open mode for reading, writing or appending data to the file. On Windows system, The $mode argument takes another letter, "t" or "b", to control whether the file should be opened in text mode or binary mode. In text mode, the PHP engine will do automatic conversion between \\n and \\r\\n. In binary mode, the PHP engine will not do any conversions. For example, fopen($path,"rb") opens a file for binary reading.
*   fclose($file) - This "file close" function closes the specified file resource handle.
*   fread($file,$length) - This "file read" function reads $length number of bytes from $file. and returns input bytes as a string.
*   fgets($file) - This "file get string" function reads one line from $file and returns it as a string.
*   feof($file) - This "file end of file" function returns true, if $file is pointing to the end of file currently.
*   fwrite($file,$data,$length) - This "file write" function writes $length number of bytes from $data to $file.
*   fscanf($file,$format,$var1,$var2,...) - This "file scan formatted" function parses input data into $var1, $var2,..., according to $format.
*   fprintf($file,$format,$var1,$var2,...) - This "file print formatted" function writes data from $var1, $var2,..., according to $format.
*   fflush($file) - This "file flush" function forces all buffered output to be written the actual $file.
*   ftruncate($file) - This "file truncate" function truncates $file to a given length.
*   ftell($file) - This "file tell" function returns the current position of the $file pointer in the actual file as an offset from the beginning of the file.
*   fseek($file,$offset) - This "file seek" function moves $file to the $offset position in the actual file.
*   rewind($file) - This "rewind" function $file position to beginning of the actual file.
*   flock($file,$locker) - This "file lock" function applies a locker on $file. 4 locker types are supported: LOCK\_SH, LOCK\_EX, LOCK\_UN, and LOCK\_NB.
*   fstat($file) - This "file statistics" function returns an array containing statistics information about $file. The returned array contains element keys of dev, ino, mode, nlink, uid, gid, rdev, size, atime, mtime, ctime, blksize, and blocks.
*   fgetc($file) - This "file get character" function reads 1 byte and return it as a string.

See the next section for example PHP scripts.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Functions to Manage Directories, Files and Images](#part0138.xhtml)

∟File\_Input\_Output\_Test.php - File Input/Output Examples

This section provides a tutorial example script on how to use file input and output functions like fopen(), fread(), fwrite(), and fclose(). The example script copies any file in binary mode.

To show you how to use some of those file testing functions described in the previous section, I wrote this simple script:

```
<?php
#  File_Input_Output_Test.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   if (count($argv) > 1) {
      $path = $argv[1];
   } else {
      print("\n Please specify a file path name.\n");
      exit();
   }

   if (file_exists($path)) {
      print("\n Good. $path does exists!.\n");

      if (is_file($path)) {
         print("\n Very good. $path is a file.\n");

         print("\n Starting to copy $path to $path.bck...\n");
         $input = fopen($path,"rb"); # For binary read
         $output = fopen($path.".bck","wb"); # For binary write
         $inCount = 0;
         $outCount = 0;
         while (!feof($input)) {
            $buffer = fread($input,1024);
            $inCount += strlen($buffer);
            $outCount += fwrite($output,$buffer);
         }
         fclose($input);
         fclose($output);

         print("   # of bytes read: $inCount\n");
         print("   # of bytes write: $outCount\n");
      } else {
         print("\n Too bad. $path is not a file.\n");
         exit();
      }
   } else {
      print("\n Bad. $path does not exists!.\n");
      exit();
   }
?>
```

If you run this sample script with different path names, you should get:

```
herong> \php\php File_Input_Output_Test.php \php\php.exe

 Good. \php\php.exe does exists!.

 Very good. \php\php.exe is a file.

 Starting to copy \php\php.exe to \php\php.exe.bck...
   # of bytes read: 32821
   # of bytes write: 32821


herong> \php\php File_Input_Output_Test.php \php

 Good. \php does exists!.

 Too bad. \php is not a file.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Functions to Manage Directories, Files and Images](#part0138.xhtml)

∟readfile() and Special File Handling Functions

This section describes some special file handling functions. readfile() copies a file to standard output. fgetss() reads a line with tags removed. tmpfile() opens a temporary file. file() reads a file into an array.

PHP also offers a number of other built-in functions to perform some special file input and output tasks:

*   file\_get\_contents($path) - This "file get contents" returns the entire content of the specified file as a string.
*   file\_put\_contents($path, $data) - This "file put contents" writes the specified data to the specified file.
*   file($path) - This "file" function returns the entire content of the specified file as an array. Each element in the array represents one line in the file.
*   readfile($path) - This "read file" function reads the entire content of a file and writes to the standard output.
*   fpassthru($file) - This "file pass through" function reads remaining data from $file and writes to the standard output.
*   fgetss($file) - This "file get string strip" function reads one line from $file and returns it as a string with HTML and PHP tags stripped off.
*   fgetcsv($file) - This "file get CSV" function reads one line from $file and returns it as an array by parsing the line in CSV format into array elements.
*   fputcsv($file,$array) - This "file put CSV" function writes elements from $array to $file in CSV format.
*   tmpfile() - This "temporary file" function opens a temporary file in read-write (w+) mode and returns the file resource handle. This temporary file will be removed with its file resource handle is closed.
*   tempnam($path,$prefix) - This "temporary name" function creates a temporary file name in $path with a $prefix.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Functions to Manage Directories, Files and Images](#part0138.xhtml)

∟ShowPhoto.php - Simple Slid Show Script

This section provides a tutorial example on how to display image files in a directory in a slide show format. The getimagesize() function is used to retrieve image sizes from image files.

Another nice function for image file management is the "get image size" function, getimagesize($path), which returns the size and other information about the image stored in a file located at $path.

To show you how to use this getimagesize() function, I wrote the following sample script:

```
<?php
#  PhotoShow.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
#- Get the photo file name
   $i = intval($_GET['i']);
   $c = 0;
   $p = "";
   if ($d = opendir(".")) {
      while (($f = readdir($d)) != false) {
         if (preg_match('/.jpg$/',$f)) {
            if ($i==$c) {
               $p = $f;
            }
            $c++;
         }
      }
      closedir($d);
    }

#- Build the page
   $h = fopen("header.html", "r");
   $s = fread($h, filesize("header.html"));
   fclose($h);
   print "$s\n";

   if (strlen($p)>0) {
      $i1 = ($i+$c-1) % $c;
      $i2 = ($i+$c+1) % $c;
      list($width, $height, $type, $attr) = getimagesize($p);
      if ($width>700) {
         $width = $width/2;
         $height = $height/2;
      }
      print "<center><a href=\"ShowPhoto.php?i=$i1\"><=</a>&nbsp;"
         ."<a href=\"ShowPhoto.php?i=$i2\">=></a></center>\n"
         ."<center><img src=\"$p\" border=\"1\" width=\"$width\" "
         ."height=\"$height\"></center><br\>\n"
         ."<center><a href=\"ShowPhoto.php?i=$i1\"><=</a>&nbsp;"
         ."<a href=\"ShowPhoto.php?i=$i2\">=></a></center>\n";
   } else {
      print "<p>Wrong URL. Please go back to the home page.</p>\n";
   }

   $h = fopen("footer.html", "r");
   $s = fread($h, filesize("footer.html"));
   fclose($h);
   print "$s\n";
?>
```

This script will display image files stored in a directory one image at a time like a slideshow.

Try it out. It's very easy to use. You can easily customize it to meet your requirements.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟SOAP Extension Function and Calling Web Services

This chapter provides tutorial examples and notes about SOAP extension functions. Topics include PHP implementations of SOAP, the SOAP extension library, SOAP client functions, Calling Web services with and without using the WSDL standard, example scripts to dump SOAP communication detailed debug information.

> [PHP Implementations of SOAP](#part0147.xhtml)
> 
> [Turning on the Default SOAP Extension](#part0148.xhtml)
> 
> [Hello\_There.php - First Example of SOAP](#part0149.xhtml)
> 
> [SoapClient - SOAP Client Class and Functions](#part0150.xhtml)
> 
> [Hello\_There\_Dump.php - Debugging SOAP Messages](#part0151.xhtml)
> 
> [What Is WSDL](#part0152.xhtml)
> 
> [Using SOAP Extension in non-WSDL Mode](#part0153.xhtml)

Takeaways:

*   There seems to be 3 popular PHP implementations of SOAP: PEAR SOAP, NuSOAP, and PHP Group SOAP Extension.
*   The PHP Group SOAP Extension 5.0.4 seems to be supporting SOAP 1.2. But it uses SOAP 1.1 by default.
*   WSDL is an XML based standard designed to describes protocol bindings and message formats of Web services.
*   WSDL document does help simplifying the set up process of SOAP calls. But without WSDL documents, making SOAP calls is not that hard.
*   www.xmethods.net is doing a great job for offering this demonstration SOAP service.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Extension Function and Calling Web Services](#part0146.xhtml)

∟PHP Implementations of SOAP

This section describes the SOAP protocol and PHP implementations of SOAP. PEAR::Package::SOAP, NuSOAP, and php\_soap.dll (from the PHP Group) seems to be 3 different SOAP implementations.

**What Is SOAP?** SOAP (Simple Object Access Protocol) is an XML based protocol intended for exchanging structured information in a distributed application environment.

If you search the Web with key words of "PHP Implementation of SOAP", you may find these implementations:

*   PHP SOAP extension at [php.net/manual/en/book.soap.php](http://php.net/manual/en/book.soap.php).
*   NuSOAP - SOAP Toolkit for PHP at http://sourceforge.net/projects/nusoap/. Current release: Version 0.9.5 on 2011-01-13.
*   PEAR::Package::SOAP at [http://pear.php.net/package/SOAP](http://pear.php.net/package/SOAP). It's not available any more.

PHP SOAP extension is included in the PHP distribution package:

```
herong> dir \php\ext\php_soap.dll

12/05/2018  09:38 PM           247,808 php_soap.dll
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Extension Function and Calling Web Services](#part0146.xhtml)

∟Turning on the Default SOAP Extension

This section provides a tutorial example on how to turn on the SOAP extension inluded in the default distribution package - extension=php\_soap.dll in the php.ini file.

The PHP distribution package comes with a default SOAP extension library. But it is not turned on automatically. I did the following test to see if SOAP turned on or not with the phpinfo() function:

```
herong> type PhpInfo.php
   <?php phpinfo();?>

herong> php PhpInfo.php > PhpInfo.txt

herong> find /i "soap" PhpInfo.txt
---------- PHPINFO.TXT

herong> php -v
PHP 7.3.0 (cli) (built: Dec  6 2018 01:54:19) ( ZTS MSVC15 ...
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.0-dev, Copyright (c) 1998-2018 Zend Technologies
```

So SOAP function is not available in my default installation, which is PHP 7.3.0 by The PHP Group.

The next thing I did is to to turn on the SOAP extension by editing \\php\\php.ini and update the following lines:

```
; Directory in which the loadable extensions (modules) reside.
extension_dir = "ext"
...

# PHP 7
extension=soap

# PHP 5
extension=php_soap.dll
```

I checked again:

```
herong> php PhpInfo.php > PhpInfo.txt

herong> find /i "soap" PhpInfo.txt

---------- PHPINFO.TXT
soap
Soap Client => enabled
Soap Server => enabled
soap.wsdl_cache => 1 => 1
soap.wsdl_cache_dir => /tmp => /tmp
soap.wsdl_cache_enabled => 1 => 1
soap.wsdl_cache_limit => 5 => 5
soap.wsdl_cache_ttl => 86400 => 86400
```

Cool. Some settings related to SOAP showed up now.

To check who developed this implementation, I right-mouse clicked on the file \\php\\ext\\php\_soap.dll, and selected Properties. The pop up window told me this:

```
Internal Name: php_soap.dll
File Version: 7.3.0
Copyright (c) 1997-2018 The PHP Group
```

I then browsed the installed documentation at \\php\\html\\intro.soap.html, and got the following information:

*SOAP Functions*

*Introduction*

*The SOAP extension can be used to write SOAP Servers and Clients. It supports subsets of SOAP 1.1, SOAP 1.2 and WSDL 1.1 specifications.*

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Extension Function and Calling Web Services](#part0146.xhtml)

∟Hello\_There.php - First Example of SOAP

This section provides a tutorial example on how to use the SOAP extension to call a Web service provided by herongyang.com to get a greeting message.

To show you an example of how PHP SOAP extension can be used in a SOAP client application, here is my first SOAP PHP script, Hello\_There.php

```
<?php
#  Hello_There.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient
      ("http://herongyang.com/Service/Hello_WSDL_11_SOAP.wsdl");
   echo("\nReturning value of Hello() call: ".$client->Hello());
?>
```

Run it while your computer is connected to the Internet. You will get:

```
herong> php Hello_There.php

Returning value of Hello() call:
      Hello from server - herongyang.com.
```

Very nice. This confirms that:

*   PHP SOAP extension is easy to use. Two statements are enough to call a SOAP service.
*   You PHP SOAP extension is installed correctly and working.
*   PHP SOAP extension supports WSDL.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Extension Function and Calling Web Services](#part0146.xhtml)

∟SoapClient - SOAP Client Class and Functions

This section describes the SoapClient class and functions provided in the SOAP extension library for writing SOAP client application. \_\_soapCall() allows you to make a RPC function call on the target SOAP node.

If you read the SOAP Extension reference page, you will see that SOAP extension support SOAP client applications with a class called SoapClient, which offers the following functions:

*   SoapClient->\_\_construct() - constructs a new SoapClient object
*   SoapClient->\_\_soapCall() - Calls a SOAP function
*   SoapClient->\_\_getFunctions() - Returns list of SOAP functions
*   SoapClient->\_\_getLastRequestHeaders() - Returns last SOAP request headers
*   SoapClient->\_\_getLastRequest() - Returns last SOAP request
*   SoapClient->\_\_getLastResponseHeaders() - Returns last SOAP response headers
*   SoapClient->\_\_getLastResponse() - Returns last SOAP response
*   ...

SoapClient->\_\_construct() allows you to construct a new SoapClient object with the following syntax:

```
   __construct ( mixed wsdl [, array options] );
```

where "wsdl" specifies the URL of the WSDL document, and "options" specifies a list of options:

```
   'location'     => "...", # the URL where to send the request
   'uri'          => "...", # the name space of the SOAP service
   'soap_version' => SOAP_1_1 | SOAP_1_2,
   'trace'        => 0 | 1,
   ...
```

Note that SoapClient object can be constructed in two modes, WSDL mode and non-WSDL mode:

```
   __construct( "..."[, array options] ); # WSDL mode, many options
      # are provided by the WSDL document
   __construct( null, array options ); # non-WSDL mode, 'location'
      # and 'uri' are required options.
```

SoapClient->\_\_getFunctions() allows you to get a list of functions supported by the target node. This function is only valid in WSDL mode:

```
   array $a = $obj->__getFunctions();
```

SoapClient->\_\_soapCall() allows you to make a RPC function call on the target SOAP node.

```
   $obj->__soapCall(string func_name[, array arguments [, ...]]);
```

Note that in WSDL mode, you can also make a RPC call as a local method on the SoapClient object:

```
   $obj->func_name(arg1, arg2, ...);
```

SoapClient->\_\_getLastRequestHeaders() allows you to retrieve the HTTP request header lines of the last SOAP request executed. This function works only if the SoapClient object was created with the option of "trace=1".

```
   string $s = $obj->__getLastRequestHeaders();
```

SoapClient->\_\_getLastRequest() allows you to retrieve SOAP request message of the last SOAP request executed. This function works only if the SoapClient object was created with the option of "trace=1".

```
   string $s = $obj->__getLastRequest();
```

SoapClient->\_\_getLastResponseHeaders() allows you to retrieve the HTTP response header lines of the last SOAP request executed. This function works only if the SoapClient object was created with the option of "trace=1".

```
   string $s = $obj->__getLastRequestHeaders();
```

SoapClient->\_\_getLastResponse() allows you to retrieve SOAP response message of the last SOAP request executed. This function works only if the SoapClient object was created with the option of "trace=1".

```
   string $s = $obj->__getLastResponse();
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Extension Function and Calling Web Services](#part0146.xhtml)

∟Hello\_There\_Dump.php - Debugging SOAP Messages

This section provides a tutorial example on how to use SOAP client functions to make Web service call on the target SOAP node and print detailed debug information.

After learning the basic functions of the SoapClient class, I revised my Hello\_There.php client program to get more information on how SOAP Extension works, and to show you how to debug a SOAP client program. The new client program is called, Hello\_There\_Dump.php:

```
<?php
#  Hello_There_Dump.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient
      ("http://herongyang.com/Service/Hello_WSDL_11_SOAP.wsdl",
      array('trace' => 1));

   echo("\nDumping client object:\n");
   var_dump($client);

   echo("\nDumping client object functions:\n");
   var_dump($client->__getFunctions());

   $return = $client->Hello();
   echo("\nReturning value of Hello() call: ".$return);

   $return = $client->__soapCall("Hello",array());
   echo("\nReturning value of __soapCall() call: ".$return);

   echo("\nDumping request headers:\n"
      .$client->__getLastRequestHeaders());

   echo("\nDumping request:\n".$client->__getLastRequest());

   echo("\nDumping response headers:\n"
      .$client->__getLastResponseHeaders());

   echo("\nDumping response:\n".$client->__getLastResponse());
?>
```

If you run this sample script, you will get:

```
Dumping client object:
object(SoapClient)#1 (3) {
  ["trace"]=>
  int(1)
  ["_soap_version"]=>
  int(1)
  ["sdl"]=>
  resource(6) of type (Unknown)
}

Dumping client object functions:
array(1) {
  [0]=>
  string(36) "string Hello(string $helloInputPart)"
}

Returning value of Hello() call:
      Hello from server - herongyang.com.

Returning value of __soapCall() call:
      Hello from server - herongyang.com.

Dumping request headers:
POST /Service/Hello_SOAP_11.php HTTP/1.1
Host: www.herongyang.com
Connection: Keep-Alive
User-Agent: PHP-SOAP/7.3.0
Content-Type: text/xml; charset=utf-8
SOAPAction: "https://www.herongyang.com/Service/Hello"
Content-Length: 235


Dumping request:
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="https://www.herongyang.com/Service/">
 <SOAP-ENV:Body>
  <ns1:HelloRequest/>
 </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

Dumping response headers:
HTTP/1.1 200 OK
Server: Apache
X-Powered-By: PHP/7.2.14
Keep-Alive: timeout=2, max=199
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: text/xml

Dumping response:
<soapenv:Envelope
  xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
  xmlns:hy="https://www.herongyang.com/Service/">
  <soapenv:Header/>
  <soapenv:Body>
    <hy:HelloResponse>
      Hello from server - herongyang.com.
    </hy:HelloResponse>
  </soapenv:Body>
</soapenv:Envelope>
```

The output is very useful. It confirms that:

*   The default SOAP version is SOAP 1.1. For SOAP 1.2, the envelope namespace should be http://www.w3.org/2003/05/soap-envelope, not http://schemas.xmlsoap.org/soap/envelope/.
*   The transportation protocol is HTTP/1.1. See the request header lines.
*   There is only one RPC function supported in this WSDL: "string Hello(string $helloInputPart)". See the \_\_getFunctions() dump.
*   SOAP Extension converts my Hello() RPC call nicely in a SOAP request message based on the definitions in the WSDL document.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Extension Function and Calling Web Services](#part0146.xhtml)

∟What Is WSDL

This section describes what is WSDL - an XML based standard designed to describes protocol bindings and message formats of Web services.

**What Is WSDL?** WSDL (Web Services Definition Language) is an XML based standard designed to describes protocol bindings and message formats of Web services. WSDL is often pronounced as "Whiz-Dull".

A WSDL document is an XML document written in WSDL to describe Web service. Here is a copy of the WSDL document for the demonstration Web service used in previous sections. You can download one yourself by going to http://herongyang.com/Service/Hello\_WSDL\_11\_SOAP.wsdl with your Web browser:

```
<?xml version="1.0"?>
<wsdl:definitions xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/"
  xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
  xmlns:hy="https://www.herongyang.com/Service/"
  targetNamespace="https://www.herongyang.com/Service/">

  <wsdl:documentation>
    Hello_WSDL_11_SOAP.wsdl
    Copyright (c) 2009 HerongYang.com. All Rights Reserved.
    All rights reserved
  </wsdl:documentation>

  <wsdl:types>
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
      targetNamespace="https://www.herongyang.com/Service/">
      <xsd:element name="HelloRequest" type="xsd:string"/>
      <xsd:element name="HelloResponse" type="xsd:string"/>
    </xsd:schema>
  </wsdl:types>

  <wsdl:message name="helloInputMessage">
    <wsdl:part name="helloInputPart" element="hy:HelloRequest"/>
  </wsdl:message>
  <wsdl:message name="helloOutputMessage">
    <wsdl:part name="helloOutputPart" element="hy:HelloResponse"/>
  </wsdl:message>

  <wsdl:portType name="helloPortType">
    <wsdl:operation name="Hello">
      <wsdl:input name="helloInput"
        message="hy:helloInputMessage"/>
      <wsdl:output name="helloOutput"
        message="hy:helloOutputMessage"/>
    </wsdl:operation>
  </wsdl:portType>

  <wsdl:binding name="helloBinding" type="hy:helloPortType">
    <soap:binding transport="http://schemas.xmlsoap.org/soap/http"/>
    <wsdl:operation name="Hello">
      <soap:operation
        soapAction="https://www.herongyang.com/Service/Hello"/>
      <wsdl:input name="helloInput">
        <soap:body use="literal"/>
      </wsdl:input>
      <wsdl:output name="helloOutput">
        <soap:body use="literal"/>
      </wsdl:output>
    </wsdl:operation>
  </wsdl:binding>

  <wsdl:service name="helloService">
    <wsdl:port name="helloPort" binding="hy:helloBinding">
      <soap:address
location="https://www.herongyang.com/Service/Hello_SOAP_11.php"/>
    </wsdl:port>
  </wsdl:service>

</wsdl:definitions>
```

I cannot read this document well before learning the WSDL specifications. But it seems to be describing precisely how this Web service should be used. See my other book: ["SOAP Web Service Tutorials - Herong's Tutorial Examples"](http://herongyang.com/Web-Services/) for more information on SOAP and WSDL.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Extension Function and Calling Web Services](#part0146.xhtml)

∟Using SOAP Extension in non-WSDL Mode

This section provides a tutorial example on how to use SOAP client functions to make Web service call without using the WSDL standard on the target SOAP node and print detailed debug information.

I think we had enough fun with the WSDL mode. Let's try the non-WSDL mode now. Here is the third version of my Get\_Temperature.php SOAP client program, Hello\_There\_Non\_WSDL.php:

```
<?php
#  Hello_There_Non_WSDL.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient(null, array(
      'location' =>
         "https://www.herongyang.com/Service/Hello_SOAP_11.php",
      'uri'      => "https://www.herongyang.com/Service/",
      'trace'    => 1 ));

   echo("\nDumping client object:\n");
   var_dump($client);

   $return = $client->__soapCall("Hello",array());
   echo("\nReturning value of __soapCall() call: ".$return);

   echo("\nDumping request headers:\n"
      .$client->__getLastRequestHeaders());

   echo("\nDumping request:\n".$client->__getLastRequest());

   echo("\nDumping response headers:\n"
      .$client->__getLastResponseHeaders());

   echo("\nDumping response:\n".$client->__getLastResponse());
?>
```

If you run this sample script, you will get:

```
Dumping client object:
object(SoapClient)#1 (4) {
  ["uri"]=>
  string(34) "https://www.herongyang.com/Service/"
  ["location"]=>
  string(51) "https://www.herongyang.com/Service/Hello_SOAP_11.php"
  ["trace"]=>
  int(1)
  ["_soap_version"]=>
  int(1)
}

Returning value of __soapCall() call:
Dumping request headers:
POST /Service/Hello_SOAP_11.php HTTP/1.1
Host: www.herongyang.com
Connection: Keep-Alive
Content-Type: text/xml; charset=utf-8
SOAPAction: "https://www.herongyang.com/Service/#Hello"
Content-Length: 399


Dumping request:
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="https://www.herongyang.com/Service/"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
 SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
 <SOAP-ENV:Body>
  <ns1:Hello/>
 </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

Dumping response headers:
HTTP/1.1 200 OK
Server: Apache
Keep-Alive: timeout=2, max=200
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: text/xml

Dumping response:
<soapenv:Envelope
  xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
  xmlns:hy="https://www.herongyang.com/Service/">
  <soapenv:Header/>
  <soapenv:Body>
    <hy:HelloResponse>
      Hello from server - herongyang.com.
    </hy:HelloResponse>
  </soapenv:Body>
</soapenv:Envelope>
```

The output shows that:

*   My Hello\_There\_Non\_WSDL.php works the same as the WSDL mode version.
*   If you compare this output with the WSDL output, SOAP Extension generates the request headers with one difference: SOAPAction is not blank any more. It has the value of "https://www.herongyang.com/Service/#Hello".

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟SOAP Server Functions and Examples

This chapter provides tutorial examples and notes about SOAP server functions and examples. Topics include introduction to SOAP server class and functions, SOAP server example - HelloServer.php, server examples with SOAP 1.1 and 1.2, server example in WSDL mode.

> [SoapServer - SOAP Server Class and Functions](#part0155.xhtml)
> 
> [HelloServer.php - First SOAP Server Application](#part0156.xhtml)
> 
> [HelloServer12.php - First SOAP 1.2 Server Application](#part0157.xhtml)
> 
> [HelloServerWsdl.php - SOAP 1.2 Server Application in WSDL Mode](#part0158.xhtml)

Takeaways:

*   SOAP Extension is easy to use for setting up SOAP server to provide Web services quickly.
*   SOAP Extension does support SOAP 1.1 and 1.2 specifications.
*   WSDL document is actually easy to understand.

**Exercise**: Write a temperature conversion SOAP service.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Server Functions and Examples](#part0154.xhtml)

∟SoapServer - SOAP Server Class and Functions

This section describes the SoapServer class and functions provided in the SOAP extension library for writing SOAP server application.

If you read the SOAP Extension reference page, you will see that SOAP Extension support SOAP server applications with a class called SoapServer, which offers the following functions:

*   SoapServer->\_\_construct() - construct a new SoapServer object
*   SoapServer->addFunction() - Adds one or several functions those will handle SOAP requests
*   SoapServer->setClass() - Sets class which will handle SOAP requests
*   SoapServer->handle() - Handles a SOAP request
*   SoapServer->getFunctions() - Returns list of defined functions
*   ...

SoapServer->\_\_construct() allows you to construct a new SoapServer object with the following syntax:

```
   __construct ( mixed wsdl [, array options] );
```

where "wsdl" specifies the URL of the WSDL document, and "options" specifies a list of options:

```
   'uri'          => "...", # the name space of the SOAP service
   'soap_version' => SOAP_1_1 |SOAP_1_2,
   'actor'        => "...", # the actor
   'encoding'     => "...", # the encoding name
   'classmap'     => "...", # a map of WSDL types to PHP classes
   ...
```

Note that SoapServer object can be constructed in two modes, WSDL mode and non-WSDL mode:

```
   __construct( "..."[, array options] ); # WSDL mode, many options
      # are provided by the WSDL document
   __construct( null, array options ); # non-WSDL mode,
      # 'uri' is a required option.
```

SoapServer->addFunction() allows you to add one or more functions to handle SOAP requests. The functions to be added are functions defined in the current PHP program file.

```
   $obj->addFunction("func"); # adds one function
   $obj->addFunction(array("func1",...)); # adds many functions
   $obj->addFunction(SOAP_FUNCTIONS_ALL); # adds all functions
```

SoapServer->setClass() allows you to call methods in the specified class to handle SOAP requests.

```
   $obj->setClass("cls");
```

SoapServer->handle() allows you to return the execution back the SOAP Extension to handle the incoming SOAP request.

```
   $obj->handle();
```

SoapServer->getFunctions() allows you to get a list of all functions that have been assigned to handle SOAP requests.

```
   array $a = $obj->getFunctions();
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Server Functions and Examples](#part0154.xhtml)

∟HelloServer.php - First SOAP Server Application

This section provides a tutorial example on how to write a simple SOAP server application. The HelloServer.php example defines a hello() function, adds it to the SOAP server, waits for the client program to call.

Okay. Now let's build our first SOAP server. I want the first server to perform a very simple function of return a greeting string based on the input name. Here is my version called, HelloServer.php:

```
<?php
#  HelloServer.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
function hello($someone) {
   return "Hello " . $someone . "!";
}
   $server = new SoapServer(null,
      array('uri' => "urn://www.herong.home/res"));
   $server->addFunction("hello");
   $server->handle();
?>
```

The sever application is ready. Note that:

*   This SOAP server application can not be used as a standalone SOAP server. It needs a HTTP server to receive SOAP requests, and a PHP runtime to act as a CGI to feed SOAP requests.
*   The "uri" value is just an unique identification, used as the namespace for the response message.

The HTTP server I will be using is the Apache Server. It has already configured correctly to interface with PHP CGI. All I have to do is to move my server application to Apache document directory:

```
herong> copy HelloServer.php \apache\htdocs
```

To test my server application, I wrote this client application, HelloClient.php:

```
<?php
#  HelloClient.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient(null, array(
      'location' => "http://localhost/HelloServer.php",
      'uri'      => "urn://www.herong.home/req",
      'trace'    => 1 ));

   $return = $client->__soapCall("hello",array("world"));
   echo("\nReturning value of __soapCall() call: ".$return);

   echo("\nDumping request headers:\n"
      .$client->__getLastRequestHeaders());

   echo("\nDumping request:\n".$client->__getLastRequest());

   echo("\nDumping response headers:\n"
      .$client->__getLastResponseHeaders());

   echo("\nDumping response:\n".$client->__getLastResponse());
?>
```

Check your Web server to make sure it is running. Then run HelloClient.php. You will get:

```
Returning value of __soapCall() call: Hello world!

Dumping request headers:
POST /HelloServer.php HTTP/1.1
Host: localhost
Connection: Keep-Alive
Content-Type: text/xml; charset=utf-8
SOAPAction: "urn://www.herong.home/req#hello"
Content-Length: 499

Dumping request:
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="urn://www.herong.home/req"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
 SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
 <SOAP-ENV:Body><ns1:hello>
  <param0 xsi:type="xsd:string">world</param0>
 </ns1:hello></SOAP-ENV:Body>
</SOAP-ENV:Envelope>

Dumping response headers:
HTTP/1.1 200 OK
Server: Apache
Connection: close
Content-Type: text/xml; charset=utf-8
Content-Length: 522

Dumping response:
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="urn://www.herong.home/res"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
 SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
 <SOAP-ENV:Body><ns1:helloResponse>
  <return xsi:type="xsd:string">Hello world!</return>
 </ns1:helloResponse></SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Very exciting, right? Both server and client work nicely.

If you are interested in how the execution was carried out on the server, I have a simplified execution flow diagram on the server side:

```
                 IIS      PHP (SOAP Extension)      HelloServer.php
    HTTP request  |
   -------------->|
    SOAP message  |
                  |  CGI   |      PHP CGI API
                  |------->|------------------------>|
                                                     | addFunction()
                                                     |
                                SOAP Extension API   | handle()
                           |<------------------------|
                           |
                           |    SOAP Extension API
                           |------------------------>|
                                                     |
                                SOAP Extension API   | hello()
                           |<------------------------|
                     CGI   |
                  |<-------|
    HTTP response |
   <--------------|
    SOAP message  |
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Server Functions and Examples](#part0154.xhtml)

∟HelloServer12.php - First SOAP 1.2 Server Application

This section provides a tutorial example on how to write a simple SOAP 1.2 server application. The HelloServer.php example defines a hello() function, adds it to the SOAP server, waits for the client program to call.

So far, we have tried only with SOAP 1.1. Can we do some tests with SOAP 1.2? Sure. Here is my hello server modified for SOAP 1.2, HelloServer12.php:

```
<?php
#  HelloServer12.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
function hello($someone) {
   return "Hello " . $someone . "! - SOAP 1.2";
}
   $server = new SoapServer(null, array(
      'uri' => "urn://www.herong.home/res",
      'soap_version' => SOAP_1_2));
   $server->addFunction("hello");
   $server->handle();
?>
```

Here is my hello client modified for SOAP 1.2, HelloClient12.php:

```
<?php
#  HelloClient12.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient(null, array(
      'location' => "http://localhost/HelloServer12.php",
      'uri'      => "urn://www.herong.home/req",
      'soap_version' => SOAP_1_2,
      'trace'    => 1 ));

   $return = $client->__soapCall("hello",array("world"));
   echo("\nReturning value of __soapCall() call: ".$return);

   echo("\nDumping request headers:\n"
      .$client->__getLastRequestHeaders());

   echo("\nDumping request:\n".$client->__getLastRequest());

   echo("\nDumping response headers:\n"
      .$client->__getLastResponseHeaders());

   echo("\nDumping response:\n".$client->__getLastResponse());
?>
```

Remember to move HelloServer12.php to IIS document directory. Then run HelloClient12.php. You will get:

```
Returning value of __soapCall() call: Hello world! - SOAP 1.2

Dumping request headers:
POST /HelloServer12.php HTTP/1.1
Host: localhost
Connection: Keep-Alive
Content-Type: application/soap+xml;
   charset=utf-8; action="urn://www.herong.home/req#hello"
Content-Length: 458

Dumping request:
<?xml version="1.0" encoding="UTF-8"?>
<env:Envelope
 xmlns:env="http://www.w3.org/2003/05/soap-envelope"
 xmlns:ns1="urn://www.herong.home/req"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:enc="http://www.w3.org/2003/05/soap-encoding">
 <env:Body>
  <ns1:hello
   env:encodingStyle="http://www.w3.org/2003/05/soap-encoding">
   <param0 xsi:type="xsd:string">world</param0>
  </ns1:hello>
 </env:Body>
</env:Envelope>

Dumping response headers:
HTTP/1.1 200 OK
Server: Microsoft-IIS/5.1
Connection: close
Content-Type: application/soap+xml; charset=utf-8
Content-Length: 570

Dumping response:
<?xml version="1.0" encoding="UTF-8"?>
<env:Envelope
 xmlns:env="http://www.w3.org/2003/05/soap-envelope"
 xmlns:ns1="urn://www.herong.home/res"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:enc="http://www.w3.org/2003/05/soap-encoding">
 <env:Body
  xmlns:rpc="http://www.w3.org/2003/05/soap-rpc">
  <ns1:helloResponse
   env:encodingStyle="http://www.w3.org/2003/05/soap-encoding">
   <rpc:result>return</rpc:result>
   <return xsi:type="xsd:string">Hello world! - SOAP 1.2</return>
  </ns1:helloResponse>
 </env:Body>
</env:Envelope>
```

Now the output is more interesting:

*   SOAP 1.2 HTTP Binding rules are applied. See the HTTP request header line: Content-Type. It has a value of "application/soap+xml", and parameter of "action=...".
*   SOAP 1.2 Message rules are applied. See the envelope namespace value in both request message and response message: xmlns:env="http://www.w3.org/2003/05/soap-envelope.
*   SOAP 1.2 RPC Presentation rules are applied. See the "result" sub element in the response element of the response message. But SOAP Extension does not put the returning value directly in this sub element. It inserts a second sub element in the response element, and puts the returning value in this second element. The value in the required "result" element is just a reference to the second element. This seems to be violating the SOAP 1.2 RPC Presentation specifications.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[SOAP Server Functions and Examples](#part0154.xhtml)

∟HelloServerWsdl.php - SOAP 1.2 Server Application in WSDL Mode

This section provides a tutorial example on how to write a simple SOAP 1.2 server application in WSDL mode. The HelloServer.php example defines a hello() function, adds it to the SOAP server, waits for the client program to call.

Now let's move forward one step further: creating a SOAP 1.2 server application in WSDL mode. Here is the same hello server modified to work in WSDL mode, HelloServerWdsl.php:

```
<?php
#  HelloServerWsdl.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
function hello($someone) {
   return "Hello " . $someone . "! - With WSDL";
}
   ini_set("soap.wsdl_cache_enabled", "0");
   $server = new SoapServer("http://localhost/Hello.wsdl",
      array('soap_version' => SOAP_1_2));
   $server->addFunction("hello");
   $server->handle();
?>
```

Nothing special in the program. The server object is now created with the location of the WSDL document.

Here is the WSDL document, Hello.wsdl

```
<?xml version="1.0"?>
<definitions name="MyDefinition"
 targetNamespace="urn:myTargetNamespace"
 xmlns:tns="urn:myTns"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
 xmlns="http://schemas.xmlsoap.org/wsdl/">
 <message name="myRequest">
  <part name="reqParam" type="xsd:string"/>
 </message>
 <message name="myResponse">
  <part name="resParam" type="xsd:string"/>
 </message>
 <portType name="MyPortType">
  <operation name="hello">
   <input message="tns:myRequest"/>
   <output message="tns:myResponse"/>
  </operation>
 </portType>
 <binding name="MyBinding" type="tns:MyPortType">
  <soap:binding style="rpc"
   transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="hello">
   <soap:operation soapAction=""/>
   <input>
    <soap:body use="encoded"
     namespace="urn:myInputNamespace"
     encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"/>
   </input>
   <output>
    <soap:body use="encoded"
     namespace="urn:myOutputNamespace"
     encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"/>
   </output>
  </operation>
 </binding>
 <service name="MyService">
  <documentation>Returns a greeting string.
  </documentation>
  <port name="MyPort" binding="tns:MyBinding">
   <soap:address
  location="http://localhost/HelloServerWsdl.php"/>
  </port>
 </service>
</definitions>
```

The WSDL document looks complicated. But it actually very simple to understand, as long as you remember the following points:

*   Read the document backward. The goal of this document is to define a "service" with two pieces of information: "binding" definition, and "url" where to reach the server. The "binding" is then defined with "type", "style", "transportation" and "operation". And so on.
*   The values of "name" attributes in most of the elements are identifiers local to this document only. You can use any strings. Some of them will be used on the SOAP messages.
*   The values of "namespace" attributes can also be any strings. They are just used to distinguish name spaces.

To install HelloServerWsdl.php to my Apache server, copy these two files to the Apache document directory:

```
herong> copy HelloServerWsdl.php \apache\htdocs
herong> copy Hello.wsdl \apache\htdocs
```

Of course, we need to modify out hello client program as, HelloClientWsdl.php:

```
<?php
#  HelloClientWsdl.php
#- Copyright 2009-2015 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient("http://localhost/Hello.wsdl",
      array('soap_version' => SOAP_1_2,'trace' => 1 ));

   echo("\nDumping client object functions:\n");
   var_dump($client->__getFunctions());

   $return = $client->__soapCall("hello",array("world"));
   echo("\nReturning value of __soapCall() call: ".$return);

#   $return = $client->hello("world");
#   echo("\nReturning value: ".$return);

   echo("\nDumping request headers:\n"
      .$client->__getLastRequestHeaders());

   echo("\nDumping request:\n".$client->__getLastRequest());

   echo("\nDumping response headers:\n"
      .$client->__getLastResponseHeaders());

   echo("\nDumping response:\n".$client->__getLastResponse());
?>
```

When you are ready to test, run HelloClientWsdl.php. You will get:

```
Dumping client object functions:
array(1) {
  [0]=>
  string(30) "string hello(string $reqParam)"
}

Returning value of __soapCall() call: Hello world! - With WSDL

Dumping request headers:
POST /HelloServerWsdl.php HTTP/1.1
Host: localhost
Connection: Keep-Alive
Content-Type: application/soap+xml; charset=utf-8; action=""
Content-Length: 457

Dumping request:
<?xml version="1.0" encoding="UTF-8"?>
<env:Envelope
 xmlns:env="http://www.w3.org/2003/05/soap-envelope"
 xmlns:ns1="urn:myInputNamespace"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:enc="http://www.w3.org/2003/05/soap-encoding">
 <env:Body>
  <ns1:hello
   env:encodingStyle="http://www.w3.org/2003/05/soap-encoding">
   <reqParam xsi:type="xsd:string">world</reqParam>
  </ns1:hello>
 </env:Body>
</env:Envelope>

Dumping response headers:
HTTP/1.1 200 OK
Server: Microsoft-IIS/5.1
Connection: close
Content-Type: application/soap+xml; charset=utf-8
Content-Length: 573

Dumping response:
<?xml version="1.0" encoding="UTF-8"?>
<env:Envelope
 xmlns:env="http://www.w3.org/2003/05/soap-envelope"
 xmlns:ns1="urn:myOutputNamespace"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:enc="http://www.w3.org/2003/05/soap-encoding">
 <env:Body xmlns:rpc="http://www.w3.org/2003/05/soap-rpc">
  <ns1:helloResponse
   env:encodingStyle="http://www.w3.org/2003/05/soap-encoding">
   <rpc:result>resParam</rpc:result>
   <resParam xsi:type="xsd:string">Hello world! - With WSDL</resParam>
  </ns1:helloResponse>
 </env:Body>
</env:Envelope>
```

Anything interesting here? Yes. Some names defined in the WSDL document did show up in the SOAP request message and response message, like: "urn:myInputNamespace", "reqParam", "urn:myOutputNamespace", etc.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Localization Overview of Web Applications

This chapter provides tutorial examples and notes about Web application localization. Topics include what is localization; software components in Web applications; travel paths of output and input character strings; outputting ASCII character from PHP scripts.

> [What Is Localization / Internationalization](#part0160.xhtml)
> 
> [Localization of Web Based Applications](#part0161.xhtml)
> 
> [Character String Traveling Paths](#part0162.xhtml)
> 
> [Output ASCII Character Strings from PHP Scripts](#part0163.xhtml)

Takeaways:

*   Localization is mainly a process of managing input and output character strings in a specific language tailored to the end user.
*   In a Web application, characters must travel through different paths involving a number of programs and systems.
*   ASCII characters have no problems to travel through different programs and systems.
*   Non ASCII characters must be encoded into a safe format to travel through different programs and systems.
*   Tutorial notes are provided in the next 5 chapters for handling non ASCII characters in different areas: HTML documents, PHP string literals, HTML input forms, PHP string functions, and MySQL databases.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Localization Overview of Web Applications](#part0159.xhtml)

∟What Is Localization / Internationalization

This section describes what is localization and internationalization. Locale is a concept that defines geographical and cultural specific preferences on the user interface.

Localization (software localization), sometimes shortened to "l10n", is a process that tailors software user interface for the user based on his/her specific geographical, and cultural preferences.

Internationalization (software Internationalization), sometimes shortened to "i18n", is a process of enabling software for localization.

Users specific geographical and cultural preferences can be abstracted into a concept of locale. A locale usually determines the following aspects of the user interface:

*   Using the specific language for system output and user input.
*   Using the specific time zone and date/time format.
*   Using the specific currency and numbering system.

We know that the main task of localization is to communicate with user in the local language. This means that software must present information as characters of the local language, and take information as characters of the local language.

In this part of the book, we will concentrate on presenting and managing information as characters of the local language.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Localization Overview of Web Applications](#part0159.xhtml)

∟Localization of Web Based Applications

This section describes what are involved in localization of a Web based application, which uses multiple programs: Web browser, Web server, application server, and database server.

Managing character strings of a specific language in a Web based application is not a simple task, because there are a number of software components involved in a typical Web based application. We have to understand how each of them manages character strings and how we transfer character strings from one component to another component.

First, let me try to abstract software programs involved in a Web application into the following list:

*   Web browser: End user interface program responsible for presenting and taking characters to and from users.
*   Web server: Communication program responsible for forwarding characters between Web browser and application program.
*   Application program: Program developed by you for processing characters received from the Web server and/or retrieved from the database server.
*   Database server: Storage program responsible for storing characters.
*   Development environment: Software program responsible for embedding characters into the source code of the application program.

Before we get into details of how characters are handled in those programs, we need to understand how characters of a specific language are represented in computers. Here is my understanding:

*   Characters of English language can be represented by ASCII encoding schema. ASCII encoding schema represents one English character into one byte.
*   Characters of a non English language can be represented either in Unicode encoding schema or in a specific encoding scheme designed for that language. For example, characters of simplified Chinese can be represented either in Unicode or in GB2312. Characters of Japanese can be represented either in Unicode or in Shift-JIS.
*   Unicode encoding schema has several encoding variations: Unicode internal code, UTF-8, UTF16, etc.

To read more about character encoding and Unicode, see my other book: "Herong's tutorial notes on Unicode".

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Localization Overview of Web Applications](#part0159.xhtml)

∟Character String Traveling Paths

This section describes steps of connection paths that character strings must travel through in a typical Web based application: output characters strings come from PHP files or data base tables and input character strings come from user's Web browser.

In a typical Web based application, character strings will travel from one part of the application to another part. Here are some possible paths character strings may travel through.

**From PHP file to Web browser**: The following diagram illustrates steps that character strings must travel through from a PHP file to a browser screen. It also shows the computing technologies that are used at different steps:

```
A1. Key Sequences from keyboard
      |
      |- Text editor
      v
A2. PHP File
      |
      |- PHP CGI engine
      v
A3. HTML Document
      |
      |- Web server
      v
A4. HTTP Response
      |
      |- Internet TCP/IP Connection
      v
A5. HTTP Response
      |
      |- Web browser
      v
A6. Visual characters on the screen
```

**From Database to Web browser**: The following diagram illustrates steps that character strings must travel through from a database table to a browser screen. It also shows computing technologies that are used at different steps:

```
B1. Byte sequences in storage
      |
      |- Database server
      v
B2. Byte stream
      |
      |- Database connection driver
      v
B3. Byte stream
      |
      |- PHP Application
      v
B4. HTTP Response
      |
      |- Internet TCP/IP Connection
      v
B5. HTTP Response
      |
      |- Web browser
      v
B6. Visual characters on the Screen
```

**From Web browser to Database**: The following diagram illustrates steps that character strings must travel from a Web browser to a database table. It also shows computing technologies that are used at different steps:

```
C1. Key sequences on keyboard
      |
      |- Language input tool (optional)
      v
C2. Byte sequences
      |
      |- Browser input form
      v
C3: HTTP request
      |
      |- Internet TCP/IP Connection
      v
C4. HTTP request
      |
      |- Web server
      v
C5. CGI variables and input stream
      |
      |- PHP Application
      v
C6. PHP variables
      |
      |- Database connection driver
      v
C7. Byte stream
      |
      |- Database server
      v
C8. Byte sequence in storage
```

Since all computing technologies are using ASCII encoding by default, text of ASCII characters can safely travel through those steps without any issues.

However, for non ASCII characters, we have to watch out each steps carefully to make sure that characters are not damaged and are encoded and decoded correctly.

Now I will try to provide some tutorials in this chapter and next 5 chapters to show you how to handle characters correctly in different steps of different connection paths.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Localization Overview of Web Applications](#part0159.xhtml)

∟Output ASCII Character Strings from PHP Scripts

This section provides tutorial example on how to include output ASCII character strings in a PHP script file. ASCII characters can be entered directly as string literals in PHP code segments or as text in non-PHP code segments. No special techniques are needed.

As I mentioned earlier, ASCII characters can travel from PHP files to browsers easily without any trouble. Here is a simple PHP file with ASCII characters only:

```
<?php
#  HelpASCII.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print("<html><body>\n");
   print("<b>Help</b><br/>\n");
   print("This is a very simple help page...<br/>\n");
?>
This is a very simple help page...<br/>
</body></html>
```

If you view this page with a browser, you will get the following output:

```
Help
This is a very simple help page...
This is a very simple help page...
```

Perfect, right? ASCII text entered as a PHP string literal travels through correctly. Text entered as HTML static text outside the PHP block travels through also correctly.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Using Non-ASCII Characters in HTML Documents

This chapter provides tutorial examples and notes about non-ASCII characters in HTML documents. Topics include basic rules on using non-ASCII characters in HTML documents; examples of using French characters with UTF-8 and ISO-8859-1 encodings; examples of using Chinese characters with UTF-8 and GB2312 encodings.

> [Basic Rules of Using Non-ASCII Characters in HTML Documents](#part0165.xhtml)
> 
> [French Characters in HTML Documents - UTF-8 Encoding](#part0166.xhtml)
> 
> [French Characters in HTML Documents - ISO-8859-1 Encoding](#part0167.xhtml)
> 
> [Chinese Characters in HTML Documents - UTF-8 Encoding](#part0168.xhtml)
> 
> [Chinese Characters in HTML Documents - GB2312 Encoding](#part0169.xhtml)
> 
> [Characters of Multiple Languages in HTML Documents](#part0170.xhtml)

Takeaways:

*   You can only use one encoding schema in a HTML document. You should a <meta> tag to specify the encoding name.
*   Entering non ASCII characters into a HTML document with the desired encoding is a challenge. If you are not sure on what encoding used by the editor to store HTML document, open the document with another editor to validate.
*   Use UTF-8 as the HTML document encoding instead of encodings of a particular local language, like GB2312. This may cause problems for users on local systems where Unicode fonts are not supported. But more and more local systems are supporting Unicode and UTF-8 encoding.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters in HTML Documents](#part0164.xhtml)

∟Basic Rules of Using Non-ASCII Characters in HTML Documents

This section describes basic rules on how non-ASCII character strings should be managed at different steps to ensure localized text strings can be used in HTML documents and displayed correctly on the browser window.

As you can see from the previous chapters, a Web based application always delivers information to the user interface as a HTML document. The application can either take a static HTML document from the file system, or generate a dynamic HTML document from a PHP script.

First, let's concentrate on how to handle non ASCII characters in static HTML documents. Here are the steps and technologies involved in entering a HTML document and delivering it to the user interface:

```
H1. Key Sequences from keyboard
      |
      |- Text editor
      v
H2. HTML Document
      |
      |- Web server
      v
H3. HTTP Response
      |
      |- Internet TCP/IP Connection
      v
H4. HTTP Response
      |
      |- Web browser
      v
H5. Visiual characters on the Screen
```

Based on my experience, here are some basic rules related to those steps:

1\. You must decide on the character encoding schema to be used in the HTML document first. For most of human written languages, you have two options, a) use a encoding schema specific to that language; b) use a Unicode schema. For example, you can use either GB2312 (a simplified Chinese character schema) or UTF-8 (a Unicode character schema) for Chinese characters. My suggestion used to be "a". But from now on, I am suggesting "b", because Unicode schema can support all characters of all languages.

2\. PHP seems to be a nice language. The data type of string is defined as a sequence of bytes, like C language. This is different than Java language, where string is defined as a sequence of Unicode characters. String literals in PHP can take any sequence of bytes. Therefore you can enter non ASCII characters as PHP string literals in any encoding schema.

3\. From step "H1" to "H2", you need select good text editor that supports the encoding schema you have selected. The end goal of this step is simple - characters in the HTML documents must be stored in a file using the selected encoding schema. Don't under estimate the difficulty level of this step. It could be very frustrating, because most computer keyboards support alphabetic letters only. You may have to use some language specific input software to translate alphabetic letters into language specific characters. The editor sometimes may also store characters in memory in one encoding schema, and offer you different encoding schema when saving files to hard disk.

4\. From step "H3" to "H4", it is the job for the Internet to send data from the Web server to the Web browser. The HTTP response will be transmitted as is to the browser. The characters in the HTML document attached in the HTTP response will also be maintained as is.

5\. From step "H4" to "H5", the browser opens the received HTML document and displays encoded characters as written characters of the specific language. To do this, the browser needs your help. The first help is to specify the character encoding name, "charset", used in the HTML document as a <meta> tag. The second help is to make sure the browser can access the a character font file designed for the specified encoding schema.

If no character encoding name is specified in the <meta> tag, some browsers will try to detect the encoding schema based on the HTML document content. If not successful, browsers will use default encoding schemas. For example, Internet Explorer (IE) use "Western European" as the default encoding schema. "Western European" seems to be referring to "ISO-8859-1" standard.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters in HTML Documents](#part0164.xhtml)

∟French Characters in HTML Documents - UTF-8 Encoding

This section provides a tutorial example on how enter and use French characters in HTML documents using Unicode UTF-8 encoding. The HTML document should include a meta tag with charset=utf-8 and be stored in UTF-8 format.

Let's play to some French characters in UTF-8 encoding first.

1\. On a Windows system, run Start > All Programs > Accessories > Notepad.

2\. In Notepad, enter the following HTML document:

```
<html>
<!-- HelpUtf8French.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<body>
<b>Help</b><br/>
English: System load is very high.<br/>
French: L'utilisation de système est très haute.<br/>
</body>
</html>
```

3\. To enter the French character, "e with grave", you can run Start > All Programs > System Tools > Character Map. Select "e with grave" on the character map. Click the Select button, then the Copy button. Go back to your Notepad and click Ctrl-V to paste "e with grave" into your HTML document.

4\. Select menu File > Save as. Enter the file name as HelpUtf8French.html. Select "UTF-8" in the Encoding field and click the Save button.

5\. Copy HelpUtf8French.html to c:\\apache\\htdocs. Make sure your Internet Information Service is running the local default Web site.

6\. Now run Internet Explorer (IE) with http://localhost/HelpUtf8French.html. Your should see the French characters displayed correctly as shown below:

```
Help
English: System load is very high.
French: L'utilisation de système est très haute.
```

7\. On the IE window, select menu View > Encoding. You should see UTF-8 is selected.

Note that how I specify the <meta> tag:

```
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
```

Another interesting thing you should know is about how Notepad stores a UTF-8 file. When you use UTF-8 encoding to store a file in Notepad, it will insert a UTF-8 marker (3 bytes) at the beginning of the file. Use the "type" command in a command window, you will see this:

```
herong> type HelpUtf8French.html

<html>
<!-- HelpUtf8French.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<body>
<b>Help</b><br/>
English: System load is very high.<br/>
French: L'utilisation de système est très haute.<br/>
</body>
</html>
```

The hex value of the UTF-8 marker is 0xEFBBBF. Web server will send it the client. IE browser will not show it on the page, but it will use it to detect the encoding schema, if needed. Not sure on how other browsers will behave on this marker.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters in HTML Documents](#part0164.xhtml)

∟French Characters in HTML Documents - ISO-8859-1 Encoding

This section provides a tutorial example on how enter and use French characters in HTML documents using Unicode ISO-8859-1 encoding. The HTML document should include a meta tag with charset=ISO-8859-1 and be stored in ANSI format.

Now we know how to make French characters working in a HTML document in UTF-8 encoding schema. Next let's see how to use French characters in HTML documents in ISO-8859-1 encoding schema.

1\. On a Windows system, run Start > All Programs > Accessories > Notepad.

2\. In Notepad, enter the following HTML document:

```
<html>
<!-- HelpIsoFrench.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<body>
<b>Help</b><br/>
English: System load is very high.<br/>
French: L'utilisation de système est très haute.<br/>
</body>
</html>
```

3\. To enter the French character, "e with grave", you can run Start > All Programs > System Tools > Character Map. Select "e with grave" on the character map. Click the Select button, then the Copy button. Go back to your Notepad and click Ctrl-V to paste "e with grave" into your HTML document.

4\. Select menu File > Save as. Enter the file name as HelpIsoFrench.html. Select "ANSI" in the Encoding field and click the Save button. Note that ANSI is encoding schema defined by Microsoft and used on Windows system. ANSI contains more characters than ISO-8859-1. But it is compatible with ISO-8859-1.

5\. Copy HelpIsoFrench.html to c:\\apache\\htdocs. Make sure your Internet Information Service is running the local default Web site.

6\. Now run Internet Explorer (IE) with http://localhost/HelpIsoFrench.html. Your should see the French characters displayed correctly as shown below:

```
Help
English: System load is very high.
French: L'utilisation de système est très haute.
```

7\. On the IE window, select menu View > Encoding. You should see "Western European" is selected. Again "Western European" is a different name for ISO-8859-1.

Easy to do, right? We could make it even easier. You can remove the <meta> tag setting in HelpIsoFrench.html. French characters will still show up on the IE window. This is because ISO-8859-1 is the default encoding schema to IE.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters in HTML Documents](#part0164.xhtml)

∟Chinese Characters in HTML Documents - UTF-8 Encoding

This section provides a tutorial example on how enter and use Chinese characters in HTML documents using Unicode UTF-8 encoding. The HTML document should include a meta tag with charset=utf-8 and be stored in UTF-8 format.

Now let's play with Chinese characters. They are definitely harder to work with than French characters. My first example shows you how to handle Chinese characters in HTML documents with UTF-8 encoding.

1\. On a Windows system, run Start > All Programs > Accessories > Notepad.

2\. In Notepad, enter the following HTML document:

```
<html>
<!-- HelpUtf8Chinese.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<body>
<b>说明</b><br/>
这是一份非常间单的说明书…<br/>
</body>
</html>
```

3\. As I mentioned earlier in this book, entering Chinese characters is not an easy job. You need to use a Chinese Windows system, or a Chinese input tool on a non-Chinese Windows system. If you don't have any Chinese input tool, you can simply go to the Yahoo Chinese Web site, http://www.yahoo.com.cn/, copy some Chinese characters, and paste them into Notepad. The Yahoo Chinese Web site is encoded in UTF-8.

4\. Select menu File > Save as. Enter the file name as HelpUtf8Chinese.html. Select "UTF-8" in the Encoding field and click the Save button.

5\. Copy HelpUtf8Chinese.html to c:\\apache\\htdocs. Make sure your Internet Information Service is running the local default Web site.

6\. Now run Internet Explorer (IE) with http://localhost/HelpUtf8Chinese.html. Your should see the Chinese characters displayed correctly.

7\. On the IE window, select menu View > Encoding. You should see UTF-8 is selected.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters in HTML Documents](#part0164.xhtml)

∟Chinese Characters in HTML Documents - GB2312 Encoding

This section provides a tutorial example on how enter and use Chinese characters in HTML documents using GB2312 encoding. The HTML document should include a meta tag with charset=GB2312 and be stored in GB2312 format.

We are ready to test Chinese characters in HTML documents with GB2312 encoding schema.

1\. This time, we can not use Notepad, because Notepad is not compatible with GB2312 encoding. It will actually convert GB2312 encoding to UTF-8 encoding. So don't use Notepad.

You need to go get another text editor, like Jext, to help you enter the Chinese characters in GB2312 encoding.

2\. In a good text editor, enter the following HTML document:

```
<html>
<!-- HelpGb2312Chinese.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=gb2312"/>
<body>
<b>??</b><br/>
????????????<br/>
</body>
</html>
```

When I copy this HTML document into this book, I have to replace all GB2312 encoded Chinese characters with "?"s, because my book is written in HTML document with UTF-8 encoding schema. To follow my tutorial, just enter any Chinese character whenever you see "?".

3\. Entering Chinese characters in GB2312 encoding also requires some Chinese input tools. If you don't have any Chinese input tool, you can simply go to my GB2312 page, https://www.herongyang.com/gb2312\_gb/, open the source code of the page, copy some Chinese characters, and paste them into the editor. My GB2312 page is encoded in GB2312. Warning, do not copy Chinese characters from the IE browser window. The browser window copy function is assuming UTF-8 encoding and will corrupt the copied characters.

4\. Select menu File > Save as. Enter the file name as HelpGb2312Chinese.html and click the Save button.

5\. Copy HelpGb2312Chinese.html to c:\\apache\\htdocs. Make sure your Internet Information Service is running the local default Web site.

6\. Now run Internet Explorer (IE) with http://localhost/HelpGb2312Chinese.html. Your should see the Chinese characters displayed correctly.

7\. On the IE window, select menu View > Encoding. You should see Gb2312 is selected.

Still not hard to do, right? The key point is to use an editor that compatible with GB2312.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters in HTML Documents](#part0164.xhtml)

∟Characters of Multiple Languages in HTML Documents

This section provides a tutorial example on how enter and use characters of multiple languages in a single HTML document with Unicode UTF-8 encoding.

After going through above examples, you should feel comfortable now on how to handle non-ASCII characters of any single language. You have a choice of using UTF-8 or a language specific encoding.

If you want to have characters of multiple languages in a single HTML document, then you have to use UTF-8 encoding. Here are the steps you can follow make a HTML document in UTF-8 to support multiple languages in a single HTML document.

1\. On a Windows system, run Start > All Programs > Accessories > Notepad.

2\. In Notepad, enter the following HTML document:

```
<html>
<!-- HelloUtf8MultiLanguages.html
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
-->
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
<body>
<b>Test</b><br/>
English: Hello world!<br/>
Spanish: ¡Hola mundo!<br/>
Korean: 여보세요 세계 !<br/>
Chinese: 你好世界!<br/>
</body>
</html>
```

3\. Don't try to enter those hello messages yourself. Go to the Google language tool site, [google.com/language\_tools](http://www.google.com/language_tools). You can enter "Hello world!" and translate it to other languages. On the translation output page, just copy those translations and paste them back to Notepad. This should cause no corruption, because Google site, Windows IE, and Notepad all support UTF-8.

4\. Select menu File > Save as. Enter the file name as HelloUtf8MultiLanguages.html. Select "UTF-8" in the Encoding field and click the Save button.

5\. Copy HelloUtf8MultiLanguages.html to c:\\apache\\htdocs. Make sure your Internet Information Service is running the local default Web site.

6\. Now run Internet Explorer (IE) with http://localhost/HelloUtf8MultiLanguages.html. Your should see all characters displayed correctly.

7\. On the IE window, select menu View > Encoding. You should see UTF-8 is selected.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Using Non-ASCII Characters as PHP Script String Literals

This chapter provides tutorial examples and notes about non-ASCII characters in PHP scripts. Topics include basic rules on using non-ASCII characters in PHP scripts as string literals; examples of using French characters with UTF-8 and ISO-8859-1 encodings; examples of using Chinese characters with UTF-8 and GB2312 encodings.

> [Basic Rules of Using Non-ASCII Characters in HTML Documents](#part0172.xhtml)
> 
> [French Characters in String Literals - UTF-8 Encoding](#part0173.xhtml)
> 
> [French Characters in HTML Documents - ISO-8859-1 Encoding](#part0174.xhtml)
> 
> [Chinese Characters in String Literals - UTF-8 Encoding](#part0175.xhtml)
> 
> [Chinese Characters in String Literals - GB2312 Encoding](#part0176.xhtml)
> 
> [Characters of Multiple Languages in String Literals](#part0177.xhtml)

Takeaways:

*   PHP string data type is defined as sequences of bytes.
*   PHP string literal can almost non ASCII characters in almost any encoding schema.
*   The best choice of encoding schema is UTF-8.
*   Using UTF-8 encoding in PHP scripts requires a good UTF-8 compatible editor.
*   PHP script generates HTML document using print() function, which is a byte stream output function, offers no encoding conversion by default.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters as PHP Script String Literals](#part0171.xhtml)

∟Basic Rules of Using Non-ASCII Characters in HTML Documents

This section describes basic rules on how non-ASCII character strings should be managed at different steps to ensure localized text strings can be used in PHP script string literals and displayed correctly on the browser window.

As you can see from the previous chapters, when PHP scripts are involved in a Web based application, they are always used behind a Web server. PHP scripts are expected to generate HTML documents and pass them back to the Web server. There are about four ways non ASCII characters can get into the HTML document through PHP scripts: a) Enter them as string literals; b) Receive them from HTTP request; c) Retrieve them from files; d) Retrieve them from a database.

In this chapter, we will concentrate on how to include non ASCII characters in PHP scripts as string literals. Here are the steps involved in this scenario:

```
A1. Key Sequences from keyboard
      |
      |- Text editor
      v
A2. PHP File
      |
      |- PHP CGI engine
      v
A3. HTML Document
```

Based on my experience, here are some basic rules related to those steps:

1\. You must decide on the character encoding schema to be used in your PHP script file. For most of the languages, you have two options, a: use a encoding schema specific to that language; b: use a Unicode schema. For example, you can use either GB2312 (a simplified Chinese character schema) or UTF-8 (a Unicode character schema) for Chinese characters. My suggestion used to be "a". But today, I am suggesting "b", because Unicode schema can support all characters of all languages.

2\. From step "A1" to "A2", you need select good text editor that supports the encoding schema you have decided. The end goal of this step is simple - characters in string literals must be stored in the PHP file using the decided encoding schema. Don't under estimate the difficulty level of this step. It could be very frustrating, because most computer keyboards support alphabetic letters only. You may have to use some language specific input software to translate alphabetic letters into language specific characters. The editor sometimes may also store characters in memory in one encoding schema, and offer you different encoding schema when saving files to hard disk.

3\. String data type is defined as a sequence of bytes in PHP, like C language. This is different than Java language, where string data type is defined as a sequence of Unicode characters. String literals in PHP are also taken as sequences of bytes. This is a nice feature. It allows us to enter non ASCII characters in almost any encoding schema.

4\. All PHP built-in string functions assume that strings are sequences of bytes. For example, strlen() returns the number of bytes of the given string, not the number of characters of a specific language. To manage strings as sequences of characters, we need to use Multibyte String functions, mb\_\*().

5\. From step "A2" to "A3", HTML documents are generated from PHP script mainly through the print() function. The print() function will nicely copy every bytes from the specified string to HTML documents. This guarantees that any non ASCII characters encoded in any encoding schema will be copied correctly to the HTML document. Again, this is different than JSP pages, where strings will be converted into bytes stream based a specified encoding schema, if you are using character based output stream functions.

6\. If you do want to convert from one encoding schema to another encoding schema during the print() function call, you can use mb\_output\_handler as the call back function on the output buffer: ob\_start("mb\_output\_handler").

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters as PHP Script String Literals](#part0171.xhtml)

∟French Characters in String Literals - UTF-8 Encoding

This section provides a tutorial example on how enter and use French characters PHP string literals using Unicode UTF-8 encoding. The PHP script file should be stored in UTF-8 format.

First, let's play to some French characters in UTF-8 encoding first.

1\. On a Windows system, run Start > All Programs > Accessories > Notepad.

2\. In Notepad, enter the following PHP script:

```
<?php
#  HelpUtf8French.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      ' content="text/html; charset=utf-8"/>');
   print('<body>');
   print('<b>Help</b><br/>');
   print('English: System load is very high.<br/>');
   print('French: L\'utilisation de système est très haute.<br/>');
   print('</body>');
   print('</html>');
?>
```

3\. To enter the French character, "e with grave", you can run Start > All Programs > System Tools > Character Map. Select "e with grave" on the character map. Click the Select button, then the Copy button. Go back to your Notepad and click Ctrl-V to paste "e with grave" into your PHP script.

4\. Select menu File > Save as. Enter the file name as HelpUtf8French.php. Select "UTF-8" in the Encoding field and click the Save button.

5\. Copy HelpUtf8French.php to c:\\apache\\htdocs. Make sure your Internet Information Service is running the local default Web site.

6\. Now run Internet Explorer (IE) with http://localhost/HelpUtf8French.php. Your should see the French characters displayed correctly as shown below:

```
Help
English: System load is very high.
French: L'utilisation de système est très haute.
```

7\. On the IE window, select menu View > Encoding. You should see UTF-8 is selected.

Another interesting thing you should know is about how Notepad stores a UTF-8 file. When you use UTF-8 encoding to store a file in Notepad, it will insert a UTF-8 marker (3 bytes) at the beginning of the file. Use the "type" command in a command window, you will see this:

```
>type HelpUtf8French.php

<?php
#  HelpUtf8French.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      ' content="text/html; charset=utf-8"/>');
   print('<body>');
   print('<b>Help</b><br/>');
   print('English: System load is very high.<br/>');
   print('French: L\'utilisation de système est très haute.<br/>');
   print('</body>');
   print('</html>');
?>
```

The hex value of the UTF-8 marker is 0xEFBBBF. Web server will send it the client. IE browser will not show it on the page, but it will use it to detect the encoding schema, if needed. Not sure on how other browsers will behave this marker.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters as PHP Script String Literals](#part0171.xhtml)

∟French Characters in HTML Documents - ISO-8859-1 Encoding

This section provides a tutorial example on how enter and use French characters PHP string literals using ISO-8859-1 encoding. The PHP script file should be stored in ANSI format.

Now we know how to make French characters working in a PHP string literal in UTF-8 encoding schema. Next let's see how to them working in ISO-8859-1 encoding schema.

1\. On a Windows system, run Start > All Programs > Accessories > Notepad.

2\. In Notepad, enter the following PHP script:

```
<?php
#  HelpIsoFrench.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      ' content="text/html; charset=iso-8859-1"/>');
   print('<body>');
   print('<b>Help</b><br/>');
   print('English: System load is very high.<br/>');
   print('French: L\'utilisation de système est très haute.<br/>');
   print('</body>');
   print('</html>');
?>
```

3\. To enter the French character, "e with grave", you can run Start > All Programs > System Tools > Character Map. Select "e with grave" on the character map. Click the Select button, then the Copy button. Go back to your Notepad and click Ctrl-V to paste "e with grave" into your PHP script.

4\. Select menu File > Save as. Enter the file name as HelpIsoFrench.php. Select "ANSI" in the Encoding field and click the Save button. Note that ANSI is encoding schema defined by Microsoft and used on Windows system. ANSI contains more characters than ISO-8859-1. But it is compatible with ISO-8859-1.

5\. Copy HelpIsoFrench.php to c:\\apache\\htdocs. Make sure your Internet Information Service is running the local default Web site.

6\. Now run Internet Explorer (IE) with http://localhost/HelpIsoFrench.php. Your should see the French characters displayed correctly as shown below:

```
Help
English: System load is very high.
French: L'utilisation de système est très haute.
```

7\. On the IE window, select menu View > Encoding. You should see "Western European" is selected. Again "Western European" is a different name for ISO-8859-1.

Easy to do, right? We could make it even easier. You can remove the <meta> tag setting in HelpIsoFrench.html. French characters will still show up on the IE window. This is because ISO-8859-1 is the default encoding schema to IE.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters as PHP Script String Literals](#part0171.xhtml)

∟Chinese Characters in String Literals - UTF-8 Encoding

This section provides a tutorial example on how enter and use Chinese characters PHP string literals using Unicode UTF-8 encoding. The PHP script file should be stored in UTF-8 format.

Now let's play with Chinese characters. They are definitely harder to work with than French characters. My first example shows you how to handle Chinese characters in PHP scripts with UTF-8 encoding.

1\. On a Windows system, run Start > All Programs > Accessories > Notepad.

2\. In Notepad, enter the following HTML document:

```
<?php
#  HelpUtf8Chinese.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      ' content="text/html; charset=utf-8"/>');
   print('<body>');
   print('<b>说明</b><br/>');
   print('这是一份非常间单的说明书…<br/>');
   print('</body>');
   print('</html>');
?>
```

3\. As I mentioned earlier in this book, entering Chinese characters is not an easy job. You need to use a Chinese Windows system, or a Chinese input tool on a non-Chinese Windows system. If you don't have any Chinese input tool, you can simply go to the Yahoo Chinese Web site, http://www.yahoo.com.cn/, copy some Chinese characters, and paste them into Notepad. The Yahoo Chinese Web site is encoded in UTF-8.

4\. Select menu File > Save as. Enter the file name as HelpUtf8Chinese.php. Select "UTF-8" in the Encoding field and click the Save button.

5\. Copy HelpUtf8Chinese.php to c:\\apache\\htdocs. Make sure your Internet Information Service is running the local default Web site.

6\. Now run Internet Explorer (IE) with http://localhost/HelpUtf8Chinese.php. Your should see the Chinese characters displayed correctly.

7\. On the IE window, select menu View > Encoding. You should see UTF-8 is selected.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters as PHP Script String Literals](#part0171.xhtml)

∟Chinese Characters in String Literals - GB2312 Encoding

This section provides a tutorial example on how enter and use Chinese characters PHP string literals using GB2312 encoding. The PHP script file should be stored in GB2312 format.

I think we are ready to test Chinese characters in PHP scripts with GB2312 encoding schema now.

1\. This time, we can not use Notepad, because Notepad is not compatible with GB2312 encoding. It will actually convert GB2312 encoding to UTF-8 encoding. So don't use Notepad.

You need to go get another text editor, like Jext, to help you enter the Chinese characters in GB2312 encoding.

2\. In a good text editor, enter the following HTML document:

```
<?php
#  HelpGb2312Chinese.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      'content="text/html; charset=gb2312"/>');
   print('<body>');
   print('<b>??</b><br/>');
   print("????????????<br/>");
   print('</body>');
   print('</html>');
?>
```

When I copy this HTML document into this book, I have to replace all GB2312 encoded Chinese characters with "?"s, because my book is written in HTML document with UTF-8 encoding schema. To follow my tutorial, just enter any Chinese character whenever you see "?".

3\. Entering Chinese characters in GB2312 encoding also requires some Chinese input tools. If you don't have any Chinese input tool, you can simply go to my GB2312 page, https://www.herongyang.com/gb2312\_gb/, open the source code of the page, copy some Chinese characters, and paste them into the editor. My GB2312 page is encoded in GB2312. Warning, do not copy Chinese characters from the IE browser window. The browser window copy function is assuming UTF-8 encoding and will corrupt the copied characters.

4\. Select menu File > Save as. Enter the file name as HelpGb2312Chinese.php and click the Save button.

5\. Copy HelpGb2312Chinese.php to c:\\apache\\htdocs. Make sure your Internet Information Service is running the local default Web site.

6\. Now run Internet Explorer (IE) with http://localhost/HelpGb2312Chinese.php. Your should see the Chinese characters displayed correctly.

7\. On the IE window, select menu View > Encoding. You should see Gb2312 is selected.

Still not hard to do, right? The key point is to use an editor that compatible with GB2312.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Using Non-ASCII Characters as PHP Script String Literals](#part0171.xhtml)

∟Characters of Multiple Languages in String Literals

This section provides a tutorial example on how enter and use characters of multiple languages in a single PHP script with Unicode UTF-8 encoding.

After going through the above examples, you should feel comfortable now on how to handle non-ASCII characters of any single language. You have a choice of using UTF-8 or a language specific encoding.

If you want to have characters of multiple languages in a single PHP script, then you have to use UTF-8 encoding. Here are the steps you can follow make a PHP script in UTF-8 for a number of languages.

1\. On a Windows system, run Start > All Programs > Accessories > Notepad.

2\. In Notepad, enter the following PHP script:

```
<?php
#  HelpUtf8MultiLanguages.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print('<html>');
   print('<meta http-equiv="Content-Type"'.
      ' content="text/html; charset=utf-8"/>');
   print('<body>');
   print('<b>Test</b><br/>');
   print('English: Hello world!<br/>');
   print('Spanish: ¡Hola mundo!<br/>');
   print('Korean: 여보세요 세계 !<br/>');
   print('Chinese: 你好世界!<br/>');
   print('</body>');
   print('</html>');
?>
```

3\. Don't try to enter those hello messages yourself. Go to the Google language tool site, [google.com/language\_tools](http://www.google.com/language_tools). You can enter "Hello world!" and translate it to other languages. On the translation output page, just copy those translations and paste them back to Notepad. This should cause no corruption, because Google site, Windows IE, and Notepad all support UTF-8.

4\. Select menu File > Save as. Enter the file name as HelloUtf8MultiLanguages.php. Select "UTF-8" in the Encoding field and click the Save button.

5\. Copy HelloUtf8MultiLanguages.php to c:\\apache\\htdocs. Make sure your Internet Information Service is running the local default Web site.

6\. Now run Internet Explorer (IE) with http://localhost/HelloUtf8MultiLanguages.php. Your should see all characters displayed correctly.

7\. On the IE window, select menu View > Encoding. You should see UTF-8 is selected.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Receiving Non-ASCII Characters from Input Forms

This chapter provides tutorial examples and notes about non-ASCII characters in Web forms. Topics include basic rules on receiving non-ASCII characters from Web input forms; examples of using the $\_REQUEST array to receive non-ASCII characters submitted with GET or POST method; examples of handling non-ASCII character submitted with UTF-8 and ISO-8859-1 encodings.

> [Basic Rules of Receiving Non-ASCII Characters from Input Forms](#part0179.xhtml)
> 
> [Receiving Non-ASCII Characters with GET Method](#part0180.xhtml)
> 
> [Receiving Non-ASCII Characters with POST Method](#part0181.xhtml)
> 
> [Receiving Non ASCII Characters in UTF-8 Encoding](#part0182.xhtml)
> 
> [Decoding HTML Entities](#part0183.xhtml)

Takeaways:

*   How non ASCII characters are recorded on a Web page depends on the "charset" setting of the page.
*   URL encoding is applied when input strings are transferred to the server.
*   PHP CGI module applies URL decoding when parsing input strings into $\_REQUEST.
*   My suggestion is to use "charset=utf-8" for your input pages. No need to worry about HTML entity conversion.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Receiving Non-ASCII Characters from Input Forms](#part0178.xhtml)

∟Basic Rules of Receiving Non-ASCII Characters from Input Forms

This section describes basic rules on how non-ASCII character strings should be managed at different steps to ensure localized text strings can be entered in HTML forms and received correctly by PHP scripts that process those forms.

As you see from the previous chapters, when PHP scripts are involved in a Web based application, they are always used behind a Web server. PHP scripts are expected to generate HTML documents and pass them back to the Web server. There are about four ways non ASCII characters can get into the HTML document through PHP scripts: a) Enter them as string literals; b) Receive from HTTP request; c) Retrieve them from files; d) Retrieve them from a database.

In this chapter, we will concentrate on how to handle non ASCII characters received in the HTTP request. Here are the steps involved in this scenario:

```
C1. Key sequences on keyboard
      |
      |- Language input tool (optional)
      v
C2. Byte sequences
      |
      |- Web browser
      v
C3: HTTP request
      |
      |- Internet TCP/IP Connection
      v
C4. HTTP request
      |
      |- Web server
      v
C5. CGI variables and input stream
      |
      |- PHP CGI interface
      v
C6. PHP built-in variable and input stream
```

Based on my experience, here are some basic rules related to those steps:

1\. Page encoding - Input strings entered in a HTML page will be encoded immediately based on the page's "charset" setting. For example, if the page has "charset=iso-8859-1", double-byte Unicode characters will be encoded as HTML entities in the form of "&#nnnnn;", where "nnnnn" represents the decimal value of the Unicode character code. For example, "&#20320;" is Unicode character encoded as a HTML entity.

If the page has "charset=utf-8", double-byte Unicode characters will be encoded as UTF-8 byte sequences. For example, "\\xE4\\xBD\\xA0" is a Unicode character encoded as a UTF-8 byte sequence.

2\. URL encoding - Web browser will then apply "x-www-form-urlencoded" to all input strings when sending them to the server as part of the HTTP request. URL encoding converts all non ASCII bytes in the form of "%xx", "xx" is the HEX value of the byte. URL encoding also converts special characters in the form of "%xx", with one exception for the space character " ". It will be converted to "+".

For example, if the page "charset=iso-8859-1", a Unicode character is entered into the page. It will be encoded immediately as a HTML entity, like "你". When sending it to the server, it will be encoded again as "%26%2320320%3B".

If the page has "charset=utf-8", the same Unicode character is entered into the page. It will be encoded immediately as a UTF-8 byte sequence, like '\\xE4\\xBD\\xA0". When sending it to the server, it will be encoded again as "%E4%BD%A0".

3\. From step "C3" to "C4", Internet will maintain the URL encoded input strings as is.

4\. From step "C4" to "C5", Web server will maintain the URL encoded input strings as is.

5\. From step "C5" to "C6", PHP CGI interface is doing something interesting for you:

*   $\_SERVER\['QUERY\_STRING'\] stores the URL encoded input strings as is, if input is submitted with the GET method.
*   If input is submitted with the POST method, the URL encoded input strings will be maintained in the input stream.
*   PHP parses input strings out of $\_SERVER\['QUERY\_STRING'\] or input stream into an array called $\_REQUEST. During this parsing process, URL decoding is applied. All input strings are converted back to how they are entered on the page.

6\. What do you want to do with the characters in the input data is your decision. You could output them back to the HTML document, or store them in a file. Of course, you can apply any conversion you want to.

In the sections below, I will show you some sample PHP scripts to validate those rules.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Receiving Non-ASCII Characters from Input Forms](#part0178.xhtml)

∟Receiving Non-ASCII Characters with GET Method

This section provides a tutorial example on how enter non-ASCII characters in HTML forms and receive them correctly with the GET method. The HTML form is using the iso-8859-1 encoding.

We know that there are two methods you can use to submit input data in a HTML form: GET and POST. Let's work with GET method first. I wrote the following PHP script to demonstrate how non ASCII characters are managed in the steps described in the previous section.

```
<?php
#  InputIsoGet.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
#- Promoting CGI values to local variables
   global $r_English, $r_Spanish, $r_Korean, $r_ChineseUtf8;
   global $r_ChineseGb2312;
   import_request_variables("GPC","r_");

#- Generating HTML document
   print("<html>");
   print('<meta http-equiv="Content-Type"'
      .' content="text/html; charset=iso-8859-1"/>');
   print("<body>\n");
   print("<form action=InputIsoGet.php method=get>");
   print("English ASCII: <input name=English"
      ." value='$r_English' size=16><br>\n");
   print("Spanish UTF-8: <input name=Spanish"
      ." value='$r_Spanish' size=16><br>\n");
   print("Korean UTF-8: <input name=Korean"
      ." value='$r_Korean' size=16><br>\n");
   print("Chinese UTF-8: <input name=ChineseUtf8"
      ." value='$r_ChineseUtf8' size=16><br>\n");
   print("Chinese GB2312: <input name=ChineseGb2312"
      ." value='$r_ChineseGb2312' size=16><br>\n");
   print("<input type=submit name=submit value=Submit>\n");
   print("</form>\n");

#- Outputing input strings back to HTML document
   print("<hr>");
   print("<pre>");
   foreach ($_GET as $k => $v) {
      print "$k = ($v)\n";
   }
   print("</pre>");
   print("</body>");
   print("</html>");

#- Dumping input strings to a file
   $file = fopen("\\temp\\InputIsoGet.txt", 'ab');
   $str = "------\n";
   fwrite($file, $str, strlen($str));
   if (array_key_exists('QUERY_STRING',$_SERVER)) {
      $str = $_SERVER['QUERY_STRING'];
   } else {
      $str = NULL;
   }
   fwrite($file, $str, strlen($str));

   $str = "------\n";
   fwrite($file, $str, strlen($str));
   foreach ($_REQUEST as $k => $v) {
      $str = "$k = ($v)\n";
      fwrite($file, $str, strlen($str));
   }
   fclose($file);
?>
```

Couple of notes for this script:

*   The "global" statement declares all variables in the global scope. I don't really need them to be in the global scope. But this statement also make those variables defined to avoid the "undefined variable" error message at run time.
*   import\_request\_variables() is a nice method to bring in all input strings in $\_GET, $\_POST, and $\_COOKIE as variables. This saves a lots of coding like this: "if (array\_key\_exists('English',$\_GET)) { $r\_English = $\_GET\['English'\]; } else { $r\_English = NULL;}"
*   I used the single quote "'" in "<input name=English value='$r\_English' ...>" to stop white spaces damaging the tag syntax. But I didn't do enough to escape "'". I will leave that to you.
*   I dumped all input strings to a file in a binary mode to see what we are really getting from the PHP CGI interface. "b" is used in fopen() to make sure file is open binary mode. fwrite() is used for output binary data. String length is given in fwrite() to stop the magic\_quotes\_runtime stripping slashes in the string.
*   iso-8859-1 is used as the HTML document encoding.

Now, move this script to your Web server. Open your IE to http://localhost/InputIsoGet.php. You should see a simple Web form.

Next, enter the following strings on the form:

```
English ASCII: Hello world!
Spanish UTF-8: ¡Hola mundo!
Korean UTF-8: 여보세요 세계 !
Chinese UTF-8: 你好世界!
Chinese GB2312: 你好世界!
```

Don't try to enter those hello messages in UTF-8 yourself. Go to the Google language tool site [google.com/language\_tools](http://www.google.com/language_tools). You can enter "Hello world!" and translate it to other languages. On the translation output page, just copy those translations and paste them back to this page. This should cause no corruption, because Google site, Windows IE, and Notepad all support UTF-8.

But for the "Chinese GB2312" field, you can enter the message in GB2312 compatible editor. Then copy and paste it to the Web form. Do not enter it directly on the Web form, IE will convert it to Unicode encoding without telling you.

When you are ready, click the submit button. You will see the form comes back with input strings maintained in the field. The input strings are also display below the form as:

```
English = (Hello world!)
Spanish = (¡Hola mundo!)
Korean = (여보세요 세계 !)
ChineseUtf8 = (你好世界!)
ChineseGb2312 = (????!)
submit = (Submit)
```

As you can see that the input strings return to the Web page appear to be matching values I entered on the form. But they do not match at all. If you view the source code of the page, you will see that HTML entity encoded strings are generated in the HTML document:

```
<html><meta http-equiv="Content-Type" content="text/html;
 charset=iso-8859-1"/><body>
<form action=InputIsoGet.php method=get>English ASCII:
 <input name=English value='Hello world!' size=16><br>
Spanish UTF-8: <input name=Spanish value='¡Hola mundo!' size=16><br>
Korean UTF-8: <input name=Korean value='&#50668;&#48372;&#49464;
 &#50836; &#49464;&#44228; !&#50668;&#48372;&#49464;&#50836;
 &#49464;&#44228; !' size=16><br>
Chinese UTF-8: <input name=ChineseUtf8 value='&#20320;&#22909;
 &#19990;&#30028;!' size=16><br>
Chinese GB2312: <input name=ChineseGb2312 value='????¡'
 size=16><br>
<input type=submit name=submit value=Submit>
</form>
<hr><pre>English = (Hello world!)
Spanish = (¡Hola mundo!)
Korean = (&#50668;&#48372;&#49464;&#50836; &#49464;&#44228; !&#50668;
 &#48372;&#49464;&#50836; &#49464;&#44228; !)
ChineseUtf8 = (&#20320;&#22909;&#19990;&#30028;!)
ChineseGb2312 = (????¡)
submit = (Submit)
</pre></body></html>
```

This matches well with the rule that form input strings are stored in $\_REQUEST in the decode format, for example, "&#20320;", where "20320" is the decimal value of Unicode character "\\u4F60".

If you open the dump file, \\temp\\InputIsoGet.txt, you will see how input strings are URL encoded in query string, and decoded in $\_REQUEST.

```
------
English=Hello+world%21&Spanish=%A1Hola+mundo%21&
Korean=%26%2350668%3B%26%2348372%3B%26%2349464%3B%26%2350836%3B
+%26%2349464%3B%26%2344228%3B+%21%26%2350668%3B%26%2348372%3B
%26%2349464%3B%26%2350836%3B+%26%2349464%3B%26%2344228%3B+%21&
ChineseUtf8=%26%2320320%3B%26%2322909%3B%26%2319990%3B
%26%2330028%3B%21&ChineseGb2312=%CA%C0%BD%E7%C4%E3%BA%C3%A3%A1
&submit=Submit
------
English = (Hello world!)
Spanish = (¡Hola mundo!)
Korean = (&#50668;&#48372;&#49464;&#50836;
&#49464;&#44228; !&#50668;&#48372;&#49464;
&#50836; &#49464;&#44228; !)
ChineseUtf8 = (&#20320;&#22909;&#19990;&#30028;!)
ChineseGb2312 = (????!)
submit = (Submit)
```

For example, the Chinese character entered as Unicode was recorded by the browser as "&#20320;". It was then URL encoded into "%26%2320320%3B" when submitted to the server. PHP CGI module recorded it in $\_SERVER\['QUERY\_STRING'\] without any changes. But it was decoded back to "&#20320;" when PHP CGI module copy it to $\_REQUEST.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Receiving Non-ASCII Characters from Input Forms](#part0178.xhtml)

∟Receiving Non-ASCII Characters with POST Method

This section provides a tutorial example on how enter non-ASCII characters in HTML forms and receive them correctly with the POST method. The HTML form is using the iso-8859-1 encoding.

To test the POST method, I wrote the following script, InputIsoPost.php:

```
<?php
#  InputIsoPost.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
#- Promoting CGI values to local variables
   global $r_English, $r_Spanish, $r_Korean, $r_ChineseUtf8;
   global $r_ChineseGb2312;
   import_request_variables("GPC","r_");

#- Generating HTML document
   print("<html>");
   print('<meta http-equiv="Content-Type"'
      .' content="text/html; charset=iso-8859-1"/>');
   print("<body>\n");
   print("<form action=InputIsoPost.php method=post>");
   print("English ASCII: <input name=English"
      ." value='$r_English' size=16><br>\n");
   print("Spanish UTF-8: <input name=Spanish"
      ." value='$r_Spanish' size=16><br>\n");
   print("Korean UTF-8: <input name=Korean"
      ." value='$r_Korean' size=16><br>\n");
   print("Chinese UTF-8: <input name=ChineseUtf8"
      ." value='$r_ChineseUtf8' size=16><br>\n");
   print("Chinese GB2312: <input name=ChineseGb2312"
      ." value='$r_ChineseGb2312' size=16><br>\n");
   print("<input type=submit name=submit value=Submit>\n");
   print("</form>\n");

#- Outputing input strings back to HTML document
   print("<hr>");
   print("<pre>");
   foreach ($_POST as $k => $v) {
      print "$k = ($v)\n";
   }
   print("</pre>");
   print("</body>");
   print("</html>");

#- Dumping input strings to a file
   $file = fopen("\\temp\\InputIsoPost.txt", 'ab');
   $str = "------\n";
   fwrite($file, $str, strlen($str));
   foreach ($_REQUEST as $k => $v) {
      $str = "$k = ($v)\n";
      fwrite($file, $str, strlen($str));
   }
   fclose($file);
?>
```

If you test this script with Internet Explorer, you will get the same result as InputIsoGet.php.

I was looking for a way to dump the input strings submitted by the POST method. But I could not find the right function to do this.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Receiving Non-ASCII Characters from Input Forms](#part0178.xhtml)

∟Receiving Non ASCII Characters in UTF-8 Encoding

This section provides a tutorial example on how enter non-ASCII characters in HTML forms and receive them correctly with the GET method. The HTML form is using the Unicode UTF-8 encoding.

In the previous scripts, "charset=iso-8859-1" is used for the input page. Now let's play with "charset=utf-8". Here is my sample script:

```
<?php
#  InputUtf8Get.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
#- Promoting CGI values to local variables
   global $r_English, $r_Spanish, $r_Korean, $r_ChineseUtf8;
   global $r_ChineseGb2312;
   import_request_variables("GPC","r_");

#- Generating HTML document
   print("<html>");
   print('<meta http-equiv="Content-Type"'
      .' content="text/html; charset=utf-8"/>');
   print("<body>\n");
   print("<form action=InputUtf8Get.php method=get>");
   print("English ASCII: <input name=English"
      ." value='$r_English' size=16><br>\n");
   print("Spanish UTF-8: <input name=Spanish"
      ." value='$r_Spanish' size=16><br>\n");
   print("Korean UTF-8: <input name=Korean"
      ." value='$r_Korean' size=16><br>\n");
   print("Chinese UTF-8: <input name=ChineseUtf8"
      ." value='$r_ChineseUtf8' size=16><br>\n");
   print("Chinese GB2312: <input name=ChineseGb2312"
      ." value='$r_ChineseGb2312' size=16><br>\n");
   print("<input type=submit name=submit value=Submit>\n");
   print("</form>\n");

#- Outputing input strings back to HTML document
   print("<hr>");
   print("<pre>");
   foreach ($_GET as $k => $v) {
      print "$k = ($v)\n";
   }
   print("</pre>");
   print("</body>");
   print("</html>");

#- Dumping input strings to a file
   $file = fopen("\\temp\\InputUtf8Get.txt", 'ab');
   $str = "------\n";
   fwrite($file, $str, strlen($str));
   if (array_key_exists('QUERY_STRING',$_SERVER)) {
      $str = $_SERVER['QUERY_STRING'];
   } else {
      $str = NULL;
   }
   fwrite($file, $str, strlen($str));

   $str = "------\n";
   fwrite($file, $str, strlen($str));
   foreach ($_REQUEST as $k => $v) {
      $str = "$k = ($v)\n";
      fwrite($file, $str, strlen($str));
   }
   fclose($file);
?>
```

If you enter the same input strings as in the previous tests:

```
English = (Hello world!)
Spanish = (¡Hola mundo!)
Korean = (여보세요 세계 !)
ChineseUtf8 = (你好世界!)
ChineseGb2312 = (????!)
submit = (Submit)
```

The page returned with the input strings displayed below the form. They look correct to me.

If you open the dump file, \\temp\\InputUtf8Get.txt, you will see how input strings are URL encoded in query string, and decoded in $\_REQUEST.

```
------
English=Hello+world%21&
Spanish=%C2%A1Hola+mundo%21&
Korean=%EC%97%AC%EB%B3%B4%EC%84%B8%EC%9A%94+%EC%84%B8%EA%B3%84+%21&
ChineseUtf8=%E4%BD%A0%E5%A5%BD%E4%B8%96%E7%95%8C%21&
ChineseGb2312=%C3%8A%C3%80%C2%BD%C3%A7%C3%84%C3%A3%C2%BA%C3%83%C2%A3
   %C2%A1
&submit=Submit------
------
English = (Hello world!)
Spanish = (¡Hola mundo!)
Korean = (여보세요 세계 !)
ChineseUtf8 = (你好世界!)
ChineseGb2312 = (????!)
submit = (Submit)
```

Again, the result matches the rules listed earlier in this chapter. Input strings are recorded as UTF-8 byte sequences when entered on the page. Then each byte is URL encoded as %xx when sending to the server. When input strings are parsed into $\_REQUEST, they are decoded back to UTF-8 byte sequences.

One surprise to me is that the GB2312 characters are also recorded as UTF-8 byte sequences.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Receiving Non-ASCII Characters from Input Forms](#part0178.xhtml)

∟Decoding HTML Entities

This section provides a tutorial example on how decode HTML entities received from HTML forms with iso-8859-1 encoding for non-ASCII characters.

As you see earlier in this chapter, if page has "charset=iso-8859-1", Unicode characters will be received as HTML entities in $\_REQUEST. How can we convert them back to Unicode characters?

I have tried with "urldecode()" and "rawurldecode()". They work fine on single-byte characters. But they do not work with multi-byte characters.

PHP has a special function "html\_entity\_decode()" to decode HTML entities with multi-byte characters. Here is the syntax of html\_entity\_decode():

```
   html_entity_decode(string[, quote_style[, charset]])
```

where "string" is the HTML entity encoded string; "quote\_style" specifies how quotes should be handled; and "charset" specifies which character set to use. Supported character sets include: ISO-8859-1, UTF-8, cp1251, GB2312, and Shift\_JIS.

To show you how to use html\_entity\_decode(), I modified InputIsoGet.php to InputIsoGetDecoded.php:

```
<?php
#  InputIsoGetDecoded.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
#- Promoting CGI values to local variables
   global $r_English, $r_Spanish, $r_Korean, $r_ChineseUtf8;
   global $r_ChineseGb2312;
   import_request_variables("GPC","r_");

#- Generating HTML document
   print("<html>");
   print('<meta http-equiv="Content-Type"'
      .' content="text/html; charset=utf-8"/>');
   print("<body>\n");
   print("<form action=InputIsoGetDecoded.php method=get>");
   print("English ASCII: <input name=English"
      ." value='$r_English' size=16><br>\n");
   print("Spanish UTF-8: <input name=Spanish"
      ." value='$r_Spanish' size=16><br>\n");
   print("Korean UTF-8: <input name=Korean"
      ." value='$r_Korean' size=16><br>\n");
   print("Chinese UTF-8: <input name=ChineseUtf8"
      ." value='$r_ChineseUtf8' size=16><br>\n");
   print("Chinese GB2312: <input name=ChineseGb2312"
      ." value='$r_ChineseGb2312' size=16><br>\n");
   print("<input type=submit name=submit value=Submit>\n");
   print("</form>\n");

#- Outputing input strings back to HTML document
   print("<hr>");
   print("<pre>");
   print("Input strings before decoding:\n");
   foreach ($_GET as $k => $v) {
      print "$k = ($v)\n";
   }
   print("</pre>");

#- Outputing input strings back to HTML document - decoded
   print("<hr>");
   print("<pre>");
   print("Input strings after decoding:\n");
   foreach ($_GET as $k => $v) {
      print("$k = (".html_entity_decode($v,ENT_COMPAT,"UTF-8").")\n");
   }
   print("</pre>");
   print("</body>");
   print("</html>");

#- Dumping input strings to a file
   $file = fopen("\\temp\\InputIsoGet.txt", 'ab');
   $str = "------\n";
   fwrite($file, $str, strlen($str));
   if (array_key_exists('QUERY_STRING',$_SERVER)) {
      $str = $_SERVER['QUERY_STRING'];
   } else {
      $str = NULL;
   }
   fwrite($file, $str, strlen($str));

   $str = "------\n";
   fwrite($file, $str, strlen($str));
   foreach ($_REQUEST as $k => $v) {
      $str = "$k = ($v)\n";
      fwrite($file, $str, strlen($str));
   }
   fclose($file);
?>
```

Now enter the following input strings on InputIsoGetDecoded.php to see what happens:

```
English ASCII: Hello world!
Spanish UTF-8: ¡Hola mundo!
Korean UTF-8: ???? ?? !
Chinese UTF-8: ????!
Chinese GB2312: ????¡
```

If you click the submit button, you will get:

```
Input strings before decoding:
English = (Hello world!)
Spanish = (¡Hola mundo!)
Korean = (???? ?? !)
ChineseUtf8 = (????!)
ChineseGb2312 = (????¡)
submit = (Submit)
------
Input strings after decoding:
English = (Hello world!)
Spanish = (¡Hola mundo!)
Korean = (여보세요 세계 !)
ChineseUtf8 = (仠好世界!)
ChineseGb2312 = (????¡)
submit = (Submit)
```

The first section shows you input strings as they are received in HTML entity encoding. The second section shows you input strings as they are decoded from HTML entity encoding to UTF-8 encoding.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟"mbstring" Extension and Non-ASCII Encoding Management

This chapter provides tutorial examples and notes about mbstring extension library and encoding management. Topics include introduction of mbstring extension library; tutorial example of using mbstring functions; using mb\_convert\_encoding() function; the best way to manage HTTP input and output encoding.

> ["mbstring" - Multi-Byte String Extension](#part0185.xhtml)
> 
> [mb\_convert\_encoding() and Other mbstring Functions](#part0186.xhtml)
> 
> [Examples of Using "mbstring" Functions](#part0187.xhtml)
> 
> [Managing HTTP Input and Output Encoding](#part0188.xhtml)

Takeaways:

*   "mbstring" is a very useful extension for to handle multi-byte character strings.
*   "mbstring" is also useful to convert strings to different encodings.
*   The best way to manage Web application encoding is to use UTF-8 for both page content encoding and PHP script internal encoding.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟["mbstring" Extension and Non-ASCII Encoding Management](#part0184.xhtml)

∟"mbstring" - Multi-Byte String Extension

This section describes the mbstring (multi-byte string) extension library designed to help you manipulate non-ASCII character strings encoded in various encoding schemas like Unicode UTF-8.

PHP offers a nice extension called "mbstring (multi-byte string)" to help you manage non-ASCII strings. Here are the features of "mbstring":

*   Provides multibyte specific string functions that properly detect the beginning or ending of a multibyte character. For example, mb\_strlen() and mb\_split().
*   Handles character encoding conversion between the possible encoding pairs.
*   Offers automatic encoding conversion for HTTP input and output.
*   Supports 'function overloading' feature which enables you to add multibyte awareness to regular string functions. For example, you can overload substr() with mb\_substr(), so that calling substr() is really calling mb\_substr().

"mbstring" extension needs to installed and configured by updating the php.ini file. To get started with "mbstring" features, I modified my php.ini as:

```
extension=php_mbstring.dll
...
mbstring.language = Neutral
mbstring.internal_encoding = UTF-8
mbstring.http_input = pass
mbstring.http_output = pass
mbstring.encoding_translation = Off
mbstring.detect_order = auto
```

Note that:

*   "mbstring.language = Neutral" is really setting the language to UTF-8. I like to work with Unicode UTF-8 encoding.
*   "mbstring.http\_input = pass" means no decoding when receiving HTTP input. I like to manage the decoding myself inside my PHP script.
*   "mbstring.http\_output = pass" means no encoding when generating HTTP output. I like to manage the encoding myself inside my PHP script.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟["mbstring" Extension and Non-ASCII Encoding Management](#part0184.xhtml)

∟mb\_convert\_encoding() and Other mbstring Functions

This section describes some basic functions provided in the mbstring extension library. mb\_strlen() returns the number of characters. mb\_convert\_encoding() converts a string to a new encoding schema.

Let's first look at some of the basic "mbstring" functions offered in the "mbstring" extension library:

mb\_get\_info ( ) - Returns the current settings of "mbstring" extension.

mb\_internal\_encoding ( \[string encoding\] ) - Sets the current internal encoding with the specified encoding name. If no encoding is specified, it returns the current internal encoding.

string mb\_strlen ( string str \[, string encoding\] ) - Returns the number of characters in the specified string based on the specified encoding name. If no encoding is specified, it uses the current internal encoding.

string mb\_convert\_encoding ( string str, string to\_encoding \[, mixed from\_encoding\] ) - Converts the specified string to a new encoding from an old encoding and returns the converted string. If no old encoding is specified, it uses the current internal encoding.

mb\_detect\_encoding ( string str ) - Detects and returns the encoding name of the specified string.

mb\_http\_input ( string type ) - Detects and returns the encoding name of the specified HTTP input type: "G" for GET, "P" for POST, "C" for COOKIE.

mb\_http\_output ( \[string encoding\] ) - Sets or returns the current HTTP output encoding.

mb\_output\_handler ( string contents, int status ) - Call back function for output buffer. When used as ob\_start("mb\_output\_handler"), all strings going to the output buffer will be converted from the internal encoding to the HTTP output encoding.

mb\_parse\_str ( string encoded\_string \[, array &result\] ) - Parses URL encoded strings, like the query string received with GET method. Resulting variables will be stored in the specified array. If no array is specified, resulting variables will be promoted into global variables.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟["mbstring" Extension and Non-ASCII Encoding Management](#part0184.xhtml)

∟Examples of Using "mbstring" Functions

This section provides a tutorial example of using mbstring functions, mb\_get\_info(), mb\_detect\_encoding(), mb\_strlen(), mb\_convert\_encoding(), etc.

I wrote the following script to test some of "mbstring" basic functions, MbStringBasic.php:

```
<?php
#  MbStringBasic.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   print("\nCurrent settings:\n");
   $settings = mb_get_info();
   foreach ($settings as $k => $v) {
      print "   $k = ($v)\n";
   }

   print("\nEncoding detection:\n");
   $str = "Hello!";
   $coding = mb_detect_encoding($str);
   print("1. ".$coding." for (\x".bin2hex($str).")\n");

   $str = "\x00H\x00e\x00l\x00l\x00o\x00!";
   $coding = mb_detect_encoding($str);
   print("2. ".$coding." for (\x".bin2hex($str).")\n");

   $str = "\xC2\xA1Hola!";
   $coding = mb_detect_encoding($str);
   print("3. ".$coding." for (\x".bin2hex($str).")\n");

   $str = "\xE4\xBD\xA0\xE5\xA5\xBD!";
   $coding = mb_detect_encoding($str);
   print("4. ".$coding." for (\x".bin2hex($str).")\n");

   $str = "\xC4\xE3\xBA\xC3\xA3\xA1";
   $coding = mb_detect_encoding($str);
   print("5. ".$coding." for (\x".bin2hex($str).")\n");

   print("\nString length:\n");
   $str = "Hello!";
   $length = mb_strlen($str, "ASCII");
   print("1. ".$length." for (\x".bin2hex($str).")\n");

   $str = "\x00H\x00e\x00l\x00l\x00o\x00!";
   $length = mb_strlen($str, "UTF-16");
   print("2. ".$length." for (\x".bin2hex($str).")\n");

   $str = "\xC2\xA1Hola!";
   $length = mb_strlen($str, "UTF-8");
   print("3. ".$length." for (\x".bin2hex($str).")\n");

   $str = "\xE4\xBD\xA0\xE5\xA5\xBD!";
   $length = mb_strlen($str, "UTF-8");
   print("4. ".$length." for (\x".bin2hex($str).")\n");

   $str = "\xC4\xE3\xBA\xC3\xA3\xA1";
   $length = mb_strlen($str, "GB2312");
   print("5. ".$length." for (\x".bin2hex($str).")\n");

   print("\nString conversion - ASCII <--> UTF-16:\n");
   $str = "Hello!";
   print("   String in ASCII = (\x".bin2hex($str).")\n");
   $str = mb_convert_encoding($str, "UTF-16", "ASCII");
   print("   Converted to UTF-16 = (\x".bin2hex($str).")\n");
   $str = mb_convert_encoding($str, "ASCII", "UTF-16");
   print("   Converted to ASCII = (\x".bin2hex($str).")\n");

   print("\nString conversion - UTF-8 <--> UTF-16:\n");
   $str = "\xC2\xA1Hola!";
   print("   String in UTF-8 = (\x".bin2hex($str).")\n");
   $str = mb_convert_encoding($str, "UTF-16", "UTF-8");
   print("   Converted to UTF-16 = (\x".bin2hex($str).")\n");
   $str = mb_convert_encoding($str, "UTF-8", "UTF-16");
   print("   Converted to UTF-8 = (\x".bin2hex($str).")\n");

   print("\nString conversion - UTF-8 <--> GB2312:\n");
   $str = "\xE4\xBD\xA0\xE5\xA5\xBD!";
   print("   String in UTF-8 = (\x".bin2hex($str).")\n");
   $str = mb_convert_encoding($str, "GB2312", "UTF-8");
   print("   Converted to GB2312 = (\x".bin2hex($str).")\n");
   $str = mb_convert_encoding($str, "UTF-8", "GB2312");
   print("   Converted to UTF-8 = (\x".bin2hex($str).")\n");

   print("\nString conversion - GB2312 <--> UTF-16:\n");
   $str = "\xC4\xE3\xBA\xC3\xA3\xA1";
   print("   String in GB2312 = (\x".bin2hex($str).")\n");
   $str = mb_convert_encoding($str, "UTF-16", "GB2312");
   print("   Converted to UTF-16 = (\x".bin2hex($str).")\n");
   $str = mb_convert_encoding($str, "GB2312", "UTF-16");
   print("   Converted to GB2312 = (\x".bin2hex($str).")\n");
?>
```

I you run it directly, you will get:

```
Current settings:
   internal_encoding = (UTF-8)
   http_input = ()
   http_output = (pass)
   func_overload = (pass)

Encoding detection:
1. ASCII for (\x48656c6c6f21)
2. ASCII for (\x00480065006c006c006f0021)
3. UTF-8 for (\xc2a1486f6c6121)
4. UTF-8 for (\xe4bda0e5a5bd21)
5. UTF-8 for (\xc4e3bac3a3a1)

String length:
1. 6 for (\x48656c6c6f21)
2. 6 for (\x00480065006c006c006f0021)
3. 6 for (\xc2a1486f6c6121)
4. 3 for (\xe4bda0e5a5bd21)
5. 3 for (\xc4e3bac3a3a1)

String conversion - ASCII <--> UTF-16:
   String in ASCII = (\x48656c6c6f21)
   Converted to UTF-16 = (\x00480065006c006c006f0021)
   Converted to ASCII = (\x48656c6c6f21)

String conversion - UTF-8 <--> UTF-16:
   String in UTF-8 = (\xc2a1486f6c6121)
   Converted to UTF-16 = (\x00a10048006f006c00610021)
   Converted to UTF-8 = (\xc2a1486f6c6121)

String conversion - UTF-8 <--> GB2312:
   String in UTF-8 = (\xe4bda0e5a5bd21)
   Converted to GB2312 = (\xc4e3bac321)
   Converted to UTF-8 = (\xe4bda0e5a5bd21)

String conversion - GB2312 <--> UTF-16:
   String in GB2312 = (\xc4e3bac3a3a1)
   Converted to UTF-16 = (\x4f60597dff01)
   Converted to GB2312 = (\xc4e3bac3a3a1)
```

Some interesting notes about this test:

*   I did set "mbstring.http\_input = pass", but "mb\_get\_info()" reported no setting. I don't know why.
*   Encoding detection #2 did not recognize the string "\\x00480065006c006c006f0021" as UTF-16 encoding.
*   Encoding detection #3 did not recognize the string "\\xc4e3bac3a3a1" as GB2312.
*   By telling "mbstring" the correct encoding name, mb\_strlen() worked perfectly.
*   Encoding conversion worked nicely too. I am actually surprised to see UTF-8 and GB2312 conversion working correctly.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟["mbstring" Extension and Non-ASCII Encoding Management](#part0184.xhtml)

∟Managing HTTP Input and Output Encoding

This section provides a tutorial example on how to manage HTTP input and output encoding in 3 different ways, using the same encoding input, output and internal storage, using different encodings and managing conversion manually, or using different encodings and managing conversion automatically.

There are 3 approaches on how to manage HTTP input and output encodings:

1\. Set HTTP input encoding, HTTP output encoding and PHP script internal encoding to be exactly the same, like UTF-8 or GB2312. I am strongly recommending this approach, since it avoids the need for conversion when receiving HTTP input and generating HTTP output.

2\. Set HTTP input encoding and HTTP output encoding to be the same, and PHP script internal encoding to be a different one. But do not let the PHP engine to do automated conversion on HTTP input and output. Let your PHP script manage it explicitly.

3\. Set HTTP input encoding and HTTP output encoding to be the same, and PHP script internal encoding to be a different one. But let the PHP engine do automated conversion on HTTP input and output.

For approach #1, you need turn off HTTP input and output encoding conversion by these php.ini settings:

```
mbstring.language = Neutral
mbstring.internal_encoding = UTF-8
mbstring.http_input = pass
mbstring.http_output = pass
mbstring.encoding_translation = Off
```

While writing your script, you must always remember that you are dealing with UTF-8 encoded strings.

Approach #2 is useful, if you want your Web page to be GB2312 encoded while using UTF-8 as your script internal encoding, and you want your script to control the HTTP input and output conversion process. Here are the php.ini settings:

```
mbstring.language = Neutral
mbstring.internal_encoding = UTF-8
mbstring.http_input = pass
mbstring.http_output = pass
mbstring.encoding_translation = Off
```

Approach #3 is useful, if you want your Web page to be UTF-8 encoded while using UTF-16 as your script internal encoding, and you trust the PHP engine to do HTTP input and output encoding conversion. Here are the php.ini settings:

```
mbstring.language = Neutral
mbstring.internal_encoding = UTF-8
mbstring.http_input = GB2312
mbstring.http_output = GB2312
mbstring.encoding_translation = On
```

Since approach #2 is more challenging than the others, I wrote the following script to give you some ideas:

```
<?php
#  MbStringHttp.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   mb_internal_encoding("UTF-8");

#- Taking care of HTTP input conversion
   $myRequest['English'] = "";
   $myRequest['ChineseUtf8'] = "";
   $myRequest['ChineseGb2312'] = "";
   foreach ($_REQUEST as $k => $v) {
      $myRequest[$k] = mb_convert_encoding($v,"UTF-8", "GB2312");
   }
   $r_English = $myRequest['English'];
   $r_ChineseUtf8 = $myRequest['ChineseUtf8'];
   $r_ChineseGb2312 = $myRequest['ChineseGb2312'];

#- Taking care of HTTP output conversion
   mb_http_output("GB2312");
   ob_start("mb_output_handler");

#- Generating HTML document
   print("<html>");
   print('<meta http-equiv="Content-Type"'
      .' content="text/html; charset=gb2312"/>');
   print("<body>\n");
   print("<form action=MbStringHttp.php method=get>");
   print("English ASCII: <input name=English"
      ." value='$r_English' size=16><br>\n");
   print("Chinese UTF-8: <input name=ChineseUtf8"
      ." value='$r_ChineseUtf8' size=16><br>\n");
   print("Chinese GB2312: <input name=ChineseGb2312"
      ." value='$r_ChineseGb2312' size=16><br>\n");
   print("<input type=submit name=submit value=Submit>\n");
   print("</form>\n");

#- Outputing input strings back to HTML document
   print("<hr>");
   print("<pre>");
   print("{$myRequest['English']}\n");
   print("{$myRequest['ChineseUtf8']}\n");
   print("{$myRequest['ChineseGb2312']}\n");
   print("</pre>");
   print("</body>");
   print("</html>");

#- Dumping input strings to a file
   $file = fopen("\\temp\\MbStringHttp.txt", 'ab');
   $str = "--- Query String ---\n";
   fwrite($file, $str, strlen($str));
   if (array_key_exists('QUERY_STRING',$_SERVER)) {
      $str = $_SERVER['QUERY_STRING'];
   } else {
      $str = NULL;
   }
   fwrite($file, $str, strlen($str));

   $str = "--- Raw reqeust input ---\n";
   fwrite($file, $str, strlen($str));
   foreach ($_REQUEST as $k => $v) {
      $str = "$k = ($v)\n";
      fwrite($file, $str, strlen($str));
   }

   $str = "--- Converted reqeust input ---\n";
   fwrite($file, $str, strlen($str));
   foreach ($myRequest as $k => $v) {
      $str = "$k = ($v)\n";
      fwrite($file, $str, strlen($str));
   }
   fclose($file);
?>
```

I tested this script with IE, and entered the following strings:

```
English ASCII: Hello world!
Spanish UTF-8: ¡Hola mundo!
Korean UTF-8: 여보세요 세계 !
Chinese UTF-8: 你好世界!
Chinese GB2312: ????¡
```

The returning page showed input strings correctly. But the source code was very interesting:

```
<html><meta http-equiv="Content-Type" content="text/html;
   charset=gb2312"/><body>
<form action=MbStringHttp.php method=get>
English ASCII: <input name=English value='Hello world!' size=16><br>
Spanish UTF-8: <input name=Spanish value='&iexcl;Hola mundo!'
   size=16><br>
Korean UTF-8: <input name=Korean value='&#50668;&#48372;&#49464;
   &#50836; &#49464;&#44228; !' size=16><br>
Chinese UTF-8: <input name=ChineseUtf8 value='ÄãºÃÊÀ½ç!' size=16><br>
Chinese GB2312: <input name=ChineseGb2312 value='&Ecirc;&Agrave;
   &frac12;&ccedil;&Auml;&atilde;&ordm;&Atilde;&pound;&iexcl;'
   size=16><br>
<input type=submit name=submit value=Submit>
</form>
<hr><pre>Hello world!
&iexcl;Hola mundo!
&#50668;&#48372;&#49464;&#50836; &#49464;&#44228; !
ÄãºÃÊÀ½ç!
&Ecirc;&Agrave;&frac12;&ccedil;&Auml;&atilde;&ordm;&Atilde;
   &pound;&iexcl;
</pre></body></html>
```

*   When the Web page has "charset=gb2312", some Unicode characters are recorded as HTML named entities, like "&iexcl;", and "&Ecirc;". Some Unicode characters are recorded as HTML numeric entities, like "&#50668;" and "&#48372;".
*   When Chinese characters in UTF-8 encoding are copied into the form, they are recorded as GB2312 encoding.
*   When Chinese characters in GB2312 encoding are copied into the form, they are recorded as HTML named entities. I don't know why.

I looked at the dump file, \\temp\\MbStringHttp.txt:

```
--- Query String ---
English=Hello+world%21&
Spanish=%26iexcl%3BHola+mundo%21&
Korean=%26%2350668%3B%26%2348372%3B%26%2349464%3B%26%2350836%3B+
   %26%2349464%3B%26%2344228%3B+%21&
ChineseUtf8=%C4%E3%BA%C3%CA%C0%BD%E7%21&
ChineseGb2312=%26Ecirc%3B%26Agrave%3B%26frac12%3B%26ccedil%3B
   %26Auml%3B%26atilde%3B%26ordm%3B%26Atilde%3B%26pound%3B%26iexcl%3B&
submit=Submit
--- Raw reqeust input ---
English = (Hello world!)
Spanish = (&iexcl;Hola mundo!)
Korean = (&#50668;&#48372;&#49464;&#50836; &#49464;&#44228; !)
ChineseUtf8 = (ÄãºÃÊÀ½ç!)
ChineseGb2312 = (&Ecirc;&Agrave;&frac12;&ccedil;&Auml;&atilde;&ordm;
   &Atilde;&pound;&iexcl;)
submit = (Submit)
--- Converted reqeust input ---
English = (Hello world!)
Spanish = (&iexcl;Hola mundo!)
Korean = (&#50668;&#48372;&#49464;&#50836; &#49464;&#44228; !)
ChineseUtf8 = (ä½ å¥½ä¸–ç•Œ!)
ChineseGb2312 = (&Ecirc;&Agrave;&frac12;&ccedil;&Auml;&atilde;&ordm;
   &Atilde;&pound;&iexcl;)
submit = (Submit)
```

My script handled HTTP input and output encoding correctly, if the input strings are recorded in GB2312 by the Web browser. For other characters recorded as HTML entities, you need to avoid them by telling your users to enter data correctly.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Managing Non-ASCII Character Strings with MySQL Servers

This chapter provides tutorial examples and notes about handling non-ASCII characters with MySQL server. Topics include storing non-ASCII characters in MySQL database with various character set encodings; managing encoding conversion when inserting data to and retrieving data from database; examples on using UTF-8 encoding.

> [Storing Non-ASCII Characters in Database](#part0190.xhtml)
> 
> [Transmitting Non-ASCII Characters with Database](#part0191.xhtml)
> 
> [MySqlUnicode.php - MySQL Unicode UTF-8 Encoding Example](#part0192.xhtml)

Takeaways:

*   MySQL provides a good support on non-ASCII characters. If offers a number of encodings (character sets).
*   MySQL allows us to specify encodings at database, table or column level.
*   MySQL allows us to control encoding conversions on receiving SQL statements and returning query results.
*   My recommendation is to use UTF-8 to all text information, turn off MySQL encoding conversion on receiving SQL statements and returning query results, and let your PHP script to handle UTF-8 strings.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing Non-ASCII Character Strings with MySQL Servers](#part0189.xhtml)

∟Storing Non-ASCII Characters in Database

This section describes how to store non-ASCII characters in MySQL database using different character set settings set column, table or database level.

MySQL can store non-ASCII characters in database in a number of encodings, MySQL call them character sets:

```
+----------+-----------------------------+
| Charset  | Description                 |
+----------+-----------------------------+
| big5     | Big5 Traditional Chinese    |
| dec8     | DEC West European           |
| cp850    | DOS West European           |
| hp8      | HP West European            |
| koi8r    | KOI8-R Relcom Russian       |
| latin1   | ISO 8859-1 West European    |
| latin2   | ISO 8859-2 Central European |
| swe7     | 7bit Swedish                |
| ascii    | US ASCII                    |
| ujis     | EUC-JP Japanese             |
| sjis     | Shift-JIS Japanese          |
| cp1251   | Windows Cyrillic            |
| hebrew   | ISO 8859-8 Hebrew           |
| tis620   | TIS620 Thai                 |
| euckr    | EUC-KR Korean               |
| koi8u    | KOI8-U Ukrainian            |
| gb2312   | GB2312 Simplified Chinese   |
| greek    | ISO 8859-7 Greek            |
| cp1250   | Windows Central European    |
| gbk      | GBK Simplified Chinese      |
| latin5   | ISO 8859-9 Turkish          |
| armscii8 | ARMSCII-8 Armenian          |
| utf8     | UTF-8 Unicode               |
| ucs2     | UCS-2 Unicode               |
| cp866    | DOS Russian                 |
| keybcs2  | DOS Kamenicky Czech-Slovak  |
| macce    | Mac Central European        |
| macroman | Mac West European           |
| cp852    | DOS Central European        |
| latin7   | ISO 8859-13 Baltic          |
| cp1256   | Windows Arabic              |
| cp1257   | Windows Baltic              |
| binary   | Binary pseudo charset       |
| geostd8  | GEOSTD8 Georgian            |
+----------+-----------------------------+
```

To store non-ASCII characters in a database column, you need to define that column with a specific character set. You can specify a character set at 3 levels: database, table, and column. For example:

```
   CREATE DATABASE db_name CHARACTER SET utf8
   CREATE TABLE tbl_name (...) CHARACTER SET utf8
   CREATE TABLE tbl_name (col_name CHAR(80) CHARACTER SET utf8, ...)
```

*   If a character set is specified at the database level, it is applied to all CHAR, VARCHAR, and TEXT columns of all tables in this database.
*   If a character set is specified at the table level, it is applied to all CHAR, VARCHAR, and TEXT columns in this table.
*   If a character set is specified at the column level, it is applied to this column only.
*   The column length specified in the table creation statement is counted at the character level, not at the encoding byte level.
*   If "utf8" is used on a CHAR(n) column, this column will require 3\*n bytes of storage.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing Non-ASCII Character Strings with MySQL Servers](#part0189.xhtml)

∟Transmitting Non-ASCII Characters with Database

This section describes some basic settings and rules on how to transmit non-ASCII characters from PHP scripts to MySQL database server, and from MySQL database server back to PHP scripts.

Handling non ASCII characters with MySQL not only requires us setting up the table columns with the correct encoding (character set), but also requires us setting up the correct encoding for transmitting characters to and from the database.

MySQL offers the following global variables to control the encodings used to transmit characters between the client (PHP script) and the server (MySQL database):

*   character\_set\_server - Character set used for all databases on the server.
*   character\_set\_database - Character set used for the default databases on the server.
*   character\_set\_client - Character set used by the client for all SQL statements.
*   character\_set\_connection - Character set that all SQL statements should be converted to by the server before executing them.
*   character\_set\_results - Character set that all returning result should be converted to by the server before sending it back to the client.

In most cases, you should make the client (PHP script) to use the same encoding (character set) as the server (MySQL server), so that there is no need to convert when transmitting characters between them.

Some times, you may need to use different encodings. For example, you want to use UTF-8 for your PHP scripts, while using GB2312 for your MySQL tables.

You can use two special SET commands to change those variables:

1\. "SET NAMES 'x'" is equivalent to these three statements:

```
   SET character_set_client = x;
   SET character_set_results = x;
   SET character_set_connection = x;
```

2\. "SET CHARACTER SET x" is equivalent to these three statements:

```
   SET character_set_client = x;
   SET character_set_results = x;
   SET collation_connection = @@collation_database;
```

You can always use the SHOW VARIABLES LIKE 'variable\_name' to view the current value of the given variable.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing Non-ASCII Character Strings with MySQL Servers](#part0189.xhtml)

∟MySqlUnicode.php - MySQL Unicode UTF-8 Encoding Example

This section provides a tutorial example on how to send and receive non-ASCII character strings in Unicode UTF-8 encoding to and from a MySQL database server.

My is my sample script to show you how to send UTF-8 strings to a MySQL server and store them in UTF-8 encoding, MySqlUnicode.php:

```
<?php
#  MySqlUnicode.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   $con = mysqli_connect('localhost', 'root', '');
   print "\nDefault settings...\n";
   $rs = mysqli_query($con,"SHOW VARIABLES LIKE 'character_set_%'");
   while ($row = mysqli_fetch_array($rs)) {
      print "    ".$row[0].'   '.$row[1]."\n";
   }

   print "\nUpdated settings...\n";
   $rs = mysqli_query($con,"SET NAMES 'utf8'");
   $rs = mysqli_query($con,"SHOW VARIABLES LIKE 'character_set_%'");
   while ($row = mysqli_fetch_array($rs)) {
      print "    ".$row[0].'   '.$row[1]."\n";
   }

   print "\nCreating a table in UTF-8...\n";
   $rs = mysqli_query($con,'DROP DATABASE MyBase');
   $rs = mysqli_query($con,'CREATE DATABASE MyBase CHARACTER SET utf8');
   $rs = mysqli_query($con,'USE MyBase');
   $rs = mysqli_query($con,'CREATE TABLE MyTable (ID INTEGER,'
      .' Message VARCHAR(80))');

   print "\nInserting some rows to the table...\n";
   $str = "Hello!";
   $rs = mysqli_query($con,"INSERT INTO MyTable VALUES ( 1, '$str')");
   $str = "\xC2\xA1Hola!";
   $rs = mysqli_query($con,"INSERT INTO MyTable VALUES ( 2, '$str')");
   $str = "\xE4\xBD\xA0\xE5\xA5\xBD!";
   $rs = mysqli_query($con,"INSERT INTO MyTable VALUES ( 3, '$str')");

   print "\nQuery some rows from the table...\n";
   $rs = mysqli_query($con,'SELECT * FROM MyTable WHERE ID < 10');
   print "   ".mysqli_field_name($rs,0)."   "
      .mysqli_field_name($rs,1)."\n";
   while ($row = mysqli_fetch_array($rs)) {
      print "    ".$row[0].'   '.$row[1]."=(\x".bin2hex($row[1]).")\n";
   }
   mysqli_free_result($rs);
   mysqli_close($con);

function mysqli_field_name($result, $field_offset) {
   $properties = mysqli_fetch_field_direct($result, $field_offset);
   return is_object($properties) ? $properties->name : null;
}
?>
```

If you run it, you will get:

```
Default settings...
    character_set_client   latin1
    character_set_connection   latin1
    character_set_database   latin1
    character_set_results   latin1
    character_set_server   latin1
    character_set_system   utf8
    character_sets_dir   C:\MySQL\share\charsets/

Updated settings...
    character_set_client   utf8
    character_set_connection   utf8
    character_set_database   latin1
    character_set_results   utf8
    character_set_server   latin1
    character_set_system   utf8
    character_sets_dir   C:\MySQL\share\charsets/

Creating a table in UTF-8...

Inserting some rows to the table...

Query some rows from the table...
   ID   Message
    1   Hello!=(\x48656c6c6f21)
    2   -íHola!=(\xc2a1486f6c6121)
    3   S+ásÑ+!=(\xe4bda0e5a5bd21)
```

MySQL works as expected, no conversion on the SQL statements, storing strings in UTF-8, and no conversion on query result.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Parsing and Managing HTML Documents

This chapter provides tutorial examples and notes on handling HTML documents. Topics include understanding DOM Extension; parsing HTML document string; building new HTML documents.

> [DOM Extension for HTML Documents](#part0194.xhtml)
> 
> [Parse and Traverse HTML Documents](#part0195.xhtml)
> 
> [Build New HTML Documents](#part0196.xhtml)
> 
> [Load HTML Documents with LIBXML\_NOBLANKS](#part0197.xhtml)
> 
> [Remove Whitespaces in HTML Documents](#part0198.xhtml)
> 
> [DOCTYPE Element in HTML Documents](#part0199.xhtml)
> 
> [Remove Dummy Elements in HTML Documents](#part0200.xhtml)
> 
> [Install DOM Extension on CentOS](#part0201.xhtml)

Takeaways:

*   DOM Extension can be used to parse and manage HTML documents.
*   DOMDocument class represents an HTML document as a "DOMNode" object tree.
*   "$doc->loadHTML($html)" parses an HTML document string into a DOMDocument object.
*   "$doc->saveHTML()" dumps a DOMDocument object into an HTML document string.
*   "sudo dnf install php-xml" installs the DOM Extension on CentOS systems.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Parsing and Managing HTML Documents](#part0193.xhtml)

∟DOM Extension for HTML Documents

This section provides a tutorial example on how to setup your local Windows system to use IIS (Internet Information Services) as a SMTP mail server.

**What Is DOM Extension?** - The DOM extension allows you to operate on XML or HTML documents through the DOM (Document Object Model) API with PHP.

Here is list of some DOM classes and methods.

*   $doc = new DOMDocument(): Creates an new and empty DOM object.
*   $doc->loadHTML($html): Parses an HTML document from the given string into this DOM object.
*   $node = $doc: Uses a DOMDocument object as a DOMNode object.
*   $node->nodeName: Is the name of the node: element name, attribute name, #document, #text, or #comment.
*   $node->nodeValue: Is the concatenation of all text contents in the node.
*   $node->nodeType: Is the node type code.
*   $node->attributes: Is a list of nodes representing attributes of the node.
*   $node->childNodes: Is a list of nodes representing child nodes of the node.
*   $element = $doc->createElement(): Creates a new DOMElement object.
*   $text = $doc->createTextNode(): Creates a new DOMText object.
*   $node->appendChild(): Inserts a child node into the current node.
*   $element->setAttribute(): Adds new attribute into an element.
*   $doc->saveHTML(): Dumps this DOMDocument object into an HTML document string.
*   $element->getElementsByTagName(): Returns a DOMNodeList object representing all descendant child elements that match the given tag name.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Parsing and Managing HTML Documents](#part0193.xhtml)

∟Parse and Traverse HTML Documents

This section provides a tutorial example on how to parse an HTML document into a DOMDocument object and traverse it as a DOMNode object tree.

If you have an existing HTML document, you can use the DOMDocument::loadHTML() method to parse in into a DOMDocument object.

A DOMDocument object is also a DOMNode object, which presents attributes and child elements as child DOMNode objects to form a DOMNode object tree.

If you want to traverse the DOMNode object tree, you can use the following API properties and methods:

*   $doc = new DOMDocument(): Creates an new and empty DOM object.
*   $doc->loadHTML($html): Parses an HTML document from the given string into this DOM object.
*   $node = $doc: Uses a DOMDocument object as a DOMNode object.
*   $node->nodeName: Is the name of the node: element name, attribute name, #document, #text, or #comment.
*   $node->nodeValue: Is the concatenation of all text contents in the node.
*   $node->nodeType: Is the node type code.
*   $node->attributes: Is a list of nodes representing attributes of the node.
*   $node->childNodes: Is a list of nodes representing child nodes of the node.

Here is a PHP script example, Traverse-HTML-DOM-Tree.php, that prints out information of all elements and their attributes in a given HTML document.

```
<?php
#  Traverses-HTML-DOM-Tree.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $file = $argv[1];
  $html = file_get_contents($file);

  $doc = new DOMDocument();
  $doc->loadHTML($html);
  printNode($doc, "");

function printNode($node, $prefix) {
  $attriLen = -1;
  $attriList = $node->attributes;
  if (isset($attriList)) $attriLen = $attriList->length;

  $childLen = -1;
  $childList = $node->childNodes;
  if (isset($childList)) $childLen = $childList->length;

  print($prefix . $node->nodeName . "= "
    . $attriLen . ", " . $childLen . ", " . $node->nodeType) . " ";
  if ($node->nodeType==XML_TEXT_NODE)
    print("text: (" . $node->nodeValue . ")\n");
  else if ($node->nodeType==XML_ATTRIBUTE_NODE)
    print("attribute: (" . $node->nodeValue . ")\n");
  else
    print("other: (...)\n");

  if (isset($attriList)) foreach ($attriList as $n)
    printNode($n, $prefix." @");
  if (isset($childList)) foreach ($childList as $n)
    printNode($n, $prefix." ");
}
?>
```

Here is an XHTML document example, XHTML-Example.html, which is also an HTML document.

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
   "DTD/xhtml1-strict.dtd">
<!-- XHTML-Example.html
 - Copyright (c) 2009 HerongYang.com. All Rights Reserved.
-->
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Strict DTD XHTML Example </title>
</head>
<body>
<p>Please Choose a Day:<br/><br/>
<select name="day">
  <option selected="selected">Monday</option>
  <option>Tuesday</option>
  <option>Wednesday</option>
</select>
</p>
</body>
</html>
```

Now run the PHP script on the HTML document file. You should see the following output.

```
herong> php Traverses-HTML-DOM-Tree.php XHTML-Example.html

#document= -1, 4, 13 other: (...)
 html= -1, -1, 10 other: (...)
 xml= -1, -1, 7 other: (...)
 #comment= -1, -1, 8 other: (...)
 html= 3, 5, 1 other: (...)
  @xmlns= -1, 1, 2 attribute: (http://www.w3.org/1999/xhtml)
  @ #text= -1, -1, 3 text: (http://www.w3.org/1999/xhtml)
  @xml:lang= -1, 1, 2 attribute: (en)
  @ #text= -1, -1, 3 text: (en)
  @lang= -1, 1, 2 attribute: (en)
  @ #text= -1, -1, 3 text: (en)
  #text= -1, -1, 3 text: (
)
  head= 0, 3, 1 other: (...)
   #text= -1, -1, 3 text: (
)
   title= 0, 1, 1 other: (...)
    #text= -1, -1, 3 text: (Strict DTD XHTML Example )
   #text= -1, -1, 3 text: (
)
  #text= -1, -1, 3 text: (
)
  body= 0, 3, 1 other: (...)
   #text= -1, -1, 3 text: (
)
   p= 0, 6, 1 other: (...)
    #text= -1, -1, 3 text: (Please Choose a Day:)
    br= 0, 0, 1 other: (...)
    br= 0, 0, 1 other: (...)
    #text= -1, -1, 3 text: (
)
    select= 1, 7, 1 other: (...)
     @name= -1, 1, 2 attribute: (day)
     @ #text= -1, -1, 3 text: (day)
     #text= -1, -1, 3 text: (
  )
     option= 1, 1, 1 other: (...)
      @selected= -1, 1, 2 attribute: (selected)
      @ #text= -1, -1, 3 text: (selected)
      #text= -1, -1, 3 text: (Monday)
     #text= -1, -1, 3 text: (
  )
     option= 0, 1, 1 other: (...)
      #text= -1, -1, 3 text: (Tuesday)
     #text= -1, -1, 3 text: (
  )
     option= 0, 1, 1 other: (...)
      #text= -1, -1, 3 text: (Wednesday)
     #text= -1, -1, 3 text: (
)
    #text= -1, -1, 3 text: (
)
   #text= -1, -1, 3 text: (
)
  #text= -1, -1, 3 text: (
)
```

The output gives us a clear picture of how an HTML document is represented as a DOMNode object tree.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Parsing and Managing HTML Documents](#part0193.xhtml)

∟Build New HTML Documents

This section provides a tutorial example on how to create an HTML document using methods provided from the DOM extension.

DOMDocument objects can also be created from scratch instead of parsing an HTML document text string. This can be easily done by using the following methods:

*   $doc = new DOMDocument(): Creates an new and empty DOM object.
*   $element = $doc->createElement(): Creates a new DOMElement object.
*   $text = $doc->createTextNode(): Creates a new DOMText object.
*   $node->appendChild(): Inserts a child node into the current node.
*   $element->setAttribute(): Adds new attribute into an element.
*   $doc->saveHTML(): Dumps this DOMDocument object an HTML document string.

The following program shows how to create a simple HTML document with these methods:

```
<?php
#  Create-HTML-DOM-Document.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $file = $argv[1];

  $doc = new DOMDocument();
  createHTML($doc);
  $html = $doc->saveHTML();
  file_put_contents($file, $html);

function createHTML($doc) {

  $doc->appendChild($html);

  $body = $doc->createElement("body");
  $html->appendChild($body);

  $p = $doc->createElement("p");
  $body->appendChild($p);

  $text = $doc->createTextNode("Hello World!");
  $p->appendChild($text);

  $body->setAttribute("bgcolor", "#ddddff");
}
?>
```

Now run the PHP script. You should get a simple HTML document as shown below.

```
herong> php Create-HTML-DOM-Document.php Hello.html

herong> type Hello.html
<html><body bgcolor="#ddddff"><p>Hello World!</p></body></html>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Parsing and Managing HTML Documents](#part0193.xhtml)

∟Load HTML Documents with LIBXML\_NOBLANKS

This section provides a tutorial example on how to load HTML documents with the LIBXML\_NOBLANKS using the PHP DOM Extension. It only removes whitespaces between tags inside the 'head' element.

In HTML documents, whitespace (any sequence of space, tab, carriage return and line feed) is largely ignored. To be precise, whitespace in between words is treated as a single character, and whitespace before and after element tags is ignored.

Whitespace is usually inserted into an HTML document to make it into a readable format. Here is an example of HTML document formatted with whitespaces, Hello-Formatted.html:

```
<html>
  <head>
    <title>
      Hello
    </title>
  </head>
  <body bgcolor="#ddddff">
    <p>
      Hello World!
    </p>
  </body>
</html>
```

To save storage space, you may want to remove whitespaces, also called blanks from a formatted HTML document.

According to the DOM Extension documentation, the LIBXML\_NOBLANKS option on the loadHTML() method can be used to remove blank nodes.

Here is my test script, Load-HTML-with-NOBLANKS.php:

```
<?php
#  Load-HTML-with-NOBLANKS.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $input = $argv[1];
  $option = $argv[2];
  $html = file_get_contents($input);
  $doc = new DOMDocument();

  if ($option=="noblanks") {
    $doc->loadHTML($html, LIBXML_NOBLANKS);
  } else {
    $doc->loadHTML($html);
  }

  print("\n------ HTML Document ------\n");
  print($doc->saveHTML());

  print("\n------ DOMNode Tree ------\n");
  printNode($doc, "");

function printNode($node, $prefix) {
  $attriLen = -1;
  $attriList = $node->attributes;
  if (isset($attriList)) $attriLen = $attriList->length;

  $childLen = -1;
  $childList = $node->childNodes;
  if (isset($childList)) $childLen = $childList->length;

  print($prefix . $node->nodeName . "= "
    . $attriLen . ", " . $childLen . ", " . $node->nodeType) . " ";
  if ($node->nodeType==XML_TEXT_NODE)
    print("text: (" . $node->nodeValue . ")\n");
  else if ($node->nodeType==XML_ATTRIBUTE_NODE)
    print("attribute: (" . $node->nodeValue . ")\n");
  else
    print("other: (...)\n");

  if (isset($attriList)) foreach ($attriList as $n)
    printNode($n, $prefix." @");
  if (isset($childList)) foreach ($childList as $n)
    printNode($n, $prefix." ");
}
?>
```

**Test 1** - Run the script without LIBXML\_NOBLANKS to see all blank nodes:

```
herong> php Load-HTML-with-NOBLANKS.php Hello-Formatted.html default

------ HTML Document ------
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN" ...>
<html>
  <head>
    <title>
      Hello
    </title>
  </head>
  <body bgcolor="#ddddff">
    <p>
      Hello World!
    </p>
  </body>
</html>

------ DOMNode Tree ------
#document= -1, 2, 13 other: (...)
 html= -1, -1, 10 other: (...)
 html= 0, 5, 1 other: (...)
  #text= -1, -1, 3 text: (
  )
  head= 0, 3, 1 other: (...)
   #text= -1, -1, 3 text: (
    )
   title= 0, 1, 1 other: (...)
    #text= -1, -1, 3 text: (
      Hello
    )
   #text= -1, -1, 3 text: (
  )
  #text= -1, -1, 3 text: (
  )
  body= 1, 3, 1 other: (...)
   @bgcolor= -1, 1, 2 attribute: (#ddddff)
   @ #text= -1, -1, 3 text: (#ddddff)
   #text= -1, -1, 3 text: (
    )
   p= 0, 1, 1 other: (...)
    #text= -1, -1, 3 text: (
      Hello World!
    )
   #text= -1, -1, 3 text: (
  )
  #text= -1, -1, 3 text: (
)
```

As you see from the output, the default behavior of loadHTML() preserves all whitespaces as "#text" nodes.

**Test 2** - Run the script with LIBXML\_NOBLANKS to see which blank nodes are removed.

```
herong> php Load-HTML-with-NOBLANKS.php Hello-Formatted.html noblanks

------ HTML Document ------
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN" ...>
<html><head><title>
      Hello
    </title></head><body bgcolor="#ddddff">
    <p>
      Hello World!
    </p>
  </body></html>

------ DOMNode Tree ------
#document= -1, 2, 13 other: (...)
 html= -1, -1, 10 other: (...)
 html= 0, 2, 1 other: (...)
  head= 0, 1, 1 other: (...)
   title= 0, 1, 1 other: (...)
    #text= -1, -1, 3 text: (
      Hello
    )
  body= 1, 3, 1 other: (...)
   @bgcolor= -1, 1, 2 attribute: (#ddddff)
   @ #text= -1, -1, 3 text: (#ddddff)
   #text= -1, -1, 3 text: (
    )
   p= 0, 1, 1 other: (...)
    #text= -1, -1, 3 text: (
      Hello World!
    )
   #text= -1, -1, 3 text: (
  )
```

The output shows some interesting surprises to me:

*   LIBXML\_NOBLANKS option removes blank nodes between tags inside <head>. For example spaces and line breaks between <head> and <title> are removed as a blank node.
*   LIBXML\_NOBLANKS option does not remove any blank nodes between tags inside <body>. For example spaces and line breaks between <head> and <title> are removed as a blank node.

I think that LIBXML\_NOBLANKS option is trying to preserve whitespaces inside <body>, because they do have meanings in HTML documents. This is different than XML documents.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Parsing and Managing HTML Documents](#part0193.xhtml)

∟Remove Whitespaces in HTML Documents

This section provides a tutorial example on how to remove whitespaces in HTML Documents with PHP DOM Extension.

If you write your HTML documents following XML syntax rules, you can write a PHP script to remove whitespaces in both <head> and <body> elements.

Here is my version, Remove-Whitespaces-in-HTML.php;

```
<?php
#  Remove-Whitespaces-in-HTML.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $input = $argv[1];
  $html = file_get_contents($input);
  $doc = new DOMDocument();

  $doc->loadHTML($html);
  removeBlanks($doc);
  print($doc->saveHTML());

function removeBlanks($node) {
  $junks = array();
  $oldList = array();
  $newList = array();

  $childList = $node->childNodes;
  if (isset($childList)) foreach ($childList as $n) {
    if ($n->nodeType==XML_TEXT_NODE) {
      $t = $n->nodeValue;
      $t = trim($t);
      if (strlen($t)==0) {

        # not safe to touch $node while looping its $childList
        # $node->removeChild($n);
        array_push($junks, $n);
      } else {
        $nn = $node->ownerDocument->createTextNode($t);

        # not safe to touch $node while looping its $childList
        # $node->replaceChild($nn, $n);
        array_push($oldList, $n);
        array_push($newList, $nn);
      }
    } else {
      removeBlanks($n);
    }
  }

  foreach($junks as $n) $node->removeChild($n);

  for ($i=0; $i<count($oldList); $i++)
    $node->replaceChild($newList[$i], $oldList[$i]);
}
?>
```

Note that it is not safe to touch a DOMNode object while looping its child list. The child list is forced to rebuild whenever its parent node is touched.

This is why we should not call removeChild() and replaceChild() in the first loop. We need to cache those changes and get them done after the first loop is completed.

Try it out on the Hello-Formatted.html file:

```
herong> type Hello-Formatted.html

<html>
  <head>
    <title>
      Hello
    </title>
  </head>
  <body bgcolor="#ddddff">
    <p>
      Hello World!
    </p>
  </body>
</html>

herong$> php Remove-Whitespaces-in-HTML.php Hello-Formatted.html

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN" ...>
<html><head><title>Hello</title></head><body bgcolor="#ddddff">\
<p>Hello World!</p></body></html>
```

Cool. All whitespaces are removed from the HTML document!

Remove all whitespaces in an HTML document is fine if it's perfectly written in XML style and has no <pre> elements.

But for most HTML documents, whitespaces do have meanings:

*   Whitespaces between inline elements are considered as part of the text content of their parent element.
*   Leading and trailing whitespaces of the text content of <pre> elements must be preserved and displayed.

So, do not use this script on any real HTML documents.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Parsing and Managing HTML Documents](#part0193.xhtml)

∟DOCTYPE Element in HTML Documents

This section provides a quick introduction on the DOCTYPE elements in HTML documents.

According to the HTML specification, every HTML document should have a "DOCTYPE" element located before the "html" element. The "DOCTYPE" element is used to specify which DTD (Document Type Definition) schema this HTML document follows.

For example, the following HTML document example, HTML-Exsmples.html, uses a "DOCTYPE" element to specify HTML 4.0 Loose DTD schema:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN"
 "http://www.w3.org/TR/REC-html40/loose.dtd">
<html><body bgcolor="#ddddff"><p>Hello World!</p></body></html>
```

If you dump the DOMNode object tree, you should see the "DOCTYPE" element is represented as the first child node of the HTML document.

```
herong> php Traverses-HTML-DOM-Tree.php HTML-Example.html

#document= -1, 2, 13 other: (...)
 html= -1, -1, 10 other: (...)
 html= 0, 1, 1 other: (...)
  body= 1, 1, 1 other: (...)
   @bgcolor= -1, 1, 2 attribute: (#ddddff)
   @ #text= -1, -1, 3 text: (#ddddff)
   p= 0, 1, 1 other: (...)
    #text= -1, -1, 3 text: (Hello World!)
```

As you can see from the output:

*   The first line "#document= -1, 2, 13 other: (...)" represents the entire HTML document.
*   The second line "html= -1, -1, 10 other: (...)" represents the the "DOCTYPE" element.
*   The third line "html= 0, 1, 1 other: (...)" represents the "html" element.

By the way, the loadHTML() will automatically add a default "DOCTYPE" element into the DOMNode object tree, if the original HTML document string does not have the "DOCTYPE" element. See the example below:

```
herong> type Hello-Formatted.html

<html>
  <head>
    <title>
      Hello
    </title>
  </head>
  <body bgcolor="#ddddff">
    <p>
      Hello World!
    </p>
  </body>
</html>

herong$> php Remove-Whitespaces-in-HTML.php Hello-Formatted.html

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN" ...>
<html><head><title>Hello</title></head><body bgcolor="#ddddff">\
<p>Hello World!</p></body></html>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Parsing and Managing HTML Documents](#part0193.xhtml)

∟Remove Dummy Elements in HTML Documents

This section provides a tutorial example on how to remove dummy elements in HTML documents, including empty elements, elements with whitespaces only, and redundant whitespaces.

In some HTML documents, especially generated by HTML editors, you may see many dummy (unnecessary or redundant) elements as listed below:

1\. Sequences of multiple wightspace characters generated by mistakes. For example, <p> Hello world! </p>. We can replace with a single space. But we need to keep them inside <pre>.

2\. Empty inline elements generated by mistakes. For example, <span></span>. We can remove them. But we need to keep <img>, <br>, <td>, and <meta>.

3\. Inline elements with wightspaces only generated by mistakes. For example, <span> </span>. We can replace them with a single space. But we need to keep them in <pre>.

4\. Empty block elements generated by mistakes or used for graphical presentations like vertical spaces, background or borders. For example, <div></div>. We can remove them, if we don't care about those graphical presentations.

5\. Block elements with wightspaces only generated by mistakes or used for graphical presentations like vertical spaces, background or borders. For example, <div> </div>. We can remove them, if we don't care about those graphical presentations.

6\. Other special elements for vertical spaces, like <div><br></div>.

Here is my PHP script, Remove-Dummy-Elements-in-HTML.php, that removes dummy elements in an HTML document. It also collapses whitespaces in non <pre> elements.

```
<?php
#  Remove-Dummy-Elements-in-HTML.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $input = $argv[1];
  $html = file_get_contents($input);
  $doc = new DOMDocument();

  $doc->loadHTML($html);

  $hasDummies = true;
  $i = 0;
  while ($hasDummies) {
    $i++;
    print("Removing dummies and whitespaces: $i\n");

    collapseSpaces($doc);
    $hasDummies = removeDummies($doc);

    # After removing "empty", text-empty-text becomes text-text
    # We need to combine those text neighbors.
    $html = $doc->saveHTML();
    $doc->loadHTML($html);

  }

  print($doc->saveHTML());

function collapseSpaces($node) {
  $oldList = array();
  $newList = array();

  $childList = $node->childNodes;
  if (isset($childList)) foreach ($childList as $n) {
    $t = $n->nodeName;
    if ($n->nodeType==XML_TEXT_NODE) {
      $v = $n->nodeValue;
      $v = preg_replace('/\s{2,}/', " ", $v);
      $nn = $node->ownerDocument->createTextNode($v);
      array_push($oldList, $n);
      array_push($newList, $nn);
    } else if ( !($t=="pre") && $n->hasChildNodes() ) {
      collapseSpaces($n);
    }
  }

  for ($i=0; $i<count($oldList); $i++)
    $node->replaceChild($newList[$i], $oldList[$i]);
}

function removeDummies($node) {
  $hasDummies = false;

  $junks = array();
  $oldList = array();
  $newList = array();

  $childList = $node->childNodes;
  if (isset($childList)) foreach ($childList as $n) {
    $t = $n->nodeName;

    # skip some special elements
    if ( $n->nodeType==XML_DOCUMENT_TYPE_NODE
      || $n->nodeType==XML_DOCUMENT_NODE) continue;
    if ( $t=="#text" || $t=="img" || $t=="br" || $t=="td"
      || $t=="meta" ) continue;

    if ($n->hasChildNodes()) {

      $childList = $n->childNodes;
      if ($childList->length==1) { # $n has a single child

        $i = $childList->item(0);
        $it = $i->nodeType;
        $iv = $i->nodeValue;
        if ( $it==XML_TEXT_NODE && preg_match('/^\s+$/', $iv) ) {
          # $n has a single text child with whitespaces only
          $nn = $node->ownerDocument->createTextNode(" ");
          array_push($oldList, $n);
          array_push($newList, $nn);
          $hasDummies = true;

        } else if ($i->nodeName=="br") {
          # $n has a single "br" child
          array_push($junks, $n);
          $hasDummies = true;

        } else {
          $h = removeDummies($n);
          $hasDummies = $hasDummies || $h;
        }

      } else { # $n has multiple children
        $h = removeDummies($n);
        $hasDummies = $hasDummies || $h;
      }

    } else { # remove empties elements
      array_push($junks, $n);
      $hasDummies = true;
    }

  }
  foreach($junks as $n) $n->parentNode->removeChild($n);
  for ($i=0; $i<count($oldList); $i++)
    $node->replaceChild($newList[$i], $oldList[$i]);

  return $hasDummies;
}
?>
```

Notes about my script:

*   When dummy elements are removed from the DOMNode object tree, their neighboring text nodes need to be concatenated. Instead of playing with the object tree, I dump it to an HTML string and reload it to get those text nodes concatenated.
*   When dummy elements are removed from the DOMNode object tree, their parents may become dummy elements too. So I have to run the process in a loop until there is no more dummy elements in the HTML document.

Here is an HTML document with some dummy elements and whitespaces,

```
<!-- With-Dummies.html
 - Copyright (c) 2009 HerongYang.com. All Rights Reserved.
-->
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title></title>
</head>
<body bgcolor="#ddddff">
  <p>Example<br>with<span> </span>Dummies</p>
  <div>
    <p> </p>
  </div>
  <pre>
    Copyright   c   HerongYang.com
  </pre>
  <p>
    Copyright   c   HerongYang.com
  </p>
</body>
</html>
```

Here is the output after its dummy elements are removed:

```
herong> php Remove-Dummy-Elements-in-HTML.php With-Dummies.html

Removing dummies and whitespaces: 1
Removing dummies and whitespaces: 2
Removing dummies and whitespaces: 3

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN" ...>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">\
 </head>
<body bgcolor="#ddddff"> <p>Example<br>with Dummies</p> <pre>
    Copyright   c   HerongYang.com
  </pre> <p> Copyright c HerongYang.com </p>
</body>
</html>
```

The output tells me that:

*   2 rounds of removing dummy elements perform, because of the nested dummy elements: <div> <p> </p> </div>.
*   The 3rd round acted as a verification operation to ensure there is no more dummy elements in the HTML document.
*   <pre> elements were preserved correctly.

I think my script is pretty safe to use on any non-input HTML documents. You need to revise it, if you want to use it on HTML documents with input elements.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Parsing and Managing HTML Documents](#part0193.xhtml)

∟Install DOM Extension on CentOS

This section provides a tutorial example on how to install PHP DOM Extension on CentOS systems.

On some Linux systems, you may need to install PHP DOM Extension explicitly. Here is what I did on my CentOS computer.

1\. Try an PHP script that uses the DOM Extension. You see the "Class 'DOMDocument' not found" error.

```
herong$ php Create-HTML-DOM-Document.php output.html

PHP Fatal error:  Uncaught Error: Class 'DOMDocument' not found
  in /home/herong/Create-HTML-DOM-Document.php:7
```

2\. Search for the DOM Extension binary package using "xml" as the keyword, not "dom", not "html".

```
herong$ dnf search php | grep xml

php-xml.x86_64 : A module for PHP applications which use XML
...
```

3\. Install the DOM Extension binary package.

```
herong$ sudo dnf install php-xml

Installed:
  php-xml-7.2.24-1.module_el8.2.0+313+b04d0a66.x86_64
```

4\. Try the PHP script again. It should work now.

```
herong$ php Create-HTML-DOM-Document.php hello.html

herong$ more hello.html
<html><body bgcolor="#ddddff"><p>Hello World!</p></body></html>
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Configuring and Sending Out Emails

This chapter provides tutorial examples and notes about sending emails. Topics include setting up Windows IIS as a SMTP mail server, configuring PHP to use mail() function, 'sendmail' program or SMTP/SMTPS protocols, write PHP scripts to send out emails with PHPMailer package.

> [Using Local Windows System as a Mail Server](#part0203.xhtml)
> 
> [Sending Out Emails from PHP Scripts](#part0204.xhtml)
> 
> [Sending Out Emails on Linux Systems](#part0205.xhtml)
> 
> [Install PHPMailer on CentOS Systems](#part0206.xhtml)
> 
> [Send Local Emails with PHPMailer](#part0207.xhtml)
> 
> [Send Remote Emails with PHPMailer](#part0208.xhtml)
> 
> [Use SMTPS Protocol with PHPMailer](#part0209.xhtml)
> 
> [PHP 5.6 and PHPMailer 5.2](#part0210.xhtml)
> 
> [Install PHPMailer from Source Code](#part0211.xhtml)

Takeaways:

*   IIS (Internet Information Services) can be used as a local SMTP mail server.
*   The built-in mail() function can be used to send out emails using the local 'sendmail' program.
*   The PHPMailer is a popular PHP package that allows you to send out emails to remove servers using SMTP or SMTPS protocols.
*   The best way to install PHPMailer is to download its source code from GitHub.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Configuring and Sending Out Emails](#part0202.xhtml)

∟Using Local Windows System as a Mail Server

This section provides a tutorial example on how to setup your local Windows system to use IIS (Internet Information Services) as a SMTP mail server.

PHP provides us a nice built-in function, mail(), that allows us to send emails over the Internet. But it requires a SMTP mail server that the mail() function can communicate with.

If you don't have a service provider who provides you the SMTP mail service, you can set up your local system as a SMTP mail server to test mail().

If you are running a Linux/Unix system, setting up a mail server is easy. Just run sendmail as a daemon.

If you are running a Windows system, setting up a mail server is a little bit harder. But if IIS (Internet Information Services) is running on your system, it also provides SMTP services. Here is how you can check this:

1\. Go to Control Panel / Services, and make sure Simple Mail Transfer Protocol (SMTP) is running.

2\. Open a command window, and run the following command:

```
>telnet localhost 25

220 localhost Microsoft ESMTP MAIL Service, Version: 6.0.2600.1106...
help
214-This server supports the following commands:
214 HELO EHLO STARTTLS RCPT DATA RSET MAIL QUIT HELP AUTH BDAT VRFY
quit
221 2.0.0 localhost Service closing transmission channel
```

If you got similar outputs as above, your IIS is running as SMTP mail server correctly.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Configuring and Sending Out Emails](#part0202.xhtml)

∟Sending Out Emails from PHP Scripts

This section provides a tutorial example on how to configure the PHP engine to use the local SMTP mail server and write a PHP script to send an email.

Once we have a SMTP mail server ready to use, we are ready to try to send out emails from PHP scripts.

First you need to verify the PHP initialization file, \\php\\php.ini, to make sure that the following settings are configured correctly:

```
SMTP = localhost
smtp_port = 25
```

Then write and run the following PHP script, MailTest.php:

```
<?php
#  MailTest.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
mail("nobody","Testing","This is a test.","From: herong@localhost");
?>
```

Go check to see the email is delivered or not in a command window:

```
>dir \inetpub\mailroot\drop

... d9765b3001c54a1200000001.eml

>type \inetpub\mailroot\drop\d9765b3001c54a1200000001.eml

x-sender: herong@localhost
x-receiver: nobody@localhost
Received: from localhost ([127.0.0.1]) by localhost with Microsoft...
Subject: Testing
To: nobody
From: herong@localhost
Return-Path: herong@localhost
......

This is a test.
```

If you can follow me to here, you have successfully used the PHP engine to send out an email from a PHP sample script.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Configuring and Sending Out Emails](#part0202.xhtml)

∟Sending Out Emails on Linux Systems

This section provides a tutorial example on how to use the mail() function to send an email to the local SMTP mail server.

If you are using a Linux system, you can also send out emails from PHP scripts as shown in this tutorial.

1\. Make sure that the "sendmail" command is working:

```
herong$ which sendmail
/usr/sbin/sendmail

herong$ sendmail -r "herong@localhost" joe@localhost
Subject: Last Test

Hi Joe, This is the last test. Bye!
.

jeo$ mailx ~/Maildir
& $
Message 334:
From herong@localhost Sat Jun 11 14:13:01 2021
Return-Path: <herong@localhost>
X-Original-To: joe@localhost
Delivered-To: jeo@localhost
Subject: Last Test
Date: Sat, 12 Jun 2021 14:13:00 +0800 (CST)
From: Herong Yang <herong@localhost>
Status: RO

Hi Joe, This is the last test. Bye!
```

2\. Check the "sendmail" log file:

```
herong$ sudo grep joe /var/log/maillog
Jun 12 14:04:43 mail postfix/local[697852]: ...: to=<joe@localhost>,
relay=local, delay=23, delays=23/0.01/0/0.07, dsn=2.0.0,
status=sent (delivered to maildir)
```

3\. Write PHP script to use the built-in mail() function.

```
<?php
#  Mail-Test-2.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

echo 'SMTP = ' . ini_get('SMTP') . "\n";
echo 'smtp_port = ' . ini_get('smtp_port') . "\n";
echo 'sendmail_from = ' . ini_get('sendmail_from') . "\n";
echo 'post_max_size = ' . ini_get('post_max_size') . "\n";
echo 'sendmail_path = ' . ini_get('sendmail_path') . "\n";

$to = "doe@localhost";
$subject = "Testing";
$message = "This is a test.";
$headers = "From: herong@localhost";
mail($to, $subject, $message, $headers);
?>
```

4\. Run the above PHP script, you should see the following output:

```
herong$ php Mail-Test-2.php

SMTP = localhost
smtp_port = 25
sendmail_from =
post_max_size = 10M
sendmail_path = /usr/sbin/sendmail -t -i
```

5\. Check the "sendmail" log file:

```
herong$ sudo grep joe /var/log/maillog

Jun 11 17:26:16 mail postfix/local[703828]: ***: to=<doe@localhost>,
relay=local, delay=0.12, delays=0.08/0/0/0.04, dsn=2.0.0,
status=sent (delivered to maildir)
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Configuring and Sending Out Emails](#part0202.xhtml)

∟Install PHPMailer on CentOS Systems

This section provides a tutorial example on how to install PHPMailer on CentOS systems.

Using the mail() function can only send out emails through the "sendmail" command on the local system.

If you want to send out emails through remote mail servers, you can use the PHPMailer package.

PHPMailer has the following features:

*   Integrated SMTP support – send without a local mail server
*   Send emails with multiple To, CC, BCC and Reply-to addresses
*   Add attachments, including inline
*   Support for UTF-8 content and 8bit, base64, binary, and quoted-printable encodings
*   SMTP authentication with LOGIN, PLAIN, CRAM-MD5, and XOAUTH2 mechanisms over SMTPS and SMTP+STARTTLS transports
*   Validates email addresses automatically
*   Protects against header injection attacks
*   Error messages in over 50 languages!
*   DKIM and S/MIME signing support

Here is what I did to install PHPMailer on my CentOS 8 computer.

1\. Make sure you have PHP Composer installed:

```
herong$ /usr/local/bin/composer --version
  Composer version 2.1.3 2021-06-09 16:31:20
```

2\. Using "composer require" command to install PHPMailer:

```
herong$ /usr/local/bin/composer require phpmailer/phpmailer
Using version ^6.4 for phpmailer/phpmailer
./composer.json has been created
Running composer update phpmailer/phpmailer
Loading composer repositories with package information
Updating dependencies
Lock file operations: 1 install, 0 updates, 0 removals
  - Locking phpmailer/phpmailer (v6.4.1)
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 1 install, 0 updates, 0 removals
  - Downloading phpmailer/phpmailer (v6.4.1)
  - Installing phpmailer/phpmailer (v6.4.1): Extracting archive
```

3\. Find the PHPMailer class directory:

```
herong$ /usr/local/bin/composer show phpmailer/phpmailer
  name     : phpmailer/phpmailer
  descrip. : PHPMailer is a full-featured email creation and transfer
             class for PHP
  keywords :
  versions : * v6.4.1
  path     : /home/herong/local/php/vendor/phpmailer/phpmailer
  names    : phpmailer/phpmailer
```

4\. Write a PHP script to test the PHPMailer class:

```
herong$ vi PHPMail-Test.php

<?php
#  PHPMailer-Test.php
#- Copyright 2019 (c) HerongYang.com. All Rights Reserved.

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\SMTP;
use PHPMailer\PHPMailer\Exception;

$srcDir = "/home/herong/local/php/vendor/phpmailer/phpmailer/src/";
require "$srcDir/PHPMailer.php";
require "$srcDir/SMTP.php";
require "$srcDir/Exception.php";

$mail = new PHPMailer(true);

herong$ php PHPMail-Test.php
?>
```

I see no error messages from PHPMailer-Test.php execution, so PHPMailer is installed correctly on my CentOS computer.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Configuring and Sending Out Emails](#part0202.xhtml)

∟Send Local Emails with PHPMailer

This section provides a tutorial example on how to send local emails with PHPMailer using mail() function and 'sendmail' program.

PHPMailer supports 3 options on how emails are delivered to the recipients:

*   $mail->isMail() - Call this method to deliver emails using the PHP built-in mail() function to the local host. This is the default option.
*   $mail->isSendmail() - Call this method to deliver emails using the "sendmail" program located in path specified by the $mail->$sendmail variable.
*   $mail->isSMTP() - Call this method to deliver emails using the "STMP" protocol to a remote server specified by the $mail->$host variable to the local host.

Here is a PHP script to test the first 2 options.

```
<?php
#  PHPMailer-Send-Email-Locally.php
#- Copyright 2019 (c) HerongYang.com. All Rights Reserved.

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\SMTP;
use PHPMailer\PHPMailer\Exception;

$srcDir = "/home/herong/local/php/vendor/phpmailer/phpmailer/src/";
require "$srcDir/PHPMailer.php";
require "$srcDir/SMTP.php";
require "$srcDir/Exception.php";

$mail = new PHPMailer(true);
$mail->SMTPDebug = 4; # highest debugginng level

if ($argv[1]=="mail") {
  $mail->isMail();
} else if ($argv[1]=="sendmail") {
  $mail->isSendmail();
  $mail->$sendmail = "/usr/sbin/sendmail";
} else {
  # default option
}

try {
   $mail->setFrom('joe@herongyang.com', 'Joe Doe');
   $mail->addAddress('herong@herongyang.com', 'Herong Yang');
   $mail->Subject = 'PHPMailer Test - Local Delivery';
   $mail->Body = 'There is a test message from PHPMailer.';
   $mail->send();
} catch (Exception $e) {
   # PHPMailer exceptions
   echo $e->errorMessage();
} catch (\Exception $e) {
   # PHP exceptions
   echo $e->getMessage();
}
?>
```

Run the above PHP script with different options:

```
herong$ php PHPMailer-Send-Email-Locally.php mail
...	Sending with mail()
...	Sendmail path: /usr/sbin/sendmail -t -i
...	Envelope sender: joe@herongyang.com
...	To: Herong Yang <herong@herongyang.com>
...	Subject: PHPMailer Test - Local Delivery
...	Headers: Date: Sun, 13 Jun 2021
      From: Joe Doe <joe@herongyang.com>
      Message-ID: <...@mail.herongyang.com>
      X-Mailer: PHPMailer 6.4.1 (https://github.com/PHPMailer/PHPMailer)
      MIME-Version: 1.0
      Content-Type: text/plain; charset=iso-8859-1
...	Additional params: -fjoe@herongyang.com
...	Result: true

herong$ php PHPMailer-Send-Email-Locally.php sendmail
...	Sending with sendmail
...	Sendmail path: /usr/sbin/sendmail
...	Sendmail command: /usr/sbin/sendmail -oi -fjoe@herongyang.com -t
...	Envelope sender: joe@herongyang.com
...	Headers: Date: Sun, 13 Jun 2021
      To: Herong Yang <herong@herongyang.com>
      From: Joe Doe <joe@herongyang.com>
      Subject: PHPMailer Test - Local Delivery
      Message-ID: <...@mail.herongyang.com>
      X-Mailer: PHPMailer 6.4.1 (https://github.com/PHPMailer/PHPMailer)
      MIME-Version: 1.0
      Content-Type: text/plain; charset=iso-8859-1
...	Result: true

herong$ php PHPMailer-Send-Email-Locally.php default
...	Sending with mail()
...	Sendmail path: /usr/sbin/sendmail -t -i
...	Envelope sender: joe@herongyang.com
...	To: Herong Yang <herong@herongyang.com>
...	Subject: PHPMailer Test - Local Delivery
...	Headers: Date: Sun, 13 Jun 2021
      From: Joe Doe <joe@herongyang.com>
      Message-ID: <...@mail.herongyang.com>
      X-Mailer: PHPMailer 6.4.1 (https://github.com/PHPMailer/PHPMailer)
      MIME-Version: 1.0
      Content-Type: text/plain; charset=iso-8859-1
...	Additional params: -fjoe@herongyang.com
...	Result: true
```

Output confirms that both isMail() and isSendmail() options are working correctly.

Note that PHPMailer only accepts fully qualified email addresses like joe@herongyang.com. It will reject short addresses like "joe" or "joe@localhost".

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Configuring and Sending Out Emails](#part0202.xhtml)

∟Send Remote Emails with PHPMailer

This section provides a tutorial example on how to send remote emails with PHPMailer using STMP protocol.

If you don't have an email server running on your local host, you can use PHPMailer's isSMTP() option to use the SMTP protocol to deliver emails to a remote email server.

Here is a PHP script that delivers emails to a remote email server using the SMTP protocol without the Opportunistic TLS option.

```
<?php
#  PHPMailer-Send-Email-Remotely.php
#- Copyright 2019 (c) HerongYang.com. All Rights Reserved.

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\SMTP;
use PHPMailer\PHPMailer\Exception;

$srcDir = "/home/herong/local/php/vendor/phpmailer/phpmailer/src/";
require "$srcDir/PHPMailer.php";
require "$srcDir/SMTP.php";
require "$srcDir/Exception.php";

$mail = new PHPMailer(true);
$mail->SMTPDebug = 4;
$mail->isSMTP();
$mail->SMTPAutoTLS = false; # default is "true"
$mail->Host = "192.168.1.25";

try {
   $mail->setFrom('joe@herongyang.com', 'Joe Doe');
   $mail->addAddress('herong@herongyang.com', 'Herong Yang');
   $mail->Subject = 'PHPMailer Test - Remote Delivery';
   $mail->Body = 'There is a test message from PHPMailer.';
   $mail->send();
} catch (Exception $e) {
   # PHPMailer exceptions
   echo $e->errorMessage();
} catch (\Exception $e) {
   # PHP exceptions
   echo $e->getMessage();
}
?>
```

Run the above PHP script, you will get the follow debugging messages.

```
[herong@mail php]$ php PHPMailer-Send-Email-Remotely.php
...	Connection: opening to 192.168.1.25:25, timeout=300, options=array()
...	Connection: opened
...	SMTP INBOUND: "220 mail.herongyang.com ESMTP Postfix"
...	SERVER -> CLIENT: 220 mail.herongyang.com ESMTP Postfix
...	CLIENT -> SERVER: EHLO mail.herongyang.com
...	SMTP INBOUND: "250-mail.herongyang.com"
...	SMTP INBOUND: "250-PIPELINING"
...	SMTP INBOUND: "250-SIZE 5111222333"
...	SMTP INBOUND: "250-VRFY"
...	SMTP INBOUND: "250-ETRN"
...	SMTP INBOUND: "250-STARTTLS"
...	SMTP INBOUND: "250-ENHANCEDSTATUSCODES"
...	SMTP INBOUND: "250-8BITMIME"
...	SMTP INBOUND: "250-DSN"
...	SMTP INBOUND: "250 SMTPUTF8"

...	CLIENT -> SERVER: MAIL FROM:<joe@herongyang.com>
...	SMTP INBOUND: "250 2.1.0 Ok"
...	SERVER -> CLIENT: 250 2.1.0 Ok
...	CLIENT -> SERVER: RCPT TO:<herong@herongyang.com>
...	SMTP INBOUND: "250 2.1.5 Ok"
...	SERVER -> CLIENT: 250 2.1.5 Ok
...	CLIENT -> SERVER: DATA
...	SMTP INBOUND: "354 End data with <CR><LF>.<CR><LF>"
...	SERVER -> CLIENT: 354 End data with <CR><LF>.<CR><LF>
...	CLIENT -> SERVER: Date: Sun, 13 Jun 2021 08:18:02 +0000
...	CLIENT -> SERVER: To: Herong Yang <herong@herongyang.com>
...	CLIENT -> SERVER: From: Joe Doe <joe@herongyang.com>
...	CLIENT -> SERVER: Subject: PHPMailer Test - Remote Delivery
...	CLIENT -> SERVER: Message-ID: <...@mail.herongyang.com>
...	CLIENT -> SERVER: X-Mailer: PHPMailer 6.4.1
...	CLIENT -> SERVER: MIME-Version: 1.0
...	CLIENT -> SERVER: Content-Type: text/plain; charset=iso-8859-1
...	CLIENT -> SERVER:
...	CLIENT -> SERVER: There is a test message from PHPMailer.
...	CLIENT -> SERVER:
...	CLIENT -> SERVER: .
...	SMTP INBOUND: "250 2.0.0 Ok: queued as ..."
...	SERVER -> CLIENT: 250 2.0.0 Ok: queued as ...
...	CLIENT -> SERVER: QUIT
...	SMTP INBOUND: "221 2.0.0 Bye"
...	SERVER -> CLIENT: 221 2.0.0 Bye
...	Connection: closed
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Configuring and Sending Out Emails](#part0202.xhtml)

∟Use SMTPS Protocol with PHPMailer

This section provides a tutorial example on how to send remote emails with PHPMailer using STMPS (SMTP Secure) protocol.

If your remote email server uses STMPS protocol, you need to add more settings on the PHPMailer instance.

For example, your remote email service provider gives you the following access information:

```
Host Name: smtp.example.com
Port: 587
Protocol: SMTPS (Use TLS/SSL)
Authentication: Password
User Name: herong@herongyang.com
Password: TopScret
```

Then you can use the following PHP script to send out emails.

```
<?php
#  PHPMailer-Send-Email-SMTPS.php
#- Copyright 2019 (c) HerongYang.com. All Rights Reserved.

use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\SMTP;
use PHPMailer\PHPMailer\Exception;

$srcDir = "/home/herong/local/php/vendor/phpmailer/phpmailer/src/";
require "$srcDir/PHPMailer.php";
require "$srcDir/SMTP.php";
require "$srcDir/Exception.php";

$mail = new PHPMailer(true);
$mail->SMTPDebug = 4;
$mail->isSMTP();
$mail->SMTPAuth = true;
$mail->SMTPSecure = 'TLS';
$mail->Host = "smtp.example.com";
$mail->Port = 587;
$mail->Username = 'herong@herongyang.com';
$mail->Password = 'TopScret';

try {
   $mail->setFrom('herong@herongyang.com', 'Herong Yang');
   $mail->addAddress('joe@herongyang.com', 'Joe Doe');
   $mail->Subject = 'PHPMailer Test - SMTPS Protocol';
   $mail->Body = 'There is a test message from PHPMailer.';
   $mail->send();
} catch (Exception $e) {
   # PHPMailer exceptions
   echo $e->errorMessage();
} catch (\Exception $e) {
   # PHP exceptions
   echo $e->getMessage();
}
?>
```

If you run the above PHP script, you should these debugging messages:

```
heronng$ php PHPMailer-Send-Email-SMTPS.php
...	Connection: opening to smtp.herongyang.com:587, timeout=300
...	Connection: opened
...	SMTP INBOUND: "220 smtp.herongyang.com"
...	SERVER -> CLIENT: 220 smtp.herongyang.com
...	CLIENT -> SERVER: EHLO localhost
...	SMTP INBOUND: "250-smtp.herongyang.com"
...	SMTP INBOUND: "250-PIPELINING"
...	SMTP INBOUND: "250-SIZE 73400320"
...	SMTP INBOUND: "250-STARTTLS"
...	SMTP INBOUND: "250-AUTH LOGIN PLAIN"
...	SMTP INBOUND: "250-AUTH=LOGIN"
...	SMTP INBOUND: "250-MAILCOMPRESS"
...	SMTP INBOUND: "250 8BITMIME"
...	CLIENT -> SERVER: STARTTLS
...	SMTP INBOUND: "220 Ready to start TLS"
...	SERVER -> CLIENT: 220 Ready to start TLS
...	Auth method requested: UNSPECIFIED
...	Auth methods available on the server: LOGIN,PLAIN
...	Requested auth method not available:
...	Auth method selected: LOGIN
...	CLIENT -> SERVER: AUTH LOGIN
...	SMTP INBOUND: "334 ..."
...	SMTP INBOUND: "235 Authentication successful"
...	SERVER -> CLIENT: 235 Authentication successful
...	CLIENT -> SERVER: MAIL FROM:<herong.yang@herongyang.com>
...	SMTP INBOUND: "250 Ok"
...	SERVER -> CLIENT: 250 Ok
...	CLIENT -> SERVER: RCPT TO:<herong.yang@herongyang.com>
...	SMTP INBOUND: "250 Ok"
...	SERVER -> CLIENT: 250 Ok
...	CLIENT -> SERVER: DATA
...	SMTP INBOUND: "354 End data with <CR><LF>.<CR><LF>"
...	SERVER -> CLIENT: 354 End data with <CR><LF>.<CR><LF>
...
...	CLIENT -> SERVER: .
...	SMTP INBOUND: "250 Ok: queued as"
...	SERVER -> CLIENT: 250 Ok: queued as
...	CLIENT -> SERVER: QUIT
...	SMTP INBOUND: "221 Bye"
...	SERVER -> CLIENT: 221 Bye
...	Connection: closed
```

Sometimes, you may get the following error message. The error message suggests that the certificate from the remote host failed to pass the validation. It might be using a self-signed certificate, which should be imported manually imported to your local computer.

```
...	Connection: opening to somehost.com:587, timeout=300, options=array()
...	Connection: opened
...	SMTP INBOUND: "220 somehost.com ESMTP Postfix"
...	SERVER -> CLIENT: 220 somehost.com ESMTP Postfix
...	CLIENT -> SERVER: EHLO local.herongyang.com
...	SMTP INBOUND: "250-somehost.com"
...
... CLIENT -> SERVER: STARTTLS
... SMTP INBOUND: "220 2.0.0 Ready to start TLS"
... SERVER -> CLIENT: 220 2.0.0 Ready to start TLS
... Connection failed. Error #2: stream_socket_enable_crypto(): SSL
      operation failed with code 1. OpenSSL Error messages:
      rror:14090086:SSL routines: SSL3_GET_SERVER_CERTIFICATE:
      certificate verify failed...
... SMTP Error: Could not connect to SMTP host.
... CLIENT -> SERVER: QUIT
... SMTP INBOUND: "...??????\4O...
... SERVER -> CLIENT: ????B??dU??S9Ly...
... SMTP ERROR: QUIT command failed: ????B??dU??S9Ly...
... Connection: closed
... SMTP Error: Could not connect to SMTP host.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Configuring and Sending Out Emails](#part0202.xhtml)

∟PHP 5.6 and PHPMailer 5.2

This section provides a tutorial example on how to install PHPMailer 5.2 in CentOS 8 for PHP 5.6 to send out emails to remote STMPS server.

If you are still using PHP 5.6 engine for some reason, you can use PHPMailer 5.2 to send out emails. Here is what I did on my CentOS 8 computer.

1\. Check PHP version:

```
herong$ php -version

PHP 5.6.40 (cli) (built: May 12 2020 15:27:05)
Copyright (c) 1997-2016 The PHP Group
```

2\. Install Remi's RPM repository, where PHPMailer packages are hosted.

```
herong$ export url=http://rpms.remirepo.net/enterprise/8/remi/x86_64
herong$ wget $url/remi-release-8.3-1.el8.remi.noarch.rpm
herong$ sudo rpm -Uvh remi-release-8.3-1.el8.remi.noarch.rpm
```

3\. Install php-PHPMailer from Remi's RPM repository.

```
herong$ sudo dnf --enablerepo=remi install php-PHPMailer
...
Installed:
  php-PHPMailer-5.2.28-6.el8.remi.noarch
  php-common-7.2.24-1.module_el8.2.0+313+b04d0a66.x86_64
  php-intl-7.2.24-1.module_el8.2.0+313+b04d0a66.x86_64
  php-mbstring-7.2.24-1.module_el8.2.0+313+b04d0a66.x86_64
```

4\. Find the path name where php-PHPMailer is installed:

```
herong$ sudo find / -name PHPMailer
/usr/share/php/PHPMailer

herong$ sudo ls -l /usr/share/php/PHPMailer
-rw-r--r-- 1   2464 Mar 19  2020 class.phpmaileroauthgoogle.php
-rw-r--r-- 1   7216 Mar 19  2020 class.phpmaileroauth.php
-rw-r--r-- 1 148027 Mar 26 17:43 class.phpmailer.php
-rw-r--r-- 1  11006 Mar 19  2020 class.pop3.php
-rw-r--r-- 1  43495 Mar 19  2020 class.smtp.php
-rw-r--r-- 1   1216 Mar 26 17:43 PHPMailerAutoload.php
```

5\. Run the following PHP script to test. It works!

```
<?php
#  PHPMailer-PHP-5.php
#- Copyright 2019 (c) HerongYang.com. All Rights Reserved.

$path = "/usr/share/php/PHPMailer";
require "$path/class.phpmailer.php";

$mail = new PHPMailer(true);
$mail->CharSet = "utf-8"; # must be the first
$mail->SMTPDebug = 4;
$mail->isSMTP();
$mail->SMTPAuth = true;
$mail->SMTPSecure = 'TLS';
$mail->Host = "smtp.example.com";
$mail->Port = 587;
$mail->Username = 'herong@herongyang.com';
$mail->Password = 'TopScret';

try {
   $mail->setFrom('herong@herongyang.com', 'Herong Yang');
   $mail->addAddress('joe@herongyang.com', 'Joe Doe');
   $mail->Subject = 'PHPMailer 5.2 and PHP 5.6 Test';
   $mail->Body = 'There is a test message from PHPMailer.';
   $mail->AddCC('amy@herongyang.com', '');
   $mail->AddAttachment('/home/herong/tmp/junk.pdf');
   $mail->send();
} catch (Exception $e) {
   echo $e->errorMessage();
} catch (\Exception $e) {
   echo $e->getMessage();
}
?>
```

You should avoid using "rpm" command to install PHPMailer package files directly. It is not smart enough to manage dependencies automatically. See the example below:

```
herong$ export url=http://rpms.remirepo.net/enterprise/8/remi/x86_64
herong$ wget $url/php-PHPMailer-5.2.28-6.el8.remi.noarch.rpm

heron$ sudo rpm -Uvh php-PHPMailer-5.2.28-6.el8.remi.noarch.rpm
error: Failed dependencies:
  php-date is needed by php-PHPMailer-5.2.28-6.el8.remi.noarch
  php-filter is needed by php-PHPMailer-5.2.28-6.el8.remi.noarch
  php-hash is needed by php-PHPMailer-5.2.28-6.el8.remi.noarch
  php-intl is needed by php-PHPMailer-5.2.28-6.el8.remi.noarch
  php-mbstring is needed by php-PHPMailer-5.2.28-6.el8.remi.noarch
  php-openssl is needed by php-PHPMailer-5.2.28-6.el8.remi.noarch
  php-pcre is needed by php-PHPMailer-5.2.28-6.el8.remi.noarch
  php-spl is needed by php-PHPMailer-5.2.28-6.el8.remi.noarch
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Configuring and Sending Out Emails](#part0202.xhtml)

∟Install PHPMailer from Source Code

This section provides a tutorial example on how to install PHPMailer from source code on any system without any installation tools.

If you are not able to install PHPMailer with any installation tool on any system, you can try to install it from source code as what I did below:

1\. Go to PHPMailer GitHub site at [https://github.com/PHPMailer/PHPMailer](https://github.com/PHPMailer/PHPMailer).

2\. Click "Code > Download ZIP" to get the source code as PHPMailer-master.zip.

3\. Unzip the downloaded file. You will see the "PHPMailer-master" sub-directory.

4\. Move and rename the "PHPMailer-master/src" sub-directory to a shared installation directory like:

```
linux$ sudo mv PHPMailer-master/src /usr/share/PHPMailer

mac$ sudo mv PHPMailer-master/src /Users/Shared/PHPMailer

windows> xcopy PHPMailer-master/src C:\Users\public\PHPMailer
```

5\. Update the test program, PHPMailer-Test.php, with the installation directory and run it. I see no errors.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Image and Picture Processing

This chapter provides tutorial examples and notes on creating and processing images and managing image file formats. Topics include trying 'Imager' module for PNG images; drawing graphical elements, setting transparent background, and copying images with GD Library.

> [GD Library of Image Functions](#part0213.xhtml)
> 
> [GD Library - Draw Graphical Elements](#part0214.xhtml)
> 
> [GD Library - Print 2 Pictures on 1 Page](#part0215.xhtml)
> 
> [GD Library - Create Transparent Image](#part0216.xhtml)
> 
> [Transparent Image Over Text Web Page](#part0217.xhtml)
> 
> [GD Library - Pad Transparent Image](#part0218.xhtml)

Takeaways:

*   "Imager" is a PHP module for creating and altering 24-bit images.
*   "Imager" supports only bmp, ico, pnm, raw, sgi and tga image file formats.
*   "Imager::File::PNG" is a PHP module to support PNG file format. But I could not install it on macOS.
*   GD Library is a collection of image functions that supports a variety of different image formats, including GIF, PNG, JPEG, WBMP, and XPM.
*   GD Library allows you to draw graphical elements, set transparent background, copy images, etc.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Image and Picture Processing](#part0212.xhtml)

∟GD Library of Image Functions

This section provides a quick introduction on GD Library for creating images and managing image files in BMP, GIF, PNG, JPEG formats.

GD Library is a collection of image functions that allows you manipulate image files in a variety of different image formats, including GIF, PNG, JPEG, WBMP, and XPM.

GD library supports the following main features:

*   Create new images and draw graphical elements.
*   Read images from image files in BMP, GIF, PNG, JPEG formats.
*   save images to image files in BMP, GIF, PNG, JPEG formats.
*   Transform images by clipping, scaling, rotating, flipping, etc..

Examples of GD functions:

*   gd\_info() - This "GD information" function returns information about the GD Imaging library as an array.
*   imagecreate($width,$height) - This "image create" function creates a blank image object.
*   imagecreatetruecolor($width,$height) - This "image create true color" function creates a blank image object with in true color mode, which uses RGB color format with 256 value for each color component.
*   imagecreatefromgif($path) - This "image create from GIF" function creates an image object from a GIF image file.
*   imagecreatefromjpeg($path) - This "image create from JPEG" function creates an image object from a JPEG (JPG) image file.
*   imagecreatefromwbmp($path) - This "image create from BMP" function creates an image object from a BMP image file.
*   imagegif($image,$path) - This "image GIF" function writes an image object to a GIF image file.
*   imagejpeg($image,$path) - This "image JPEG" function writes an image object to a JPEG (JPG) image file.
*   imagerotate($image,$angle,$color) - This "image rotate" function rotates an image object of $angle degrees and returns the rotated image. $color is used to fill uncovered area after the rotation.
*   imagesx($image) - This "image size x" function returns the width of $image.
*   imagesy($image) - This "image size y" function returns the height of $image.
*   imagedestroy($image) - This "image destroy" function descries an image object.
*   imagecopyresized($dst\_image,$src\_image, $dst\_x,$dst\_y, $src\_x,$src\_y, $dst\_w,$dst\_h, $src\_w,$src\_h) - This "image copy resized" function copies a part of an image from $src\_image to $dst\_image. $src\_x and $src\_y specifies the copy-from location. $dst\_x and $dst\_y specifies the copy-to location. $src\_w and $src\_h specifies the copy-from size. $dst\_w and $dst\_h specifies the copy-to size. If the copy-to size is larger or smaller than the copy-from size, the copied part will be resized.
*   imagecopyresampled($dst\_image,$src\_image, $dst\_x,$dst\_y, $src\_x,$src\_y, $dst\_w,$dst\_h, $src\_w,$src\_h) - This "image copy resampled" function does the same job as imagecopyresized() with a better quality.
*   imagecopy($dst\_image,$src\_image, $dst\_x,$dst\_y, $src\_x,$src\_y, $src\_w,$src\_h) - This "image copy" function does the same job as imagecopyresized() except that the copied part will not be resized.
*   imagecopymerge($dst\_image,$src\_image, $dst\_x,$dst\_y, $src\_x,$src\_y, $src\_w,$src\_h, $percentage) - This "image copy merge" function does the same job as imagecopy() except that the copied part will be merged to $dst\_image with a $percentage factor.
*   imagecolortransparent($image,$color) - This "image color transparent" function sets new color as the transparent color.
*   imagecolorat($image, $x,$y) - This "image color at" function returns the color value from $image at $x and $y position. In true color mode, the returned $rgb value can be decomposed as $r = ($rgb >> 16) & 0xFF, $g = ($rgb >> 8) & 0xFF, and $b = $rgb & 0xFF.
*   imagecolorsforindex(image, $color) - This "image color for index" function return RGB color values and alpha key of the specified color index.
*   imagesetpixel($image, $x,$y, $color) - This "image set pixel" function set one pixel at $x and $y with $color.
*   imagefill($image, $x,$y, $color) - This "image fill" function performs a flood fill at $x and $y position with a given $color.
*   imagecolorallocate($image, $r,$g,$b) - This "image color allocate" function allocates a color index with $r, $g and $b values. The allocated color index is returned.
*   imagecolorallocatealpha($image, $r,$g,$b, $alpha) - This "image color allocate alpha" function does the same job as imagecolorallocate() except that it applies a transparency parameter $alpha between 0, completely opaque, and 127, completely transparent.
*   imagestring($image, $font, $x,$y, $string, $color) - This "image string" function draws a $string horizontally at $x and $y with $font in $color.
*   imagettftext($image, $size, $angle, $x,$y, $color, $font, $text) - This "image TTF Text draws a $text at $x and $y with a $font of $size in a $color at an $angle.
*   imageline($image, $x1,$y1, $x2,$y2, $color) - This "image line" function draws a line in a $color.
*   imagerectangle($image, $x1,$y1, $x2,$y2, $color) - This "image rectangle" function draws a rectangle in a $color.

For more information, see GD Library Website at [https://www.php.net/manual/en/book.image.php](https://www.php.net/manual/en/book.image.php).

If you want to use the GD library, you may need to turning on the extension=gd2 (or extension=php\_gd2.dll in PHP 5) setting in php.ini.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Image and Picture Processing](#part0212.xhtml)

∟GD Library - Draw Graphical Elements

This section provides a tutorial example on how to draw graphical elements using GD Library functions.

You can use GD Library functions to create a new image and draw some graphical elements.

1\. Write a PHP script to create an image with some graphical elements added and save it to GD-Graphics.png:

```
<?php
#  GD-Create-Image.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

$image = imagecreatetruecolor(400,400);

$blue = imagecolorallocate($image, 0, 0, 255);
$green = imagecolorallocate($image, 0, 255, 0);
$red = imagecolorallocate($image, 255, 0, 0);

print("Drawing a box...\n");
imagefilledrectangle($image, 50, 50, 350, 350, $blue);

print("Drawing a circle...\n");
imagefilledellipse($image, 200, 200, 200, 200, $green);

print("Drawing 2 lines...\n");
imageline($image, 0,0, 400, 400, $red);
imageline($image, 400,0, 0, 400, $red);

$file = "GD-Graphics.png";
imagepng($image, $file);
print("Image saved:\n");
print("   File: $file\n");
?>
```

2\. Run the above script:

```
herong$ php GD-Create-Image.php
Drawing a box...
Drawing a circle...
Drawing 2 lines...
Image saved:
   File: GD-Graphics.png
```

3\. View GD-Graphics.png. You see a nice image.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Image and Picture Processing](#part0212.xhtml)

∟GD Library - Print 2 Pictures on 1 Page

This section provides a tutorial example on how to compose a print page with 2 pictures placed vertically using GD Library functions.

You can follow this tutorial to compose a print page with 2 pictures placed vertically using GD Library functions.

1\. Here is the PHP script, GD-2-To-1-Page.php:

```
<?php
#  GD-2-To-1-Page.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

$resolution = 300;
$margin = intval(0.5*$resolution);
$page_width = intval(8.5*$resolution);
$page_height = intval(11.0*$resolution);

if (count($argv)<3) {
  print("Usage: php GD-2-To-1-Page input1 input2.\n");
  exit;
}
$pic1 = imagecreatefrompng($argv[1]);
$pic2 = imagecreatefrompng($argv[2]);

$page = imagecreatetruecolor($page_width,$page_height);
$white = imagecolorallocate($page, 255,255,255);
imagefill($page, 0,0, $white);

$width = $page_width - 2*$margin;
$height = intval($page_height/2 - 1.5*$margin);
$center_x = intval($width/2) + $margin;
$center_y = intval($height/2) + $margin;
post_on_page($page, $pic1, $center_x, $center_y, $width, $height);

$width = $page_width - 2*$margin;
$height = intval($page_height/2 - 1.5*$margin);
$center_x = intval($width/2) + $margin;
$center_y = intval($height/2) + $margin + $height + $margin;
post_on_page($page, $pic2, $center_x, $center_y, $width, $height);

$file = "GD-Page.png";
imagepng($page, $file);
print("Page saved:\n");
print("   File: $file\n");

function post_on_page($page, $pic, $center_x, $center_y, $width, $height) {
  $w = imagesx($pic);
  $h = imagesy($pic);
  $ratio = min($width/$w,$height/$h);
  if ($ratio<1.0) {
    $w = intval($ratio*$w);
    $pic = imagescale($pic,$w);
    $h = imagesy($pic);
  }
  $off_x = $center_x - intval($w/2);
  $off_y = $center_y - intval($h/2);
  imagecopy($page,$pic, $off_x,$off_y, 0,0, $w,$h);

  $black = imagecolorallocate($page, 0,0,0);
  imagerectangle($page,$off_x-1,$off_y-1, $off_x+$w+1,$off_y+$h+1, $black);
}
?>
```

Run it with 2 sample pictures:

```
php GD-2-To-1-Page.php sample1.png sample2.png
Page saved:
   File: GD-Page.png
```

Note that the script is using a resolution of 300 DPI. Your picture should have more than 300\*8=2400 pixel in one direction to fill the page. In other words, the camera should take about 2400\*2400=5,760,000 or 6M pixels.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Image and Picture Processing](#part0212.xhtml)

∟GD Library - Create Transparent Image

This section provides a tutorial example on how to create an image with transparent background using GD Library functions.

If you want to create an image with a transparent background with the GD Library, here is what you need to remember:

1\. Select a color for the background of the image. Make sure this background color is not used to draw any graphical element on the image.

2\. Fill the entire image with the background color using imagefilledrectangle().

3\. Draw all graphical elements on the image using imageline(), imageRectangle(), etc.

4\. Set the background color to be transparent using imagecolortransparent().

5\. Save the image in a format that supports transparent background like GIF or PNG.

Below is a PHP script that creates transparent background image in PNG format.

```
<?php
#  GD-Create-Transparent-Image.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

$image = imagecreatetruecolor(400,400);

$blue = imagecolorallocate($image, 0, 0, 255);
$green = imagecolorallocate($image, 0, 255, 0);
$red = imagecolorallocate($image, 255, 0, 0);
$black = imagecolorallocate($image, 0, 0, 0);

print("Fill the background...\n");
$bgColor = $black;
imagefilledrectangle($image, 0, 0, 400, 400, $bgColor);

print("Drawing some graphics...\n");
imagefilledrectangle($image, 50, 50, 350, 350, $blue);
imagefilledellipse($image, 200, 200, 200, 200, $green);

print("Open a circle to see the backgound...\n");
imagefilledellipse($image, 200, 200, 100, 100, $bgColor);

print("Set the background to be transparent...\n");
imagecolortransparent($image, $bgColor);

$file = "GD-Transparent-Graphics.png";
imagepng($image, $file);
print("Image saved:\n");
print("   File: $file\n");
?>
```

Run the above PHP script example:

```
php GD-Create-Transparent-Image.php

Fill the background...
Drawing some graphics...
Open a circle to see the backgound...
Set the background to be transparent...
Image saved:
   File: GD-Transparent-Graphics.png
```

You should get an interesting transparent image.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Image and Picture Processing](#part0212.xhtml)

∟Transparent Image Over Text Web Page

This section provides a tutorial example on how to display a transparent image floating over Web page text.

If you are looking for ways to verify the transparent background of an image, you can use my following HTML document file:

```
<html><body>
<!-- Display-Transparent-Image.html -->
<img style="position:absolute; top: 50; left: 50;"
  src="GD-Transparent-Graphics.png" border="10"/>
<script type="text/javascript">
for (i=0; i<=2000; i++) {document.write('Bla ');}
</script>
</body></html>
```

Now open the above HTML file in a Web browser. You should see some text displayed on the Web page, with the transparent image floating above the text.

![Display Transparent Image over Text](Images/image00232.jpeg)

Display Transparent Image over Text

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Image and Picture Processing](#part0212.xhtml)

∟GD Library - Pad Transparent Image

This section provides a tutorial example on how to pad the transparent background of to expand an image using GD Library functions.

If you want to pad an image with a transparent background with the GD Library, here is what you need to remember:

1\. Select a color for the background of the image. Make sure this background color is not used to draw any graphical element on the image.

2\. Create a new image with the padded size of the original image.

3\. Fill the new image with the background color using imagefilledrectangle().

4\. Copy the original image to the new image using imagecopy(). The transparent background color of the original image is not copied.

5\. Set the background color of the new image to be transparent using imagecolortransparent().

6\. Save the new image in a format that supports transparent background like GIF or PNG.

Below is a PHP script that pads a transparent background image by 10% at all 4 sides.

```
<?php
#  GD-Pad-Transparent-Image.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

$factor = 10; # padding transparent background for 10%
$pic = imagecreatefrompng($argv[1]);
$w = imagesx($pic);
$h = imagesy($pic);
$padx = intval($factor*$w/100);
$pady = intval($factor*$h/100);

print("Create a new image in padded size...\n");
$image = imagecreatetruecolor($w+2*$padx, $h+2*$pady);

print("Select gray as the background.\n");
print("Hope it is not used in the original image...\n");
$bgColor = imagecolorallocate($image, 127, 127, 127);
imagefill($image, 0,0, $bgColor);

print("Copy over the original image.\n");
imagecopy($image,$pic, $padx,$pady, 0,0, $w,$h);

print("Set the background to be transparent...\n");
imagecolortransparent($image, $bgColor);

$file = "GD-Padded-Transparent-Graphics.png";
imagepng($image, $file);
print("Image saved:\n");
print("   File: $file\n");
?>
```

Run the above PHP script example:

```
php GD-Pad-Transparent-Image.php GD-Transparent-Graphics.png

Create a new image in padded size...
Select gray as the background.
Hope it is not used in the original image...
Copy over the original image.
Set the background to be transparent...
Image saved:
   File: GD-Padded-Transparent-Graphics.png
```

You should get a padded transparent image.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Managing ZIP Archive Files

This chapter provides tutorial examples and notes on managing ZIP archive files. Topics include introduction of ZipArchive class; creating new ZIP archive; extracting files from ZIP archive; creating directory structure inside ZIP archive; creating ZIP archive in a temporary file with dynamic data.

> [The ZipArchive Class](#part0220.xhtml)
> 
> [Create New ZIP Archive](#part0221.xhtml)
> 
> [Exact Files from ZIP Archive](#part0222.xhtml)
> 
> [Create ZIP Archive with Directory](#part0223.xhtml)
> 
> [Create ZIP Archive for Download](#part0224.xhtml)

Takeaways:

*   Use ZipArchive class to manage ZIP archives with PHP scripts.
*   Use "$zip = new ZipArchive;" to create an instance of ZipArchive class.
*   Use "$zip->open($zip\_path\_name, ZipArchive::CREATE);" to create a ZIP archive.
*   Use "$zip->addFile($file);" to add a file to the ZIP archive.
*   Use "$zip->extractTo($destination, $file);" to extract a file from the ZIP archive.
*   Use "$zip->addEmptyDir($dir\_path);" to create a directory inside the ZIP archive.
*   Use "$zip->addFile($file, $dir\_path);" to add a file to the given directory inside the ZIP archive.
*   Use "$tmpDir = sys\_get\_temp\_dir();" to access the system temporary directory.
*   Use "$tmpFile = tempnam($tmpDir, $prefix);" to get a temporary file name.
*   Use "$zip->open($tmpFile, ZipArchive::CREATE);" to create a ZIP archive in a temporary file.
*   Use "$zip->addFromString($fileName, $data);" to add dynamic data as file inside the ZIP archive.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing ZIP Archive Files](#part0219.xhtml)

∟The ZipArchive Class

This section provides a quick introduction to the ZipArchive class, which provides you creating new ZIP archives, extracting files from existing ZIP archives, and other functionalities.

**What Is ZipArchive Class?** - ZipArchive is a built-in PHP class that provides you creating new ZIP archives, extracting files from existing ZIP archives, and other functionalities.

Here is a list of some main methods provided by the ZipArchive class:

*   $zip = $zip = new ZipArchive: Creates an instance of the ZipArchive class as $zip.
*   $zip->open(): Associates the given ZIP archive to $zip. Option flags can be provided to create new or update/extract existing ZIP archives.
*   $zip->close(): Closes the associated ZIP archive.
*   $zip->addFile(): Adds the given file to the associated ZIP archive.
*   $zip->addFromString(): Adds the given string as a file to the associated ZIP archive.
*   $zip->addEmptyDir(): Adds the given path name as empty directory to the associated ZIP archive.
*   $zip->addPattern(): Adds files that match the regular expression pattern from a given directory. The operation is not recursive. The pattern will be matched against the file name only.
*   $zip->extractTo(): Extract the complete archive or the given files to the specified destination.
*   $zip->deleteName(): Deletes an entry in the associated archive using its name.
*   $zip->setPassword: Sets the password for the associated archive.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing ZIP Archive Files](#part0219.xhtml)

∟Create New ZIP Archive

This section provides a tutorial example on how to create a new ZIP archive and add files into the archive using the ZipArchive class.

The best way to create a new ZIP archive is to use the "ZipArchive::CREATE" flag in the $zip->open() method. For example, the following code will create a new empty ZIP archive, if '/tmp/test.zip' does not exist. If '/tmp/test.zip' exists, it will be open to add new entries or extract entries. It fails only if '/tmp/test.zip' exists and is not a ZIP file.

```
$zip = new ZipArchive;
$zip->open('/tmp/test.zip',ZipArchive::CREATE);
```

Here is an example script that create a new ZIP archive and adds some files into the archive.

```
<?php
#  zip-create-new.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $zip = new ZipArchive;
  echo "Creating test.zip:\n";
  $rc = $zip->open('/tmp/test.zip',ZipArchive::CREATE);
  if ($rc === TRUE) {
    echo "   test.zip opened\n";

    $file = 'dot.gif';
    if ($zip->addFile($file) === TRUE) {
      echo "   $file added\n";
    } else {
      echo "   Failed to add $file.\n";
    }

    $file = 'zip-create-new.php';
    if ($zip->addFile($file) === TRUE) {
      echo "   $file added\n";
    } else {
      echo "   Failed to add $file.\n";
    }

    $file = 'junk.jnk';
    if ($zip->addFile($file) === TRUE) {
      echo "   $file added\n";
    } else {
      echo "   Failed to add $file.\n";
    }

    $zip->close();
  } else {
    echo "   Failed to create test.zip with error: $rc\n";
  }
?>
```

Let's try it:

```
herong$ php zip-create-new.php
Creating test.zip:
   test.zip opened
   dot.gif added
   zip-create-new.php added
   Failed to add junk.jnk.

herong$ unzip -l /tmp/test.zip
Archive:  /tmp/test.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
       43  03-01-2020 14:15   dot.gif
      815  03-01-2020 15:17   zip-create-new.php
---------                     -------
      858                     2 files
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing ZIP Archive Files](#part0219.xhtml)

∟Exact Files from ZIP Archive

This section provides a tutorial example on how to open an existing ZIP archive and extract files from the archive using the ZipArchive class.

The easiest way to extract files from an ZIP archive to use the $zip->extractTo() method. For example, the following code extracts 'dot.gif' from '/tmp/test.zip' into the '/tmp' directory.

```
$zip = new ZipArchive;
$zip->open('/tmp/test.zip');
$zip->extractTo('/tmp','dot.gif');
```

Here is an example script that opens an existing ZIP archive and extracts files from the archive.

```
<?php
#  zip-extract-file.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $zip = new ZipArchive;
  echo "Opening test.zip:\n";
  $rc = $zip->open('/tmp/test.zip',ZipArchive::CREATE);
  if ($rc === TRUE) {
    echo "   test.zip opened\n";

    $file = 'dot.gif';
    if ($zip->extractTo('.', $file) === TRUE) {
      echo "   $file extracted\n";
    } else {
      echo "   Failed to extract $file.\n";
    }

    mkdir('./tmp');
    if ($zip->extractTo('./tmp') === TRUE) {
      echo "   All files extracted\n";
    } else {
      echo "   Failed to extract all files.\n";
    }

    $zip->close();
  } else {
    echo "   Failed to open test.zip with error: $rc\n";
  }
?>
```

Let's try it:

```
herong$ php zip-extract-file.php
Opening test.zip:
test.zip opened
dot.gif extracted
All files extracted

herong$ ls -l tmp
total 16
-rw-r--r--  1 herong  staff   43 Mar  1 15:37 dot.gif
-rw-r--r--  1 herong  staff  815 Mar  1 15:37 zip-create-new.php
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing ZIP Archive Files](#part0219.xhtml)

∟Create ZIP Archive with Directory

This section provides a tutorial example on how to create a ZIP archive with a directory and adds files to that directory using the ZipArchive class.

If you want create a directory structure inside the ZIP archive so that files can be added to the archive to different locations, you need to two methods from the ZipArchive class:

1\. Create directory inside ZIP archive using addEmptyDir() method. For example, the following code creates a directory and a sub-directory.

```
$zip->addEmptyDir('src');
$zip->addEmptyDir('src/gif');
```

2\. Add file to archive with local path name using addFile() method. For example, the following code adds 'dot.gif' to the 'src/gif' sub-directory in the archive.

```
$zip->addFile('dot.gif', 'src/gif/dot.gif');
```

Here is an example script that creates a new ZIP archive with a directory and adds some files to that directory in the archive.

```
<?php
#  zip-with-directory.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.

  $zip = new ZipArchive;
  echo "Creating test.zip:\n";
  $rc = $zip->open('/tmp/test.zip',ZipArchive::CREATE);
  if ($rc === TRUE) {
    echo "   test.zip opened\n";

    $dir = "srcDir";
    if ($zip->addEmptyDir($dir) === TRUE) {
      echo "   $dir added\n";
    } else {
      echo "   Failed to add $dir.\n";
    }

    $file = 'dot.gif';
    if ($zip->addFile($file, "$dir/$file") === TRUE) {
      echo "   $file added\n";
    } else {
      echo "   Failed to add $file.\n";
    }

    $file = 'zip-create-new.php';
    if ($zip->addFile($file, "$dir/$file") === TRUE) {
      echo "   $file added\n";
    } else {
      echo "   Failed to add $file.\n";
    }

    $zip->close();
  } else {
    echo "   Failed to create test.zip with error: $rc\n";
  }
?>
```

Let's try it:

```
herong$ php zip-with-directory.php
Creating test.zip:
   test.zip opened
   srcDir added
   dot.gif added
   zip-create-new.php added

herong$ unzip -l /tmp/test.zip
Archive:  /tmp/test.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
        0  06-04-2020 15:53   srcDir/
       43  06-04-2020 15:37   srcDir/dot.gif
      815  06-04-2020 15:17   srcDir/zip-create-new.php
---------                     -------
      858                     3 files
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing ZIP Archive Files](#part0219.xhtml)

∟Create ZIP Archive for Download

This section provides a tutorial example on how to create a ZIP archive in a temporary file with dymanic data and send it to Web browser as a download using the ZipArchive class.

If you have data items from database for Users to download from a Web server, you may want to ZIP them on the fly so users can download them in a single ZIP file.

Of course, the best option is to retrieve data items from database in memory, ZIP them in memory and send the ZIP to user's browser without creating any physical files on the Web server. However, this is not doable with the ZipArchive class, which does not support ZIP archive as file handles or pipes.

The next option is to retrieve data items from database in memory, ZIP them in a temporary file and remove it after sending it to user's browser. This can be done the following steps:

1\. Create a unique file name in the system temporary directory as the ZIP file name:

```
$tmpDir = sys_get_temp_dir();
$zipFile = tempnam($tmpDir, "ZIP"); # ZIP is the prefix for temp name
```

2\. Open the temporary file and the ZIP archive:

```
$zip->open($zipFile, ZipArchive::CREATE);
```

3\. Retrieve data items from database and loop over each item.

4\. Create an unique name for each item, and the item data to the ZIP archive as a string.

```
$itemData = ...; # based data from database
$itemName = ...; # based record ID from database
$zip->addFromString("$itemName", $itemData);
```

5\. Close the ZIP archive, read the ZIP data back from the temporary file, and remove it immediately.

```
$zip->close();
$zipData = file_get_contents($zipFile);
unlink($zipFile);
```

6\. Send the ZIP data to the Web browser.

Here is an example script that creates a new ZIP archive in temporary file with dynamic data items. The ZIP archive is then pushed to client browser.

```
<?php
#  zip-in-temp-file.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
  $dir = "msg";
  $file = 'hello.txt';

  $tmpDir = sys_get_temp_dir();
  $zipFile = tempnam($tmpDir, "ZIP");

  $zip = new ZipArchive;
  error_log("Creating ZIP file $zipFile");
  $rc = $zip->open($zipFile, ZipArchive::CREATE);
  if ($rc === TRUE) {
    if ($zip->addEmptyDir($dir) === TRUE) error_log("$dir added");

    # this could be any data and muliple times
    if ($zip->addFromString("$dir/$file", 'Hello world!') === TRUE)
      error_log("$file added");

    $zip->close();
  } else {
    error_log("Failed to create ZIP with error: $rc");
  }

  $zipData = file_get_contents($zipFile);
  unlink($zipFile);

  header("Content-Type: application/octet-stream");
  header("Content-Disposition: attachment; filename=Hello.zip");
  header("Content-Length: " . strlen($zipData));
  header("Cache-Control: no-cache");
  print($zipData);
?>
```

If you put the above script on a Web server and open it in Web browser. You will get a ZIP file, Hello.zip, downloaded.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Managing PHP Engine and Modules on macOS

This chapter provides tutorial examples and notes on managing PHP engine and modules on macOS systems. Topics include verify PHP installation on macOS.

> [PHP Version Pre-Installed on macOS](#part0226.xhtml)
> 
> [Upgrade PHP Engine on macOS](#part0227.xhtml)

Takeaways:

*   macOS comes with PHP engine pre-installed.
*   No PHP binary package available in Homebrew repository for macOS 10.12.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing PHP Engine and Modules on macOS](#part0225.xhtml)

∟PHP Version Pre-Installed on macOS

This section provides notes to verify PHP version supported on macOS and run a simple PHP interactive scripting session.

macOS comes with PHP engine pre-installed. Here is what I did to verify the PHP version and program file location:

1\. Start a Terminal and run "php -version" to see the PHP version number:

```
herong$ php -version
PHP 5.6.30 (cli) (built: Feb  7 2017 16:18:37)
Copyright (c) 1997-2016 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2016 Zend Technologies
```

2\. Run PHP scripts interactively:

```
herong$ php -a
Interactive shell

php > print "Hello world!\n";
Hello world!

php > exit
```

3\. Verify PHP program file locations:

```
herong$ which php
/usr/bin/php
```

4\. Get a detailed list of modules supported in PHP:

```
herong$  php -i | more
phpinfo()
PHP Version => 5.6.30

System => Darwin local 16.7.0 Darwin Kernel Version 16.7.0:
   Thu Jun 15 17:36:27 PDT 2017; root:xnu-3789.70.16~2/RELEASE_X86_64 x86_64
Build Date => Feb  7 2017 16:11:14
Configure Command =>  '/Library/Caches/com.apple.xbs/Binaries/apache_mod_php
   /apache_mod_php-117.2~3/TempContent/Objects/php/configure'
   '--mandir=/usr/share/man' '--infodir=/usr/share/info'
   '--disable-dependency-tracking' '--sysconfdir=/private/etc' ...

Server API => Command Line Interface
Virtual Directory Support => disabled
Configuration File (php.ini) Path => /etc
Loaded Configuration File => /etc/php.ini

curl

cURL support => enabled
cURL Information => 7.54.0
Age => 3
Features
AsynchDNS => Yes
CharConv => No
Debug => No
...
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing PHP Engine and Modules on macOS](#part0225.xhtml)

∟Upgrade PHP Engine on macOS

This section provides notes on upgrade PHP on macOS computers. There seems to be no PHP binary package available in Homebrew repository for macOS 10.12.

Here is what I did to upgrade the PHP engine on my macOS computer.

1\. Search for PHP binary packages managed by Homebrew:

```
herong$ brew search php

==> Formulae
php@7.2
phplint
phpmyadmin
phpunit
php
php-cs-fixer
php@7.3
...
```

2\. Get the "php" package information:

```
herong$ brew info php

php: stable 7.4.12, HEAD
General-purpose scripting language
https://www.php.net/
Not installed
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/php.rb
License: PHP-3.01
==> Dependencies
...
==> Options
--HEAD
  Install HEAD version
==> Caveats
...
```

3\. Install "php" package.

```
herong$ brew install php

Error:
  homebrew-cask is a shallow clone.
To `brew update`, first run:
  git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask fetch --unshallow

This restriction has been made on GitHub's request because updating shallow
clones is an extremely expensive operation due to the tree layout and traffic of
Homebrew/homebrew-core and Homebrew/homebrew-cask. We don't do this for you
automatically to avoid repeatedly performing an expensive unshallow operation in
CI systems (which should instead be fixed to not use shallow clones). Sorry for
the inconvenience!

Warning: You are using macOS 10.12.
We (and Apple) do not provide support for this old version.
You will encounter build failures with some formulae.
Please create pull requests instead of asking for help on Homebrew's GitHub,
Twitter or any other official channels. You are responsible for resolving
any issues you experience while you are running this
old version.

Error: php: no bottle available!
You can try to install from source with e.g.
  brew install --build-from-source php
Please note building from source is unsupported. You will encounter build
failures with some formulae. If you experience any issues please create pull
requests instead of asking for help on Homebrew's GitHub, Twitter or any other
official channels.
```

4\. Upgrade brew:

```
herong$ git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask fetch --unshallow

remote: Enumerating objects: 94461, done.
remote: Counting objects: 100% (91037/91037), done.
remote: Compressing objects: 100% (28031/28031), done.
remote: Total 83177 (delta 61120), reused 77072 (delta 55130), pack-reused 0
Receiving objects: 100% (83177/83177), 39.20 MiB | 5.31 MiB/s, done.
Resolving deltas: 100% (61120/61120), completed with 5002 local objects.
From https://github.com/Homebrew/homebrew-cask
   6c13600ce5..125cd9a5ca  master     -> origin/master
```

5\. Try to install PHP again. It sill says "php: no bottle available!"

```
herong$ brew install php

Updating Homebrew...
==> Auto-updated Homebrew!

Warning: You are using macOS 10.12.
...

Error: php: no bottle available!
...
```

Looks like I need to upgrade my macOS 10.12 to a newer release. I will do it later.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Managing PHP Engine and Modules on CentOS

This chapter provides tutorial examples and notes on managing PHP engine and modules on CentOS systems. Topics include verify PHP installation on CentOS.

> [PHP Version Pre-Installed on CentOS](#part0229.xhtml)
> 
> [Install PHP Extensions on CentOS](#part0230.xhtml)
> 
> [PHP Version Pre-Installed on CentOS 6](#part0231.xhtml)
> 
> [Use PHP Composer on CentOS Computers](#part0232.xhtml)

Takeaways:

*   CentOS comes with PHP engine pre-installed.
*   "sudo dnf install php-\*" command can be used to install PHP extensions.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing PHP Engine and Modules on CentOS](#part0228.xhtml)

∟PHP Version Pre-Installed on CentOS

This section provides notes to verify PHP version supported on CentOS and run a simple PHP interactive scripting session.

CentOS comes with PHP engine pre-installed. Here is what I did to verify the PHP version and program file locations:

1\. Run "uname -mprsv" to confirm the Linux version. The output shows that I am running Linux 4 with CentOS 8 (el8):

```
herong$ uname -mprsv
Linux 4.18.0-147.el8.x86_64
   #1 SMP Wed Dec 4 21:51:45 UTC 2019 x86_64 x86_64
```

2\. Run "php -version" to see the PHP version number:

```
herong$ php -version

PHP 7.2.11 (cli) (built: Oct  9 2018 15:09:36) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.2.0, Copyright (c) 1998-2018 Zend Technologies
```

3\. Run PHP scripts interactively:

```
herong$ php -a
Interactive shell

php > print "Hello world!\n";
Hello world!

php > exit
```

4\. Verify PHP program file locations:

```
herong$ which php
/usr/bin/php
```

5\. Verify PHP installation package information:

```
herong$ dnf info php
CentOS-8 - AppStream ...
CentOS-8 - Extras ...

Installed Packages
Name         : php
Version      : 7.2.11
Release      : 2.module_el8.1.0+209+03b9a8ff
Architecture : x86_64
Size         : 5.5 M
Source       : php-7.2.11-2.module_el8.1.0+209+03b9a8ff.src.rpm
Repository   : @System
From repo    : AppStream
Summary      : PHP scripting language for creating dynamic web sites
URL          : http://www.php.net/
License      : PHP and Zend and BSD and MIT and ASL 1.0
Description  : PHP is an HTML-embedded scripting language. PHP attempts to make it
             : easy for developers to write dynamically generated web pages. PHP also
             : offers built-in database integration for several commercial and
             : non-commercial database management systems, so writing a
             : database-enabled webpage with PHP is fairly simple. The most common
             : use of PHP coding is probably as a replacement for CGI scripts.
             :
             : The php package contains the module (often referred to as mod_php)
             : which adds support for the PHP language to Apache HTTP Server.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing PHP Engine and Modules on CentOS](#part0228.xhtml)

∟Install PHP Extensions on CentOS

This section provides a tutorial example on how to add PHP extensions on CentOS Linux systems by searching and installing the extension using the 'dnf' package manager.

PHP has many extensions. Some of them are pre-installed and some are not. If you are getting errors like "Class ... not found", or "Call to undefined function ...", you need to install the extension that provides the missing class or function.

For example, when I test a new Web application on my CentOS system, I see this error. I know that I need to install the ZIP extension.

```
PHP Fatal error:  Uncaught Error: Class 'ZipArchive' not found in
   /var/www/html/download.php:361

Stack trace:
#0 download.php(338): zipData()
#1 dowload.php(22): prepareData()
#2 {main}
```

To fix the problem, I check what PHP extensions have been installed on the system first:

```
herong$ dnf list installed | grep php

php.x86_64
php-cli.x86_64
php-common.x86_64
php-fpm.x86_64
php-json.x86_64
php-mbstring.x86_64
php-mysqlnd.x86_64
php-pdo.x86_64
```

There is no ZIP related extensions installed yet. So I search for PHP extensions:

```
herong$ dnf search php

...
php-opcache.x86_64 : The Zend OPcache
php-pecl-zip.x86_64 : A ZIP archive management extension
php-pecl-apcu.x86_64 : APC User Cache
php-pecl-apcu-devel.x86_64 : APCu developer files (header)
```

I see that "php-pecl-zip" is available for my system. So I install it:

```
herong$ sudo dnf install php-pecl-zip
...
Installed:
php-pecl-zip-1.15.3-1.module_el8.1.0+209+03b9a8ff.x86_64
libzip-1.5.1-2.module_el8.1.0+209+03b9a8ff.x86_64
Complete!
```

Now re-run the Web application. The 'ZipArchive' error is gone!

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing PHP Engine and Modules on CentOS](#part0228.xhtml)

∟PHP Version Pre-Installed on CentOS 6

This section provides notes to verify PHP version supported on CentOS 6.0 and run a simple PHP interactive scripting session.

Older versions of CentOS also comes with PHP engine pre-installed. Here is what I did to verify the PHP version and program file locations on my CentOS 6 system:

1\. Run "php -version" to see the PHP version number:

```
herong$ php -version

PHP 5.3.3 (cli) (built: Mar 22 2017 12:17:33)
Copyright (c) 1997-2010 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies
```

2\. Run PHP scripts interactively:

```
herong$ php -a
Interactive shell

php > print "Hello world!\n";
Hello world!

php > exit
```

3\. Verify PHP program file locations:

```
herong$ which php
/usr/bin/php
```

4\. Check to see if there any updates available:

```
herong$ yum info php

Installed Packages
Name        : php
Arch        : i686
Version     : 5.3.3
Release     : 49.el6
Size        : 3.3 M
Repo        : installed
From repo   : base
Summary     : PHP scripting language for creating dynamic web sites
URL         : http://www.php.net/
License     : PHP
Description : PHP is an HTML-embedded scripting language. PHP attempts to
              ...

Available Packages
Name        : php
Arch        : i686
Version     : 5.3.3
Release     : 50.el6_10
Size        : 1.1 M
Repo        : updates
Summary     : PHP scripting language for creating dynamic web sites
URL         : http://www.php.net/
License     : PHP
Description : PHP is an HTML-embedded scripting language. PHP attempts to
              ...
```

So there is a minor update available. I can install it with the "yum install php" command if I want to.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Managing PHP Engine and Modules on CentOS](#part0228.xhtml)

∟Use PHP Composer on CentOS Computers

This section provides a tutorial example on how to install PHP Composer to manage PHP packages on CentOS systems.

**What is PHP Composer?** PHP Composer is an extension package manager for the PHP environment. Composer will pull in all the required extension packages your PHP script depends on and manage them for you.

Here is what I did to install PHP Composer on my CentOS 8 computer.

1\. Install required tools:

```
herong$ sudo dnf install php-cli php-zip wget unzip
```

2\. Download the Composer setup script:

```
herong$ sudo php -r \
  "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```

3\. Run Composer setup script:

```
herong$ sudo php composer-setup.php --install-dir=/usr/local/bin \
  --filename=composer

All settings correct for using Composer
Downloading...
Composer (version 2.1.3) successfully installed to: /usr/local/bin/composer
Use it: php /usr/local/bin/composer
```

4\. Try Composer command:

```
herong$ /usr/local/bin/composer
   ______
  / ____/___  ____ ___  ____  ____  ________  _____
 / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
/ /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
\____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                    /_/
Composer version 2.1.3 2021-06-09 16:31:20

Usage:
  command [options] [arguments]

...
Available commands:
  about     Shows a short information about Composer.
  archive   Creates an archive of this composer package.
  config    Sets config options.
  exec      Executes a vendored binary/script.
  help      Displays help for a command
  info      Shows information about packages.
  list      Lists commands
  require   Adds required packages to your composer.json and installs them.
  ...
```

5\. Run "composer show --platform" command to show all PHP packages on the platform.

```
herong$ sudo /usr/local/bin/composer show --platform
composer-plugin-api    2.1.0      The Composer Plugin API
composer-runtime-api   2.1.0      The Composer Runtime API
ext-calendar           7.2.24     The calendar PHP extension
ext-ctype              7.2.24     The ctype PHP extension
ext-curl               7.2.24     The curl PHP extension
ext-date               7.2.24     The date PHP extension
ext-dom                20031129   The dom PHP extension
ext-exif               7.2.24     The exif PHP extension
ext-fileinfo           1.0.5      The fileinfo PHP extension
ext-filter             7.2.24     The filter PHP extension
ext-ftp                7.2.24     The ftp PHP extension
ext-gettext            7.2.24     The gettext PHP extension
ext-hash               1.0        The hash PHP extension
ext-iconv              7.2.24     The iconv PHP extension
ext-json               1.6.0      The json PHP extension
ext-libxml             7.2.24     The libxml PHP extension
ext-mbstring           7.2.24     The mbstring PHP extension
ext-mysqli             7.2.24     The mysqli PHP extension
...
lib-bz2                1.0.6      The bz2 library
lib-curl               7.61.1     The curl library
lib-curl-libssh        0.9.4      curl libssh version
lib-curl-openssl       1.1.1.7    curl OpenSSL version (1.1.1.7)
lib-curl-zlib          1.2.11     curl zlib version
lib-date-timelib       2017.09    date timelib version
lib-date-zoneinfo      0          zoneinfo ("Olson") database for date
lib-fileinfo-libmagic  531        fileinfo libmagic version
lib-iconv              2.28       The iconv library
lib-libxml             2.9.7      libxml library version
lib-libxslt            1.1.32     The libxslt library
...
php                    7.2.24     The PHP interpreter
php-64bit              7.2.24     The PHP interpreter, 64bit
php-ipv6               7.2.24     The PHP interpreter, with IPv6 support
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟Archived Tutorials

This chapter contains some outdated tutorial notes and example codes from previous versions of this book.

> [Archived: Downloading and Installing PHP 7.0 for Windows](#part0234.xhtml)
> 
> [Archived: Downloading and Installing PHP 5.6.6 for Windows](#part0235.xhtml)
> 
> [Archived: Downloading and Installing PHP 5.4.3 for Windows](#part0236.xhtml)
> 
> [Archived: Downloading and Installing PHP 5.2.2 for Windows](#part0237.xhtml)
> 
> [Archived: Downloading and Installing PHP 5.0.4 for Windows](#part0238.xhtml)
> 
> [Archived: Adding PHP to IIS as CGI](#part0239.xhtml)
> 
> [Archived: Downloading Apache HTTP Server 2.4.12 for Windows](#part0240.xhtml)
> 
> [Archived: Installing Apache HTTP Server 2.4.12 on Windows](#part0241.xhtml)
> 
> [Archived: Publishing PHP Scripts as Web Pages](#part0242.xhtml)
> 
> [Archived: Configuration for php\_mysql.dll Library](#part0243.xhtml)
> 
> [Archived: mysql\_connect() using php\_mysql.dll Library](#part0244.xhtml)
> 
> [Archived: MySqlLoop.php using php\_mysql.dll Library](#part0245.xhtml)
> 
> [Archived: Get\_Temperature.php - First Example of SOAP](#part0246.xhtml)
> 
> [Archived: Get\_Temperature\_Dump.php - Dumping Debugging Information](#part0247.xhtml)
> 
> [Archived: MySqlUnicode.php using php\_mysql.dll Library](#part0248.xhtml)

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Downloading and Installing PHP 7.0 for Windows

This section provides a tutorial example on how to download and install the PHP engine 7.0 on a Windows system.

1\. Go to [windows.php.net/download/](http://windows.php.net/download/) and download the "VC14 x86 Thread Safe (2016-Jan-06 23:30:05)" binary version for Windows. You will get a file called "php-7.0.2-Win32-VC14-x86.zip" of 21,846,474 bytes.

2\. Unzip "php-7.0.2-Win32-VC14-x86.zip" to \\php folder.

3\. Open a command window, and try the following commands:

```
herong> \php\php -v
```

4\. If see an error message saying: "The program can't start because VCRUNTIME140.dll is missing from your computer. Try reinstalling the program to fix this problem.", you need to install "Visual Studio 2015 x86".

*   Go to "Microsoft Visual C++ Redistributable for Visual Studio 2015" page at [microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145).
*   Click the "Download" button.
*   Save the download file "vc\_redist.x86.exe" to desktop.
*   Double-click on "vc\_redist.x86.exe" to run it.
*   Follow instruction to finish installation.

5\. Open a command window, and try the following commands again:

```
herong> \php\php -v

PHP 7.0.2 (cli) (built: Jan  6 2016 13:05:11) ( ZTS )
Copyright (c) 1997-2015 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2015 Zend Technologies
```

Cool, both Command Line Interface (CLI) and Common Gateway Interface (CGI) of PHP are working!

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Downloading and Installing PHP 5.6.6 for Windows

This section provides a tutorial example on how to download and install the PHP engine 5.6.6 on a Windows system.

1\. Go to [windows.php.net/download/](http://windows.php.net/download/) and download the "VC11 x86 Thread Safe (2015-Feb-19 01:45:25)" binary version for Windows. You will get a file called "php-5.6.6-Win32-VC11-x86.zip" of 21,072,108 bytes.

2\. Unzip "php-5.6.6-Win32-VC11-x86.zip" to \\php folder.

3\. Open a command window, and try the following commands:

```
herong> \php\php -v
PHP 5.6.6 (cli) (built: Feb 18 2015 16:02:19)
Copyright (c) 1997-2015 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2015 Zend Technologies

herong> \php\php-cgi -v
PHP 5.6.6 (cgi-fcgi) (built: Feb 18 2015 16:02:17)
Copyright (c) 1997-2015 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2015 Zend Technologies
```

Cool, both Command Line Interface (CLI) and Common Gateway Interface (CGI) of PHP are working!

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Downloading and Installing PHP 5.4.3 for Windows

This section provides a tutorial example on how to download and install the PHP engine 5.4.3 on a Windows system.

1\. Go to [windows.php.net/download/](http://windows.php.net/download/) and download the "PHP 5.4 (5.4.3) - VC9 x86 Thread Safe (2012-May-08 18:26:37)" binary version for Windows. You will get a file called php-5.4.3-Win32-VC9-x86.zip of 14.44MB.

2\. Unzip php-5.4.3-Win32-VC9-x86.zip to \\php directory.

3\. Open a command window, and try the following commands:

```
herong> \php\php -v
PHP 5.4.3 (cli) (built: May  8 2012 00:51:31)
Copyright (c) 1997-2012 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2012 Zend Technologies

herong> \php\php-cgi -v
PHP 5.4.3 (cgi-fcgi) (built: May  8 2012 00:51:30)
Copyright (c) 1997-2012 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2012 Zend Technologies
```

Cool, both Command Line Interface (CLI) and Common Gateway Interface (CGI) of PHP are working!

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Downloading and Installing PHP 5.2.2 for Windows

This section provides a tutorial example on how to download and install the PHP engine 5.2.2 on a Windows system.

1\. Go to [php.net](http://www.php.net), and download PHP 5.2.2 binary for Windows. You will get a file called php-5.0.4-Win32.zip of 9722 KB.

2\. Unzip php-5.2.2-Win32.zip to \\php directory.

3\. Open a command window, and try the following commands:

```
herong> \php\php -v
PHP 5.2.2 (cli) (built: May  2 2007 19:18:26)
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

herong> \php\php-cgi -v
PHP 5.2.2 (cgi-fcgi) (built: May  2 2007 19:18:25)
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies
```

Cool, both Command Line Interface (CLI) and Common Gateway Interface (CGI) of PHP are working!

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Downloading and Installing PHP 5.0.4 for Windows

This section provides a tutorial example on how to download and install the PHP engine 5.0.4 on a Windows system.

1\. Go to [php.net](http://www.php.net), and download PHP 5.0.4 binary for Windows. You will get a file called php-5.0.4-Win32.zip of 7488 KB.

2\. Unzip php-5.0.4-Win32.zip to \\php directory.

3\. Open a command window, and try the following commands:

```
herong> \php\php -v
PHP 5.0.4 (cli) (built: Mar 31 2005 02:45:48)
Copyright (c) 1997-2004 The PHP Group
Zend Engine v2.0.4-dev, Copyright (c) 1998-2004 Zend Technologies

herong> \php\php-cgi -v
PHP 5.0.4 (cgi-fcgi) (built: Mar 31 2005 02:45:43)
Copyright (c) 1997-2004 The PHP Group
Zend Engine v2.0.4-dev, Copyright (c) 1998-2004 Zend Technologies
```

Cool, both Command Line Interface (CLI) and Common Gateway Interface (CGI) of PHP are working!

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Adding PHP to IIS as CGI

This section provides a tutorial example on how to add the PHP engine to the IIS server to serve PHP scripts as Web pages.

If you want to add PHP scripts to your IIS server to serve as Web pages, you need to add the PHP engine to the IIS server as a CGI interface.

1\. Add \\php to the PATH environment variable. I assume you know how to do this.

2\. Set up PHP configuration file. First copy \\php\\php.ini-recommended to \\php\\php.ini. Then edit \\php\\php.ini to set the following values:

```
cgi.force_redirect = 0
doc_root = "c:\inetpub\wwwroot"
cgi.redirect_status_env = ENV_VAR_NAME
```

3\. Create a new environment variable PHPRC with \\php. This is needed to access php.ini.

4\. Now we need to change IIS configuration to run PHP scripts as CGI scripts. Click Control Panel, Internet Information Service (IIS), Default Web Site, and Properties. On the Directory tab, first set Execute Permissions to "Scripts only". Then click Configuration to add a new Application Mapping with Executable=\\php\\php-cgi.exe, Extension=.php, and Script engine checked.

5\. Stop and start Default Web Site in IIS.

6\. Copy Hello.php to \\inetpub\\wwwroot.

7\. Run Internet Explorer (IE) with http://localhost/Hello.php. You should see:

```
Hello world!
```

Congratulation, you have added PHP to IIS as CGI correctly!

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Downloading Apache HTTP Server 2.4.12 for Windows

This section describes how to download Apache (HTTP Server) 2.4.12 binary distribution for Windows systems.

In order to serve PHP scripts as Web pages, you need to have a Web server running and integrated with the PHP engine. The most popular Web server today is Apache (HTTP Server). Here is what you should do to download Apache 2.4.12 binary distribution for Windows:

1\. If you have an older version of Apache (HTTP Server) running on your computer, uninstall it first.

2\. Go to [Apache HTTP Server Web site](http://httpd.apache.org/).

3\. Go to the "Apache 2.4.\* Released" section and click the "Download" link. You will see "Downloading the Apache HTTP Server" page.

4\. Go to the "Apache HTTP Server 2.4.\* (httpd)" section and click "Files for Microsoft Windows". Do not click the "Binaries" link. The "win32" folder is empty under the "Binaries" link.

5\. Go to the "Apache Lounge" site and click "httpd-2.4.12-win32-VC11.zip" under the "Apache 2.4.12 Win32" section to start download.

6\. Save the downloaded file, httpd-2.4.12-win32-VC11.zip, 12,335,452 bytes, in a temporary folder.

See the next tutorial on how to install Apache Windows version.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Installing Apache HTTP Server 2.4.12 on Windows

This section describes how to install Apache 2.4.12 binary distribution on Windows systems.

After downloaded Apache HTTP Server 2.4.12, I continued to install it on my Windows system:

1\. Unzip httpd-2.4.12-win32-VC11.zip. Move and rename sub folder .\\Apache24 to be C:\\apache.

2\. Try to start the Apache server in a command window. I got the following error:

```
C:\>\apache\bin\httpd

httpd: Syntax error on line 37 of C:/apache/conf/httpd.conf:
   ServerRoot must be a valid directory
```

3\. To fix this error, open and edit the following line in C:\\apache\\conf\\httpd.conf:

```
#ServerRoot "c:/Apache24" # original setting
ServerRoot "c:/apache"
```

4\. Terminate the httpd process in Task Manager and start the Apache server again. I got another error:

```
C:\>\apache\bin\httpd

AH00526: Syntax error on line 242 of C:/apache/conf/httpd.conf:
DocumentRoot must be a directory
```

5\. Open and edit C:\\apache\\conf\\httpd.conf again to fix the DocumentRoot configuration:

```
#DocumentRoot "c:/Apache24/htdocs"
DocumentRoot "c:/apache/htdocs"
#<Directory "c:/Apache24/htdocs">
<Directory "c:/apache/htdocs">
```

6\. Terminate the httpd process and start the Apache server again. No errors reported this time.

7\. Open a Web browser with http://localhost. You should see the Apache server default home page saying: "It works!".

Congratulations, the Apache Server is up and running now as a Web server serving HTTP requests at the default port 80. See the next tutorial on how to serve HTML static documents on Apache server.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Publishing PHP Scripts as Web Pages

This section describes how to publish PHP scripts as Web pages on the Apache server.

To verify my Apache and PHP integration, here what I did to publish a PHP script as a Web page on the Apache server:

1\. I wrote this simple PHP script, hello.php, with a text editor:

```
<html>
<body>
<?php echo "Hello world!"; ?> - PHP script.
</body>
</html>
```

2\. Copied this script file to Apache document directory, \\apache\\htdocs:

```
C:\> copy hello.php \apache\htdocs
```

3\. View it with a Web browser at http://localhost/hello.php. Surprisingly, I got the following error:

```
Forbidden

You don't have permission to access
   /cgi-bin-php/php-cgi.exe/hello.php on this server.
```

4\. Check the error log file: \\apache\\logs\\error.log. I saw this message:

```
[authz_core:error] ... AH01630: client denied by server
   configuration: C:/local/php/php-cgi.exe
```

5\. I modified the access control section in \\apache\\conf\\httpd.conf to match what Apache 2.4 provided for the /cgi-bin directory:

```
<Directory "/local/php/">
    AllowOverride None
    Options None
    Require all granted
</Directory>
```

6\. Restart the Apache server and run the PHP script again http://localhost/hello.php. The Web page resulted from the PHP script shows up correctly this time:

```
Hello world! - PHP script.
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Configuration for php\_mysql.dll Library

This section provides a tutorial example on how to configure the PHP engine for MySQL server connection access. Setting, extension=php\_mysql.dll, needs to be turned in the configuration file php.ini.

To use PHP with MySQL servers, of course you need to install a MySQL server on you system first. On my local system, I have a MySQL server installed in \\mysql directory. If you need help on installing a MySQL server on your system, please read my other tutorial book, "Herong's Notes on SQL".

To make sure my MySQL server is running on my local system, I executed commands below to start my MySQL server and check its status:

```
herong> \mysql\bin\mysqld

herong> \mysql\bin\mysqladmin ping
mysqld is alive
```

Now edit \\php\\php.ini with:

```
extension=php_mysql.dll
```

Then I added \\php\\ext to the PATH system environment variable, because php\_mysql.dll is located in the \\php\\ext directory.

When I was ready to test the configuration, I ran this script:

```
<?php
#  MySqlTest.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   $con = mysql_connect('localhost');
   print "MySQL server info = ".mysql_get_server_info()."\n";
   print "MySQL status = ".mysql_stat()."\n";
   mysql_close($con);
?>
```

I got this output:

```
herong> php MySqlTest.php
MySQL server info = 5.0.2-alpha
MySQL status = Uptime: 1167  Threads: 1  Questions: 5  Slow queries...
  Flush tables: 1  Open tables: 0  Queries per second avg: 0.004
```

Cool, this confirmed that my PHP engine configured to access my MySQL server.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: mysql\_connect() using php\_mysql.dll Library

This section describes functions supported by the MySQL extension library, php\_mysql.dll. mysql\_connect() creates a connection to the specified MySQL server.

PHP's MySQL support comes from an extension library, php\_mysql.dll, which offers a number of functions:

*   mysql\_connect() - Connects to a MySQL server, and returns a connection resource. In most cases, you need to call it with 3 arguments like mysql\_connect($server, $username, $password). $server specifies the network address of machine where the MySQL server is running. $username specifies the user login name on the MySQL server. $password specifies the password for the login name.
*   mysql\_close() - Closes a MySQL connection resource. Usually, you call it with 1 parameter like mysql\_close($connection), where $connection represents the connection resource to be closed.
*   mysql\_get\_server\_info() - Returns a string of server information.
*   mysql\_status() - Returns a string of server status.
*   mysql\_query() - Sends a query to the server, and returns a result set resource. For example, mysql\_query('SELECT \* FROM MyTable WHERE ID = 10').
*   mysql\_affected\_rows() - Returns the number of effected rows of the given result set, if the executed query is an INSERT or UPDATE statement.
*   mysql\_num\_rows() - Returns the number of rows of the given result set, if the executed query is a SELECT statement.
*   mysql\_fetch\_array() - Fetches a row from a given result set, and returns the row as an array with both numeric index, and column name map. It will return boolean false, if there is no row left in the result set.
*   mysql\_free\_result() - Frees the given result set.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: MySqlLoop.php using php\_mysql.dll Library

This section provides a tutorial example on how to use MySQL functions to connect to a MySQL server, and run SQL statements to create a table, insert rows and fetch rows with the MySQL server.

To show you how some of those MySQL functions should be used, I wrote this simple script, MySqlLoop.php:

```
<?php
#  MySqlLoop.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   $con = mysql_connect('localhost');
   $rs = mysql_query('DROP DATABASE MyBase');
   $rs = mysql_query('CREATE DATABASE MyBase');
   $rs = mysql_query('USE MyBase');
   print "Creating a table...\n";
   $rs = mysql_query('CREATE TABLE MyTable (ID INTEGER,'
      .' Value INTEGER)');
   $n = 100;
   $i = 0;
   print "Inserting some rows to the table...\n";
   while ($i < $n) {
      $rs = mysql_query('INSERT INTO MyTable VALUES ('.$i.', '
         .rand(0,$n-1).')');
      $i++;
   }
   print "Query some rows from the table...\n";
   $rs = mysql_query('SELECT * FROM MyTable WHERE ID < 10');
   print "   ".mysql_field_name($rs,0)."   "
      .mysql_field_name($rs,1)."\n";
   while ($row = mysql_fetch_array($rs)) {
      print "    ".$row[0].'   '.$row[1]."\n";
   }
   mysql_free_result($rs);
   mysql_close($con);

function mysqli_field_name($result, $field_offset) {
   $properties = mysqli_fetch_field_direct($result, $field_offset);
   return is_object($properties) ? $properties->name : null;
}
?>
```

Note that if the connection resource is not specified in a query call, the last connection resource will be used. If you run this script, you will get something like:

```
Creating a table...
Inserting some rows to the table...
Query some rows from the table...
   ID   Value
    0   14
    1   91
    2   84
    3   16
    4   88
    5   51
    6   12
    7   19
    8   39
    9   5
```

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Get\_Temperature.php - First Example of SOAP

This section provides a tutorial example on how to use the SOAP extension to call a Web service provided by xmethods.org to get the current temperature.

To show you an example of how PHP SOAP extension can be used in a SOAP client application, here is my first SOAP PHP script, Get\_Temperature.php

```
<?php
#  Get_Temperature.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   $client = new SoapClient
      ("http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl");
   echo("\nReturning value of getTemp() call: ".
      $client->getTemp("12345"));
?>
```

Run it while your computer is connected to the Internet. You will get:

```
>php Get_Temperature.php

Returning value of getTemp() call: 52
```

Very nice. This confirms that:

*   PHP SOAP extension is easy to use. Two statements are enough to call a SOAP service.
*   You PHP SOAP extension is installed correctly and working.
*   PHP SOAP extension supports WSDL.
*   www.xmethods.net is doing a great job for offering this demonstration SOAP service.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: Get\_Temperature\_Dump.php - Dumping Debugging Information

This section provides a tutorial example on how to use SOAP client functions to make Web service call on the target SOAP node and print detailed debug information.

After learning the basic functions of the SoapClient class, I revised my Get\_Temperature.php client program to get more information on how SOAP Extension works, and to show you how to debug a SOAP client program. The new client program is called, Get\_Temperature\_Dump.php:

```
<?php
#  Get_Temperature_Dump.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   $zip = "123456";
   $client = new SoapClient
      ("http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl",
      array('trace' => 1));

   echo("\nDumping client object:\n");
   var_dump($client);

   echo("\nDumping client object functions:\n");
   var_dump($client->__getFunctions());

   $return = $client->getTemp($zip);
   echo("\nReturning value of getTemp() call: ".$return);

   $return = $client->__soapCall("getTemp",array($zip));
   echo("\nReturning value of __soapCall() call: ".$return);

   echo("\nDumping request headers:\n"
      .$client->__getLastRequestHeaders());

   echo("\nDumping request:\n".$client->__getLastRequest());

   echo("\nDumping response headers:\n"
      .$client->__getLastResponseHeaders());

   echo("\nDumping response:\n".$client->__getLastResponse());
?>
```

If you run this sample script, you will get:

```
Dumping client object:
object(SoapClient)#1 (3) {
  ["trace"]=>
  int(1)
  ["_soap_version"]=>
  int(1)
  ["sdl"]=>
  resource(5) of type (Unknown)
}

Dumping client object functions:
array(1) {
  [0]=>
  string(30) "float getTemp(string $zipcode)"
}

Returning value of getTemp() call: 52

Returning value of __soapCall() call: 52

Dumping request headers:
POST /soap/servlet/rpcrouter HTTP/1.1
Host: services.xmethods.net
Connection: Keep-Alive
User-Agent: PHP SOAP 0.1
Content-Type: text/xml; charset=utf-8
SOAPAction: ""
Content-Length: 510
Cookie: JSESSIONID=uuqkGDvtzw_IPlMLsodnVX9j;

Dumping request:
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:ns1="urn:xmethods-Temperature-Demo"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
 SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
 <SOAP-ENV:Body><ns1:getTemp>
  <zipcode xsi:type="xsd:string">123456</zipcode>
 </ns1:getTemp></SOAP-ENV:Body>
</SOAP-ENV:Envelope>

Dumping response headers:
HTTP/1.1 200 OK
Server: Enhydra-MultiServer/3.1.1b1
Status: 200
Content-Type: text/xml; charset=utf-8
Servlet-Engine: Enhydra Application Server/3.1.1b1 (JSP 1.1;
   Servlet 2.2; Java 1.4.2_03; Linux 2.4.7-10smp i386;
   java.vendor=Sun Microsystems Inc.)
Content-Length: 470
X-Cache: MISS from www.xmethods.net
Keep-Alive: timeout=15, max=99
Connection: Keep-Alive

Dumping response:
<?xml version='1.0' encoding='UTF-8'?>
<SOAP-ENV:Envelope
 xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<SOAP-ENV:Body>
<ns1:getTempResponse xmlns:ns1="urn:xmethods-Temperature-Demo"
SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">
<return xsi:type="xsd:float">52.0</return>
</ns1:getTempResponse>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

The output is very useful. It confirms that:

*   The default SOAP version is SOAP 1.1. For SOAP 1.2, the envelope namespace should be http://www.w3.org/2003/05/soap-envelope, not http://schemas.xmlsoap.org/soap/envelope/.
*   The transportation protocol is HTTP/1.1. See the request header lines.
*   There is only one RPC function supported in this WSDL: "float getTemp(string $zipcode)". See the \_\_getFunctions() dump.
*   SOAP Extension converts my getTemp() RPC call nicely in a SOAP request message based on the definitions in the WSDL document.
*   The returning value is also converted properly into a "float" type of value, not a "string". The SOAP response message shows "52.0", but the print out of $return is "52".

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟[Archived Tutorials](#part0233.xhtml)

∟Archived: MySqlUnicode.php using php\_mysql.dll Library

This section provides a tutorial example on how to send and receive non-ASCII character strings in Unicode UTF-8 encoding to and from a MySQL database server.

My is my sample script to show you how to send UTF-8 strings to a MySQL server and store them in UTF-8 encoding, MySqlUnicode.php:

```
<?php
#  MySqlUnicode.php
#- Copyright 2009 (c) HerongYang.com. All Rights Reserved.
#
   $con = mysql_connect('localhost');
   print "\nDefault settings...\n";
   $rs = mysql_query("SHOW VARIABLES LIKE 'character_set_%'");
   while ($row = mysql_fetch_array($rs)) {
      print "    ".$row[0].'   '.$row[1]."\n";
   }

   print "\nUpdated settings...\n";
   $rs = mysql_query("SET NAMES 'utf8'");
   $rs = mysql_query("SHOW VARIABLES LIKE 'character_set_%'");
   while ($row = mysql_fetch_array($rs)) {
      print "    ".$row[0].'   '.$row[1]."\n";
   }

   print "\nCreating a table in UTF-8...\n";
   $rs = mysql_query('DROP DATABASE MyBase');
   $rs = mysql_query('CREATE DATABASE MyBase CHARACTER SET utf8');
   $rs = mysql_query('USE MyBase');
   $rs = mysql_query('CREATE TABLE MyTable (ID INTEGER,'
      .' Message VARCHAR(80))');

   print "\nInserting some rows to the table...\n";
   $str = "Hello!";
   $rs = mysql_query("INSERT INTO MyTable VALUES ( 1, '$str')");
   $str = "\xC2\xA1Hola!";
   $rs = mysql_query("INSERT INTO MyTable VALUES ( 2, '$str')");
   $str = "\xE4\xBD\xA0\xE5\xA5\xBD!";
   $rs = mysql_query("INSERT INTO MyTable VALUES ( 3, '$str')");

   print "\nQuery some rows from the table...\n";
   $rs = mysql_query('SELECT * FROM MyTable WHERE ID < 10');
   print "   ".mysql_field_name($rs,0)."   "
      .mysql_field_name($rs,1)."\n";
   while ($row = mysql_fetch_array($rs)) {
      print "    ".$row[0].'   '.$row[1]."=(\x".bin2hex($row[1]).")\n";
   }
   mysql_free_result($rs);
   mysql_close($con);
?>
```

If you run it, you will get:

```
Default settings...
    character_set_client   latin1
    character_set_connection   latin1
    character_set_database   latin1
    character_set_results   latin1
    character_set_server   latin1
    character_set_system   utf8
    character_sets_dir   C:\local\MySQL\share\charsets/

Updated settings...
    character_set_client   utf8
    character_set_connection   utf8
    character_set_database   latin1
    character_set_results   utf8
    character_set_server   latin1
    character_set_system   utf8
    character_sets_dir   C:\local\MySQL\share\charsets/

Creating a table in UTF-8...

Inserting some rows to the table...

Query some rows from the table...
   ID   Message
    1   Hello!=(\x48656c6c6f21)
    2   -íHola!=(\xc2a1486f6c6121)
    3   S+ásÑ+!=(\xe4bda0e5a5bd21)
```

MySQL works as expected, no conversion on the SQL statements, storing strings in UTF-8, and no conversion on query result.

[PHP Tutorials - Herong's Tutorial Examples](#part0001.xhtml)

∟References

List of reference materials used in this book.

*   *LERDORF.COM*, Rasmus Lerdorf (Creator of the PHP programming language), [www.lerdorf.com/](http://www.lerdorf.com/)
*   *PHP: Hypertext Preprocessor*, The PHP Group, [www.php.net/](http://www.php.net/)
*   *PHP Freaks.com: Your PHP Help Center!*, The Web Freaks, INC., [www.phpfreaks.com/](http://www.phpfreaks.com/)
*   *Zend - The PHP Company*, Zend Technologies Ltd., [www.zend.com/](http://www.zend.com/)
*   *ISO/IEC 8859-1*, Wikipedia, [en.wikipedia.org/wiki/ISO\_8859-1](http://en.wikipedia.org/wiki/ISO_8859-1)
*   *Herong's Tutorial Notes on Unicode*, Herong Yang, [herongyang.com/unicode/](https://www.herongyang.com/unicode/)
*   *Herong's Tutorial Notes on GB23212*, Herong Yang, [herongyang.com/gb2312/](https://www.herongyang.com/gb2312/)

![The Front Cover](Images/cover00233.jpeg)