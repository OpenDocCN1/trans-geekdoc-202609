**ISBN: 978-93-5620-360-0**

# Learning Server-Side Scripting

## AN IMPLEMENTATION BOOK ON PHP-MySQL

By

### SHANMUGAPRIYAA S

Title: Learning Server-Side Scripting

Author: Shanmugapriyaa S

Published By: Self-Published

  

Copyright © 2022 Shanmugapriyaa S.

All rights reserved. No portion of this e-book may be reproduced in whole or in part in any form.

# Introduction

* * *

Websites in the earlier years comprised only static web pages, that is, web page content would appear exactly the same for every user. The need for dynamic web pages started growing, where the pages appear different for different users. To enable a web page to display dynamic content for different users, we require a scripting language which is used along with HTML in web pages. One such scripting language is PHP.

HTML takes care of rendering the web page design; while PHP takes care of processing the content inside the web page. PHP not only helps in delivering dynamic content to the page but also helps in interacting with databases to manipulate the stored data

This e-book integrates learning and application development:

*   Learning server-side scripting language - PHP
*   Developing Web Application using PHP and MySQL relational database

**What will you gain on reading and practising this e-book?**

*   Know the need of scripting languages
    
*   Install PHP in your system
    
*   Work with PHP syntax and check results in the browser
    
*   Understand programming constructs such as conditionals, loops, files and use them in scripting
    
*   Understand the use of forms and web related concepts
    
*   Design a web application
    
*   Set up the working environment and MySQL database
    
*   Design relevant forms for the application
    
*   Connect the forms with database using PHP-MySQL
    
*   Bind the works as a web application
    

I assume, whoever reads this e-book will have exposure to HTML and SQL.

This e-book will help you design and develop a web application from scratch using PHP and MySQL.

You can consider this e-book as a self-guiding material to make your learning comfortable.

Let us start learning!

* * *

# Chapter 1: Overview of PHP

* * *

*   [](#part0004.xhtml)
    
    #### 1.1 Introduction to Web Application
    
*   [](#part0005.xhtml)
    
    #### 1.2 Role of Server-side Scripting
    
*   [](#part0006.xhtml)
    
    #### 1.3 Introduction to PHP
    
*   [](#part0007.xhtml)
    
    #### 1.4 Installation of PHP
    
*   [](#part0008.xhtml)
    
    #### 1.5 Start Coding PHP
    

* * *

### 1.1 Introduction to Web Application

* * *

We will first understand the difference between a website and a web application.

A website is a collection of web pages. The website is hosted on a web server and accessible via browser.

*A web application is a software or program, hosted in a server, which is accessible using any web browser.*

**Difference between website and web application:**

![1-1-websiteandapplication](Images/image00130.jpeg)

Web applications can be served through websites (that is, web pages).

All websites run on three components: the server, the database, and the client.

*   The server is at a remote location anywhere in the world, running a site’s back-end architecture, processing requests, and sending pages to the browser.
*   The database resides on a server.
*   The client is anywhere your users are viewing your site: mobile devices, laptops, or desktop computers.

**Server-side scripting is executed by a web server** whereas, client-side scripting is executed by a browser.

When we talk about servers, there are indeed two servers involved in web applications.

*   Web Server
*   Application Server

A web server will be sufficient for a website while a web application would need a web server and an application server.

**Web server vs Application server:**

*   A web server accepts and fulfills requests from clients for static content (i.e., HTML pages, files, images, videos). Web servers handle HTTP requests and responses only.

*   An application server generates dynamic content. It is a software framework that transforms data to provide the functionality offered by an application. Application servers enhance the interactive parts of a website making a page different for different users based on the request.

Have a look at the diagram below for a detailed view:

![webserver-webapp](Images/image00131.jpeg)

![1-1-webandapplicationserver](Images/image00132.jpeg)

Hope you are clear with the explanation on servers.

* * *

### 1.2 Role of Server-side Scripting

* * *

In computing terminology, both “client” and “server” refer to computers that are used for different purposes.

We will first discuss the difference between client-side and server-side scripting or programming.

**Client-side Programming:**

A client is a computer application, such as a web browser, that runs on a user's local computer or workstation and connects to a server.

It is the program that runs on the client machine (browser) and deals with the user interface/display and any other processing that can happen on client machine.

**Features of client-side programming** include:

1) Interact with temporary storage

2) Make interactive web pages

3) Send request to server

4) Work as an interface between server and user

**Programming languages for client-side programming** are:

1) JavaScript

2) VBScript

3) HTML

4) CSS

5) AJAX

**Server-side Programming:**

A server machine is a large-capacity computer that can store a wide variety of files such as application files and data files.

It is the program that runs on server dealing with the generation of web page content.

**Features of server-side programming** include:

1) Querying the database

2) Operations over databases

3) Access/Write a file on server.

4) Interact with other servers.

5) Structure web applications.

6) Process user input.  
\[For example, if user input is a text in search box, run a search algorithm on the data stored on server and send the results\]

**Programming languages for server-side programming** are:

1) PHP

2) C++

3) Java and JSP

4) Python

5) Ruby on Rails

We have now learnt some information on client side and server side programming.

Let us now learn 2 other terminologies: front-end and back-end.

**Front-end vs Back-end:**

Front-end development involves all the things the user sees and interacts with, making web design and user experience as key concerns. Back-end development covers the server and databases.

In practice, front-end development is usually focused on client-side techniques that make use of HTML, CSS and JavaScript, while server-side scripting remains more relevant to back-end developers.

Overall, this e-book is based on back-end development where we induce server-side scripting.

**Role of Server-side scripting:**

The diagram below gives a nutshell view of the various roles done by server-side scripts.

![serverside-scripting-role](Images/image00133.jpeg)

Let us have a tabulated look on the advantages and disadvantages of server-side scripting:

![1-2advantagesdisadvantages](Images/image00134.jpeg)

The majority of websites now use dynamic content, much of which is managed using server-side scripting. Without server-side scripting, the functionality of the internet (as we know it today) would just not exist.

In this e-book, we will learn about the server-side scripting language - PHP.

* * *

### 1.3 Introduction to PHP

* * *

*PHP (Hypertext Preprocessor) is a programming language that allows web developers to create dynamic content that interacts with databases.*

*   PHP is a widely used open source server scripting language and a powerful tool for making dynamic and interactive Web pages.
*   PHP is basically used for developing web based software applications.
*   PHP code is executed on the server.

If you are a beginner in learning server side languages, then PHP will be the right and the easiest choice to start with.

PHP started out as a small open source project that evolved as more and more people found out how useful it was. Rasmus Lerdorf unleashed the first version of PHP way back in 1994.

**Reasons for choosing PHP:**

*   It runs on various platforms (Windows, Linux, Unix, Mac OS X, etc.)
*   It is compatible with almost all servers used today (Apache, IIS, etc.)
*   It runs efficiently on the server side
*   It supports a wide range of databases
*   It is free. Download it from the official PHP resource: [www.php.net](https://www.php.net)
*   PHP supports a large number of major protocols such as POP3, IMAP, and LDAP. PHP4 added support for Java and distributed object architectures (COM and CORBA), making n-tier development a possibility for the first time.
*   PHP Syntax is C-Like.

It is always better to learn a technology which is open source (free). The main reason is you can explore top-to-bottom about the technology. When you access a paid technology, your learning is limited to what you pay.

**Characteristics of PHP**

Five important characteristics make PHP's practical nature possible:

*   Simplicity
*   Efficiency
*   Security
*   Flexibility
*   Familiarity

**Applications of PHP**

*   It performs system file functions, i.e. on a system, it can create, open, read, write, and close files.
*   It can handle forms, i.e. gather data from files, save data to a file, send data through email, return data to the user.
*   You can add, delete, modify elements within your database through PHP.
*   You can Set and Access cookies variables.
*   You can restrict users to access some pages of your website using PHP.
*   It can encrypt data.

**A Note on PHP page:**

*   A PHP page / file can consist of HTML, CSS, JavaScript and PHP codes.
*   PHP files are saved using the extension .php
*   Once the code gets executed by the server, the result is returned to the browser as plain HTML.
*   The output is not limited to HTML. You can output images, PDF files, and even Flash movies. You can also output any text, such as XHTML and XML.

**A Note on PHP 7 (Used in this e-book):**

*   PHP 7 is much faster than the previous popular stable release (PHP 5.6)
*   PHP 7 has improved Error Handling
*   PHP 7 supports stricter Type Declarations for function arguments
*   PHP 7 supports new operators (like the spaceship operator: <=> )

Hope you have got some idea on PHP.

* * *

### 1.4 Installation of PHP

* * *

If you wish to install PHP, you will additionally need a server to be installed in your system. The reason is that, this server will enact as a web server to execute the scripts coded in PHP.

What do we need?

1\. PHP

2\. Web Server (we will go with Apache server - this also enacts as the application server)

3\. MySQL database

We will proceed with a quick installation using XAMPP stack. Instead of installing PHP, Apache and MySQL separately, we will install XAMPP which will in turn install all the necessities.

Note: Make sure you don’t have any of PHP / Apache / MySQL previously installed in your system. In case you have a version installed, kindly uninstall them before proceeding.

**Installation Instructions:**

1.  Go to XAMPP download page - [https://www.apachefriends.org/download.html](https://www.apachefriends.org/download.html)
    
2.  Download the installer respective to your system's operating system
    
    At the time of publishing this e-book, the stable version is 7.4.  
    When I installed XAMPP for demo purpose, I used 7.3 version.
    
3.  Installation Steps
    
    *   Double click XAMPP installer
        
    *   Click Next
        
        ![1](Images/image00135.jpeg)
        
    *   Select all the components and Click Next.  
        Apache, MySQL, PHP, phpMyAdmin are mandatory.
        
        ![2](Images/image00136.jpeg)
        
    *   Choose a Folder (path) to install XAMPP
        
        ![3-1](Images/image00137.jpeg)
        
    *   Uncheck the checkbox and Click Next
        
        ![5](Images/image00138.jpeg)
        
    *   Click Next
        
        ![6](Images/image00139.jpeg)
        
    *   Installation process
        
        ![7](Images/image00140.jpeg)
        
    *   Click Finish (Check \[Select\] the checkbox to start Control Panel)
        
        ![8](Images/image00141.jpeg)
        
    *   This is the XAMPP Control Panel
        
        ![10](Images/image00142.jpeg)
        
    *   Start Apache Server and MySQL to check if they are working properly
        
        ![11](Images/image00143.jpeg)
        
    *   If PHP is successfully installed, you can see the localhost's dashboard page!
        
    *   Click Admin button next to Apache, you will land on [http://localhost/dashboard](#part0007.xhtml)
        
        ![final](Images/image00144.jpeg)
        
    *   Click Admin button next to MySQL, you will land on [http://localhost/phpmyadmin](#part0007.xhtml)
        
        ![final2](Images/image00145.jpeg)
        
4.  Once the installation is over, start Apache as for now. MySQL will be needed from Chapter-6, so you can start it later
    

* * *

### 1.5 Start Coding PHP

* * *

**Where do we code?**

PHP needs a text editor to be scripted. You can use any text editor like Notepad, Notepad++, etc. You are free to use Visual Studio Code or any such editors or even IDEs to script. But I recommend you not to use any IDE’s or code builders. Code builders will assist you in coding but your learning graph will not be proper.

So, either go with Notepad++ or any such simple text editor! I recommend using Notepad++ due to syntax highlighting (PHP syntax will be highlighted in colors)

**Start Coding PHP:**

Let us take a single line PHP script.

1\. Open text editor

2\. Type the following:

```
<?php
echo "Testing PHP code";
?>
```

3\. Create a folder named **PracticePHP** in the location C:/xampp/htdocs. htdocs is the folder from where your web pages will be served via localhost.This path C:/xampp/htdocs/PracticePHP will be your file saving path.

4\. Save the file as **test.php** in the file saving path - C:/xampp/htdocs/PracticePHP

5\. Make sure Apache is started in XAMPP

6\. Go to the browser and type: [http://localhost/PracticePHP/test.php](#part0008.xhtml)

Hope you can see the output as below:

![testphp](Images/image00146.jpeg)

If you can see the output, your installation and saving location are perfect. Since this is the first script, I have posted it along with the URL of the page. Only if this test page works, it means your system is running PHP. Else, we need to check what went wrong!

One of the most common errors encountered is - site not reachable. When you find site not reachable message, it means you have not started Apache! (Apache's port 80 may not be available)

**Note:**

When you try to open php page via double-click (as you click-open html file), it will not be opened in browser. PHP files/pages must always be accessed via a server. Always execute PHP pages from localhost!

Say, you try executing them from a browser using the file path (like a html file) as below, you can just see the code.

![1-5](Images/image00147.jpeg)

To process PHP script, we need a server (Apache in our case). Do not forget it anytime!

For the rest of the e-book,

*   When I mention, **save** the file, make sure you save it in the path - C:/xampp/htdocs/PracticePHP
*   When I mention, **execute** the script/file, it means you have to access it using browser, using the URL - http://localhost/PracticePHP

With this, I think you know what is PHP, how to install PHP using XAMPP and how to test a code!;

From here, you will start learning programming constructs in PHP. Try to execute all the code snippets to ensure hands-on experience!

Happy Learning and Coding!!!

* * *

# Chapter 2: Essentials of PHP

* * *

*   [](#part0010.xhtml)
    
    #### 2.1 Basics
    
*   [](#part0011.xhtml)
    
    #### 2.2 Variables
    
*   [](#part0012.xhtml)
    
    #### 2.3 Data Types
    
*   [](#part0013.xhtml)
    
    #### 2.4 Built-in Functions
    
*   [](#part0014.xhtml)
    
    #### 2.5 Arrays
    
*   [](#part0015.xhtml)
    
    #### 2.6 User-Defined Functions
    
*   [](#part0016.xhtml)
    
    #### 2.7 More on Functions
    
*   [](#part0017.xhtml)
    
    #### 2.8 Constants
    

* * *

### 2.1 Basics

* * *

A PHP script is executed on the server, and the plain HTML result is sent back to the browser.The script can be placed anywhere in the document.

**Syntax:**

```
<?php
// PHP code goes here
?>
```

*   A PHP script starts with <?php and ends with ?>.
    
*   PHP statements end with a semicolon (;).
    
*   In PHP, NO keywords (e.g. if, else, while, echo, etc.), classes, functions, and user-defined functions are case-sensitive. However; all variable names are case-sensitive! But, PHP is case sensitive in printing too.
    
*   The default file extension for PHP files is ".php".
    
*   A PHP file normally contains HTML tags, and some PHP scripting code.
    

**How to differentiate PHP code?**

The PHP parsing engine needs a way to differentiate PHP code from the other elements in the page. The mechanism for doing so is known as 'escaping to PHP'. There are 4 ways to do:

**Canonical PHP tags** - <?php...?>

If you use this style, you can be positive that your tags will always be correctly interpreted.

**Short-open (SGML-style) tags** - <?...?>

Short tags are the shortest option to enable PHP to recognize the tags

*   Choose the --enable-short-tags configuration option when you're building PHP.
*   Set the short\_open\_tag setting in your php.ini file to on.
*   This option must be disabled to parse XML with PHP because the same syntax is used for XML tags.

**ASP-style tags** - <%...%>

ASP-style tags mimic the tags used by Active Server Pages to describe code blocks. ASP-style tags look like this

To use ASP-style tags, you will need to set the configuration option in your php.ini file.

**HTML script tags**

HTML script tags look like this

<script language = "PHP">...</script>

**Note:** We will stick to canonical PHP tags throughout the course.

**Comments:**

A comment is the portion of a program that exists only for the human readers.

A comment in PHP code is a line that is not executed as a part of the program. There are two commenting formats in PHP

**Single-line comments**: //

**Multi-lines comments**: /\* \*/

**Why do we use comments?**

It may be helpful in providing short explanation of a code block. Let others understand your code. Sometimes, they can remind you of what you had been thinking when you wrote the code

**Whitespace in PHP:**

PHP is whitespace insensitive.

Whitespace includes spaces, tabs, and carriage returns (end-of-line characters).

PHP almost never matters how many whitespace characters you have in a row. One whitespace character is the same as many such characters.

* * *

**Statements in PHP:**

A statement in PHP is any expression that is followed by a semicolon (;).

A sequence of valid PHP statements that are enclosed by the PHP tags is a valid PHP program.

**Echo and Print Statements:**

There are two basic ways to get output: echo and print.

echo and print are both used to output data to the screen. echo is marginally faster than print.

![2-1-echo-print](Images/image00148.jpeg)

**echo Statement:**

The echo statement can be used with or without parentheses

**Syntax:**

```
echo or echo()
```

**Practice:**

Open a new file in the editor and save it as section2.php

```
<?php

//normal echo statement
echo "Hello!";

//echo statement with html tags inside
echo "<h2>Hello</h2>";

//multiple parameters
echo "This ", "is ", "an ", "example ";

?>
```

**Execute:**

Execute the script in the browser:

**![2-1-1](Images/image00149.jpeg)**

**print Statement**

The print statement can be used with or without parentheses

**Syntax:**

```
print or print()
```

**Practice:**

```
<?php
print "Normal statement";
print "<h4>HTML tag usage</h4>";
//try multiple parameters
print "Trying ","parameters";
?>
```

**Execute:**

You will receive an error as below because print accepts single parameter.

![2-1-2](Images/image00150.jpeg)

Now comment or remove the last statement. Let me comment as for now!

```
<?php
print "Normal statement";
print "<h4>HTML tag usage</h4>";
//try multiple parameters
//print "Trying ","parameters";
?>
```

Now look at the output:

![2-1-3](Images/image00151.jpeg)

Can you notice? echo’s last statement and print’s first statement are together instead of printing on next line. The reason is there is no mention of new line in between those 2 statements.

We will now insert a <br> tag in the first print statement:

```
<?php
print "<br>Normal statement";
print "<h4>HTML tag usage</h4>";
//try multiple parameters
//print "Trying ","parameters";
?>
```

You can find the difference in the output as below:

![2-1-4](Images/image00152.jpeg)

Use whitespaces in between words and check how much space is printed on the screen.

**Example:**

```
<?php
echo "checking...              ... for spaces";
?>
```

You will have only single space printed!

![2-1-5](Images/image00153.jpeg)

Hope you are now clear what echo and print statements do! They just print to the screen!

**Note-1:**

To demonstrate echo, print, whitespace we used <?php ?> tags multiple times. That is not the need actually!

Let me make the code as below:

```
<?php

//normal echo statement
echo "Hello!";

//echo statement with html tags inside
echo "<h2>Hello</h2>";

//multiple parameters
echo "This ", "is ", "an ", "example ";

print "<br>Normal statement";
print "<h4>HTML tag usage</h4>";
//try multiple parameters
//print "Trying ","parameters";

echo "checking...              ... for spaces";

?>
```

From the next section, I will be demonstrating the scripts alone. Make sure you add the opening and closing tags of php.

If you don’t add? Let us try that too!

Remove <?php and ?> from the above coding snippet. Here is the output:

![2-1-6](Images/image00154.jpeg)

Only the HTML tags will be printed! So do not forget to add PHP tags to every PHP file!

**Note-2:**

Shall we check the page source to know what happens to the server-script?

Consider this code snippet:

```
<?php
//normal echo statement
echo "Hello!";

//echo statement with html tags inside
echo "<h2>Hello</h2>";

//multiple parameters
echo "This ", "is ", "an ", "example ";

print "<br>Normal statement";
print "<h4>HTML tag usage</h4>";
//try multiple parameters
//print "Trying ","parameters";

echo "checking...              ... for spaces";
?>
```

Execute the script!

Right-Click on browser and choose View Page Source! (Or just Ctrl + U)

You can find the HTML tags coded clearly! In case of PHP, the output is alone shown but not the script!

![2-1-7](Images/image00155.jpeg)

This is how server-side renders the HTML part to the browser! That is, browser cannot view the server-side scripting code!

Try executing few more codes to understand how HTML is rendered.

* * *

### 2.2 Variables

* * *

A variable is used to store information in PHP programs.

**How to use variables?**

*   Variables are assigned using the = operator, with the variable on the left-hand side and the expression to be evaluated on the right.
*   The value of a variable is the value of its most recent assignment.

**Features of PHP variables:**

*   Variables can be declared / assigned anywhere in the script.
*   Variables can, (but do not need to) be declared before assignment.
*   A variable does not know in advance whether it will be used to store a number or a string of characters.
*   Variables used before they are assigned have default values.
*   PHP automatically associates a data type to the variable, depending on its value.
*   PHP does a good job of automatically converting types from one to another when necessary.

**Rules to name a variable**

*   A variable starts with the $ sign, followed by the name of the variable
*   A variable name must start with a letter or the underscore character
*   A variable name cannot start with a number
*   A variable name can only contain alpha-numeric characters and underscores (a-z, A-Z, 0-9, and \_ )
*   A variable name cannot contain characters like +, - , % , ( , ) . & , etc
*   Variable names are **case-sensitive** ($var and $VAR are different)

**Practice:**

You can either use the same php file from the previous section or create a new file if you wish.

Always remember:

*   Open XAMPP - Start Apache Server
*   Save your file with .php extension
*   Code inside the PHP tags <?php ?>

Let us now create / declare variables:

```
/* Variables */

//variable to store string
$var1 = 'Hello';
$var2 = "Hello World";

//variables to store numbers
$x = 5; $y = 10;
$z = $x + $y;

echo "Single quote String - ".$var1;
echo '<br>Double quote String - '.$var2;
echo "<br>Sum of x and y = ".$z;
```

**Execute:**

When you execute the page, you will get the output as:

![2-2-1](Images/image00156.jpeg)

*   You have to use single or double quotes for storing strings / text
*   You can assign expression to a variable to store the result.

**Variable Scope:**

The scope of a variable is the part of the PHP script where the variable can be referenced or used.

PHP has three different variable scopes:

*   local
*   global
*   static

Right now, it will be difficult to understand scope of variables. We will discuss them in detail when we discuss PHP functions.

* * *

### 2.3 Data Types

* * *

Variables can store data of different types and different data types can do different things.

PHP supports the following data types:

*   String
*   Integer
*   Double
*   Boolean
*   NULL
*   Array
*   Object
*   Resource

We will just look at a glance on all the types:

*   **Strings** − are sequences of characters, like 'PHP supports string operations.'
    
*   **Integers** − are whole numbers, without a decimal point, like 4195.
    
*   **Doubles** − are floating-point numbers, like 3.14159 or 3.1.
    
*   **Booleans** − have only two possible values either true or false.
    
*   **NULL** − is a special type that only has one value: NULL.
    
*   **Arrays** − are named and indexed collections of other values.
    
*   **Objects** − are instances of programmer-defined classes, which can pack up values and functions that are specific to the class.
    
*   **Resources** − are special variables that hold references to resources external to PHP (such as database connections).
    

* * *

**Strings:**

A string is a sequence of characters. A string can be any text inside quotes. You can use single or double quotes.

*   Certain character sequences beginning with backslash (\\) are replaced with special characters
*   Variable names (starting with $) are replaced with string representations of their values.

Escape-sequence replacements:

*   \\n is replaced by the newline character
    
*   \\r is replaced by the carriage-return character
    
*   \\t is replaced by the tab character
    
*   \\$ is replaced by the dollar sign itself ($)
    
*   \\" is replaced by a single double-quote (")
    
*   \\\\ is replaced by a single backslash (\\)
    

**Practice:**

```
/*Data Types */
//Strings
$string1 = "Hello, This is a single line string";
$string2 = "<br>This is printed in new first line <br> This is the second line<br>";
$string3 = "";   //Empty String
$string4 = "<br>Using " quotes " inside string";
echo $string1;
echo $string2;
echo $string3;
echo $string4;
```

**Execute:**

![2-3-1](Images/image00157.jpeg)

*   Since $string2 ends with a <br> tag, the cursor comes to the new line
*   $string3 is an empty variable, so, it prints nothing.
*   $string4 starts with <br> tag again. This is the reason for the gap between $string2 and $string4 variables.
*   Try removing and adding <br> tags to see what happens.

**Integers:**

An integer data type is a non-decimal number between -2,147,483,648 and 2,147,483,647.

Rules for integers:

*   An integer must have at least one digit
*   An integer must not have a decimal point
*   An integer can be either positive or negative
*   Integers can be specified in: decimal (base 10), hexadecimal (base 16), octal (base 8), or binary (base 2) notation

**Double:**

A double or float (floating point number) is a number with a decimal point or a number in exponential form.

**Practice:**

```
//Integers
$x = 5691;
$y = -5691;
echo "<br>Sum of Integers = ".($x + $y);
//Floats
$a = 56.940;
$b = -56.910;
echo "<br>Sum of Floats = ".($a + $b);
```

**Execute:**

![2-3-2](Images/image00158.jpeg)

In the coding, if you remove ( ) surrounding the expression, a warning will be triggered.

Let’s take for example: change the echo statement of integer part as:

```
echo "<br>Sum of Integers = ".$x + $y;
```

![2-3-3](Images/image00159.jpeg)

It means, echo statement is correct till $x. So, expression must be surrounded by parenthesis.

Moreover, using the code below, it just prints the values of $x and $y variables instead of calculating them.

```
echo "<br>Sum of Integers = ".$x."+".$y;
```

![2-3-4](Images/image00160.jpeg)

Hope you understand how echo reacts to the usage of quotes.

**Boolean:**

A Boolean represents two possible states: TRUE or FALSE. Booleans are mostly used in conditionals and loops (discussed in the next chapter).

**Null:**

Null is a special data type which can have only one value: NULL. A variable of data type NULL is a variable that has no value assigned to it.

If a variable is created without a value, it is automatically assigned a value of NULL. The variable can also be emptied by setting the value to NULL. It evaluates to FALSE in a Boolean context.

**Practice:**

```
//Boolean
$t = TRUE;
$f = FALSE;
echo "<br>True - ".$t;
echo "<br>False - ".$f;
//Null
$var = NULL;
echo "<br>Printing NULL - ".$var;
$var_new = "Hello";
echo "<br> Testing var_new - ".$var_new;
$var_new = NULL;
echo "<br> Testing var_new - ".$var_new;
```

**Execute:**

FALSE and NULL print nothing.

![2-3-5](Images/image00161.jpeg)

**How can you find a data type based on assignment?**

Let us take a code set as follows:

```
//checking data type
$d1 = 91;
$d2 = 9.1;
$d3 = "hello";
$d4 = TRUE;
$d5 = NULL;
var_dump($d1);
echo "<br>";
var_dump($d2);
echo "<br>";
var_dump($d3);
echo "<br>";
var_dump($d4);
echo "<br>";
var_dump($d5);
```

When you wish to know the data type of a variable, you can use var\_dump() function. 

![2-3-6](Images/image00162.jpeg)

**How to check if a variable is not null?**

We can check whether a variable holds a value or not. If the variable does not hold any value, we call it as NULL.

Let us see the coding below:

```
//check for NULL
$n1 = NULL;
$n2 = 10;
echo "checking n1 = ".isset($n1);
echo "<br>checking n2 = ".isset($n2);
```

![2-3-7](Images/image00163.jpeg)

isset($n1) will return false because $n1 does not hold any value.

isset($n2) will return true (1) because $n2 holds an integer value.

**Object:**

Instantiating an object from a class belongs to object-oriented programming. You can just view an example below

```
/* $myCar is an object */
<?php
class Car {
  public $color;
  public $model;
}
$myCar = new Car();
?>
```

If you execute this, nothing will happen. We are not displaying anything in this code. We have created a class with two properties and created an object from this class.

We will discuss Arrays in another section of this chapter.  
Example of Resource will be discussed in Chapter-4.

* * *

### 2.4 Built-in Functions

* * *

PHP has built-in functions that can be called directly, from within a script, to perform a specific task.

We have built-in functions to work with data types: string, numbers, etc. We will discuss few of many functions in the following categories:

*   Numeric functions
*   Mathematical functions
*   String functions
*   Date/Time functions

PHP provides automatic data type conversion. We will look into this conversion while dealing with examples.

* * *

**Numeric Functions:**

Functions related to integers and floats will be discussed here.

PHP has the following functions to check if the type of a variable is integer:

*   is\_int()
*   is\_integer()
*   is\_long()

PHP has the following functions to check if the type of a variable is float:

*   is\_float()
*   is\_double()

PHP has the following functions to check if a numeric value is finite or infinite. A numeric value that is larger than PHP\_FLOAT\_MAX is considered infinite.

*   is\_finite()
*   is\_infinite()

PHP has function to check if a value is not a number. NaN stands for Not a Number. NaN is used for impossible mathematical operations.

*   is\_nan()

The PHP function uses the following function to find whether a variable is numeric. The function returns true if the variable is a number or a numeric string. It returns false otherwise.

*   is\_numeric()

From PHP 7.0, this function will return FALSE for numeric strings in hexadecimal form (e.g. 0xf4c3b00c), as they are no longer considered as numeric strings.

Sometimes you need to cast a numerical value into another data type. The following functions are often used to convert a value to an integer.

(int), (integer), or intval()

**Practice:**

Though not all, I have tried maximum functions to be included:

```
//Numeric Functions

$x = 56;
$y = 56.7905;
$z = acos(8);
echo "<br>x is an integer? ";
var_dump(is_int($x));
echo "<br>y is an integer? ";
var_dump(is_int($y));
echo "<br>y is a float? ";
var_dump(is_float($y));
echo "<br>z is a ";
var_dump($z);
echo "<br> z is not a number? ";
var_dump(is_nan($z));


$m = 1.9e501;
$n = 1.8e45;
echo "<br> m is finite? ";
var_dump(is_finite($m));
echo "<br> n is finite? ";
var_dump(is_finite($n));
echo "<br> m is infinite? ";
var_dump(is_infinite($m));


$s = "5679";
echo "<br> s is numeric? ";
var_dump(is_numeric($s));
$t = "56.79" + 10;
echo "<br> t is numeric? ";
var_dump(is_numeric($t));
$r = "Hello";
echo "<br> r is numeric? ";
var_dump(is_numeric($r));
```

**Execute:**

Since variable $s is completely a number, PHP automatically casts string to number. Similar automatic casting (conversion) happens in variable $t.

![2-4-1](Images/image00164.jpeg)

Try changing the expression of variable $r as:

```
$r = 10 + "Hello";
```

A warning will be generated for using string (non-numeric) but in the end, $r will be a numeric.

![2-4-2](Images/image00165.jpeg)

PHP tries converting string to number, when it cannot do it, it simply ignores and counts only 10 in the above expression to which is\_numeric() becomes true. On the other hand, a warning will be triggered by PHP to specify that it has encountered a non-numeric value in a numerical expression!

* * *

**Mathematical Functions:**

PHP has a set of math functions that allows you to perform mathematical tasks on numbers. We will discuss few of them here:

*   pi() - to return the value of pi
    
*   min() - to return the lowest of values in the argument list
    
*   max() - to return the highest of values in the argument list
    
*   abs() - to return the absolute (positive) value of a number
    
*   sqrt() - to return the square root of a number
    
*   round() - rounds a floating-point number to its nearest integer
    
*   rand() - generates a random number
    

**Practice:**

We will look into every function!

We will check rounding in 2 ways, to nearest integer. Similarly, we will check generating random number between a minimum and maximum limit!

```
//Mathematical Functions

echo "<br>Value of pi = ".pi();
echo "<br>Highest of 12 25 9 = ".max(12,25,9);
echo "<br>Lowest of 12 25 9 = ".min(12,25,9);
echo "<br>Absolute value of -5.97 = ".abs(-5.97);
echo "<br>Square root of 625 = ".sqrt(625);
echo "<br>Rounding to nearest 7.58 = ".round(7.58);
echo "<br>Rounding to nearest 7.08 = ".round(7.08);
echo "<br>Generate a random number = ".rand();
echo "<br>Generate a random number between 30 and 60 = ".rand(30,60);
```

**Execute:**

Hope every function has displayed the expected result!

![2-4-3](Images/image00166.jpeg)

Test more examples for your understanding!

* * *

**String Functions:**

Before getting into functions, we will first know about the **string concatenation operator** called dot (.). Guess you would have seen this operator in echo statements in the previous examples. The use of concatenation operator is to concatenate or merge two strings!

We will look at some commonly used functions to manipulate strings.

**String Length:**

*   strlen(string) function returns the length of a string.
*   The length of a string is often used in loops or other functions, when it is important to know when the string ends.

**Words Count:**

*   str\_word\_count(string) function counts the number of words in a string.

**String Reverse:**

*   strrev(string) function reverses a string.

**String Search**:

*   strpos(string,search) function is used to search for a specific string or character within a string.
*   If a match is found in the string, this function will return the position of the first match.
*   If no match is found, it will return FALSE.
*   The position starts from 0 and not 1.

**String Replace:**

*   str\_replace(find,replace,string,count) function replaces some characters with some other characters in a string.
*   count (optional parameter) is a variable that counts the number of replacements.

**Practice:**

We will look into all the above functions.

```
//String Functions
$str = "Welcome to PHP";
echo "<br>Example String: ".$str;
echo "<br>Length of string = ".strlen($str);
echo "<br>Number of words in string = ".str_word_count($str);
echo "<br>Reverse of string = ".strrev($str);
echo "<br>Search P position in string = ".strpos($str,"P");
echo "<br>Replace PHP with PHP Course = ".str_replace("PHP","PHP Course",$str);
```

**Execute:**

**![2-4-4](Images/image00167.jpeg)**

Length is inclusive of space characters. That is, space is also counted as a character. P position in Welcome to PHP is 11 by means of starting the string with 0.

* * *

**Date/Time Functions:**

Though there are lots of discuss in this topic, we will learn about working with date/time in PHP.

The date() function is used to format a date and / or a time.

This function formats a timestamp to a more readable date and time. A timestamp is a sequence of characters, denoting the date and/or time at which a certain event occurred.

**Syntax:**

```
date(format,timestamp)
```

There are 2 parameters:

format - It is a required parameter. It specifies the format of the timestamp

timestamp - It is an optional parameter to specify a timestamp. Default is the current date and time

**How to get a date?**

Here are some characters that are commonly used for date:

*   d - Represents the day of the month (01 to 31)
*   m - Represents a month (01 to 12)
*   Y - Represents a year (in four digits)
*   l (lowercase 'L') - Represents the day of the week

Other characters, like "/", ".", or "-" can also be inserted between the characters to add additional formatting.

**How to get a time?**

Here are some characters that are commonly used for time:

*   H - 24-hour format of an hour (00 to 23)
*   h - 12-hour format of an hour with leading zeros (01 to 12)
*   i - Minutes with leading zeros (00 to 59)
*   s - Seconds with leading zeros (00 to 59)
*   a - Lowercase Ante meridiem and Post meridiem (am or pm)

**How to specify your timezone?**

The PHP date() function will return the current date/time of the server! The timezone of the server is UTC.  
Since I am in India, I am going to use the IST timezone!

To specify the timezone, we have to include the line:

```
date_default_timezone_set("Asia/Kolkata");
```

Reference:

View timezones of various countries by choosing your continent from the link below:

[https://www.php.net/manual/en/timezones.php](https://www.php.net/manual/en/timezones.php)

**Practice:**

We will display today’s date in various formats.

```
/* Date/Time Functions */

//Display Date/Time as per Server
echo "<br>Date in dd-mm-yyyy format: ".date("d-m-Y");
echo "<br>Date in dd-mm-yyyy format with day: ".date("l, M d, Y");
echo "<br>Default date format with time: ".date("Y-m-d h:i:s a");
echo "<br>Date with 24-hour format: ".date("d/m/y H:i:s");

//Display Date/Time as per IST timezone
date_default_timezone_set("Asia/Kolkata");
echo "<br>Time as per IST timezone!";
echo "<br>Default date format with time: ".date("Y-m-d h:i:s a");
echo "<br>Date with 24-hour format: ".date("d/m/y H:i:s");
```

**Execute:**

First, we will display date/time in server’s timestamp. Later, we will display in IST to check the difference in time!

![2-4-5](Images/image00168.jpeg)

**How to create a time using the optional parameter?**

We have an optional parameter in the date() function. Using this, we can create a date/time and display it in a specified format. Let us learn to do it:

**Syntax**

```
mktime(hour, minute, second, month, day, year);
```

**Practice:**

```
//Create a date
$createdate = mktime(10,54,06,11,23,2020);
echo "Created date is 23-11-2020 10:54:06 am: ".date("M d, Y H:i:s",$createdate);
```

**Execute:**

**![2-4-6](Images/image00169.jpeg)**

**How to create a date from a string?**

We can create a date from a string using strtotime() function. This function is used to convert a human readable date string into a Unix timestamp (the number of seconds since January 1 1970 00:00:00 GMT)

**Syntax:**

```
strtotime(time, now)
```

**Practice:**

We will see various examples on how to use strtotime() function. It will give you the possibilities on what to do with this function.

```
//Using strtotime() function (Code was executed in the year 2020)
date_default_timezone_set("Asia/Kolkata");
$today = strtotime("now");
echo "<br>Today's date in string: ".$today;
echo "<br>Today's date: ".date("l, M d Y, h:i:s A",$today);
echo "<br>+5 hours from now: ".date("M d Y, h:i:s A",strtotime("+5 hours",$today));
echo "<br>+1 week from now: ".date("M d Y, h:i:s A",strtotime("+1 week",$today));
echo "<br>Next monday from now: ".date("M d Y, h:i:s A",strtotime("next Monday",$today));
```

**Execute:**

We have used strtotime() function to manipulate date related queries. If you don’t use timezone, all timing will be in UTC format. Only when you get your system timezone, you can understand how the function works.

If we do not use the date() function to format the date, strtotime() will not be readable. That is why we have included date formats in every line of code. To show how a string of date/time looks, we have just printed it in string format (the first line of output). When the string is displayed using date(), it is rendered as a readable date.

![2-4-7](Images/image00170.jpeg)

**Note:**

Below is the list of formats a date can take:

*   d - The day of the month (from 01 to 31)
*   D - A textual representation of a day (three letters)
*   j - The day of the month without leading zeros (1 to 31)
*   l (lowercase 'L') - A full textual representation of a day
*   N - The ISO-8601 numeric representation of a day (1 for Monday, 7 for Sunday)
*   S - The English ordinal suffix for the day of the month (2 characters st, nd, rd or th. Works well with j)
*   w - A numeric representation of the day (0 for Sunday, 6 for Saturday)
*   z - The day of the year (from 0 through 365)
*   W - The ISO-8601 week number of year (weeks starting on Monday)
*   F - A full textual representation of a month (January through December)
*   m - A numeric representation of a month (from 01 to 12)
*   M - A short textual representation of a month (three letters)
*   n - A numeric representation of a month, without leading zeros (1 to 12)
*   t - The number of days in the given month
*   L - Whether it's a leap year (1 if it is a leap year, 0 otherwise)
*   W - The ISO-8601 year number
*   Y - A four digit representation of a year
*   y - A two digit representation of a year
*   a - Lowercase am or pm
*   A - Uppercase AM or PM
*   B - Swatch Internet time (000 to 999)
*   g - 12-hour format of an hour (1 to 12)
*   G - 24-hour format of an hour (0 to 23)
*   h - 12-hour format of an hour (01 to 12)
*   H - 24-hour format of an hour (00 to 23)
*   i - Minutes with leading zeros (00 to 59)
*   s - Seconds, with leading zeros (00 to 59)
*   u - Microseconds (added in PHP 5.2.2)
*   e - The timezone identifier (Examples: UTC, GMT, Atlantic/Azores)
*   I (capital i) - Whether the date is in daylights savings time (1 if Daylight Savings Time, 0 otherwise)
*   O - Difference to Greenwich time (GMT) in hours (Example: +0100)
*   P - Difference to Greenwich time (GMT) in hours:minutes (added in PHP 5.1.3)
*   T - Timezone abbreviations (Examples: EST, MDT)
*   Z - Timezone offset in seconds. The offset for timezones west of UTC is negative (-43200 to 50400)
*   c - The ISO-8601 date (e.g. 2013-05-05T16:34:42+00:00)
*   r - The RFC 2822 formatted date (e.g. Fri, 12 Apr 2013 12:01:05 +0200)
*   U - The seconds since the Unix Epoch (January 1 1970 00:00:00 GMT)

The following predefined constants can also be used (available since PHP 5.1.0):

*   DATE\_ATOM - Atom (example: 2013-04-12T15:52:01+00:00)
*   DATE\_COOKIE - HTTP Cookies (example: Friday, 12-Apr-13 15:52:01 UTC)
*   DATE\_ISO8601 - ISO-8601 (example: 2013-04-12T15:52:01+0000)
*   DATE\_RFC822 - RFC 822 (example: Fri, 12 Apr 13 15:52:01 +0000)
*   DATE\_RFC850 - RFC 850 (example: Friday, 12-Apr-13 15:52:01 UTC)
*   DATE\_RFC1036 - RFC 1036 (example: Fri, 12 Apr 13 15:52:01 +0000)
*   DATE\_RFC1123 - RFC 1123 (example: Fri, 12 Apr 2013 15:52:01 +0000)
*   DATE\_RFC2822 - RFC 2822 (Fri, 12 Apr 2013 15:52:01 +0000)
*   DATE\_RFC3339 - Same as DATE\_ATOM (since PHP 5.1.3)
*   DATE\_RSS - RSS (Fri, 12 Aug 2013 15:52:01 +0000)
*   DATE\_W3C - World Wide Web Consortium (example: 2013-04-12T15:52:01+00:00)

With this, we come to an end of this long discussion!

* * *

### 2.5 Arrays

* * *

An array is a variable, which can hold more than one value at a time. An array can hold many values under a single name and you can access the values by referring to an index number.

**Types of arrays:**

In PHP, there are three types of arrays:

*   **Indexed arrays** - Arrays with a numeric index
*   **Associative arrays** - Arrays with a string index (called keys)
*   **Multidimensional arrays** - Arrays containing one or more arrays, accessed by multiple indices

**Example:**

Assume, a student has completed 5 tests with scores.

We create a variable called $scores. To store 5 tests marks, we store them in $scores\[0\], $scores\[1\], $scores\[2\], $scores\[3\] and $scores\[4\].

The number inside the square brackets is called the index. Index usually starts with 0 and proceeds till array-size minus 1. That is, if you have 5 tests, index will be from 0 to 4 counting to 5 on the total.

This is an example for the indexed array.

Assume, there are 10 tests conducted for the student. We are calculating scores of only 5 of the selected tests. We will not be knowing the index number of the test. In these places, we use an array like:

$scores\['test1'\], $scores\['test4'\], $scores\['test5'\], $scores\['test7'\] and $scores\['test10'\]

The count is again 5 test scores. Here, the index is a string. Indices of $scores are test1, test4, test5, test7, test10.

This is an example for the associative array.

Assume, for every test, there are 3 attempts with indices 0,1,2. 0 denotes first attempt, 1 denotes second attempt, 2 denotes third attempt. We have an array like:

$scores\['test1'\]\[0\], $scores\['test1'\]\[1\], $scores\['test1'\],\[2\]

$scores\['test4'\]\[0\], $scores\['test4'\]\[1\], $scores\['test4'\],\[2\]

$scores\['test5'\]\[0\], $scores\['test5'\]\[1\], $scores\['test5'\],\[2\]

$scores\['test7'\]\[0\], $scores\['test7'\]\[1\], $scores\['test7'\],\[2\]

$scores\['test10'\]\[0\], $scores\['test10'\]\[1\], $scores\['test10'\],\[2\]

The count is 5\*3 => 5 tests \* 3 attempts of each test = 15

This is an example for multidimensional array.

The indexes can be numbers or strings. We have used string index for first dimension and numeric index for second dimension. Since we have used only two dimensions, we can also name it as two-dimensional array.

**Syntax:**

The array() function is used to create an array.

**Practice:**

We will now code to create all the three types of array based on the above examples.

We will create three variables $scores1, $scores2, $scores3 to depict the three types.

```
//Arrays

//Declare array to be used later
$scores = array();

//Indexed arrays
$scores1 = array(56, 57, 59, 65, 74);
echo "Printing indexed array: &emsp;";
echo $scores1[0]."&nbsp;";
echo $scores1[1]."&nbsp;";
echo $scores1[2]."&nbsp;";
echo $scores1[3]."&nbsp;";
echo $scores1[4]."&nbsp;";
echo "<br>";

//Associate arrays
$scores2 = array("test1"=>56, "test4"=>57, "test5"=>59);
$scores2['test7'] = 65;
$scores2['test10'] = 74;
echo "Printing associative array: &emsp;";
echo $scores2['test1']."&nbsp;";
echo $scores2['test4']."&nbsp;";
echo $scores2['test5']."&nbsp;";
echo $scores2['test7']."&nbsp;";
echo $scores2['test10']."&nbsp;";
echo "<br>";

//Multidimensional arrays
$scores3 = array("test1" => array(53,54,56), "test4" => array(51,56,57));
$scores3['test5'][0] = 45;
$scores3['test5'][1] = 55;
$scores3['test5'][2] = 59;
$scores3['test7'] = array(61,63,65);
$scores3['test10'] = array(71,72,74);
echo "Printing 2-D array: <br>";
echo "Test 1 - All Attempts =".$scores3['test1'][0]."&emsp;".$scores3['test1'][1]."&emsp;".$scores3['test1'][2];
echo "<br>Test 1 Attempt 1 = ".$scores3['test1'][0];
echo "<br>Test 1 Attempt 3 = ".$scores3['test1'][2];
```

**Execute:**

You can try printing different indices of two dimensional arrays to get a better clarity!

![2-5-1](Images/image00171.jpeg)

You may find it difficult to traverse the array this way. In the next chapter, when we discuss loops, we will again use arrays. There, we will traverse arrays using loops and you will find them far batter.

**Built-in Functions of Arrays:**

We will discuss two built-in functions of array here:

**Length of Array:**

The count() function is used to return the length (the number of elements) of an array.

**Practice:**

```
//Declare arrays
$scores = array();
$scores1 = array(56, 57, 59, 65, 74);
$scores2 = array("test1" => 56, "test4" => 57, "test5" => 59, "test7" => 65, "test10" => 74);
$scores3 = array("test1" => array(53,54,56), "test4" => array(51,56,57), "test5" => array(45,55,59), "test7" => array(61,63,65), "test10" => array(71,72,74));

//Array Length/Size
echo "<br>Size of $scores = ".count($scores);
echo "<br>Size of $scores1 = ".count($scores1);
echo "<br>Size of $scores2 = ".count($scores2);
echo "<br>Size of $scores3 = ".count($scores3);
echo "<br> Size of $scores3 test1's attempts - ".count($scores3['test1']);
```

**Execute:**

We have declared all arrays in a single place from the above example set. We execute count function on all the 4 arrays.

*   Empty array $scores returns 0.
*   $scores1, $scores2, $scores3 return 5.
*   In $scores3, the array's first dimension size is alone counted. To get the second dimension index count, we need to specify the first dimension index in the count function.

![2-5-2](Images/image00172.jpeg)

**Sorting Arrays:**

The elements in an array can be sorted in alphabetical or numerical order, descending or ascending.

In PHP, we have the following the sort functions:

*   sort() - sort arrays in ascending order
*   rsort() - sort arrays in descending order
*   asort() - sort associative arrays in ascending order, according to the value
*   ksort()- sort associative arrays in ascending order, according to the key
*   arsort() - sort associative arrays in descending order, according to the value
*   krsort() - sort associative arrays in descending order, according to the key

**Practice:**

We already have all our values in ascending order, all we can try here is descending!

```
//Declare arrays
$scores = array();
$scores1 = array(56, 57, 59, 65, 74);
$scores2 = array("test1"=>56, "test4"=>57, "test5"=>59, "test7" => 65, "test10" => 74);

//Sorting indexed arrays
echo "<br>Printing $scores1 - ".$scores1[0]."&nbsp;".$scores1[1]."&nbsp;".$scores1[2]."&nbsp;".$scores1[3]."&nbsp;".$scores1[4];
rsort($scores1);
echo "<br>Printing after sorting $scores1 - ".$scores1[0]."&nbsp;".$scores1[1]."&nbsp;".$scores1[2]."&nbsp;".$scores1[3]."&nbsp;".$scores1[4];

echo "<br><br>Printing $scores2 <br>";
var_dump($scores2);

//Sorting associative arrays by values
arsort($scores2);
echo "<br><br>Printing $scores2 after sorting by values: <br>";
var_dump($scores2);

//Sorting associative arrays by keys
krsort($scores2);
echo "<br><br>Printing $scores2 after sorting by keys: <br>";
var_dump($scores2);
```

**Execute:**

We use var\_dump() function to get the values of sorted arrays,

In sorting $scores2,

*   the array is sorted in descending order of the values when using arsort() function.
*   the array in sorted in descending order of the keys when using krsort() function.

![2-5-3](Images/image00173.jpeg)

With this, the discussion on arrays comes to an end!

* * *

### 2.6 User-defined Functions - I

* * *

Besides the built-in PHP functions, it is possible to create your own functions.

*   A function is a block of statements that can be used repeatedly in a program.
*   A function will not execute automatically when a page loads.
*   A function will be executed by a call to the function.

**How to create a (user-defined) function?**

A user-defined function is declared using the word function.

**Syntax**

```
function function_name(){
   code to be executed;
}
```

A function name must start with a letter or an underscore. Function names are NOT case-sensitive. Always choose a name that reflects what the function does! The name should serve the purpose!

**Function Arguments:**

Information can be passed to functions through arguments. An argument is just like a variable.

Arguments are specified after the function name, inside the parentheses. You can add as many arguments as you want, just separate them with a comma.

**Practice:**

We will look over two functions now:

```
//User Defined functions

function print_message(){
 echo "<p>Message printed from the function</p>";
}

function print_message_string($str){
 echo $str;
}

print_message();
print_message_string("Printing from arguments");
```

**Execute:**

We have printed two statements. First statement is printed by print\_message() function. Second statement is passed as an argument to the print\_message\_string($string) function.

![2-6-1](Images/image00174.jpeg)

In the example set above, we do not have to tell PHP which data type the variable is. PHP automatically associates a data type to the variable, depending on its value. Since the data types are not set in a strict sense, you can do things like adding a string to an integer without causing an error.

**Type declarations:**

In PHP 7, type declarations were added. This gives us an option to specify the expected data type when declaring a function, and by adding the strict declaration, it will throw a "Fatal Error" if the data type mismatches.

To specify strict, we need to set:

```
declare(strict_types=1);
```

It must be specified on the very first line of the file.

Try this code snippet now:

```
declare(strict_types=1);
function print_message_string(int $str){
 echo $str;
}
print_message_string("Hello");
```

You will be thrown fatal error as below:

![26-2](Images/image00175.jpeg)

Try replacing the function call as:

```
print_message_string(10);
```

The output will print 10.

Hope you can understand restricting the data type of argument!

Arguments and Parameters mean the same.

**Where should we use the term parameter and argument?** 

*   Parameters: function definition
*   Arguments: function call

**Default value of parameter:**

You can also specify the default value of a parameter.

When no arguments are passed through the function, the default value is taken up. If argument is passed, passed value will be used.

Let us see the working below:

```
declare(strict_types=1);
function print_message_string(int $str = 10){
 echo "<br>".$str;
}
print_message_string();
print_message_string(50);
```

![2-6-3](Images/image00176.jpeg)

When no arguments are passed, 10 is printed. When 50 is passed, 50 gets printed.

**Returning Values:**

A function can also return a value at the end of its execution. We need to use the return statement.

PHP 7 also supports Type Declarations for the **return** statement. Similar to the type declaration for function arguments, by enabling the strict requirement, it will throw a "Fatal Error" on a type mismatch.

To declare a type for the function return, add a colon ( : ) and the type right before the opening curly ( { )bracket when declaring the function.

We will look at an example set!

```
declare(strict_types=1);
function sum_number(float $a, float $b){
 return ($a + $b);
}
function sum_number2(float $a, float $b) : float{
 return ($a + $b);
}
function sum_number3(float $a, float $b) : int{
 return ($a + $b);
}
echo "<br> Return value = ".sum_number(5,10);
echo "<br> Return strict value = ".sum_number2(5,10);
```

We will perform calls only to two functions:

![2-6-4](Images/image00177.jpeg)

Now, call the third function:

```
echo sum_number3(5,10);
```

![2-6-5](Images/image00178.jpeg)

A fatal error will be thrown because adding two floats should result in a float, not an integer. No matter, how you pass your parameters, return type must match!

**Passing Arguments by Reference:**

In PHP, arguments are usually passed by value, which means that a copy of the value is used in the function and the variable that was passed into the function cannot be changed.

When a function argument is passed by reference, changes to the argument would also change the value of the variable that was passed in. To turn a function argument into a reference, the & operator is used.

Let us see the difference through an example:

```
function sum_number($a, $b){
 $a = $a + $b;
 return $a;
}
function sum_number_ref(&$a, $b){
 $a = $a + $b;
 return $a;
}

$a = 5;
$b = 10;
echo "<br>Passing by Value: <br>";
echo "<br>Before Sum: $a = ".$a." $b = ".$b. " Sum = ".sum_number($a,$b);
echo "<br> After Sum:  $a = ".$a." $b = ".$b;
echo "<br><br>Passing by Reference: <br>";
echo "<br>Before Sum: $a = ".$a." $b = ".$b. " Sum = ".sum_number_ref($a,$b);
echo "<br> After Sum:  $a = ".$a." $b = ".$b;
```

![2-6-6](Images/image00179.jpeg)

In the second function sum\_number\_ref(), the argument $a is passed by reference, denoted by &$a. It means, once the $a gets updated, it retains the value even after it comes out of the function.  
Whereas, when the parameter is passed just as value, as in function sum\_number(), whatever calculations happen, it belongs and stays only inside the function!

* * *

### 2.7 User-defined Functions - II

* * *

This will be the right context to discuss about variable scopes. Let me remind you the scopes:

**Global** - A variable declared outside a function has a GLOBAL SCOPE and can only be accessed outside a function.

**Local** - A variable declared within a function has a LOCAL SCOPE and can only be accessed within that function.

**Static** - A local variable that is not deleted even after the execution of the function.

Let us see an example!

Consider the coding segment:

```
$x = 10;
function print_x(){
 echo "<br>Printing from function - ".$x;
}
print_x();
echo "<br>Printing outside function - ".$x;
```

Here, variable $x is defined globally. So, it is accessible outside the function.

![2-7-1](Images/image00180.jpeg)

**Global**

The global keyword is used to access a global variable from within a function.

PHP also stores all global variables in an array called $GLOBALS\[index\]. The index holds the name of the variable. This array is also accessible from within functions and can be used to update global variables directly.

**Local**

You can have local variables with the same name in different functions, because local variables are only recognized by the function in which they are declared.

**Static**

Normally, when a function is completed/executed, all of its variables are deleted. However, sometimes we want a local variable NOT to be deleted. We need it for a further job.

Then, each time the function is called, that variable will still have the information it contained from the last time the function was called. But the variable is still local to the function.

Now, we will look onto an example with all the three scopes!

**Practice:**

```
//Scopes of variables - global, local, static
$x = 5;
$y = 10;

function add_num(){
  global $x, $y;
  $z = $x + $y;
  return $z;
}

function add_static(){
  static $m;
  $m = $m + ($GLOBALS['x'] + $GLOBALS['y']);
  return $m;
}

echo "<br> Sum using global x,y = ".add_num();
echo "<br> Sum using global index = ".add_nums();
echo "<br> Accessing local variable z: ".$z;
echo "<br> Addition 1 - ".add_static();
echo "<br> Addition 2 - ".add_static();
echo "<br> Addition 3 - ".add_static();
```

**Execute:**

We have tried accessing global variables using global keyword and $GLOBALS\[index\]. At the same time, when the local variable $z is accessed outside the function, a notice is issued by PHP.

If we consider static variable $m, the value of $m is retained and then added again when the function in called. We have called the function thrice!

*   Initial call will set $m = 0 and assigns 15.
*   Second call will hold the previous value 15 and add it to $m (which holds 15) making it to 30.
*   Third call will add 15 to $m which is already 30 making it to 45.

Let me work it out:

First Call:

$m = 0;

$m = 0 + (5+10) = 15

Second Call:

$m = 15;

$m = 15 + (5 + 10) = 30

Third Call:

$m = 30;

$m = 30 + (5 + 10) = 45;

![2-7-2](Images/image00181.jpeg)

**Callback Functions:**

A callback function is a function which is passed as an argument into another function.

Any existing function can be used as a callback function. To use a function as a callback function, pass a string containing the name of the function as the argument of another function.

Starting with version 7, PHP can pass anonymous functions as callback functions. Anonymous functions are functions that are not previously declared or defined!

Consider the coding segment:

```
//Callbacks
function get_size($str){
 return strlen($str);
}
$str_array = ["PHP","Server-side","Scripting"];
$str_size = array_map("get_size",$str_array);
print_r($str_size);

//anonymous function
$str_size2 = array_map(function($str) { return strlen($str); },$str_array);
echo "<p>Using anonymous function</p>";
print_r($str_size);
```

The functions' purpose are the same, but the way of using them has been illustrated.

![](Images/image00182.jpeg)

**How to use callbacks in user-defined functions?**

User-defined functions and methods can also take callback functions as arguments. To use callback functions inside a user-defined function or method, call it by adding parentheses to the variable and pass arguments as normal functions.

Let us understand this using an example!

```
//Callbacks

function purpose($str){
 return $str."is used to design web pages!<br>";
}
function explain($str){
 return $str."is a server-side scripting language!<br>";
}
function what_is_php($str,$callfunction){
 echo $callfunction($str);
}

what_is_php("PHP ", "explain");
what_is_php("PHP ","purpose");
```

Let me explain the example first!

We have defined two functions - purpose and explain to display some messages. We have defined the third function what\_is\_php to send any of the above 2 functions as its parameter.

purpose($str) => $str is the parameter

explain($str) => $str is the parameter

what\_is\_php($str,$callfunction) => $str is the parameter to pass to the function, $callfunction is the name of the function to which the parameter is passed!

Have a look at the output!

![](Images/image00183.jpeg)

PHP is the parameter supplied to the functions explain and purpose via $str variable! Also remember, first two functions just return the string, while the third function is the function which actually has the echo statement to print the string returned from those functions.

* * *

We have something to discuss! Usually functions need not be placed in the same PHP file. They can be written in a different php file and included in the page you actually wanted to use!

Getting my point? Functions can be defined separately and included where/whenever required!

We will now discuss two statements for this purpose!

**Include / Require:**

The **include** or **require** statement takes all the text/code/markup that exists in the specified file and copies it into the file that uses the include statement.

Including files is very useful when you want to include the same PHP, HTML, or text on multiple pages of a website.

It is possible to insert the content of one PHP file into another PHP file (before the server executes it), with the **include** or **require** statement.

These 2 statements are identical, except upon failure:

*   **require** will produce a fatal error (E\_COMPILE\_ERROR) and will stop the script
*   **include** will only produce a warning (E\_WARNING) and the script will continue

So, if you want the execution to go on and show users the output, even if the included file is missing, use the include statement. Always use the require statement to include a key file to the flow of execution. This will help avoid compromising your application's security and integrity, just in-case one key file is accidentally missing.

**Syntax:**

```
include 'filename';
or
require 'filename';
```

**Practice:**

Create 2 php files now: file1.php and file2.php

Content of file1.php:

```
<?php
function print_name($name){
 echo "Name of the course: ".$name;
}
?>
```

Content of file2.php:

```
<?php
echo "Try accessing function ";
print_name("PHP Scripting");
?>
```

**Execute:**

Try executing file2.php:

A fatal error states that the function name is undefined

![2-7-5](Images/image00184.jpeg)

**Modify the code: file2.php**

Make sure both file1.php and file2.php are in the same location! Save file2.php once again!

```
<?php
include('file1.php');
echo "<br>Try accessing function after include";
print_name("PHP Scripting");
?>
```

Try executing file2.php:

![2-7-6](Images/image00185.jpeg)

You can also try executing using the require statement.

**Tip:**

*   Use require when the file is required by the application.
*   Use include when the file is not required and the application should continue even when the file is not found.

When developing an application, you can place all user-defined functions in a php file and use it in pages whichever needs any of the functions to be called.

* * *

### 2.8 Constants

* * *

A constant is an identifier (name) for a simple value. The value cannot be changed during the script.

*   By default, a constant is case-sensitive.
*   By convention, constant identifiers are always uppercase.
*   A constant name starts with a letter or underscore, followed by any number of letters, numbers, or underscores.
*   If you have defined a constant, it can never be changed or undefined.
*   Unlike variables, constants are automatically global across the entire script.
*   Constants can contain only scalar data (boolean, integer, float and string).

**Differences between constants and variables:**

*   There is no need to write a dollar sign ($) before a constant, where as in variable, one has to write a dollar sign.
*   Constants cannot be defined by simple assignment, they may only be defined using the define() function.
*   Constants may be defined and accessed anywhere without regard to variable scoping rules.
*   Once the constants have been set, they may not be redefined or undefined.

**Syntax**

To create a constant, use the define() function.

```
define(name, value, case-insensitive);
```

Parameters:

*   name: Specifies the name of the constant
*   value: Specifies the value of the constant
*   case-insensitive: Specifies whether the constant name should be case-insensitive. Default is false

**Practice:**

Now, get back your section2.php where you have been coding! Keep file1.php and file2.php closed!

```
//Constants
define("PHPMARK",75);
define("SQLMARK",70,true);
define("courses",["PHP","SQL"]);
echo "<br>PHP Mark - ".PHPMARK;
echo "<br>SQL Mark - ".SQLMARK;
echo "<br>SQL Mark (case insensitive is true) - ".sqlmark;
echo "<br>PHP Mark (case insensitive is false) - ".phpmark;
echo "<br>Current Course - ".courses[0];
```

**Execute:**

The output includes the warning triggered by the phpmark usage.  
Actually while creating SQLMARK we used the third parameter as true which means that constant can be mentioned in uppercase or lowercase since case-insensitive is set to true!  
But, PHPMARK 's third parameter is set to false by default!

![2-7-9](Images/image00186.jpeg)

**PHP Magic constants:**

PHP provides a large number of predefined constants to any script which it runs.

There are five magical constants that change, depending on where they are used. For example, the value of \_\_LINE\_\_ depends on the line that it is used on, in your script. These special constants are case-insensitive and are as follows:

![2-8](Images/image00187.jpeg)

We will use 2 constants for example to see what they do:

```
//Magic Constants
 echo "<p>Example for __FILE__</p>";    
 //print full path of file with .php extension    
 echo __FILE__ ; 
 echo "<p>Example for __LINE__</p>";    
 //print full path of file with .php extension    
 echo "You are at Line number: ".__LINE__;  
```

![2-7-10](Images/image00188.jpeg)

My line number is 374 because I have commented all the codes and kept this snippet in the end!

**Just remember**: Constants are like variables except that once they are defined they cannot be changed or undefined.

* * *

# Chapter 3: Conditionals and Loops

* * *

*   [](#part0019.xhtml)
    
    #### 3.1 Operators
    
*   [](#part0020.xhtml)
    
    #### 3.2 Conditional Statements
    
*   [](#part0021.xhtml)
    
    #### 3.3 Loops
    
*   [](#part0022.xhtml)
    
    #### 3.4 Regular Expressions
    
*   [](#part0023.xhtml)
    
    #### 3.5 Exceptions
    

* * *

### 3.1 Operators

* * *

Operators are used to perform operations on variables and values.

PHP has the following classification:

*   Arithmetic operators
*   Assignment operators
*   Comparison operators
*   Increment/Decrement operators
*   Logical operators
*   String operators
*   Array operators
*   Conditional assignment operators

We will need to know about operators so that we can use them in conditional and loop statements!

**Arithmetic Operators:**

The arithmetic operators are used with numeric values to perform common arithmetical operations.

![3-1-arithmetic](Images/image00189.jpeg)

**Assignment Operators:**

The assignment operators are used with numeric values to write a value to a variable. The basic assignment operator in PHP is =. It means that the left operand is assigned the value of the assignment expression on the right.

![3-1-assignment](Images/image00190.jpeg)

**Comparison Operators:**

The comparison operators are used to compare two values (number or string).

![3-1-comparison](Images/image00191.jpeg)

**Increment / Decrement Operators:**

The increment operators are used to increment a variable’s value while the decrement operators are used to decrement a variable’s value. The placement of operator before/after the variable decides whether it returns the incremented / decremented value or returns the value first and then increments / decrements the value.

![3-1-increment-decrement](Images/image00192.jpeg)

**Practice:**

We will practise these operators now! Hope you have opened a new file section3.php

```
//Operators
$x = 10;
$y = 20;
echo "<br>Values of $x = ".$x." and $y = ".$y;

echo "<br>Arithmetic Operators ";
echo "<br>Addition: $x + $y = ".($x + $y);
echo "<br>Division: $y / $x = ".($y / $x);
echo "<br>Modulus: $y % $x = ".($y % $x);

echo "<br><br>Assignment Operators ";
$x += $y;
echo "Value of $x after $x += $y = ".$x;

echo "<br><br>Comparison Operators ";
echo "<br>Values of $x = ".$x." and $y = ".$y;
echo "<br> $x is greater than $y? ".($x > $y);
echo "<br> Spaceship operator: $x<=>$y ".($x <=> $y);
$z1 = 55;
$z2 = "55";
echo "<br> $z1 is integer 55 and $z2 is string 55";
echo "<br> Checking $z1 == $z2 Answer: ".($z1 == $z2);
echo "<br> Checking $z1 === $z2 Answer: ".($z1 === $z2);

echo "<br><br>Increment/Decrement Operators";
echo "<br> $x Value: ".$x;
echo "<br>Pre-increment ++$x = ".++$x;
echo "<br>Post-increment $x++ = ".$x++;
echo "<br> $x after post-increment: ".$x;
```

**Execute:**

The post increment operator returns the value of the variable $x and then increments it by one. That is why $x value stays as 31 and then the subsequent statement prints $x as 32.

![3-1-1](Images/image00193.jpeg)

**Logical Operators:**

The logical operators are used to combine conditional statements.

![3-1-logical](Images/image00194.jpeg)

**String Operators:**

There are 2 operators for strings specially. We have seen one of them in echo statements.

![3-1-string](Images/image00195.jpeg)

**Array Operators:**

They are used to compare arrays. Some operators are similar to comparison operators.

![3-1-array](Images/image00196.jpeg)

**Conditional Assignment Operators:**

They are used to set a value depending on conditions.

![3-1-conditional](Images/image00197.jpeg)

**Practice:**

We will practise the next set of operators. The real use of operators can be found in the upcoming sections of this chapter.

```
//Operators:
$x = 5;
$y = 10;
echo "<br>Values of $x = ".$x." and $y = ".$y;

echo "<br>Logical Operators ";
$z1 = $x > $y;
$z2 = $x < $y;
echo "<br> Either of z1 or z2 is true - ".($z1 or $z2);

$test = ($x > $y) ? '$x is greater' : '$y is greater';
echo "<br><br>Ternary Operator: ".$test;

echo "<br><br>String Operators ";
$str1 = "Hello";
$str2 = "World";
echo "<br> str1 - ".$str1." str2 = ".$str2;
echo "<br> Concatenation = ".$str1." ".$str2;
$str1 .= $str2;
echo "<br> Concatenation assigned to str1 - ".$str1;

$a = array(10,12,15);
$b = array(15,10,12);
echo "<br><br>Array Operators:";
echo "<br>Checking $a == $b - ".($a == $b);
```

**Execute:**

The array operator will return false because arrays $a and $b do not have the same indices but only values!

That is, a\[0\] = 10, a\[1\] = 12, a\[2\] = 15 and b\[0\] = 15, b\[1\] = 10, b\[2\] = 12.

It means, a\[0\] != b\[0\], a\[1\] != b\[1\], a\[2\] != b\[2\]

![3-1-2](Images/image00198.jpeg)

I think you have got some clarity on operators. The next section is for conditional statements. We will use operators in those statements!

* * *

### 3.2 Conditional Statements

* * *

Sometimes, you would like to execute a set of code (code block) only when it satisfies a condition. You can use conditional statements in your code for this purpose.

**Conditional statements are used to perform actions based on the specified conditions.**

In PHP we have the following conditional statements:

*   if statement
*   if...else statement
*   if...elseif...else statement
*   switch statement

We will look into the syntax of these statements and then go into practice session.

**if Statement**

It executes a code block if a condition is true.

**Syntax**

```
if (condition) {
  code to be executed if condition is true;
}
```

**if...else Statement**

It executes one code block if a condition is true or another code block if that condition is false.

**Syntax**

```
if (condition) {
  code to be executed if condition is true;
} else {
  code to be executed if condition is false;
}
```

**if...elseif...else Statement**

It executes different code blocks for each of the specified conditions.

**Syntax**

```
if (condition) {
  code to be executed if this condition is true;
} elseif (condition) {
  code to be executed if first condition is false and this condition is true;
} else {
  code to be executed if all conditions are false;
}
```

**Practice:**

Conditions are nothing but expressions.

```
//Conditionals
$x = 10;
$y = 15;
$z = 5;
if($x > $y){
 echo "x is greater than y";
 }
 elseif ($x > $z) {
  echo "x is greater than z";
 }
 else {
  echo "x is the least value";
}  
```

**Execute:**

In the above example code segment, x is not greater than y, so we check the elseif condition, which turns to be true. And so, the statement inside the elseif block gets executed.

Try executing the same code with different values of x, so that you can clearly understand how a condition is satisfied and how the associated block of code gets executed.

![3-2-1](Images/image00199.jpeg)

**switch Statement**

We use the switch statement to **select one of many blocks of code to be executed**. In fact, it actually resembles the execution of if…elseif…else statement except that instead of condition, we check with the result of the expression.

**Syntax**

```
switch (n) {
  case label1:
    code to be executed if n=label1;
    break;
  case label2:
    code to be executed if n=label2;
    break;
  case label3:
    code to be executed if n=label3;
    break;
    ...
  default:
    code to be executed if n is different from all labels;
}
```

Let me explain you the working:

*   We have a single expression *n* (most often a variable), that is evaluated once.
*   The value of the expression is then compared with the values for each case in the structure.
*   If there is a match, the block of code associated with that case is executed.
*   Use break to prevent the code from running into the next case automatically.
*   If you miss the break statement, the cases following the match will be executed.
*   The default statement is used if no match is found.

**Practice:**

```
$n = 80;
switch($n){
  case $n > 90: echo "Distinction"; break;
  case $n > 80: echo "First Class"; break;
  case $n > 70: echo "Second Class"; break;
  case $n < 40: echo "Not completed";break;
  default: echo "Completed Course";
}
```

**Execute:**

We will execute the code as it is!

![3-2-2](Images/image00200.jpeg)

Remove the break statement as below and execute:

```
case $n > 70: echo "Second Class";
```

![3-2-3](Images/image00201.jpeg)

Can you understand the need for break statement? If you don’t specify, the cases following the matched case keeps executing. What happens when no cases are matched? The default case gets executed!

Try changing value of n = 50 because cases exist for n > 70 and n < 40.

```
n = 50;
```

![3-2-4](Images/image00202.jpeg)

Hope you are clear with conditional statements. We also call them as branching statements since the conditions are like branches. When a condition is satisfied, that associated branch of code is alone executed.

* * *

### 3.3 Loop Statements

* * *

Sometimes you want the same block of code to run a certain number of times. You can make use of loops instead of repeating the code lines multiple times.

**Loops are used to execute the same block of code again and again, as long as a certain condition is true.**

In PHP, we have the following loop types:

*   while
*   do...while
*   for
*   foreach

We will look the syntax of each loop and practise the same.

**while Loop**

The while loop executes a block of code as long as the specified condition is true.

**Syntax**

```
while (condition is true) {
  code to be executed;
}
```

Once the condition in the while is evaluated to true, the code between the braces gets executed. If the condition evaluates to false, the code block does not get executed.

**Practice:**

We will find the sum of 5 test marks!

*   Marks of 5 tests are stored in $marks array.
*   The size of the array is stored in variable $n.
*   For counting number of tests we use the variable $i.
*   We will also initialize a variable $sum to calculate the sum of the marks of 5 tests.

```
//while loop
$i = 0;
$marks = array(50,70,74,83,65);
$n = count($marks);
$sum = 0;
echo "Marks: ";
var_dump($marks);
while($i < $n){
 $sum = $sum + $marks[$i];
 echo "<br> Value of i = ".$i;
 echo " marks[$i] = ".$marks[$i];
 echo " Sum = ".$sum;
 $i++;
}
```

**Execute:**

What does the code do?

*   We declare an array $marks\[\]
*   We initialize loop count variable $i = 0, array size variable $n = count($marks), sum variable $sum = 0
*   While loop tests the condition $i < $n 
    *   We print value of $i, $marks\[$i\] and $sum
    *   Increment $i by 1 for every iteration.
    *   The loop executes till $i < $n. Once $i = $n, the loop stops executing.

Here is the output:

![3-3-1](Images/image00203.jpeg)

**do...while Loop**

The do...while loop will always execute the block of code once, it will then check the condition and repeat the loop while the specified condition is true. Here, the condition is tested AFTER executing the statements within the loop. This means that the loop will execute its statements at least once, even when the condition is false.

**Syntax**

```
do {	
  code to be executed;
} while (condition is true);
```

**Practice:**

We will now rewrite the same code segment using this loop:

```
//do while loop
$i = 0;
$marks = array(50,70,74,83,65);
$n = count($marks);
$sum = 0;
echo "Marks: ";
var_dump($marks);
do{
 $sum = $sum + $marks[$i];
 echo "<br> Value of i = ".$i;
 echo " marks[$i] = ".$marks[$i];
 echo " Sum = ".$sum;
 $i++;
}while($i < $n);
```

You will get the same output as while loop on executing the above code. The reason why we rewrite the same code is to tell you how the execution happens and where the condition is checked!

**for Loop**

The for loop is used when you know in advance how many times the script should run. It also works as the other 2 loops but how we specify the increment counter and where we check the condition matter!

**Syntax**

```
for (initialize; check condition; increment/decrement) {
  code to be executed for each iteration;
}
```

Parameters:

*   Initialize the loop counter value
*   Check condition to be evaluated for each loop iteration. If it evaluates to TRUE, the loop continues. If it evaluates to FALSE, the loop ends.
*   Increment or decrement the loop counter value

**Practice:**

Not to bore you, but to tell you how this loop works, we again go with same example!

```
//for loop
$marks = array(50,70,74,83,65);
$n = count($marks);
$sum = 0;
echo "Marks: ";
var_dump($marks);
for($i = 0; $i < $n; $i++){
 $sum = $sum + $marks[$i];
 echo "<br> Value of i = ".$i;
 echo " marks[$i] = ".$marks[$i];
 echo " Sum = ".$sum;
}
```

There is a small difference noted! Instead of incrementing the variable $i inside the loop's code block, we increment it along with initialization and testing condition. Execute the same and you will find the same output again!

**foreach Loop**

The foreach loop works only on arrays, and is used to loop through each key/value pair in an array.

**Syntax**

```
foreach ($array as $value) {
  code to be executed;
}
```

For every loop iteration, the value of the current array element is assigned to $value and the array pointer is moved by one, until it reaches the last array element.

**Practice:**

Again, we will take the same example coding. This time, instead of using counting variable $i, we will loop using the key/value pair. Check the coding below:

```
//for each loop
$marks = array(50,70,74,83,65);
$sum = 0;
$i = 0;
echo "Marks: ";
var_dump($marks);
foreach($marks as $mark){
 $sum = $sum + $mark;
 echo "<br> Value of i = ".$i++;
 echo " marks[$i] = ".$mark;
 echo " Sum = ".$sum;
}
```

When you execute, you will have the same output. But, can you see how it is easy to traverse the array?

You don’t need a counter, you need not increment / decrement values, you just pass every array element of $marks array as a single value named $mark! The purpose of using $i here, in the above code, is to depict how $mark variable gets the value one by one from $marks array! We don’t need a counter variable at all when we use foreach loop!

This is the reason, why I tried using an array since the starting of loops. To know how different loops work, we need to use the same example! Learning by executing same example code for different loops will give you better clarity on how each loop works and their requirements too!

We will now look at two statements to be used inside loops: **break** and **continue**

I am going to pick the same example again for these statements too!

**Break**

You have already seen the break statement which was used to exit from a switch statement. In the same way, we can use the break statement to jump out of a loop.

**Practice:**

We have the $marks array. We will find the first mark which is higher than 80. Once we find, we will exit the loop. Ok?

```
//break
$marks = array(50,70,74,83,65);
$sum = 0;
echo "Marks: ";
var_dump($marks);
foreach($marks as $mark){
 if($mark > 80) break;
 echo "<br> Mark Value: ".$mark;
 $sum = $sum + $mark; 
 echo " Sum = ".$sum;
}
```

**Execute:**

When you try executing this code block above, the marks will be summed up till 74. Once $mark > 80, break statement will exit the loop.

![3-3-3](Images/image00204.jpeg)

If you place the break statement in the end of code block inside the loop, 83 will also be summed up leaving out 65.

**Continue**

The continue statement breaks one iteration (in the loop), if a specified condition occurs and continues with the next iteration in the loop.

**Practice:**

We have the $marks array with values: 50,70,74,83,65. We will find sum of values above 60. To exclude 50, we will use continue statement.

```
//continue
$marks = array(50,70,74,83,65);
$sum = 0;
echo "Marks: ";
var_dump($marks);
foreach($marks as $mark){
 if($mark < 60) continue;
 echo "<br> Mark Value: ".$mark;
 $sum = $sum + $mark; 
 echo " Sum = ".$sum;
}
```

**Execute:**

When $mark < 60, we have mentioned continue, which means the loop should go with next iteration.

![3-3-2](Images/image00205.jpeg)

Now can you understand the difference between break and continue?

The continue statement continues with the loop iteration leaving out the current iteration while break statement exits the loop once for all!

* * *

### 3.4 Regular Expressions

* * *

A regular expression is a sequence of characters that forms a search pattern. A regular expression can be a single character, or a more complicated pattern. Regular expressions can be used to perform all types of text search and text replace operations.

In PHP, regular expressions are strings composed of:

*   delimiters,
*   a pattern and
*   optional modifiers.

**Delimiters:**

A delimiter can be any character that is not a letter, number, backslash or space. The most common delimiter is the forward slash (/), but when your pattern contains forward slashes it is convenient to choose other delimiters such as # or ~.

**Patterns:**

A pattern or search pattern is a sequence of characters that we use for search. Brackets are used to find a range of characters:

![3-4-1-pattern](Images/image00206.jpeg)

**Note:**

If your expression needs to search for one of the special characters you can use a backslash (\\) to escape them.

**Modifiers:**

Modifiers can change how a search is performed.

![3-4-2-modifier](Images/image00207.jpeg)

We can also mention some meta characters and quantifiers in a regular expression.

**Metacharacters**

Metacharacters are characters with a special meaning. They can be included in search patterns.

![3-4-3-metacharacter](Images/image00208.jpeg)

**Quantifiers**

Quantifiers define quantities. This tells the occurrences of a search character or search pattern.

![3-4-4-quantifier](Images/image00209.jpeg)

**Grouping**

You can use parentheses ( ) to apply quantifiers to entire patterns. They can also be used to select parts of the pattern to be used as a match.

Where and how are we going to use these regular expressions? We have functions for that purpose. We will use these expressions in those functions. We will apply modifiers, quantifiers in an expression and use the same as a function parameter.

Let me directly show you some functions and then we will go to practice session.

**Regular Expression Functions**

PHP provides a variety of functions that allow you to use regular expressions.

![3-4-5-function](Images/image00210.jpeg)

**Practice:**

We will look at some of the most commonly used functions here. We will use delimiters, modifiers, quantifiers in these examples!

```
//Regular expression
$str_array = array("Hello World","New World","Welcome to New Course", "This is a new course","Hello is the first word tested");

//case sensitive search
$pattern1 = "/New/";
echo "<br>Case sensitive Search Pattern: ".$pattern1;
foreach ($str_array as $str){
  echo "<br>String: ".$str." | Search result - ".preg_match($pattern1,$str);
}

//case insensitive search
$pattern2 = "/New/i";
echo "<br><br>Case insensitive Search Pattern: ".$pattern2;
foreach ($str_array as $str){
  echo "<br>String: ".$str." | Search result - ".preg_match($pattern2,$str);
}

$pattern3 = "/is/i";
echo "<br><br>Case insensitive Search all pattern: ".$pattern3;
foreach ($str_array as $str){
  echo "<br>String: ".$str." | Search result - ".preg_match_all($pattern3,$str);
}

$pattern4 = "/world/i";
echo "<br><br>Case insensitive Replace pattern: ".$pattern4;
foreach ($str_array as $str){
  echo "<br>String: ".$str." | Search result - ".preg_replace($pattern4,'universe',$str);
}

//using quantifiers
$pattern5 = "/(l){2}/";
echo "<br><br>Case sensitive Search all pattern: ".$pattern5;
foreach ($str_array as $str){
  echo "<br>String: ".$str." | Search result - ".preg_match($pattern5,$str);
}
```

We have used 5 patterns in this example code snippet

*   `$pattern1 = "/New/";`
*   `$pattern2 = "/New/i";`
*   `$pattern3 = "/is/i";`
*   `$pattern4 = "/world/i";`
*   `$pattern5 = "/(l){2}/";`

Let us analyse the above patterns!

*   The delimiter used here is /. It means, the delimiter specifies the start and stop of the pattern string.
*   The use of modifier i next to delimiter at the end will say that the pattern search should be case insensitive as opposed to default sensitive search.
*   The last pattern uses a quantifier specifying the character 'l' should occur twice.

**Execute:**

On execution, try to check if the pattern search is giving the same output as you guessed.

![3-4](Images/image00211.jpeg)

* * *

### 3.5 Exceptions

* * *

An exception is an object that describes an error or unexpected behaviour of a PHP script.

Exceptions are thrown by many PHP in-built functions / classes and user defined functions / classes. They are a good way to stop a function when it comes across data that it cannot use.

There might be some places in the code where we feel a wrong input may result in an error. To a normal user, they might not have any clues on working with the input. So, when they provide a wrong input, an exception can give them appropriate message on what went wrong.

Since this e-book does not cover object oriented programming, we will discuss exceptions related to functions alone.

**The Exception Object**

The Exception Object contains information about the error or unexpected behaviour that the function encountered. Though this part uses objects, we will learn it for using in functions.

We have two actions related to exceptions:

*   throw an exception - throw information that some error has occurred
*   catch an exception - tell what the exception is (hinting on what kind of error has occurred)

**Syntax**

```
new Exception(message, code, previous)
```

Parameters:

All the parameters are optional.

*   message - A string describing why the exception was thrown
*   code - an integer that can be used to easily distinguish this exception from others of the same type
*   previous - If this exception was thrown in a catch block of another exception, it is recommended to pass that exception into this parameter

**Throwing an Exception**

The throw statement allows a user defined function or method to throw an exception. When an exception is thrown, the code following it will not be executed.

If an exception is not caught, a fatal error will occur with an "Uncaught Exception" message.

**Practice:**

We will look into an example now where we use an exception. This is a universal example of using exceptions so that everyone understands it clearly.

We will look into the code segment without throwing exception:

```
//Exception
function divide($dividend,$divisor){
	return ($dividend / $divisor);
}

echo "<br>Division 10/5 = ".divide(10,5);
echo "<br>Division 10/0 = ".divide(10,0);
```

![3-5-1](Images/image00212.jpeg)

Can you see? 10/0 gives infinity.

Now, we will include exception in our code:

```
//Exception
function divide($dividend,$divisor){
 if($divisor == 0){
	throw new Exception("Division by zero");
 }
 return ($dividend / $divisor);
}

echo "<br>Division 10/5 = ".divide(10,5);
echo "<br>Division 10/0 = ".divide(10,0);
```

Now, the output will be:

![3-5-2](Images/image00213.jpeg)

This exception does not allow the function to return any value when it finds the value of the variable $divisor as 0, there by not allowing the relevant echo statement also to be printed.

To a normal user using your web page, INF may not be clear, but an error message will mean that their input is not valid. This might be a small example so it cannot have much impact on displaying INF without exceptions. Moreover, the INF value is not used further. But when you develop real time applications, it becomes a big deal when one output is forwarded to other parts of program, sometimes resulting in an uncontrolled loop. So let us practise using exceptions.

Now, we will have a look on the catch statement.

**try...catch Statement**

To avoid the error from the example above, we can use the try...catch statement to catch exceptions and continue the process.

**Syntax**

```
try {
  code that can throw exceptions
} catch(Exception $ex) {
  code that runs when an exception is caught
}
```

The catch block indicates what type of exception should be caught and the name of the variable which can be used to access the exception. In the example above, the type of exception is Exception and the variable name is $ex.

**Practice:**

```
//Exception
function divide($dividend,$divisor){
 if($divisor == 0){
	throw new Exception("Division by zero");
 }
 return ($dividend / $divisor);
}

echo "<br>Division 10/5 = ".divide(10,5);
echo "<br>Division 10/0 = ";
try{
  echo divide(10,0);
}catch (Exception $ex){
  echo "Unable to divide";
}
```

**Execute:**

![3-5-3](Images/image00214.jpeg)

**The try...catch...finally Statement**

The try...catch...finally statement can be used to catch exceptions. Code in the finally block will always run regardless of whether an exception was caught. If finally is present, the catch block is optional.

**Syntax**

```
try {
  code that can throw exceptions
} catch(Exception $e) {
  code that runs when an exception is caught
} finally {
  code that always runs regardless of whether an exception was caught
}
```

**Practice:**

We will rewrite the same example with finally:

```
//Exception
function divide($dividend,$divisor){
 if($divisor == 0){
	throw new Exception("Division by zero");
 }
 return ($dividend / $divisor);
}

echo "<br>Division 10/5 = ".divide(10,5);
echo "<br>Division 10/0 = ";
try{
  echo divide(10,0);
}catch (Exception $ex){
  echo "Unable to divide";
}finally{
echo "<br> End of Program";
}
```

**Execute:**

Now, we will get an output with the echo statement from the finally block.

![3-5-4](Images/image00215.jpeg)

**Methods**

When catching an exception, the following table shows some of the methods that can be used to get information about the exception:

![3-5-methods](Images/image00216.jpeg)

**Practice:**

We will look the same coding example with the methods discussed above.

Hope you will be getting a question, what happens if try block gets executed? This question will be answered too.

```
//Exception
function divide($dividend,$divisor){
 if($divisor == 0){
	throw new Exception("Division by zero");
 }
 return ($dividend / $divisor);
}

try{
  echo "<br>Division 10/5 = ".divide(10,5);
}catch(Exception $ex){
  echo "No error in input";
}

echo "<br>Division 10/0 = ";
try{
  echo divide(10,0);
}catch (Exception $ex){
  $code = $ex->getCode();
  $message = $ex->getMessage();
  $file = $ex->getFile();
  $line = $ex->getLine();
  echo "Exception thrown in $file on line $line: [Code $code] $message";
}
```

**Execute:**

When a try block gets executed, the catch does not get executed. It is similar to an execution of if…else statement. Either of the block gets executed!

Hope you can understand:

*   $ex -> getCode() - states the exception code
*   $ex -> getMessage() - retrieves the message from Exception() object inside the function
*   $ex -> getFile() - retrieves the complete file path where exception is thrown
*   $ex -> getLine() retrieves the line number where the exception is thrown (Exception() object)

![3-5-5](Images/image00217.jpeg)

If you are a novice programmer, you may feel like why you should get along with these exceptions. Perhaps you are right in the context of learning and practising. But in the case of development, a good programmer should define all possible blocks of his/her code so that unwanted and unclear errors will be avoided for the end-users.

Hope you will start using exceptions when you start working on real-time applications.

* * *

# Chapter 4: Files and Forms

* * *

*   [](#part0025.xhtml)
    
    #### 4.1 File Handling
    
*   [](#part0026.xhtml)
    
    #### 4.2 Superglobals
    
*   [](#part0027.xhtml)
    
    #### 4.3 Working with Forms
    
*   [](#part0028.xhtml)
    
    #### 4.4 Form Validation
    
*   [](#part0029.xhtml)
    
    #### 4.5 File Upload
    

* * *

### 4.1 File Handling

* * *

File handling is an important aspect of a web application. This section deals with how to work with files on a server.

PHP has several functions for creating, opening, reading, uploading, and editing files.

**Creating / Opening a File:**

In PHP, in order to open a file, or to write a file to a server, we need to create the file. All these tasks are done by a single function. It means,

*   when you create, you need to open, once you open, you need to write it to server
*   when you want to write a file to server, you must obviously open it
*   when you want to open a file, it has to be either created or existing.

**Function: fopen()**

If you use fopen() on a file that does not exist, it will create it, given that the file is opened for writing (w) or appending (a). Writing means starting to write a content, while appending means adding some more content to the existing content.

Parameters:

fopen(name of the file, mode to open);

We will just look at the various modes available:

![4-1-filemodes](Images/image00218.jpeg)

When you create a new file, you need to use “w”.

**Practice:**

Hope your new file section4.php is already created and opened for editing. We will first create a file for writing:

```
$testfile = fopen("test.txt", "w");
```

Once you execute, you will find a text file created in the location of section4.php

A new file with 0 byte size is created. The text document will have no content.

![4-1-1](Images/image00219.jpeg)

**Note:** If you are having errors when trying to get this code to run, check that you have granted your PHP file access to write information to the hard drive.

*   To grant access, right click on the folder PracticePHP => Properties => Uncheck Read-only
*   Go to Security Tab => Check permissions needed for the appropriate users

You remember **Resource data type** from Section 2?  
$testfile belongs to the resource data type - though not an actual type, it holds a resource such as a file here. 

**Writing content to a File:**

There is a function fwrite() which will write contents to the file.

Understand:

*   when you open a file, the file gets written to the server
*   But when you write using fwrite(), it means you are adding content to the file

Hope you understand both ‘write’. When you open a file, you open in the write mode mentioning it as ‘w’. Whereas a function fwrite() serves for writing content.

There are 2 parameters:

fwrite(name of the file, content to be added);

**Practice:**

We will add few string characters to the file: Continue coding in the same section4.php:

```
$texttoadd = "First Line of Text followed by new line character! ";
fwrite($testfile,$texttoadd);
$texttoadd = "Second Line of Text followed by new line character! ";
fwrite($testfile,$texttoadd);
```

Do not execute now, we will close the file and execute it.

**Closing a File:**

Once we finish writing, we have to close the file. It’s just like when you open a file, you ought to close it.

The function fclose() takes care of closing the file.

**Practice:**

Add the following line to the above code:

```
fclose($testfile);
```

It's a good programming practice to close all files after you have finished working with them. An open file will be taking up resources.

Now, execute the php file and then go to the path where text.txt is located. Open text.txt, you will find the following lines:

![4-1-2](Images/image00220.jpeg)

**Writing contents to an existing file:**

**What happens when you close and then open the file again to write?**

The file testfile.txt already contains some data, right? Now, if you open an existing file in the write mode, all the existing data will be erased and we should start again with an empty file, as if we created it from scratch.

Now, let us just write the following code in section4.php as:

```
$testfile = fopen("test.txt", "w");
$texttoadd = "New first Line! ";
fwrite($testfile,$texttoadd);
$texttoadd = "New Second Line! ";
fwrite($testfile,$texttoadd);
fclose($testfile);
```

When you execute the file now, instead of appending the content, they just overwrite the content from scratch.

![4-1-3](Images/image00221.jpeg)

So, what should you do to continue writing content, that is appending content without erasing the existing content? Go with append mode: Comment all the previous coding and have only these 4 lines.

```
$testfile = fopen("test.txt", "a");
$texttoadd = "Third Line to existing 2 lines! ";
fwrite($testfile,$texttoadd);
fclose($testfile);
```

Execute the php file and now open test.txt, you will find the following:

![4-1-4](Images/image00222.jpeg)

**You cannot refresh an open text document! Please close it and open again to check!**

Now we have done with writing contents to a file. The next task is to read contents from a file. We have many functions for that purpose.

**Reading a File:**

We can open a file to read in the following ways:

*   using readfile() function
*   using fread() function

We will look into one by one:

For executing code to read the file, try commenting all write related codes and use only read related codes to check how they retrieve content from existing text document!

**Using readfile() function:**

It reads a file and writes it to the output buffer. It returns the number of bytes read on success. The readfile() function is useful if all you want to do is open up a file and read its contents.

We have already created a file named test.txt. Let us try reading the same file.

```
echo readfile("test.txt");
```

![4-1-5](Images/image00223.jpeg)

Comment the echo statement and try the next function.

**Using fread() function:**

The fread() function reads from an open file.

Parameters:

fread(name of the open file, maximum number of bytes to read);

Let us use this in code:

```
$filecontent = fopen("test.txt","r");
echo fread($filecontent,filesize("test.txt"));
```

On executing, we get the output:

![4-1-6](Images/image00224.jpeg)

*   filesize(file) is a function to return the number of bytes of the file.

**Reading Functions:**

We will look upon few functions to read:

*   read single line: fgets()
*   read single character: fgetc()
*   check end-of-file: feof()

**fgets() function:**

The fgets() function is used to read a single line from a file.

Let us practise this code:

```
$filecontent = fopen("test.txt","r");
echo fgets($filecontent);
fclose($filecontent);
```

Whenever there is a call to fgets() function, the pointer moves to the next line. Since there is single fgets() function, one line is alone read.

![4-1-7](Images/image00225.jpeg)

**fgetc() function:**

The fgetc() function is used to read a single character from a file.

Let us practise this code:

```
$filecontent = fopen("test.txt","r");
echo fgetc($filecontent);
fclose($filecontent);
```

After a call to the fgetc() function, the file pointer moves to the next character. Since fgetc() is called once, one character is alone read!

![4-1-8](Images/image00226.jpeg)

**What do you do when you wish to read the file till the end?**

**feof() function:**

The feof() function checks if the "end-of-file" (EOF) has been reached. It is useful for looping through data of unknown length.

Let us practise this code:

```
$filecontent = fopen("test.txt","r");
echo "<p>Printing character by character </p>";
while(!feof($filecontent)){
    echo fgetc($filecontent);
}
fclose($filecontent);

$filecontent = fopen("test.txt","r");
echo "<p>Printing line by line </p>";
while(!feof($filecontent)){
    echo "<p>".fgets($filecontent). "</p>";
}
fclose($filecontent);
```

We close the file after fgets() and open it again. Why? Once the first while loop reaches the end of the file, it cannot point back to the beginning. So, we close and then open the file again for reading to execute fgetc() in wile loop.

Let us execute the same:

![4-1-9](Images/image00227.jpeg)

Hope you understand why we check feof() in the while loop. The reason is in order to read all the lines (using fgets()) and all the characters (fgetc()), we use !feof() inside while, as a condition instructing the loop to continue till the end of the file.

**Note:**

**What happens if you open a non-existing file?**

Shall we try this?

```
$newfile = fopen("newtest.txt","r");
```

What is the output?

![4-1-10](Images/image00228.jpeg)

There is a way to give an information to the user that a file is not existing:

```
$newfile = fopen("newtest.txt","r") or die("Unable to open file!");
```

![4-1-11](Images/image00229.jpeg)

This die statement can get executed when:

*   the file does not exist
*   the file is not granted access to be opened

It will end the script immediately.

With this, file handling section comes to an end!

* * *

### 4.2 Superglobals

* * *

Some predefined variables exist in PHP where they are always accessible, regardless of scope - you can access them from any function, class or file without having to do anything special. These variables are called superglobal variables or simply superglobals.

The PHP superglobal variables are:

*   $\_GLOBALS
*   $\_SERVER
*   $\_REQUEST
*   $\_POST
*   $\_GET
*   $\_FILES
*   $\_ENV
*   $\_COOKIE
*   $\_SESSION

**Superglobal variables are built-in variables that are always available in all scopes.**

We will not discuss every variable in this chapter itself. An introduction will be given to all, the real usage will be dealt in this chapter and in the next chapter.

**$\_GLOBALS:**

$GLOBALS is used to access global variables from anywhere in the PHP script. We used these variables while discussing variables scope in functions. Hope you remember!

**S\_SERVER:**

$\_SERVER holds information about headers, paths, and script locations. $\_SERVER superglobal variable has many elements to get description about server and server related entities.

You will find a list of elements to be used with $\_SERVER:

![4-2-superglobals](Images/image00230.jpeg)

We will test a few elements in practice session:

```
echo "Server Address: ".$_SERVER['SERVER_ADDR'];
echo "<br>Server Name: ".$_SERVER['SERVER_NAME'];
```

![4-2-1](Images/image00231.jpeg)

We have 3 superglobal variables which are used to collect and pass data from a form. We will just know in one line as of now and look them in depth in the next section.

**$\_REQUEST:**

$\_REQUEST is used to collect data after submitting an HTML form.

**$\_POST:**

$\_POST is used to collect form data after submitting an HTML form using method="post".

**$\_GET:**

$\_GET is used to collect form data after submitting an HTML form using method="get".

**$\_ENV:**

$\_ENV is used to return the environment variables from the web server. For learning purpose, we will go with an example now:

```
echo 'Username: ' .$_ENV['USER'];
```

![4-2-2](Images/image00232.jpeg)

It is an error! No issues!

Let us debug the error! Undefined index: It means we have to define an index USER!

We will now modify the code as:

```
$_ENV['USER'] = $_SERVER['SERVER_NAME'];

echo 'Username: ' .$_ENV['USER'];
```

![4-2-3](Images/image00233.jpeg)

That's all!

We will discuss $\_FILES later in this chapter. We will discuss $\_COOKIE and $\_SESSION in the next chapter.

Let us move to the next section!

* * *

### 4.3 Working with Forms

* * *

We will be developing a web application using a project title from Chapter-6. So, we will now design some forms for that application and through that we will learn how to work with forms using php. Got it? Let’s start then!

I will just give you a small intro on what the project is all about.

**Project:** We will go with **online course** web application.

In this online course application, we will have instructors who teach courses and learners who learn those stuff.

Basically, we have 2 users: instructor and learner. Same way, we have 2 more things: course and its content.

We will simply design forms and use them to learn about certain superglobals discussed in the previous section.

Remember, we do not validate any data in the form, we are just learning how to send and retrieve form data.

**Designing a Form:**

Let us design a form for instructor sign up (registration of instructor):

From here, we will create a folder for this project and work through it!

**What to do?**

*   Create a folder named onlinecourse in C:/xampp/htdocs
*   Create a new php file named instructor\_signup.php

**Remember:** Even when the form you design is just with HTML elements, in order to work with form data, you need PHP. So, save the file with .php extension.

If you are ready, start your Apache server in xampp and run the project onlinecourse in the browser as:

![4-3-1](Images/image00234.jpeg)

Here is the coding snippet in HTML:

**Design Code in instructor\_signup.php file**

```
<!DOCTYPE html>
<html>
<head>
<title>Instructor Sign Up </title>
</head>
<body>
<h2>Instructor Sign Up </h2>
<form method="get" action="" name="form1">
<table>
<tr>
<th style='text-align:left;'><label>Email Address</label></th>
<td>:&emsp;</td>
<td><input type="email" name="txtemail" size="30" placeholder="Your Email Address"></td>
</tr>
<tr>
<th style='text-align:left;'><label>Name</label></th>
<td>:&emsp;</td>
<td><input type="text" name="txtname" size="30" placeholder="Your Name"></td>
</tr>
<tr>
<th style='text-align:left;'><label>Qualification</label></th>
<td>:&emsp;</td>
<td><input type="text" name="txtqualification" size="30" placeholder="Your Qualification"></td>
</tr>
<tr>
<th style='text-align:left;'><label>Country </label></th>
<td>:&emsp;</td>
<td><select name="txtcountry">
<option value="">Choose a country from the list</option>
<option value="India">India</option>
<option value="France">France</option>
<option value="Japan">Japan</option>
<option value="Canada">Canada</option>
</select></td>
</tr>
<tr></tr>
<tr>
<th></th><td></td><td><p><input type="submit" name="signup" value="Sign Up"></p></td>
</tr>
</table>
</form>
<hr></body>
</html>
```

I assume that you have some idea / understanding on HTML forms.

I have just randomly used some country names!

Let me explain what the code snippet is about:

We have 4 fields - instructor email id, instructor name, instructor qualification, instructor country. We try getting inputs using these 4 fields. If the form’s action is empty, all the data is submitted to the same page. Right now, we are not saving this data anywhere. We just pass the data and print them in the same page using superglobal variables.

On execution, you should see like this (if you have coded as above):

![4-3-2](Images/image00235.jpeg)

You can design the form as you like. But for learning purpose, don't change any element's name. We have these names in this form: **form1**, **txtemail**, **txtname**, **txtqualification**, **txtcountry**, **signup**. Make sure the spellings are right. Because, these names are going to play a big role.

Since the method we used here is get, we can collect those data using $\_REQUEST or $\_GET variables!

Code the following in the beginning of instructor\_signup.php file:

```
<?php
if(isset($_GET['signup'])){
  echo "<br>You have clicked Sign up";
}
?>
```

We will check if the form is submitted. What to do?

*   Add this code to the php file.
*   Execute the file
*   Click Sign up button in the page

![4-3-3](Images/image00236.jpeg)

If you get this message displayed on top, your form is submitted.

if(isset($\_GET\['signup'\])) explanation:

*   $\_GET\['signup'\] will get the value 1 if the button named signup is clicked.
*   isset() will check if $\_GET\['signup'\] has a value. If the button is not clicked, $\_GET\['signup'\] will not have value, making isset() to false. When it is clicked, isset() return true.
*   when you pass isset($\_GET\['signup'\]) inside if() statement, the condition is evaluated to be true and the statement block is executed. If condition evaluates to false, the statement block does not get executed.

Example: when you executed the page, you did not get the message, only when you clicked the button, you got this message.

Can you see the URL? When you use the $\_GET method, all your values will be explicitly shown in the URL along with name parameters.

Now we will just get all these values in variables and print the same.

Add this code in the beginning: (Instead of only echo statement, we add few more lines).

```
<?php
if(isset($_GET['signup'])){
   echo "<br>You have clicked Sign up";
   $email = $_REQUEST['txtemail'];
   $name = $_GET['txtname'];
   $qualification = $_GET["txtqualification"];
   $country = $_GET['txtcountry'];
}
?>
```

Unless needed, we can use single or double quotes.

We shall print the details below the form. See where your form ends with </form>. Place the code snippet below <hr> tag:

```
<?php
if(isset($email)){
  echo "<br>Email - ".$email;
}
if(isset($name)){
  echo "<br>Name - ".$name;
}
if(isset($qualification)){
  echo "<br>Qualification - ".$qualification;
}
if(isset($country)){
  echo "<br>Country - ".$country;
}
?>
```

The reason for using isset() for every php variable is simple - if you don’t use, when you execute, php will search for those variables and display error if not found. Do you want to check? You can!

After adding code, make sure you don't refresh the URL with the parameters.

Execute [http://localhost/onlinecourse/instructor\_signup.php](#part0027.xhtml)

After execution, give some input in those fields and click Sign up button:

![4-3-4](Images/image00237.jpeg)

Can you understand what it does? Also, make a note on the URL parameters!

Do you want your form data to be safe?

Very simple, you need to do 2 things:

*   change form method="post"
*   Change all your $\_GET\[\] to $\_POST\[\] variables. You can change / leave $\_REQUEST\[\]

Let me give the code:

```
<?php
if(isset($_POST['signup'])){
    echo "<br>You have clicked Sign up";
    $email = $_REQUEST['txtemail'];
    $name = $_POST['txtname'];
    $qualification = $_POST["txtqualification"];
    $country = $_POST['txtcountry'];
}
?>

<form method="post" action="" name="form1">
```

Execute [http://localhost/onlinecourse/instructor\_signup.php](#part0027.xhtml)

![4-3-5](Images/image00238.jpeg)

See how clean your URL is!

When you are not sure whether your form is sent by get or post method, you can retrieve the form variables using $\_REQUEST!

Let us have an idea on **GET vs POST:**

Both GET and POST create an array like: array( key1 => value1, key2 => value2, key3 => value3, ...). This array holds key/value pairs, where keys are the names of the form controls and values are the input data from the user.

You can access them from any function, class or file without having to do anything special. They are accessible globally.

*   $\_GET is an array of variables passed to the current script via the URL parameters.
*   $\_POST is an array of variables passed to the current script via the HTTP POST method.

**When to use GET?**

Information sent from a form with the GET method is visible to everyone (all variable names and values are displayed in the URL).

*   GET has limits on the amount of information to send.
*   The limitation is about 2000 characters.
*   However, because the variables are displayed in the URL, it is possible to bookmark the page. This can be useful in some cases.
*   GET may be used for sending non-sensitive data.
*   GET should NEVER be used for sending passwords or other sensitive information!

**When to use POST?**

Information sent from a form with the POST method is invisible to others (all names/values are embedded within the body of the HTTP request)

*   It has no limits on the amount of information to send.
*   Moreover POST supports advanced functionality such as support for multi-part binary input while uploading files to server.
*   However, because the variables are not displayed in the URL, it is not possible to bookmark the page.
*   Developers prefer POST for sending form data.

* * *

### 4.4 Form Validation

* * *

We will learn how to process forms with security in this section. Proper Validation of form data is important to protect your data from hackers and spammers!

Examples on validation:

These 2 validation rules are as per our instructor form signup.

*   if you provide a name in text field, it should contain letters and whitespace.
*   if you provide an email address in email field, it must be valid with @ and domain name.
*   we can also mention a field as mandatory or optional using required attribute in html input element.

**How do we validate the form designed in the previous section?**

We will follow some steps here:

*   Pass all variables through htmlspecialchars() function. The reason for using this function is unnecessary script codes will not be passed inside text fields like name, email.
*   Strip unnecessary characters (extra space, tab, newline) from the user input data (with the PHP trim() function).
*   Remove backslashes (\\) from the user input data (with the PHP stripslashes() function)
*   Check whether the field is empty when the mandatory attribute is mentioned.
*   Place each validation in separate functions so that same code need not be repeated for every form.
*   Generate appropriate error message for every field, so that the user understands what went wrong in his/her input.

These are few steps in general. I have also hinted some functions to make your work easier.

For our signup form, we can try validating email, name and country fields. We may not use all the above functions. Instead, we will use some other functions for our purpose!

Shall we proceed validating our form?

*   create a file named validate\_form.php inside C:/xampp/htdocs/onlinecourse
*   include the validate\_form.php file in instructor\_signup.php file

Let me show you the include statement to be placed in the beginning of instructor\_signup.php:

```
include('validate_form.php');
```

Let me remind you the fields once again:

*   txtemail - for email address
*   txtname - for name
*   txtqualification - for qualification
*   txtcountry - for country

Out of these 4 fields, txtcountry is a field chosen from a given list. But still we have one requirement, that is, some value has to be selected making the field mandatory!

This is no rule set to validate this way. You are free to choose your own rules for your fields provided they are appropriate.

We will practise code snippets for every validation.

Once all validation snippets are ready, we will update instructor\_signup.php file in the last!

**Validate Email Address:**

If you are using type=email (HTML5) in input element and check in latest browsers, this field will be automatically validated by the browser. We will look a solution for the old browsers and for older versions of HTML.

We will use the filter\_var() function to check whether an email address is well-formed.

We retrieve the email address in $email variable as:

```
$email = $_REQUEST['txtemail'];
```

Let us now write a function in validate\_form.php:

```
function check_email($email){
  if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
	return "Invalid email address";
  }
}
```

Let me explain:

*   We pass the variable $email as a parameter to the function check\_email($email)
*   We use filter\_var() function to validate email address format
*   If the format is wrong, it returns an error message

**Validate Name:**

We will use regular expression function preg\_match() to check if name field contains letters, dashes, apostrophe and whitespaces.

We retrieve the name field in $name variable as:

```
$name = $_POST['txtname'];
```

Let us now write a function in validate\_form.php

```
function check_name($name){
  if (!preg_match("/^[a-zA-Z-' ]*$/",$name)) {
    return "Name must contain letters and whitespaces!";
  }
}
```

Let me explain:

*   We pass the variable $name as a parameter to the function check\_name($name)
*   We use preg\_match() to check whether the name contains letters, whitespaces,dashes.
*   If the format is wrong, it returns an error message

**What to modify in sign up page?**

Hope you have added 2 functions in validate\_form.php. Now, we will update the code in instructor\_signup.php file:

There are 2 sets of php coding tags. One set appears in the top.

We have included the validate\_form.php file

```
<?php
include('validate_form.php');
if(isset($_POST['signup'])){
  echo "<br>You have clicked Sign up";
  $email = $_REQUEST['txtemail'];
  $name = $_POST['txtname'];
  $qualification = $_POST["txtqualification"];
  $country = $_POST['txtcountry'];
}
?>
```

The second set of php code appears near the bottom:

We will apply validation here:

```
<?php
$display = true;
if(isset($email) and isset($name) and isset($qualification) and isset($country)){
  //check field validation
  $email_status = check_email($email);
  $name_status = check_name($name);
  if($email_status <> NULL){
    echo "<p style='text-color:red;'>".$email_status."</p>";
    $display = false;
  }
  if($name_status <> NULL){
    echo "<p style='text-color:red;'>".$name_status."</p>";
    $display = false;
  }
  if(empty($country)){
    echo "<p style='text-color:red;'>No country chosen</p>";
    $display = false;
  }
  //display fields if no errors found
  if($display){
    echo "<br>Email - ".$email;
    echo "<br>Name - ".$name;
    echo "<br>Qualification - ".$qualification;
    echo "<br>Country - ".$country;
  }
}
?>
```

Let me explain the code:

*   We have set a variable $display to true
*   We check if all variables have a value, If yes, proceed 
    *   validate email field, if the email field is not valid, display message
    *   validate name field, if the name field is not valid, display message
    *   check if a country is chosen, else display a message
    *   if any of the three validation fails, then turn $display = false, which will not print any details
    *   if $display = true even after validation, print the fields

Let us execute with valid/invalid input data.

Invalid input data and output:

![4-4-1](Images/image00239.jpeg)

![4-4-2](Images/image00240.jpeg)

Valid input data and output:

![4-4-3](Images/image00241.jpeg)

![4-4-4](Images/image00242.jpeg)

**Note:**

In HTML5, we have text fields like email, url, number, search which will be auto validated before submitting a form. If you wish to use type=text, you ought to validate them. Even if you have email, url types, it is a good practice to impose validation rules so that the input data of users using older browsers can also be validated.

**Validating URL:**

Just for knowledge purpose, let me give you the code for validating a URL field.

Assume we store a website’s URL in $url variable, find the validation below:

```
if (!preg_match("/\b(?:(?:https?|ftp):\/\/|www\.)[-a-z0-9+&@#\/%?=~_|!:,.;]*[-a-z0-9+&@#\/%=~_|]/i",$url))
{
  return "Invalid URL";
}
```

The intention of this section is to give you an insight on how to use PHP (and PHP functions) for form validation. Hope you understood how to validate form fields in PHP. The next section will deal how to upload a file using form and validate the same.

* * *

### 4.5 File Upload

* * *

In our onlinecourse project, we have a form to get course contents. Say, we have this ebook content as a PHP course. What will be the format of the content?

*   content type: pdf / ppt / doc / video
*   content file: uploading files through browser

What are we going to do in this section?

*   Enable file upload
*   Design a form and upload file
*   Impose rules for files being uploaded
*   Validate those rules

**Enabling File Upload:**

Generally, servers will have this feature enabled. But locally, we can have a check once.

*   Locate your php.ini file in the path C:/xampp/php
*   Open the file using any text editor
*   Search for file\_uploads (around line 830) and check whether file\_uploads = on
*   If it is not enabled, enable it as given above.

**Designing the course content form:**

Create a new php file named upload\_content.php in the path C:/xampp/htdocs/onlinecourse

We have created the form in this way:

*   Forms must be submitted using 'post' method.
*   We should include the attribute: enctype="multipart/form-data" in the form element. This specifies what content-type it should use when submitting the form.
*   Using file in type attribute in the input element will provide a Browser button

Remember that the above set rules have to be applied to make file uploading work.

Here is the form code:

```
<!DOCTYPE html>
<html>
<head>
<title>Upload Content</title>
</head>
<body>
<h2>Upload Course Content</h2>
<form method="post" action="" name="form2" enctype="multipart/form-data">
<p>Choose File Type:
<select name='txtfiletype'>
<option value='docx'>DOCX</option>
<option value='pptx'>PPT</option>
<option value='pdf'>PDF</option>
<option value='mp4'>MP4 Video</option>
</select>
</p>
<p>Choose File: <input type="file" name="txtfileupload"></p>
<p><input type="submit" name="upload" value="Upload File"></p>
</form>
</body>
</html>
```

Have a look at the form:

![4-5-1](Images/image00243.jpeg)

We have provided only 4 file types - docx, pptx, pdf and mp4 extensions.

**Upload Script for selected files:**

Now, we have the form ready. We have to choose the file type and choose the file to be uploaded. Once done, we have to click the Upload File button.

The script below will upload the file to the server. We will first look at the code and the explanation will follow the code.

```
<?php
if(isset($_POST['upload'])){
 echo "<br>You have clicked Upload File button...";

 //fetching uploaded file details
  $file_name = $_FILES['txtfileupload']['name'];
  $file_tmp =$_FILES['txtfileupload']['tmp_name'];
  $file_type = $_POST['txtfiletype'];
  $file_string = explode('.',$_FILES['txtfileupload']['name']);
  $file_ext= strtolower(end($file_string));

 //check if uploaded file extension is from the selected type
 echo "<br>File name = ".$file_name;
 echo "<br>File Temp = ".$file_tmp;
 echo "<br>File Type = ".$file_type;
 echo "<br>File Ext of file = ".$file_ext;

 if($file_type == $file_ext){
  //uploaded file moved to current folder
  move_uploaded_file($file_tmp,$file_name); 
  echo "<br>File Uploaded successfully!";
  }
  else{
   echo "<br>File extension not matching!";
  }

}
?>
```

Let me explain:

*   We retrieve file name, file's temporary location from the uploaded file using $\_FILES\[\] superglobal variable.
    
    ```
    $file_name = $_FILES['txtfileupload']['name'];
    $file_tmp =$_FILES['txtfileupload']['tmp_name'];
    ```
    
*   We fetch file type from the selected drop down list in the form.
    
    ```
    $file_type = $_POST['txtfiletype'];
    ```
    
*   We find the extension of the uploaded file in 2 steps:
    
    ```
    $file_string = explode('.',$_FILES['txtfileupload']['name']);
    $file_ext= strtolower(end($file_string));
    ```
    
    *   Using explode function, we split the string using the separator or split character '.' That is, explode splits the file name xxxx.docx as 2 strings namely xxxx and docx
    *   Using end function, we find the string at the end. That’s is, out of two strings xxxx, docx end() picks the final string - docx
*   We print all the above fetched details
    
    ```
    echo "<br>File name = ".$file_name;
    echo "<br>File Temp = ".$file_tmp;
    echo "<br>File Type = ".$file_type;
    echo "<br>File Ext of file = ".$file_ext;
    ```
    
*   We have stored form selected type in $file\_type and uploaded file's extension in $file\_ext.
*   We compare $file\_type and $file\_ext variables
    
    ```
    if($file_type == $file_ext)
    ```
    
*   If the extension matches, we move the file from temporary location to the folder in which we are working
    
    ```
    move_uploaded_file($file_tmp,$file_name); 
    echo "<br>File Uploaded successfully!";
    ```
    
*   If the extension does not match, we simply print a message and do not move the file.
    
    ```
    echo "<br>File extension not matching!";
    ```
    

You can also move the file to a different folder. To keep it as simple, we upload to the same folder onlinecourse from where we are currently working.

Shall we execute now?

Browse [http://localhost/onlinecourse/upload\_content.php](#part0029.xhtml)

In my case, I selected a file named Content.docx from my system:

![4-5-2](Images/image00244.jpeg)

Can you find the temporary location? It is the actual upload, but a temporary place of store!

*   Once we move the file to our destination, we print the message as file uploaded successfully.
*   Check onlinecourse folder to see your uploaded file!

**Why should we move the file?**

Because you cannot access the file from the temporary location! Once program stops executing, temporary files go away! You need a permanent location to save the uploaded file!

Try selecting a file type like docx and try uploading a picture file:

![4-5-3](Images/image00245.jpeg)

Can you see the upload has happened in the temporary location but file has not been moved to our location, just a message is printed stating file extension is not matching.

Check onlinecourse folder, you cannot find the uploaded picture. You can even check the temporary path, you will not find the temporary file too.

![4-5-4](Images/image00246.jpeg)

This is all about file uploading script.

Now we have certain rules that can be imposed while uploading files, we will just have a quick look over them!

Assume $file\_uploaded is the variable holding the file! The corresponding form element is $\_FILES\[‘txtfileupload’\]

**Check if file is already existing:**

We use the file\_exists() function to do this.

```
// Check if file already exists
if (file_exists($file_uploaded)) {
  echo "File already exists.";
}
```

**Limit file size:**

We check the file size using bytes value.

```
// Check file size
if ($_FILES["txtfileupload"]["size"] > 500000) {
  echo "File is too large.";
}
```

**Limit File Type:**

We can also limit file type in the upload script using if()condition. Say, we have a variable $file\_type.

You can set conditions like:

```
// Allow certain file formats
if(($file_type != "docx") && ($file_type != "pptx") && ($file_type != "pdf" ) && ($file_type != "mp4" )){
  echo "Only docx, pptx, pdf and mp4 files are allowed.";
}
```

These conditions check if the uploaded file type is not docx, not pptx, not pdf and not mp4 - if all 4 extensions are not there, it means some other extension is present, thus a message is thrown to the user.

We will include limit file size in our coding snippet:

We will restrict files to 2MB. 2 MB = 2097152 Bytes.

```
<?php
if(isset($_POST['upload'])){
  echo "<br>You have clicked Upload File button...";

  //fetching uploaded file details
  $file_name = $_FILES['txtfileupload']['name'];
  $file_tmp =$_FILES['txtfileupload']['tmp_name'];
  $file_size =$_FILES['txtfileupload']['size'];
  $file_type = $_POST['txtfiletype'];
  $file_string = explode('.',$_FILES['txtfileupload']['name']);
  $file_ext= strtolower(end($file_string));

  //check if uploaded file extension is from the selected type
  echo "<br>File name = ".$file_name;
  echo "<br>File Temp = ".$file_tmp;
  echo "<br>File Type = ".$file_type;
  echo "<br>File Ext of file = ".$file_ext;

  if($file_type == $file_ext){
    if($file_size > 2097152){
       echo "<br>Cannot Upload! File > 2MB";
    }
    else{
       move_uploaded_file($file_tmp,$file_name); 
       echo "<br>File Uploaded successfully!";
    }
  }
  else{
    echo "<br>File extension not matching!";
  }
}
```

Try uploading a file greater than 2 MB. It will give a message instead of uploading it to the onlinecourse folder!

I tried uploading an mp4 video > 5MB

![4-5-5](Images/image00247.jpeg)

Impose your restrictions as to your need! We are completing File uploading with this!

I think you are clear on how to work with forms and upload files using forms in php.

With this, we come to the end of this chapter!

* * *

# Chapter 5: PHP in the Web

* * *

*   [](#part0031.xhtml)
    
    #### 5.1 Sessions
    
*   [](#part0032.xhtml)
    
    #### 5.2 Cookies
    
*   [](#part0033.xhtml)
    
    #### 5.3 Filters
    
*   [](#part0034.xhtml)
    
    #### 5.4 Handling JSON Data
    

* * *

### 5.1 Sessions

* * *

A session is a way to store information (in variables) to be used across multiple pages.

**What is a Session?**

Let us taking our surfing activity in a browser. We open a browser, we keep surfing content in the web. A browser session is between opening and closing the browser.

Now, let us see session in the context of web:

Assume you work in a web application. You log in to your account, make some changes and then log out. This is exactly a session. A session will retain some identity of yours so that the server knows who you are, throughout the session.

In PHP, we achieve this session concept using session variables. Session variables solve this problem by storing user information to be used across multiple pages. By default, session variables last until the user closes the browser or until the user is logged in.

Session variables hold information about one single user and make it available to all the pages the user visits within the application. Whenever a user logs in, a session for that user is started. If there are 3 users - user1, user2, user3 logging into the web application at the same time, one session variable will be created and it will store 3 values - say, the userid of the users. Based on the userid, it will identify which user has done what modification in the application.

**How do you start a session?**

We have the session\_start() function for starting a session.

Do you remember superglobal variable $\_SESSION? $\_SESSION global variable is used to set session variables.

Shall we practise this via our onlinecourse project?

**Practice:**

We will create a session variable in one page and retrieve the session variable value in another page.

Now, you have to create 2 php files: page1.php and page2.php in C:/xampp/htdocs/onlinecourse path.

What will we do in page1.php?

*   Design a form to get a name field
*   Set session variable and store the name

What will we do in page2.php?

*   Retrieve the name stored from session variable
*   Print the retrieved name

**Code in page1.php:**

I will present the design code first and then we will add php code so that you can understand how to set a session variable.

Here is the design code:

```
<!DOCTYPE html>
<html>
<head>
<title>Page 1 </title>
</head>
<body>
<h3> Page 1 - Get Name </h3>
<form method="post" name="form3">
<p><input type="text" name="txtname" placeholder="Enter your name"></p>
<p><input type="submit" name="submit" value="Submit"></p>
</form>
</body>
</html>
```

Now, we will add php code in the beginning of the page:

```
<?php
session_start();
if(isset($_POST['submit'])){
  $_SESSION['name'] = $_POST['txtname'];
  echo "<br> Session variable is set: ".$_SESSION['name'];
}
?>
```

Let me explain php coding:

*   We start a new session using session\_start()
*   We set the value of the name field to $\_SESSION\['name'\] global variable.
*   We print the stored variable

Execute page1.php from the browser and provide a name as input and press submit. Screenshots are provided below for reference:

![5-1-0](Images/image00248.jpeg)

![5-1-1](Images/image00249.jpeg)

The next work is to retrieve this name from page2.php file.

**Code in page2.php:**

There is nothing to design here. We will directly get into php code.

```
<?php
session_start();
if(isset($_SESSION['name'])){
  echo $_SESSION['name'];
}
else{
  echo "Nothing is stored in session variable";
}
?>
```

Session variables are not passed individually to each page as we do in $\_GET and $\_POST. They are retrieved from the session variable ($\_SESSION\[\]) placed in the beginning of the page.

How do we get the session variable value?

*   We open the session using session\_start()
*   We check whether the value is set for $\_SESSION\['name'\] variable
*   If it is set, we print the same, else we print a message that nothing is stored

Just execute page2.php file from the browser:

![5-1-2](Images/image00250.jpeg)

That's the story! We didn't provide any input in page2.php, yet the name is retrieved. How?

That is the power of session variables! Not only login details, we can retain any values in session variables! For the sake of example, I used login process.

**Note:**

Make sure you execute the pages: page1.php and page2.php in the same browser session. That means, you should not close and open browser. Keep browser alive and execute both the pages.

**How to change the value of a session variable?**

It is very simple, just assign the new value to the session variable wherever you need to modify.

**How to destroy a session?**

To remove all globally set session variables, we use session\_unset() function.

To destroy the session, we use session\_destroy() function.

Now shall we add some code to page2.php and test this?

Let me modify the code in page2.php as below:

```
<?php
session_start();
echo "<p>Session Set</p>";
if(isset($_SESSION['name'])){
 echo $_SESSION['name'];
}
else{
 echo "Nothing is stored in session variable";
}

//unset session variables
echo "<p>Session Unset</p>";
session_unset();
if(isset($_SESSION['name'])){
 echo $_SESSION['name'];
}
else{
 echo "Nothing is stored in session variable";
}
?>
```

Executing page2.php will now be:

![5-1-3](Images/image00251.jpeg)

Hope you can understand what happens after session\_unset().

Now, session variable is unset, so that page2.php does not have any value when executed individually.

Execute in browser: [http://localhost/onlinecourse/page2.php](#part0031.xhtml)

![5-1-4](Images/image00252.jpeg)

Since you have already unset the session variable, this page no more holds the value of $\_SESSION\['name'\]. Obviously nothing is stored! So, the message is printed twice (once for Session Set and once for Session Unset)!

* * *

### 5.2 Cookies

* * *

A cookie is a small file that the server embeds on the user's computer. Each time the same computer requests a page with a browser, it will send the cookie too.

A cookie is used to identify a user. You can create as well as retrieve cookies in PHP.

**Create Cookies:**

We can create a cookie using the setcookie() function. The setcookie() function must appear BEFORE the <html> tag.

**Syntax:**

`setcookie(name, value, expire, path, domain, secure, httponly);`

Parameters:

![5-2-parameters](Images/image00253.jpeg)

**Note:**

The value of the cookie is automatically URL encoded when sending the cookie, and automatically decoded when received.

In order to prevent URLencoding, we have to use setrawcookie().

**Retrieve Cookies:**

We can retrieve cookies using the superglobal variable $\_COOKIE.

**Modify Cookie value:**

We just need to assign the new value to the cookie using the setcookie() function.

**Delete a Cookie:**

To delete a cookie, use the setcookie() function with an expiration date in the past. A recommended practice is to set an expiry date when you create a cookie, so that you need not destroy it. When cookie gets expired, it is automatically deleted.

**How do you check if cookies are enabled?**

We will just perform a count on $\_COOKIE variables. $\_COOKIE will store values in arrays. So, performing a count and resulting in zero would state there are no cookies. We will directly code this in practice session.

**Practice:**

We will work with an example. Take those 2 files page1.php and page2.php.

*   We will set a cookie in page1.php
*   We will retrieve the cookie in page2.php

Let us code for both pages together and execute the pages because we will set the expiry of the cookie as 60 secs. After 60 secs, when we try loading page2.php, it should say cookie is deleted.

**Code for page1.php:**

Instead of $\_SESSION, we will replace php code alone with setcookie() function. The design code (html part) stays the same in page1.php

```
<?php
if(isset($_POST['submit'])){
setcookie('cookiename',$_POST['txtname'],time() + 60);
}
?>
<!DOCTYPE html>
<html>
<head>
<title>Page 1 </title>
</head>
<body>
<h3> Page 1 - Get Name </h3>
<form method="post" name="form3">
<p><input type="text" name="txtname" placeholder="Enter your name"></p>
<p><input type="submit" name="submit" value="Submit"></p>
</form>
</body>
</html>
```

Hope you understand the php code part. We just set a cookie with name as cookiename and value as $\_POST\['txtname'\], the value we would enter in the text field. The cookie is given an expiry of 60 secs.

Please do not execute it now. Since the cookie will expire in 60 secs, you cannot retrieve it in page2.php.

**Code for page2.php:**

For this file, we will completely replace the code as:

```
<?php
if(isset($_COOKIE['cookiename'])){
  echo $_COOKIE['cookiename'];
}
else{
  echo "Cookie has been expired";
}
echo "<p>Counting Cookies : ".count($_COOKIE); 
?>
```

Are both the pages ready?

Execute in order:

[http://localhost/onlinecourse/page1.php](#part0032.xhtml)

Give a name and press submit. Immediately execute:

[http://localhost/onlinecourse/page2.php](#part0032.xhtml)

Let me give both the screens:

We are not printing anything in page1.php after submit. So, here is the input:

![5-2-1](Images/image00254.jpeg)

After clicking submit, we get the form again. Now after executing page2.php, we get:

![5-2-2](Images/image00255.jpeg)

My browser is running a cookie, which is count 1 and guest cookie is count 2.

Hope 60 secs have gone after you execution of page2.php!

Execute again: [http://localhost/onlinecourse/page2.php](#part0032.xhtml)

![5-2-3](Images/image00256.jpeg)

My browser's cookie is alone counted as 1. guest cookie has been expired. That is, the cookie is automatically deleted after 60 secs.

We may need cookies when working with applications.

In fact, when you go through some sites, they openly ask you stating: We have cookies in our site, it is using your information, do you accept or decline?Have you come across such things? If you have not observed so far, observe hereafter!

* * *

### 5.3 Filters

* * *

Filters are used to validate and sanitize user’s input. Validating data is determining if the data is in the proper form. Sanitizing data is removing any illegal character from the data.

We have already discussed on validation of user input when working with forms.

The PHP filter extension has many of the functions needed for checking user input and is designed to make data validation easier and quicker.

**Why do we need filters?**

Many web applications receive external input. External input/data can be:

*   User input from a form
*   Cookies
*   Server variables
*   Database query results
*   Web services data

It is recommended to always validate external data! Invalid submitted data can lead to security problems and break your webpage! By making the best use of PHP filters, you can be sure that your application gets the correct input!

There are filters for validating and sanitizing data. We will have a look at the list!

**Validating Filters:**

![5-3-1-validatingfilter](Images/image00257.jpeg)

**Sanitizing Filters:**

![5-3-2sanitizingfilter](Images/image00258.jpeg)

**Reference:** [https://www.php.net/manual/en/filter.filters.php](https://www.php.net/manual/en/filter.filters.php)

**Where are we going to use these filters?**

If you can remember validation of email address in forms, we used a function called filter\_var() with 2 parameters. These filter IDs will be used inside that function. We will now discuss the filter\_var() function with adequate examples.

**filter\_var() function:**

The filter\_var() function is used to validate and sanitize data. It filters a single variable with a specified filter. It takes two pieces of data: the variable you want to check, the type of check to use on the variable (filter ID)

We will look at few ID's from the above list:

*   Sanitizing a string -  It removes all HTML tags from a string
*   Validating an integer - It checks whether the variable is an integer (0 is not a part of integer, so it may return false, we will look into a solution during practice session)
*   Validating an IP address - It checks if the variable is a valid IP address
*   Sanitizing and Validating a URL - It will sanitize the URL and then validate it

**Practice:**

Create a new page called filter.php (or any filename as you wish). Code this in a new page!

```
<?php
$str = "<h3>Hello World!</h3>";
$int = 0;
$float = 100.09;
$ip = "127.0.0.1";
$url1 = "www.google.com";
$url2 = "https://www.google.com";

echo "<p>Before Sanitizing and Validating: </p>";
echo "<p> str = ".$str."</p>";
echo "<p> int = ".$int."</p>";
echo "<p> float = ".$float."</p>";
echo "<p> ip = ".$ip."</p>";
echo "<p> url1 = ".$url1."</p>";
echo "<p> url2 = ".$url2."</p>";

echo "<p>Applying Sanitizing and Validating Filters: </p>";
$str = filter_var($str,FILTER_SANITIZE_STRING);
echo "<p> str = ". $str . "</p>";
if(filter_var($int, FILTER_VALIDATE_INT) === 0){
  echo "<p> int = ".filter_var($int, FILTER_VALIDATE_INT)."</p>";
}
if(!filter_var($float, FILTER_VALIDATE_INT)){
  echo "<p>float is not an integer</p>";
}
if(filter_var($ip, FILTER_VALIDATE_IP)){
  echo "<p>ip - Valid IP address</p>";
}
$url1 = filter_var($url1,FILTER_SANITIZE_URL);
echo "<p> url after sanitizing = ".$url1."</p>";
$url1 = filter_var($url1,FILTER_VALIDATE_URL);
echo "<p> url after validating = ".$url1."</p>";
$url2 = filter_var($url2,FILTER_SANITIZE_URL);
echo "<p> url after sanitizing = ".$url2."</p>";
$url2 = filter_var($url2,FILTER_VALIDATE_URL);
echo "<p> url after validating = ".$url2."</p>";
?>
```

On execution, we get the output as:

![5-3-1](Images/image00259.jpeg)

*   When we print $str with html tag, html is applied on printing. When we sanitize the string, it removes the html tag and prints the string alone.
*   When we check integer for value 0, we ought to do with if condition. Similarly, we use same filter to validate integer with float input
*   $url1 and $url2 are the same URLs for users. But only $url2 is validated and gets printed. Though we don't sanitize the urls here, we can see the difference for validation done on $url1 and $url2

We will look on to a validation example of integer within some range.

```
<?php
$int1 = 50;
$int2 = 150;
echo "<p> int1 = ".$int1." int2 = ".$int2."</p>";

if (filter_var($int1, FILTER_VALIDATE_INT, array("options" => array("min_range"=>1, "max_range"=>100))) ) {
   echo "<p>int1 value is within 1-100</p>";
} 
else {
   echo "<p>int1 value is not within 1-100</p>";
}

if (filter_var($int2, FILTER_VALIDATE_INT, array("options" => array("min_range"=>1, "max_range"=>100))) ) {
   echo "<p>int2 value is within 1-100</p>";
} 
else {
   echo "<p>int2 value is not within 1-100</p>";
}
?>
```

![5-3-2](Images/image00260.jpeg)

Similarly, we should make use of these filters to sanitize and validate user data.

* * *

### 5.4 Handling JSON Data

* * *

JSON stands for JavaScript Object Notation. It is a syntax used for storing and exchanging data.

Since the JSON format is a text-based format, it can easily be sent to and from a server, and used as a data format by any programming language.

So, we will learn how to handle JSON data using PHP in this section.

We have 2 built-in functions to handle JSON.

*   json\_encode() - to encode a value to JSON format
*   json\_decode() - to decode a JSON object into a PHP object or an associative array.

Since many of you would be new to JSON, we will do this:

*   Practise an example to convert an associative array to JSON format
*   Use the output JSON data and decode back to array

**Practice:**

**Convert Array to JSON:**

```
<?php
$array = array("Test1" => 75, "Test2" => 80, "Test3" => 60);
echo "Array: ";
var_dump($array);
echo "<p>JSON format: </p>";
echo json_encode($array);
?>
```

![5-4-1](Images/image00261.jpeg)

**Convert JSON to Array:**

```
<?php
$json = '{"Test1":75,"Test2":80,"Test3":60}';
echo "<p> JSON format: ".$json."</p>";
echo "<p>JSON Decode: </p>";
var_dump(json_decode($json));
echo "<p>JSON Decode To Array: </p>";
var_dump(json_decode($json,true));
?>
```

The json\_decode() function returns an object by default. The json\_decode() function has a second parameter and when set to true, JSON objects are decoded into associative arrays.

![5-4-2](Images/image00262.jpeg)

Do you remember Object data type from Chapter-2? You can consider this resulting object as an object data type.

Since an object is returned as a result of decode, we can access the decoded values individually.

We can access via 2 ways: object and array. Let us see this through an example code snippet:

```
<?php
$json = '{"Test1":75,"Test2":80,"Test3":60}';
echo "<p> JSON format: ".$json."</p>";
echo "<p>JSON Decode: </p>";
var_dump(json_decode($json));
echo "<p>JSON Decode To Array: </p>";
var_dump(json_decode($json,true));

$array = json_decode($json,true);
$object = json_decode($json);

echo "<p>Accessing via Array: </p>";
echo "Test1 = ".$array["Test1"];
echo "<p>Accessing via Object: </p>";
echo "Test2 = ".$object->Test2;

echo "<p>Using Loops</p>";
foreach ($array as $key => $value) {
  echo $key." - ".$value."<br>";
}
?>
```

I have just added retrieving lines to the previous coding snippet.

![5-4-3](Images/image00263.jpeg)

With this, we come to an end of this chapter!

The learning and practising sessions of PHP would have provided hands-on experience to you.

The rest of the e-book is about implementing those concepts using a web application.

* * *

# Chapter 6: Designing a Web Application

* * *

*   [](#part0036.xhtml)
    
    #### 6.1 Project Outline
    
*   [](#part0037.xhtml)
    
    #### 6.2 Database Design
    
*   [](#part0038.xhtml)
    
    #### 6.3 Setting up Environment
    
*   [](#part0039.xhtml)
    
    #### 6.4 Setting up Database Tables
    
*   [](#part0040.xhtml)
    
    #### 6.5 Web Application Template
    

* * *

### 6.1 Project Outline

* * *

In the upcoming chapters, we will develop a small web application. By means of developing the application, we will learn how to connect an application to database and produce dynamic content for users.

We will term the project as Online Course System!

**What is an online course system?**

In an online course system, there will be courses from various topics that are authored by instructors and uploaded in the website. Learners have to sign up to the site and enrol to the course in order to access the contents. An automatic record of the learners' learning progress will be done and made available as a report to the instructor.

We will try to do it as simple as possible without complicating anything. The reason is, we are learning how to develop php pages as an application and connect them to database for data processing.

**What processes are necessary for this application?**

We broadly have 2 users - instructor and learner:

![6-1-tasks](Images/image00264.jpeg)

The above is an outline of the main tasks/processes. It does not mean you are restricted to these tasks alone. You can extend and include as many as you want as to your need. These tasks alone will be dealt in this e-book.

**Flow of Project:**

There are 3 pages in menu: Home, Courses and Login

*   In Home Page, we will present project information, list courses with number of enrolment and list of instructors registered.
    
*   In Courses Page, we will provide search facility to find courses.
    
    *   Search results page from searching the courses
    *   Course details page from search results links
*   In Login Page, we will provide login form and a link to register to the website.
    
    *   Registration Page from the link in login page.
    *   User dashboard page after login
    *   Change profile link
    *   Create course & content for instructors
    *   Enrol & access course for learners
    *   Learners' progress report for instructors

As an instructor,

*   You need to sign up
*   You need to login
*   You need to create a course and provide details
*   You need to upload content to course as files
*   You can view list of enrolled learners and their progress
*   You can modify your profile

As a learner,

*   You need to search a course
*   Your search results will be a list of course topics as links
*   You will browse the link and find details about course like eligibility and outcomes
*   You need to enrol
*   You need to browse course contents and those learning activities will be recorded
*   A progress bar will notify how much you have completed
*   You can modify your profile

Hope from here, it is going to be complete hands-on with little to learn and more to practise!

Happy learning and coding!

* * *

### 6.2 Database Design

* * *

In this section, I will provide you the data dictionary of the database we are about to use for this project.

**Data Dictionary:**

![6-2-1-instructor](Images/image00265.jpeg)

![6-2-2-courses](Images/image00266.jpeg)

![6-2-3-content](Images/image00267.jpeg)

![6-2-4-learner](Images/image00268.jpeg)

![6-2-5-enroll](Images/image00269.jpeg)

![6-2-6-record](Images/image00270.jpeg)

![6-2-7-login](Images/image00271.jpeg)

This is the simplest of database design! A good database should hold only mandatory details. Details that are needed to be derived from existing fields if possible, are usually not placed inside the database.

* * *

### 6.3 Setting up Environment

* * *

Requirements needed for this web application:

*   Apache Server
*   PHP
*   MySQL

We have already installed the XAMPP stack for this purpose!

Let me remind:

XAMPP is installed in C:/xampp/htdocs

**Checklist:**

*   Make sure Apache is accessible via port 80. If you have changed the port, you need to execute pages as [http://localhost:port](#part0038.xhtml)where port is the newly changed port.
*   Make sure File\_uploads is enabled in php.ini file
*   Create database via phpMyAdmin

Let us create the required database from data dictionary.

**Accessing phpMyAdmin:**

*   In XAMPP, start both Apache and MySQL services. Hope MySQL will be running in port 3306.
*   Go to phpMyAdmin, that is, Browse to [http://localhost/](#part0038.xhtml) and choose phpMyAdmin from the top menu.  
    or  
    Click Admin button next to MySQL service in XAMPP control panel.

Once you access phpmyadmin successfully, you will end up like this:

![1-0-1](Images/image00272.jpeg)

I have just shown you a part of the screen.

On the left panel, you will have a list of databases. To the right of the above image, you will find database server details. Make sure, you get this page!

**Note:**

If you have not started MySQL service, you will end up like this:

![1-0-0](Images/image00273.jpeg)

Whenever I say, go to database or access phpmyadmin, you need to browse to [http://localhost/phpmyadmin](#part0038.xhtml)

**Steps to create database:**

1\. In the image below, click New:

![1-0-2](Images/image00274.jpeg)

2\. You will get a screen like this:

![1-0-3](Images/image00275.jpeg)

3\. Enter the database name as onlinecourse

![1-0-4](Images/image00276.jpeg)

4\. When creation process is successful, you will be taken to the next screen as below:

![1-0-5](Images/image00277.jpeg)

Thus, the database is created. We will create the tables in the next section.

* * *

### 6.4 Setting up Database Tables

* * *

We will create 7 tables one by one. I will explain how to create the first table in detail.

Once you create the database, you will automatically end up with create table option. If you have closed phpmyadmin accidently, Browse [http://localhost/phpmyadmin/](#part0039.xhtml) and click onlinecourse from the left panel.

1\. Enter table name as:

![6-4-1](Images/image00278.jpeg)

2\. At the right end, click Go

![6-4-2](Images/image00279.jpeg)

3\. When you click Go, you will be taken to:

![6-4-3](Images/image00280.jpeg)

4\. From the data dictionary, we have to enter the fields here, as below:

![6-4-4](Images/image00281.jpeg)

5\. When you choose Primary in Index field, a pop-up will appear as below. Just give Go and proceed.

![6-4-5](Images/image00282.jpeg)

6\. Once field entry is over, click Save.

![6-4-6](Images/image00283.jpeg)

7\. That’s all, the first table is ready!

**Table-1:** instructors

![6-4-7](Images/image00284.jpeg)

You can continue creating the second table from this screen or by clicking **New** under **onlinecourse** in the left panel.

8\. Click the table name instructors:

![6-4-8](Images/image00285.jpeg)

Click the Structure Tab next to Browse Tab

![6-4-9](Images/image00286.jpeg)

This gives you the complete structure of the table. So, from here, I will share the screenshots of the input fields and the above structure of every table. Make sure, you follow the steps and create tables successfully!

**Table-2:** courses

When you click New in left panel under onlinecourse database, you will directly get this page:

![6-4-10](Images/image00287.jpeg)

You can add number of columns and click Go (as marked) to increase the columns.

*   When you mark a field as A\_I (auto increment) it automatically sets the field as Primary Key.
*   When you mark a field as Unique in Index column, it shows a pop-up similar to Primary Key. Just do the same as we did to primary key pop-up.

![6-4-11](Images/image00288.jpeg)

When you Save the table, it will automatically take you to Structure tab as:

![6-4-12-table2](Images/image00289.jpeg)

**Table-3:** contents

*   We will store only path of the content in database. Files for content will be stored separately.
*   There is no need to explicitly mention a foreign key here. When we insert records in this table, our application does that.

![6-4-13](Images/image00290.jpeg)

![6-4-14-table3](Images/image00291.jpeg)

**Table-4:** learners

![6-4-15](Images/image00292.jpeg)

![6-4-16-table4](Images/image00293.jpeg)

**Table-5:**enroll

*   For this table, we will include a default value for learn\_start field called CURRENT\_TIMESTAMP which will automatically insert the current date when inserting a new record.
*   When you do this in servers, check for server timezone because MySQL inserts date/time in server timezone!

![6-4-17](Images/image00294.jpeg)

![6-4-18-table5](Images/image00295.jpeg)

**Table-6:** record

There is no primary key for this table. If you want, you can create a separate field, but be careful when you insert records, you have to include three values. I am avoiding primary key here because when a learner keeps completing content, an entry is inserted. During retrieval, we would pull details with learn\_mail field and content\_id field to know which learner completed what content.

![6-4-19](Images/image00296.jpeg)

![6-4-20-table6](Images/image00297.jpeg)

Since no primary key is defined, no index is created!

**Table-7:** userlogin

![6-4-21](Images/image00298.jpeg)

We will be storing the hash value of password, so we have given a higher length to that field.

![6-4-22-table7](Images/image00299.jpeg)

Finally, click onlinecourse in the left panel:

![6-4-23-alltables](Images/image00300.jpeg)

Thus, all the tables, necessary for the application, are created!

* * *

### 6.5 Web Application Template

* * *

This section will provide you a template to work with the application and the pages required to be designed.

**What is a template?**

It is a web page that is ready with the layout, fonts, images and other elements to be included. When you have the template ready, you can make sure that there is uniform design throughout the application (in all your web pages).

Why should I use a template?

Very simple, it gives uniform design to all the pages!

**Where should you place this template?**

Remember, we are working with xampp server.

Hope you have already created a folder **onlinecourse** in C:/xampp/htdocs.

*   If you have not done so far, create a folder named onlinecourse in C:/xampp/htdocs path. This is our project folder.
*   Create a new file index.php inside onlinecourse folder
*   Create a new folder named css, inside onlinecourse folder
*   Create a new file style.css inside css folder

**Files included:**

*   index.php
*   css folder - style.css

![1-1-0](Images/image00301.jpeg)

**Starter Code:**

You can the place the code snippet below, inside index.php file

```
<!-- index.php -->
<!DOCTYPE html>
<html>
<head>
<title> Template </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>

<main>
<section>
<h3>Welcome to Online Course System!</h3>
<p style='text-align:left;'>In this web application, we will develop user-friendly application to enroll to courses. We primarily have 2 major users for this application: </p>
<ul  style='text-align:left;'>
<li>Instructor - the one who develops course materials </li>
<li>Learner - the one who studies those developed course materials </li>
</ul>
<p style='text-align:left;'>
The instructors develop course materials and upload the same in this website. Once the course is published, they appear in the search list. The learners browse through the course list and sneek into every detail. nce they are 
comfortable with a course, they enroll into it. Once they enroll, they can view the course materials. A progress track will be there to specify how far they have completed the course. When progress reaches 100%, it marks the course to be completed.
</p>
<p>
For this application, we keep all courses free of cost!
</p>
</section>
<article class="artclass">
<div>
<h3>Courses with enrollments</h3>
<p>Course Name 1      Enrollment Nos</p> 
<p>Course Name 2      Enrollment Nos</p> 
<p>Course Name 3      Enrollment Nos</p> 
</div>
<div>
<h3>Instructors List</h3>
<p>Instructor 1</p> 
<p>Instructor 2</p> 
<p>Instructor 3</p> 
</div>
</article>
</main>

<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

You can the place the code snippet below, inside style.css file

```
/* style.css -  CSS coding */
body{
  margin: auto;
  width: 80%;
}
header{
  display: block;
  background-color: #DAF7A6;
  padding: 30px;
  text-align:center;
}
footer{
  display: block;
  background-color: #DAF7A6;
  padding: 10px;
  text-align:center;
}

/*Navigation */
nav ul{
  list-style: none;
  background-color: #8b9e68;
  text-align: center;
  padding: 0;
  margin: 0;
}
nav li{
  font-family: 'Oswald', sans-serif;
  font-size: 1.2em;
  line-height: 40px;
  height: 40px;
  border-bottom: 1px solid #888;
  padding: 0 20px;
}
nav a{
  text-decoration: none;
  color: #fff;
}
nav a:hover{
  color: #000;
}
button{
  width: 100%;
  margin: auto;
  display: block;
  background-color: #8b9e68;
  font-family: 'Oswald', sans-serif;
  font-size: 1.2em;
  line-height: 40px;
  height: 40px;
  border-bottom: 1px solid #888;
  padding: 0 20px;
}
 
/* Main Content */
section{
  padding: 20px 0;
  text-align:center;
  border-bottom: 1px solid #8b9e68;
}
.imgclass{
  display: inline-block;
  border: 1px solid #000;
  width: 150px;
  height: 150px;
}
article{
  padding: 10px 0;
}
input,select,textarea{
  width:90%;
  display:block;
  margin:0 auto;
}
.frmbtn{
  background-color:#8b9e68;
  cursor: pointer;
  color: white;
}
.frmbtn:hover{
  color:black;
}

/*Responsive Design */
@media screen and (min-width: 600px){
  .artclass div {
    display: inline-block;
    text-align: left;
    width: 48%; 
  }
  nav li {
    width: 120px;
    border-bottom: none;
    height: 50px;
    line-height: 50px;
    font-size: 1.4em;
	display: inline-block;  
  }	
  button{
    display: none;
  }  
  form{
    display:inline-block;
  }
  input,select,textarea{
	padding:10px 20px;
    margin:8px 0;
    display:inline-block;
    border:1px solid #ccc;
    border-radius:4px;
    box-sizing:border-box;
  }
}
```

Let us check our template!

Browsing [http://localhost/onlinecourse/](#part0040.xhtml) should automatically open the index.php file contents.

![1-1-1](Images/image00302.jpeg)

Remember, we have not included any images for this project.

How to include templates on your own?

It is not necessary that you should stick to this template. You can search using key phrases like web template for free, free html templates, free php templates, etc.

Once you find a template, just start working as we do here. If you have a html template with index.html file, just rename the file as index.php and continue working.

Hope the home page is ready. Make sure you stick to this same template for the rest of the project.

Instead of designing forms separately and including php code separately, we will do a combined work so that you can be clear on: 'which form does what work' in a better way.

* * *

# Chapter 7: Interacting with MySQL Database

* * *

*   [](#part0042.xhtml)
    
    #### 7.1 Connecting to Database
    
*   [](#part0043.xhtml)
    
    #### 7.2 Inserting Data - I
    
*   [](#part0044.xhtml)
    
    #### 7.3 Inserting Data - II
    
*   [](#part0045.xhtml)
    
    #### 7.4 Retrieving Data - I
    
*   [](#part0047.xhtml)
    
    #### 7.5 Retrieving Data - II
    
*   [](#part0046.xhtml)
    
    #### 7.6 Updating Data
    
*   [](#part0048.xhtml)
    
    #### 7.7 Deleting Data
    

* * *

### 7.1 Connecting to Database

* * *

There are three ways to work with PHP and MySQL Database

*   MySQLi (Procedural)
*   MySQLi (Object-oriented)
*   PDO

The MySQLi ways work with MySQL database systems while PDO works with 12 database systems.

In this e-book, we will go with the MySQLi Procedural method. It would be the apt method for learning purpose.

Basically to work with a database, you need to establish connection. So, the first thing we will learn here is to establish a connection.

**Syntax:**

```
mysqli_connect($servername, $username, $password, $database);
```

*   $servername is the name of the host
*   $username - username to connect to the database
*   $password - password to connect to the database
*   $database - the name of the database to be connected

Let us see whether we have values for those parameters:

*   $servername is the hostname. Currently we are running the application from the local server. The host name is localhost. So, the value of $servername = localhost.
*   $database has the value onlinecourse (the database created in phpmyadmin)

Usually, when xampp installation takes place, root is the username with no password.

We cannot use this as it is. In order to secure our database in the servers, we have to follow the procedure of creating an username and password just for the onlinecourse database.

**How to create username and password for database?**

Let us get back to phpmyadmin.

1\. Access phpMyAdmin in your browser ([http://localhost/phpmyadmin](#part0042.xhtml))

2\. Go to User Accounts Tab

![7-1-1](Images/image00303.jpeg)

3\. There are user accounts already created for the root user. Click Add user account

![7-1-2](Images/image00304.jpeg)

4\. Give the following details in the next screen:

Username: ocuser

Hostname: localhost

Password & Re-type: Pass@OC20

![7-1-3](Images/image00305.jpeg)

5\. Click Go in the right bottom corner. You will get the screen below:

![7-1-4](Images/image00306.jpeg)

6\. Go the Database Tab next to Global

![7-1-5](Images/image00307.jpeg)

7\. Select onlinecourse from the list. You will be taken to:

![7-1-6](Images/image00308.jpeg)

8\. Check all privileges. Click Go and you will be taken to:

![7-1-7](Images/image00309.jpeg)

A user account (username and password) is created and mapped to onlinecourse database. The corresponding SQL syntax is generated on execution of every command.

**Check if privileges are granted:**

*   Click Home icon in the left panel -> Go to User Accounts
*   Check whether the Grant field has Yes against *ocuser*.

![7-1-8](Images/image00310.jpeg)

*   If Grant field has No, just click Edit privileges, check all privileges and then click Go. Come back and check here, it should turn Yes.

**Note:** Without Grant turning Yes, you cannot establish connection to the database from the application.

Now, back to connection syntax:

So, we have all 4 parameters now.

Create a new file named connect.php in onlinecourse folder (C:/xampp/htdocs/onlinecourse). Use the following code:

```
<?php
$host = "localhost";
$username = "ocuser";
$password = "Pass@OC20";
$database = "onlinecourse";
$con = mysqli_connect($host,$username,$password,$database);
if (!$con) {
  die("Connection failed: " . mysqli_connect_error());
}
else {
  echo "Database connected";
}
?>
```

**Explanation:**

We have created 4 variables to hold those 4 parameter values. We pass them via mysqli\_connect() built-in function and we store the result of the connection in $con variable. $con is a resource type variable.

If the database is not connected, it will display the if statement. If it is connected, it will display the else statement.

Why have I reversed the condition in if-else?

The reason is: we would not need the else part anywhere. Just for the purpose of checking, we use echo statement in the else part.

Execute the page using [http://localhost/onlinecourse/connect.php](#part0042.xhtml)

![7-1-9](Images/image00311.jpeg)

Possible Errors:

1\. You might be denied connection, if your password is not matching with what is entered in phpmyadmin

2\. Check for all spelling errors

Now, it’s time to remove the else part of the connection code. Let us keep it as:

```
connect.php
<?php
$host = "localhost";
$username = "ocuser";
$password = "Pass@OC20";
$database = "onlinecourse";
$con = mysqli_connect($host,$username,$password,$database);
if (!$con) {
  die("Connection failed: " . mysqli_connect_error());
}
?>
```

Hereafter, only when there is an error in establishing connection, error message will be produced.

**Closing the connection:**

The connection is closed when the script ends. If at all you want to manually close the database connection, just use:

```
mysqli_close($con);
```

It is a good practice to close the connection. But we may not use this function in our application.

**Execution of Queries:**

When working with the database, the first primary step is to establish connection. Once connected, we can use SQL commands in MySQLi procedural functions.

There is a common syntax for executing queries:

```
mysqli_query($database_connection,$query_string);
```

There are 2 parameters:

*   $database\_connection is the resource variable $con (the one we used to connect to the database)
*   $query\_string is the string containing the SQL statements

For making a query in a string, we ought to follow this:

*   The SQL query must be quoted in PHP
*   String values inside the SQL query must be quoted
*   Numeric values must not be quoted
*   The word NULL must not be quoted

That means, if we use double quotes for enclosing SQL string, for string values, we will use single quotes. When we code in practice session, we will clearly understand this.

In the subsequent sections, we will learn to manipulate data - insert / select / update/ delete data in the application specific forms.

* * *

### 7.2 Inserting Data - I

* * *

There are 3 forms to insert data from user:

1\. Registration (instructor / learner)

2\. New Course

3\. Upload Content

In registration, we will get input from user. In new course and upload content, instructor provides values for fields. These 3 forms will now be designed and used for learning inserting data statements.

First, let me start with Registration form. We will use a single registration form and provide appropriate fields to find whether they are instructor or learner.

**Practice:**

1\. If you have kept index.php open in a text editor, choose Save as option and save it as **register.php** inside the onlinecourse folder

2\. When you save it, your onlinecourse folder should have 2 files: index.php and register.php

Alternative:

If you are uncomfortable with the above process, then:

*   create a new file called register.php inside onlinecourse folder.
*   copy contents from index.php to register.php and save them.

**Form Design: register.php**

1\. Change the title tag content as User Registration

2\. Remove the contents between main tags.

3\. Replace with the following code:

```
<main>
<section>
<h3> User Registration </h3>
<p>
<form method="post" name="frmregister">
<p><select name="txtusercategory">
<option value="">Who are you?</option>
<option value="learner">Learner</option>
<option value="instructor">Instructor</option>
</select></p>
<p><input type="email" name="txtmail" size="40" placeholder="Enter your Email Address" required></p>
<p><input type="password" name="txtpwd" size="40" placeholder="Enter your Password 8-15 characters" required></p>
<p><input type="text" name="txtname"  size="40" placeholder="Enter you Full Name" required></p>
<p><textarea name="txtdetails" cols="40" placeholder="Enter your details" required></textarea></p>
<p><input type="submit" name="register" value="Register" class="frmbtn"></p>
</form>
</p>
</section>
</main>
```

4\. Execute [http://localhost/onlinecourse/register.php](#part0043.xhtml)

![7-2-1](Images/image00312.jpeg)

**Insert Data: register.php**

In the beginning of the file, above the html declaration line, we will include the insert code:

```
<?php
require('connect.php');

if(isset($_POST['register'])){
  $category = $_POST['txtusercategory'];
  $usermail = $_POST['txtmail'];
  $userpwd = $_POST['txtpwd'];
  $name = $_POST['txtname'];
  $details = $_POST['txtdetails'];
  
  if((strlen($userpwd) > 7) && strlen($userpwd < 16)){
    $userpwd = password_hash($userpwd, PASSWORD_DEFAULT);
    $insert1 = "INSERT INTO userlogin VALUES ('$usernmail','$userpwd','$category')";
    if($category == 'learner'){
       $insert2 = "INSERT INTO learners VALUES ('$usermail','$name','$details')";
    }
    if($category == 'instructor'){
       $insert2 = "INSERT INTO instructors VALUES ('$usermail','$name','$details')";
    }
    $check_insert1 = mysqli_query($con,$insert1);
    $check_insert2 = mysqli_query($con,$insert2);
    if($check_insert1 and $check_insert2){
       echo "<script>alert('Registration successful!');</script>";
    }
    else{
       echo "<script>alert('Sorry! Try again!');</script>";
    }
  }
  else{
    echo "<script>alert('Password should be between 8-15 characters');</script>";
  }
}
?>
```

Let me explain line by line:

```
require('connect.php');
```

We connect to the database in connect.php file. So we include the connect file for this page.

```
if(isset($_POST['register'])){ }
```

The complete set of php code works only when register button is pressed.

```
$category = $_POST['txtusercategory'];
$usermail = $_POST['txtmail'];
$userpwd = $_POST['txtpwd'];
$name = $_POST['txtname'];
$details = $_POST['txtdetails'];
```

We copy the values submitted in the form to variables

```
if((strlen($userpwd) > 7) && strlen($userpwd < 16)){
}
else{
  echo "<script>alert('Password should be between 8-15 characters');</script>";
}
```

Here, we check if password is between 8 and 15 characters by imposing 2 conditions checking if length is greater than 7 and less than 16. If the length does not fall between 8 and 15, it prints a message and skips registration. If the length is between 8-15, it proceeds inside the if block.

```
$userpwd = password_hash($userpwd, PASSWORD_DEFAULT);
```

It is a sin to store the password as it is, in the database. So, we create a hash using password\_hash() function.

```
$insert1 = "INSERT INTO userlogin VALUES ('$usermail','$userpwd','$category')";
if($category == 'learner'){
  $insert2 = "INSERT INTO learners VALUES ('$usermail','$name','$details')";
}
if($category == 'instructor'){
  $insert2 = "INSERT INTO instructors VALUES ('$usermail','$name','$details')";
}
```

During registration, we have to insert data into 2 tables. One table is either instructor or login, the other table is userlogin which stores login details and user category data.  
$insert1 statement has the query string for userlogin table.  
Based on the category, $insert2 statement will be used. Hope you can see how double quotes are used for query string and single quotes are used for string values.

```
$check_insert1 = mysqli_query($con,$insert1);
$check_insert2 = mysqli_query($con,$insert2);
if($check_insert1 and $check_insert2){
  echo "<script>alert('Registration successful!');</script>";
}
else{
  echo "<script>alert('Sorry! Try again!');</script>";
}
```

Here, we execute mysqli\_query() function for 2 insert statements. Hope you remember the syntax for executing queries from the previous section.  
$check\_insert1 and $check\_insert2 will either hold true (if the query is executed) or false (if query is not executed). If both the statements are executed and their values are true, we print a message on successful registration. If either of them fail, we ask the users to try again.

```
<script>alert();</script>
```

Script tag is included in the echo statement. It means content inside the script tag is javascript code. This alert() function in JS will display a pop-up with some message. We try to inform the user what kind of action takes places through a pop-up instead of printing the message on the page.

One more thing! This is not the only way to carry out insert process. What stays the same is the mysqli\_query() function. The way we carry out can differ in many ways like:

*   We can insert data into instructor / learner table first, if successful we can insert data to userlogin table
*   In case one table data is inserted and the other fails, we can issue commands to reverse the inserted data by issuing a delete command.
*   Not only password, all the other fields can also be validated before inserting data.

All these factors depend on the one who develops the application and the conditions depend on what sort of application is developed.

Here my intention is to teach how to insert data and how to make registration process through that statement. I do not validate all other fields since I have provided required attribute and type attribute accordingly in the HTML code.

Ok, shall we execute this page? Let me sign up as an instructor!

Execute [http://localhost/register.php](#part0043.xhtml) and enter details as:

*   Category: Instructor
*   Email: [instructor1@onlinecourse.com](#part0043.xhtml)
*   Password: password
*   Name: Instructor 1
*   Details: I wish to develop programming courses

When you click register, you will get a pop-up as below:

![7-2-4](Images/image00313.jpeg)

Press OK and close the pop-up, you will get the page as it is! Where should I go after registration? This work will be done in the next chapter!

In case, you get some error:

*   Go to phpmyadmin and check if any of the tables instructor or userlogin has a record entry.
*   If yes, delete them, correct your error and execute again!
*   If not, correct your error and execute again!
*   Since we are executing in localhost, the errors will be listed on the top of the page automatically.

**Looking into MySQL:**

Go to phpmyadmin and select instructors table from onlinecourse database:

![7-2-5](Images/image00314.jpeg)

Now, select userlogin table and look how the password hash is formed:

![7-2-6](Images/image00315.jpeg)

Hope you are clear how to insert data into a table!

* * *

### 7.3 Inserting Data - II

* * *

Shall we proceed designing the other forms discussed in the beginning of the chapter?

Either create a file named **newcourse.php** or use save as on index.php and save it as newcourse.php. We will now create

**Form Design: newcourse.php**

Change the title tag content as New Course and replace the main element as:

```
<main>
<section>
<h3> New Course Details </h3>
<p>
<form method="post" name="frmnewcourse">
<p><input type="text" name="txtcourse" size="60" placeholder="Enter your Course Title" required></p>
<input type='hidden' name='txtinstruct' value='instructor1@onlinecourse.com'>
<p><textarea name="txtdesc" cols="60" placeholder="Enter Course Description Details" required></textarea></p>
<p><textarea name="txtoutcome" cols="60" placeholder="Enter Course Outcomes separated by commas" required></textarea></p>
<p><textarea name="txteligible" cols="60" placeholder="Enter Eligibility Details separated by commas " required></textarea></p>
<p><input type="submit" name="newcourse" value="Create Course" class="frmbtn"></p>
</form>
</p>
</section>
</main>
```

![7-3-1](Images/image00316.jpeg)

We have placed a hidden field for instructor id. Right now, we have only one instructor, so we have directly specified the value. When binding these forms in the application, the value will be taken from the previous page. Those details will be dealt later.

**Insert Data: newcourse.php**

This time, we are inserting data with an auto increment field called course\_code. Since it is an auto incrementing field, whenever a record is inserted, a count is increased. If we provide NULL as value, it will automatically count the existing records and add plus one to the count. Say, if it's first record, first course will have 1, when it's second course, second course will have 2 as course code.

```
<?php
require('connect.php');
if(isset($_POST['newcourse'])){
 $title = $_POST['txtcourse'];
 $instruct = $_POST['txtinstruct'];
 $outcome = $_POST['txtoutcome'];
 $eligible = $_POST['txteligible'];
 $insert = mysqli_query($con,"INSERT INTO courses VALUES (NULL,'$title','$instruct','$describe','$outcome','$eligible')"); if($insert){
 echo "<script>alert('New Course created!');</script>";
}
else {
 echo "<script>alert('Sorry, try again!');</script>";
}
?>
```

I don't wish to bore you with same type of explanation as done in the previous section.

Let me give you the glimpse of what the code does. Try learning it in the same way it was done for the previous form.

*   We pass the submitted values to the variables
*   Instead of assigning a variable to query, we have directly placed the query in mysqli\_query() function.
*   As usual, when insertion is successful, we print a positive message, else we print a message asking to try again.

The reason why I chose explaining the register form was to mention how to place validations, how to print false condition messages, how to create hashed password, etc. This form is very straight forward to do an insert operation as simple as it is.

Executing [http://localhost/onlinecourse/newcourse.php](#part0044.xhtml) give the following input:

![7-3-2](Images/image00317.jpeg)

You will receive a pop-up as:

![7-3-3](Images/image00318.jpeg)

Shall we check in the database? Access phpmyadmin and select courses table:

![7-3-4](Images/image00319.jpeg)

Hope this form is also done now!

* * *

We will now get into designing the upload content form.

Create a new file called **uploadcontent.php** or save the previous file in this name using save as option.

**Form Design: uploadcontent.php**

Change the title tag content as Upload Content and replace the main element as:

```
<main>
<section>
<h3> Add Content to Course </h3>
<p>
<form method="post" name="frmnewcontent" enctype="multipart/form-data">
<p><input type="text" name="txtcontent" size="60" placeholder="Enter Content Title" required></p>
<input type='hidden' name='txtcourse' value='1'>
<p>Allowed extensions: txt, rtf, doc, docx, pdf, ppt, pptx, mp4
<input type="file" name="txtfile" id="txtfile" required></p>
<p><input type="submit" name="upload" value="Upload" class="frmbtn"></p>
</form>
</p>
</section>
</main>
```

![7-3-5](Images/image00320.jpeg)

We have a hidden field to carry the course code details. Right now, we have one course inserted and the course code is 1. So, we directly provide the value through this form.

**Insert Data: uploadcontent.php**

We will include $\_FILES\[\] variable for uploading process. We will not store the file in the database, we will store files in the server (onlinecourse folder in our case) and the file path alone in the database.

```
<?php
require('connect.php');
if(isset($_POST['upload'])){
 $title = $_POST['txtcontent'];
 $course = $_POST['txtcourse']’
 $filename = $_FILES['txtfile']['name'];
 $filetmp =$_FILES['txtfile']['tmp_name'];
 $filestring = explode('.',$_FILES['txtfile']['name']);
 $file_ext= strtolower(end($filestring));
 $exts = array('txt','rtf','doc','docx','pdf','ppt','pptx','mp4');
 if(in_array($file_ext,$exts)===false){
   echo "<script>alert('You can upload only txt, rtf, doc, docx, pdf, ppt, pptx, mp4 files');</script>";
 }
 else{
   $newpath = 'uploads/';
   if (!is_dir($newpath)) {
      mkdir($newpath, 0777, true);
   }
   $filepath = $newpath.strtotime("now").'.'.$file_ext;
   move_uploaded_file($filetmp,$filepath); 
   $insert = mysqli_query($con,"INSERT INTO contents VALUES (NULL,  '$title', $course, '$filepath')");
   if($insert){
      echo "<script>alert('Content Uploaded successfully!');</script>";
   }
   else{
      echo "<script>alert('Something went wrong, Try again!');</script>";
   }
  } 
}
?>
```

Let me explain the file upload part:

```
$filename = $_FILES['txtfile']['name'];
$filetmp =$_FILES['txtfile']['tmp_name'];
```

These lines will extract the file name of the uploaded file and the temporary location where it is stored.

```
$filestring = explode('.',$_FILES['txtfile']['name']);
$file_ext= strtolower(end($filestring));
```

We split the file name with the string ‘dot’ and find the extension of the file.

```
$exts = array('txt','rtf','doc','docx','pdf','ppt','pptx','mp4');
if(in_array($file_ext,$exts)===false){ 
	echo "<script>alert('You can upload only txt, rtf, doc, docx, pdf, ppt, pptx, mp4 files');</script>";
}
else{ }
```

We define an array variable $exts with the allowed extensions. We compare the extracted extension to the elements (extensions) in the array using in\_array() function. If the extension is not allowed, we print a message as a pop-up. If the extension is allowed, the else part works.

```
$newpath = 'uploads/';
if (!is_dir($newpath)) {
  mkdir($newpath, 0777, true);
}
```

We store the files in uploads folder inside onlinecourse folder. But do we have such folder? No! So, we check if such a folder exists using is\_dir() function. If it does not exist, it creates a folder **uploads** with permissions to place contents inside.

```
$filepath = $newpath.strtotime("now").'.'.$file_ext;
move_uploaded_file($filetmp,$filepath);
```

Here, we try to rename the file as a string of uploaded time. This avoids files with same names from being overwritten. We find string value of the current time and add the appropriate extension from $file\_ext variable. The new file path will be uploads/time\_in\_string\_format.extension. We move the file from temporary location to the new path.

```
$insert = mysqli_query($con,"INSERT INTO contents VALUES (NULL,  '$title', $course , '$filepath')");
if($insert){
  echo "<script>alert('Content Uploaded successfully!');</script>";
}
else{
  echo "<script>alert('Something went wrong, Try again!');</script>";
}
```

We insert the path of the file to the database. The third value of the insert statement is 1, which is an integer. So, we have not placed any quotes.

Before executing this file, we need to:

*   Create few files with txt, rtf, doc, docx, pdf, ppt, pptx and mp4 extensions.
*   Do not place the files in htdocs. Keep it somewhere else (like Desktop).

After execution, you can:

*   Try uploading one of these files
*   Try uploading some images because their extensions are not allowed and check whether pop-up is displayed with message
*   Go to C:/xampp/htdocs/onlinecourse and check if uploads folder is created
*   Also check if the uploaded files are existing and the contents are still the same

**Note:** You can upload only one file at a time

Executing [http://localhost/onlinecourse/uploadcontent.php](#part0044.xhtml)

![7-3-6](Images/image00321.jpeg)

![7-3-7](Images/image00322.jpeg)

I have uploaded file1.txt and file2.docx. Now let me show you uploads folder:

![7-3-8](Images/image00323.jpeg)

Can you see the names of those files? They are perfectly renamed! Shall we check the database?

![7-3-9](Images/image00324.jpeg)

**Note:**  
We have used the same code of Chapter 4.5 (File Upload) with few modifications according to the application.

I think we have completed insertion statements. We will move on to the next section.

* * *

### 7.4 Retrieving Data - I

* * *

Whatever content we insert, in some way or the other, we have to retrieve them. We will display courses on the courses page of menu.

You can either resave index.php as courses.php or create the file with this name and copy the contents. Change the title tag content as Courses.

What will we do?

1\. Display Courses (this section's task)

*   Select all records from courses
*   Display them in neat manner

2\. Search Courses (next section's task)

*   Provide a search box and search button to search
*   Filter records based on search phrases

Shall we start?

**Display courses:**

From here, our php code appears in between html tags, so make sure you correctly place the coding snippet.

Replace the head tag element with the code below:

```
<head>
<title> Courses </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
.cl{
margin: 5px;
display: inline-block;
vertical-align: top;
width: 300px;
height: 150px;border: 1px solid #ccc;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
 if($(window).width() > 600)
  $("ul").show();
  else
  $("ul").hide();
 $("button").click(function(){
  $("ul").slideToggle();
 });
});
</script>
</head>
```

We have included a style tag to provide appropriate space for the courses to appear. The style tag specifies the class element *cl* will have a border with 300px width, 150px height and displayed consecutively in a wider screen.

Replace the main tag element with the code below:

```
<main>
<section>
<h3>Courses</h3>
<?php
require('connect.php');
$query = "SELECT * FROM courses";
$select_courses = mysqli_query($con,$query);
while($selected = mysqli_fetch_row($select_courses)){
 echo "<div class='cl'>";
 echo "<h4><a href='details.php?search=$selected[0]'>".$selected[1]."<a/></h4>";
 echo "<p>".$selected[3]."</p>";
 echo "</div>";
}
?>
</section>
</main>
```

Let me explain the retrieval process:

```
$query = "SELECT * FROM courses";
$select_courses = mysqli_query($con,$query);
```

\>

This is the actual retrieval statement via query. $select\_courses is a resource type variable which will hold the table data.

```
while($selected = mysqli_fetch_row($select_courses)){ }
```

This while loop is used to iterate through the rows in the table. mysqli\_fetch\_row() will pass row by row (that is, record by record) data to the $selected variable from the $select\_courses variable which has all the records.

```
echo "<div class='cl'>";
echo "<h4><a href='details.php?search=$selected[0]'>".$selected[1]."<a/></h4>";
echo "<p>".$selected[3]."</p>";
echo "</div>";
```

$select\_courses variable holds all the retrieved records. $selected variable holds an array of fields from one record at a time. Each field can be accessed by an index number.

*   course\_code field will be 0, course\_title field will be 1. So, in $selected\[1\], we have the course title. We display the title in heading h4 format.
*   $selected\[3\] holds the course\_description field. So, we display it in a paragraph.
*   We enclose these 2 statements inside a div tag with class named cl. This cl class was defined in the style tag. It means, 2 fields namely course title and course description are displayed to the user inside the cl styled div tag.

```
<a href='details.php?search=$selected[0]'>".$selected[1]."<a/>
```

We have to understand this line in specific. The course title is provided as a link. The statement search=$selected\[0\] is the parameter passed through this page. This parameter can be accessed in 2 ways:

$\_GET\['search'\] or $\_REQUEST\['search'\]

This will pass the course code value of the displayed course title without a form. After execution, try placing your mouse over the title, you can find the link with the search value.

Before execution, let us create one more course so that we can know how cl styled div tag works.

*   Go to [http://localhost/onlinecourse/newcourse.php](#part0045.xhtml)
*   Place the values in the fields: 
    *   Title: Course 2
    *   Description: Description for course 2 is provided here. This course will be useful to enable search and find feature in the courses page.
    *   Outcome: Helps finding courses, Helps searching courses, Helps filtering courses
    *   Eligibility: Anyone can search, Only registered can enrol.

Now, execute the courses page. You can execute in 2 ways:

Go to [http://localhost/onlinecourse](#part0045.xhtml) and click Courses menu

OR

Directly fetch [http://localhost/onlinecourse/courses.php](#part0045.xhtml)

![7-4-1](Images/image00325.jpeg)

Now, you can see how these two div tags are created and placed. Place your mouse (do not click) over the course title. Left bottom corner you will find the url with the search value.

*   When you hover on Course Name 1, the url will be [http://localhost/onlinecourse/display.php?search=1](#part0045.xhtml)
*   When you hover on Course 2, the url will be [http://localhost/onlinecourse/display.php?search=2](#part0045.xhtml)

We have one more task here, when you click the link, the details have to be displayed. We will display the details in the same page when you click the link.

Shall we add some more code?

Use save as or create a file named **details.php**. As usual, replace the main element with the following code:

```
<main>
<section style="text-align:left;padding: 0 30px;">
<h3>Course Details</h3>
<?php
require('connect.php');
if(isset($_REQUEST['search'])){
 $search = $_REQUEST['search'];
}
$query = "SELECT * FROM courses WHERE course_code = $search";
$select_courses = mysqli_query($con,$query);
if($selected = mysqli_fetch_row($select_courses)){
 echo "<h4>".$selected[1]."</h4>";
 echo "<h5> Instructor: ";
 $find_instructor = mysqli_query($con,"SELECT instruct_name FROM instructors WHERE instruct_mail = '$selected[2]'");
 $found = mysqli_fetch_array($find_instructor);
 echo $found['instruct_name'];
 echo "</h5>";
 echo "<h5>Description:</h5>";
 echo "<p>".$selected[3]."</p>";
 echo "<h5>Outcomes:</h5>";
 $temp = explode(",",$selected[4]);
 echo "<ul>";
 foreach($temp as $t){
   echo "<li>".$t."</li>";
 } 
 echo "</ul>"; 
 echo "<h5>Eligibility:</h5>";
 $temp = explode(",",$selected[5]);
 echo "<ul>";
 foreach($temp as $t){
   echo "<li>".$t."</li>";
 } 
 echo "</ul>";
 echo "</div>";
}
?>
</section>
</main>
```

Let me explain and then you can execute:

```
if(isset($_REQUEST['search'])){
  $search = $_REQUEST['search'];
}
```

This part is used to retrieve the search value (course code) from the previous page <a> tag reference (search=$selected\[0\]).

```
$query = "SELECT * FROM courses WHERE course_code = $search";
$select_courses = mysqli_query($con,$query);
if($selected = mysqli_fetch_row($select_courses)){
	echo "<h4>".$selected[1]."</h4>";
```

We filter the query using the course\_code = $search condition. So, only one record will be selected. Instead of while, we will use the if() statement since only one record is displayed.

```
echo "<h5> Instructor: ";
$find_instructor = mysqli_query($con,"SELECT instruct_name FROM instructors WHERE instruct_mail = '$selected[2]'");
$found = mysqli_fetch_array($find_instructor);
echo $found['instruct_name'];
echo "</h5>";
```

We have displayed the instructor of the course here. Instructor id is stored in the course table. So, we frame a query to fetch instructor name using $selected\[2\] array element which holds the instructor id. This time, we fetch the details in an array using mysqli\_fetch\_array(). We treat it as an associative array and retrieve the field using the key - the name of the field in the table.

```
echo "<h5>Outcomes:</h5>";
$temp = explode(",",$selected[4]);
echo "<ul>";
foreach($temp as $t){
  echo "<li>".$t."</li>";
}
echo "</ul>";
```

This part is new for us, so we will cover this here.

*   explode will convert a string as string of arrays using a separator. We have already used this in uploading file for extracting file extension.
*   We have commas separated statements in outcomes and eligibility. So, using comma as separator, we convert the single string to array of strings.
*   Since $temp is an array, we use foreach loop to print the array element. We print them in an unordered list for neat appearance.

We use the same strategy for displaying eligibility too.

**How do we execute now?**

Go to [http://localhost/onlinecourse/courses.php](#part0045.xhtml) and click on Course Name 1:

![7-4-2](Images/image00326.jpeg)

Similarly, when you click Course 2, we will get the details of that course.

We have done the display course part of retrieval process. We are yet to include a search feature in the course page. Let us move to the next section.

* * *

### 7.6 Updating Data

* * *

For updating data, we will again use mysqli\_query() function with UPDATE statement of SQL.

We have profiles of 2 users (instructors and learners) and course details whose fields can be updated.

For editing profiles, we have to choose profile based on user category to update the concerned table. We will pick updating course details for this section.

Hope you have your newcourse.php file. Do a **Save as** to the file and name it as **editcourse.php**

We will do data update for course\_code = 1. Reason is, when you bind pages as an application, course\_code value will be sent to this page via variable. Here, we are individually working on this page, so, for now, we will go with the first course.

Now, we will do 2 editing works here:

*   Change the form design to include details of selected course
*   Change the php segment with retrieving course details and update the same

We will carry out this process in 3 phases:

*   Retrieval of course details in php
*   Form design for updating fields
*   Update statements for fields in php

**Phase-1: Retrieval code in php**

First, we will update the top php segment:

```
<?php
require('connect.php');
$course = 1;
$instructor = 'instructor1@onlinecourse.com';
$get_details = mysqli_query($con,"SELECT * FROM courses WHERE course_code = $course");
if($details = mysqli_fetch_row($get_details)){
 $titleval = $details[1];
 $describeval = $details[3]; 
 $outcomeval = $details[4];
 $eligibleval = $details[5]; 
}
```

This code is retrieving the course details of a particular course. Here, the course code is 1. So it is retrieving the first course details. The values of $course and $instructor variables are passed from the previous page in the actual application. For now, we will just assign values. In the next chapter, we will alter the code accordingly.

**Phase-2: Design modification**

Replace the main tag element with the code below:

```
<main>
<section>
<h3> Edit Course Details </h3>
<p>
<form method="post" name="frmeditcourse">
<input type="hidden" name="txtcourse" value="<?php echo $course; ?>">
<input type="hidden" name="txtinstruct" value="<?php echo $instructor; ?>">
<p><input type="text" name="txtcourse" size="60" value="<?php echo $titleval; ?>"></p>
<p><textarea name="txtdesc" cols="60"><?php echo $describeval; ?></textarea></p>
<p><textarea name="txtoutcome" cols="60"><?php echo $outcomeval; ?></textarea></p>
<p><textarea name="txteligible" cols="60"><?php echo $eligibleval; ?></textarea></p>
<p><input type="submit" name="editcourse" value="Update Course" class="frmbtn"></p>
</form>
</p>
</section>
</main>
```

There is a small modification done to the values of the variables. We place the values retrieved from the database into the form. We can modify the existing values and click update.

Execute: [http://localhost/onlinecourse/editcourse.php](#part0046.xhtml)

![7-6-1](Images/image00327.jpeg)

Do not do any changes now or click update. We have not added update code so far.

**Phase-3: Update fields in php**

We have a php segment in the top right? Add these lines to that segment. For clarity, I will post the complete code.

```
<?php
require('connect.php');
$course = 1;
$instructor = 'instructor1@onlinecourse.com';
$get_details = mysqli_query($con,"SELECT * FROM courses WHERE course_code = $course");
if($details = mysqli_fetch_row($get_details)){
 $titleval = $details[1];
 $describeval = $details[3]; 
 $outcomeval = $details[4];
 $eligibleval = $details[5]; 
}
//update part
if(isset($_POST['editcourse'])){
 $course = $_POST['txtcourse'];
 $instructor = $_POST['txtinstruct'];
 $title = $_POST['txttitle'];
 $describe = $_POST['txtdesc'];
 $outcome = $_POST['txtoutcome'];
 $eligible = $_POST['txteligible'];
 $update = false;
 if($title != $titleval){
   $update1 = mysqli_query($con,"UPDATE courses SET course_title = '$title' WHERE course_code = $course");
   $titleval = $title;
   $update = true;
 }
 if($describe != $describeval){
   $update2 = mysqli_query($con,"UPDATE courses SET course_description = '$describe' WHERE course_code = $course");
   $describeval = $describe;
   $update = true;
 }
 if($outcome != $outcomeval){
   $update3 = mysqli_query($con,"UPDATE courses SET course_outcome = '$outcome' WHERE course_code = $course");
   $outcomeval = $outcome;
   $update = true;
 }
 if($eligible != $eligibleval){
   $update4 = mysqli_query($con,"UPDATE courses SET course_eligible = '$eligible' WHERE course_code = $course");
   $eligibleval = $eligible;
   $update = true;
 }
 if($update){
   echo "<script>alert('Course Updated!');</script>";
 }
}
?>
```

I have updated where the update part code starts. Let me explain first:

We have $titleval, $describeval, $outcomeval, $eligibleval variables which hold values from the database. These values are used to fill the HTML elements in form.

```
if(isset($_POST['editcourse'])){
  $title = $_POST['txtcourse'];
  $describe = $_POST['txtdesc'];
  $outcome = $_POST['txtoutcome'];
  $eligible = $_POST['txteligible'];
```

We have these 4 variables to hold the values submitted via form during update.

```
if($title != $titleval){
	$update1 = mysqli_query($con,"UPDATE courses SET course_title = '$title' WHERE course_code = $course");
	$titleval = $title;
}
if($describe != $describeval){
	$update2 = mysqli_query($con,"UPDATE courses SET course_description = '$describe' WHERE course_code = $course");
	$describeval = $describe;
}
if($outcome != $outcomeval){
	$update3 = mysqli_query($con,"UPDATE courses SET course_outcome = '$outcome' WHERE course_code = $course");
	$outcomeval = $outcome;
}
if($eligible != $eligibleval){
	$update4 = mysqli_query($con,"UPDATE courses SET course_eligible = '$eligible' WHERE course_code = $course");
	$eligibleval = $eligible;
}
```

We have placed 4 conditions to be checked.

*   If the course title value in the database does not match with the course title form field value, we perform an update operation on the course title field
*   If the course description value in the database does not match with the course description form field value, we perform an update operation on the course description field
*   If the course outcome value in the database does not match with the course outcome form field value, we perform an update operation on the course outcome field
*   If the course eligibility value in the database does not match with the course eligibility form field value, we perform an update operation on the course eligibility field
*   We pass the submitted field values to the variables $titleval, $describeval, $outcomeval, $eligibleval because these variables will hold the updated values in the fields.

**Why have we checked fields individually instead of using 4 update statements?**

Every update operation in the database is costly. It means, you need to retrieve a field, perform an edit and update the same to the database. In order to minimize database complexity and optimize server resource, we check fields individually. In fact, we never modify all the fields every time. We update only when a field needs some modification. So, it is a good practice as a developer to follow this approach.

```
if($update){
	echo "<script>alert('Course Updated!');</script>";
}
```

We have a boolean variable $update initialized to false. Whenever an update operation takes place, it turns true. If it is true, user is given a message that an update has been performed.

It is always not necessary to display error related messages. Until you are in development, error messages may help, when you go live (real-time), minimizing them is a good and recommended practice unless it is needed.

You already have the form opened in the browser.

Make changes to the last field - eligibility:  
Anyone can enroll to this course, You should know English language to learn this

![7-6-2](Images/image00328.jpeg)

Click Update Course button.

![7-6-3](Images/image00329.jpeg)

When you press ok, the page will be displayed with the updated values.

With this, we wind up this section! We will look on deleting data in the next section.

* * *

### 7.5 Retrieving Data - II

* * *

We will now see how to provide search feature to the courses page.

**Search Courses:**

We will provide a search box and a submit button as discussed. Using SQL operators, we will filter the results.

We will again work with courses.php file.

*   Inside the main tag element, below the h3 tag, we will place a div with search box.
*   We will place a button to enable search
*   Corresponding php code snippets are added

Replace the main tag element with the code below:

```
<main>
<?php
$pattern = '';
$patternexist = false;
if(isset($_POST['searchcourse'])){
 $pattern = $_POST['txtsearch'];
 $patternexist = true;
}
?>
<section>
<h3>Courses</h3>
<div>
<form method="post" name="frmsearch">
<p><input type="search" name="txtsearch" size="60" value="<?php if($patternexist){echo $pattern; }?>"></p>
<p><input type="submit" name="searchcourse" class="frmbtn" value="Search Courses"></p>
</form>
</div>
<?php
require('connect.php');
$query = "SELECT * FROM courses";
if($patternexist){
  $query = "SELECT * FROM courses WHERE course_title LIKE '%$pattern%' OR course_description LIKE '%$pattern%'";
}
$select_courses = mysqli_query($con,$query);
while($selected = mysqli_fetch_row($select_courses)){
  echo "<div class='cl'>";
  echo "<h4><a href='details.php?search=$selected[0]'>".$selected[1]."<a/></h4>";
  echo "<p>".$selected[3]."</p>";
  echo "</div>";
}
?>
</section>
</main>
```

Let me explain the new segments of the code:

```
<?php
$pattern = '';
$patternexist = false;
if(isset($_POST['searchcourse'])){
  $pattern = $_POST['txtsearch'];
  $patternexist = true;
}
?>
```

We initialize two variables: $pattern for the search phrase and a Boolean to check if search phrase is present or not. We check isset() on search button to check if the button is clicked or not. If clicked, move the phrase to the variable $pattern and change $patternexist to true which means a search phrase is present.

```
<div>
<form method="post" name="frmsearch">
<p><input type="search" name="txtsearch" size="60" value="<?php if($patternexist){echo $pattern; }?>"></p>
<p><input type="submit" name="searchcourse" class="frmbtn" value="Search Courses"></p>
</form>
</div>
```

This is the design part of the search box. There is a php code segment inside value attribute. The php part states that, if search phrase exists ($patternexist = true), display the phrase in the search box. If search phrase is not present, nothing will be displayed in the search box.

```
$query = "SELECT * FROM courses";
if($patternexist){
  $query = "SELECT * FROM courses WHERE course_title LIKE '%$pattern%' OR course_description LIKE '%$pattern%'";
}
```

The query is to select all records from the courses table.

*   If there is a search pattern existing in the search box, we select records whose course title or course description fields have the search phrase, using the LIKE operator in the SQL syntax.
*   Either the first query or this query will be executed, and the while loop functions in the same way as it did earlier.
*   It will display either all the courses or only the selected courses having the pattern.

Getting into the execution part,

1\. Go to [http://localhost/onlinecourse/courses.php](#part0047.xhtml) and provide the search term as: **feature**

![7-5-1](Images/image00330.jpeg)

From the above image we can see the word feature appears in second course's description. So, we will have one course displayed when the search button is clicked.

2\. Click the search button

![7-5-2](Images/image00331.jpeg)

So, our php code and sql query works fine!

3\. Click Course 2 link and the course details are displayed.

![7-5-3](Images/image00332.jpeg)

You can find the URL with parameter search=2 since we have clicked second course.  
We have provided search courses and fetch course details features to our application.

The more you are comfortable with SQL syntax, the more it is easy to apply these features to the application.

* * *

### 7.7 Deleting Data

* * *

Right now in the application, we are not providing delete user account, delete course facilities. But we will provide delete content feature to our application.

If we provide editing facility to contents, either the uploaded file has to be deleted or the content title will be changed. Instead of doing this, we will give the instructor an option to delete the content (both the title and the file) and upload a new content.

The page we are going to work is obviously uploadcontent.php

**What will we do in this section?**

*   We will first retrieve the uploaded contents in this page
*   We will provide delete link to delete a particular content
*   If delete is attempted, we have to delete both database entry as well as the uploaded file

Ok, let us get back to the file.

**Retrieve uploaded contents:**

In the top part of the page, below the require statement add the code as:

```
require('connect.php');
$course = 1;
```

The $course variable will have the parameter passed from the previous page in the application. As for now, we initialized with course code as 1 (the first course).

In the main tag element, after the end of section element, we will include another section.

Add the following code:

```
<section>
<h3> Uploaded Contents </h3>
<?php
$fetch_contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
$fetch_num = mysqli_num_rows($fetch_contents);
if($fetch_num == 0){
 echo "No contents uploaded in this course!";
}
else{
 echo "<table style='margin: 0 10px; text-align:left;'>";
 echo "<tr>";
 echo "<th style='width: 50%'> Content Title </th>";
 echo "<th style='width: 40%'> Content File Path </th>";
 echo "<th style='width: 10%'> Delete Content </th>";
 echo "</tr>";
} 
while($fetched = mysqli_fetch_row($fetch_contents)){
 echo "<tr>";
 echo "<td>".$fetched[1]."</td>";
 echo "<td>".$fetched[3]."</td>";
 echo "<td><a href='uploadcontent.php?delete=$fetched[0]'>Delete</a></td>";
 echo "</tr>";
}
echo "</table>";
?>
</section>
```

This time we have displayed the records as a table. We have placed a link in the third column with delete as parameter variable. The delete variable will hold the value of content id.

Let me explain the new part of the code segment:

```
$fetch_contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
$fetch_num = mysqli_num_rows($fetch_contents);
if($fetch_num == 0){
 echo "No contents uploaded in this course!";
}
else{
 echo "<table style='margin: 0 10px; text-align:left;'>";
 echo "<tr>";
 echo "<th style='width: 50%'> Content Title </th>";
 echo "<th style='width: 40%'> Content File Path </th>";
 echo "<th style='width: 10%'> Delete Content </th>";
 echo "</tr>";
} 
```

mysqli\_num\_rows() will fetch the number of records retrieved by the query. If the record count is zero, we would display a message that no content is uploaded for that course. If there is at least one record, the table format gets displayed from the else block.

Execute [http://localhost/onlinecourse/uploadcontent.php](#part0048.xhtml)

![7-7-1](Images/image00333.jpeg)

Now, we will do the next part of the work - delete process!

**Delete Contents:**

We will add few more lines to the beginning of the file to the existing php code snippet.

Do not replace any content, you have to add this code before if(isset($\_POST\['upload'\])) {} block

```
require('connect.php');
$course = 1;
if(isset($_REQUEST['delete']))
{
  $id = $_REQUEST['delete'];
  $url = '';
  $getpath = mysqli_query($con,"SELECT * FROM contents WHERE content_id = $id");
  if($path = mysqli_fetch_row($getpath)){
    $url = $path[3];
  }
  $delete1 = mysqli_query($con, "DELETE FROM contents WHERE content_id = $id");
  $delete2 = unlink($url);
  if($delete1 and $delete2){
    echo "<script>alert('Content deleted!');</script>";
  }
}
```

Let me explain this part:

We first fetch the path of the content using the content\_id

```
$delete1 = mysqli_query($con, "DELETE FROM contents WHERE content_id = $id");
```

We delete the content record from the database

```
$delete2 = unlink($url);
```

We delete the file from the server (onlinecoourse/uploads folder). $url holds the path of the file.

When both $delete1 and $delete2 are successful, we display a message to the user through a pop-up.

Execute: [http://localhost/onlinecourse/uploadcontent.php](#part0048.xhtml)

Let us upload a new file named file3.ppt

![7-7-2](Images/image00334.jpeg)

![7-7-3](Images/image00335.jpeg)

Let us check in uploads folder too:

![7-7-4](Images/image00336.jpeg)

Now, we will delete the content named Content 3, click Delete link of Content 3 row.

![7-7-5](Images/image00337.jpeg)

![7-7-7](Images/image00338.jpeg)

Let us check in uploads folder again:

![7-7-6](Images/image00339.jpeg)

Hope you liked the approach of manipulating data via application.

With this, this chapter comes to an end! The next chapter will turn all these parts into a coherent and working application.

* * *

# Chapter 8: Working with Application

* * *

*   [](#part0050.xhtml)
    
    #### 8.1 Registration and Login
    
*   [](#part0051.xhtml)
    
    #### 8.2 User Dashboard
    
*   [](#part0052.xhtml)
    
    #### 8.3 Modify Profile
    
*   [](#part0053.xhtml)
    
    #### 8.4 Manage Courses and Content
    
*   [](#part0054.xhtml)
    
    #### 8.5 Enrolment and Course Access
    
*   [](#part0055.xhtml)
    
    #### 8.6 Home Page
    
*   [](#part0056.xhtml)
    
    #### 8.7 Application Demo
    

* * *

### 8.1 Registration and Login

* * *

The first step to use any application is to register for it. Once you create an account, you will be able to login. Whenever you want to access, you need to login.

This section will train you to complete the processes: registration and login.

We have already done with registering the details of the user. We are yet to complete login form. Let me describe you the flow:

Register -> Login -> User Dashboard

After you complete registration, you will be taken to the login page. When you successfully login, you will be taken to the corresponding user dashboard page. Dashboard is the place from where you can access user related pages. We will obviously have 2 types of dashboard: one for instructor and the other for learner.

We will need 3 pages for this:

*   register.php
*   login.php
*   dashboard.php

We have to redirect from register page to login page, similarly from login page to dashboard page. In the login page, we will create a link to the registration page. We will do this one by one. Before that, create the other 2 pages **login.php** and **dashboard.php**.

Let me remind you again, either create files and copy contents or use the save as option to create these 2 files. Only after creating files, we can redirect to login.php from register.php. If we don’t have a page named login.page, on redirecting, we will end up with 404 page not found error.

So, with no further delay, make those 2 pages ready. First, we will work with registration.

* * *

**Registration - Redirect to Login:**

Hope you have the file ready. We will include the code now. We will test it after completing the login process.

You have an if block in the top php segment:

```
if($check_insert1 and $check_insert2){
  echo "<script>alert('Registration successful!');</script>";
}
```

We will issue redirect command via JavaScript in this echo statement. Why are we doing so? Since we get success message via this alert(), we have to induce redirect after this message. If we code in php for redirection, this alert message will be missed. For safer side, we will code in JS.

Change the code as:

```
if($check_insert1 and $check_insert2){
  echo "<script>alert('Registration successful!');
  window.location.replace('login.php');</script>";
}
```

This code states that the current page has to be replaced with the url in the parameter.

* * *

**Login Process:**

We will design a login form and then include php code as usual. On successful login, we will redirect to dashboard.php. Let us start.

**Design Form: login.php**

Change the title tag content as User Login and replace the main tag element with the code below:

```
<main>
<section>
<h3> User Login </h3>
<p>
<form method="post" name="frmlogin">
<p><input type="email" name="txtuser" size="40" placeholder="Enter your email"></p>
<p><input type="password" name="txtpwd" size="40" placeholder="Enter your password"></p>
<p><input type="submit" name="login" value="Login" class="frmbtn"></p>
</form>
</p>
</section>
</main>
```

Do not enter any detail! Just execute for seeing the page: [http://localhost/onlinecourse/login.php](#part0050.xhtml)

![8-1-1](Images/image00340.jpeg)

**Authentication code: login.php**

We will include the authentication part in the top of the page as usual.

```
<?php
session_start();
require('connect.php');
$auth = true;
$hashedpwd = '';
if(isset($_POST['login'])){
  $username = $_POST['txtmail'];
  $password = $_POST['txtpwd'];
  $select_user = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail='$username'");
  if($user = mysqli_fetch_row($select_user)){
    $hashedpwd = $user[1];
  }
  else{
    $auth = false;
  }
  if(!password_verify($password,$hashedpwd)){
    $auth = false;
  }
  if($auth){
    $_SESSION['usersession'] = $username;
    echo "<script>window.location.replace('dashboard.php')</script>";
  }
  else{
    echo "<script>alert('Invalid username or password!')</script>";
  } 
}
?>
```

We will look at the explanation:

```
session_start();
```

We will use session\_start() for this authentication because we have to store the username as the session variable. It means, until the user logs out / closes session, the session variable will be alive.

```
$auth = true;
$hashedpwd = '';
```

We initialize two variables. $auth will hold true till the end of code if username and password matches database records. If $auth become false somewhere, it means either username or password does not match which means authentication fails. $hashedpwd will later hold the password field if username matches.

```
$select_user = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail='$username'");
if($user = mysqli_fetch_row($select_user)){
  $hashedpwd = $user[1];
}
else{
  $auth = false;
}
```

We search the record of userlogin table which matches the username.

*   If a user is existing with the username, the password field is assigned to $hashedpwd variable.
*   If a user is not existing with the username, $auth variable is set to false.

```
if(!password_verify($password,$hashedpwd)){
  $auth = false;
}
```

We compare the password entered in the form to the hashed password stored in the table. We use password\_verify() function designated for this purpose exclusively. In case, if there is no match between passwords, $auth turns to false.

```
if($auth){
  $_SESSION['usersession'] = $username;
  echo "<script>window.location.replace('dashboard.php')</script>";
}
else{
  echo "<script>alert('Invalid username or password!')</script>";
}
```

If $auth holds true under all those checks, we assign $username value to a session variable $\_SESSION\[‘usersession’\]. After this, we redirect to dashboard page. If $auth turns false in any of the checks, we print invalid login message.

**When does $auth turn false?**

*   When a username does not exist
*   When the entered password does not match with the hashed password value already stored in table (checked via password\_verify() function)

The login part is over here. We will do few changes in dashboard.php so that we can display the session variable value in this page from the login page.

* * *

**Session variable: dashboard.php**

Change the title tag content as User Dashboard.

Place the following lines in the top of the page:

```
<?php
session_start();
require('connect.php');
?>
```

It is advisable to place session\_start() in the beginning of the page.

As usual, replace the main tag content with the code:

```
<main>
<section>
<h3> User Dashboard </h3>
<p>
<?php 
$usersession = '';
if(isset($_SESSION['usersession'])){
  $usersession = $_SESSION['usersession'];
}
echo "<p>Hello ".$usersession."</p>";
?>
</p>
</section>
</main>
```

We have just assigned the session variable value to a variable $usersession and print the same.

**Execution:**

Shall we check the complete process now?

This time, we will:

*   register a learner
*   login the learner
*   see the learner's username in the dashboard page

We have to execute this as an application. So we will travel to registration page from the home page.

*   Go to [http://localhost/onlinecourse/](#part0050.xhtml)
*   Click Login
*   Click Register here link.

Let me sign up / register as a learner this time:

Details to be entered:

*   Who are you? Learner
*   Email - [learner1@onlinecourse.com](#part0050.xhtml)
*   Password - password
*   Full Name - Learner 1
*   Details - First learner of this platform

Let me show the process.

*This is a GIF image. Make sure GIF is supported in your device.*

![1604664851-registration-login](Images/image00341.gif)

Hope you also have the same flow of application without any bugs in between.

Do not forget to check phpmyadmin - learners and userlogin tables!

![8-1-2](Images/image00342.jpeg)

![8-1-3](Images/image00343.jpeg)

* * *

**How to redirect to dashboard if a session is running?**

We have one more work to do. In case you close a browser's tab unknowingly, but still your session is not expired, we have to redirect the login page to dashboard without asking for login details once more.

So, we will add up this code to the beginning of **login.php** file:

```
session_start();
if(isset($_SESSION['usersession'])){
  echo "<script>window.location.replace('dashboard.php')</script>";
}
require('connect.php');
```

*   Execute [http://localhost/onlinecourse/](#part0050.xhtml) in 2 tabs of a browser.
*   Try logging in one tab of the browser
*   Click Login in the other tab of the browser. You will be redirected to dashboard.php

We have to make much more changes to the dashboard page. We will do it in the next section.

* * *

### 8.2 User Dashboard

* * *

Dashboard is the place from where you can access all the necessary links.

In the instructor’s dashboard, we can place links to create course, edit course, upload / delete content, view enrolled learner’s progress reports, change profile and log out.

In the learner’s dashboard, we can place links to enrolled courses, access to courses, change profile and log out.

Whatever page we create, we have two options:

*   to place all the links in every page
*   to place all the links in a single page (dashboard) and place the dashboard link in every page

We will follow the second option. We will create a dashboard page, place all the links here and then link the dashboard in pages wherever it is needed. The reason is when you want to expand the project features / facilities, you can easily add them to the dashboard for linking.

For every dashboard link, we have to make few checks!

*   check if user is logged in
*   check the category of user - instructor or learner

**Pages - check and logout:**

*   We will create a new php page called check.php while will contain all the above checks. For every dashboard linked page, we will include check.php file and based on user category, appropriate dashboard will be displayed.
*   We will create a new php page called logout.php. In case, if a learner tries to access an instructor’s page, or vice versa, we will forcefully log them out. Also, we need to provide a log out link too.

* * *

**Logging out of session:**

Just create a blank file named logout.php and place the code below:

```
<?php
session_start();
if(isset($_SESSION['usersession'])){
 unset($_SESSION['usersession']);
}
header('Location: login.php');
?>
```

After un-setting the session variable, we redirect to login.php page. header() is a php function used for redirection. So far, we used JavaScript since we had pop-up messages displayed to the user. Since there is no message displayed, we used php function for this purpose.

Executing [http://localhost/onlinecourse/logout.php](#part0051.xhtml) will take you to login.php page.

* * *

**Checking session and category:**

What we will do here is:

*   check if the user is logged in
*   find the category of user (instructor / learner) using a function
*   find the name of user using a function

Just create a blank file named check.php and place the code below:

```
<?php
session_start();
require('connect.php');
//functions
function get_category($con,$id){
 $get_cat = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail = '$id'");
 if($cat = mysqli_fetch_row($get_cat)){
 return $cat[2];
 } 
}
function get_name($con,$id,$cat){
 $str = '';
 if($cat == 'instructor'){
  $str = "SELECT * FROM instructors WHERE instruct_mail = '$id'";
 }
 if($cat == 'learner'){
  $str = "SELECT * FROM learners WHERE learn_mail = '$id'";
 }
 $get_fname = mysqli_query($con,$str);
 if($name = mysqli_fetch_row($get_fname)){
   return $name[1];
 }  
}
//checking session
$usersession = '';
$category = '';
$name = '';
if(isset($_SESSION['usersession'])){
 $usersession = $_SESSION['usersession'];
 $category = get_category($con,$usersession);
 $name = get_name($con,$usersession,$category);
}
else{
 echo "<script>window.location.replace('login.php');</script>";
} 
?>
```

We will look at the functions first:

```
function get_category($con,$id){
  $get_cat = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail = '$id'");
  if($cat = mysqli_fetch_row($get_cat)){
	return $cat[2];
  }
}
```

We send 2 parameters to this function - the database connection resource and the email id of the user. Using this email id, we find the category of the user and return the same.

```
function get_name($con,$id,$cat){
   $str = '';
   if($cat == 'instructor'){
	  $str = "SELECT * FROM instructors WHERE instruct_mail = '$id'";
   } 
   if($cat == 'learner'){
	  $str = "SELECT * FROM learners WHERE learn_mail = '$id'";
   }
   $get_fname = mysqli_query($con,$str);
   if($name = mysqli_fetch_row($get_fname)){
	  return $name[1];
   }  
}
```

We send 3 parameters to this function - the database connection resource, the email id and the category of the user. Using the category, we query the corresponding table. We execute the query and return the user's name.

We will look at the session code now:

```
//checking session
$usersession = '';
$category = '';
$name = '';
if(isset($_SESSION['usersession'])){
  $usersession = $_SESSION['usersession'];
  $category = get_category($con,$usersession);
  $name = get_name($con,$usersession,$category);
}
else{
  echo "<script>window.location.replace('login.php');</script>";
}
```

We check if the session variable is set. If it is set, we copy the value to $usersession variable. Since $usersession is an email address (primary key of instructor and learner table), we send it as a parameter to get\_category() function and assign the value returned to $category variable. Similarly, we send $category as the third parameter to get\_name() and assign the value returned to $name variable.

In case the session variable is not set, the user will be sent back to login.php.

Purpose of redirection: Only logged in users can access this page!

So, three variables will be available to any page whichever includes check.php file:

*   $usersession - email id / primary key
*   $category - instructor / learner
*   $name - user's full name

Shall we design the dashboard?

* * *

**Instructor Dashboard:**

We will start with the instructor.

What are the menus needed for an instructor?

*   Courses - create course / edit course / upload content / view report of learners’ progress
*   Profile - change password / modify profile
*   Logout - to come out of dashboard

**Learner Dashboard:**

We will now look for learner.

What are the menus needed for a learner?

*   Enrolments - enrolled courses list / access courses
*   Profile - change password / modify profile
*   Logout - to come out of dashboard

From the above 2 lists, we can understand, we have to design a single page for profile modification. Logout will just be a link to logout.php. Profile designing will be dealt in the next section.

We will now design the dashboard. We need to alter the code segment that was provided temporarily in the previous section.

Replace the top php segment code as:

```
<?php
include ('check.php');
?>
<!DOCTYPE html>
…
</html>
```

Similarly for the main tag content, just retain that single line and remove the rest of the code as:

```
<main>
<section>
<h3> User Dashboard </h3>
<p>
<?php 
echo "<p>Hello ".$usersession."</p>";
?>
</p>
</section>
</main>
```

Login either as a learner / an instructor and check if you are getting the Hello <email> message. If you get it correctly as done in last section, your code is perfect so far!

We will do necessary modifications in the head element first:

Hope you know where to include a style tag. Include the style tag code (before </head>):

```
<style>
.cl{
 margin: 5px;
 display: inline-block;
 vertical-align: top;
 width: 300px;
 height: 100px;
 border: 1px solid #ccc;
}
</style>
```

This content is just the same as the one we used for listing courses.

Replace the main tag content as:

```
<main>
<section>
<?php 
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='logout.php'>Logout</a></p>";
echo "<div class='cl'>";
if($category == 'instructor'){
 echo "<h3><a href='clist.php'>Courses<a/></h3>";
 echo "<p>Manage Courses, Content and Reports</p>";
}
if($category == 'learner'){
 echo "<h3><a href='elist.php'>Enrolments<a/></h3>";
 echo "<p>Enrolled Courses and Content Access</p>";
}
echo "</div>";
echo "<div class='cl'>";
echo "<h3><a href='profile.php'>Profile<a/></h3>";
echo "<p>Change password and Profile</p>";
echo "</div>";
?>
</section>
</main>
```

For instructors, we have added courses link. For learners, we have added enrolments link. We link the profile to the same page for both the users. The logout link is given below the name of the user.

Login as learner,

![8-2-1](Images/image00344.jpeg)

Logout as learner and Login as instructor,

![8-2-2](Images/image00345.jpeg)

Hope you understood the next set of works! It would be clist.php, elist.php and profile.php. We will start with profile.php

* * *

### 8.3 Modify Profile

* * *

We will first list the tasks to be done in this chapter:

*   Design relevant form 
    *   Provide two modification - one for password, one for profile
    *   Changing email address is denied!
*   Add appropriate PHP code snippets for accomplishing tasks

We will start with form design! As usual use save as option or create new file and paste contents. The file name is profile.php

**Form design: profile.php**

In the beginning of the file, do not forget to include the line below:

```
<?php
include ('check.php');
?>
```

This time in design, we will include some php code for the purpose of displaying details from the database.

Replace main tag content as:

```
<main>
<section>
<?php 
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='dashboard.php'>Dashboard</a>&emsp;<a href='logout.php'>Logout</a></p>";
$str = '';
$details = '';
if($category == 'instructor'){
 $str = "SELECT * FROM instructors WHERE instruct_mail = '$usersession'";
}
if($category == 'learner'){
 $str = "SELECT * FROM learners WHERE learn_mail = '$usersession'";
}
$fetch_details = mysqli_query($con,$str);
if($fetch = mysqli_fetch_row($fetch_details)){
  $details = $fetch[2];
}
?>
<form method="post" name="frmpwd">
<p><input type="password" name="txtoldpwd" size="40" placeholder="Enter your old Password" required></p>
<p><input type="password" name="txtnewpwd" size="40" placeholder="Enter your new Password 8-15 characters" required></p>
<p><input type="submit" name="changepwd" value="Change Password" class="frmbtn"></p>
</form>
<p><hr></p>
<form method="post" name="frmprofile">
<p><input type="text" name="txtname" size="40" value="<?php echo $name; ?>" required></p>
<p><textarea name="txtdetails" cols="40" required><?php echo $details; ?></textarea></p>
<p><input type="submit" name="changeprofile" value="Update Profile" class="frmbtn"></p>
</form>
</section>
</main>
```

We are selecting the table using the category of users. Based on the selection, details are retrieved from the appropriate tables. Since we have same set of fields in both instructors and learners table, we use $details\[2\] element to get the details.

You can execute the profile page and look at the design:

![8-3-1](Images/image00346.jpeg)

As per design code, we are performing two updates - one to change password and the other to change profile details. We have to include two if(isset()) for two submissions.

**Updating profile: profile.php**

1\. Add this snippet to the beginning of php file: for changing password

```
<?php
include ('check.php');
if(isset($_POST['changepwd'])){
  $oldpassword = $_POST['txtoldpwd'];
  $newpassword = $_POST['txtnewpwd'];
  $get_password = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail = '$usersession'");
  $pwd = mysqli_fetch_array($get_password);
  //verifying if old password = new password
  if(password_verify($oldpassword,$pwd['user_pwd'])){ 
 
    if((strlen($newpassword) > 7) and (strlen($newpassword) < 21)){
      $hashed = password_hash($newpassword,PASSWORD_DEFAULT);
      $updatepwd = "UPDATE userlogin SET user_pwd = '$hashed' WHERE user_mail = '$usersession'";     
      if(mysqli_query($con,$updatepwd)){
         echo "<script>alert('Password changed! Login with new password!');
         window.location.replace('logout.php');</script>";
      }
    }
    else{
      echo "<script>alert('Password length must be between 8-15 characters!');</script>";
    } 

  }
  else{
    echo "<script>alert('Old password is wrong!');</script>";
  }
}
?>
```

The exact work starts from checking old password using password\_verify() function.

*   We have retrieved the hashed password from the table and accessed via $pwd\[‘user\_pwd’\]
*   We use password\_verify() to compare $pwd\['user\_pwd'\] and $oldpassword entered in the form
*   If the passwords do not match, we print old password is wrong.
*   If the passwords match, we make other check for the length of the password. 
    *   If the length of the new password is between 8 and 15 characters, the hash value of new password is updated and message is displayed to the user
    *   If the length does not match, we print a message asking the user to provide password in between 8 and 15 character length.

2\. Append the following profile change submission code to the previous php segment:

```
if(isset($_POST['changeprofile'])){
 $newname = $_POST['txtname'];
 $newdetails = $_POST['txtdetails'];
 if($category == 'instructor'){
   $updateprofile1 = "UPDATE instructors SET instruct_name = '$newname' WHERE instruct_mail = '$usersession'";
   $updateprofile2 = "UPDATE instructors SET instruct_details = '$newdetails' WHERE instruct_mail = '$usersession'";
 }
 if($category == 'learner'){
   $updateprofile1 = "UPDATE learners SET learn_name = '$newname' WHERE learn_mail = '$usersession'";
   $updateprofile2 = "UPDATE learners SET learn_details = '$newdetails' WHERE learn_mail = '$usersession'";
 }
 if(mysqli_query($con,$updateprofile1) and mysqli_query($con,$updateprofile2)){
   echo "<script>alert('Profile Updated!');</script>";
 }
}
```

This time, we have just updated both the fields irrespective of where the change is made. It is just to show you that either way is correct. It all depends on the developer.

Hope the update process is clear.

Execute [http://localhost/onlinecourse](#part0052.xhtml)

Login as instructor / learner and update profile.

*This is a GIF image. Make sure GIF is supported in your device.*

![1604664382-change-profile](Images/image00347.gif)

In the next section, we will work on the instructor's dashboard.

* * *

### 8.4 Manage Courses and Contents

* * *

Now, we are into the core part of Instructor category!

An instructor should be able to:

*   create new course
*   view existing courses
*   edit course details
*   upload content to course
*   view learners enrolled and their progress

We have pages for new course, edit course and upload content. For this page which we designed in dashboard section, the file name is **clist.php**

Either use save as of dashboard.php page or create new file clist.php and copy contents from dashboard.php

**What are the contents of this page?**

*   A link to create new course
*   Courses already created will be displayed as a table
*   Link to edit course
*   Link to upload content
*   Link to view progress of learners

We will make all pages ready for the instructor. Regarding progress page, we will design and make it ready. Once we complete the contents of next section, we will execute this progress page's working from there.

Shall we start?

**Display existing courses:**

We will display the courses created by the instructor - Instructor 1.

Hope the page clist.php already included check.php file in the beginning of the page. If it is not done, please include it as below along with one more line:

```
<?php include('check.php');
if($category == 'learner'){
  header('logout.php');
}
?>
```

We will also add a condition here, in case if a learner has logged in and somehow retrieved this page, we can redirect them to logout automatically.

To test this, login as learner and in the url access clist.php, you will be logged out and taken to login.php.

**clist.php**

```
<main>
<section>
<?php 
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='dashboard.php'>Dashboard</a>&emsp;<a href='logout.php'>Logout<a/></p>";
echo "<h4><a href='newcourse.php'>Add New Course</a></h4>";
$fetch_courses = mysqli_query($con,"SELECT * FROM courses WHERE course_instruct = '$usersession'");
if(mysqli_num_rows($fetch_courses) == 0){
 echo "No courses created so far!";
}
else{
 echo "<table style='margin:0 10%;width:80%;;text-align:left;'>";
 echo "<tr>";
 echo "<th style='width:40%;'> Course Title </th>";
 echo "<th style='width:10%;'> Edit Details </th>";
 echo "<th style='width:10%;'> Manage Content </th>";
 echo "<th style='width:20%;'> Learners Count </th>";
 echo "</tr>";
} 
while($fetched = mysqli_fetch_row($fetch_courses)){
 echo "<tr>";
 echo "<td>".$fetched[1]."</td>";
 echo "<td><a href='editcourse.php?cid=$fetched[0]'>Edit</td>";
 echo "<td><a href='uploadcontent.php?cid=$fetched[0]'>Add</td>";
 $get_enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code=$fetched[0]");
 echo "<td>";
 echo mysqli_num_rows($get_enrols);
 if (mysqli_num_rows($get_enrols) > 0){
  echo "&emsp;<a href='reports.php?cid=$fetched[0]'>View";
 }
 echo "</td>"; 
 echo "</tr>";
}
echo "</table>";
?>
</section>
</main>
```

*   We have displayed the details as a table. Only the title field is displayed.
*   We have provided a link to create new course.
*   In order to edit the course, we have provided link with parameter cid = coursecode
*   In order to upload content, we have provided link with parameter cid
*   In order to view learners' list and progress, we have used the same parameter cid

Login as instructor, click Courses in the dashboard:

![8-4-1](Images/image00348.jpeg)

We have passed the parameter cid which carries course code value. The next task we ought to do is: retrieve the parameter in 3 pages - editcourse.php, uploadcontent.php and reports.php

We shall the do the appropriate changes now:

* * *

First, we will start with newcourse.php

**newcourse.php**

We are not passing any parameter here, but we have to tell php to use $usersession value for instructor id.

Remove the following line from the form:

<input type='hidden' name='txtinstruct' value='instructor1@onlinecourse.com'>

We will modify the php segment as:

```
<?php
include('check.php');
if(isset($_POST['newcourse'])){
 $title = $_POST['txtcourse'];
 $describe = $_POST['txtdesc'];
 $instruct = $usersession;
 $outcome = $_POST['txtoutcome'];
 $eligible = $_POST['txteligible'];
 $insert = mysqli_query($con,"INSERT INTO courses VALUES (NULL,'$title','$instruct','$describe','$outcome','$eligible')");
 if($insert){
 echo "<script>alert('New Course created!');window.location.replace('clist.php');</script>";
 }
 else {
 echo "<script>alert('Sorry, try again!');</script>";
 }
}
?>
```

We have done three changes:

*   Instead of connect.php, we have included check.php
*   Instead of form submitted value, we assign $usersession value to $instruct variable
*   After pop-up message new course created is displayed, we direct the page to clist.php to show the courses list.

Make changes one by one so that you can understand better!

* * *

The next file to work is editcourse.php, to include the parameter cid.

**editcourse.php**

In the form design, remove the following line:

<input type="hidden" name="txtinstruct" value="<?php echo $instructor;?> ">

Since the code segment is too big, let me give you the part what you have to replace:

Replace:

require('connect.php');  
$course = 1;  
$instructor = 'instructor1@onlinecourse.com';

With:

```
include('check.php');
$course = '';
$instructor = $usersession;
if(isset($_REQUEST['cid'])){
  $course = $_REQUEST['cid'];
}
```

We have made 4 changes:

*   We have included check.php file
*   We have initialized $course as empty string
*   We have assigned request parameter cid (course code)'s value to $course variable
*   We have assigned $usersession value to $instructor variable

Try making changes one by one! It will give you better clarity on what you modify!

Since the instructor is logged in, we will retrieve the value from $usersession variable,remove one line from if(isset($\_POST\['editcourse'\])){}:

$instructor = $\_POST\['txtinstruct'\];

Similarly, make one more change. After updating, you have to redirect the page to clist.php:

In the php segment, find the if($update) block which prints course updated message and replace this:

```
if($update){
  echo "<script>alert('Course Updated!');window.location.replace('clist.php');</script>";
 }
```

We are just including the redirecting code here along with displaying pop-up. With this, we are done with editing course.

* * *

The next file we will work is uploadcontent.php

**uploadcontent.php**

There are 4 changes:

**Change 1** - We will alter the beginning of the code:

Replace:

require('connect.php');  
$course = 1;

With:

```
include('check.php');
$course = '';
if(isset($_REQUEST['cid'])){
  $course = $_REQUEST['cid'];
}
```

We have done the same changes. We have to add back link to courses. Because, in this page, we add and delete content. So redirecting to course page will make it terrific!

**Change 2** - In the main tag content, inside the first section element, add the link below the h3 tag as:

```
<h3> Add Content to Course </h3>
<p><a href='clist.php'>Back to Courses</a></p>
```

This will explicitly provide a link to go back to Courses page after adding / removing content.

In the form design we have to modify two things:

**Change 3** - The first modification is course hidden field.

Replace:

<input type='hidden' name='txtcourse' value='1'>

With:

```
<input type="hidden" name="txtcourse" value="<?php echo $course; ?>">
```

Else, whatever contents we add, it will be added to course 1.

**Change 4** - The second modification is adding an additional parameter in delete link.

Actually we sent content id via delete parameter here:

echo "<td><a href='uploadcontent.php?delete=$fetched\[0\]'>Delete</a></td>";

Modify the line as:

```
echo "<td><a href='uploadcontent.php?delete=$fetched[0]&&course=$course'>Delete</a></td>";
```

It is because, your course value has to be retained throughout add / delete processes of contents.

Appropriately, we will modify the if(isset($\_REQUEST\['delete'\])) as:

Replace:

if(isset($\_REQUEST\['delete'\]))  
{  
$id = $\_REQUEST\['delete'\];  
$url = '';

With:

```
if(isset($_REQUEST['delete']))
{
  $id = $_REQUEST['delete'];
  $course = $_REQUEST['course'];
  $url = '';
```

* * *

The final page we will work is reports.php

**reports.php**

Use save as option on dashboard / any page to create reports.php

We will need the beginning code of php segment in this file too:

Once reports.php file is created, make sure you place the following code in the beginning of file:

```
<?php
include('check.php');
$course = 0;
if(isset($_REQUEST['cid'])){
  $course = $_REQUEST['cid'];
}
?>
```

You can just save this code on the file. Once we enrol courses in the next section, we can check how this page is displayed!

Replace the main tag content as:

```
<main>
<section>
<?php 
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='clist.php'>Back to Courses<a/></p>";
$fetch_enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code = $course");
if(mysqli_num_rows($fetch_enrols) == 0){
 echo "No learners enrolled so far!";
}
else{
 echo "<table style='margin:0 10%;width:80%;;text-align:left;'>";
 echo "<tr>";
 echo "<th style='width:30%;'> Learner Name </th>";
 echo "<th style='width:30%;'> Learner Email </th>";
 echo "<th style='width:20%;'> Progress </th>";
  echo "</tr>";
} 
while($enrols = mysqli_fetch_row($fetch_enrols)){
  echo "<tr>";
 echo "<td>".get_name($con,$enrols[1],'learner')."</td>";
 echo "<td>".$enrols[1]."</td>";
  echo "<td><progress id='progress' value='".get_progress($con,$enrols[0])."' max='100'></progress> ".get_progress($con,$enrols[0])."%</td>"; 
 echo "</tr>";
}
echo "</table>";
?>
</section>
</main>
```

We retrieved and displayed the details as a table:

*   We have retrieved learner's id from enroll table
*   Using get\_name() function in check.php, we display the name of the learner
*   We use another function get\_progress() by passing the enroll\_id as parameter to get how far the learner has progressed (we are yet to define this function) using progress bar

The reason why we used get\_progress() function is, not only for instructors, even learners would need this progress count during their learning process. So, instead of calculating progress twice, we use a function.

* * *

In **check.php**, we have to define a function get\_progress()

Where should you place this function? To be honest, wherever you want! For uniformity, we will place this function below the other 2 functions as:

function get\_category() { }

function get\_name() { }

function get\_progress() { }

Let us follow this order, ok?

**check.php**

Now, let us look at the definition of get\_progress() function. Place this code snippet appropriately in the page.

```
function get_progress($con,$id){
 $get_enrols = mysqli_query($con,"SELECT * FROM enroll WHERE enroll_id = $id");
 $progress = 0;
 if($enrol = mysqli_fetch_row($get_enrols)){
  $enrolid = $enrol[0];
  $course = $enrol[2];
  $completed = 0;
  $contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
  $total = mysqli_num_rows($contents);
  while($content = mysqli_fetch_row($contents)){
     $contentid = $content[0];
     $records = mysqli_query($con,"SELECT * FROM record WHERE enroll_id = $enrolid AND content_id = $contentid");
     if(mysqli_num_rows($records) == 1){
       $completed = $completed + 1;
     }
  }
  $progress = round(($completed / $total) * 100);
 }
 return $progress;
}
```

It is kind of complicated code when you look for the first time. But it is just logic based. So, let me explain you the logic used:

*   Using enroll id we find the learner id and course code.
*   Using course code, we retrieve all contents associated with it.
*   We assign contents count to $total and initialize learner’s completion - $completed to zero.
*   For every content id, we find if there is an entry in record table by asking is there any record with the enroll id and content id in the record table.
*   If there is an entry, we increment the value of $completed variable.
*   For progress calculation, we use simple mathematics (completed / total \* 100), round the value and return the same.
*   In case, the learner has not started learning, we will return $progress variable's initial value which is zero.

Now, you can compare, each line of the query with this logic.

```
$contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
$total = mysqli_num_rows($contents);
```

This will find the count of contents for that particular course

```
while($content = mysqli_fetch_row($contents)){
  $contentid = $content[0];
  $records = mysqli_query($con,"SELECT * FROM record WHERE learn_mail = '$learner' AND content_id = $contentid");
  if(mysqli_num_rows($records) == 1){
	  $completed = $completed + 1;
  }
}
```

For every content id, we seek an entry matching the learner id and content id in the record table. If an entry is found, $completed count is incremented by 1.

```
$progress = round(($completed / $total) * 100);
```

Progress calculation part is done here.

Let me show you, how to create a new course, edit course and upload content. Remember, reports cannot be seen now!

*This is a GIF image. Make sure GIF is supported in your device.*

![1604666457-instructor-dashboard](Images/image00349.gif)

* * *

### 8.5 Enrolment and Course Access

* * *

We will now work on learner's dashboard page. Similar to instructor, a learner also has a set of tasks to do. We will list the tasks here:

*   enroll in a course
*   access the course - view course contents
*   see the progress

Sounds to be simple right? We have already defined a function to get the progress of a learner in a course.

**What are the contents of this page?**

*   List of enrolled courses with details
*   Link to view course contents

Where should the learner enroll from? From the courses.php page.

We will be modifying: courses.php first. Later, we will create two pages - elist.php and contents.php

* * *

**Enrolment process:**

Let us first create an enroll button in courses.php

**Creating enroll button: courses.php**

Let us increase the height of the course listing box: Change the height in the style tag.

```
<style>
.cl{
 margin: 5px;
 display: inline-block;
 vertical-align: top;
 width: 300px;
 height: 200px;
 border: 1px solid #ccc;
}
</style>
```

We have changed the height from 150px to 200px. We will create a form button with 40px height. The form will be placed inside the while loop's div element.

Replace the while loop in the main tag content as:

```
while($selected = mysqli_fetch_row($select_courses)){
 echo "<div class='cl'>";
 echo "<h4><a href='details.php?search=$selected[0]'>".$selected[1]."<a/></h4>";
 echo "<p style='height:70px';>".$selected[3]."</p>";
 echo "<form method='post'>";
 echo "<input type='hidden' name='txtcourse' value='$selected[0]'>";
 echo "<input type='submit' name='enroll' value = 'Enroll' class='frmbtn'>";
 echo "</form>";
 echo "</div>"; 
}
```

Check the courses.php page.

![8-5-1](Images/image00350.jpeg)

**Enrolling code: courses.php**

Add the following code snippet to the beginning of the file:

```
<?php
session_start();
require('connect.php');
if(isset($_POST['enroll'])){
  if(isset($_SESSION['usersession'])){
  $usersession = $_SESSION['usersession'];
  $course = $_POST['txtcourse'];
  $get_enrol = mysqli_query($con,"SELECT * FROM enroll WHERE learn_mail = '$usersession' AND course_code = $course");
  if(mysqli_num_rows($get_enrol) == 0){
    $enrol = "INSERT INTO enroll VALUES (NULL,'$usersession',$course,DEFAULT,NULL)";
    if(mysqli_query($con,$enrol)){
      echo "<script>alert('You are enrolled!');window.location.replace('elist.php');</script>";
    }
  }
  else{
    echo "<script>alert('You are already enrolled!');window.location.replace('elist.php');</script>";
  }
 }
 else{
   echo "<script>alert('Please login and enroll!');</script>";
 }
}
?>
```

We make 2 checks here:

*   If the user is logged into the site (first check), 
    *   We check if the user has already enrolled to the course (second check). If yes, we display already enrolled message.
    *   If the user is not already enrolled, we insert a record into the enroll table and confirm enrolment with a message.
    *   In both cases, we direct to elist.php after pop-up display.
*   If the user is not logged in, we ask to login and enroll

This time, we did not include check.php because, that file is for ensuring whether users are logged in, to access those pages. But courses.php is a general page that should be accessed even without logging into the site. So we have included connect.php file this time.

Please do not check the working now! We have no file named elist.php and it will end up in 404 file not found error.

We will create the file with listing of enrolments and then execute the enrolment process. This page will more or less be similar to clist.php.

**Listing enrolments:**

Use save as option to create elist.php. Change title tag content as Enrollments.

Include the following code in the beginning of the file.

```
<?php
include ('check.php');
if($category == 'instructor'){
  header('logout.php');
}
?>
```

Here, we check if an instructor gets into this page by mistake with the url and redirect to logout.php page. Only learners can access this page.

Replace the main tag content as:

```
<main>
<section>
<?php 
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='logout.php'>Logout<a/></p>";
$fetch_enrolls = mysqli_query($con,"SELECT * FROM enroll WHERE learn_mail = '$usersession'");
if(mysqli_num_rows($fetch_enrolls) == 0){
 echo "No enrollments so far!";
}
else{
 echo "<table style='margin: 0 5%;text-align:left;'>";
 echo "<tr>";
 echo "<th style='width:30%;'> Course Title </th>";
 echo "<th style='width:15%;'> Start Date </th>";
 echo "<th style='width:15%;'> Completion Date </th>";
 echo "<th style='width:15%;'> Access Content </th>";
 echo "<th style='width:15%;'> Progress </th>";
  echo "</tr>";
} 
while($fetched = mysqli_fetch_row($fetch_enrolls)){
 echo "<tr>";
 $get_coursetitle = mysqli_query($con,"SELECT * FROM courses WHERE course_code = $fetched[0]");
 $coursetitle = mysqli_fetch_array($get_coursetitle);
  echo "<td>".$coursetitle['course_title']."</td>";
 echo "<td>".$fetched[3]."</td>";
 if($fetched[4] == NULL){
   echo "<td>Not completed</td>";
 }
 else{
   echo "<td>".$fetched[4]."</td>";
 }
 echo "<td>";
 echo "<form method='post' action='contents.php'><input type='hidden' name='txtcourse' value='$fetched[2]'>";
 echo "<input type='submit' name='access' value='View' class='frmbtn'></form>";
  echo "</td>"; 
 echo "<td><progress id='progress' value='".get_progress($con,$fetched[0])."' max='100'></progress> ".get_progress($con,$fetched[0])."%</td>";
 echo "</tr>";
}
echo "</table>";
?>
</section>
</main>
```

*   We have made one check while displaying retrieved fields.  
    We check if $fetched\[4\] = NULL (that is, completion date is NULL).  
    If it is null, it means course is in progress, so we have displayed 'not completed' message.  
    If it is not null, we display the course completion date.
    
*   We give access to content via POST method in form. As long as the course is free, it is not an issue. When it comes to learning paid courses, this becomes a problem. So, on safer side, we use POST method form.
    
*   We have also given the action attribute in the form. So, contents.php will process the values submitted via this form.

Now, let me login as a learner and then enroll in one of the courses.

*This is a GIF image. Make sure GIF is supported in your device.*

![1604666907-enroll-course](Images/image00351.gif)

The next work is to view the contents of the course!

* * *

**Accessing Course contents:**

We have to design a page to view the course contents - the files uploaded by the instructor.

*   We will use a select box to display the contents title. Based on title selection, appropriate content file will be displayed.
*   Since we have different file types, we will use iframe tag to display them

First, use save as and name the file as **contents.php**

There is nothing in specific to design. So, as usual let us start with the php segment to be placed in the beginning of the page.

```
<?php
include ('check.php');
$course = 0;
$contents = 0;
if(isset($_POST['access'])){
  $course = $_POST['txtcourse'];
}
?>
```

We still have some more to add. We will add it after finishing the main tag segment. $course will hold the course code throughout the learning process. $contents will hold the content id of the content to be displayed.

Replace the main tag content with:

```
<main>
<section>
<?php 
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='elist.php'>Back to Enrollments</a></p>";
echo "<p>";
echo "<form method='post'>";
echo "<input type='hidden' name='txtcourse' value='$course'>";
echo "<select name='txtcontent'>";
echo "<option value='999'>Choose the content title</option>";
$fetch_contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
while($fetched = mysqli_fetch_row($fetch_contents)){
 echo "<option value='$fetched[0]'>".$fetched[1]."</option>";
}
echo "</select>";
echo "<input type='submit' name='getcontent' value='Go' class='frmbtn'>";
echo "</form>";
echo "</p>";
?>
</section>
</main>
```

If no content title is selected, we will submit the form with Choose the content title option which has value 999. We will use this in the later part.

Go to elist.php and click View (View link of Course Name 1)

![8-5-2](Images/image00352.jpeg)

You can find the content titles of the course in the drop down list. Based on this selection, we will display the content in the iframe tag.

Add few more lines to the beginning of the file as:

```
<?php
include ('check.php');
$course = 0;
$contents = 0;
if(isset($_POST['access'])){
  $course = $_POST['txtcourse'];
}
if(isset($_POST['getcontent'])){
  $course = $_POST['txtcourse'];
  $contents = $_POST['txtcontent'];
}
?>
```

We assign course code to $course and content id to $contents variables on form submission.

We will display the content file below the form. We will add another section element to the main tag element. There is already a section element. Place this between </section> and </main>:

```
<section>
<?php
if(($contents == 999) || ($contents == 0)){
 echo "Please choose a content title!";
}
else{
 $fetch_content = mysqli_query($con,"SELECT * FROM contents WHERE content_id = $contents");
 if($fetch = mysqli_fetch_row($fetch_content)){
   echo "<h4>".$fetch[1]."</h4>";
   $filestring = explode('.',$fetch[3]);
   $file_ext= strtolower(end($filestring));
   $exts = array('doc','docx','ppt','pptx');
   if(in_array($file_ext,$exts)){
     echo "<p>The content will be downloaded!</p>";
   }
   echo "<p><iframe src='$fetch[3]' height='auto' width='80%' height='500px' frameborder='0'></iframe></p>";
  }
}
?>
</section>
```

Here, we check if $contents value = 0 or 999, then we display 'Please choose a content title' message. It means, whenever a content title is not chosen, this message will be displayed.

As usual we find the extension of the file and if it is one among doc, docx, ppt,pptx, it cannot be displayed in the html file. So, we print a message that the file will be downloaded and the download starts when iframe tag loads. If the file extension is among pdf / mp4 / txt / rtf, it gets displayed via the iframe tag.

Try selecting a content, and see the corresponding file getting displayed or downloaded.

Now, there is one more pending task!

**Record learner progress:**

This progress will also be recorded in the same page.

We need to include code for inserting into record table below the iframe tag:

Replace the if block above, with:

```
if($fetch = mysqli_fetch_row($fetch_content)){
  echo "<h4>".$fetch[1]."</h4>";
  $filestring = explode('.',$fetch[3]);
  $file_ext= strtolower(end($filestring));
  $exts = array('doc','docx','ppt','pptx');
  if(in_array($file_ext,$exts)){
    echo "<p>The content will be downloaded!</p>";
  }
  echo "<p><iframe src='$fetch[3]' height='auto' width='80%' height='500px' frameborder='0'></iframe></p>";
  $get_enrolid = mysqli_query($con,"SELECT * FROM enroll WHERE learn_mail = '$usersession' AND course_code = $course");
  $enrolid = mysqli_fetch_array($get_enrolid);
  $eid = $enrolid['enroll_id'];
  $check_records = mysqli_query($con,"SELECT * FROM record WHERE enroll_id = $eid AND content_id = $contents");
  if(mysqli_num_rows($check_records) == 0){
    mysqli_query($con,"INSERT INTO record VALUES ($eid,$contents)");
 } 
  if(get_progress($con,$eid) == 100){
    mysqli_query($con,"UPDATE enroll SET learn_end = NOW() WHERE enroll_id = $eid");
  } 
}
```

*   We find the enroll\_id using $usersession variable and $course variable
*   We check if content\_id and $enroll\_id have already been inserted in the record table
*   If it is not inserted, we insert the data to the record table.
*   When the progress reaches 100, we assign the current date as the completion date of the course.

Let me show accessing contents of course name 1

*This is a GIF image. Make sure GIF is supported in your device.*

![1604667223-access-contents](Images/image00353.gif)

We will look at the phpmyadmin screenshot of record table.

![8-5-3](Images/image00354.jpeg)

Shall we check the progress of learners from instructor’s dashboard?

Logout as learner and Login as instructor:

You will see a link next to number of learners enrolled:

![8-5-4](Images/image00355.jpeg)

Click View to view the learner’s progress:

![8-5-5](Images/image00356.jpeg)

I think, the development of the application almost comes to an end with this! We covered everything as per the project outline specified in the Chapter 6.1.

We are just left with one page - the home page of the application. We will do it in the next section.

* * *

### 8.6 Home Page

* * *

The only thing we have to do is to complete the home page tasks

*   Display the courses and number of enrolled learners in each course
*   Display the details of Instructors

They are simple retrieval processes!

Open **index.php** page.

Change the title tag content as **Online Course Home**

Replace the article tag content as:

```
<article class="artclass">
<div>
<h3>Courses with enrollments</h3>
<?php
require('connect.php');
$get_courses = mysqli_query($con,"SELECT * FROM courses");
while($courses = mysqli_fetch_row($get_courses)){
  $enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code = $courses[0]");
  echo "<p>".$courses[1]." &emsp; - &emsp; ".mysqli_num_rows($enrols)."</p>";
}
?>
</div>
<div style='vertical-align:top;'>
<h3>Instructors List</h3>
<?php
$get_instr= mysqli_query($con,"SELECT * FROM instructors");
while($instr = mysqli_fetch_row($get_instr)){
  echo "<p>".$instr[1]." - ".$instr[2]."</p>";
}
?>
</div>
</article>
```

We have done simple retrievals for displaying relevant information as per the template.

```
$get_courses = mysqli_query($con,"SELECT * FROM courses");
while($courses = mysqli_fetch_row($get_courses)){
  $enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code = $courses[0]");
  echo "<p>".$courses[1]." &emsp; - &emsp; ".mysqli_num_rows($enrols)."</p>";
}
```

We fetch all the courses. For each course in the while loop, we fetch enrolments made to that particular course. mysqli\_num\_rows($enrols) holds the number of enrolment to the course.

```
$get_instr= mysqli_query($con,"SELECT * FROM instructors");
while($instr = mysqli_fetch_row($get_instr)){
  echo "<p>".$instr[1]." - ".$instr[2]."</p>";
}
```

We fetch all the instructors and display two of their details: instructor's name and instructor's details.

Let me give the screenshot:

![8-6](Images/image00357.jpeg)

* * *

### 8.7 Application Demo

* * *

Let me show a demo video of the working application!

I will create one more learner, one more instructor, one more course and upload contents for the new course. We will enroll the new learner to the new course and see progress in each stage.

Here is the demo!

*This is a GIF image. Make sure GIF is supported in your device.*

![1604667613-Demo](Images/image00358.gif)

**Note:**

For debugging reasons and replacing code issues, let me provide the code page by page.

Click on the file name to view coding

**Code Menu:**

1.  [Database Connection - connect.php](#part0056.xhtml#connect)
    
2.  [Home Page - index.php](#part0056.xhtml#homepage)
    
3.  [Login Page - login.php](#part0056.xhtml#login)
    
4.  [Logout Page - logout.php](#part0056.xhtml#logout)
    
5.  [Functions - check.php](#part0056.xhtml#check)
    
6.  [Register - register.php](#part0056.xhtml#register)
    
7.  [Dashboard Page - dashboard.php](#part0056.xhtml#dashboard)
    
8.  [Profile Page - profile.php](#part0056.xhtml#profile)
    
9.  [Courses Page - courses.php](#part0056.xhtml#courses)
    
10.  [Course Details Page - details.php](#part0056.xhtml#details)
     
11.  [Course Enrolments of Learners - elist.php](#part0056.xhtml#elist)
     
12.  [Course Contents - contents.php](#part0056.xhtml#contents)
     
13.  [Manage Courses - clist.php](#part0056.xhtml#clist)
     
14.  [Add New Course - newcourse.php](#part0056.xhtml#newcourse)
     
15.  [Edit Existing Course - editcourse.php](#part0056.xhtml#editcourse)
     
16.  [Upload Contents for Courses - uploadcontent.php](#part0056.xhtml#uploadcontent)
     
17.  [Reports of Learners - reports.php](#part0056.xhtml#reports)
     

* * *

**Database Connection - connect.php** 

```
<?php
$host = "localhost";
$username = "ocuser";
$password = "Pass@OC20";
$database = "onlinecourse";
$con = mysqli_connect($host,$username,$password,$database);
if (!$con) {
    die("Connection failed: " . mysqli_connect_error()); 
}
?>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Home Page - index.php** 

```
<!DOCTYPE html>
<html>
<head>
<title> Online Course Home </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<h3>Welcome to Online Course System!</h3>
<p style='text-align:left;'>In this web application, we will develop user-friendly application to enroll to courses. We primarily have 2 major users for this application: </p>
<ul  style='text-align:left;'>
<li>Instructor - the one who develops course materials </li>
<li>Learner - the one who studies those developed course materials </li>
</ul>
<p style='text-align:left;'>
The instructors develop course materials and upload the same in this website. Once the course is published, they appear in the search list. The learners browse through the course list and sneek into every detail. nce they are 
comfortable with a course, they enroll into it. Once they enroll, they can view the course materials. A progress track will be there to specify how far they have completed the course. When progress reaches 100%, it marks the course to be completed.
</p>
<p>
For this application, we keep all courses free of cost!
</p>
</section>
<article class="artclass">
<div>
<h3>Courses with enrollments</h3>
<?php
require('connect.php');
$get_courses = mysqli_query($con,"SELECT * FROM courses");
while($courses = mysqli_fetch_row($get_courses)){
    $enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code = $courses[0]");
	echo "<p>".$courses[1]."  -  ".mysqli_num_rows($enrols)."</p>";
}
?>
</div>
<div style='vertical-align:top;'>
<h3>Instructors List</h3>
<?php
$get_instr= mysqli_query($con,"SELECT * FROM instructors");
while($instr = mysqli_fetch_row($get_instr)){
	echo "<p>".$instr[1]." - ".$instr[2]."</p>";
}
?>
</div>
</article>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) **Login Page - login.php** 

```
<?php
session_start();
if(isset($_SESSION['usersession'])){
	echo "<script>window.location.replace('dashboard.php')</script>";
}
require('connect.php');
$auth = true;
$hashedpwd = '';
if(isset($_POST['login'])){
 $username = $_POST['txtuser'];
 $password = $_POST['txtpwd'];
 $select_user = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail='$username'");
 if($user = mysqli_fetch_row($select_user)){
   $hashedpwd = $user[1];
 }
 else{
    $auth = false;
 }
 if(!(password_verify($password,$hashedpwd))){
    $auth = false;
 }
 if($auth){
    $_SESSION['usersession'] = $username;
    echo "<script>window.location.replace('dashboard.php')</script>";
 }
else{
	echo "<script>alert('Invalid username or password!')</script>";
}  
}
?>

<!DOCTYPE html>
<html>
<head>
<title> User Login </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<h3> User Login </h3>
<p>
<form method="post" name="frmlogin">
<p><input type="email" name="txtuser" size="40" placeholder="Enter your email"></p>
<p><input type="password" name="txtpwd" size="40" placeholder="Enter your password"></p>
<p><input type="submit" name="login" value="Login" class="frmbtn"></p>
</form>
</p>
<p>New learner or instructor? <a href="register.php">Register here</a> </p>
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Logout Page - logout.php** 

```
<?php
session_start();
if(isset($_SESSION['usersession'])){
	unset($_SESSION['usersession']);
}
header('Location: login.php');
?>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Functions - check.php** 

```
<?php
session_start();
require('connect.php');
//functions
function get_category($con,$id){
  $get_cat = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail = '$id'");
  if($cat = mysqli_fetch_row($get_cat)){
   return $cat[2]; 
  }	
}
function get_name($con,$id,$cat){
   $str = '';
   if($cat == 'instructor'){
     $str = "SELECT * FROM instructors WHERE instruct_mail = '$id'";
   }
   if($cat == 'learner'){
     $str = "SELECT * FROM learners WHERE learn_mail = '$id'";
   }
   $get_fname = mysqli_query($con,$str);
   if($name = mysqli_fetch_row($get_fname)){
      return $name[1];
   }	  
}

function get_progress($con,$id){
   $get_enrols = mysqli_query($con,"SELECT * FROM enroll WHERE enroll_id = $id");
   $progress = 0;
   if($enrol = mysqli_fetch_row($get_enrols)){
        $enrolid = $enrol[0];
	    $course = $enrol[2];
		$completed = 0;
        $contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
		$total = mysqli_num_rows($contents);
		while($content = mysqli_fetch_row($contents)){
		    $contentid = $content[0];
			$records = mysqli_query($con,"SELECT * FROM record WHERE enroll_id = $enrolid AND content_id = $contentid");
			if(mysqli_num_rows($records) == 1){
				$completed = $completed + 1;
			}
		}
		$progress = round(($completed / $total) * 100);
   }
   return $progress;
}

//checking session
$usersession = '';
$category = '';
$name = '';
if(isset($_SESSION['usersession'])){
  $usersession = $_SESSION['usersession'];
  $category = get_category($con,$usersession);
  $name = get_name($con,$usersession,$category);
}
else{
  echo "<script>window.location.replace('login.php');</script>";
}  
?>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Registration - register.php** 

```
<?php
require('connect.php');
if(isset($_POST['register'])){
  $category = $_POST['txtusercategory'];
  $usermail = $_POST['txtmail'];
  $userpwd = $_POST['txtpwd'];
  $name = $_POST['txtname'];
  $details = $_POST['txtdetails'];

  if((strlen($userpwd) > 7) && strlen($userpwd < 21)){
      $userpwd = password_hash($userpwd,PASSWORD_DEFAULT);
	  $insert1 = "INSERT INTO userlogin VALUES ('$usermail','$userpwd','$category')";
	  if($category == 'learner'){
	    $insert2 = "INSERT INTO learners VALUES ('$usermail','$name','$details')";
	  }
	  if($category == 'instructor'){
	  $insert2 = "INSERT INTO instructors VALUES ('$usermail','$name','$details')";
	  }	  
	  $check_insert1 = mysqli_query($con,$insert1);
	  $check_insert2 = mysqli_query($con,$insert2);
	  if($check_insert1 and $check_insert2){
		echo "<script>alert('Registration successful!');window.location.replace('login.php');</script>";
	  }
      else{
         echo "<script>alert('Sorry! Try again!');</script>";
      }		 
  }
  else{
     echo "<script>alert('Password should be between 8-15 characters');</script>";
  }	 
}
?>
<!DOCTYPE html>
<html>
<head>
<title> User Registration </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<h3> User Registration </h3>
<p>
<form method="post" name="frmregister">
<p><select name="txtusercategory">
<option value="">Who are you?</option>
<option value="learner">Learner</option>
<option value="instructor">Instructor</option>
</select></p>
<p><input type="email" name="txtmail" size="40" placeholder="Enter your Email Address" required></p>
<p><input type="password" name="txtpwd" size="40" placeholder="Enter your Password 8-15 characters" required></p>
<p><input type="text" name="txtname"  size="40" placeholder="Enter you Full Name" required></p>
<p><textarea name="txtdetails" cols="40" placeholder="Enter your details" required></textarea></p>
<p><input type="submit" name="register" value="Register" class="frmbtn"></p>
</form>
</p>
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Dashboard Page - dashboard.php** 

```
<?php
include ('check.php');
?>
<!DOCTYPE html>
<html>
<head>
<title> User Dashboard </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<style>
.cl{
margin: 5px;
display: inline-block;
vertical-align: top;
width: 300px;
height: 100px;
border: 1px solid #ccc;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<?php  
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='logout.php'>Logout<a/></p>";
echo "<div class='cl'>";
if($category == 'instructor'){
   echo "<h3><a href='clist.php'>Courses<a/></h3>";
   echo "<p>Manage Courses, Content and Reports</p>";
}
if($category == 'learner'){
   echo "<h3><a href='elist.php'>Enrolments<a/></h3>";
   echo "<p>Enrolled Courses and Content Access</p>";
}
echo "</div>";
echo "<div class='cl'>";
echo "<h3><a href='profile.php'>Profile<a/></h3>";
echo "<p>Change password and Profile</p>";
echo "</div>";
?> 
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Profile Page - profile.php** 

```
<?php
include ('check.php');
if(isset($_POST['changepwd'])){
 $oldpassword = $_POST['txtoldpwd'];
 $newpassword = $_POST['txtnewpwd'];
 $get_password = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail = '$usersession'");
 $pwd = mysqli_fetch_array($get_password);
 if(password_verify($oldpassword,$pwd['user_pwd'])){
   if((strlen($newpassword) > 7) and (strlen($newpassword) < 21)){
      $hashed = password_hash($newpassword,PASSWORD_DEFAULT);
      $updatepwd = "UPDATE userlogin SET user_pwd = '$hashed' WHERE user_mail = '$usersession'";
      if(mysqli_query($con,$updatepwd)){
		echo "<script>alert('Password changed! Login with new password!');window.location.replace('logout.php');</script>";
	  }
   }
   else{
       echo "<script>alert('Password length must be between 8-15 characters!');</script>";
   }   
  }
  else{
	   echo "<script>alert('Old password is wrong!');</script>";
  }
}
if(isset($_POST['changeprofile'])){
  $newname = $_POST['txtname'];
  $newdetails = $_POST['txtdetails'];
  if($category == 'instructor'){
   $updateprofile1 = "UPDATE instructors SET instruct_name = '$newname' WHERE instruct_mail = '$usersession'";
   $updateprofile2 = "UPDATE instructors SET instruct_details = '$newdetails' WHERE instruct_mail = '$usersession'";
  }
  if($category == 'learner'){
   $updateprofile1 = "UPDATE learners SET learn_name = '$newname' WHERE learn_mail = '$usersession'";
   $updateprofile2 = "UPDATE learners SET learn_details = '$newdetails' WHERE learn_mail = '$usersession'";
  }
  if(mysqli_query($con,$updateprofile1) and mysqli_query($con,$updateprofile2)){
	echo "<script>alert('Profile Updated!');</script>";
  }
}
?>
<!DOCTYPE html>
<html>
<head>
<title> User Dashboard </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<style>
.cl{
margin: 5px;
display: inline-block;
vertical-align: top;
width: 300px;
height: 100px;
border: 1px solid #ccc;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<?php  
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='dashboard.php'>Dashboard</a>    <a href='logout.php'>Logout<a/></p>";
$str = '';
$details = '';
if($category == 'instructor'){
	$str = "SELECT * FROM instructors WHERE instruct_mail = '$usersession'";
}
if($category == 'learner'){
	$str = "SELECT * FROM learners WHERE learn_mail = '$usersession'";
}
$fetch_details = mysqli_query($con,$str);
if($fetch = mysqli_fetch_row($fetch_details)){
		$details = $fetch[2];
} 
?>
<form method="post" name="frmpwd">
<p><input type="password" name="txtoldpwd" size="40" placeholder="Enter your old Password" required></p>
<p><input type="password" name="txtnewpwd" size="40" placeholder="Enter your new Password 8-15 characters" required></p>
<p><input type="submit" name="changepwd" value="Change Password" class="frmbtn"></p>
</form>
<p><hr></p>
<form method="post" name="frmprofile">
<p><input type="text" name="txtname"  size="40" value="<?php echo $name; ?>" required></p>
<p><textarea name="txtdetails" cols="40" required><?php echo $details; ?></textarea></p>
<p><input type="submit" name="changeprofile" value="Update Profile" class="frmbtn"></p>
</form>
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Courses Page - courses.php** 

```
<?php
session_start();
require('connect.php');
if(isset($_POST['enroll'])){
  if(isset($_SESSION['usersession'])){
    $usersession = $_SESSION['usersession'];
	$course = $_POST['txtcourse'];
	$get_enrol = mysqli_query($con,"SELECT * FROM enroll WHERE learn_mail = '$usersession' AND course_code = $course");
	if(mysqli_num_rows($get_enrol) == 0){
	   $enrol = "INSERT INTO enroll VALUES (NULL,'$usersession',$course,DEFAULT,NULL)";
	   if(mysqli_query($con,$enrol)){
		 echo "<script>alert('You are enrolled!');window.location.replace('elist.php');</script>";
	   }
	}
	else{
		 echo "<script>alert('You are already enrolled!');window.location.replace('elist.php');</script>";
	}
  }
  else{
	echo "<script>alert('Please login and enroll!');</script>";
  }
}
?>
<!DOCTYPE html>
<html>
<head>
<title> Courses </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<style>
.cl{
margin: 5px;
display: inline-block;
vertical-align: top;
width: 300px;
height: 200px;
border: 1px solid #ccc;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<?php
$pattern = '';
$patternexist = false;
if(isset($_POST['searchcourse'])){
  $pattern = $_POST['txtsearch'];
  $patternexist = true;
}
?>
<section>
<h3>Courses</h3>
<div>
<form method="post" name="frmsearch">
<p><input type="search" name="txtsearch" size="60" value="<?php if($patternexist){echo $pattern; }?>"></p>
<p><input type="submit" name="searchcourse" class="frmbtn" value="Search Courses"></p>
</form>
</div>
<?php
require('connect.php');
$query = "SELECT * FROM courses";
if($patternexist){
$query = "SELECT * FROM courses WHERE course_title LIKE '%$pattern%' OR course_description LIKE '%$pattern%'";
}
$select_courses = mysqli_query($con,$query);
while($selected = mysqli_fetch_row($select_courses)){
   echo "<div class='cl'>";
   echo "<h4><a href='details.php?search=$selected[0]'>".$selected[1]."<a/></h4>";
   echo "<p style='height:70px';>".$selected[3]."</p>";
   echo "<form method='post'>";
   echo "<input type='hidden' name='txtcourse' value='$selected[0]'>";
   echo "<input type='submit' name='enroll' value = 'Enroll' class='frmbtn'>";
   echo "</form>";
   echo "</div>";   
}
?>
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Course Details Page - details.php** 

```
<!DOCTYPE html>
<html>
<head>
<title> Courses </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<style>
.cl{
margin: 5px;
display: inline-block;
vertical-align: top;
width: 300px;
height: 150px;
border: 1px solid #ccc;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section style="text-align:left;padding: 0 30px;">
<h3>Course Details</h3>
<?php
require('connect.php');
if(isset($_REQUEST['search'])){
  $search = $_REQUEST['search'];
}
$query = "SELECT * FROM courses WHERE course_code = $search";
$select_courses = mysqli_query($con,$query);
if($selected = mysqli_fetch_row($select_courses)){
   echo "<h4>".$selected[1]."</h4>";
   echo "<h5> Instructor: ";
   $find_instructor = mysqli_query($con,"SELECT instruct_name FROM instructors WHERE instruct_mail = '$selected[2]'");
   $found = mysqli_fetch_array($find_instructor);
   echo $found['instruct_name'];
   echo "</h5>";
   echo "<h5>Description:</h5>";
   echo "<p>".$selected[3]."</p>";
   echo "<h5>Outcomes:</h5>";
   $temp = explode(",",$selected[4]);
   echo "<ul>";
   foreach($temp as $t){
	echo "<li>".$t."</li>";
   }	
   echo "</ul>";   
   echo "<h5>Eligibility:</h5>";
   $temp = explode(",",$selected[5]);
   echo "<ul>";
   foreach($temp as $t){
	echo "<li>".$t."</li>";
   }	
   echo "</ul>"; 
   echo "</div>";
}
?>
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Course Enrolments of Learners - elist.php** 

```
<?php
include ('check.php');
if($category == 'instructor'){
header('logout.php');
}
?>
<!DOCTYPE html>
<html>
<head>
<title> Enrollments </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<style>
.cl{
margin: 5px;
display: inline-block;
vertical-align: top;
width: 300px;
height: 100px;
border: 1px solid #ccc;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<?php  
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='logout.php'>Logout<a/></p>";
$fetch_enrolls = mysqli_query($con,"SELECT * FROM enroll WHERE learn_mail = '$usersession'");
if(mysqli_num_rows($fetch_enrolls) == 0){
	echo "No enrollments so far!";
}
else{
	echo "<table style='margin: 0 5%;text-align:left;'>";
	echo "<tr>";
	echo "<th style='width:30%;'> Course Title </th>";
	echo "<th style='width:15%;'> Start Date </th>";
	echo "<th style='width:15%;'> Completion Date </th>";
	echo "<th style='width:15%;'> Access Content </th>";
	echo "<th style='width:15%;'> Progress </th>";
    echo "</tr>";
}	
while($fetched = mysqli_fetch_row($fetch_enrolls)){
    echo "<tr>";
	$get_coursetitle = mysqli_query($con,"SELECT * FROM courses WHERE course_code = $fetched[0]");
	$coursetitle = mysqli_fetch_array($get_coursetitle);
    echo "<td>".$coursetitle['course_title']."</td>";
	echo "<td>".$fetched[3]."</td>";
	if($fetched[4] == NULL){
	echo "<td>Not completed</td>";
	}
	else{
	echo "<td>".$fetched[4]."</td>";
	}
	echo "<td>";
	echo "<form method='post' action='contents.php'><input type='hidden' name='txtcourse' value='$fetched[2]'>";
	echo "<input type='submit' name='access' value='View' class='frmbtn'></form>";
    echo "</td>";	
	echo "<td><progress id='progress' value='".get_progress($con,$fetched[0])."' max='100'></progress> ".get_progress($con,$fetched[0])."%</td>";
	echo "</tr>";
}
echo "</table>";
?> 
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Course Contents - contents.php** 

```
<?php
include ('check.php');
$course = 0;
$contents = 0;
if(isset($_POST['access'])){
 $course = $_POST['txtcourse'];
}
if(isset($_POST['getcontent'])){
 $course = $_POST['txtcourse'];
 $contents = $_POST['txtcontent'];
}
?>
<!DOCTYPE html>
<html>
<head>
<title> Enrollments </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<style>
.cl{
margin: 5px;
display: inline-block;
vertical-align: top;
width: 300px;
height: 100px;
border: 1px solid #ccc;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<?php  
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='elist.php'>Back to Enrollments</a></p>";
echo "<p>";
echo "<form method='post'>";
echo "<input type='hidden' name='txtcourse' value='$course'>";
echo "<select name='txtcontent'>";
echo "<option value='999'>Choose the content title</option>";
$fetch_contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
while($fetched = mysqli_fetch_row($fetch_contents)){
	echo "<option value='$fetched[0]'>".$fetched[1]."</option>";
}
echo "</select>";
echo "<input type='submit' name='getcontent' value='Go' class='frmbtn'>";
echo "</form>";
echo "</p>";
?> 
</section>
<section>
<?php
if(($contents == 999) || ($contents == 0)){
   echo "Please choose a content title!";
}
else{
$fetch_content = mysqli_query($con,"SELECT * FROM contents WHERE content_id = $contents");
if($fetch = mysqli_fetch_row($fetch_content)){
    echo "<h4>".$fetch[1]."</h4>";
	$filestring = explode('.',$fetch[3]); 
    $file_ext=  strtolower(end($filestring));
	$exts = array('doc','docx','ppt','pptx');
	if(in_array($file_ext,$exts)){
	echo "<p>The content will be downloaded!</p>";
    }
	echo "<p><iframe src='$fetch[3]' height='auto' width='80%' height='500px' frameborder='0'></iframe></p>";
	$get_enrolid = mysqli_query($con,"SELECT * FROM enroll WHERE learn_mail = '$usersession' AND course_code = $course");
	$enrolid = mysqli_fetch_array($get_enrolid);
	$eid = $enrolid['enroll_id'];
	$check_records = mysqli_query($con,"SELECT * FROM record WHERE enroll_id = $eid AND content_id = $contents");
	if(mysqli_num_rows($check_records) == 0){
		mysqli_query($con,"INSERT INTO record VALUES ($eid,$contents)");
	}
    if(get_progress($con,$eid) == 100){
        mysqli_query($con,"UPDATE enroll SET learn_end = NOW() WHERE enroll_id = $eid");
    }	
}
}
?>
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Manage Courses - clist.php** 

```
<?php
include ('check.php');
if($category == 'learner'){
header('logout.php');
}
?>
<!DOCTYPE html>
<html>
<head>
<title> User Dashboard </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<style>
.cl{
margin: 5px;
display: inline-block;
vertical-align: top;
width: 300px;
height: 100px;
border: 1px solid #ccc;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<?php  
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='dashboard.php'>Dashboard</a>    <a href='logout.php'>Logout<a/></p>";
echo "<h4><a href='newcourse.php'>Add New Course</a></h4>";
$fetch_courses = mysqli_query($con,"SELECT * FROM courses WHERE course_instruct = '$usersession'");
if(mysqli_num_rows($fetch_courses) == 0){
	echo "No courses created so far!";
}
else{
	echo "<table style='margin:0 10%;width:80%;;text-align:left;'>";
	echo "<tr>";
	echo "<th style='width:40%;'> Course Title </th>";
	echo "<th style='width:10%;'> Edit Details </th>";
	echo "<th style='width:10%;'> Manage Content </th>";
	echo "<th style='width:20%;'> Learners Count </th>";
    echo "</tr>";
}	
while($fetched = mysqli_fetch_row($fetch_courses)){
    echo "<tr>";
    echo "<td>".$fetched[1]."</td>";
	echo "<td><a href='editcourse.php?cid=$fetched[0]'>Edit</td>";
	echo "<td><a href='uploadcontent.php?cid=$fetched[0]'>Add</td>";
	$get_enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code=$fetched[0]");
	echo "<td>";
	echo mysqli_num_rows($get_enrols);
	if (mysqli_num_rows($get_enrols) > 0){
		echo "    <a href='reports.php?cid=$fetched[0]'>View";
	}
    echo "</td>";	
	echo "</tr>";
}
echo "</table>";
?> 
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Add New Course - newcourse.php** 

```
<?php
include('check.php');
if(isset($_POST['newcourse'])){
  $title = $_POST['txtcourse'];
  $describe = $_POST['txtdesc'];
  $instruct = $usersession;
  $outcome = $_POST['txtoutcome'];
  $eligible = $_POST['txteligible'];
  $insert = mysqli_query($con,"INSERT INTO courses VALUES (NULL,'$title','$instruct','$describe','$outcome','$eligible')");
  if($insert){
	echo "<script>alert('New Course created!');window.location.replace('clist.php');</script>";
  }
  else {
	echo "<script>alert('Sorry, try again!');</script>";
  }
}
?>
<!DOCTYPE html>
<html>
<head>
<title> New Course </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<h3> New Course Details </h3>
<p>
<form method="post" name="frmnewcourse">
<p><input type="text" name="txtcourse" size="60" placeholder="Enter your Course Title" required></p>
<p><textarea name="txtdesc" cols="60" placeholder="Enter Course Description Details" required></textarea></p>
<p><textarea name="txtoutcome" cols="60" placeholder="Enter Course Outcomes separated by commas" required></textarea></p>
<p><textarea name="txteligible" cols="60" placeholder="Enter Eligibility Details separated by commas" required></textarea></p>
<p><input type="submit" name="newcourse" value="Create Course" class="frmbtn"></p>
</form>
</p>
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Edit Existing Course - editcourse.php** 

```
<?php
include('check.php');
$course = '';
$instructor = $usersession;
if(isset($_REQUEST['cid'])){
 $course = $_REQUEST['cid'];
} 

$get_details = mysqli_query($con,"SELECT * FROM courses WHERE course_code = $course");
if($details = mysqli_fetch_row($get_details)){
   $titleval = $details[1];
   $describeval = $details[3];   
   $outcomeval = $details[4];
   $eligibleval = $details[5];  
}
if(isset($_POST['editcourse'])){
  $course = $_POST['txtcourse'];
  $title = $_POST['txttitle'];
  $describe = $_POST['txtdesc'];
  $outcome = $_POST['txtoutcome'];
  $eligible = $_POST['txteligible'];
  $update = false;
  if($title != $titleval){
   $update1 = mysqli_query($con,"UPDATE courses SET course_title = '$title' WHERE course_code = $course");
   $titleval = $title;
   $update = true;
  }
  if($describe != $describeval){
   $update2 = mysqli_query($con,"UPDATE courses SET course_description = '$describe' WHERE course_code = $course");
   $describeval = $describe;
   $update = true;
  }
  if($outcome != $outcomeval){
   $update3 = mysqli_query($con,"UPDATE courses SET course_outcome = '$outcome' WHERE course_code = $course");
   $outcomeval = $outcome;
   $update = true;
  }
  if($eligible != $eligibleval){
   $update4 = mysqli_query($con,"UPDATE courses SET course_eligibility = '$eligible' WHERE course_code = $course");
   $eligibleval = $eligible;
   $update = true;
  }
  if($update){
   echo "<script>alert('Course Updated!');window.location.replace('clist.php');</script>";
  }
}
?>
<!DOCTYPE html>
<html>
<head>
<title> Edit Course Details </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<h3> Edit Course Details </h3>
<p>
<form method="post" name="frmeditcourse">
<input type="hidden" name="txtcourse" value="<?php echo $course; ?>"> 
<p><input type="text" name="txttitle" size="60" value="<?php echo $titleval; ?>"></p>
<p><textarea name="txtdesc" cols="60"><?php echo $describeval; ?></textarea></p>
<p><textarea name="txtoutcome" cols="60"><?php echo $outcomeval; ?></textarea></p>
<p><textarea name="txteligible" cols="60"><?php echo $eligibleval; ?></textarea></p>
<p><input type="submit" name="editcourse" value="Update Course" class="frmbtn"></p>
</form>
</p>
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Upload Contents for Course - uploadcontent.php** 

```
<?php
include('check.php');
$course = '';
if(isset($_REQUEST['cid'])){
 $course = $_REQUEST['cid'];
} 

if(isset($_REQUEST['delete']))
{
 $id = $_REQUEST['delete'];
 $course = $_REQUEST['course'];
 $url = '';
 $getpath = mysqli_query($con,"SELECT * FROM contents WHERE content_id = $id");
 if($path = mysqli_fetch_row($getpath)){
	$url = $path[3];
 }
 $delete1 = mysqli_query($con, "DELETE FROM contents WHERE content_id = $id");
 $delete2 = unlink($url);
 if($delete1 and $delete2){
   echo "<script>alert('Content deleted!');</script>";
 }
}

if(isset($_POST['upload'])){
   $title = $_POST['txtcontent'];
   $course = $_POST['txtcourse'];
   $filename = $_FILES['txtfile']['name'];
   $filetmp = $_FILES['txtfile']['tmp_name'];
   $filestring = explode('.',$_FILES['txtfile']['name']); 
   $file_ext=  strtolower(end($filestring));
   $exts = array('txt','rtf','doc','docx','pdf','ppt','pptx','mp4');
   if(in_array($file_ext,$exts)===false){ 
     echo "<script>alert('You can upload only txt, rtf, doc, docx, pdf, ppt, pptx, mp4 files');</script>";
   }
   else{
     $newpath = 'uploads/';
	 if (!is_dir($newpath)) {
            mkdir($newpath, 0777, true);
     }
	 $filepath = $newpath.strtotime("now").'.'.$file_ext;
     move_uploaded_file($filetmp,$filepath);
 	 $insert = mysqli_query($con,"INSERT INTO contents VALUES (NULL, '$title', $course, '$filepath')");
	 if($insert){
	 echo "<script>alert('Content Uploaded successfully!');</script>";
	 }
	 else{
	 echo "<script>alert('Something went wrong, Try again!');</script>";
	 }	 
  }  
}
?>
<!DOCTYPE html>
<html>
<head>
<title> Upload Content </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<h3> Add Content to Course </h3>
<p><a href='clist.php'>Back to Courses</a></p>
<p>
<form method="post" name="frmnewcontent" enctype="multipart/form-data">
<p><input type="text" name="txtcontent" size="60" placeholder="Enter Content Title" required></p>
<input type="hidden" name="txtcourse" value="<?php echo $course; ?>">
<p>Allowed extensions: txt, rtf, doc, docx, pdf, ppt, pptx, mp4 
<input type="file" name="txtfile" id="txtfile" required></p>
<p><input type="submit" name="upload" value="Upload" class="frmbtn"></p>
</form>
</p>
</section>
<section>
<h3> Uploaded Contents </h3>
<?php
$fetch_contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
$fetch_num = mysqli_num_rows($fetch_contents);
if($fetch_num == 0){
  echo "No contents uploaded in this course!";
}
else{
  echo "<table style='margin: 0 10px; text-align:left;'>";
  echo "<tr>";
  echo "<th style='width: 50%'> Content Title </th>";
  echo "<th style='width: 40%'> Content File Path </th>";
  echo "<th style='width: 10%'> Delete Content </th>";
  echo "</tr>";
}  
while($fetched = mysqli_fetch_row($fetch_contents)){
  echo "<tr>";
  echo "<td>".$fetched[1]."</td>";
  echo "<td>".$fetched[3]."</td>";
  echo "<td><a href='uploadcontent.php?delete=$fetched[0]&&course=$course'>Delete</a></td>";
  echo "</tr>";
}
echo "</table>";
?>
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

**Reports of Learners - reports.php** 

```
<?php
include('check.php');
$course = 0;
if(isset($_REQUEST['cid'])){
 $course = $_REQUEST['cid'];
}
?>
<!DOCTYPE html>
<html>
<head>
<title> User Dashboard </title>
<link rel="stylesheet" href="css/style.css">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
<style>
.cl{
margin: 5px;
display: inline-block;
vertical-align: top;
width: 300px;
height: 100px;
border: 1px solid #ccc;
}
</style>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  if($(window).width() > 600)
     $("ul").show();
	 else
	 $("ul").hide();
  $("button").click(function(){
    $("ul").slideToggle();
  });
});
</script>
</head>
<body>
<header>
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
	<li><a href="index.php" title="Home">Home</a></li>
	<li><a href="courses.php" title="About">Courses</a></li>
	<li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<?php  
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='clist.php'>Back to Courses<a/></p>";
$fetch_enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code = $course");
if(mysqli_num_rows($fetch_enrols) == 0){
	echo "No learners enrolled so far!";
}
else{
	echo "<table style='margin:0 10%;width:80%;;text-align:left;'>";
	echo "<tr>";
	echo "<th style='width:30%;'> Learner Name </th>";
	echo "<th style='width:30%;'> Learner Email </th>";
	echo "<th style='width:20%;'> Progress </th>";
    echo "</tr>";
}	
while($enrols = mysqli_fetch_row($fetch_enrols)){
    echo "<tr>";
	echo "<td>".get_name($con,$enrols[1],'learner')."</td>";
	echo "<td>".$enrols[1]."</td>";
    echo "<td><progress id='progress' value='".get_progress($con,$enrols[0])."' max='100'></progress> ".get_progress($con,$enrols[0])."%</td>";	
	echo "</tr>";
}
echo "</table>";

?> 
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

[Go to Code menu](#part0056.xhtml#urllist) 

* * *

Hope, these code snippets will help you in making the application to work hassle-free!  
If you would have coded along with me throughout and used these code snippets only for reference, you would have had the best hands-on experience!  
With this, we have reached the end of this ebook!

* * *

# CONCLUSION

* * *

This e-book achieves: learning the core programming concepts of PHP and developing a web application using PHP-MySQL.

The reason for insisting to learn PHP is simple - almost the web is ruled by PHP today. There may be lots of emerging technologies. Currently, most of the websites are using php. Though not for development, in future you have scopes to maintain / monitor or modify these websites without changing the technology.

Being prepared for the future is good, but conquering the present matters!

**What's Next?**

You can be confident that you have mastered the programming constructs in PHP. You have also gained experience in designing and developing a web application from scratch. From here, you will be ready to work with real-time projects.

PHP gives you the most comfortable zone of learning as well as working!

Hope this e-book was engaging and giving you hands-on experience on working with PHP and MySQL.

**Thank You!!!**

* * *