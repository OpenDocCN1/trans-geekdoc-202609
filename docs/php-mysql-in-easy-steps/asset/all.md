![image](images/cover.jpg)

![image](images/title.jpg)

In easy steps is an imprint of In Easy Steps Limited

16 Hamilton Terrace **·** 42 Holly Walk **·** Leamington Spa

Warwickshire **·** United Kingdom **·** CV32 4LY

[www.ineasysteps.com](http://www.ineasysteps.com)

Second Edition

Copyright © 2018 by In Easy Steps Limited. All rights reserved. No part of this book may be reproduced or transmitted in any form or by any means, electronic or mechanical, including photocopying, recording, or by any information storage or retrieval system, without prior written permission from the publisher.

Notice of Liability

Every effort has been made to ensure that this book contains accurate and current information. However, In Easy Steps Limited and the author shall not be liable for any loss or damage suffered by readers as a result of any information contained herein.

Trademarks

All trademarks are acknowledged as belonging to their respective companies.

Contents

[1 **Getting started**](#chapter01.html)

[Introducing PHP & MySQL](#chapter01.html#sec1)

[Understanding The Cloud](#chapter01.html#sec2)

[Installing Abyss Web Server](#chapter01.html#sec3)

[Installing the PHP engine](#chapter01.html#sec4)

[Configuring Abyss for PHP](#chapter01.html#sec5)

[Embedding PHP script](#chapter01.html#sec6)

[Installing the MySQL Server](#chapter01.html#sec7)

[Using the MySQL Client](#chapter01.html#sec8)

[Creating MySQL users](#chapter01.html#sec9)

[Connecting PHP & MySQL](#chapter01.html#sec10)

[Summary](#chapter01.html#sec11)

[2 **Performing operations**](#chapter02.html)

[Creating variables](#chapter02.html#sec12)

[Managing strings](#chapter02.html#sec13)

[Producing arrays](#chapter02.html#sec14)

[Sorting arrays](#chapter02.html#sec15)

[Describing dimensions](#chapter02.html#sec16)

[Doing arithmetic](#chapter02.html#sec17)

[Comparing values](#chapter02.html#sec18)

[Assessing logic](#chapter02.html#sec19)

[Defining constants](#chapter02.html#sec20)

[Summary](#chapter02.html#sec21)

[3 **Controlling progress**](#chapter03.html)

[Branching alternatives](#chapter03.html#sec22)

[Switching branches](#chapter03.html#sec23)

[Performing loops](#chapter03.html#sec24)

[Looping while true](#chapter03.html#sec25)

[Breaking from loops](#chapter03.html#sec26)

[Creating functions](#chapter03.html#sec27)

[Passing arguments](#chapter03.html#sec28)

[Returning values](#chapter03.html#sec29)

[Summary](#chapter03.html#sec30)

[4 **Producing forms**](#chapter04.html)

[Performing actions](#chapter04.html#sec31)

[Checking set values](#chapter04.html#sec32)

[Validating form data](#chapter04.html#sec33)

[Sending hidden data](#chapter04.html#sec34)

[Handling submissions](#chapter04.html#sec35)

[Making sticky forms](#chapter04.html#sec36)

[Surrounding forms](#chapter04.html#sec37)

[Appending link data](#chapter04.html#sec38)

[Moving location](#chapter04.html#sec39)

[Summary](#chapter04.html#sec40)

[5 **Assembling tables**](#chapter05.html)

[Introducing tables](#chapter05.html#sec41)

[Creating tables](#chapter05.html#sec42)

[Defining data types](#chapter05.html#sec43)

[Adding modifiers](#chapter05.html#sec44)

[Setting primary keys](#chapter05.html#sec45)

[Altering tables](#chapter05.html#sec46)

[Summary](#chapter05.html#sec47)

[6 **Handling data**](#chapter06.html)

[Inserting data](#chapter06.html#sec48)

[Updating columns](#chapter06.html#sec49)

[Updating fields](#chapter06.html#sec50)

[Deleting data](#chapter06.html#sec51)

[Selecting data](#chapter06.html#sec52)

[Retrieving columns](#chapter06.html#sec53)

[Retrieving rows](#chapter06.html#sec54)

[Sorting data](#chapter06.html#sec55)

[Setting direction](#chapter06.html#sec56)

[Making comparisons](#chapter06.html#sec57)

[Summary](#chapter06.html#sec58)

[7 **Connecting databases**](#chapter07.html)

[Making connection](#chapter07.html#sec59)

[Executing queries](#chapter07.html#sec60)

[Retrieving results](#chapter07.html#sec61)

[Applying changes](#chapter07.html#sec62)

[Counting records](#chapter07.html#sec63)

[Updating records](#chapter07.html#sec64)

[Validating results](#chapter07.html#sec65)

[Ensuring security](#chapter07.html#sec66)

[Handling errors](#chapter07.html#sec67)

[Summary](#chapter07.html#sec68)

[8 **Registering users**](#chapter08.html)

[Creating a users database](#chapter08.html#sec69)

[Providing a register page](#chapter08.html#sec70)

[Processing registrations](#chapter08.html#sec71)

[Providing a login page](#chapter08.html#sec72)

[Supplying login tools](#chapter08.html#sec73)

[Processing login attempts](#chapter08.html#sec74)

[Confirming login success](#chapter08.html#sec75)

[Summary](#chapter08.html#sec76)

[9 **Providing forums**](#chapter09.html)

[Creating a forum database](#chapter09.html#sec77)

[Providing a forum page](#chapter09.html#sec78)

[Supplying a message form](#chapter09.html#sec79)

[Processing posted messages](#chapter09.html#sec80)

[Confirming post success](#chapter09.html#sec81)

[Summary](#chapter09.html#sec82)

[10 **Processing shops**](#chapter10.html)

[Creating a shop database](#chapter10.html#sec83)

[Creating an orders database](#chapter10.html#sec84)

[Providing a shop page](#chapter10.html#sec85)

[Confirming cart additions](#chapter10.html#sec86)

[Processing shopping carts](#chapter10.html#sec87)

[Checking out orders](#chapter10.html#sec88)

[Confirming logout success](#chapter10.html#sec89)

[Summary](#chapter10.html#sec90)

**Preface**

The creation of this book has provided me, Mike McGrath, a welcome opportunity to demonstrate the latest server-side scripting techniques with PHP and MySQL databases. All examples I have given in this book demonstrate modern features of the PHP scripting language using the current MySQL Relational Database Management System that is supported on both Windows and Linux operating systems. I sincerely hope you enjoy discovering the exciting possibilities of PHP and MySQL, and have as much fun with it as I did in writing this book.

In order to clarify the code listed in the steps given in each example, I have adopted certain colorization conventions. Components of the PHP language are colored blue; programmer-specified names are red; numeric and string data values are black; and comments are green:

**<?php**

**\# Write the traditional greeting.**

$string \= ‘<p>Hello World!</p>’ ;

echo $string ;

**?>**

Similarly, components of the SQL query language are colored blue; programmer-specified names are red; numeric and string data values are black; and comments are green:

\# Insert 5 records into the "top\_5\_films" table.

INSERT INTO top\_5\_films ( position , title , year ) VALUES ( 1 , "Citizen Kane" , 1941 ) ;

Additionally, in order to identify each source code file described in the steps, a colored icon and file name appears in the margin alongside the steps:

![image](images/pg6_1.jpg)

script.php

![image](images/pg6_2.jpg)

query.sql

![image](images/pg6_3.jpg)

index.html

![image](images/pg6_4.jpg)

style.css

For convenience I have placed source code files from the examples featured in this book into a single ZIP archive. You can obtain the complete archive by following these easy steps:

![image](images/1g1.jpg)Browse to **[http://www.ineasysteps.com](http://www.ineasysteps.com)** then navigate to Free Resources and choose the Downloads section

![image](images/2g1.jpg)Find PHP & MySQL in easy steps, 2nd edition in the list, then click on the hyperlink entitled All Code Examples to download the archive

![image](images/3g1.jpg)Now, extract the archive contents to any convenient location on your computer

1

Getting started

***Welcome to the exciting world of the data-driven web with PHP & MySQL. This chapter demonstrates how to create a dynamic development environment incorporating the Abyss Web Server, the PHP engine, and the MySQL database server.***

[**Introducing PHP & MySQL**](#chapter01.html#sec1)

[**Understanding The Cloud**](#chapter01.html#sec2)

[**Installing Abyss Web Server**](#chapter01.html#sec3)

[**Installing the PHP engine**](#chapter01.html#sec4)

[**Configuring Abyss for PHP**](#chapter01.html#sec5)

[**Embedding PHP script**](#chapter01.html#sec6)

[**Installing the MySQL Server**](#chapter01.html#sec7)

[**Using the MySQL Client**](#chapter01.html#sec8)

[**Creating MySQL users**](#chapter01.html#sec9)

[**Connecting PHP & MySQL**](#chapter01.html#sec10)

[**Summary**](#chapter01.html#sec11)

**Introducing PHP & MySQL**

The most appealing modern websites provide a customized user experience by dynamically responding to some current conditions – user name, time of day, latest blog, shopping cart contents, etc. Many of these dynamic websites are created with PHP and MySQL.

![image](images/pg8_1.jpg)

**What is PHP?**

PHP is a widely-used general purpose scripting language that is especially suited for web development, and can be embedded into HTML. It was created by programmer Rasmus Lerdorf as a set of scripts to maintain his website that he released as “Personal Home Page Tools (PHP Tools) version 1.0” on June 8, 1995. These were extended in the version 2 release of 1997, and the name changed to become a recursive acronym “PHP: Hypertext Preprocessor” in version 3 the following year. Performance, reliability, and extensibility were improved in 2000 with the release of PHP4, which was powered by the new Zend engine – a virtual machine. The current version, PHP5, is powered by the Zend II engine and produced as free software by the PHP group. Today, PHP is installed on over 20 million websites and 1 million web servers.

![image](images/pg8_2.jpg)

**What is MySQL?**

MySQL is the world’s most popular database software. It is used to manage stored data and is described as DataBase Management Software (DBMS) or Relational DataBase Management Software (RDBMS). MySQL was created by Michael Wildenius and David Axmark back in 1995. Its name (“My-S-Q-L” officially, but often pronounced “My Sequel”) is a combination of Michael’s daughter’s name “My” and the term “SQL” (Structured Query Language). MySQL was originally produced by the company MySQL AB, founded by its creators, which was acquired by Sun Microsystems in 2008, and subsequently by Oracle in 2010. The current version, MySQL 8.0, is powered by the InnoDB storage engine, and the MySQL Community Server edition is available as free software. Today, MySQL is used on some of the most frequently visited websites, including Google, Wikipedia, Facebook and Twitter.

It is important to recognize that PHP and MySQL are both “server-side” technologies – that is to say they reside on the web server. They are not “client-side” technologies resident on the user’s computer. So their magic takes place in “The Cloud”.

**Understanding The Cloud**

Whenever a user asks to view a web page in their browser it requests the page from the web server, and receives the page in response, via the HTTP protocol. Where a web page contains PHP script, the web server may first call upon the PHP engine to process the code and, if required, request data from a MySQL database before sending the response to the browser.

![image](images/pg9_1.jpg)

The ensuing pages describe how to create a development environment for data-driven websites by installing the following server-side technologies on your own computer:

•Web Server – Abyss Web Server X1 Free Personal Edition

•PHP Engine – PHP 7.2.4

•MySQL Server – MySQL Community Server 8.0.11

![image](images/hot.jpg)

HTTP (HyperText Transfer Protocol) is the common communication standard that allows any computer connected to any web server to access files across the web.

![image](images/forget.jpg)

The examples in this book are created and tested with the listed software versions but may require modification for other versions.

**Installing Abyss Web Server**

Abyss X1 is a free compact web server available for Windows, macOS/Mac OS X, and Linux operating systems available for download at **[aprelium.com](http://www.aprelium.com)**. Despite its small footprint, Abyss supports many powerful features, including dynamic content generation with server-side scripts – so is an ideal companion for PHP & MySQL.

The Abyss Web Server can be installed on your own computer to provide an environment for PHP & MySQL website development.

![image](images/1b.jpg)Download the Abyss X1 Web Server setup package for your system from **[aprelium.com/abyssws/download.php](http://www.aprelium.com/abyssws/download.php)**

![image](images/pg10_2.jpg)

![image](images/2b.jpg)Run the setup installer and accept the License terms, then choose to install with the recommended options

![image](images/pg10_3.jpg)

![image](images/pg10_1.jpg)

Further guidance on installation of the Abyss Web Server is available at **[aprelium.com/abyssws/start.html](http://www.aprelium.com/abyssws/start.html)**

![image](images/forget.jpg)

The Abyss setup package for Windows is an executable file named **abwsx1.exe** that you run to install the web server.

![image](images/3b.jpg)Accept the suggested location of **C:\\Abyss Web Server**, then choose to install Abyss as a Windows Service

![image](images/pg11_1.jpg)

![image](images/4b.jpg)Next, select your preferred language, then enter a name and password for future access to the Abyss server console

![image](images/5b.jpg)Now, log in using your chosen name and password to see the Abyss console confirm the server status as Running

![image](images/pg11_2.jpg)

![image](images/6b.jpg)Finally, enter **http://localhost** into your browser address field, then hit Return to see the default Abyss Welcome page get served up by the Abyss Web Server

![image](images/pg11_3.jpg)

![image](images/snake.jpg)

If you choose the Manual startup option, the Abyss logo will not appear in your system tray for easy start/stop control and access to the server console. Instead, the console can be found with your browser at **http://localhost:9999**.

![image](images/hot.jpg)

In the Abyss console, click the Configure button then the General icon to see the default HTTP Port is 80 and the default Documents Path (where your web pages will reside) is /**htdocs**.

**Installing the PHP engine**

The PHP interpreter “engine”, which implements PHP scripts within web pages, is available for Windows, macOS/Mac OS X, and Linux operating systems as a free download at **[php.net](http://www.php.net)**

![image](images/php.jpg)

Further guidance on installation of PHP is available at **[php.net/manual/en/install.php](http://www.php.net/manual/en/install.php)**

Additionally, a pre-configured package for the Abyss Web Server on Windows is available from **[aprelium.com](http://www.aprelium.com)** and is recommended for a simple, fast installation.

![image](images/1b.jpg)Download the PHP setup package for your system from **[aprelium.com/downloads](http://www.aprelium.com/downloads)**

![image](images/2b.jpg)Run the downloaded executable file to launch the Setup Wizard, then click on the Next button to begin

![image](images/pg12_1.jpg)

![image](images/3b.jpg)Next, accept the License terms, then click on the Next button to proceed with the installation

![image](images/pg12_2.jpg)

![image](images/snake.jpg)

If installing PHP for Abyss on Windows from **[php.net](http://www.php.net)**, be sure to choose the VC6 Thread Safe version – as it requires fewer Windows dependencies.

![image](images/4b.jpg)Accept the suggested location of **C:\\Program Files\\PHP7**, then click the Install button to continue

![image](images/pg13_1.jpg)

![image](images/5b.jpg)Finally, after the installation completes, click on the Finish button to close the Setup Wizard

![image](images/pg13_2.jpg)

![image](images/hot.jpg)

The PHP installation location will be required when configuring the Abyss Web Server for PHP – make a note of the Destination Folder.

![image](images/forget.jpg)

Following installation of PHP, the web server cannot yet execute PHP scripts until it is configured to recognize them and to find the PHP interpreter engine – all as described [here on pages 14-15](#chapter01.html#sec5).

**Configuring Abyss for PHP**

The Abyss Web Server must be configured to recognize PHP scripts and employ the PHP interpreter when it encounters them. This is achieved in the Abyss server console by associating the file extension “.php” as being PHP scripts, and by specifying the location of the PHP engine on your system to interpret them.

![image](images/pg14_1.jpg)

Further guidance on configuration of the Abyss Web Server is available online at **[aprelium.com/abyssws/start.html](http://www.aprelium.com/abyssws/start.html)**

![image](images/1b.jpg)Enter **http://localhost:9999** into your browser address field (or click on the Abyss logo in your system tray) to launch the Abyss server console, then click the **Configure** button to open its Configuration page

![image](images/pg14_2.jpg)

![image](images/2b.jpg)Next, click on the ![image](images/pg14_3.jpg)Scripting Parameters icon to open the Scripting Parameters page for editing

![image](images/3b.jpg)Ensure that the **Enable Scripts Execution** box is checked, then click the **Add** button in the Interpreters table to open the Interpreters-Add page

![image](images/4b.jpg)Now, set the **Interface** to “FastCGI”, the **Interpreter** to the location of the PHP interpreter (**php-cgi.exe**) on your system, and **Add** the file Extension “php” then click **OK**

![image](images/pg14_4.jpg)

![image](images/hot.jpg)

The **localhost** domain name is an alias for the IP address **127.0.0.1** – so the Abyss Web Server console can alternatively be addressed as **http://127.0.0.1:9999**.

![image](images/5b.jpg)Click **OK** in the Console window, then click the **Restart** button to apply the changes to the Abyss configuration

![image](images/pg15_1.jpg)

The Abyss Web Server should now be running on your system, correctly configured to recognize that documents having the .php file extension should be interpreted by the PHP engine. Configuration can now be tested by creating a simple PHP script for service to your web browser by Abyss.

![image](images/pg15_2.jpg)

phpinfo.php

![image](images/6b.jpg)Open a plain text editor and exactly type the script below

**<?php phpinfo() ?>**

![image](images/7b.jpg)Save the script as **phpinfo.php** in the Abyss document path directory, typically at **C:\\Abyss Web Server\\htdocs**

![image](images/8b.jpg)Exactly enter the location **http://localhost/phpinfo.php** into your web browser’s address field to see Abyss serve up a web page containing your PHP version information

![image](images/pg15_3.jpg)

![image](images/forget.jpg)

PHP scripts are case-sensitive so you must copy the listed script using lowercase characters only.

![image](images/snake.jpg)

Documents can only be interpreted by the PHP engine if served up by the web server using the HTTP protocol. You cannot simply open a PHP file in your browser directly. Always use the location **http://localhost/**.

**Embedding PHP script**

PHP script may be embedded within HTML documents – meaning PHP and HTML code can both happily co-exist in the same file. All embedded PHP code must be contained within **<?php** and **?>** tags so it can be readily recognized by the PHP engine for interpretation. Typically, the PHP code will write content into the body section of the HTML document, which is then sent to the web browser.

![image](images/pg16_1.jpg)

hello.php

![image](images/1b.jpg)Launch a plain text editor and create this valid barebones HTML5 document with an empty body section

**<!DOCTYPE HTML>**

**<html lang=“en”>**

**<head><meta charset=”UTF-8”>**

**<title>Getting Started With PHP</title>**

**</head>**

**<body>**

**</body>**

**</html>**

![image](images/2b.jpg)Insert tags into the body section to contain PHP code

**<?php**

**?>**

![image](images/3b.jpg)Now, insert between the PHP tags a descriptive comment and a line of code to write content into the body section

**\# Write the traditional greeting.**

**echo ‘<h1>Hello World!</h1>’ ;**

![image](images/pg16_2.jpg)

![image](images/hot.jpg)

All whitespace and PHP comments are ignored by the interpreter. Single-line comments may begin with **#** or **//** and multi-line comments contained between **/\*** and **\*/** – as with the C programming language.

![image](images/4b.jpg)Set the document encoding to UTF-8 format then save it as **hello.php** in the Abyss server’s **/htdocs** folder

![image](images/pg17_1.jpg)

![image](images/5b.jpg)Next, enter the location **http://localhost/hello.php** into your web browser’s address field to see Abyss serve up a web page containing content written by embedded PHP code

![image](images/pg17_2.jpg)

![image](images/6b.jpg)Now, use your web browser’s View Source facility to see that PHP has written the content into the body section, including the HTML **<h1></h1>** heading tags

![image](images/pg17_3.jpg)

PHP script can be embedded in earlier versions of HTML in just the same way. Other examples in this book demonstrate embedded PHP script but do not repeatedly list the HTML code.

![image](images/snake.jpg)

Windows’ Notepad automatically adds a hidden “Byte Order Mark” (BOM) to the file, while other editors (such as Notepad++ shown here) allow this to be omitted. Notepad++ can be freely downloaded from [notepad-plus-plus.org](http://www.notepad-plus-plus.org)

![image](images/forget.jpg)

The PHP **echo** instruction statement literally writes the entire content contained within the pair of **‘** single quote marks. Like all other PHP statements it must be terminated by a ; semi-colon character.

**Installing the MySQL Server**

The MySQL database server, which provides “back-end” storage for data-driven websites, is available for Windows, macOS/Mac OS X, and Linux operating systems as a free download at **[mysql.com](http://www.mysql.com)**

![image](images/mysql.jpg)

Further guidance on installation of the MySQL Server is available at [http://dev.mysql.com/doc/refman/8.0/en/installing.html](https://dev.mysql.com/doc/refman/8.0/en/installing.html)

![image](images/1b.jpg)Download the MySQL Community Edition Server installer for your system from **[mysql.com/downloads/mysql](http://www.mysql.com/downloads/mysql)**

![image](images/pg18_1.jpg)

![image](images/2b.jpg)Run the installer and accept the License terms, then select “Server only” and click **Next** to continue

![image](images/pg18_2.jpg)

![image](images/3b.jpg)Click the **Execute** button to install the MySQL server

![image](images/pg18_4.jpg)

![image](images/hot.jpg)

![image](images/pg18_3.jpg)

The MySQL Installer can be launched at any time from the Windows Start menu – to change the configuration or to install updates.

![image](images/4b.jpg)Next, choose the “Standalone MySQL Server” option, then click **Next** to continue

![image](images/5b.jpg)Select “Development Computer” as the server configuration type, then click **Next** to continue

![image](images/pg19_1.jpg)

![image](images/6b.jpg)Select “Use Strong Password Encryption for Authentication”, then click **Next** to continue

![image](images/7b.jpg)Enter a root user password of your choice twice into the **Password** fields, then click **Next** to continue

![image](images/pg19_2.jpg)

![image](images/8b.jpg)Click **Next** to run as a Windows Service, and **Next** to ignore Plugins, then click the **Execute** button to install the MySQL Server with your selected configuration

![image](images/pg19_3.jpg)

![image](images/snake.jpg)

By default, the MySQL Server uses port 3306. If you are running a firewall you may need to specifically allow the MySQL Server connections via this port. Refer to your firewall documentation for further guidance.

![image](images/hot.jpg)

Write down your chosen root user password, username, and user password – you will need them often.

![image](images/hot.jpg)

Ensure that your MySQL Server Configuration completes successfully before continuing. If necessary, repeat the installation process.

**Using the MySQL Client**

After installation of the MySQL Server as a Windows service, described [here on pages 18-19](#chapter01.html#sec7), you can communicate with databases via the MySQL Command Line Client that gets installed with the server package. Upon its launch it will first request the root user password you chose during installation. Once the password has been verified, the MySQL Command Line Client then presents a **mysql>** command prompt from which you can create and manipulate databases.

![image](images/1b.jpg)Launch the MySQL Command Line Client from the MySQL group that has been added to the Start menu, then enter the root password you chose during installation

![image](images/pg20_1.jpg)

![image](images/2b.jpg)At the **mysql>** command prompt, precisely issue this command to create a new database named “site\_db”

**CREATE DATABASE IF NOT EXISTS site\_db ;**

![image](images/3b.jpg)Now, precisely issue a further command to display all databases that now exist on your MySQL Server

**SHOW DATABASES ;**

![image](images/pg20_2.jpg)

![image](images/hot.jpg)

The MySQL Command Line Client can also be launched from a regular Command prompt by issuing the command **mysql -u root -p** where **mysql** is added to your system Path, or from within its /**bin** directory.

![image](images/snake.jpg)

All MySQL commands end with a ; semi-colon.

![image](images/forget.jpg)

Installation creates some default databases, such as “sys”, but your “site\_db” database is the one that will be used throughout this book.

**Creating MySQL users**

While the MySQL root user is allowed complete control over the databases on the MySQL Server, it is obviously inadvisable to allow other users such freedom for best security of the databases. The root user can therefore create users with specific “privileges” controlling what actions they may perform on the MySQL Server.

The root user can create a user in the MySQL Command Line Client by issuing a clause to identify a unique user, like this:

**CREATE USER IF NOT EXISTS *‘username’*@*’hostname’***

**IDENTIFIED WITH mysql\_native\_password BY *‘password’* ;**

The root user can then issue a clause to specify privileges allowed for a particular database to a particular user, like this:

**GRANT *privileges* ON database.\* TO *‘username’*@*‘hostname’* ;**

The privileges are specified as a comma-separated list of keywords which that user may use when accessing the specified database. For instance, basic privileges to **SELECT**, **INSERT**, and **UPDATE**.

![image](images/1b.jpg)Log into the MySQL Command Line Client as the root user, then precisely issue this clause to create a user

**CREATE USER IF NOT EXISTS ‘mike’@’locahost’**

**IDENTIFIED WITH mysql\_native\_password BY ‘easysteps’ ;**

![image](images/2b.jpg)Next, allow privileges to access the “site\_db” database

**GRANT SELECT, INSERT, UPDATE ON site\_db.\***

**TO ‘mike’@‘localhost’ ;**

![image](images/3b.jpg)Now, issue a clause to confirm this user’s privileges

**SHOW GRANTS FOR ‘mike’@’localhost’ ;**

![image](images/pg21_1.jpg)

![image](images/snake.jpg)

MySQL is case-sensitive and requires precise syntax – you must be sure to use correct spacing and letter case as it appears listed. For example, do not leave spaces around the @ character that defines the user name and host.

![image](images/new.jpg)

MySQL 8 introduces **caching\_sha2\_password** authentication, but the **mysql\_native\_password** earlier authentication can still be used to specify unencrypted passwords.

**Connecting PHP & MySQL**

Connection to a MySQL database can be attempted in PHP with a standard piece of script that describes four connection parameters of Host, Username, Password, and Database name. Upon failure, the script provides a descriptive message, whereas on success it specifies the character set to be used when sending data to and from the database server:

**$dbc = mysqli\_connect ( *‘host’, ‘user’, ‘password’, ‘database’* )**

**OR die ( mysqli\_connect\_error() ) ;**

**mysqli\_set\_charset( $dbc, *‘charset’* ) ;**

You need not understand in detail how the script works at this stage, but recognize that it contains sensitive information. For this reason it should not be placed in the web server’s /**htdocs** directory like all other PHP scripts, where its contents may be accessible, but placed instead safely in /**htdocs** parent directory – for example, in the **“C:/Abyss Web Server”** directory rather than in the **“C:/Abyss Web Server/htdocs”** directory.

Any PHP script can incorporate another PHP script by using a “require” statement to specify the other script’s path. This feature can be used to good effect to incorporate the connection script without revealing its sensitive information.

![image](images/pg22_1.jpg)

connect\_db.php

![image](images/1b.jpg)Launch a plain text editor and create a connection script describing the parameters from the previous pages

**<?php**

**\# Connect on ‘localhost’ for user ‘mike’**

**\# with password ‘easysteps’ to database ‘site\_db’.**

**$dbc \= mysqli\_connect**

**( ‘localhost’ , ‘mike’ , ‘easysteps’ , ‘site\_db’ )**

**OR die**

**( mysqli\_connect\_error() ) ;**

**\# Set encoding to match PHP script encoding.**

**mysqli\_set\_charset( $dbc , ‘utf8’ ) ;**

![image](images/2b.jpg)Save the file in the parent directory of your web server’s **/htdocs** directory folder as **connect\_db.php**

![image](images/pg23_1.jpg)

require.php

![image](images/3b.jpg)Now, begin a second script that incorporates the connection script, stating its path in the parent directory

**<?php**

**\# Incorporate the MySQL connection script.**

**require ( ‘../connect\_db.php’ ) ;**

![image](images/4b.jpg)Next, complete this script by adding instructions to display connection information if the attempt has succeeded

**\# Display MySQL version and host.**

**if( mysqli\_ping( $dbc ) )**

**{ echo ‘MySQL Server ‘ . mysqli\_get\_server\_info( $dbc ).**

**’connected on ‘ . mysqli\_get\_host\_info( $dbc ) ; }**

![image](images/5b.jpg)Save the script in your web server’s **/htdocs** directory as **require.php**, then open it in your browser (via HTTP) to see the connection details on successful connection

![image](images/pg23_2.jpg)

![image](images/6b.jpg)Temporarily edit **connect\_db.php** by changing the database name to one that does not exist, then save the file and reload the page in your browser to see the error

![image](images/pg23_3.jpg)

![image](images/7b.jpg)Finally, correct the **connect\_db.php** script by changing the database name back to **site\_db**, then save the file and reload the page to see the connection succeed once more

Congratulations, you have now successfully configured the Abyss Web Server, PHP engine, and MySQL Server for development.

![image](images/forget.jpg)

You do not need to understand how these scripts work just now – they merely ensure you can connect to MySQL with PHP. But you can usefully refer back to them later to see how your knowledge of PHP has progressed.

**Summary**

•PHP is a scripting language that is especially suited for web development, as it can be embedded in HTML.

•MySQL is Relational DataBase Management Software (RDBMS) that can provide back-end data storage for websites.

•PHP and MySQL are both server-side technologies that deliver data-driven websites to the browser from The Cloud.

•A local development environment can be created by installing a Web Server, the PHP engine, and the MySQL Server.

•The Web Server must be configured to recognize scripts so it will direct them to the PHP engine for interpretation.

•All embedded PHP code must be contained within **<?php** and **?>** tags so it can be readily recognized by the PHP engine.

•Documents containing PHP script can best be encoded using the popular UTF-8 character format.

•The MySQL Server can be installed on Windows systems as a background service so it is always readily available.

•The MySQL Command Line Client gets installed with the Server package and can create and manipulate databases.

•The root user password chosen during installation of MySQL can be used to launch the MySQL Command Line Client.

•Connection to a MySQL database can be attempted in PHP with a standard piece of script that describes connection parameters of Host, Username, Password, and Database name.

•Any PHP script can incorporate another PHP script by using a require statement stating the other script’s path.

2

Performing operations

***This chapter demonstrates how to store and manipulate data using PHP operators.***

[**Creating variables**](#chapter02.html#sec12)

[**Managing strings**](#chapter02.html#sec13)

[**Producing arrays**](#chapter02.html#sec14)

[**Sorting arrays**](#chapter02.html#sec15)

[**Describing dimensions**](#chapter02.html#sec16)

[**Doing arithmetic**](#chapter02.html#sec17)

[**Comparing values**](#chapter02.html#sec18)

[**Assessing logic**](#chapter02.html#sec19)

[**Defining constants**](#chapter02.html#sec20)

[**Summary**](#chapter02.html#sec21)

**Creating variables**

A “variable” is a named container in a PHP script in which a data value can be stored. The stored value can be referenced using the variable’s name and changed (varied) as the script proceeds. The script author can choose any name for a variable providing it adheres to these three naming conventions:

•Names must begin with a $ dollar sign – for example $name.

•Names can comprise letters, numbers, and underscore characters, but not spaces – for example $subtotal\_1.

•The first character after the $ dollar sign must be a letter or an underscore character – it cannot be a number.

Note that variable names in PHP are case-sensitive so $name, $Name, and $NAME are three separate individual variables.

PHP variables are “loosely typed” meaning they can contain data of any type, unlike “strongly typed” variables in some languages where the data type must be specified when the variable is created. So, a PHP variable may happily contain an integer number, or a floating-point number, or a string of text characters, or a Boolean value of **TRUE** or FALSE, or an object, or a **NULL** empty value.

A variable is created in a PHP script simply by stating its name. The variable can then be assigned an initial value (initialized) by using the = assignment operator to state its value. This statement, and all others in PHP, must end with a semi-colon, like this:

**$body\_temp = 98.6 ;**

The value contained within the variable can then be displayed by referencing it using the variable name, like this:

**echo $body\_temp ;**

Usefully, the variable’s value can be displayed as part of a mixed string by enclosing the string and variable name in double quotes:

**echo “Body temperature is $body\_temp degrees Fahrenheit” ;**

The double quotes ensure that PHP will evaluate the whole string and substitute named variables with their stored values. This feature does not work if the string is enclosed in single quotes!

![image](images/snake.jpg)

Do not confuse the purpose of double and single quotes. Remember that PHP only makes variable substitutions for mixed strings enclosed within double quotes.

![image](images/1r.jpg)Create a valid HTML document, like the one listed [here on page 16](#chapter01.html#sec6), then insert PHP tags into the body section

**<?php**

**\# Statements to be inserted here.**

**?>**

![image](images/pg27_1.jpg)

variable.php

![image](images/2r.jpg)Now, between the PHP tags insert a statement to create and initialize a variable

**$body\_temp \= 98.6 ;**

![image](images/3r.jpg)Next, insert a statement to display the variable value alone

**echo $body\_temp ;**

![image](images/4r.jpg)Then, insert a statement to display the variable value substituted in a mixed string – assigned in double quotes

**echo “<p>Body temperature is $body\_temp**

**degrees Fahrenheit ” ;**

![image](images/5r.jpg)Insert a statement to assign a new value to the variable

**$body\_temp \= 37.0 ;**

![image](images/6r.jpg)Finally, insert a statement to display the new variable value substituted in a mixed string

**echo “( $body\_temp degrees Celsius )</p>” ;**

![image](images/7r.jpg)Save the document in your web browser’s **/htdocs** directory as **variable.php**, then open the page via HTTP to see the variable values get displayed

![image](images/pg27_2.jpg)

![image](images/hot.jpg)

Notice that variables created in the main body of a script, like the one in this example, are accessible “globally” throughout the entire PHP script.

![image](images/forget.jpg)

Each statement in the PHP language must be terminated by a semi-colon – just as each statement in the English language must be terminated by a period.

**Managing strings**

A “string” of text can be stored in a variable in much the same way as a numeric value, but the assignment must surround the string with quote marks to denote its beginning and end. Both single and double quote marks can be used for this purpose but you must use the same type of quote marks to denote the beginning and end of the text string. For example, both of these statements make valid string assignments:

**$song\_title = “Summertime Blues” ;**

**$song\_title = ‘Summertime Blues’ ;**

Where you wish to store a string of text that itself includes quote marks, you can “escape” the included quote marks by preceding them with a **\\** backslash character, or use the alternative type of quote mark within the string. For example, both of these statements assign strings that include quote marks:

**$song\_title = “the \\”Summertime\\” aria by George Gershwin” ;**

**$song\_title = ‘the “Summertime” aria by George Gershwin’ ;**

The second technique, using double quote marks within the string, is easier to read and is preferred throughout this book.

String values can be displayed as part of a mixed string by enclosing the mixed string in double quotes, like this:

**echo “Many regard $song\_title as a popular classic” ;**

The double quotes ensure that PHP will evaluate the mixed string and substitute named variables with their stored values. This feature does not work if the string is enclosed in single quotes!

String values can be joined together (“concatenated”) into a single string using the . period concatenation operator, like this:

**$hi = ‘Hello’ ;**

**$bye = ‘Goodbye’ ;**

**$song\_title = $hi . $bye ; # ‘HelloGoodbye’**

Additionally, spaces and punctuation can usefully be inserted when concatenating strings, so the title assignment above could be modified to include a comma and a space:

**$song\_title = $hi . ‘, ‘ . $bye ; # ‘Hello, Goodbye’**

![image](images/forget.jpg)

Variable names cannot contain spaces – but the underscore character is often used in their place.

![image](images/1r.jpg)Create a valid HTML document, like the one listed [here on page 16](#chapter01.html#sec6), then insert PHP tags into the body section

**<?php**

**\# Statements to be inserted here.**

**?>**

![image](images/pg29_1.jpg)

string.php

![image](images/2r.jpg)Now, between the PHP tags insert a statement to create and initialize two variables

**$phrase \= ‘The truth is rarely pure’ ;**

**$author \= ‘Oscar Wilde’ ;**

![image](images/3r.jpg)Next, insert a statement to display a variable value alone

**echo $phrase ;**

![image](images/4r.jpg)Then, insert a statement to display the variable value substituted in a mixed string – assigned in double quotes

**echo “<p>It is often said that <q>$phrase</q> </p>” ;**

![image](images/5r.jpg)Insert a statement to concatenate a string to a variable

**$phrase \= $phrase . ‘ and never simple’ ;**

![image](images/6r.jpg)Finally, insert a statement to display both current variable values substituted in a mixed string

**echo “<p><q>$phrase</q><cite>$author</cite></p>” ;**

![image](images/7r.jpg)Save the document in your web browser’s **/htdocs** directory as **string.php**, then open the page via HTTP to see the variable values get displayed

![image](images/pg29_2.jpg)

![image](images/hot.jpg)

You can also use a shorthand concatenate assignment operator **.=** to join two strings – so that **$a = $a . $b** can be simply written **$a .= $b**.

![image](images/hot.jpg)

Adopt a consistent naming style for your variables – such as all lowercase **$my\_var**, or “camelcase” **$myVar**.

**Producing arrays**

An array variable can store multiple items of data in sequential array “elements” that are numbered (“indexed”) starting at zero. So, the first array value is stored in array element number zero. Individual array element values can be referenced using the variable name followed by the index number in square brackets. For example, **$months\[0\]** references the value stored in the first array element, **$months\[1\]** references the value stored in the second array element, and so on.

Variable arrays can be created by making multiple statements that assign values to successive elements, or by making a single statement using a PHP array() function to fill the elements:

**$months\[\] = ‘January’ ;**

**$months\[\] = ‘February’ ;**

**$months\[\] = ‘March’ ;**

**$months = array( ‘January’ , ‘February’ , ‘March’ ) ;**

Both create an array where the value stored in each element can be referenced using its index number, such as **$months\[0\]**.

When creating an array you can optionally specify a key name for each element that can be used to reference that element’s value:

**$months\[‘jan’\] = ‘January’ ;**

**$months\[‘feb’\] = ‘February’ ;**

**$months\[‘mar’\] = ‘March’ ;**

**$months =**

**array( ‘jan’ => ‘January’ , ‘feb’ => ‘February’ , ‘mar’ => ‘March’ ) ;**

Both create an array where the value stored in each element can be referenced using its key name, such as **$months\[‘jan’\]**.

All elements of an array can be accessed using a **foreach** loop to reference each element’s value in turn and assign it to a variable:

**foreach( $months as $value )**

**{**

**\# Use the current $value on each iteration.**

**}**

The keys can also be accessed on each iteration of the loop using

**foreach( $months as $key => $value )**

**{**

**\# Use the current $key and $value on each iteration.**

**}**

![image](images/forget.jpg)

Square brackets denote “element” so are not needed after the variable name in the assignment using the **array()** function – only when addressing an element.

![image](images/snake.jpg)

If you specify the same key name twice, the second value will overwrite the first value in that element.

![image](images/1r.jpg)Create a valid HTML document, like the one listed [here on page 16](#chapter01.html#sec6), then insert PHP tags into the body section

**<?php**

**\# Statements to be inserted here.**

**?>**

![image](images/pg31_1.jpg)

array.php

![image](images/2r.jpg)Now, between the PHP tags insert a statement to create and initialize a variable array with values

**$days \= array( ‘Monday’ , ‘Tuesday’ , ‘Wednesday’ ) ;**

![image](images/3r.jpg)Next, insert a statement to display the value in all array elements as a bulleted list

**foreach( $days as $value ) { echo “&bull; $value “ ; }**

![image](images/4r.jpg)Then, insert a statement to create and initialize a variable array with both keys and values

**$months \= array( ‘jan’ \=> ‘January’ ,**

**‘feb’ \=> ‘February’ , ‘mar’ \=> ‘March’ ) ;**

![image](images/5r.jpg)Finally, insert statements to display the key and value in all elements as a definition list

**echo ‘<dl>’ ;**

**foreach( $months as $key \=> $value )**

**{ echo “<dt>$key<dd>$value” ; }**

**echo ‘</dl>’ ;**

![image](images/6r.jpg)Save the document in your web browser’s /htdocs directory as array.php, then open the page via HTTP to see the variable array element values get displayed

![image](images/pg31_2.jpg)

![image](images/hot.jpg)

You can set the first element key to 1, so the index will begin at one rather than zero, using **$months = array( 1 => ‘January’ , ‘February’ , March’**);

![image](images/hot.jpg)

You can easily create arrays containing sequential numbers or letters with the PHP **range()** function. For example, with  
**$six = range( 1 , 6 ) ;**  
**$a\_z = range( ‘a’ , ‘z’ ) ;**

**Sorting arrays**

PHP provides two handy functions to convert between variable arrays and strings because they are so frequently used together. The implode() function converts an array to a string and inserts a specified separator between each value. Typically, this might be used to create a list of comma-separated values, like this:

**$csv\_list = implode( ‘ , ‘ , $array ) ;**

Conversely, the **explode()** function converts a string to an array by specifying a separator around which to break up the string. This might be used to create an array from a comma-separated list:

**$array = explode( ‘ , ‘ , $csv\_list ) ;**

PHP also provides three useful functions to sort array elements into ascending alphanumeric order (a-z 1-9):

•**sort()** function – sorts by value discarding the original key

•**asort()** function – sorts by value retaining the original key

•**ksort()** function – sorts by key

Existing array values are sorted with a simple statement, like this:

**$makers = array( ‘Ford’ , ‘Chevrolet’ , ‘Dodge’ ) ;**

**sort( $makers ) ;**

Array elements can also be sorted into descending alphanumeric order (9-1 z-a) with three similar functions:

•**rsort()** function – sorts by value discarding the original key

•**arsort()** function – sorts by value retaining the original key

•**krsort()** function – sorts by key

It is important to recognize that specified key names will be discarded by the **sort()** and **rsort()** functions so these should only be used where the key/value relationship is not significant – otherwise use the **asort()** and **arsort()** functions to retain the keys.

![image](images/hot.jpg)

You can test if a variable is an array using the **is\_array()** function. For example, **is\_array( $var ) ;**

![image](images/1r.jpg)Create a valid HTML document, like the one listed [here on page 16](#chapter01.html#sec6), then insert PHP tags into the body section

**<?php**

**\# Statements to be inserted here.**

**?>**

![image](images/pg33_1.jpg)

sort.php

![image](images/2r.jpg)Now, between the PHP tags insert a statement to create and initialize a variable array with key names and values

**$cars \= array( ‘Dodge’ \=> ‘Viper’ ,**

**‘Chevrolet’ \=> ‘Camaro’ , ‘Ford’ \=> ‘Mustang’ ) ;**

![image](images/3r.jpg)Next, insert statements to display all keys and values of the array as a bulleted list item within a definition list

**echo ‘<dl><dt>Original Element Order :<dd>’ ;**

**foreach( $cars as $key \=> $value )**

**{ echo ‘ &bull; ‘ , $key . ‘ ‘ . $value ; }**

![image](images/4r.jpg)Then, insert statements to display the array sorted by value

**asort( $cars ) ;**

**echo ‘<dt>Sorted Into Value Order :<dd>’ ;**

**foreach( $cars as $key \=> $value )**

**{ echo ‘ &bull; ‘ , $key . ‘ ‘ . $value ; }**

![image](images/5r.jpg)Finally, insert statements to display the array sorted by key

**ksort( $cars ) ;**

**echo ‘<dt>Sorted Into Key Order :<dd>’ ;**

**foreach( $cars as $key \=> $value )**

**{ echo ‘ &bull; ‘ , $key . ‘ ‘ . $value ; }**

**echo ‘</dl>’ ;**

![image](images/6r.jpg)Save the document in your web browser’s **/htdocs** directory as **sort.php**, then open the page via HTTP to see the sorted array values get displayed

![image](images/pg33_2.jpg)

![image](images/hot.jpg)

You can discover the number of elements in an array with a **count()** function. For example, **$num = count( $array ) ;**

![image](images/forget.jpg)

Do not use the **sort()** or **rsort()** functions where the keys are important.

**Describing dimensions**

The numbering of array elements is more correctly known as the “array index” and, because element numbering starts at zero, is sometimes referred to as a “zero-based index”. An array created with a single index is a one-dimensional array in which the elements appear in a single row:

![image](images/pg34_1.jpg)

 
| Element content... || **A** || **B** || **C** || **D** || **E** |
| --- | --- | --- | --- | --- | --- |
| Index numbers... || \[0\] || \[1\] || \[2\] || \[3\] || \[4\] |

Arrays can also have multiple indices – to represent multiple dimensions. An array created with two indices is a two-dimensional array in which the elements appear in multiple rows:

 
| First index || \[0\] || **A** || **B** || **C** || **D** || **E** |
| --- | --- | --- | --- | --- | --- | --- |
|   || \[1\] || **F** || **G** || **H** || **I** || **J** |
| Second index ||   || \[0\] || \[1\] || \[2\] || \[3\] || \[4\] |

With multi-dimensional arrays the value contained in each element is referenced by stating the number of each index. For example, with the two dimensional array above, the element at \[1\] \[2\] contains the letter H.

Two-dimensional arrays are useful to store grid-based information, such as XY coordinates. Creating a three dimensional array, with three indices, would allow XYZ coordinates to be stored.

Creating a multi-dimensional array in PHP is simply a matter of creating an outer array whose elements are themselves arrays. As usual you may optionally specify a key name for each element – in this case to represent each inner array. Individual values can then be referenced using the key name and inner index number:

**$matrix\[‘Letter’\]\[0\]**

It is, however, necessary to always enclose array variables that use quoted keys within curly braces when included in a string:

**echo “Element value is {$matrix\[‘Letter’\]\[0\]} ” ;**

All inner arrays in a multi-dimensional array can be accessed using a **foreach** loop to iterate through the arrays. A nested **foreach** loop can then reference each element in turn.

![image](images/snake.jpg)

Multi-dimensional arrays with more than two indices can produce hard to read source code and may lead to errors.

![image](images/1r.jpg)Create a valid HTML document, like the one listed [here on page 16](#chapter01.html#sec6), then insert PHP tags into the body section

**<?php**

**\# Statements to be inserted here.**

**?>**

![image](images/pg35_1.jpg)

matrix.php

![image](images/2r.jpg)Now, between the PHP tags insert a statement to create and initialize two regular variable arrays and a two-dimensional array with key names

**$letters \= array( ‘A’ , ‘B’ , ‘C’ ) ;**

**$numbers \= array( 1 , 2 , 3 ) ;**

**$matrix \=**

**array( ‘Letter’ \=> $letters , ‘Number’ \=> $numbers ) ;**

![image](images/3r.jpg)Next, insert a statement to display a single stored value

**echo “<p>Start : {$matrix\[‘Letter’\]\[0\]} </p>” ;**

![image](images/4r.jpg)Finally, insert statements to display the key and value in all elements as two unordered lists

**foreach( $matrix as $array \=> $list )**

**{**

**echo ‘<ul>’ ;**

**foreach( $list as $key \=> $value )**

**{ echo “<li>$array \[ $key \] = $value” ; }**

**echo ‘</ul>’ ;**

**}**

![image](images/5r.jpg)Save the document in your web browser’s /htdocs directory as matrix.php, then open the page via HTTP to see the variable array values get displayed

![image](images/pg35_2.jpg)

![image](images/hot.jpg)

Multi-dimensional arrays are more common than you might think. For example, an HTML form that allows multiple selections for inputs with the same name are submitted as a multi-dimensional array.

![image](images/forget.jpg)

Array variables that use quoted keys must be enclosed within curly braces when included in a string.

**Doing arithmetic**

The arithmetic operators commonly used in PHP scripts are listed in the table below, together with the operation they perform:

 
| **Operator:** || **Operation:** |
| --- | --- |
| **+** || Addition |
| **\-** || Subtraction |
| **\*** || Multiplication |
| **/** || Division |
| **%** || Modulus |
| **++** || Increment |
| **\--** || Decrement |

Operators for addition, subtraction, multiplication, and division act as you would expect. Care must be taken, however, to group expressions for clarity where more than one operator is used:

**a = b \* c -d % e / f ; # This is unclear.**

**a = ( b \* c ) - ( ( d % e ) / f ) ; # This is clearer.**

The % modulus operator divides the first given number by the second given number and returns the remainder of the operation. This is useful to determine if a number has an odd or even value. The ++ increment operator and -- decrement operator alter the given number by one and return the resulting new value. These are most often used to count iterations in a loop and may be placed before the operand (“prefix”) or after the operand (“postfix”). The increment operator increases the value by one, and the decrement operator decreases the value by one. Shorthand expressions can usefully be created by combining an arithmetic operator with the = assignment operator. For example:

**a += b ; # Equivalent to a = ( a + b ) ;**

**a -= b ; # Equivalent to a = ( a - b ) ;**

**a \*= b ; # Equivalent to a = ( a \* b ) ;**

**a /= b ; # Equivalent to a = ( a / b ) ;**

![image](images/hot.jpg)

The numbers used along with operators to form expressions are known as “operands” – in the expression **2 + 3** the numbers **2** and **3** are the operands.

![image](images/forget.jpg)

Group expressions with parentheses to specify evaluation precedence – innermost groups get evaluated first.

![image](images/1r.jpg)Create a valid HTML document, like the one listed [here on page 16](#chapter01.html#sec6), then insert PHP tags into the body section

**<?php**

**\# Statements to be inserted here.**

**?>**

![image](images/pg37_1.jpg)

arithmetic.php

![image](images/2r.jpg)Now, between the PHP tags insert statements to create and initialize two variables

**$a \= 4 ;**

**$b \= 8 ;**

![image](images/3r.jpg)Next, insert statements to display the results of arithmetical operations using the variable values

**$result \= $a + $b ; echo “Addition : $result <br>” ;**

**$result \= $b \- $a ; echo “Subtraction : $result <br>” ;**

**$result \= $a \* $b ; echo “Multiplication : $result <br>” ;**

**$result \= $b / $a ; echo “Division : $result <br>” ;**

**$result \= $a % $b ; echo “Modulo : $result <br>” ;**

![image](images/4r.jpg)Finally, insert statements to increment and decrement the values stored in the variables

**$a++ ; echo “Increment : $a <br>” ;**

**$b\-- ; echo “Decrement : $b <br>” ;**

![image](images/5r.jpg)Save the document in your web browser’s **/htdocs** directory as **arithmetic.php**, then open the page via HTTP to see the results and variable values get displayed

![image](images/pg37_2.jpg)

![image](images/hot.jpg)

PHP has some useful functions to work with numbers. For example, **round($n)** rounds **$n** to the nearest integer, and **number\_format($n)** adds commas to **$n** denoting groups of thousands.

![image](images/snake.jpg)

Notice that the variable value is immediately increased only with the prefix increment operator – with the postfix operator it is incremented the next time it is referenced.

**Comparing values**

The operators that are commonly used in PHP scripts to compare two values are listed in the table below:

 
| **Opertor:** || **Comparative test:** |
| --- | --- |
| **\==** || Equality |
| **!=** || Inequality |
| **\>** || Greater than |
| **<** || Less than |
| **\>=** || Greater than or equal to |
| **<=** || Less than or equal to |
| **?:** || TRUE or FALSE |

The **\==** equality operator compares two operands and returns a Boolean **TRUE** result if both are numerically equal in value, otherwise it returns **FALSE**. Characters and strings are also compared numerically by their ASCII code value. Conversely, the **!=** inequality operator returns **TRUE** if the two operands are not equal, otherwise it returns **FALSE**.

The **\>** “greater than” operator compares two operands and returns **TRUE** if the first is greater in value than the second, or it returns **FALSE** if it is equal or less in value. The **<** “less than” operator makes the same comparison but returns **TRUE** if the first operand is less in value than the second, otherwise it returns FALSE. Adding the **\=** operator after a **\>** “greater than” or **<** “less than” operator makes it also return **TRUE** when the two operands are exactly equal.

The **?:** ternary operator evaluates an expression for a **TRUE** or **FALSE** Boolean value, then executes one of two statements depending on the result of the evaluation. An appropriate returned value can be assigned to a variable using this syntax:

**$var = ( *expression* ) ? *if-TRUE-return-this* : *if-FALSE-return this* ;**

![image](images/hot.jpg)

Equality and inequality operators are useful in testing the state of two variables to perform conditional branching in a PHP script.

![image](images/1r.jpg)Create a valid HTML document, like the one listed [here on page 16](#chapter01.html#sec6), then insert PHP tags into the body section

**<?php**

\# Statements to be inserted here.

**?>**

![image](images/pg39_1.jpg)

comparison.php

![image](images/2r.jpg)Now, between the PHP tags insert statements to create and initialize five variables

**$zero \= 0 ; $nil \= 0 ; $one \= 1 ; $upr \= ‘A’ ; $lwr \= ‘a’ ;**

![image](images/3r.jpg)Next, insert statements to display equality comparisons

**$result \= ( $zero \== $nil ) ? ‘TRUE’ : ‘FALSE’**

**echo “0 == 0 is $result <br>” ;**

**$result \= ( $zero \== $one ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “0 == 1 is : $result <br>” ;**

**$result \= ( $upr \== $lwr ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “A == a is $result <br>” ;**

**$result \= ( $upr != $lwr ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “A != a is $result <hr>” ;**

![image](images/4r.jpg)Finally, insert statements to display greater comparisons

**$result \= ( $one \> $nil ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “1 > 0 is $result <br>” ;**

**$result \= ( $zero \>= $nil ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “0 >= 0 is $result <br>” ;**

**$result \= ( $one <= $nil ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “1 <= 0 is $result <br>” ;**

![image](images/5r.jpg)Save the document in your web browser’s **/htdocs** directory as **comparison.php**, then open the page via HTTP to see the results get displayed

![image](images/pg39_2.jpg)

![image](images/hot.jpg)

A Boolean **TRUE** value is represented numerically by 1 in the PHP language.

![image](images/hot.jpg)

The ASCII code value for uppercase **‘A’** is 65, and for lowercase **‘a’** it’s 97 – so their comparison here returns **FALSE**.

**Assessing logic**

The logical operators most commonly used in PHP scripts are listed in the table below:

 
| **Operator:** || **Operation:** |
| --- | --- |
| **&&** || Logical AND |
| **AND** || Logical AND ( alternative form of **&&** ) |
| **||** || Logical OR |
| **OR** || Logical OR ( alternative form of **||** ) |
| **!** || Logical NOT |

The logical operators are used with operands that have the Boolean values of **TRUE** or **FALSE**, or an expression that can convert to **TRUE** or **FALSE**.

The logical **&&** AND operator will evaluate two operands and return **TRUE** only if both operands are themselves **TRUE**. Otherwise, the **&&** AND operator will return **FALSE**. This is used in conditional branching where the direction of a PHP script is determined by testing two conditions. If both conditions are satisfied, the program will go in a certain direction, otherwise it will take a different direction.

Unlike the **&&** AND operator that needs both operands to be **TRUE**, the **||** OR operator will evaluate two operands and return **TRUE** if either one of the operands is itself **TRUE**. If neither operand is **TRUE**, then the **||** OR operator will return **FALSE**. This is useful in PHP scripts to perform a certain action if either one of two test conditions has been met.

The third logical **!** NOT operator is a “unary” operator – that is used before a single operand. It returns the inverse value of the given operand, so if the variable **$var** is a **TRUE** value then **! $var** would return a **FALSE** value. The **!** NOT operator is useful in PHP scripts to toggle the value of a variable in successive loop iterations with a statement like $**var = ! $var**. This ensures that on each pass the value is reversed, like flicking a light switch on and off.

![image](images/hot.jpg)

The term “Boolean” refers to a system of logical thought developed by the English mathematician George Boole (1815-1864).

![image](images/1r.jpg)Create a valid HTML document, like the one listed [here on page 16](#chapter01.html#sec6), then insert PHP tags into the body section

**<?php**

**\# Statements to be inserted here.**

**?>**

![image](images/pg41_1.jpg)

logic.php

![image](images/2r.jpg)Now, between the PHP tags insert statements to create and initialize two variables

**$yes \= TRUE ; $no \= FALSE ;**

![image](images/3r.jpg)Next, insert statements to display AND evaluations

**$result \= ( $no && $no ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “No AND No returns $result <br>” ;**

**$result \= ( $yes && $no ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “Yes AND No returns : $result <br>” ;**

**$result \= ( $yes && $yes ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “Yes AND Yes returns $result <hr>” ;**

![image](images/4r.jpg)Insert statements to display OR and NOT evaluations

**$result \= ( $no || $no ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “No OR No returns $result <br>” ;**

**$result \= ( $yes || $no ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “Yes OR No returns $result <br>” ;**

**$result \= ( $yes || $yes ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “Yes OR Yes returns $result <hr>” ;**

**$result \= ( ! $yes ) ? ‘TRUE’ : ‘FALSE’ ;**

**echo “NOT Yes returns $result <br>” ;**

![image](images/5r.jpg)Save the document in your web browser’s **/htdocs** directory as **logic.php**, then open the page via HTTP to see the results get displayed

![image](images/pg41_2.jpg)

![image](images/hot.jpg)

PHP also has an **XOR** (exclusive **OR**) operator, which returns **TRUE** if either of its operands are **TRUE**, but it returns **FALSE** if both its operands are **TRUE**.

![image](images/forget.jpg)

Notice that evaluation of **FALSE && FALSE** returns **FALSE** – demonstrating the anecdote “two wrongs don’t make a right”.

**Defining constants**

Where a script is required to use a fixed data value that will never change, it should be stored in a PHP “constant” rather than in a variable. A constant is a named container in a PHP script in which a data value can be stored, and can be referenced usingthe constant’s name. Unlike a variable, the stored value cannot be changed as the script proceeds. This safeguards the constant value from accidental alteration, and is good programming practice.

Constant names are subject to the same naming conventions as variable names, described [here on page 26](#chapter02.html#sec12), but it is traditional to use uppercase characters for constant names – to easily distinguish them from variable names when reading the source code. More significantly, constant names are not prefixed by a $ dollar sign.

PHP constants are not created in the same way as PHP variables. Instead, you must use a **define()** function to specify the constant’s name and the value it will contain, with this syntax:

**define( *‘NAME’* , *value* ) ;**

A constant can only contain alphanumeric values (character strings, integer and floating-point numbers), so they may not contain Boolean values of **TRUE** or **FALSE**, nor represent an object or a **NULL** empty value.

Although constant values can be accessed just like variable values, using their name to reference the value they contain, constants cannot be included in mixed strings for display – as the PHP interpreter cannot distinguish a constant name from a regular capitalized string of text. For example:

**define( ‘USER’ , ‘Mike’ ) ;**

**echo “Hello USER” ; # Displays: Hello USER**

So the constant value must be referenced separately with

**echo ‘Hello ‘ ;**

**echo USER ;**

or by concatenating the referenced value to the string, like this:

**echo ‘Hello ‘ . USER ;**

Constants defined by the script author can be used just like the predefined constants that are built into PHP, such as **PHP\_VERSION** and **PHP\_OS** that describe the version and server operating system.

![image](images/hot.jpg)

When creating a variable always consider whether its value will ever change – if not, you should create a constant instead. For example, **define( ‘PI’ , 3.14 ) ;**

![image](images/1r.jpg)Create a valid HTML document, like the one listed [here on page 16](#chapter01.html#sec6), then insert PHP tags into the body section

**<?php**

**\# Statements to be inserted here.**

**?>**

![image](images/pg43_1.jpg)

constant.php

![image](images/2r.jpg)Now, between the PHP tags insert a statement to create and initialize a constant

**define( ‘USER’ , ‘Mike’ ) ;**

![image](images/3r.jpg)Next, insert a statement to display the constant value in a concatenated string

**echo ‘<p>Hello ‘ . USER . ‘</p>’ ;**

![image](images/4r.jpg)Insert a statement to display the predefined constant value of the PHP version in a concatenated string

**echo ‘<p>You are using PHP version ‘ . PHP\_VERSION ;**

![image](images/5r.jpg)Finally, insert a statement to display the predefined constant value of the host operating system in a string

**echo ‘ running on ‘ . PHP\_OS . ‘</p>’ ;**

![image](images/6r.jpg)Save the document in your web browser’s **/htdocs** directory as **constant.php**, then open the page via HTTP to see the results get displayed

![image](images/pg43_2.jpg)

![image](images/snake.jpg)

You cannot include constants in mixed strings or change their value or begin their name with a dollar sign.

![image](images/forget.jpg)

You should always use uppercase for constant names to easily differentiate them from variables in your code.

**Summary**

•In PHP a variable is a named container in which a changeable data value can be stored, and a constant is a named container in which a fixed data value can be stored.

•The value stored in a variable or in a constant can be referenced using its name.

•Variable names must begin with a **$** dollar sign, may comprise letters, numbers, and underscore characters, and the first character after the **$** must only be a letter or an underscore.

•Constant names are not prefixed by a **$** and are all uppercase.

•A variable is initialized using the = assignment operator, whereas a constant is initialized using the **define()** function.

•A variable’s value can be displayed as part of a mixed string by enclosing the string and variable name in double quotes only.

•Strings may be enclosed in either single quotes or double quotes, and inner quote marks can be escaped using a backslash.

•String values can be joined together into a single string using the . period concatenation operator.

•An array variable can store multiple items of data in sequential array elements that are numbered starting at zero by default.

•Optionally, key names may be specified for each array element.

•A **foreach** loop can be used to access each element in an array.

•The **implode()** and **explode()** functions convert between strings and arrays by adding or removing specified separators.

•Arrays can be sorted into alphanumeric order by value or key.

•A multi-dimensional array is simply an array whose elements are themselves arrays.

•PHP has operators to perform arithmetic ( **\+ - \* / % ++ --** ) , comparison **( == != > < >= <= ?:** ) , and logic ( **&& || !** ).

3

Controlling progress

***This chapter demonstrates how to make PHP statements that evaluate expressions to determine how a script should proceed.***

[**Branching alternatives**](#chapter03.html#sec22)

[**Switching branches**](#chapter03.html#sec23)

[**Performing loops**](#chapter03.html#sec24)

[**Looping while true**](#chapter03.html#sec25)

[**Breaking from loops**](#chapter03.html#sec26)

[**Creating functions**](#chapter03.html#sec27)

[**Passing arguments**](#chapter03.html#sec28)

[**Returning values**](#chapter03.html#sec29)

[**Summary**](#chapter03.html#sec30)

**Branching alternatives**

The if keyword is used to perform the basic conditional test that evaluates a given expression for a Boolean value of TRUE or FALSE. Statements within braces following the evaluation will only be executed when the expression is found to be TRUE. So the syntax of an **if** test statement looks like this:

**if ( *test-expression* ) { *statements-to-execute-when-true* }**

There may be multiple statements to be executed when the test is TRUE, but each statement must be terminated by a semi-colon.

Multiple expressions can be tested using the logical && AND operator to ensure that following statements will only be executed when both expressions are found to be TRUE, like this:

**if ( ( *test-expression* ) && ( *test-expression* ) )**

**{ *statements-to-execute-when-true* }**

It is often preferable to extend an if statement by appending an else statement specifying statements within braces to be executed when the expressions evaluated by the if statement are found to be FALSE, with this syntax:

**if ( *test-expression* )**

**{ *statements-to-execute-when-true* }**

**else**

**{ *statements-to-execute-when-false* }**

Alternative expressions may also be evaluated in a conditional test by adding an elseif statement specifying statements within braces to be executed when the alternative expression is found to be TRUE. An else statement can be appended here too to specify statements within braces to be executed when the expressions evaluated by the if and elseif statements are found to be FALSE, with this syntax:

**if ( *test-expression* )**

**{ *statements-to-execute-when-true* }**

**elseif ( *test-expression* )**

***{ statements-to-execute-when-alternative-is-true }***

**else**

**{ *statements-to-execute-when-all-expressions-are-false* }**

This is a fundamental programming technique that offers the script different directions in which to proceed, depending on the result of the evaluations, and is known as “conditional branching”.

![image](images/hot.jpg)

When the code to be executed is just a single statement the braces may optionally be omitted.

![image](images/hot.jpg)

The **elseif** keyword can also be written as two separate words **else if.**

![image](images/pg47_1.jpg)

ifelse.php

![image](images/1g.jpg)Begin a PHP script with a statement that outputs a result only when a tested expression is found to be TRUE

**<?php**

**if ( 4 \> 2 ) { echo ‘<p>Yes, 4 is greater than 2 <br>’ ; }**

![image](images/2g.jpg)Next, add a statement that outputs a result only when two tested expressions are both found to be TRUE

**if ( ( 4 \> 2 ) && ( 8 \> 4 ) )**

**{ echo ‘4 is greater than 2 AND 8 is greater than 4<br>’ ; }**

![image](images/3g.jpg)Now, add a statement that outputs a result when a tested expression is found to be TRUE or FALSE

**if ( 4 \> 8 )**

**{ echo ‘4 is greater than 8 <br>’ ; }**

**else**

**{ echo ‘4 is less than 8 <br>’ ; }**

![image](images/4g.jpg)Finally, add a statement that outputs a result when either of two tested expressions are found to be TRUE, or when both tested expressions are found to be FALSE

**if ( 4 \> 8 )**

**{ echo ‘This test is True </p>’ ; }**

**elseif ( 8 \> 4 )**

**{ echo ‘Alternative test is True </p>’ ; }**

**else**

**{ echo ‘Both tests are False </p>’ ; } ?>**

![image](images/5g.jpg)Save the document in your web browser’s /htdocs directory as ifelse.php, then open the page via HTTP to see the results of conditional branching get displayed

![image](images/pg47_2.jpg)

![image](images/hot.jpg)

You can nest conditional if tests (one inside another) so that statements in the inner block only get executed when both tests are found to be **TRUE**.

**Switching branches**

Conditional branching performed by multiple if-elseif-else statements can often be performed more efficiently by a switch statement when the test expression just evaluates one condition.

The switch statement works in an unusual way. It takes a given value as its parameter argument then seeks to match that value from a number of case statements. Code to be executed when a match is found is included in each case statement.

It is important to end each case statement with a break keyword statement so the switch statement will then exit when a match is found without seeking further matches – unless that is the deliberate requirement.

Optionally, the list of case statements can be followed by a single final **default** statement to specify code to be executed in the event that no matches are found within any of the case statements. So the syntax of a switch statement typically looks like this:

**switch ( *test-value* )**

**{**

**case *match-value : statements-to-execute-when-matched* ; break** ;

**case *match-value : statements-to-execute-when-matched* ; break** ;

**case *match-value : statements-to-execute-when-matched* ; break** ;

**default : *statements-to-execute-when-no-match-found ;***

**}**

A switch statement can have many case statements but no two of its case statements can attempt to match the same value.

Where a number of match-values are to each execute the same statements, only the final case statement need include the statements to be executed and the **break** statement to exit the switch statement block. For example, to output the same message for match-values of 0, 1, and 2:

**switch ( $number )**

**{**

**case 0 :**

**case 1 :**

**case 2 : echo ‘Less than 3’ ; break ;**

**case 3 : echo ‘Exactly 3’ ; break ;**

**default : echo ‘Greater than 3 or less than zero’ ;**

**}**

![image](images/hot.jpg)

It’s always a good idea to include a **default** statement – even if it’s only to output an error message when the **switch** statement fails.

![image](images/forget.jpg)

A **default** statement need not appear at the end of the **switch** block but it is logical to place it there where it needs no **break** statement.

![image](images/pg49_1.jpg)

switch.php

![image](images/1g.jpg)Begin a PHP script with statements that create and initialize two variables with an integer and character value

**$number \= 2 ; $letter \= ‘B’ ;**

![image](images/2g.jpg)Next, add a switch statement that attempts to match the integer value

**switch ( $number )**

**{**

**case 1 : echo ‘Number is One<br>’ ; break ;**

**case 2 : echo ‘Number is Two<br>’ ; break ;**

**case 3 : echo ‘Number is Three<br>’ ; break ;**

**default : echo ‘Number is Unrecognized<br>’ ;**

**}**

![image](images/3g.jpg)Now, add a switch statement that attempts to match the character value

**switch ( $letter )**

**{**

**case ‘A’ : echo ‘Letter is A<br>’ ; break ;**

**case ‘B’ : echo ‘Letter is B<br>’ ; break ;**

**case ‘C’ : echo ‘Letter is C<br>’ ; break ;**

**default : echo ‘Letter is Unrecognized<br>’ ;**

**}**

![image](images/4g.jpg)Finally, add a switch statement to attempt to match against multiple integer values

**switch ( $number )**

**{**

**case 0 : case 1 : case 2 : echo ‘Less than 3<br>’ ; break ;**

**default : echo ‘3 or more, or less than zero’ ;**

**}**

![image](images/5g.jpg)Save the document in your web browser’s /htdocs directory as switch.php, then open the page via HTTP to see the results of conditional branching get displayed

![image](images/pg49_2.jpg)

![image](images/hot.jpg)

In **switch** statements the **case** keyword, match-value, and colon character are regarded as a unique “label”.

**Performing loops**

A loop is a piece of code in a script that automatically repeats. One complete execution of all statements within a loop is called an “iteration”, or a “pass”. The length of a loop is controlled by a conditional test made within the loop. While the tested expression is found to be TRUE, the loop will continue – until the tested expression is found to be FALSE, at which point the loop ends.

In PHP there are these four types of loop structure:

•for loop – performs a specified number of iterations.

•while loop – performs iterations only while a test made at the start of each iteration evaluates as TRUE.

•do while loop – performs iterations only while a test made at the end of each iteration evaluates as TRUE.

•foreach loop – performs iterations through each element of an array, as introduced [here on page 30](#chapter02.html#sec14).

Perhaps the most interesting loop structure is the for loop, which typically has this syntax:

**for ( *initializer ; test-expression ; incrementer* )**

**{ *statements-to-be-executed* }**

The initializer is used to set a starting value for a counter of the number of iterations made by the loop. An integer variable is used for this purpose, and is traditionally named “i”.

Upon each iteration of the loop the test-expression is evaluated, and that iteration will only continue while this expression is TRUE. When the test-expression becomes FALSE, the loop ends immediately without executing the statements again. With every iteration the counter is incremented then the statements executed.

Loops can be nested, one within another, to allow complete execution of all iterations of an inner nested loop on each iteration of the outer loop.

![image](images/pg51_1.jpg)

forloop.php

![image](images/1g.jpg)Begin a PHP script with a for loop to output the loop counter value in a list on each of three iterations

**for ( $i \= 1 ; $i < 4 ; $i++ )**

**{**

**echo “<dt>Outer loop iteration $i” ;**

**\# Nested loop to be inserted here.**

**}**

![image](images/2g.jpg)Save the document in your web browser’s /htdocs directory as forloop.php, then open the page via HTTP to see the loop counter values get displayed

![image](images/3g.jpg)Now, insert a nested for loop to output its loop counter value in a list on each of three iterations

**for ( $j \= 1 ; $j < 4 ; $j++ )**

**{**

**echo “<dd>Inner loop iteration $j” ;**

**}**

![image](images/4g.jpg)Save the document once more, then open the page via HTTP to see both loop counter values get displayed

![image](images/pg51_2.jpg)

![image](images/hot.jpg)

A **for** loop counter can also count down – by decrementing the counter value on each iteration using **i--** instead of **i++**.

**Looping while true**

A while loop is an alternative to the for loop described in the previous example. The while loop also requires an initializer, test-expression, and an incrementer, but these are not neatly listed within a single pair of parentheses as they are in a for loop. Instead, the initializer must appear before the start of the loop block, the test-expression must appear within parentheses after the while keyword, followed by braces containing both an incrementer and the statements to be executed on each iteration:

***initializer***

**while ( *test-expression* )**

**{ *statements-to-be-executed ; incrementer* }**

A do while loop provides a subtle variation on the syntax above by placing the do keyword before the loop block and moving the while statement to after the loop block:

***initializer***

**do { *statements-to-be-executed ; incrementer* }**

**while ( *test-expression* ) ;**

Both while loops and do while loops will proceed to make iterations until the test-expression is found to be FALSE, at which point the loop will exit. It is therefore essential that the loop body contains code that will, at some point, change the result of the test-expression evaluation – otherwise an infinite loop is created that will lock the system.

The significant difference between a while loop and a do while loop is that a while loop will not make a single iteration if the test-expression is FALSE on its first evaluation. In contrast, a do while loop will always make at least one iteration because its statements are executed before the evaluation is made. If this is desirable, a do whileloop is obviously the best choice, otherwise the choice between a for loop and a while loop is largely a matter of personal preference. One rule of thumb suggests that a for loop is best used to perform a specific number of iterations, whereas a while loop is best used to iterate until a certain condition is met.

Loops are the perfect partner to use with arrays, as each iteration can effortlessly read or write into successive array elements.

![image](images/snake.jpg)

Ensure that the test expression in a loop structure will at some point become **FALSE** to avoid creating an infinite loop that never ends.

![image](images/hot.jpg)

You will discover later in this book how a PHP **while** loop is used to retrieve records from a MySQL database.

![image](images/pg53_1.jpg)

whileloop.php

![image](images/1g.jpg)Begin a PHP script with a statement to create an array

**$numbers \= array( 10 , 20 , 30 ) ;**

![image](images/2g.jpg)Next, add a while loop to output the value of each array element

**echo ‘<dt>While Loop : ’ ;**

**$i \= 0 ;**

**while ( $i < 3 )**

**{**

**echo “<dd>Element $i = $numbers\[$i\] ” ;**

**$i++ ;**

**}**

![image](images/3g.jpg)Now, add a do while loop to output the value of each array element

**echo ‘<dt>Do While Loop : ’ ;**

**$i \= 0 ;**

**do**

**{**

**echo “<dd>Element $i = $numbers\[$i\] ” ;**

**$i++ ;**

**}**

**while ( $i < 3 ) ;**

![image](images/4g.jpg)Save the document in your web browser’s /htdocs directory as **whileloop.php**, then open the page via HTTP to see the array element values get identically displayed

![image](images/pg53_2.jpg)

![image](images/forget.jpg)

Change the value in this test expression to zero so **while ( $i = 0 )** in both loops to see only the first iteration of the **do while** loop get executed.

**Breaking from loops**

The break keyword can be used to prematurely terminate a loop when a specified condition is met. The break statement is situated inside the loop statement block and is preceded by a test expression. When the test returns TRUE, the loop ends immediately and the program proceeds on to the next task. For example, in a nested inner loop it proceeds to the next iteration of the outer loop.

![image](images/pg54_1.jpg)

breakcontinue.php

![image](images/1g.jpg)Begin a PHP script with a for loop that performs three iterations

**for ( $i \= 1 ; $i < 4 ; $i++ )**

**{**

**\# Nested loop to be inserted here (Step 2).**

**}**

![image](images/2g.jpg)Next, insert a nested for loop that also performs three iterations

**for ( $j \= 1 ; $j < 4 ; $j++ )**

**{**

**\# Statements to be inserted here (Steps 5 & 6).**

**}**

![image](images/3g.jpg)Now, insert a statement that outputs the value of both loop counters on each iteration

**echo “Running i = $i and j = $j <br>” ;**

![image](images/4g.jpg)Save the document in your web browser’s /htdocs directory as breakcontinue.php, then open the page via HTTP to see both loop counter values get displayed

![image](images/pg54_2.jpg)

![image](images/5g.jpg)Next, insert this break statement at the very beginning of the inner loop block, to break out of the inner loop – then save the document and view the change

**if ( $i \== 2 && $j \== 1 )**

**{**

**echo “Breaks inner loop when i = $i and j = $j <br>” ;**

**break ;**

**}**

![image](images/pg55_1.jpg)

The continue keyword can be used to skip a single iteration of a loop when a specified condition is met. The continue statement is situated inside the loop statement block and is preceded by a test expression. When the test returns TRUE, that single iteration ends.

![image](images/6g.jpg)Now, insert this continue statement at the beginning of the inner loop block, to skip the first iteration of the inner loop – then save the document and view the change

**if ( $i \== 1 && $j \== 1 )**

**{**

**echo “Continues inner loop when i = $i and j = $j <br>” ;**

**continue ;**

**}**

![image](images/pg55_2.jpg)

![image](images/forget.jpg)

Here, the **break** statement halts all three iterations of the inner loop when the outer loop tries to run it the second time.

![image](images/forget.jpg)

Here, the **continue** statement just skips the first iteration of the inner loop when the outer loop tries to run it for the first time.

**Creating functions**

PHP provides many built-in functions that can be called by name in your scripts to execute pre-defined actions, such as the array sorting functions described [here on page 32](#chapter02.html#sec15). Additionally, you may create your own custom functions to execute specified actions when called. This usefully allows PHP scripts to be modularized into sections of code that are easier to understand and maintain.

Your custom function names may contain any combination of letters, numbers, and the underscore character, but must begin with a letter or an underscore. Understandably, the name may not duplicate an existing built-in function name to avoid conflict, so, for example, you may not create a custom function named “sort”.

As with PHP variables, function names are case-sensitive, so cube(), Cube(), and CUBE() call three separate individual functions.

A function is created in a PHP script simply by stating its name, after the function keyword, followed by parentheses and curly brackets (braces) containing the statements to be executed each time that function gets called:

**function *function\_name* ( )**

**{**

***statements-to-be-executed***

**}**

When creating custom functions it is important to understand how variable accessibility is limited by the variable’s “scope”:

•Variables created outside a function have “global” scope but are not accessible from within any function block.

•Variables created inside a function have “local” scope so are only accessible from within that particular function block.

As a variable created within a function is not accessible from elsewhere, its name may duplicate the name of a variable outside a function block, or within another function block, without conflict. This allows a global variable to contain a different value to local variables of the same name.

The scope of a variable created within a function can be altered to make it available globally by preceding its declaration with the global keyword – but this is bad practice and should be avoided.

![image](images/snake.jpg)

Always avoid using the **global** keyword to alter the scope of local variables, to maintain your code integrity.

![image](images/pg57_1.jpg)

function.php

![image](images/1g.jpg)Begin a PHP script with a statement to create and initialize a global variable

**$result \= 5 + 5 ;**

![image](images/2g.jpg)Next, add a function to create and initialize a local variable of the same name, and to output its value

function square()

**{**

**$result \= 5 \* 5 ;**

**echo “Local Square Result = $result<br>” ;**

**}**

![image](images/3g.jpg)Now, add another function to create and initialize a local variable of the same name again, and to output its value

**function cube()**

**{**

**$result \= 5 \* 5 \* 5 ;**

**echo “Local Cube Result = $result<br>” ;**

**}**

![image](images/4g.jpg)Finally, add statements to output the value of the global variable and call both custom functions

**echo “Global Sum Result = $result<br>” ;**

**square() ;**

**cube() ;**

![image](images/5g.jpg)Save the document in your web browser’s /htdocs directory as function.php, then open the page via HTTP to see the like-named variable values get displayed

![image](images/pg57_2.jpg)

![image](images/forget.jpg)

Variables of the same name do not conflict when they are declared in a different scope – they are not visible to each other.

**Passing arguments**

Data can be passed to custom functions as “arguments” (also known as “parameters”) in the same way you can pass arguments to some built-in PHP functions. For example, the sort() function takes the array to be sorted as its argument.

Functions can be created with any number of arguments, but when called data must be supplied for each argument to avoid an error.

A function containing arguments is created by including a comma-separated list of argument variables within the parentheses after the function name, like this:

**function *function\_name* ( *$arg\_1 , $arg\_2 , $arg\_3* )**

**{**

***statements-to-be-executed***

**}**

Argument names must adhere to the same naming conventions required for other PHP variables, and should ideally be meaningful to represent the nature of the data they will be passed. The argument data must be passed by the call in the correct order and can then be used by the statements within that function:

**function print\_name( $first\_name , $last\_name )**

**{**

**echo “Name is $first\_name $last\_name “ ;**

**}**

**print\_name( ‘Mickey’ , ‘Mouse’ ) ;    # Name is Mickey Mouse**

The function call may pass literal values, like the strings in the example above, or may pass regular variables – which in turn supply their values to the function. For instance:

**$forename = ‘Donald’ ;**

**$surname = ‘Duck’ ;**

**print\_name( $forename , $surname ) ;    # Name is Donald Duck**

Argument variables have local scope so are only accessible within the function in which they are created. This means the same argument names may be used in many functions without conflict with each other or with regular variable names.

![image](images/forget.jpg)

Arguments must be specified in the function declaration and passed by the caller as a comma-separated list.

![image](images/pg59_1.jpg)

argument.php

![image](images/1g.jpg)Begin a PHP script with a statement to create and initialize a global variable

**$number \= 5 ;**

![image](images/2g.jpg)Next, add a function with one argument to utilize its value in a calculation and to output its result

**function square( $number )**

**{**

**$result \= $number \* $number ;**

**echo “$number Squared = $result<br>” ;**

**}**

![image](images/3g.jpg)Now, add another function with one argument to utilize its value in a calculation and to output its result

**function cube( $number )**

**{**

**$result \= $number \* $number \* $number ;**

**echo “$number Cubed = $result<br>” ;**

**}**

![image](images/4g.jpg)Finally, add statements to call the functions passing both literal and variable arguments

**square( 3 ) ;**

**cube( 4 ) ;**

**square( $number ) ;**

**cube( $number ) ;**

![image](images/5g.jpg)Save the document in your web browser’s /htdocs directory as argument.php, then open the page via HTTP to see the results get displayed

![image](images/pg59_2.jpg)

![image](images/hot.jpg)

You can use the same name for the argument and a regular variable to be passed to it for easy recognition.

**Returning values**

Some PHP functions return values when called, and the nature of the returned value may be determined by the argument passed. For example, the built-in date() function accepts a whole range of arguments to determine how date information should be formatted for return to the caller:

 
| **Argument:** || **Description:** || **Example:** |
| --- | --- | --- |
| Y || Year as four digits || 2018 |
| y || Year as two digits || 14 |
| n || Month as one or two digits || 5 |
| m || Month as two digits || 05 |
| F || Month full name || February |
| M || Month name as three letters || Feb |
| j || Day as one or two digits || 4 |
| d || Day as two digits || 04 |
| l || Weekday full name || Monday |
| D || Weekday as three letters || Mon |
| S || Ordinal suffix as two letters || th |
| H || Hour in 24-hour format || 14 |
| i || Minutes || 45 |
| s || Seconds || 30 |

Your own custom functions can also be made to return a value when called, simply by using the return keyword in a statement followed by the value that is to be returned. Typically, this will be the final statement in the function’s statement block.

![image](images/hot.jpg)

These are just some of the possible **date()** function arguments – you can discover the complete range in the PHP manual online at [php.net/manual](http://www.php.net/manual)

![image](images/pg61_1.jpg)

return.php

![image](images/1g.jpg)Begin a PHP script with statements to set the timezone and initialize a global variable with a user name

**date\_default\_timezone\_set( ‘UTC’ ) ;**

**$user \= ‘ Mike’ ;**

![image](images/2g.jpg)Next, add a function with no arguments to return the weekday, day with suffix, and month name when called

function display\_date( )

**{**

**return date( ‘l, jS F’ ) ;**

**}**

![image](images/3g.jpg)Now, add a function with one argument to return an appropriate user greeting for the current time of day

function welcome( $user )

**{**

**$hour \= date( ‘H’ ) ;**

**$greeting \= ( $hour < 12 ) ?**

**‘<br>Good Morning’ : ‘<br>Good Day’ ;**

**$greeting .= $user ;**

**return $greeting ;**

**}**

![image](images/4g.jpg)Finally, add statements to call the functions passing the global variable as an argument

**echo display\_date() ;**

**echo welcome( $user ) ;**

![image](images/5g.jpg)Save the document in your web browser’s /htdocs directory as return.php, then open the page via HTTP to see the returns get displayed

![image](images/pg61_2.jpg)

![image](images/forget.jpg)

The default timezone must be set to use the **date()** function – either in the PHP configuration file or with the **date\_ default\_timezone\_set()** function as seen here.

**Summary**

•The if keyword performs the basic conditional test that evaluates an expression for a Boolean value of TRUE or FALSE.

•An else statement specifies statements to be executed when the expressions evaluated by the if statement are found to be FALSE.

•Alternative expressions may be evaluated in a conditional test by adding an elseif statement.

•Multiple if-elseif-else statements can often be performed more efficiently by a switch statement.

•Each case statement must end with a break keyword statement so the switch statement will exit when a match is found.

•A default statement specifies code to be executed in the event that no matches are found within any case statements.

•A loop is a piece of code in a script that automatically repeats until a test expression becomes FALSE.

•The PHP loop structures are for, while, do while, and foreach.

•The break keyword can be used to prematurely terminate a loop when a specified condition is met.

•The continue keyword can be used to skip a single iteration of a loop when a specified condition is met.

•Functions execute specified actions when called, and allow scripts to be modularized into sections of code.

•A function is created by stating its name after the function keyword followed by parentheses and curly brackets.

•A comma-separated list of arguments can be included within the parentheses after a function name.

•Functions can return a value when called by using the **return** keyword in a statement followed by the value to be returned.

4

Producing forms

***This chapter demonstrates how to use PHP scripts to process HTML form data.***

[**Performing actions**](#chapter04.html#sec31)

[**Checking set values**](#chapter04.html#sec32)

[**Validating form data**](#chapter04.html#sec33)

[**Sending hidden data**](#chapter04.html#sec34)

[**Handling submissions**](#chapter04.html#sec35)

[**Making sticky forms**](#chapter04.html#sec36)

[**Surrounding forms**](#chapter04.html#sec37)

[**Appending link data**](#chapter04.html#sec38)

[**Moving location**](#chapter04.html#sec39)

[**Summary**](#chapter04.html#sec40)

**Performing actions**

Processing data submitted from an HTML form on a web page is perhaps the most fundamental task performed by a PHP script.

The HTML <form> tag’s action attribute is used to nominate the PHP script that will process (“handle”) the form data. Additionally, the <form> tag’s method attribute is used to specify how the data is sent to the script – typically by the POST method. So the HTML form tag and attributes might look like this:

**<form action=”script.php” method=”POST”>**

PHP provides a special “superglobal” $\_POST array variable in which it stores form data submitted by the POST method. It creates an array element of the same name as each submitted form element name, storing the value they contain. For example, with this form element:

**<input type=”text” name=”email” >**

On submission of the form, PHP will create an array element named $\_POST\[‘email’\] containing the value entered into that form input by the user.

For easy recognition, PHP variables of the same names as the form elements can be assigned the values stored in their corresponding $\_POST array elements. The values can then be displayed in a response page created by the action handler script.

![image](images/1p.jpg)Create an HTML document containing a form with three text input fields for data submission

**<form action=”action\_handler.php” method=”POST”>**

**<dl>**

**<dt>Name:**

**<dd><input type=”text” name=”name”>**

**<dt>Email Address:**

**<dd><input type=”text” name=”mail”>**

**<dt>Comments:**

**<dd><textarea rows=”5” cols=”20” name=”comment” >**

**</textarea>**

**</dl>**

**<p><input type=”submit” ></p>**

**</form>**

![image](images/pg70_1.jpg)

action.php

![image](images/2p.jpg)Now, save the document in your web browser’s /htdocs directory as action.php

![image](images/snake.jpg)

PHP is case-sensitive so the capitalization must be precisely as described – $\_POST\[‘EMail’\] or $\_Post\[‘email’\] are incorrect, for example.

![image](images/3p.jpg)Next, create an HTML document containing a script to assign form values to like-named PHP variables for output

**<?php**

**$name \= $\_POST\[‘name’\] ;**

**$mail \= $\_POST\[‘mail’\] ;**

**$comment \= $\_POST\[‘comment’\] ;**

**echo “<p>Thanks for this comment $name ...</p>” ;**

**echo “<p><i>$comment</i></p>” ;**

**echo “<p>We will reply to $mail</p>” ;**

**?>**

![image](images/pg70_1.jpg)

action\_handler.php

![image](images/4p.jpg)Save the document in your web browser’s /htdocs directory as action\_handler.php, then open action.php via HTTP and submit some data to see it get displayed in the response page produced by the PHP script

![image](images/pg65_2.jpg)

![image](images/pg65_3.jpg)

![image](images/hot.jpg)

Form submission methods may be either “GET” or “POST”. The GET method appends name=value pairs to the URL but is mostly used to request information – such as retrieving a database record. The POST method can submit more data, is more secure as the data is not appended to the URL, and is mostly used when an action is to be performed – such as updating a database record. The POST method is therefore preferred for most examples in this book.

**Checking set values**

PHP can easily ensure that the user has entered data into submitted HTML form fields using the built-in isset()function. This function takes the name of a variable as its argument and returns TRUE only if that variable value is not NULL – thus ensuring that the variable has been “set” with some value. Empty form fields will be NULL unless the user has entered a value.

Conditional tests can be made with the isset() function to indicate where form fields have been left empty, or to provide a response page where the fields have been completed.

![image](images/1p.jpg)Create an HTML document containing a form with three radio buttons providing a single field for data submission

**<form action=”isset\_handler.php” method=”POST”>**

**<fieldset>**

**<legend>What kind of language is PHP?</legend>**

**Scripting<input type=”radio”**

**name=”definition” value=”Scripting”> <br>**

**Markup<input type=”radio”**

**name=”definition” value=”Markup”> <br>**

**Programming<input type=”radio”**

**name=”definition” value=”Programming”>**

**</fieldset><p><input type=”submit” ></p>**

**</form>**

![image](images/pg70_1.jpg)

isset.php

![image](images/2p.jpg)Now, save the document in your web browser’s /htdocs directory as isset.php

![image](images/pg70_1.jpg)

isset\_handler.php

![image](images/3p.jpg)Next, create an HTML document containing a PHP script to initialize a variable with a submitted value – or with NULL if no value has been submitted

**<?php**

**if ( isset( $\_POST\[‘definition’\] ) )**

**{**

**$definition \= $\_POST\[‘definition’\] ;**

**}**

**else**

**{**

**$definition \= NULL ;**

**}**

**\# Response statements to be inserted here.**

**?>**

![image](images/4p.jpg)Finally, insert statements to output an appropriate response according to the value of the variable

**if ( $definition != NULL )**

**{**

**if ( $definition != ‘Scripting’ )**

**{ echo “$definition is Incorrect” ; }**

**else**

**{ echo “$definition is Correct” ; }**

**}**

**else**

**{ echo ‘You must select one answer’ ; }**

![image](images/5p.jpg)Save the document in your web browser’s /htdocs directory as isset\_handler.php, then open isset.php via HTTP and submit the form to see the responses

![image](images/pg67_1.jpg)

![image](images/pg67_2.jpg)

![image](images/pg67_3.jpg)

![image](images/pg67_4.jpg)

![image](images/hot.jpg)

It is technically more efficient to test whether a condition is not TRUE than whether it is TRUE – as fewer possibilities need evaluating.

**Validating form data**

As users may inadvertently submit forms with empty fields, or with data in the wrong format, it is essential your PHP scripts ensure required fields are completed and submitted data is valid.

To ensure the user has entered something into a text field, PHP provides an empty() function that accepts a variable argument and returns TRUE if its value is an empty string, zero, NULL or FALSE.

To ensure the user has entered data in numeric format, PHP provides an is\_numeric() function that accepts a variable argument and returns TRUE only if its value is a number.

More specific data validation can be performed using the PHP preg\_match() function that accepts a “regular expression” argument and a variable argument in which to seek a pattern. Typically, this is used to ensure an email address is in the expected format.

![image](images/1p.jpg)Create an HTML document containing a form with two text fields for data submission

**<form action=”valid\_handler.php” method=”POST”>**

**<fieldset>**

**<legend>Enter a quantity and email address</legend>**

**<p>Quantity : <input type=”text” name=”quantity”></p>**

**<p>Email Address : <input type=”text” name=”email”></p>**

**</fieldset><p><input type=”submit” ></p>**

**</form>**

![image](images/pg68_1.jpg)

valid.php

![image](images/2p.jpg)Now, save the document in your web browser’s /htdocs directory as valid.php

![image](images/3p.jpg)Next, create an HTML document containing a PHP script to initialize a variable with a submitted value – or with NULL if no value has been submitted

**if ( !empty ( $\_POST\[‘quantity’\] ) )**

**{**

**$quantity \= $\_POST\[‘quantity’\] ;**

**\# Format validation to be inserted here.**

**}**

**else**

**{ $quantity \= NULL ; echo ‘You must enter a quantity<br>’ ; }**

![image](images/pg68_2.jpg)

valid\_handler.php

![image](images/4p.jpg)Insert statements to ensure the format is numeric

**if ( !is\_numeric( $quantity ) )**

**{ $quantity \= NULL ; echo ‘Quantity must be numeric<br>’ ; }**

![image](images/5p.jpg)Now, add statements to initialize another variable with a submitted value – or with NULL if no value is submitted

**if ( !empty ( $\_POST\[‘email’\] ) )**

**{**

**$email \= $\_POST\[‘email’\] ;**

**\# Format validation to be inserted here.**

**}**

**else**

**{ $email \= NULL ; echo ‘You must enter an email address’ ; }**

![image](images/6p.jpg)Next, insert statements to ensure the email address uses the expected pattern

**$pattern \= ‘/\\b\[\\w.-\]+@\[\\w.-\]+\\.\[A-Za-z\]{2,6}\\b/’ ;**

**if ( !preg\_match( $pattern , $email ) )**

**{ $email \= NULL ; echo ‘Email address is incorrect format’ ; }**

![image](images/7p.jpg)Finally, add a statement to output valid submitted data

**if ( ( $quantity != NULL ) && ( $email != NULL ) )**

**{ echo “Email : $email<br>Quantity : $quantity “ ; }**

![image](images/8p.jpg)Save the document in your web browser’s /htdocs directory as valid\_handler.php, then open valid.php via HTTP and submit the form to see the responses

![image](images/pg69_1.jpg)

![image](images/pg69_2.jpg)

![image](images/hot.jpg)

Strictly speaking, the topic of regular expressions is outside the remit of this book but you can precisely copy the pattern in this example to ensure email addresses are in the expected format.

**Sending hidden data**

In addition to data entered by the user into HTML form input fields, data generated by PHP can be submitted using HTML form hidden fields. Like regular input fields these also send a name=value pair to the form handler script but here the value is supplied by PHP, not by the user.

Typically, data submitted using hidden form fields might include the login name of the user and a timestamp of the submission.

![image](images/1p.jpg)Create an HTML document containing a PHP script to define the timezone and initialize two variables

**date\_default\_timezone\_set( ‘UTC’ ) ;**

**$time \= date( ‘ H:i , F j ‘ ) ;**

**$user \= ‘Mike’ ;**

![image](images/pg70_1.jpg)

hidden.php

![image](images/2p.jpg)Now, add a statement to write a complete form containing a regular input field and two hidden fields whose values are set by the variables

**echo ‘**

**<form action=”hidden\_handler.php” method=”POST”>**

**<fieldset>**

**<legend>Send us your comments</legend>**

**<textarea rows=”5” cols=”20” name=”comment”>**

**</textarea>**

**<input type=”hidden” name=”user” value=” ‘. $user .’ “>**

**<input type=”hidden” name=”time” value=” ‘. $time.’ “>**

**</fieldset><p><input type=”submit” ></p></form> ‘ ;**

![image](images/3p.jpg)Save the document in your web browser’s /htdocs directory as hidden.php

![image](images/4p.jpg)Next, create an HTML document containing a PHP script to initialize a variable with a submitted value – or with NULL if no value has been submitted

**if ( !empty ( $\_POST\[‘comment’\] ) )**

**{**

**$comment \= $\_POST\[‘comment’\] ;**

**}**

**else**

**{**

**$comment \= NULL ;**

**echo ‘You must enter a comment’ ;**

**}**

![image](images/pg70_1.jpg)

hidden\_handler.php

![image](images/snake.jpg)

The timestamp in this example is created when the form gets created, not when the form gets submitted.

![image](images/5p.jpg)Now, add statements to initialize two variables if the hidden form field values have been set

**$time \=**

**( !isset ( $\_POST\[‘time’\] ) ) ? NULL : $\_POST\[‘time’\] ;**

**$user \=**

**( !isset ( $\_POST\[‘user’\] ) ) ? NULL : $\_POST\[‘user’\] ;**

![image](images/6p.jpg)Finally, add a statement to output valid submitted data

**if ( ( $comment != NULL ) &&**

**( $time != NULL ) && ( $user != NULL ) )**

**{ echo “<p>Comment received : \\” $comment \\”<br>**

**From $user at $time </p>” ; }**

![image](images/7p.jpg)Save the document in your web browser’s /htdocs directory as hidden\_handler.php, then open hidden.php via HTTP and submit the form to see the responses

![image](images/pg71_1.jpg)

![image](images/pg71_2.jpg)

![image](images/hot.jpg)

Notice the ternary **? :** operator is used here in place of a more lengthy **if else** statement.

![image](images/forget.jpg)

You can include quotes in output by prefixing them with a backslash to escape them from recognition – as demonstrated here.

**Handling submissions**

The examples so far in this chapter have each used two documents – one to display an HTML form and another to handle the form submission. This procedure can, however, be performed by a single document using a simple technique to determine whether a form should be displayed or its submission should be handled.

PHP provides a special “superglobal” $\_SERVER array variable with a REQUEST\_METHOD element in which it stores the type of request. Where a form uses the POST method for submission, two different types of request are made to the PHP script when the page loads – simply displaying the form uses the standard GET method made by most web pages, whereas submitting the form uses the POST method. Therefore, the request method can be examined to determine which course of action to take.

Using this technique, the name of the same single page is also specified as the form handler to the HTML action attribute. The form can be displayed by the usual echo instruction, and validation checks can be made for the response in the same way as described for separate form handler scripts.

![image](images/1p.jpg)Create an HTML document containing a PHP script that examines the page request method

**if ( $\_SERVER\[ ‘REQUEST\_METHOD’ \] != ‘POST’ )**

**{**

**\# Form display statements to be inserted here.**

**}**

**else**

**{**

**\# Form handling statements to be inserted here.**

**}**

![image](images/pg72_1.jpg)

single.php

![image](images/2p.jpg)Now, insert a statement to display a form when the page has been requested by the standard GET method

**echo ‘**

**<form action=”single.php” method=”POST”>**

**<fieldset>**

**<legend>Send us your comments</legend>**

**<textarea rows=”5” cols=”40” name=”comment”>**

**</textarea>**

**</fieldset>**

**<p><input type=”submit” ></p>**

**</form> ‘ ;**

![image](images/3p.jpg)Next, insert a statement to handle the form submission when the page has been requested by the POST method

**if ( !empty ( $\_POST\[‘comment’\] ) )**

**{**

**$comment \= $\_POST\[‘comment’\] ;**

**echo “Comment : $comment “ ;**

**}**

**else**

**{ $comment \= NULL ; echo ‘You must enter a comment’ ; }**

![image](images/4p.jpg)Save the document in your web browser’s /htdocs directory as single.php, then submit the form to see the responses

![image](images/pg73_1.jpg)

![image](images/pg73_2.jpg)

![image](images/pg73_3.jpg)

![image](images/pg73_4.jpg)

![image](images/hot.jpg)

The form will be handled by the same page on submission if the action attribute specifies an empty string action=”” – but it is preferable to specify the page name.

**Making sticky forms**

When a user attempts to submit a form where a required field has not been completed, it is desirable to retain the entries in the fields they have completed by making the form “sticky”. This is especially so for lengthy forms with many fields, so the user need not complete all fields once more, and is easily achieved with PHP.

Simply assigning the relevant submitted field data from the $\_POST array to the HTML tag’s value attribute with echo retains the entry when the form is displayed again for completion. As a precaution, the statement should use the isset() function to check that the field was in fact completed before submission.

An error message for each incomplete field can be assigned to an array to advise of omissions when the form is displayed again, or a message written confirming success when all fields are completed.

![image](images/pg74_1.jpg)

sticky.php

![image](images/1p.jpg)Create an HTML document containing a sticky form with two text fields for name and email address details

**<form action=”sticky.php” method=”POST”>**

**<p>Name:**

**<input type=”text” name=”name”**

**value=”<?php if ( isset( $\_POST\[‘name’\] ) )**

**echo $\_POST\[‘name’\] ; ?>”> </p>**

**<p>Email:**

**<input type=”text” name=”email”**

**value=”<?php if ( isset( $\_POST\[‘email’\] ) )**

**echo $\_POST\[‘email’\] ; ?>”></p>**

**<p><input type=”submit”></p>**

**</form>**

![image](images/2p.jpg)Now, add a PHP script to handle the form submission

**<?php**

**if ( $\_SERVER\[ ‘REQUEST\_METHOD’ \] \== ‘POST’ )**

**{**

**\# Statements to be inserted here.**

**}**

**?>**

![image](images/3p.jpg)Next, into the PHP script block, insert a statement to create an array for error messages

**$errors \= array() ;**

![image](images/forget.jpg)

The if statement tests that the form has been submitted by checking the request method is POST, not the GET method that is used to display the empty form.

![image](images/4p.jpg)Then, insert statements to initialize variables with submitted values, or add to the errors array for omissions

**if ( empty( $\_POST\[ ‘name’ \] ) ) { $errors\[\] \= ‘name’ ; }**

**else { $name \= trim( $\_POST\[ ‘name’ \] ) ; }**

**if ( empty( $\_POST\[ ‘email’ \] ) ) { $errors\[\] \= ‘email’ ; }**

**else { $email \= trim( $\_POST\[ ‘email’ \] ) ; }**

![image](images/5p.jpg)Now, insert statements to write error messages or confirm successful form submission

**if( !empty( $errors ) )**

**{ echo ‘Error! Please enter your ‘ ;**

**foreach ( $errors as $msg ) { echo “ - $msg “ ; } }**

**else { echo “Success! Thanks $name “ ; }**

![image](images/6p.jpg)Save the document in your web browser’s /htdocs directory as sticky.php, then open it via HTTP and submit the form to see the retained values and response messages

![image](images/pg75_1.jpg)

![image](images/pg75_2.jpg)

![image](images/hot.jpg)

It is good practice to use the **trim()** function, as seen here, to remove any leading and trailing spaces from the submitted field value.

**Surrounding forms**

PHP usefully allows multiple files to be incorporated together to create a single web page. This means that dynamic forms can be surrounded by static header and footer content that can be easily re-used to create other pages within a website.

The PHP include() function takes the URL of another file to be incorporated within a web page as its argument. Typically, included static content files are HTML, and are located in an “includes” folder within the /htdocs directory of your web server.

PHP also provides a require() function that works just like the include() function to incorporate other files within a web page, but is subtly different. When the include() function fails, as the specified file cannot be found, for example, a warning gets sent to the browser but the script continues to run. When the require() function fails, an error is printed but the script gets halted. Usually, the include() function incorporates static HTML files, whereas the require() function incorporates dynamic PHP scripts.

Importantly, the title of a web page incorporating multiple files can be dynamically written by PHP to allow maximum flexibility of otherwise static HTML header content.

![image](images/1p.jpg)Create an HTML document containing static header content and a PHP snippet to write the page title

**<!DOCTYPE HTML>**

**<html lang=”en”>**

**<head>**

**<meta charset=”UTF-8”>**

**<title> <?php echo $page\_title ; ?> </title>**

**<link rel=”stylesheet” href=”includes/style.css”>**

**</head>**

**<body>**

**<header><h1>Page Header</h1></header>**

![image](images/pg76_1.jpg)

header.html

![image](images/2p.jpg)Now, create an HTML document containing footer content

**<footer><p>Page Footer</p></footer>**

**</body>**

**</html>**

![image](images/pg76_2.jpg)

footer.html

![image](images/3p.jpg)Next, create a folder named “includes” in the /htdocs directory of your web server and save the above documents inside it as header.html and footer.html respectively

![image](images/4p.jpg)Create a CSS style sheet to present the header and footer content (and rules to present aspects of later examples)

**header > h1 { border-bottom : 1px dashed black ;**

**font-style : italic ; font-size : x-large ; }**

**footer > p { border-top : 1px dashed black ;**

**font-style : italic ; }**

**table { border-spacing : 5px ; width : 530px ; }**

**th { color : #FFF ; background : #000 ; text-align : left ; }**

**td { border-bottom : 1px solid black ;**

**padding : 3px ; background : #F0F0F0 ;**

**text-align : left ; vertical-align :top ; }**

**p#err\_msg { color : #F00 ; font-weight : bold ; }**

![image](images/pg77_1.jpg)

style.css

![image](images/5p.jpg)Save the style sheet in the /includes folder you have created, alongside the HTML header and footer files

![image](images/6p.jpg)Finally, create a PHP script that sets the web page title and surrounds a form with header and footer content

**$page\_title \= ‘PHP Include’ ;**

**include ( ‘includes/header.html’ ) ;**

**echo ‘<form action=”include.php” method=”POST”>**

**<p>Name: <input type=”text” name=”name”> </p>**

**<p>Email: <input type=”text” name=”email” ></p>**

**<p><input type=”submit”></p></form>’ ;**

**include ( ‘includes/footer.html’ ) ;**

![image](images/pg77_2.jpg)

include.php

![image](images/7p.jpg)Save the PHP script in your web browser’s /htdocs directory as include.php, then open it via HTTP to see the page title set and a form surrounded by static content

![image](images/pg77_3.jpg)

![image](images/hot.jpg)

You can use your browser’s View Source facility to see that the entire content has been effectively incorporated into a single web page.

**Appending link data**

PHP pre-defined “superglobal” variables, such as the $\_SERVER array variable that stores the page request method, and the $\_SESSION array variable that stores user data across pages of a website until the user quits, are accessible in all scopes of any script.

Where an HTML form submits data using the POST method, the $\_POST array stores the value of submitted form values in like-named array elements. So, the value of a submitted field named “city” can be accessed using $\_POST\[‘city’\].

Similarly, where data is submitted using the GET method, the $\_GET array stores the value of submitted values in named array elements. So, the value of a submitted data named “id” can be accessed using $\_GET\[‘id’\]. This is typically used to submit data to a script by appending a name=value pair to the URL in an HTML hyperlink anchor, like this:

**<a href=”www.example.com/script.php?id=1”>**

The script receiving the data, nominated by the hyperlink, may then use the passed value to determine a response.

![image](images/1p.jpg)Create an HTML document containing a PHP script that seeks an element named “id” within the $\_GET array

if ( isset ( $\_GET\[ ‘id’ \] ) )

**{**

**\# Handler statements to be inserted here.**

**}**

![image](images/pg78_1.jpg)

link.php

![image](images/2p.jpg)Next, insert a handler statement to assign a passed value to a like-named PHP variable

**$id \= $\_GET\[ ‘id’ \] ;**

![image](images/3p.jpg)Now, insert a handler statement to output an appropriate response according to the value passed

**switch( $id )**

**{**

**case 1 : echo ‘Cow selected<hr>’ ; break ;**

**case 2 : echo ‘Dog selected<hr>’ ; break ;**

**case 3 : echo ‘Goat selected<hr>’ ; break ;**

**}**

![image](images/hot.jpg)

The $\_SESSION superglobal will be used to store user details in the next example.

![image](images/4p.jpg)Finally, add statements to display hyperlinks with appended values

**echo ‘<h1>Select a buddy</h1>’ ;**

**echo ‘ <p><a href=”link.php?id=1”>Cow</a> |’ ;**

**echo ‘ <a href=”link.php?id=2”>Dog</a> | ‘ ;**

**echo ‘ <a href=”link.php?id=3”>Goat</a></p>’ ;**

![image](images/5p.jpg)Save the PHP script in your web browser’s /htdocs directory as link.php, then open it via HTTP and click the links to see the responses for the passed values

![image](images/pg79_1.jpg)

![image](images/pg79_2.jpg)

![image](images/snake.jpg)

PHP also provides a $\_REQUEST superglobal that contains the entire contents of the $\_POST and $\_GET arrays. This means that $\_POST\[‘city’\] is also accessible using $\_REQUEST\[‘city’\], but this should be avoided. Always use the specific array for the type of submission instead.

![image](images/forget.jpg)

Notice that the passed name=value pair is visible in the browser address field.

**Moving location**

PHP provides a header() function that accepts an argument to specify a raw HTTP “header” to be sent to the web browser. Headers are sent from the web server before any other data, and are normally not visible to the user. Most usefully, the PHP header() function can set the “Location” header to re-direct the browser to a new page, using this syntax:

**header( ‘Location: *www.example.com/page.php*‘ ) ;**

User data can be preserved when moving to a new page by first storing it in the special PHP superglobal $\_SESSION array variable. This is not available automatically, however, until the session\_start() function has been called in the script. Variable values can then be stored in like-named elements of the $\_SESSION array, so they become available from other pages on the website until the user quits or until the session\_destroy() function is called in the script.

![image](images/1p.jpg)Create an HTML document containing a PHP script that seeks an element named “id” within the $\_POST array

**if ( isset ( $\_POST\[ ‘id’ \] ) )**

**{**

**$id** \= **$\_POST\[ ‘id’ \] ;**

**\# Handler statements to be inserted here.**

**}**

![image](images/pg80_1.jpg)

header.php

![image](images/2p.jpg)Next, insert handler statements to store a matched id value in a $\_SESSION array element and relocate the browser – or display a message for any other id value

**if( $id\== 123 )**

**{**

**session\_start() ;**

**$\_SESSION\[‘id’\] \= $id ;**

**header( ‘Location: location.php’ ) ;**

**exit() ;**

**}**

**else { echo “<p>$id is an incorrect ID!</p>” ; }**

![image](images/3p.jpg)Now, add a statement to display a form in which the user may enter an id value for submission

**echo ‘<form action=”header.php” method=”POST”>**

**<fieldset> <legend>Enter Your User ID</legend>**

**<p>ID : <input type=”text” name=”id”></p>**

**</fieldset> <input type=”submit”> </form> ‘ ;**

![image](images/hot.jpg)

It is good practice to call the exit() function to halt the script when relocating the browser.

![image](images/4p.jpg)Save the document in your web browser’s /htdocs directory as header.php

![image](images/5p.jpg)Finally, create a target HTML document containing a PHP script to display the retained $\_SESSION array value

**session\_start() ;**

**if ( isset( $\_SESSION\[‘id’\] ) )**

**{**

**$id \= $\_SESSION\[‘id’\] ;**

**echo “Welcome user ID #$id” ;**

**}**

![image](images/pg81_1.jpg)

location.php

![image](images/6p.jpg)Save this document in your web browser’s /htdocs directory as location.php, then open header.php via HTTP and submit an id value to see the responses

![image](images/pg81_2.jpg)

![image](images/pg81_3.jpg)

![image](images/pg81_4.jpg)

![image](images/forget.jpg)

Notice that the script on the target page must also call session\_start() to make the $\_SESSION superglobal accessible.

**Summary**

•An HTML <form> tag’s action attribute specifies the PHP script to handle the form submission, and its method attribute specifies how the data is sent to the script.

•Form data submitted by the POST method gets automatically stored in the PHP superglobal $\_POST array variable.

•Elements of the $\_POST array are named the same as the HTML form element containing each submitted value.

•PHP can ensure that the user has entered data into submitted HTML form fields using the built-in isset() function.

•The PHP empty() function checks whether a value has been entered into a form text field.

•Format validation can be performed on submitted form data by the is\_numeric() function and preg\_match() function.

•Data generated by PHP, such as a timestamp created by the date() function, can be submitted from hidden form fields.

•The PHP superglobal $\_SERVER\[‘REQUEST\_METHOD’\] array element stores the type of request made to load the page.

•Sticky forms retain their field data simply by writing any submitted values back to the HTML input’s value attribute.

•The PHP include() and require() functions are used to incorporate other content and scripts within a web page.

•Data submitted by the GET method gets automatically stored in the PHP superglobal $\_GET array variable.

•Hyperlinks can have name=value pairs appended to submit data to a script using the GET method.

•A PHP script can send the browser to a new location using the header() function to set the HTTP location header URL.

•Data can be preserved in the PHP superglobal $\_SESSION array variable after calling the session\_start() function.

5

Assembling tables

***This chapter demonstrates how to make SQL statements that create MySQL database tables in which to store data.***

[**Introducing tables**](#chapter05.html#sec41)

[**Creating tables**](#chapter05.html#sec42)

[**Defining data types**](#chapter05.html#sec43)

[**Adding modifiers**](#chapter05.html#sec44)

[**Setting primary keys**](#chapter05.html#sec45)

[**Altering tables**](#chapter05.html#sec46)

[**Summary**](#chapter05.html#sec47)

**Introducing tables**

Databases are simply convenient storage containers that store data in a structured manner. Every database is composed of one or more tables that structure the data into organized rows and columns. This makes it easy to reference and manipulate the data.

Each database table column has a label to identify the data stored within the table cells in that column. Each row contains an entry called a “record” that places data in each cell along that row.

A typical simple database table looks like this:

![image](images/pg84_1.jpg)

The rows of a database table are not automatically arranged in any particular order, so they can be sorted alphabetically, numerically or by any other criteria. It is important, therefore, to have some means to identify each record in the table. The example above allocates a “member\_id” for this purpose and this unique identifier is known as the **PRIMARY KEY**.

Storing data in a single table is very useful, but relational databases with multiple tables introduce more possibilities by allowing the stored data to be combined in a variety of ways. For instance, the following two tables could be added to the database containing the first example table shown above:

![image](images/pg84_2.jpg)

The table on the left lists several video titles sorted numerically by “video\_id” number. The table on the right describes a relationship between the tables that links each member to the video they have rented. So Anne (member #2) has Titanic (video #1), John (member #1) has Star Wars (video #3) and Mike (member #3) has Men In Black (video #2).

![image](images/hot.jpg)

The column labels “member\_id” and “video\_id” include an underscore character because spaces are not allowed in labels.

In the MySQL Command Line Client you can display a list of all databases on your MySQL Server using this query:

**SHOW DATABASES ;**

To work with any database you must first tell the MySQL Server which database to use by issuing this query:

**USE *database-name ;***

Once the database has been selected it is possible to view a list of all the tables it contains with this query:

**SHOW TABLES ;**

![image](images/1o.jpg)Launch the MySQL Command Line Client, then enter the root password you chose during installation

![image](images/2o.jpg)At the **mysql>** command prompt, issue this query to list all databases that exist on your MySQL Server

**SHOW DATABASES ;**

![image](images/3o.jpg)Next, issue this query to use an existing database

**USE site\_db ;**

![image](images/4o.jpg)Now, issue a further query to display all tables that exist within the “site\_db” database

**SHOW TABLES ;**

![image](images/pg85_1.jpg)

![image](images/forget.jpg)

You created the database named “site\_db” after installation of the MySQL Server in chapter one – refer back to [here page 20](#chapter01.html#sec8).

![image](images/hot.jpg)

The **SHOW TABLES;** query in this example responds with an “empty set” message as there are no tables in the “site\_db” database yet – but you will create tables there throughout the rest of this book.

**Creating tables**

A MySQL database table is created by issuing this query:

**CREATE TABLE IF NOT EXISTS *table-name* ( *col type , col type* ) ;**

The statement in this query must be followed by parentheses containing a comma-separated list of column definitions – defining the name of each table column and the type of data that column may contain. For example, a table named “fruit” might contain three columns named “id”, “name” and “color”. The **INT** keyword could specify that the “id” column may only contain integer values and the **TEXT** keyword could specify that the “name” and “color” columns may only contain text values.

You can discover the format of any table using this query:

**EXPLAIN *table-name* ;**

A table may also be deleted from a database with this query:

**DROP TABLE IF EXISTS *table-name ;***

Issuing a query to create a table with many columns can be difficult to type accurately at the **mysql>** command prompt, so it is often better to create the query as an SQL text file first, then implement the query using the **SOURCE** keyword at the command prompt to identify the path to the file, such as within a “SQL” folder in your root system (C:\\) directory:

![image](images/pg86_1.jpg)

create\_table.sql

![image](images/1o.jpg)Launch a plain text editor, such as Notepad, and create a query defining the “fruit” table example described above

**CREATE TABLE IF NOT EXISTS fruit**

**(**

 
| **id** || **INT ,** |
| --- | --- |
| **name** || **TEXT ,** |
| **color** || **TEXT ,** |

**) ;**

![image](images/2o.jpg)Save the file in a folder at **C:\\SQL** as **create\_table.sql**, then launch the MySQL Command Line Client and log in as a user with full access privileges, such as root

![image](images/3o.jpg)Next, issue a query to use the established database

**USE site\_db ;**

![image](images/snake.jpg)

You may also see shorter **CREATE TABLE** and **DROP TABLE** queries used, but it is good practice to use these longer versions to check for existing tables.

![image](images/4o.jpg)Now, implement the SQL query by stating the source path to the SQL file on your system

**SOURCE** C:\\SQL\\create\_table.sql

![image](images/5o.jpg)Issue a query to confirm the table’s existence and format

**EXPLAIN fruit ;**

![image](images/6o.jpg)Finally, delete the table and confirm its removal

**DROP TABLE IF EXISTS fruit ;**

**SHOW TABLES ;**

![image](images/pg87_1.jpg)

The **EXPLAIN** query reveals the format of the “fruit” table, which allows the “id” field to contain integers up to 11 digits long – in actuality this is limited to values between -2147483648 and 2147483647.

In this example, “YES” denotes that each field is allowed to contain no value, defined by the **NULL** keyword. Each field has, in fact, been created with no default value, so does contain a **NULL** value. Note that **NULL** represents absolutely no value – this is not the same as an empty string that is represented by “”.

![image](images/hot.jpg)

MySQL queries use a version of the Structured Query Language (SQL) in which each query must end with a semi-colon, but the **SOURCE** keyword simply describes a path that must not end with a semi-colon.

![image](images/forget.jpg)

You can format the column definitions in an SQL file for better readability – additional spaces and line breaks are ignored.

**Defining data types**

The table below describes the range of data type specifiers that can be used to define database table columns. It is advisable to specify the permitted data type precisely. For instance, if a column only contains short strings, use **VARCHAR()** rather than **TEXT**.

 
| **Type:** || **Value:** |
| --- | --- |
| **INT** || An integer -2,147,483,648 to 2,147,483,647 |
| **DECIMAL** || A floating point number that can specify the number of permissible digits. For example,DECIMAL(5,2) permits -999.99 to 999.99 |
| **DOUBLE** || A double-precision floating point number |
| **DATE** || A date in the YYYY-MM-DD format |
| **TIME** || A time in the HH:MM:SS format |
| **DATETIME** || A combined date and time in the format YYYY-MM-DD HH:MM:SS |
| **YEAR** || A year 1901-2155 in either YY or YYYY format |
| **TIMESTAMP** || Automatic date and time of last record entry |
| **CHAR()** || A string of defined fixed length up to 255 characters long. For example, CHAR(100) pads a smaller string to make it 100 characters long |
| **VARCHAR()** || A string of variable length up to 255 characters long that is stored without padding |
| **TEXT** || A string up to 65,535 characters long |
| **BLOB** || A binary type for variable data |
| **ENUM** || A single string value from a defined list. For example, ENUM(“red”, “green”, “blue”) allows entry of any one of these three colors only |
| **SET** || A string or multiple strings from a defined list. For example, SET(“red”, “green”, “blue”) allows entry of any one, or more, of these colors |

![image](images/snake.jpg)

The **DECIMAL** data type parameters specify the total number of permissible digits, and the number of digits that may follow the decimal point – not the number of permissible digits for the decimal point’s left side and right side.

The SQL script listed opposite creates a table that includes data type specifiers in the column definitions. The “id” column only accepts integer values. The date and time of each entry can be recorded in the “date” column. The “first\_name” and “last\_name” columns may each contain up to 20 characters.

![image](images/1o.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with columns of various data types

**CREATE TABLE IF NOT EXISTS user\_log**

**(**

 
| **id** || **INT ,** |
| --- | --- |
| **date** || **TIMESTAMP ,** |
| **first\_name** || **VARCHAR(20) ,** |
| **last\_name** || **VARCHAR(20) ,** |

**) ;**

![image](images/pg89_1.jpg)

data\_types.sql

![image](images/2o.jpg)Save the file in a folder at **C:\\SQL** as **data\_types.sql**, then launch the MySQL Command Line Client and log in as a user with full access privileges, such as root

![image](images/3o.jpg)Next, issue a query to use the established database

USE site\_db ;

![image](images/4o.jpg)Now, implement the SQL query by stating the source path to the SQL file on your system

**SOURCE C:\\SQL\\data\_types.sql**

![image](images/5o.jpg)Issue a query to confirm the table’s existence and format

**EXPLAIN user\_log ;**

![image](images/pg89_2.jpg)

**Adding modifiers**

In addition to specifying permissible data types, with the keywords [here on the previous page](#chapter05.html#s1), the modifier keywords in the following table can optionally be used to further control column content:

 
| **Modifier:** || **Purpose:** |
| --- | --- |
| **NOT NULL** || Insists that each record must include a data value in this column |
| **UNIQUE** || Insists that records may not duplicate any entry in this column |
| **AUTO\_INCREMENT** || Available only for numeric columns, to automatically generate a number that is one more than the previous value in that column |
| **DEFAULT** || Specifies a value to be used where no value is stated for this column when a record is inserted |
| **PRIMARY KEY** || Specifies the column, or columns, to be used as the primary key for that table |

When it is essential that a record must include a value for a column, that column should be defined with the **NOT NULL** modifier. This allows an empty string “” to be stored there but does not allow that column to be empty or **NULL**. When the data stored in a column should never be duplicated that column should be defined with the **UNIQUE** modifier. For instance, to avoid the accidental duplication of product codes. The **AUTO\_INCREMENT** modifier is particularly useful to automatically generate incremental identity numbers for each row – the first row will be numbered 1, the second row 2, and so on. Setting a column **DEFAULT** allows records to be inserted without tediously requiring a value for a column that is usually constant. For instance, a “quantity” column might usually contain a value of 1 in each record – so 1 could be set as its default value.

The SQL script listed opposite creates a table that uses modifiers in its column definitions to control the permissible content. The “id” column automatically numbers each row and the “quantity” column will contain 1 unless another value is inserted. All the other columns must contain values – they can’t be empty or **NULL**.

![image](images/hot.jpg)

The **PRIMARY KEY** modifier is described in more detail [here on page 92](#chapter05.html#sec45).

![image](images/1o.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with columns of various modifiers

**CREATE TABLE IF NOT EXISTS product****s**

**(**

 
| **id** || **INT UNIQUE** || **AUTO\_INCREMENT ,** |
| --- | --- | --- |
| **code** || **INT** || **NOT NULL ,** |
| **name** || **VARCHAR(25)** || **NOT NULL ,** |
| **quantity** || **INT** || **DEFAULT 1 NULL ,** |
| **price** || **DECIMAL(6,2)** || **NOT NULL** |

**) ;**

![image](images/pg91_1.jpg)

modifiers.sql

![image](images/2o.jpg)Save the file in a folder at **C:\\SQL** as **modifiers.sql**, then launch the MySQL Command Line Client and log in as a user with full access privileges, such as root

![image](images/3o.jpg)Next, issue a query to use the established database

**USE site\_db ;**

![image](images/4o.jpg)Now, implement the SQL query by stating the source path to the SQL file on your system

**SOURCE C:\\SQL\\modifiers.sql**

![image](images/5o.jpg)Issue a query to confirm the table’s existence and format

**EXPLAIN products ;**

![image](images/pg91_2.jpg)

![image](images/hot.jpg)

The right-hand column in this illustration is headed “Extra”, and notes the “auto\_increment” modifier.

**Setting primary keys**

A **PRIMARY KEY** is a “constraint” that is applied to a column to uniquely identify each row of that database table. It ensures that the values in each row of that column are unique and never change, so those values can be used to reference any specific row.

By setting the **PRIMARY KEY** constraint it is possible to manipulate data on specific rows of the database table.

Any column can be set as the **PRIMARY KEY**, but it is often the first column that is used to provide a unique identifying number.

Any column set as the **PRIMARY KEY** must meet these criteria:

•Each field in that column must have a value – it may not be empty or have a **NULL** value.

•Each value in that column must be unique – there must be no duplications.

•Each value in that column can never be modified or updated.

•Each value in that column cannot be re-used – when a row is deleted its **PRIMARY KEY** value cannot be re-assigned as the **PRIMARY KEY** value of a new row.

Notice in the previous example that MySQL automatically sets the “id” column as the **PRIMARY KEY** because of the **UNIQUE** modifier that was included in that column’s definition. This is indicated in the output from the **EXPLAIN** query, [here on page 91](#chapter05.html#query91), by the term “PRI” listed under the “Key” heading. This is logical because any column that may only contain unique values can be used to identify each table row by that column’s value.

The **PRIMARY KEY** constraint can be set by adding the **PRIMARY** **KEY** keywords to the column definition in the **CREATE TABLE** query. Alternatively, a **PRIMARY KEY** can be set elsewhere in the **CREATE TABLE** query by stating the name of the column in parentheses after the **PRIMARY KEY** keywords.

The SQL script on the opposite page creates two tables with a **PRIMARY KEY** column set by different methods. Each table can reference any specific row by its “id” value. Notice that the **EXPLAIN** queries confirm both **PRIMARY KEY** settings.

![image](images/forget.jpg)

A table’s **PRIMARY** **KEY** must be a unique constant value.

![image](images/1o.jpg)Launch a plain text editor such as Notepad, and create a query defining two tables with specified primary keys

**CREATE TABLE IF NOT EXISTS cups**

**(**

 
| **id** || **INT AUTO\_INCREMENT** || **PRIMARY KEY ,** |
| --- | --- | --- |
| **cup\_pattern** || **VARCHAR(25)** ||   |

**) ;**

**CREATE TABLE IF NOT EXISTS pots**

**(**

| **id** || **INT** || **AUTO\_INCREMENT ,** |
| :-- | :-- | :-- |
| **pot\_pattern** || **VARCHAR(25) , PRIMARY KEY(** id ) |

**) ;**

![image](images/pg93_1.jpg)

primary\_key.sql

![image](images/2o.jpg)Save the file in a folder at **C:\\SQL** as **primary\_key.sql**, then log in to the MySQL Command Line Client as root, and issue a query to use the established database

**USE site\_db ;**

![image](images/3o.jpg)Now, implement the SQL query by stating the source path to the SQL file on your system

**SOURCE C:\\SQL\\primary\_key.sql**

![image](images/4o.jpg)Issue a query to confirm the tables’ existence and format

**EXPLAIN cups ; EXPLAIN pots ;**

![image](images/pg93_2.jpg)

**Altering tables**

The format of an existing database table can be changed with an **ALTER TABLE** query. This query can make a single alteration or specify a number of alterations as a comma-separated list.

An **ALTER TABLE** query can **ADD** a complete new **COLUMN** to an existing table, like this:

**ALTER TABLE *table-name ;***

**ADD COLUMN *column-name data-type optional-modifier/s ;***

It can also **ADD** a **PRIMARY KEY** to an existing column definition using this syntax:

**ALTER TABLE *table-name ;***

**ADD PRIMARY KEY ( *column-name* ) ;**

An **ALTER TABLE** query can **CHANGE** the name of an existing column. The new column will not inherit any data type or modifiers specified to the original column – these must be set anew in the **ALTER TABLE** query, like this:

**ALTER TABLE *table-name ;***

**CHANGE *old-column-name new-column-name***

***data-type optional-modifier/s ;***

An **ALTER TABLE** query can also permanently delete an entire column from the table using the **DROP COLUMN** keywords:

**ALTER TABLE *table-name ;***

**DROP COLUMN *column-name ;***

![image](images/hot.jpg)

In the **ADD COLUMN** and **DROP COLUMN** examples, the **COLUMN** keyword is optional – it is what the manual calls “a pure noise word” that is only there to aid readability.

The following SQL script demonstrates all these possibilities:

![image](images/1o.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with three columns

**CREATE TABLE IF NOT EXISTS pans**

**(**

 
| **id** || **INT** || **NOT NULL ,** |
| --- | --- | --- |
| **pattern** || **VARCHAR(25)** || **NOT NULL ,** |
| **price** || **DECIMAL( 6,2 )** ||   |

**) ;**

![image](images/pg94_1.jpg)

alter\_table.sql

![image](images/2o.jpg)Next, add a query to confirm the table’s format

**EXPLAIN pans ;**

![image](images/3o.jpg)Now, add a query to update the table

**ALTER TABLE pans**

**ADD PRIMARY KEY ( id ) ,**

**ADD COLUMN code INT UNIQUE NOT NULL ,**

**CHANGE pattern pan\_pattern VARCHAR(25) NOT NULL ,**

DROP COLUMN price ;

![image](images/4o.jpg)Finally, add a query to confirm the altered table format

**EXPLAIN pans ;**

![image](images/5o.jpg)Save the file in a folder at **C:\\SQL** as **alter\_table.sql**, then log in to the MySQL Command Line Client as root and issue a query to use the established database

**USE site\_db ;**

![image](images/6o.jpg)Implement the SQL query by stating the source path to the SQL file on your system

**SOURCE C:\\SQL\\alter\_table.sql**

![image](images/pg95_1.jpg)

![image](images/snake.jpg)

Care should be taken in using **DROP COLUMN** as it will remove any data that is contained in that column – the data cannot be recovered.

![image](images/forget.jpg)

Well-designed database tables should never need to be altered if they anticipate all likely future requirements.

**Summary**

•The **USE DATABASE** query selects a database to work with.

•The names of all the tables in a database can be revealed with the **SHOW TABLES** query.

•The format of a table can be examined with an **EXPLAIN** query.

•A new table can be created with the **CREATE TABLE** query.

•The **CREATE TABLE** query can be qualified with **IF NOT EXISTS** to ensure that a table of the specified name does not already exist.

•An existing table can be deleted with a **DROP TABLE** query.

•The **DROP TABLE** query can be qualified with **IF EXISTS** to ensure that a table of the specified name already exists.

•A column definition should specify the data type that it may contain, using recognized data type keywords such as **INT**,**DOUBLE**, **DECIMAL**, **DATETIME**, **TIMESTAMP**, **DATE**, **TIME**, **YEAR**, **CHAR()**, **VARCHAR()**, **TEXT**, **BLOB**, **ENUM** or **SET**.

•Optionally, a column definition may specify a field modifier to further control that column’s permissible content to make it **NOT NULL**, **AUTO\_INCREMENT**, **UNIQUE**, **DEFAULT** or **PRIMARY KEY**.

•When a column is set as a **PRIMARY KEY**, each row must contain unique unalterable data in that column, which can be used to identify each row of that table.

•An **ALTER TABLE** query can be used to **ADD** a new column to an existing table.

•An **ALTER TABLE** query can be used to **CHANGE** a column in an existing table.

•An **ALTER TABLE** query can be used to delete a column from an existing table with the **DROP** keyword.

6

**Handling data**

***This chapter demonstrates how to make SQL statements to store and retrieve data with MySQL database tables.***

[**Inserting data**](#chapter06.html#sec48)

[**Updating columns**](#chapter06.html#sec49)

[**Updating fields**](#chapter06.html#sec50)

[**Deleting data**](#chapter06.html#sec51)

[**Selecting data**](#chapter06.html#sec52)

[**Retrieving columns**](#chapter06.html#sec53)

[**Retrieving rows**](#chapter06.html#sec54)

[**Sorting data**](#chapter06.html#sec55)

[**Setting direction**](#chapter06.html#sec56)

[**Making comparisons**](#chapter06.html#sec57)

[**Summary**](#chapter06.html#sec58)

**Inserting data**

Data can be inserted into an existing database table with an INSERT INTO query that first specifies the table name. The SQL VALUES keyword then specifies the actual data to be inserted as a comma-separated list within parentheses, like this:

**INSERT INTO *table-name* VALUES ( *value , value* ) ;**

Each INSERT INTO query inserts just one row into the database table. A data value must be specified for each column – and in the corresponding order. The data to be inserted must also match the data type in each column’s definition or an error will be generated. The NULL keyword can be specified to leave a field empty if that column’s definition allows NULL values.

The INSERT INTO query can be improved by adding a “columns list” to explicitly specify the table column into which each value should be inserted. This changes the syntax of the INSERT INTO query to look like this:

**INSERT INTO *table-name* ( *column-name , column-name* )  
VALUES ( *value , value* ) , ( *value , value* ) , ( *value , value* ) ;**

When the INSERT INTO query contains a columns list, the MySQL Server matches each value to the specified column in the order in which they are listed – the value listed first will be matched to the column listed first, the value listed second will be matched to the column listed second, and so on. The number of listed values must match the number of listed columns, but the columns need not be listed in the order in which they appear in the database table. Additionally, a columns list need not list all the columns in the table, providing that omitted columns allow NULL values. This allows an INSERT INTO query to insert only partial rows.

It is strongly recommended that all INSERT INTO queries should include a columns list so that the query may remain valid in the event that the table gets altered.

All data contained in a table can be displayed with a SELECT query using the \* wildcard, and the FROM keyword, like this:

**SELECT \* FROM *table-name* ;**

The SQL script opposite creates a table then inserts some data into its columns before selecting the entire content for display.

![image](images/snake.jpg)

Any text values to be inserted into a database must be enclosed within quotation marks.

![image](images/pg99_1.jpg)

insert\_data.sql

![image](images/1bl.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with three columns

CREATE TABLE IF NOT EXISTS prints

**(**

 
| **id** || **INT AUTO\_INCREMENT PRIMARY KEY ,** |
| --- | --- |
| **name** || **VARCHAR(32) ,** |
| **price** || **DECIMAL(6,2)** |

**) ;**

![image](images/2bl.jpg)Next, add a query to insert three records into this table

INSERT INTO prints ( name , price )

VALUES ( “Merry Structure” , 29.99 ) ,

( “Heavy Red” , 24.99 ) , ( “Black Lines” , 45.99 ) ;

![image](images/3bl.jpg)Now, add a query to display all records from this table

SELECT \* FROM prints ;

![image](images/4bl.jpg)Save the file in a folder at C:\\SQL as insert\_data.sql, then launch the MySQL Command Line Client and issue a query to use the established database

USE site\_db ;

![image](images/5bl.jpg)Now, implement the SQL query by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\insert\_data.sql

![image](images/pg99_2.jpg)

![image](images/forget.jpg)

Always include a columns list when inserting data into a table to explicitly specify where the data should be placed.

**Updating columns**

All the data contained within a column of a database table can be changed with an UPDATE query, which has this syntax:

**UPDATE *table-name* SET *column-name* = *value* ;**

The UPDATE keyword is followed by the name of the table to work with, and the SET keyword specifies the name of the column to be updated with a new specified value.

Note that this SQL query will update every field in the specified column with the single specified value.

![image](images/pg100_1.jpg)

update\_all.sql

![image](images/1bl.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with four columns

CREATE TABLE IF NOT EXISTS towels

**(**

 
| **id** || INT AUTO\_INCREMENT PRIMARY KEY , |
| --- | --- |
| name || **CHAR(16) ,** |
| **color** || **CHAR(16) ,** |
| **price** || **DECIMAL(6,2)** |

**) ;**

![image](images/2bl.jpg)Next, add a query to insert five records into this table

INSERT INTO towels ( name , color , price )

VALUES ( “Dolphin” , “Blue” , 9.99 ) ,

( “Wine” , “Maroon” , 12.99 ) ,

( “Harvest” , “Beige” , 7.99 ) ,

( “Daisy” , “Lilac” , 8.99 ) ,

( “Starburst” , “Yellow” , 10.99 ) ;

![image](images/3bl.jpg)Now, add a query to display all records from this table

SELECT \* FROM towels ;

![image](images/4bl.jpg)Add queries to update the “color” column of this table and display all records to see the updated version

UPDATE towels SET color \= “White” ;

SELECT \* FROM towels ;

![image](images/5bl.jpg)Add queries to update the “price” column of this table and display all records to see the updated version again

UPDATE towels SET price \= 5.99 ;

SELECT \* FROM towels ;

![image](images/6bl.jpg)Save the file in a folder at C:\\SQL as update\_all.sql, then launch the MySQL Command Line Client and issue a query to use the established database

USE site\_db ;

![image](images/7bl.jpg)Now, implement the SQL queries by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\update\_all.sql

![image](images/pg101_1.jpg)

![image](images/hot.jpg)

It is sometimes useful to remove all values in a column using an **UPDATE** query to set each field to **NULL** – providing the column definition allows **NULL** values.

**Updating fields**

Usually an UPDATE query will be required to change data contained in a particular field of a column on a specific row. The row can be identified by adding the WHERE keyword to the UPDATE query to match a value in a specified column. The syntax of the specific UPDATE query now looks like this:

**UPDATE *table-name***

**SET *column-name* = *value* WHERE *column-name* = *value* ;**

A single UPDATE query can also change multiple column values on a specific row by making multiple *column-name = value* statements as a comma-delimited list after the SET keyword.

If the WHERE keyword identifies multiple rows that each have the same specified value they will each get updated with the new value – possibly causing accidental data loss. It is therefore safer to identify the row by its PRIMARY KEY value, as this is guaranteed to be unique so multiple rows cannot be accidentally updated.

![image](images/pg102_1.jpg)

update\_where.sql

![image](images/1bl.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with four columns

CREATE TABLE IF NOT EXISTS tiles

**(**

 
| **id** || **INT AUTO\_INCREMENT PRIMARY KEY ,** |
| --- | --- |
| **pattern** || **CHAR(16) ,** |
| **color** || **CHAR(16) ,** |
| **price** || **DECIMAL(6,2)** |

**) ;**

![image](images/2bl.jpg)Next, add a query to insert four records into this table

INSERT INTO tiles ( pattern , color , price )

VALUES ( “Spring” , “Green” , 9.99 ) ,

( “Summer” , “Yellow” , 12.99 ) ,

( “Autumn” , “Brown” , 9.99 ) ,

( “Winter” , “Blue” , 8.99 ) ;

![image](images/3bl.jpg)Now, add a query to display all records from this table

SELECT \* FROM tiles ;

![image](images/4bl.jpg)Add a query to update the “pattern” column of this table by identifying its current value

UPDATE tiles

SET pattern \= “Fall” WHERE pattern \= “Autumn” ;

![image](images/snake.jpg)

If the **WHERE** keyword is omitted from an **UPDATE** query, all rows will be updated – lost data cannot be recovered.

![image](images/5bl.jpg)Add queries to update other columns by identifying the current “color”, “price”, and “id” values and display them

UPDATE tiles SET color \= “Gold” WHERE color \= “Yellow” ;

UPDATE tiles SET price \= 10.99 WHERE price \= 9.99 ;

UPDATE tiles SET price \= 11.99 WHERE id \= 4 ;

SELECT \* FROM tiles ;

![image](images/6bl.jpg)Save the file in a folder at C:\\SQL as update\_where.sql, then launch the MySQL Command Line Client and issue a query to use the established database

USE site\_db ;

![image](images/7bl.jpg)Now, implement the SQL queries by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\update\_where.sql

![image](images/pg103_1.jpg)

![image](images/hot.jpg)

Always attempt to **UPDATE** tables by identifying the row by its **PRIMARY KEY** value.

**Deleting data**

Rows can be removed from a database table with a DELETE FROM query. All rows can be removed with this syntax:

**DELETE FROM *table-name* ;**

More usually, a specific row can be removed from a table by adding the WHERE keyword to a DELETE FROM query to identify the row. The syntax of the DELETE FROM query now looks like this:

**DELETE FROM *table-name* WHERE *column-name* = *value* ;**

If the WHERE keyword identifies multiple rows that each have the same specified value they will each get deleted – possibly causing accidental data loss. It is therefore safer to identify the row by its PRIMARY KEY value, as this is guaranteed to be unique, so multiple rows cannot be accidentally deleted.

![image](images/pg104_1.jpg)

delete\_from.sql

![image](images/1bl.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with four columns

CREATE TABLE IF NOT EXISTS pens

**(**

 
| **id** || **INT AUTO\_INCREMENT PRIMARY KEY ,** |
| --- | --- |
| **maker** || **CHAR(32) ,** |
| **model** || **CHAR(32) ,** |
| **price** || **DECIMAL(6,2)** |

**) ;**

![image](images/2bl.jpg)Next, add a query to insert four records into this table

INSERT INTO pens ( maker , model , price )

VALUES ( “Montegrappa” , “Silver Dragon” , 950.00 ) ,

( “Paul Rossi” , “Egyptian Lady” , 650.00 ) ,

( “Michel Perchin” , “Red Cross” , 450.00 ) ,

( “Bexley” , “Poseidon Magnum” , 350.00 ) ;

![image](images/3bl.jpg)Now, add a query to display all records from this table

SELECT \* FROM pens ;

![image](images/4bl.jpg)Add queries to individually delete rows by various column values then display the remaining records

DELETE FROM pens WHERE maker \= “Montegrappa” ;

SELECT \* FROM pens ;

DELETE FROM pens WHERE model \= “Egyptian Lady” ;

SELECT \* FROM pens ;

DELETE FROM pens WHERE price \= 450.00 ;

SELECT \* FROM pens ;

DELETE FROM pens WHERE id \= 4 ; SELECT \* FROM pens ;

![image](images/forget.jpg)

The **DELETE** keyword cannot be used to remove a table – you must use the **DROP** keyword for removal.

![image](images/5bl.jpg)Save the file in a folder at C:\\SQL as delete\_from.sql, then launch the MySQL Command Line Client and issue a query to use the established database

USE site\_db ;

![image](images/6bl.jpg)Now, implement the SQL queries by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\delete\_from.sql

![image](images/pg105_1.jpg)

![image](images/snake.jpg)

If the **WHERE** keyword is omitted from a **DELETE FROM** query, all rows will be deleted – lost data cannot be recovered.

**Selecting data**

The SQL query to view all data in a database table was introduced at the start of this chapter. The wildcard \* character, meaning “all”, can be replaced with a column name to retrieve only data from that particular column. The syntax of this query looks like this:

**SELECT *column-name* FROM *table-name* ;**

The following script creates and displays an entire table then selects individual columns for display.

![image](images/pg106_1.jpg)

selection.sql

![image](images/1bl.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with four columns

CREATE TABLE IF NOT EXISTS paintings

**(**

 
| **id** || **INT AUTO\_INCREMENT PRIMARY KEY ,** |
| --- | --- |
| **artists** || **CHAR(32) ,** |
| **titles** || **CHAR(64) ,** |
| **styles** || **CHAR(16)** |

**) ;**

![image](images/2bl.jpg)Next, add a query to insert four records into this table

INSERT INTO paintings ( artists , titles , styles )

**VALUES**

( “Salvador Dali” , “Meditative Rose” , “Surrealist” ) ,

( “Henri Matisse” , “Blue Hair” , “Impressionist” ) ,

( “Pablo Picasso” , “Girl Reading” , “Cubist” ) ,

( “Marc Chagall” , “Bonjour Paris” , “Primitivist” ) ;

![image](images/3bl.jpg)Now, add a query to display all records from this table

SELECT \* FROM paintings ;

![image](images/4bl.jpg)Add a query to individually display the “artists” column

SELECT artists FROM paintings ;

![image](images/5bl.jpg)Add a query to individually display the “titles” column

SELECT titles FROM paintings ;

![image](images/6bl.jpg)Add a query to individually display the “styles” column

SELECT styles FROM paintings ;

![image](images/7bl.jpg)Save the file in a folder at C:\\SQL as selection.sql, then launch the MySQL Command Line Client and issue a query to use the established database

USE site\_db ;

![image](images/8bl.jpg)Now, implement the SQL queries by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\selection.sql

![image](images/pg107_1.jpg)

![image](images/forget.jpg)

Notice that the data is retrieved in the same “top-down” order as it is stored in each column.

**Retrieving columns**

A SELECT query can return the data from multiple columns by including the required column names as a comma-separated list in the query. The syntax to get multiple column data looks like this:

**SELECT *column-name* , *column-name* FROM *table-name* ;**

The following script creates and displays an entire table then selects multiple columns for display.

![image](images/pg108_1.jpg)

select\_columns.sql

![image](images/1bl.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with four columns

CREATE TABLE IF NOT EXISTS phones

**(**

 
| **id** || **INT AUTO\_INCREMENT PRIMARY KEY ,** |
| --- | --- |
| **make** || **CHAR(16) ,** |
| **model** || **CHAR(16) ,** |
| **platform** || **CHAR(16)** |

**) ;**

![image](images/2bl.jpg)Next, add a query to insert four records into this table

INSERT INTO phones ( make , model , platform )

**VALUES**

( “Apple” , “iPhone” , “iOS” ) ,

( “RIM” , “Curve” , “BlackBerry” ) ,

( “HTC” , “Desire” , “Android” ) ,

( “Nokia” , “Lumia” , “Windows” ) ;

![image](images/3bl.jpg)Now, add a query to display all records from this table

SELECT \* FROM phones ;

![image](images/4bl.jpg)Add a query to display the “id” and “make” columns

SELECT id , make FROM phones ;

![image](images/5bl.jpg)Add a query to display the “make” and “model” columns

SELECT make , model FROM phones ;

![image](images/6bl.jpg)Add a query to display the “id” and “platform” columns

SELECT id , platform FROM phones ;

![image](images/7bl.jpg)Save the file in a folder at C:\\SQL as select\_columns.sql, then launch the MySQL Command Line Client and issue a query to use the established database

USE site\_db ;

![image](images/8bl.jpg)Now, implement the SQL queries by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\select\_columns.sql

![image](images/pg109_1.jpg)

![image](images/forget.jpg)

**SELECT** queries only retrieve a copy of data contained in the specified table – the table is unaltered.

**Retrieving rows**

A SELECT query can retrieve a specific row from a database table if it includes the WHERE keyword to identify the required row. The row should be identified by its PRIMARY KEY value to prevent possible duplication. The syntax of a SELECT query to retrieve a specific row looks like this:

**SELECT \* FROM *table-name* WHERE *column-name* = *value* ;**

Additionally, a WHERE clause in a SELECT query can specify a list of alternative values for comparison with column data using the IN keyword. This is followed by a comma-separated list of values within a single pair of parentheses. So the syntax looks like this:

**SELECT \* FROM *table-name***

**WHERE *column-name* IN ( *value , value , value* ) ;**

When the column data matches any one of the values in the list, the WHERE clause evaluates as TRUE, and data is returned for that row. The comparison can be inverted by preceding the IN keyword with the NOT keyword. Then the WHERE clause only evaluates as TRUE when no list value matches the column data.

![image](images/pg110_1.jpg)

select\_rows.sql

![image](images/1bl.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with four columns

CREATE TABLE IF NOT EXISTS coffee\_machines

**(**

 
| **id** || **INT AUTO\_INCREMENT PRIMARY KEY ,** |
| --- | --- |
| **make** || **CHAR(16) ,** |
| **model** || **CHAR(16) ,** |
| **price** || **DECIMAL(6,2)** |

**) ;**

![image](images/2bl.jpg)Next, add a query to insert five records into this table

INSERT INTO coffee\_machines ( make , model , price )

**VALUES**

( “Krups” , “Dolce Gusto” , 140.00 ) ,

( “Gaggia” , “Cubika” , 170.00 ) ,

( “DeLonghi” , “Magnifica” , 500.00 ) ,

( “Magimix” , “Nespresso” , 300.00 ) ,

( “Cuisinart” , “Espresso” , 280.00 ) ;

![image](images/3bl.jpg)Now, add a query to display one row from this table

SELECT \* FROM coffee\_machines WHERE id \= 3 ;

![image](images/4bl.jpg)Add a query to display two particular rows

SELECT \* FROM coffee\_machines

WHERE make IN ( “Krups” , “Gaggia” ) ;

![image](images/5bl.jpg)Finally, add a query to display all other rows

SELECT \* FROM coffee\_machines

WHERE make NOT IN ( “Krups” , “Gaggia” ) ;

![image](images/6bl.jpg)Save the file in a folder at C:\\SQL as select\_rows.sql, then launch the MySQL Command Line Client and issue a query to use the established database

USE site\_db ;

![image](images/7bl.jpg)Now, implement the SQL queries by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\select\_rows.sql

![image](images/pg111_1.jpg)

![image](images/hot.jpg)

SQL queries comprise one or more “clauses”. Each clause consists of a keyword and data. For instance, **WHERE id = 3** is known as a **WHERE** clause.

**Sorting data**

The data returned by a SELECT query can be explicitly sorted into a specified order using an ORDER BY clause, with this syntax:

**SELECT *column-name* FROM *table-name* ORDER BY *column-name* ;**

When the ORDER BY keywords are followed by a table column name, the retrieved data will be sorted into order based upon the type of data in the specified column. Typically, if the column data type is numerical, the retrieved data will be sorted in ascending numerical order. If the column data type is textual, the retrieved data will be sorted into alphabetical order from A through Z.

The SQL example script listed below demonstrates both numerical and alphabetical sorting of retrieved data.

![image](images/pg112_1.jpg)

order\_by.sql

![image](images/1bl.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with four columns

CREATE TABLE IF NOT EXISTS watches

**(**

 
| **id** || **INT AUTO\_INCREMENT PRIMARY KEY ,** |
| --- | --- |
| **model** || **CHAR(16) ,** |
| **style** || **CHAR(16) ,** |
| **price** || **DECIMAL(6,2)** |

**) ;**

![image](images/2bl.jpg)Next, add a query to insert five records into this table

INSERT INTO watches ( model , style , price )

**VALUES**

( “Boston” , “Gents” , 70.00 ) ,

( “Avante” , “Ladies” , 90.00 ) ,

( “Club” , “Gents” , 60.00 ) ,

( “Denver” , “Ladies” , 80.00 ) ,

( “Eton” , “Gents” , 50.00 ) ;

![image](images/3bl.jpg)Now, add a query to display all columns of all records in this table, sorted by ascending “price” order

SELECT \* FROM watches ORDER BY price ;

![image](images/4bl.jpg)Add a query to display all models and prices in this table, sorted by alphabetical “model” order

SELECT model , price FROM watches ORDER BY model ;

![image](images/5bl.jpg)Finally, add a query to display all models and styles in this table, sorted by alphabetical “style” order

SELECT model , style FROM watches ORDER BY style ;

![image](images/6bl.jpg)Save the file in a folder at C:\\SQL as order\_by.sql, then launch the MySQL Command Line Client and issue a query to use the established database

USE site\_db ;

![image](images/7bl.jpg)Now, implement the SQL queries by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\order\_by.sql

![image](images/pg113_1.jpg)

![image](images/snake.jpg)

An **ORDER BY** clause must only appear as the final clause of a **SELECT** query – otherwise an error is generated.

![image](images/hot.jpg)

Data retrieved from a column can be sorted by the order of another column whose data is not actually retrieved.

**Setting direction**

By default, SELECT queries are automatically sorted in ascending order. An ORDER BY clause can explicitly specify the sort direction by adding the keywords DESC (descending) or ASC (ascending) after the name of the column to sort by, with this syntax:

**SELECT *column-name* , *column-name***

**FROM *table-name***

**ORDER BY *column-name* DESC ;**

In the SQL script listed below, the ASC and DESC keywords are used to determine the sort direction for three columns of data.

![image](images/pg114_1.jpg)

sort\_direction.sql

![image](images/1bl.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with three columns

CREATE TABLE IF NOT EXISTS top\_5\_films

**(**

 
| **position** || **INT PRIMARY KEY ,** |
| --- | --- |
| **title** || **CHAR(32) NOT NULL ,** |
| **year** || **INT NOT NULL** |

**) ;**

![image](images/2bl.jpg)Next, add a query to insert five records into this table

INSERT INTO top\_5\_films ( position , title , year )

VALUES

( 1 , “Citizen Kane” , 1941 ) ,

( 2 , “Casablanca” , 1942 ) ,

( 3 , “The Godfather” , 1972 ) ,

( 4 , “Gone With The Wind” , 1939 ) ,

( 5 , “Lawrence Of Arabia” , 1962 ) ;

![image](images/3bl.jpg)Now, add a query to display all columns of all records in this table, sorted by descending “position” order

SELECT \* FROM top\_5\_films ORDER BY position DESC ;

![image](images/4bl.jpg)Add a query to display all years and titles in this table, sorted by ascending “year” order

SELECT year , title FROM top\_5\_films ORDER BY year ASC ;

![image](images/5bl.jpg)Finally, add a query to display all titles and years in this table, sorted by alphabetical “title” order

SELECT title , year FROM top\_5\_films ORDER BY title ASC ;

![image](images/hot.jpg)

Opinion may be divided on the top five films of all time – the data in this example represents the choice of the American Film Institute.

![image](images/6bl.jpg)Save the file in a folder at C:\\SQL as sort\_direction.sql, then launch the MySQL Command Line Client and issue a query to use the established database

USE site\_db ;

![image](images/7bl.jpg)Now, implement the SQL queries by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\sort\_direction.sql

![image](images/pg115_1.jpg)

![image](images/hot.jpg)

By default, the sort order is not case-sensitive, but using **ORDER BY BINARY** gives precedence to uppercase characters in the sort order.

**Making comparisons**

Like PHP, MySQL has built-in operators and functions that can be used to provide fast filtration of data stored in a database. Using these is highly recommended, as it is more efficient than having an SQL query retrieve all data for filtration by PHP. Comparison operators available in MySQL are listed below:

 
| **Operator:** || **Description:** |
| --- | --- |
| \= || Equality |
| != || Inequality |
| < || Less than |
| <= || Less than or equal |
| \> || More than |
| \>= || More than or equal |
| **BETWEEN** min **AND** max || Within the range min to max |
| **IS NULL** || Is a NULL value |
| **IS NOT NULL** || Is not a NULL value |

Comparison operators are used in a query with a WHERE clause to test if a specified condition is met. When the evaluation is TRUE, the query will return the data, otherwise nothing will be returned.

Usefully, the built-in MySQL NOW() function returns the current date and time in the format YYYY-MM-DD HH:MM:SS, which provides a timestamp of when the database was accessed. Additionally, the built-in MySQL SHA2() cryptographic hash function allows passwords to be stored securely. This takes two arguments to specify a password and hash string length to return of 224, 256, 384, or 512 bits (256 bits returns 64 hex characters).

![image](images/pg116_1.jpg)

comparison.sql

![image](images/1bl.jpg)Launch a plain text editor such as Notepad, and create a query defining a table with five columns

CREATE TABLE IF NOT EXISTS items

**(**

| **id** || **INT AUTO\_INCREMENT PRIMARY KEY ,** |
| :-- | :-- |
| **name** || **CHAR(16)** || **NOT NULL ,** |
| **quantity** || **INT** || **NOT NULL ,** |
| **pass** || **TEXT(256) NOT NULL ,** || **NOT NULL ,** |
| **stamp** || **DATETIME** || **NOT NULL** |

**) ;**

![image](images/hot.jpg)

Discover more MySQL built-in features in the MySQL 8 Reference Manual online at [dev.mysql.com/doc/refman/8.0/en](https://dev.mysql.com/doc/refman/8.0/en/)

![image](images/2bl.jpg)Next, add a query to insert four records into this table

INSERT INTO items ( name , quantity , pass , stamp )

VALUES ( “Alan” , 10 , SHA2( “m00nriver”, 256) , NOW() ) ,

( “Dean” , 20 , SHA2( “bluem00n”, 256 ) , NOW() ) ,

( “Gary” , 30 , SHA2( “m00nlight”, 256 ) , NOW() ) ,

( “Mike” , 40 , SHA2( “m00nshine”, 256 ) , NOW() ) ;

![image](images/3bl.jpg)Now, add a query to display names and quantities by comparing “quantity” values

SELECT name , quantity FROM items

WHERE quantity BETWEEN 15 AND 35 ;

![image](images/4bl.jpg)Add a query to display one timestamp and checksum

SELECT stamp , pass FROM items WHERE quantity < 15 ;

![image](images/5bl.jpg)Save the file in a folder at C:\\SQL as comparison.sql, then launch the MySQL Command Line Client and issue a query to use the established database

USE site\_db ;

![image](images/6bl.jpg)Now, implement the SQL queries by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\comparison.sql

![image](images/pg117_1.jpg)

![image](images/forget.jpg)

The timestamp returned by the **NOW()** function will be the current time on the server, which may differ from the local time of the user’s timezone.

**Summary**

•Data is inserted into a database table by an INSERT INTO query.

•The VALUES keyword in an INSERT INTO query specifies a list of comma-separated values within a single pair of parentheses.

•Text data values must be surrounded by quotes.

•All data is retrieved from a table with a SELECT \* FROM query.

•All the fields in a column can be changed with an UPDATE query.

•The WHERE keyword can be added to an UPDATE query to identify a specific row where a field is to be changed.

•The SET keyword is used in an UPDATE query to change one or more fields in a row.

•All the rows in a table can be deleted with a DELETE query.

•The WHERE keyword can be added to a DELETE query to identify a specific row that is to be deleted.

•All tables should nominate a column to contain a PRIMARY KEY.

•Multiple column data can be retrieved by stating the column names as a comma-delimited list in a SELECT query.

•A specific row can be retrieved from a table by adding the WHERE keyword to a SELECT query to identify the row.

•A WHERE clause can specify a comma-separated list of alternative comparison values in parentheses following the IN keyword.

•Data can be returned from rows that do not match any of the list of values by adding a NOT keyword before the IN keyword.

•An ORDER BY clause can specify columns to sort by, and specify how to sort retrieved data with the ASC and DESC keywords.

•MySQL has comparison operators like those in PHP.

•The built-in MySQL NOW() function provides a timestamp, and the built-in SHA2() function stores passwords securely.

7

Connecting databases

***This chapter demonstrates how to connect to MySQL databases and make SQL queries from PHP scripts.***

[**Making connection**](#chapter07.html#sec59)

[**Executing queries**](#chapter07.html#sec60)

[**Retrieving results**](#chapter07.html#sec61)

[**Applying changes**](#chapter07.html#sec62)

[**Counting records**](#chapter07.html#sec63)

[**Updating records**](#chapter07.html#sec64)

[**Validating results**](#chapter07.html#sec65)

[**Ensuring security**](#chapter07.html#sec66)

[**Handling errors**](#chapter07.html#sec67)

[**Summary**](#chapter07.html#sec68)

**Making connection**

The standard script to connect to the MySQL Server from PHP was described in Chapter 1 when you configured the development environment and is repeated below for explanation:

**<?php**

**$dbc \=**

**mysqli\_connect( *‘host’ , ‘user’ , ‘password’ , ‘database’* )**

**OR die ( mysqli\_connect\_error() ) ;**

mysqli\_set\_charset( $dbc , ‘utf8’ ) ;

![image](images/pg120_1.jpg)

connect\_db.php

The script defines a PHP variable named “dbc” (database connection) that gets assigned the value returned by the built-in mysqli\_connect() function. This call requires four arguments to specify the MySQL user details and the database to connect. When the call succeeds, the mysqli\_connect() function returns an “object” that represents the connection to the MySQL Server.

The object returned by a successful call to mysqli\_connect() is very important, as it is used as an argument in other PHP function calls that communicate with the MySQL Server. For example, in the above script it must be used as the first argument in the call to the mysqli\_set\_charset() function to identify the connection.

When the call to the mysqli\_connect() function fails, the script branches to an alternative that calls the die() function. This is equivalent to calling exit() to immediately terminate the script. Optionally, the die() function can accept a string argument that will be printed out as the scripts halts. In this case, the string message is returned by the mysqli\_connect\_error() function that describes why the connection attempt failed.

As the connection script contains sensitive user details it must not be placed alongside other PHP scripts in your web servers /htdocs directory. The connect\_db.php script should instead be located in the parent directory of /htdocs, where it is not directly accessible but can be incorporated into other PHP scripts by a require statement, like this:

**<?php**

**require ( ‘../connect\_db.php’ ) ;**

**if ( mysqli\_ping( $dbc ) )**

**{**

**echo ‘MySQL Server ‘ . mysqli\_get\_server\_info( $dbc ) .**

**‘ on ‘ . mysqli\_get\_host\_info( $dbc ) ;**

**}**

![image](images/pg120_2.jpg)

require.php

The files in your web server’s directory structure should therefore be arranged in the hierarchy depicted below, so when you request the require.php script via HTTP the connect\_db.php script gets incorporated from its location in the parent directory, and the connection gets made to the MySQL Server.

![image](images/pg121_1.jpg)

![image](images/pg121_2.jpg)

![image](images/hot.jpg)

Files that contain only pure PHP code, like both those listed here, should omit the PHP **?>** closing tag at the end of the file. This prevents accidental whitespace or new lines after the PHP closing tag, which may cause unwanted effects.

![image](images/snake.jpg)

Ensure you have the connection script **connect\_db.php** working successfully before proceeding – it will be required throughout the rest of this book to connect to the **site\_db** MySQL database.

**Executing queries**

Once your PHP script has established a connection to a nominated database on the MySQL Server, queries can be made using the PHP mysqli\_query() function, which has this syntax:

**mysqli\_query ( *database-connection-object* , *sql-query* )**

The database connection object is that assigned to a variable ($dbc) by the standard script described [here on page 121](#chapter07.html#sec121). Typically, the SQL query is a string assigned to another variable, which can then be used as the second argument to the function.

When the mysqli\_query() function is called it returns a “result set” or a TRUE value where the call is successful, or a FALSE value where the call fails. Assigning the returned value to a variable enables the execution of the query to be tested for success or failure.

Optionally, your script can call upon mysqli\_close() to explicitly close the connection after the query has executed. This will happen automatically at the end of the script anyway, but making this call is considered good practice.

![image](images/pg122_1.jpg)

query.php

![image](images/1v.jpg)Create a PHP script that begins by incorporating the standard script to establish a connection to a database on the MySQL Server

**<?php**

require ( ‘ ../connect\_db.php ‘ ) ;

![image](images/2v.jpg)Next, initialize a variable with an SQL query string

$q \= ‘SHOW TABLES’ ;

![image](images/3v.jpg)Now, initialize another variable, this time with the result of a query to the database on the MySQL Server

$r \= mysqli\_query ( $dbc , $q ) ;

![image](images/4v.jpg)Test whether the query succeeded and display an appropriate message

if ( $r )

{ echo ‘<h1>Result Set Returned OK</h1>’ ; }

**else**

{ echo ‘<p>’ . mysqli\_error( $dbc ) . ‘</p>’ ; }

![image](images/5v.jpg)Finally, close the MySQL Server database connection

mysqli\_close ( $dbc ) ;

![image](images/6v.jpg)Save the PHP script in your web server’s /htdocs directory as query.php, then open it via HTTP to see the message confirming that the query succeeded

![image](images/pg123_1.jpg)

![image](images/7v.jpg)Now, edit the SQL query string to make it erroneous

$q \= ‘SHOW TABLE’ ;

![image](images/8v.jpg)Save the edited PHP script once more, then open it again via HTTP to see the message describing the query failure

![image](images/pg123_2.jpg)

![image](images/snake.jpg)

The SQL query strings assigned to PHP variables must not end with a semi-colon as they must in the MySQL Command Line Client.

![image](images/hot.jpg)

You can make almost any SQL query using **mysqli\_query()** that you can make in the MySQL Command Line Client.

**Retrieving results**

Some SQL queries, such as INSERT, UPDATE, DELETE or ALTER, return no data from the database, so when these are made successfully from a PHP script, the mysqli\_query() function simply returns a TRUE value. Other SQL queries, such as SHOW or SELECT, return a “result set” when made successfully from PHP.

A result set contains rows of records that can be read row-by-row using a while loop. Each row can be returned as an array using the mysqli\_fetch\_array() function, which requires the result set variable to be specified as its first argument. Optionally, it may take a second variabe to specify what type of array to return – an associative array (using column names), a numeric array, or both. Conveniently, the array type can be specified using one of the built-in PHP constant values listed below:

 
| **Constant:** || **Example:** |
| --- | --- |
| **MYSQLI\_ASSOC** || **$row \[ *‘column-name’* \]** |
| **MYSQLI\_NUM** || **$row \[ 0 \]** |
| **MYSQLI\_BOTH** || **$row \[ *‘column-name’* \]** OR **$row \[ 0 \]** |

Optionally, your script can call upon mysqli\_free\_result() to free the result set resource. This will happen automatically at the end of the script but, as with mysqli\_close(), making this call is considered good practice.

![image](images/pg124_1.jpg)

result.php

![image](images/1v.jpg)Create a PHP script that begins by incorporating the standard script to establish a connection to a database on the MySQL Server

**<?php**

require ( ‘ ../connect\_db.php ‘ ) ;

![image](images/2v.jpg)Next, initialize a variable with an SQL query string

$q \= ‘SHOW TABLES’ ;

![image](images/3v.jpg)Now, initialize another variable, this time with the result of a query to the database on the MySQL Server

$r \= mysqli\_query ( $dbc , $q ) ;

![image](images/4v.jpg)Test whether the query succeeded and display an appropriate message

if ( $r )

**{**

echo ‘<h1>Tables on site\_db database</h1> ‘ ;

\# Statements to be inserted here (Step 5).

**}**

**else**

{ echo ‘<p>’ . mysqli\_error( $dbc ) . ‘</p>’ ; }

![image](images/5v.jpg)Now, insert statements to display the data contained in each returned row and free the result set resource

while ( $row \= mysqli\_fetch\_array( $r , MYSQLI\_NUM ) )

**{**

echo ‘<br>’. $row\[ 0 \] ;

**}**

mysqli\_free\_result( $r ) ;

![image](images/6v.jpg)Finally, close the MySQL Server database connection

mysqli\_close ( $dbc ) ;

![image](images/7v.jpg)Save the PHP script in your web server’s /htdocs directory as result.php, then open it via HTTP to see the result

![image](images/pg125_1.jpg)

![image](images/forget.jpg)

If the array type is not explicitly specified, the **mysqli\_fetch\_array()** function returns both types by default.

![image](images/hot.jpg)

The results shown here list the tables created in the previous two chapters from the MySQL Command Line Client.

**Applying changes**

Changes can be applied to an existing MySQL database table by making SQL queries of INSERT, UPDATE, DELETE or ALTER. When these are made from a PHP script by the mysqli\_query() function, it returns a TRUE value when the query succeeds. This condition can be tested to perform an appropriate action. For example, to display all records in the table after adding new rows upon success, or to display an error message upon failure.

![image](images/pg126_1.jpg)

insert.php

![image](images/1v.jpg)Create a PHP script that begins by incorporating the standard script to establish a connection to a database on the MySQL Server

**<?php**

require ( ‘ ../connect\_db.php ‘ ) ;

![image](images/2v.jpg)Next, add a function to display all records in an existing table, or display an error message

function show\_records( $dbc )

**{**

$q \= ‘SELECT \* FROM prints’ ;

$r \= mysqli\_query( $dbc , $q ) ;

if ( $r )

**{**

echo ‘<h1>Records in prints table</h1> ‘ ;

while ( $row \= mysqli\_fetch\_array( $r , MYSQLI\_ASSOC ) )

**{**

echo ‘<br>’ . $row\[‘id’\] . ‘ | ‘ . $row\[ ‘name’ \] .

‘ @ ‘ . $row\[ ‘price’ \] ;

**}**

**}**

else { echo ‘<p>’ . mysqli\_error( $dbc ) . ‘</p>’ ; }

**}**

![image](images/3v.jpg)Now, call the function to display all the records

show\_records( $dbc ) ;

![image](images/4v.jpg)Create and execute another query to add rows to the table

$q \= ‘INSERT INTO prints ( name , price )

VALUES

( “One Center” , 32.99 ) , ( “Yellow Red Blue” , 36.99 ) ‘ ;

$r \= mysqli\_query( $dbc , $q ) ;

![image](images/forget.jpg)

This **SELECT** query uses the **MYSQLI\_ ASSOC** constant to return the result set as an associative array so the columns can be addressed by name.

![image](images/5v.jpg)Call the function to display all records again, or display an error message if the change failed

if( $r )

**{**

show\_records( $dbc ) ;

**}**

**else**

**{**

echo ‘<p>’ . mysqli\_error( $dbc ) . ‘</p>’ ;

**}**

![image](images/6v.jpg)Finally, close the MySQL Server database connection

mysqli\_close ( $dbc ) ;

![image](images/7v.jpg)Save the PHP script in your web server’s /htdocs directory as insert.php, then open it via HTTP to see the change to the database table get applied

![image](images/pg127_1.jpg)

![image](images/snake.jpg)

Remember that the **SELECT** query returns a result set upon success, whereas the **INSERT** query simply returns a **TRUE** value upon success.

![image](images/hot.jpg)

You can create the original “prints” table from the MySQL Command Line Client by following the steps [here on page 99](#chapter06.html#sec99).

**Counting records**

A result set returned by the built-in PHP mysqli\_query() function can be examined to discover how many rows it contains using the mysqli\_num\_rows() function. This function takes the result set as its argument, and returns the number of rows it contains, like this:

**$num = mysqli\_num\_rows( $r ) ;**

Usefully, the returned row count value can be tested before executing the while loop that returns records to ensure the result set is not empty.

![image](images/pg128_1.jpg)

count.php

![image](images/1v.jpg)Create a PHP script that begins by incorporating the standard script to establish a connection to a database on the MySQL Server

**<?php**

require ( ‘ ../connect\_db.php ‘ ) ;

![image](images/2v.jpg)Next, add a function to display all records in an existing table plus the total record count, or an error message

**function show\_records( $dbc )**

**{**

$q \= ‘SELECT \* FROM towels’ ;

$r \= mysqli\_query( $dbc , $q ) ;

$num \= mysqli\_num\_rows( $r ) ;

if ( $num \> 0 )

**{**

echo ‘<h1>Records in towels table</h1> ‘ ;

while ( $row \= mysqli\_fetch\_array( $r , MYSQLI\_ASSOC ) )

**{**

echo ‘<br>’ . $row\[‘name’\] . ‘ | ‘ . $row\[ ‘color’ \] .

‘ @ ‘ . $row\[ ‘price’ \] ;

**}**

echo “<br>$num Records” ;

**}**

else { echo ‘<p>’ . mysqli\_error( $dbc ) . ‘</p>’ ; }

**}**

![image](images/3v.jpg)Now, call the function to display all the records

show\_records( $dbc ) ;

![image](images/hot.jpg)

You can also use the **mysqli\_num\_rows()** function to paginate results – by displaying a particular number of rows per page.

![image](images/4v.jpg)Create and execute another query to add a row to the table

$q \= ‘INSERT INTO towels ( name , color , price )

VALUES ( “Sunset” , “Orange” , 9.99 ) ‘ ;

$r \= mysqli\_query( $dbc , $q ) ;

![image](images/5v.jpg)Call the function to display all records again, or display an error message if the change failed

if( $r ) { show\_records( $dbc ) ; }

else { echo ‘<p>’ . mysqli\_error( $dbc ) . ‘</p>’ ; }

![image](images/6v.jpg)Finally, close the MySQL Server database connection

mysqli\_close ( $dbc ) ;

![image](images/7v.jpg)Save the PHP script in your web server’s /htdocs directory as count.php, then open it via HTTP to see the change to the database table get applied and the row count change

![image](images/pg129_1.jpg)

![image](images/hot.jpg)

You can create the original “towels” table from the MySQL Command Line Client by following the steps [here on page 100](#chapter06.html#sec49).

**Updating records**

The built-in PHP mysqli\_affected\_rows() function returns an integer that is the number of rows affected by an INSERT, UPDATE, or DELETE query. Unlike the mysqli\_num\_rows() function, which takes the result set as its argument, the mysqli\_affected\_rows() function takes the database connection object as its argument:

**$num\_affected = mysqli\_affected\_rows( $dbc ) ;**

Usefully, the returned affected row value can be tested to ensure that an UPDATE query succeeded on an expected number of records.

![image](images/pg130_1.jpg)

update.php

![image](images/1v.jpg)Create a PHP script that begins by incorporating the standard script to establish a connection to a database on the MySQL Server

**<?php**

require ( ‘ ../connect\_db.php ‘ ) ;

![image](images/2v.jpg)Next, add a function to display all records in an existing table, or display an error message

function show\_records( $dbc )

**{**

$q \= ‘SELECT \* FROM watches’ ;

$r \= mysqli\_query( $dbc , $q ) ;

$num \= mysqli\_num\_rows( $r ) ;

if ( $num \> 0 )

**{**

echo ‘<h1>Records in watches table</h1> ‘ ;

while ( $row \= mysqli\_fetch\_array( $r , MYSQLI\_ASSOC ) )

**{**

echo ‘<br>’ . $row\[‘model’\] . ‘ | ‘ . $row\[ ‘style’ \] .

‘ @ ‘ . $row\[ ‘price’ \] ;

**}**

**}**

else { echo ‘<p>’ . mysqli\_error( $dbc ) . ‘</p>’ ; }

**}**

![image](images/3v.jpg)Now, call the function to display all the records

show\_records( $dbc ) ;

![image](images/4v.jpg)Create and execute another query to update (two) records in the table that have a specified value

$q \= ‘UPDATE watches

SET style = “Gents” WHERE style = “Ladies” ‘ ;

$r \= mysqli\_query( $dbc , $q ) ;

![image](images/forget.jpg)

Where an **INSERT**, **UPDATE**, or **DELETE** query makes no changes, the affected row count will be zero.

![image](images/5v.jpg)Call the function to display all records again if the expected number of records have been updated

if( mysqli\_affected\_rows( $dbc ) == 2 )

**{**

echo ‘<hr>’ . mysqli\_affected\_rows( $dbc ) .

‘ Records Updated...’ ;

show\_records( $dbc ) ;

**}**

![image](images/6v.jpg)Finally, close the MySQL Server database connection

mysqli\_close ( $dbc ) ;

![image](images/7v.jpg)Save the PHP script in your web server’s /htdocs directory as update.php, then open it via HTTP to see the change to the database table and the number of affected rows

![image](images/pg131_1.jpg)

![image](images/hot.jpg)

You can create the original “watches” table from the MySQL Command Line Client by following the steps [here on page 112](#chapter06.html#sec55).

**Validating results**

PHP provides built-in functions that allow data to be tested by type for validation. Each of the functions in the table below return TRUE if the data is of a certain type, otherwise they return FALSE:

 
| **Function:** || **Validates:** || **Example:** |
| --- | --- | --- |
| **is\_numeric()** || Number, even as string || **2.0, 20, ‘20’** |
| **is\_int()** || Integer || **100** |
| **is\_float()** || Floating-point number || **3.124** |
| **is\_string()** || String || **‘Hello World!’** |
| **is\_null()** || Null || **NULL** |
| **is\_scalar()** || Variable || **$var** |
| **is\_array()** || Array || **$days** |
| **is\_bool()** || Boolean || **TRUE** |
| **is\_resource()** || External Resource || **File Stream** |

![image](images/pg132_1.jpg)

validate.php

![image](images/1v.jpg)Create a PHP script that begins by incorporating the standard script to establish a connection to a database on the MySQL Server

**<?php**

require ( ‘ ../connect\_db.php ‘ ) ;

![image](images/2v.jpg)Next, add statements to retrieve a single piece of data from a database table for validation

$q \=

‘SELECT price FROM watches WHERE model = “Boston” ‘ ;

$r \= mysqli\_query( $dbc , $q ) ;

while ( $row \= mysqli\_fetch\_array( $r , MYSQLI\_NUM ) )

{ $var \= $row\[0\] ; }

![image](images/3v.jpg)Now, add statements to test the retrieved data type and display an appropriate result

$result \= is\_numeric( $var ) ? ‘numeric’ : ‘not numeric’ ;

echo “$var is $result<br>” ;

$result \= is\_int( $var ) ? ‘an integer’ : ‘not an integer’ ;

echo “$var is $result<br>” ;

$result \= is\_float( $var ) ? ‘a float’ : ‘not a float’ ;

echo “$var is $result<br>” ;

$result \= is\_string( $var ) ? ‘a string’ : ‘not a string’ ;

echo “$var is $result<br>” ;

$result \= is\_null( $var ) ? ‘NULL’ : ‘not NULL’ ;

echo “$var is $result<br>” ;

$result \= is\_scalar( $var ) ? ‘a variable’ : ‘not a variable’ ;

echo “$var is $result<br>” ;

$result \= is\_array( $var ) ? ‘an array’ : ‘not an array’ ;

echo “$var is $result<br>” ;

$result \= is\_bool( $var ) ? ‘a boolean’ : ‘not a boolean’ ;

echo “$var is $result<br>” ;

$result \= is\_resource( $var ) ? ‘a resource’ : ‘not a resource’ ;

echo “$var is $result<br>” ;

![image](images/4v.jpg)Finally, close the MySQL Server database connection

mysqli\_close ( $dbc ) ;

![image](images/5v.jpg)Save the PHP script in your web server’s /htdocs directory as validate.php, then open it via HTTP to see the results of the validation tests

![image](images/pg133_1.jpg)

![image](images/forget.jpg)

You should always validate data entered by users into HTML forms to ensure it is of the expected data type.

![image](images/hot.jpg)

You can see here that the decimal price value is stored in the variable as a string, not a float.

**Ensuring security**

When scripting with PHP and MySQL it is important to consider these security issues to prevent users entering data that may, accidentally or maliciously, produce undesirable effects:

•Do not allow the database connection script to be directly accessible – place it in the parent directory of /htdocs.

•Employ validation functions to ensure data exists and is of the correct type – frequently use isset() , !empty() and is\_numeric().

•Escape special characters in strings to make them safe for queries – first pass them to mysqli\_real\_escape\_string().

•Avoid HTML special characters – turn them into entity format with htmlentities() or remove them with strip\_tags().

![image](images/snake.jpg)

Removal of HTML tags is especially important as it prevents cross-site scripting (XSS) attacks – by stripping out the **<script>** tags so malicious JavaScript code cannot be executed.

Allowing users to submit data surrounded by quote marks can cause a script failure when that data gets entered into string, as the quote marks prematurely terminate the string. For example, in the assignment $str = “Submitted $data” where the $data variable itself contains a string enclosed in quotes. Passing the string to the mysqli\_real\_escape\_string() function returns it in a safe format. Similarly, allowing users to submit data surrounded by HTML tags can be problematic, but passing it to strip\_tags() removes the tags, or passing it to htmlentities() turns them into entity format.

![image](images/pg134_1.jpg)

secure.php

![image](images/1v.jpg)Create an HTML document containing a form with one text input field for data submission

<form action=”secure.php” method=”POST”>

<p>New Name : <input type=”text” name=”name”>

<input type=”submit”></p></form>

![image](images/2v.jpg)Add a script that displays an item from an existing table

**<?php**

require ( ‘../connect\_db.php’ ) ;

**\# Validation statements to be inserted here (Step 3).**

$q \= ‘SELECT \* FROM towels WHERE id = 1 ‘ ;

$r \= mysqli\_query( $dbc , $q ) ;

while ( $row \= mysqli\_fetch\_array( $r , MYSQLI\_NUM) )

{ echo “<p>Name : $row\[1\] </p>” ; }

mysqli\_close ( $dbc ) ;

**?>**

![image](images/3v.jpg)Next, insert statements to validate that the user has submitted a valid string, then update the existing table record

if ( !empty($\_POST\[‘name’\]) && !is\_numeric($\_POST\[‘name’\]) )

**{**

$name \= $\_POST\[‘name’\] ;

**\# Security statements to be inserted here (Step 4).**

$q \= ‘UPDATE towels SET name= “’.$name.‘” WHERE id= 1’ ;

mysqli\_query( $dbc , $q ) ;

} else { echo ‘No valid new name submitted’ ; }

![image](images/4v.jpg)Now, insert statements to make the submitted data safe for use in SQL queries, and to remove any HTML tags

$name \= mysqli\_real\_escape\_string( $dbc , $name ) ;

$name \= strip\_tags( $name ) ;

![image](images/5v.jpg)Save the PHP script in your web server’s /htdocs directory as secure.php, then open it via HTTP and submit data enclosed in HTML tags and quote marks to see them securely handled by the script

![image](images/pg135_1.jpg)

![image](images/pg135_2.jpg)

![image](images/hot.jpg)

You can comment out (by inserting a # at the beginning of the line) the first statement in Step 4 to see the update fail, or comment out its second statement to see the update then display in a bold font.

![image](images/hot.jpg)

You can create the original “towels” table from the MySQL Command Line Client by following the steps [here on page 100](#chapter06.html#sec49).

**Handling errors**

PHP provides useful error messages when it encounters problems with a script – describing both runtime and syntax errors. Additionally, you can create your own custom error handler to provide messages describing script problems that may arise.

Each error that occurs can be defined by a built-in PHP constant that has a unique numerical value, like those in the table below:

 
| **Value:** || **Constant:** || **Description:** |
| --- | --- | --- |
| **1** || **E\_ERROR** || Fatal runtime error, which halts execution of the script |
| **2** || **E\_WARNING** || Non-fatal runtime error, which does not halt the script |
| **4** || **E\_PARSE** || Syntax error, which prevents the interpreter running the script |
| **8** || **E\_NOTICE** || Possible runtime error, which simply provides a notice tip |
| **256** || **E\_USER\_ERROR** || Fatal user-generated error, set by the trigger\_error() function |
| **512** || **E\_USER\_WARNING** || Non-fatal user-generated error, set by trigger\_error() function |
| **1024** || **E\_USER\_NOTICE** || User-generated notice, set by the trigger\_error() function |

A custom error handler function of your own name is nominated as the argument to the PHP set\_error\_handler() function. Errors generate five descriptive components that can be passed as arguments to your error handler – error level, message, file, line, and context. The error level and message are mandatory.

In scripts that handle user input it is useful to “trigger” errors when the user enters inappropriate data. This is achieved using the PHP trigger\_error() function, which takes two arguments to specify the error message and level. As this function only describes user-generated errors, the specified error level must be one of the E\_USER constant types in the table above.

![image](images/hot.jpg)

PHP error handling is set on by its configuration file, but can also be set on manually by calling ini\_set( ‘display\_errors’,1).

![image](images/pg137_1.jpg)

error.php

![image](images/1v.jpg)Create an HTML document containing a PHP script that begins by nominating a custom error handler function

**<?php**

set\_error\_handler( ‘error\_handler’ ) ;

![image](images/2v.jpg)Next, add the custom error handler function to display error details to the user when called

function error\_handler ( $level , $message , $file , $line )

**{**

echo “Error \[$level\] : $message <br>

(Check line $line in $file )” ;

**}**

![image](images/3v.jpg)Now, initialize a variable, simulating a user input value

$num \= 500 ;

![image](images/4v.jpg)Finally, set the trigger to call the custom error handler

if ( $num \> 100 )

{ trigger\_error( ‘Number must be less than 100’ ,

E\_USER\_ERROR ) ; }

**?>**

![image](images/5v.jpg)Save the PHP script in your web server’s /htdocs directory as error.php, then open it via HTTP to see the message generated by your custom error handler function

![image](images/pg137_2.jpg)

![image](images/hot.jpg)

Individual expression errors can be suppressed by prefixing the expression with the **@** error control operator. So **$num = @( 8 / 0 ) ;** suppresses the default Division By Zero error message.

**Summary**

•The PHP mysqli\_connect() function connects a user to a specified database and returns a database connection object.

•A database connection object is used as an argument in other PHP functions that communicate with the database.

•The PHP mysqli\_query() function sends SQL queries to the connected database on the MySQL Server.

•When the mysqli\_query() function is called it returns a result set or a TRUE value upon success, or a FALSE value upon failure.

•Optionally, mysqli\_close() can be called to explicitly close the database connection.

•An SQL SELECT query returns a result set that contains rows of records that can be read row-by-row using a while loop.

•The PHP mysqli\_fetch\_array() function returns each row of a result set as an associative or numbered array.

•Optionally, mysqli\_free\_result() can be called to explicitly free a result set resource.

•An SQL INSERT, UPDATE, DELETE, or ALTER query simply returns a TRUE value upon success.

•The PHP mysqli\_num\_rows() function returns an integer that is the number of rows within a specified result set.

•The mysqli\_affected\_rows() function returns an integer that is the number of rows affected by an INSERT, UPDATE, or DELETE.

•PHP functions that test data by type return TRUE if the data is of a certain type, otherwise they return FALSE.

•The mysqli\_real\_escape\_string() function escapes special characters from strings, and strip\_tags() removes HTML tags.

•The set\_error\_handler() function nominates a custom error handler, and trigger\_error() can be used to generate errors.

8

Registering users

***This chapter demonstrates how to create a simple registration procedure and login application.***

[**Creating a users database**](#chapter08.html#sec69)

[**Providing a register page**](#chapter08.html#sec70)

[**Processing registrations**](#chapter08.html#sec71)

[**Providing a login page**](#chapter08.html#sec72)

[**Supplying login tools**](#chapter08.html#sec73)

[**Processing login attempts**](#chapter08.html#sec74)

[**Confirming login success**](#chapter08.html#sec75)

[**Summary**](#chapter08.html#sec76)

**Creating a users database**

User details can be usefully stored in a MySQL database table upon their first registration visit, so those details may be easily retrieved upon subsequent visits for comparison by a PHP script. When the user enters login details matching those already stored in the database table, the script can allow access to the website. Typically, a database table containing user details might store the user ID, first name, last name, email address, password, and registration date of each user, in individual columns:

 
| **Column Name:** || Content Type: || Example: |
| --- | --- | --- |
| **user\_id** || Number || 123 |
| **first\_name** || Text || Mike |
| **last\_name** || Text || McGrath |
| **email** || Text || mike@example.com |
| **pass** || Text || m00nshine |
| **reg\_date** || Date/Time || 2018-05-14 12:30:00 |

The design of this database table simply requires **CHAR** or **VARCHAR** data types to be specified for those columns storing text. User IDs should be positive (**UNSIGNED**) integer **INT** values that the table automatically allocates with **AUTO\_INCREMENT**, and the user’s first registration timestamp stored as a **DATETIME** value. The user’s email address should be **UNIQUE**, so they cannot be registered more than once, and as all these items will be required for registration, each column must have a **NOT NULL** rule.

The SQL command required to produce this design as a MySQL database table named “users” can be issued at the prompt in the MySQL Command Line Client. Alternatively, the SQL command can be saved in an SQL file, which can be implemented at the MySQL Command Line Client prompt by issuing the SOURCE command followed by the path to the SQL file on your system.

![image](images/forget.jpg)

MySQL database tables can only be created by the root MySQL user or other MySQL user that has been granted full access privileges.

![image](images/pg141_1.jpg)

create\_users.sql

![image](images/1b.jpg)Launch a plain text editor and create an SQL command describing the table requirements shown opposite

CREATE TABLE IF NOT EXISTS users (

**user\_id INT UNSIGNED NOT NULL AUTO\_INCREMENT ,**

**first\_name VARCHAR(20) NOT NULL ,**

**last\_name VARCHAR(40) NOT NULL ,**

**email VARCHAR(60) NOT NULL ,**

**pass VARCHAR(256) NOT NULL ,**

**reg\_date DATETIME NOT NULL ,**

**PRIMARY KEY ( user\_id ) ,**

**UNIQUE ( email ) ) ;**

![image](images/2b.jpg)Save the file in a folder at **C:\\SQL** as **create\_users.sql**, then launch the MySQL Command Line Client and log in as a user with full access privileges, such as the root user

![image](images/3b.jpg)Next, issue a command to use the established database

**USE site\_db ;**

![image](images/4b.jpg)Now, implement the SQL command by stating the source path to the SQL file on your system

**SOURCE C:\\SQL\\create\_users.sql**

![image](images/5b.jpg)Finally, issue a command to confirm the table format

**EXPLAIN users ;**

![image](images/pg141_2.jpg)

![image](images/snake.jpg)

Name the users password column “pass” rather than “password” – to avoid confusion with the built-in MySQL **password()** function.

**Providing a register page**

A user registration form might typically provide input fields requiring the user to input their first name, last name, email address, and a unique password. This can be displayed on a web page by a PHP script that also includes page header and footers.

![image](images/pg142_1.jpg)

The PHP script can also process the form when submitted, to first ensure the user has entered valid data in each field, then insert that user data into the MySQL database “users” table created [here on page 141](#chapter08.html#sec141).

In order to process the form, the HTML **<form>** tag’s **method** attribute should specify the form be submitted using the **POST** method, and its **action** method should specify the name of the same PHP script that displays the form. This allows any input entered by the user to be retained by the input fields in the event that any item fails validation.

When the form is submitted after user input, the PHP script will display messages to advise the user of any validation error, or display a confirmation that registration has succeeded and provide a hyperlink to a Login page.

![image](images/forget.jpg)

The page’s header and footer are included in HTML documents, simply styled by a CSS stylesheet.

![image](images/pg143_1.jpg)

register.php

![image](images/1b.jpg)Launch a plain text editor and begin a PHP script with statements to set the page title and include a page header

**<?php**

**$page\_title \= ‘Register’ ;**

**include ( ‘includes/header.html’ ) ;**

![image](images/2b.jpg)Now, add a conditional test that will only execute the statements it contains if the form has been submitted

**if ( $\_SERVER\[ ‘REQUEST\_METHOD’ \] \== ‘POST’ )**

**{**

**\# Statements to be inserted here (Steps 3-10).**

**}**

**?>**

![image](images/3b.jpg)Next, insert statements to open the database connection and initialize an array for error messages

**require ( ‘../connect\_db.php’ ) ;**

**$errors \= array() ;**

![image](images/4b.jpg)Insert statements to store an error message if the first name field remains empty, or store its value in a variable

**if ( empty( $\_POST\[ ‘first\_name’ \] ) )**

**{ $errors\[\] \= ‘Enter your first name.’ ; }**

**else**

**{ $fn \= mysqli\_real\_escape\_string( $dbc,**

**trim( $\_POST\[ ‘first\_name’ \] ) ) ; }**

![image](images/5b.jpg)Now, insert statements to store an error message if the last name field remains empty, or store its value in a variable

**if ( empty( $\_POST\[ ‘last\_name’ \] ) )**

**{ $errors\[\] \= ‘Enter your last name.’ ; }**

**else**

**{ $ln \= mysqli\_real\_escape\_string( $dbc,**

**trim( $\_POST\[ ‘last\_name’ \] ) ) ; }**

![image](images/6b.jpg)Insert statements to store an error message if the email address field remains empty, or store its value in a variable

**if ( empty( $\_POST\[ ‘email’ \] ) )**

**{ $errors\[\] \= ‘Enter your email address.’ ; }**

**else**

**{ $e \= mysqli\_real\_escape\_string( $dbc,**

**trim( $\_POST\[ ‘email’ \] ) ) ; }**

![image](images/forget.jpg)

The database connection variable **$dbc** is initialized by the **connect\_db.php** script, and the **$\_POST\[\]** array contains the values in the named form fields.

![image](images/hot.jpg)

Use the **mysqli\_ real\_escape\_string()** function to escape special characters, and the **trim()** function to remove unwanted spaces.

![image](images/7b.jpg)Next, insert statements to store the password value in a variable if the passwords are a valid match, or store an error message if they do not match or the first field is empty

**if ( !empty( $\_POST\[ ‘pass1’ \] ) )**

**{**

**if ( $\_POST\[ ‘pass1’ \] != $\_POST\[ ‘pass2’ \] )**

**{ $errors\[\] \= ‘Passwords do not match.’ ; }**

**else**

**{ $p \= mysqli\_real\_escape\_string( $dbc,**

**trim( $\_POST\[ ‘pass1’ \] ) ) ; }**

**}**

**else { $errors\[\] \= ‘Enter your password.’ ; }**

![image](images/8b.jpg)Insert statements to store an error message if the email address is already registered in the “users” database table

**if ( empty( $errors ) )**

**{**

**$q \= “SELECT user\_id FROM users WHERE email=’$e’” ;**

**$r \= mysqli\_query ( $dbc , $q ) ;**

**if ( mysqli\_num\_rows( $r ) != 0 )**

**{ $errors\[\] \= ‘Email address already registered.**

**<a href=”login.php”>Login</a>’ ; }**

**}**

![image](images/9b.jpg)Now, insert statements to store the user data in the database table, display a confirmation when registration succeeds, close the database connection, include a page footer, and exit the script

**if ( empty( $errors ) )**

**{**

**$q \= “INSERT INTO users**

**(first\_name, last\_name, email, pass, reg\_date)**

**VALUES (‘$fn’, ‘$ln’, ‘$e’, SHA2(‘$p’, 256 ), NOW() )” ;**

**$r \= mysqli\_query ( $dbc , $q ) ;**

**if ( $r )**

**{**

**echo ‘<h1>Registered!</h1>**

**<p>You are now registered.</p>**

**<p><a href=”login.php”>Login</a></p>’ ;**

**}**

**mysqli\_close( $dbc ) ;**

**include ( ‘includes/footer.html’ ) ;**

**exit() ;**

**}**

![image](images/hot.jpg)

Notice that the error message provides a hyperlink to the Login page if the email address is found in the database table – as the user is already registered.

![image](images/forget.jpg)

The password gets securely stored in the users database table in encrypted format by the **SHA2()** function as a string of 64 hex digits.

![image](images/10b.jpg)Append alternative statements to display all stored error messages when registration cannot be completed, and close the database connection

**else**

**{**

**echo ‘<h1>Error!</h1>**

**<p id=”err\_msg”>The following error(s) occurred:<br>’ ;**

**foreach ( $errors as $msg )**

**{**

**echo “ -$msg<br>” ;**

**}**

**echo ‘Please try again.</p>’ ;**

**mysqli\_close( $dbc ) ;**

**}**

![image](images/11b.jpg)Now, add the HTML sticky form that uses this script

**<h1>Register</h1>**

**<form action=”register.php” method=”POST”>**

**<p>**

**First Name: <input type=”text” name=”first\_name”**

**value=”<?php if ( isset( $\_POST\[ ‘first\_name’ \] ) )**

**echo $\_POST\[ ‘first\_name’ \] ; ?>”>**

**Last Name: <input type=”text” name=”last\_name”**

**value=”<?php if ( isset( $\_POST\[ ‘last\_name’ \] ) )**

**echo $\_POST\[ ‘last\_name’ \] ; ?>”>**

**</p> <p>**

**Email Address: <input type=”text” name=”email”**

**value=”<?php if ( isset( $\_POST\[ ‘email’ \] ) )**

**echo $\_POST\[ ‘email’ \] ; ?>”>**

**</p> <p>**

**Password: <input type=”password” name=”pass1”**

**value=”<?php if ( isset( $\_POST\[ ‘pass1’ \] ) )**

**echo $\_POST\[ ‘pass1’ \] ; ?>” >**

**Confirm Password: <input type=”password” name=”pass2”**

**value=”<?php if ( isset( $\_POST\[ ‘pass2’ \] ) )**

**echo $\_POST\[ ‘pass2’ \] ; ?>”>**

**</p> <p>**

**<input type=”submit” value=”Register”> </p>**

**</form>**

![image](images/12b.jpg)Add a final script instruction to include a page footer, then save the script in your web server’s /htdocs directory as register.php

**<?php include ( ‘includes/footer.html’ ) ; ?>**

![image](images/snake.jpg)

Always remember to close the database connection when access is no longer needed.

![image](images/hot.jpg)

Assign the values passed to the **$\_POST\[\]** global variable array upon submission to retain the field values when registration fails.

**Processing registrations**

Having created the user registration page, described [here on pages 142-145](#chapter08.html#sec70), you can now test the registration process to ensure the validation checks perform correctly and the PHP script provides appropriate confirmation messages to the user.

![image](images/1b.jpg)With the MySQL Server running, enter the location http://localhost/register.php into your web browser’s address field to see Abyss serve up the registration page

![image](images/2b.jpg)Now, click the “Register” button to see messages appear advising that field validation has failed for each input

![image](images/pg146_1.jpg)

![image](images/3b.jpg)Next, complete all input fields, ensuring you enter identical password values, then click the “Register” button once more to see a message advising that registration has succeeded and providing a hyperlink to a Login page

![image](images/pg147_1.jpg)

![image](images/forget.jpg)

When registration fails the user’s input details are retained in the sticky form fields for correction.

![image](images/4b.jpg)Return to the registration page and enter identical user details as before, then click the “Register” button to see a message appear advising that your email address is registered, and providing a hyperlink to a Login page

![image](images/pg147_2.jpg)

![image](images/hot.jpg)

Try entering differing password values to see registration fail with a message advising that passwords do not match.

![image](images/snake.jpg)

Remember that the MySQL Server must be running so the input data can be written into the users table for subsequent comparison.

**Providing a login page**

Having completed the user registration process, described [here on pages 142-147](#chapter08.html#sec70), you can now create the Login page that the user can access by following the hyperlinks provided upon registration, or by addressing the Login page directly.

![image](images/pg148_1.jpg)

login.php

![image](images/1b.jpg)Launch a plain text editor and begin a PHP script with statements to set the page title and include a page header

**<?php**

**$page\_title \= ‘Login’ ;**

**include ( ‘includes/header.html’ ) ;**

![image](images/2b.jpg)Now, add a conditional test that will display any error messages if they exist, and provide a hyperlink back to the registration page when the login attempt fails

**if ( isset( $errors ) && !empty( $errors ) )**

**{**

**echo ‘<p id=”err\_msg”>Oops! There was a problem:<br>’ ;**

**foreach ( $errors as $msg )**

**{**

**echo “ - $msg<br>” ;**

**}**

**echo ‘Please try again or**

**<a href=”register.php”>Register</a></p>’ ;**

**}**

**?>**

![image](images/3b.jpg)Next, add the HTML form that will submit the user login details to be processed by a PHP script

**<h1>Login</h1>**

**<form action=”login\_action.php” method=”POST”>**

**<p>**

**Email Address: <input type=”text” name=”email”>**

**</p><p>**

**Password: <input type=”password” name=”pass”>**

**</p><p>**

**<input type=”submit” value=”Login” >**

**</p>**

**</form>**

![image](images/4b.jpg)Add a final script instruction to include a page footer, then save the script in your web server’s /htdocs directory as login.php

**<?php include ( ‘includes/footer.html’ ) ; ?>**

![image](images/forget.jpg)

The **$errors** array will only be set by the PHP handler script after the form has been submitted when login fails.

![image](images/5b.jpg)Click the hyperlink on the registration page, or enter the location http://localhost/login.php into your web browser’s address field, to see Abyss serve up the Login page

![image](images/pg149_1.jpg)

When the login form is submitted, a validation function must ensure the fields are not empty then seek their input values in the “users” database table.

If the submitted values are found, the login attempt succeeds, so the corresponding user id, first name, and last name, can be retrieved from the “users” table, and a further function can be called to load a Home page in the browser.

If the submitted values are not found, the login attempt fails and the validation function will simply set a descriptive error message.

These two functions, to validate form fields and to load a new page, can usefully be created as login “tools” within an independent PHP script, so they may be readily called from the script nominated to handle the Login page form and by other PHP scripts as the user navigates to other pages in the website.

![image](images/snake.jpg)

Clicking the Login button before the PHP handler script has been created will simply produce an HTTP 404 Page Not Found error.

![image](images/hot.jpg)

Create functions in independent PHP scripts for modularity if they can be useful to multiple pages across a website.

**Supplying login tools**

Having completed the user login form, described [here on pages 148-149](#chapter08.html#sec72), you can now create the login tools that will validate login attempts and load a new page when required. These tools can be easily made available to other pages on the website, simply by inserting a PHP require statement in them naming this script.

![image](images/pg150_1.jpg)

login\_tools.php

![image](images/1b.jpg)Launch a plain text editor and begin a PHP script with a function block to load a page specified as its argument

**<?php**

**function load( $page \= ‘login.php’ )**

**{**

**\# Statements to be inserted here (Steps 2-4).**

**}**

![image](images/2b.jpg)Now, in the load function block, insert a statement to build a URL string of protocol, current domain, and directory

**$url \= ‘http://’ . $\_SERVER\[ ‘HTTP\_HOST’ \] .**

**dirname( $\_SERVER\[ ‘PHP\_SELF’ \] ) ;**

![image](images/3b.jpg)Next, in the load function block, insert statements to remove any trailing slashes from the URL string, then append a forward slash and the specified page argument

**$url \= rtrim( $url , ‘/\\\\’ ) ;**

**$url .= ‘/’ . $page ;**

![image](images/4b.jpg)Finally, in the load function block, insert statements to load the specified page then quit the script

**header( “Location: $url” ) ;**

**exit() ;**

![image](images/5b.jpg)Add a function block to validate the user login details as correct, or supply error messages

**function validate( $dbc , $email \= ‘’ , $pwd \= ‘’ )**

**{**

**\# Statements to be inserted here (Steps 6-10).**

**}**

![image](images/6b.jpg)In the validate function block, insert a statement to initialize an array for error messages

**$errors \= array() ;**

![image](images/hot.jpg)

Assign the name of the Login page to the load argument to become the default page to load if no other page is specified by the caller.

![image](images/forget.jpg)

The existence of a sub-directory may add trailing slashes to the URL string, so these must be removed before appending the page.

![image](images/7b.jpg)Next, insert statements to store an error message if the email field remains empty, or store its value in a variable

**if ( empty( $email ) )**

**{ $errors\[\] \= ‘Enter your email address.’ ; }**

**else**

**{ $e \= mysqli\_real\_escape\_string( $dbc , trim( $email ) ) ;** **}**

![image](images/8b.jpg)Now, insert statements to store an error message if the password field remains empty, or store its value in a variable

**if ( empty( $pwd ) )**

**{ $errors\[\] \= ‘Enter your password.’ ; }**

**else**

**{ $p \= mysqli\_real\_escape\_string( $dbc , trim( $pwd ) ) ; }**

![image](images/9b.jpg)Insert statements to store an error message if the email and password are not found in the database table, or return the associated user ID, first name, and last name to the caller – if the login attempt succeeds

**if ( empty( $errors ) )**

**{**

**$q \= “SELECT user\_id, first\_name, last\_name**

**FROM users**

**WHERE email = ’$e’**

**AND pass = SHA2( ‘$p’, 256 ) ” ;**

**$r \= mysqli\_query ( $dbc , $q ) ;**

**if ( mysqli\_num\_rows( $r ) == 1 )**

**{**

**$row \= mysqli\_fetch\_array ( $r , MYSQLI\_ASSOC ) ;**

**return array( true , $row ) ;**

**}**

**else**

**{ $errors\[\] \= ‘Email address and password not found.’ ; }**

**}**

![image](images/10b.jpg)Finally, insert a statement in the validate function block to return the list of error messages to the caller – if the login attempt fails

**return array( false , $errors ) ; }**

![image](images/11b.jpg)Be sure to now save this script in your web server’s **/htdocs** directory as **login\_tools.php**

![image](images/hot.jpg)

For stability you should use the **mysqli\_ real\_escape\_string()** function to escape any unexpected characters.

![image](images/snake.jpg)

The registration process stored the user password in encrypted format using the MySQL **SHA2()** function (see [here page 116](#chapter06.html#sec57)) – so the SELECT comparison must also use that function.

**Processing login attempts**

Having completed the login form and the login tools, described [here on pages 148-151](#chapter08.html#sec72), you can now create the PHP script to actually process login attempts. When a login attempt succeeds, this script will set user details retrieved from the database as session data – so the logged-in user can be easily recognized as they navigate between other pages of the same website.

![image](images/pg152_1.jpg)

login\_action.php

![image](images/1b.jpg)Launch a plain text editor and begin a PHP script with a test block to see if the login form has been submitted

**<?php**

**if ( $\_SERVER\[ ‘REQUEST\_METHOD’ \] \== ‘POST’ )**

**{**

**\# Statements to be inserted here (Steps 2-6).**

**}**

![image](images/2b.jpg)Now, insert a statement to open the database connection

**require ( ‘../connect\_db.php’ ) ;**

![image](images/3b.jpg)Next, insert a statement to make the login tools available

**require ( ‘login\_tools.php’ ) ;**

![image](images/4b.jpg)Insert a statement to ensure login succeeded and get the associated user details of ID, first name, and last name

**list ( $check , $data ) =**

**validate ( $dbc , $\_POST\[ ‘email’ \] , $\_POST\[ ‘pass’ \] ) ;**

![image](images/5b.jpg)Now, insert statements to set the user details as session data and load a Home page, or assign error messages

**if ( $check )**

**{**

**session\_start() ;**

**$\_SESSION\[ ‘user\_id’ \] \= $data\[ ‘user\_id’ \] ;**

**$\_SESSION\[ ‘first\_name’ \] \= $data\[ ‘first\_name’ \] ;**

**$\_SESSION\[ ‘last\_name’ \] \= $data\[ ‘last\_name’ \] ;**

**load ( ‘home.php’ ) ;**

**}**

**else { $errors \= $data ; }**

![image](images/6b.jpg)Next, insert a statement to close the database connection

**mysqli\_close( $dbc ) ;**

![image](images/forget.jpg)

Your **validate()** login tool function returns an array whose elements are assigned to individual variables by the PHP **list()** function.

![image](images/hot.jpg)

Storing user details as server-side session data is preferable to storing as client-side “cookies” that the user can choose to disable.

![image](images/7b.jpg)Finally, after the test block, add a statement to continue display of the Login page when the login attempt fails

**include ( ‘login.php’ ) ;**

![image](images/8b.jpg)Save this script in your web server’s **/htdocs** directory as **login\_action.php**, then enter the Login page location **http://localhost/login.php** in your web browser’s address field and attempt to log in with incorrect user details

![image](images/pg153_1.jpg)

![image](images/pg153_2.jpg)

![image](images/snake.jpg)

This login form is not a “sticky” form – so the entered user details are not retained after the form gets submitted.

![image](images/hot.jpg)

The **validate()** function in **login\_tools.php** sets the error message shown here – so it gets displayed by **login.php** when loaded by the include statement in **login\_action.php**.

**Confirming login success**

Having completed the PHP script to actually process login attempts, described [here on pages 152-153](#chapter08.html#sec74), you can now create the Home page to be loaded when the login attempt succeeds. Typically, this will contain hyperlinks to allow the user to navigate between other pages of the website.

![image](images/pg154_1.jpg)

home.php

![image](images/1b.jpg)Launch a plain text editor and begin a PHP script with a statement to allow access to session data

**<?php**

**session\_start() ;**

![image](images/2b.jpg)Now, add statements to redirect the browser to the Login page if the user is not already logged in

**if ( !isset( $\_SESSION\[ ‘user\_id’ \] ) )**

**{**

**require ( ‘login\_tools.php’ ) ;**

**load() ;**

**}**

![image](images/3b.jpg)Next, add statements to set the page title and include a page header

**$page\_title \= ‘Home’ ;**

**include ( ‘includes/header.html’ ) ;**

![image](images/4b.jpg)Add a statement to confirm the named user is logged in

**echo “<h1>HOME</h1>**

**<p>You are now logged in,**

**{ $\_SESSION\[ ‘first\_name’ \] } { $\_SESSION\[ ‘last\_name’ \] }**

**</p>” ;**

![image](images/5b.jpg)Now, add statements to create hyperlinks to other pages on this website

**echo ‘<p>**

**<a href=”forum.php”>Forum</a> |**

**<a href=”shop.php”>Shop</a> |**

**<a href=”goodbye.php”>Logout</a>**

**</p> ’ ;**

![image](images/6b.jpg)Add a final statement to include a page footer

**include ( ‘includes/footer.html’ ) ;**

**?>**

![image](images/forget.jpg)

The Home page cannot be reached until completing the login process during which the session variable gets set.

![image](images/7b.jpg)Save this script in your web server’s /htdocs directory as home.php, then enter the Login page location http://localhost/login.php in your web browser’s address field and attempt to log in with correct user details

![image](images/pg155_1.jpg)

![image](images/pg155_2.jpg)

![image](images/hot.jpg)

The hyperlinks on the Home page will be used to demonstrate PHP forums and e-commerce in the following two chapters of this book.

**Summary**

•User details can be stored in a MySQL database table for comparison on subsequent visits to a website.

•Typically, a MySQL database users table might store their ID, names, email address, password, and date of registration.

•A typical registration form might request the user’s names, their email address, and their chosen password twice.

•The registration form should be submitted by the **POST** method and specify the name of a PHP script as its action.

•The PHP script processing a registration attempt should first ensure that all required field data is valid, and provide appropriate error message where validation fails.

•When all registration data appears valid, the PHP script processing a registration attempt can then store the submitted user data in a MySQL database users table.

•A typical login form might request the user’s email address and the password chosen by them during the registration process.

•The login form should be submitted by the **POST** method and specify the name of a PHP script as its action.

•Login tools can be contained in a separate PHP script so they can be easily made available to other pages on the website.

•The PHP script processing a login attempt should ensure that all required field data is valid and that the user exists in the users database, or provide an appropriate error message.

•When all login data is valid and the user found in the database, the PHP script processing a login attempt can store the user details as session data so the user can be easily recognized as they navigate between other pages on that website.

•The PHP script processing a successful login attempt can load the website’s Home page containing navigation links.

9

Providing forums

***This chapter builds on the previous chapter to demonstrate how to create a simple forum application.***

[**Creating a forum database**](#chapter09.html#sec77)

[**Providing a forum page**](#chapter09.html#sec78)

[**Supplying a message form**](#chapter09.html#sec79)

[**Processing posted messages**](#chapter09.html#sec80)

[**Confirming post success**](#chapter09.html#sec81)

[**Summary**](#chapter09.html#sec82)

**Creating a forum database**

User messages can be stored in a MySQL database table by a PHP script so they may be subsequently retrieved for display in a Forum page containing messages from various registered users. Typically, a database table containing posted user messages might store the post ID, the user’s first name and last name, the subject title, the message itself, and the date when posted:

 
| **Column Name:** || **Content Type:** || **Example:** |
| --- | --- | --- |
| **post\_id** || Number || 123 |
| **first\_name** || Text || Mike |
| **last\_name** || Text || McGrath |
| **subject** || Text || Ice Cream |
| **message** || Text || Delicious on a hot day. |
| **post\_date** || Date/Time || 2018-05-14 12:30:00 |

The design of this database table simply requires that VARCHAR or TEXT data types should be specified for those columns storing text. Post IDs should be positive (UNSIGNED) integer INT values that the table automatically allocates with AUTO\_INCREMENT, and the message posted timestamp should be stored as a DATETIME value. All these items will be required to post a message to the database table, so each column must have a NOT NULL rule.

The SQL command required to produce this design as a MySQL database table named “forum” can be issued at the prompt in the MySQL Command Line Client. Alternatively, the SQL command can be saved in an SQL file, which can be implemented at the MySQL Command Line Client prompt by issuing the SOURCE command followed by the path to the SQL file on your system.

![image](images/forget.jpg)

MySQL database tables can only be created by the root MySQL user or other MySQL user that has been granted full access privileges.

![image](images/pg159_1.jpg)

create\_forum.sql

![image](images/1r.jpg)Launch a plain text editor and create an SQL command describing the table requirements shown opposite

CREATE TABLE IF NOT EXISTS forum (

post\_id INT UNSIGNED NOT NULL AUTO\_INCREMENT ,

first\_name VARCHAR(20) NOT NULL ,

last\_name VARCHAR(40) NOT NULL ,

subject VARCHAR(60) NOT NULL ,

message TEXT NOT NULL ,

post\_date DATETIME NOT NULL ,

PRIMARY KEY ( post\_id ) ) ;

![image](images/2r.jpg)Save the file in a folder at C:\\SQL as create\_forum.sql, then launch the MySQL Command Line Client and log in as a user with full access privileges, such as the root user

![image](images/3r.jpg)Next, issue a command to use the established database

USE site\_db ;

![image](images/4r.jpg)Now, implement the SQL command by stating the source path to the SQL file on your system

SOURCE C:\\SQL\\create\_forum.sql

![image](images/5r.jpg)Finally, issue a command to confirm the table format

EXPLAIN forum ;

![image](images/pg159_2.jpg)

![image](images/hot.jpg)

The MySQL **TEXT** data type accommodates up to 65,535 characters. Larger messages can be accommodated with **MEDIUMTEXT** and **LONGTEXT** data types.

**Providing a forum page**

Typically, a message board page displaying posted forum messages might only be available to registered users. The PHP script providing this page can check that the user is registered by testing the session data, and redirect to the Login page when this test fails. When the test succeeds, previous posted messages can be retrieved from the MySQL forum database table for display on the page, or the script can simply advise that there are currently no messages. Forum messages can be displayed between page header and footers together with a hyperlink to another page where the current user can post a new forum message.

![image](images/pg160_1.jpg)

forum.php

![image](images/1r.jpg)Launch a plain text editor and begin a PHP script with a statement to allow access to session data

**<?php**

**session\_start() ;**

![image](images/2r.jpg)Now, add statements to redirect the browser to the Login page if the user is not already logged in

if ( !isset( $\_SESSION\[ ‘user\_id’ \] ) )

**{**

require ( ‘login\_tools.php’ ) ;

**load() ;**

**}**

![image](images/3r.jpg)Next, add statements to set the page title and include a page header

$page\_title \= ‘Forum’ ;

include ( ‘includes/header.html’ ) ;

![image](images/4r.jpg)Add a statement to open the database connection

require ( ‘../connect\_db.php’ ) ;

![image](images/5r.jpg)Now, add statements to retrieve messages from the database or provide a default message

$q \= “SELECT \* FROM forum” ;

$r \= mysqli\_query( $dbc , $q ) ;

if ( mysqli\_num\_rows( $r ) > 0 )

**{**

**\# Statements to be inserted here (Step 6).**

**}**

**else**

{ echo ‘<p>There are currently no messages.</p>’ ; }

![image](images/forget.jpg)

The Forum page cannot be reached until completing the login process, during which the session variable gets set.

![image](images/6r.jpg)Next, insert statements to write a table displaying all messages retrieved from the database table if any found

echo ‘<table><tr><th>Posted By</th>

<th>Subject</th><th id=”msg”>Message</th></tr>’;

while ( $row \= mysqli\_fetch\_array( $r , MYSQLI\_ASSOC ) )

**{**

echo ‘<tr>

<td>’.$row\[‘first\_name’\].’ ‘.$row\[‘last\_name’\].‘<br>’

.$row\[‘post\_date’\].’</td>

<td>’.$row\[‘subject’\].‘</td><td>’.$row\[‘message’\].‘</td>

</tr>’;

**}**

echo ‘</table>’ ;

![image](images/7r.jpg)Add a statement to create hyperlinks to other pages on this website, including a “Post Message” page

echo ‘<p>

<a href=”post.php”>Post Message</a> |

<a href=”shop.php”>Shop</a> |

<a href=”home.php”>Home</a> |

<a href=”goodbye.php”>Logout</a></p>’ ;

![image](images/8r.jpg)Now, add a statement to close the database connection

mysqli\_close( $dbc ) ;

![image](images/9r.jpg)Add a final statement to include a page footer

include ( ‘includes/footer.html’ ) ; ?>

![image](images/10r.jpg)Save this script in your web browser’s /htdocs directory as forum.php, then log in and follow the link on the Home page to the Forum

![image](images/pg161_1.jpg)

![image](images/forget.jpg)

The cells on a table row will be populated by the data contained in the columns on a row of the database forum table.

![image](images/hot.jpg)

The hyperlinks on the Forum page will be used to demonstrate PHP e-commerce and allow the user to post a message, return to the Home page, or log out.

**Supplying a message form**

Having completed the PHP script to display posted forum messages, described [here on pages 160-161](#chapter09.html#sec78), you can now create a PHP script to allow the user to post new messages. This can check that the user is indeed logged in then simply provide a form with fields for the subject title and the message body itself.

![image](images/pg162_1.jpg)

post.php

![image](images/1r.jpg)Launch a plain text editor and begin a PHP script with a statement to allow access to session data

**<?php**

**session\_start() ;**

![image](images/2r.jpg)Now, add statements to redirect the browser to the Login page if the user is not already logged in

if ( !isset( $\_SESSION\[ ‘user\_id’ \] ) )

**{**

require ( ‘login\_tools.php’ ) ;

**load() ;**

**}**

![image](images/3r.jpg)Next, add statements to set the page title and include a page header

$page\_title \= ‘Post Message’ ;

include ( ‘includes/header.html’ ) ;

![image](images/4r.jpg)Add a statement to display the form

echo ‘<form action=”post\_action.php” method=”POST”

accept-charset=”utf-8”>

<p>Subject:<br>

<input name=”subject” type=”text” size=”64”></p>

<p>Message:<br>

<textarea name=”message” rows=”5” cols=”50”>

</textarea></p>

<p><input type=”submit” value=”Submit”></p>

</form>’ ;

![image](images/5r.jpg)Next, add a statement to create hyperlinks to other pages on this website

echo ‘<p>

<a href=”forum.php”>Forum</a> |

<a href=”shop.php”>Shop</a> |

<a href=”home.php”>Home</a> |

<a href=”goodbye.php”>Logout</a></p>’ ;

![image](images/hot.jpg)

Notice that the form **action** attribute nominates a submission handler named **post\_action.php** – this is listed [here on pages 164-165](#chapter09.html#sec80).

![image](images/6r.jpg)Add a final statement to include a page footer

include ( ‘includes/footer.html’ ) ;      ?>

![image](images/7r.jpg)Save this script in your web browser’s /htdocs directory as post.php, then log in and follow the link on the Forum page to this Post Message page

![image](images/pg163_1.jpg)

![image](images/pg163_2.jpg)

![image](images/forget.jpg)

This page provides a hyperlink back to the Forum page, should the user wish to return there.

**Processing posted messages**

Having completed the PHP script to supply a form to post new forum messages, described [here on pages 162-163](#chapter09.html#sec79), you can now create a PHP script to process the submitted messages. This can check that the user is logged in then ensure that the subject and message fields are not empty. Once the form input is found to be valid, the script can then store the submitted message in the MySQL “forum” database table. If the attempt to post the message succeeds, the Forum page can be loaded to display the messages, or upon failure an error message can be displayed:

![image](images/pg164_1.jpg)

post\_action.php

![image](images/1r.jpg)Launch a plain text editor and begin a PHP script with a statement to allow access to session data

**<?php**

**session\_start() ;**

![image](images/2r.jpg)Next, add a statement to make the load function available

require ( ‘login\_tools.php’ ) ;

![image](images/3r.jpg)Now, add a statement to redirect the browser to the Login page if the user is not already logged in

if ( !isset( $\_SESSION\[ ‘user\_id’ \] ) ) { load() ; }

![image](images/4r.jpg)Add statements to set the page title and include a page header

$page\_title \= ‘Post Error’ ;

include ( ‘includes/header.html’ ) ;

![image](images/5r.jpg)Next, add a statements block to ensure the submitted form fields are not empty, or display an error message

if ( $\_SERVER\[ ‘REQUEST\_METHOD’ \] \== ‘POST’ )

**{**

if ( empty( $\_POST\[ ‘subject’\] ) )

{ echo ‘<p>Please enter a subject for this post.</p>’ ; }

if ( empty( $\_POST\[ ‘message’ \] ) )

{ echo ‘<p>Please enter a message for this post.</p>’; }

**\# Statements to be inserted here (Step 6).**

**}**

![image](images/forget.jpg)

This script is nominated by the form in **post.php** to process its submitted user data messages.

![image](images/6r.jpg)Insert statements into the block to add the form data to the MySQL “forum” database table

if( !empty( $\_POST\[ ‘subject’ \] )

&& !empty( $\_POST\[ ‘message’\] ) )

**{**

require ( ‘../connect\_db.php’ ) ;

$q \= “INSERT INTO forum

(first\_name,last\_name,subject,message,post\_date)

VALUES (

‘{$\_SESSION\[first\_name\]}’ ,

’{$\_SESSION\[last\_name\]}’ ,

’{$\_POST\[subject\]}’ ,

’{$\_POST\[message\]}’ ,

NOW() )” ;

$r \= mysqli\_query ( $dbc , $q ) ;

\# Statements to be inserted here (Step 7).

mysqli\_close( $dbc ) ;

**}**

![image](images/7r.jpg)Now, insert statements to display the forum messages on success, or display a MySQL error message on failure

if ( mysqli\_affected\_rows( $dbc ) != 1 )

**{**

echo ‘<p>Error</p>’.mysqli\_error( $dbc ) ;

**}**

**else**

**{**

load( ‘forum.php’ ) ;

**}**

![image](images/8r.jpg)After the statements block, add a statement to create a hyperlink back to the Forum page

echo ‘<p><a href=”forum.php”>Forum</a>’ ;

![image](images/9r.jpg)Add a final statement to include a page footer

include ( ‘includes/footer.html’ ) ; ?>

![image](images/10r.jpg)Save this script in your web browser’s /htdocs directory as post\_action.php, then submit the form with no subject or message to see the script display error messages

![image](images/hot.jpg)

This script supplies its own error messages if it finds empty form fields, or a MySQL error message if the data cannot be added to the database table.

![image](images/snake.jpg)

The form is not sticky so field data is not retained.

**Confirming post success**

Having created the PHP script to process submitted forum messages, described [here on pages 164-165](#chapter09.html#sec80), you can now test the message board process to ensure the validation checks perform correctly to display errors when appropriate, and that posted messages appear on the Forum page.

![image](images/1r.jpg)Log in and navigate to the Post Message page, then enter a subject and message – submit the form to see the message appear on the message board

![image](images/pg166_1.jpg)

![image](images/pg166_2.jpg)

![image](images/forget.jpg)

The “Posted By” details are retrieved from the first\_name, last\_name, and post\_date columns of the MySQL “forum” database table.

![image](images/2r.jpg)Next, return to the Post Message page, then enter only a subject title and submit the form to see an error

![image](images/pg167_1.jpg)

![image](images/3r.jpg)Now, log in as different users and submit more messages to see them get added to the message board

![image](images/pg167_2.jpg)

![image](images/hot.jpg)

You can stop the MySQL Server service and post an empty form to see the MySQL error report.

![image](images/snake.jpg)

New forum messages are added to the bottom of the table here, but the order could be reversed by adding a SORT clause to the SQL query.

**Summary**

•User messages can be stored in a MySQL database table and retrieved later for display on a Forum page.

•Typically, a MySQL database forum table might store the post ID, users’ names, subject, message, and date of posting.

•Forum pages are often only available to registered users, so the PHP script providing a Forum page will check for user login.

•A Forum page will display a list of posted messages or advise that there are currently no messages.

•The Forum page can include a hyperlink to a page where the user can post new messages to the forum.

•A form to post forum messages will submit the subject and message to a PHP script for processing.

•The script processing posted messages stores the submitted subject and message data in a MySQL database table when the data is valid and the post attempt succeeds.

•The script processing posted messages also stores user details from session data in the MySQL database table together with the date and time that the message was posted by the user.

•PHP scripts to process messages posted to a forum should supply an error message when the post attempt fails.

•The script producing a Forum page can retrieve the user’s names, date of posting, subject, and message body for each message stored in a MySQL database table.

•Forum messages can be displayed in individual rows of a table on the Forum page.

10

Processing shops

***This chapter builds on the previous two chapters to demonstrate how to create a simple e-commerce shopping cart application.***

[**Creating a shop database**](#chapter10.html#sec83)

[**Creating an orders database**](#chapter10.html#sec84)

[**Providing a shop page**](#chapter10.html#sec85)

[**Confirming cart additions**](#chapter10.html#sec86)

[**Processing shopping carts**](#chapter10.html#sec87)

[**Checking out orders**](#chapter10.html#sec88)

[**Confirming logout success**](#chapter10.html#sec89)

[**Summary**](#chapter10.html#sec90)

**Creating a shop database**

Item details can be stored in a MySQL database table for display in a Shop page containing items for selection by registered users. Typically, a database table containing shop items might store the item’s ID, name, description, an illustrative image path and price:

 
| **Column Name:** || **Content Type:** || **Example:** |
| --- | --- | --- |
| **item\_id** || Number || 1 |
| **item\_name** || Text || Cow |
| **item\_desc** || Text || A meadow mate |
| **item\_img** || Text || images/cow.png |
| **item\_price** || Decimal || 10.00 |

The design of this database table requires that VARCHAR data types should be specified for columns storing text. Item IDs should be positive (UNSIGNED) integer INT values that the table automatically allocates with AUTO\_INCREMENT, and the price should be stored as a DECIMAL(4,2) value. All details will be required to store an item in the database table, so each column must have a NOT NULL rule.

The SQL command required to produce this design as a MySQL database table named “shop” can be issued at the prompt in the MySQL Command Line Client, or saved in an SQL file that can be implemented by issuing the SOURCE command.

The table can then be populated with items by issuing a further command describing each required item detail.

![image](images/pg170_1.jpg)

create\_shop.sql

![image](images/1g.jpg)Launch a plain text editor and create an SQL command describing the table requirements shown above

**CREATE TABLE IF NOT EXISTS shop (**

**item\_id INT UNSIGNED NOT NULL AUTO\_INCREMENT ,**

**item\_name VARCHAR(20) NOT NULL ,**

**item\_desc VARCHAR(200) NOT NULL ,**

**item\_img VARCHAR(20) NOT NULL ,**

**item\_price DECIMAL(4,2) NOT NULL ,**

**PRIMARY KEY ( item\_id ) ) ;**

![image](images/forget.jpg)

The illustrative image files, such as “cow.ash">png” must be contained in a folder named “images” located in your web server’s **/htdocs** directory.

![image](images/2g.jpg)Now, create an SQL command to populate the table

**INSERT INTO shop**

**( item\_name , item\_desc , item\_img , item\_price )**

**VALUES**

**( “Cow” , “A friendly field buddy.” ,**

“images/cow.png” , 19.99 ) ,

**( “Dog” , “A friendly lap buddy.” ,**

“images/dog.png” , 14.99 ) ,

**( “Goat” , “A friendly mountain buddy.” ,**

“images/goat.png” , 16.99 ) ,

**( “Leopard” , “A friendly spotted buddy.” ,**

“images/leopard.png” , 17.99 ) ,

**( “Rhino” , “A friendly jungle buddy.” ,**

“images/rhino.png” , 29.99 ) ;

![image](images/3g.jpg)Save the file in a folder at C:\\SQL as create\_shop.sql then launch the MySQL Command Line Client as the root user and issue a command to use the established database

USE site\_db ;

![image](images/4g.jpg)Now, implement the SQL command by stating the source path to the SQL file on your system

**SOURCE C:\\SQL\\create\_shop.sql**

![image](images/5g.jpg)Finally, issue a command to confirm the table format and to see all the items it contains

**EXPLAIN shop ; SELECT \* FROM shop ;**

![image](images/pg171_1.jpg)

![image](images/hot.jpg)

Notice how the table can be populated with multiple items in a single command by specifying their data groups as a comma-separated list.

**Creating an orders database**

Items selected by the user on a Shop page for an order can best be stored in two MySQL database tables – allowing the user to select multiple items in multiple orders if they so wish.

The first table simply contains summary details of order ID, user ID, total value, and the date on which the order was placed:

 
| **Column Name:** || **Content Type:** || **Example:** |
| --- | --- | --- |
| **order\_id** || Number || 8 |
| **user\_id** || Number || 123 |
| **total** || Decimal || 20.00 |
| **order\_date** || Date/Time || 2018-05-14 12:30:00 |

The second table contains content details of the actual items selected by content ID, order ID, item ID, quantity, and price:

 
| **Column Name:** || **Content Type:** || **Example:** |
| --- | --- | --- |
| **content\_id** || Number || 100 |
| **order\_id** || Number || 8 |
| **item\_id** || Number || 1 |
| **quantity** || Number || 2 |
| **price** || Decimal || 10.00 |

The order\_id, content\_id, and order\_date columns are generated by MySQL. The user\_id is supplied by the “users” table for the current logged-in user, and the item\_id is supplied by the “shop” table for the selected item. Submission of the shopping cart supplies the price and quantity from which the total is calculated.

![image](images/hot.jpg)

Notice that this shopping cart application utilizes four tables (users, shop, orders, order\_contents) perfectly demonstrating the “relational” aspect of MySQL databases.

![image](images/pg173_1.jpg)

create\_orders.sql

![image](images/1g.jpg)Launch a plain text editor and create an SQL command describing the first table requirements shown opposite

**CREATE TABLE IF NOT EXISTS orders (**

**order\_id INT UNSIGNED NOT NULL AUTO\_INCREMENT ,**

**user\_id INT UNSIGNED NOT NULL ,**

**total DECIMAL(8,2) NOT NULL ,**

**order\_date DATETIME NOT NULL ,**

**PRIMARY KEY ( order\_id ) ) ;**

![image](images/pg173_2.jpg)

create\_order\_contents.sql

![image](images/2g.jpg)Save the file in a folder at C:\\SQL as create\_orders.sql, then create an SQL command describing the second table requirements

**CREATE TABLE IF NOT EXISTS order\_contents (**

**content\_id INT UNSIGNED NOT NULL AUTO\_INCREMENT ,**

**order\_id INT UNSIGNED NOT NULL ,**

item\_id INT UNSIGNED NOT NULL ,

**quantity INT UNSIGNED NOT NULL DEFAULT 1,**

**price DECIMAL(4,2) NOT NULL ,**

**PRIMARY KEY ( content\_id ) ) ;**

![image](images/3g.jpg)Save the file as create\_order\_contents.sql, then launch the MySQL Command Line Client as the root user and issue a command to use the established database

**USE site\_db ;**

![image](images/4g.jpg)Now, implement the SQL commands by stating the source path to the SQL files and confirm the table format

**SOURCE C:\\SQL\\create\_orders.sql**

**SOURCE C:\\SQL\\create\_order\_contents.sql**

**EXPLAIN orders ; EXPLAIN order\_contents ;**

![image](images/pg173_3.jpg)

**Providing a shop page**

Having created the “shop” database, described [here on pages 170-171](#chapter10.html#sec83), you can now create the PHP script to display all items that may be selected for addition to the shopping cart. Each item will be displayed on the Shop page in a table cell containing the item details, and its associated image, together with a hyperlink for adding that item to the shopping cart.

![image](images/pg174_1.jpg)

shop.php

![image](images/1g.jpg)Launch a plain text editor and begin a PHP script with a statement to allow access to session data

**<?php**

**session\_start() ;**

![image](images/2g.jpg)Now, add statements to redirect the browser to the Login page if the user is not already logged in

**if ( !isset( $\_SESSION\[ ‘user\_id’ \] ) )**

**{**

**require ( ‘login\_tools.php’ ) ;**

**load() ;**

**}**

![image](images/3g.jpg)Next, add statements to set the page title and include a page header

**$page\_title \= ‘Shop’ ;**

**include ( ‘includes/header.html’ ) ;**

![image](images/4g.jpg)Add a statement to open the database connection

**require ( ‘../connect\_db.php’ ) ;**

![image](images/5g.jpg)Now, add statements to retrieve all items from the database or provide a default message

**$q \= “SELECT \* FROM shop” ;**

**$r \= mysqli\_query( $dbc , $q ) ;**

**if ( mysqli\_num\_rows( $r ) > 0 )**

**{**

**\# Statements to be inserted here (Step 6).**

**}**

**else**

**{**

**echo ‘<p>There are currently no items in this shop.</p>’ ;**

**}**

![image](images/forget.jpg)

The user must be logged in to access this page so their user ID can identify them when placing an order from the shop.

![image](images/6g.jpg)Next, insert statements displaying all items retrieved from the database table then closing the database connection

**echo ‘<table><tr>’ ;**

**while ( $row \= mysqli\_fetch\_array( $r , MYSQLI\_ASSOC ) )**

**{**

**echo ‘<td><strong>’ . $row\[‘item\_name’\] .**

**’</strong><br>’ . $row\[‘item\_desc’\] .**

**‘<br><img src=’. $row\[‘item\_img’\] .**

**’><br>$’ . $row\[‘item\_price’\] .**

**‘<br><a href=”added.php?id=’ . $row\[‘item\_id’\] .**

**’”>Add To Cart</a></td>’;**

**}**

**echo ‘</tr></table>’ ;**

**mysqli\_close( $dbc ) ;**

![image](images/7g.jpg)Add a statement to create hyperlinks to other pages on the website, including a “View Cart” page

**echo ‘<p><a href=”cart.php”>View Cart</a> |**

**<a href=”forum.php”>Forum</a> |**

**<a href=”home.php”>Home</a> |**

**<a href=”goodbye.php”>Logout</a></p>’ ;**

![image](images/8g.jpg)Add a final statement to include a page footer

**include ( ‘includes/footer.html’ ) ;**

![image](images/9g.jpg)Save this script in your web browser’s /htdocs directory as shop.php then log in and visit the Shop page

![image](images/pg175_1.jpg)

![image](images/hot.jpg)

Notice that the hyperlink to add an item to the cart appends the item ID when the link is followed – so the target page can identify the item.

![image](images/forget.jpg)

The illustrative image files, such as “cow.png” must be contained in a folder named “images” located in your web server’s **/htdocs** directory.

**Confirming cart additions**

Having provided the Shop page, described [here on pages 174-175](#chapter10.html#sec85), you can now create the PHP script that will store items selected by the user in a session variable array. This will use the item’s ID number, appended in the “Add To Cart” hyperlink, to retrieve the associated item name from the “shop” database table for display in a confirmation message that the item has been added to the cart.

![image](images/pg176_1.jpg)

added.php

![image](images/1g.jpg)Launch a plain text editor and begin a PHP script with a statement to allow access to session data

**<?php**

**session\_start() ;**

![image](images/2g.jpg)Now, add statements to redirect the browser to the Login page if the user is not already logged in

**if ( !isset( $\_SESSION\[ ‘user\_id’ \] ) )**

**{**

**require ( ‘login\_tools.php’ ) ;**

**load() ;**

**}**

![image](images/3g.jpg)Next, add statements to set the page title and include a page header

**$page\_title \= ‘Cart Addition’ ;**

**include ( ‘includes/header.html’ ) ;**

![image](images/4g.jpg)Assign the passed item ID to a variable

**if ( isset( $\_GET\[‘id’\] ) ) $id \= $\_GET\[‘id’\] ;**

![image](images/5g.jpg)Now, add a statement to open the database connection

**require ( ‘../connect\_db.php’ ) ;**

![image](images/6g.jpg)Next, add statements to retrieve the selected item’s data from the database

**$q \= “SELECT \* FROM shop WHERE item\_id = $id ” ;**

**$r \= mysqli\_query( $dbc , $q ) ;**

**if ( mysqli\_num\_rows( $r ) == 1 )**

**{**

**$row \= mysqli\_fetch\_array( $r , MYSQLI\_ASSOC ) ;**

**\# Statements to be inserted here (Step 7).**

**}**

![image](images/forget.jpg)

The ID number of the selected item is appended to the URL of this web page by the Shop page’s PHP script.

![image](images/7g.jpg)Insert statements to add the selected item to the cart and display an appropriate confirmation message

**if ( isset( $\_SESSION\[‘cart’\]\[$id\] ) )**

**{**

**$\_SESSION\[‘cart’\]\[$id\]\[‘quantity’\]++ ;**

**echo ‘<p>Another ‘.$row\[“item\_name”\].**

**’ has been added to your cart</p>’;**

**}**

**else**

**{**

**$\_SESSION\[‘cart’\]\[$id\]\=**

**array ( ‘quantity’ => 1, ‘price’ => $row\[‘item\_price’\] ) ;**

**echo ‘<p>A ‘.$row\[“item\_name”\].**

**’ has been added to your cart</p>’ ;**

**}**

![image](images/8g.jpg)Next, add a statement to close the database connection

**mysqli\_close( $dbc ) ;**

![image](images/9g.jpg)Now, add a statement to create hyperlinks to other pages on the website

**echo ‘<p><a href=”shop.php”>Shop</a> |**

**<a href=”cart.php”>View Cart</a> |**

**<a href=”forum.php”>Forum</a> |**

**<a href=”home.php”>Home</a> |**

**<a href=”goodbye.php”>Logout</a></p>’ ;**

![image](images/10g.jpg)Add a final statement to include a page footer

**include ( ‘includes/footer.html’ ) ;**

![image](images/11g.jpg)Save this script in your web browser’s /htdocs directory as added.php, then add an item to the cart on the Shop page

![image](images/pg177_1.jpg)

![image](images/hot.jpg)

Notice that the cart array quantity is set to 1 and its price is set when the first item with that ID gets added, otherwise its quantity is simply incremented by 1.

![image](images/snake.jpg)

Reloading this web page in your browser will once more pass the selection to the script – increasing its cart quantity again.

**Processing shopping carts**

Having provided a page to confirm addition of a selected item to the shopping cart, described [here on pages 176-177](#chapter10.html#sec86), you can now create the PHP script that will display a summary of all selections. This will use the session data to create a table of selected items and quantities, retrieve their associated name and description from the database, calculate a total, and allow quantities to be updated.

![image](images/pg178_1.jpg)

cart.php

![image](images/1g.jpg)Launch a plain text editor and begin a PHP script with a statement to allow access to session data

**<?php**

**session\_start() ;**

![image](images/2g.jpg)Now, add statements to redirect the browser to the Login page if the user is not already logged in

**if ( !isset( $\_SESSION\[ ‘user\_id’ \] ) )**

**{**

**require ( ‘login\_tools.php’ ) ;**

**load() ;**

**}**

![image](images/3g.jpg)Next, add statements to set the page title and include a page header

**$page\_title \= ‘Cart’ ;**

**include ( ‘includes/header.html’ ) ;**

![image](images/4g.jpg)Add statements to update the quantities if the page has been submitted for amendment

**if ( $\_SERVER\[‘REQUEST\_METHOD’\] \== ‘POST’ )**

**{**

**foreach ( $\_POST\[‘qty’\] as $item\_id \=> $item\_qty )**

**{**

**\# Ensure values are integers.**

**$id \= (int) $item\_id ;**

**$qty \= (int) $item\_qty ;**

**\# Change quantity or delete if zero.**

if ( $qty \== 0 )

**{ unset ( $\_SESSION\[‘cart’\]\[$id\] ) ; }**

**elseif ( $qty \> 0 )**

**{ $\_SESSION\[‘cart’\]\[$id\]\[‘quantity’\] \= $qty ; }**

**}**

**}**

![image](images/forget.jpg)

The user might enter a non-numeric value into the quantity update field so the script must ensure the quantity field value is indeed an integer.

![image](images/5g.jpg)Now, initialize a grand total variable

**$total \= 0 ;**

![image](images/6g.jpg)Next, add a statement to display the contents of the shopping cart, or display a message if the cart is empty

**if ( !empty( $\_SESSION\[‘cart’\] ) )**

**{**

**\# Statements to be inserted here (Steps 7-11).**

**}**

**else**

**{ echo ‘<p>Your cart is currently empty.</p>’ ; }**

![image](images/7g.jpg)Insert a first statement to open the database connection

**require ( ‘../connect\_db.php’ ) ;**

![image](images/8g.jpg)Next, insert statements to retrieve data from the “shop” database for all associated items in the shopping cart

**$q \= “SELECT \* FROM shop WHERE item\_id IN (“ ;**

**foreach ( $\_SESSION\[‘cart’\] as $id \=> $value )**

**{ $q .= $id . ‘,’ ; }**

**$q \= substr( $q , 0 , -1 ) . ‘) ORDER BY item\_id ASC’ ;**

**$r \= mysqli\_query ( $dbc , $q ) ;**

![image](images/9g.jpg)Now, insert statements to display the cart selections in a form that contains a table

**echo ‘<form action=”cart.php” method=”POST”><table>**

**<tr><th colspan=”5”>Items in your cart</th></tr><tr>’ ;**

**while ( $row \= mysqli\_fetch\_array ( $r , MYSQLI\_ASSOC ) )**

**{**

**\# Calculate sub-totals and grand total.**

**$subtotal \= $\_SESSION\[‘cart’\]\[$row\[‘item\_id’\]\]\[‘quantity’\]**

**\* $\_SESSION\[‘cart’\]\[$row\[‘item\_id’\]\]\[‘price’\] ;**

**$total += $subtotal ;**

**\# Display the row.**

**echo “<tr> <td>{$row\[‘item\_name’\]}</td>**

**<td>{$row\[‘item\_desc’\]}</td>**

**<td><input type=\\”text\\” size=\\”3\\”**

name=\\”qty\[{$row\[‘item\_id’\]}\]\\”

value=\\”{$\_SESSION\[‘cart’\]\[$row\[‘item\_id’\]\]\[‘quantity’\]}\\”>

**</td> <td>@ {$row\[‘item\_price’\]} = </td>**

**<td>”.number\_format ( $subtotal , 2 ).”</td></tr>” ;**

**}**

![image](images/hot.jpg)

The **foreach** loop adds each item ID plus a comma to the query, and the **substr()** function removes the final comma.

![image](images/hot.jpg)

The SQL **ORDER BY** clause will ensure the selected items are displayed in the order of their number ID.

![image](images/10g.jpg)Insert a statement to display the grand total at the end of the table and a submit button at the end of the form

**echo ‘ <tr><td colspan=”5”>**

**Total = ‘.number\_format( $total , 2 ).’</td></tr>**

**</table>**

**<input type=”submit” value=”Update My Cart”>**

**</form>’ ;**

![image](images/11g.jpg)Now, insert a statement to close the database connection

**mysqli\_close( $dbc ) ;**

![image](images/12g.jpg)Add a statement to create hyperlinks to other pages on the website, including a “Checkout” page that appends the grand total to the URL

**echo ‘<p><a href=”shop.php”>Shop</a> |**

**<a href=”checkout.php?total=’.$total.’”>Checkout</a> |**

**<a href=”forum.php”>Forum</a> |**

**<a href=”home.php”>Home</a> |**

**<a href=”goodbye.php”>Logout</a></p>’ ;**

![image](images/13g.jpg)Add a final statement to include a page footer

**include ( ‘includes/footer.html’ ) ;**

![image](images/14g.jpg)Save this script in your web browser’s /htdocs directory as cart.php, then select items on the Shop page and view the cart to see the selection details and values

![image](images/pg180_1.jpg)

![image](images/forget.jpg)

Appending the total value to the Checkout page URL enables that page to confirm that the cart is not empty.

![image](images/15g.jpg)Now, change the value in the quantity field of one of the items and click the Update button to see the revised cart

![image](images/pg181_1.jpg)

![image](images/pg181_2.jpg)

![image](images/hot.jpg)

You can change all quantities to zero and click the Update button to see the default empty cart message.

**Checking out orders**

Having produced a shopping cart page, described [here on pages 174-181](#chapter10.html#sec85), you can now create a PHP script to process the user’s selected items as a “checkout” order. This is the culmination of the shopping cart process and will store the cart selections in the “order” and “order\_contents” database tables for subsequent fulfilment by the supplier.

![image](images/pg182_1.jpg)

checkout.php

![image](images/1g.jpg)Launch a plain text editor and begin a PHP script with a statement to allow access to session data

**<?php**

**session\_start() ;**

![image](images/2g.jpg)Now, add statements to redirect the browser to the Login page if the user is not already logged in

**if ( !isset( $\_SESSION\[ ‘user\_id’ \] ) )**

**{ require ( ‘login\_tools.php’ ) ; load() ; }**

![image](images/3g.jpg)Next, add statements to set the page title and include a page header

**$page\_title \= ‘Checkout’ ;**

**include ( ‘includes/header.html’ ) ;**

![image](images/4g.jpg)Add statements to store the shopping cart items in the database or provide a default message

**if ( isset( $\_GET\[‘total’\] )**

**&& ( $\_GET\[‘total’\] \> 0 )**

**&& ( !empty( $\_SESSION\[‘cart’\] ) ) )**

**{**

**\# Statements to be inserted here (Steps 5-10).**

**}**

**else**

**{ echo ‘<p>There are no items in your cart.</p>’ ; }**

![image](images/5g.jpg)Now, insert a statement to open the database connection

**require ( ‘../connect\_db.php’ ) ;**

![image](images/6g.jpg)Next, insert statements to store the user ID, total order value, and current date/time in the “orders” database table

**$q \=**

**“INSERT INTO orders ( user\_id , total , order\_date ) VALUES (“**

**. $\_SESSION\[‘user\_id’\].”,”.$\_GET\[‘total’\].”, NOW() ) ” ;**

**$r \= mysqli\_query ( $dbc , $q ) ;**

![image](images/forget.jpg)

The total value of the shopping cart is appended to the URL of this web page by the cart page’s PHP script.

![image](images/7g.jpg)Insert a statement to retrieve the current order number

**$order\_id \= mysqli\_insert\_id( $dbc ) ;**

![image](images/8g.jpg)Now, add statements to retrieve the selected cart item details from the “shop” database

**$q \= “SELECT \* FROM shop WHERE item\_id IN (“ ;**

**foreach ( $\_SESSION\[‘cart’\] as $id \=> $value )**

**{ $q .= $id . ‘,’ ; }**

**$q \= substr( $q , 0 , -1 ) . ‘) ORDER BY item\_id ASC’ ;**

**$r \= mysqli\_query ( $dbc , $q ) ;**

![image](images/9g.jpg)Next, insert statements to store the item details in the “order\_contents” database

**while ( $row \= mysqli\_fetch\_array ( $r , MYSQLI\_ASSOC ) )**

**{**

**$query \= “INSERT INTO order\_contents**

**( order\_id, item\_id, quantity, price )**

VALUES ( $order\_id , “.$row\[‘item\_id’\].”,”.

**$\_SESSION\[‘cart’\]\[$row\[‘item\_id’\]\]\[‘quantity’\].”,”.**

**$\_SESSION\[‘cart’\]\[$row\[‘item\_id’\]\]\[‘price’\].”)” ;**

**$result \= mysqli\_query( $dbc , $query ) ;**

**}**

![image](images/10g.jpg)Insert statements to close the database connection, display a confirmation message, and empty the cart

**mysqli\_close( $dbc ) ;**

**echo “<p>Thanks for your order.**

**Your Order Number Is #”.$order\_id.”</p>” ;**

**$\_SESSION\[‘cart’\] \= NULL ;**

![image](images/11g.jpg)Add a statement to create hyperlinks to other pages on the website, including a “Logout” page

**echo ‘<p><a href=”shop.php”>Shop</a> |**

**<a href=”forum.php”>Forum</a> |**

**<a href=”home.php”>Home</a> |**

**<a href=”goodbye.php”>Logout</a></p>’ ;**

![image](images/12g.jpg)Add a final statement to include a page footer

**include ( ‘includes/footer.html’ ) ;**

![image](images/13g.jpg)Save this script in your web browser’s /htdocs directory as checkout.php to complete the shopping cart application

![image](images/hot.jpg)

The **foreach** loop adds each item ID plus a comma to the query, and the **substr()** function removes the final comma.

![image](images/snake.jpg)

Payment processing is not included in this example but could be added before the checkout has ended.

**Confirming logout success**

Having produced a Checkout page, described [here on pages 182-183](#chapter10.html#sec88), you can now create a PHP script to allow the user to log out from the website. This destroys all session data so the user cannot access the website without logging in once more.

![image](images/pg184_1.jpg)

goodbye.php

![image](images/1g.jpg)Launch a plain text editor and begin a PHP script with a statement to allow access to session data

**<?php**

**session\_start() ;**

![image](images/2g.jpg)Now, add statements to redirect the browser to the Login page if the user is not already logged in

**if ( !isset( $\_SESSION\[ ‘user\_id’ \] ) )**

{ require ( ‘login\_tools.php’ ) ; load() ; }

![image](images/3g.jpg)Next, add statements to set the page title and include a page header

**$page\_title \= ‘Goodbye’ ;**

**include ( ‘includes/header.html’ ) ;**

![image](images/4g.jpg)Add a statement to clear existing session variables

**$\_SESSION \= array() ;**

![image](images/5g.jpg)Now, add a statement to end the session

**session\_destroy() ;**

![image](images/6g.jpg)Next, add a statement to display a confirmation message and provide a hyperlink back to the Login page

**echo ‘<h1>Goodbye!</h1>**

**<p>You are now logged out.</p>**

**<p><a href=”login.php”>Login</a></p>’ ;**

![image](images/7g.jpg)Finally, add a statement to include a page footer

**include ( ‘includes/footer.html’ ) ;**

![image](images/8g.jpg)Save the script in your web browser’s /htdocs directory as goodbye.php, then select items from the shop, checkout, then log out from the website

![image](images/pg185_1.jpg)

![image](images/pg185_2.jpg)

PHP and MySQL are a flexible, powerful combination that have an important role to fill in the future of the web.

![image](images/forget.jpg)

By default, a session does not end until the user closes their browser – so the PHP script must end the session when the user logs out.

![image](images/hot.jpg)

You could easily extend the Checkout page script to include order details.

**Summary**

•Item details can be stored in a MySQL database table for display in a Shop page containing items for selection.

•Typically, a database table containing shop items might store the item ID, name, description, image path, and price.

•Order details can be stored in two related MySQL database tables allowing selection of multiple items in multiple orders.

•Typically, a database table containing order summary details might store the order ID, user ID, total value, and order date.

•A database table containing order content details might store the content ID, order ID, user ID, quantity, and price.

•A shop item can be added to the shopping cart by appending its ID to a hyperlink to the cart page.

•Details of items in a shopping cart can be stored in a session variable array.

•Session data can be used to create a table of selected items and quantities by retrieving their associated name and description.

•A PHP script to display shopping cart contents can calculate the total value and be easily updated by the user.

•Checkout stores the items in a shopping cart as an order in related database tables containing order summary and contents.

•A supplier can retrieve order details stored in a MySQL database to subsequently fulfill orders.

•A PHP logout script must destroy all session data so the user cannot access the website until they log in once more.

![image](images/bm1.jpg)

![image](images/bm2.jpg)

![image](images/bcover.jpg)