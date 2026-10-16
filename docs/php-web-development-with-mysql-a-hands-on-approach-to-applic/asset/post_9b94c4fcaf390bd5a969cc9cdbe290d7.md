
## Dedications

**To my wife, Debbie,** *who always encourages me to strive for what’s good and to “do the next right thing.” I never would have finished this project without your love, support, and gentle prodding.*

**To my students,** *who made me realize I am not here to teach you, but rather to enable your learning.*

## Foreword

Almost a decade ago, I was running our local PHP user group, and Ken heard about and attended one of our events. He instantly became an ever-enthusiastic member of our community. Ken is always ready to say hi to everyone and make sure they feel welcome. On top of that, he is also always happy to give a talk, which is a surefire way to endear yourself to a user group leader. When we needed a new space to hold our meetings, Ken once again stepped up and volunteered his classroom space at the local tech college where he was teaching. It was a perfect fit with plenty of space, easy transportation access, a projector, and great Wi-Fi—a user group’s dream come true! Eventually, Ken made the mistake of mentioning that he wouldn’t mind helping more if we needed anything. He had barely finished saying that before I made him a co-organizer of the group.

Throughout the years, Ken has been invaluable in building our amazing local PHP community. He has an infectious enthusiasm that draws people in, and his love of teaching is second to none. He doesn’t just teach the material, but he truly cares about helping his students succeed. Not only that, but you can always rely on him. When he started toying with the idea of writing a book, Ken wasn’t sure he would be able to finish the book, but I never doubted he would. I knew that once he agreed to do it, he would persevere and get it done. That’s just the kind of person Ken is.

Ken’s teaching style focuses on real-world skills and hands-on practice. This book is no exception. When you are done with this book, you will have working examples of code talking with databases and interacting with users. You will have a good understanding of what happens during these interactions, which will help you immensely during your future debugging sessions and give you a solid foundation to stand on as you learn about more advanced programming techniques, frameworks, and libraries.

So even though Ken and I agree to disagree on specifically which framework you should learn next, I am so grateful for his love of PHP and his love of sharing knowledge with others. Our community is far better for having Ken around, and I’m so excited for you to get to know him a bit through this book.

Welcome to the PHP community. We are glad you are here!

– Beth Tucker Long, July 2021

## About the Author

Ken Marks has been working in his dream job as a Programming Instructor at Madison College in Madison, Wisconsin, teaching PHP web development using MySQL since 2012. Prior to teaching, Ken worked as a software engineer for more than 20 years, mainly developing medical device software.

Ken earned his Bachelors of Science in Computer Science from California State University at Fullerton and earned his Masters of Science in Adult Education from the University of Wisconsin at Platteville.

Ken is actively involved in the PHP community, speaking and teaching at conferences.

In his spare time, he’s a man of many hobbies such as 3D printing, board game development, Ham radio, Fly fishing, and of course, Coffee Roasting :-)

Ken has two grown daughters and lives in the Madison area with his wife and their cat Ophelia who thinks she’s a dog.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_15_0.png)

## Introduction

> *The best way to predict the future is to invent it.*
> 
> *-Alan Kay*

### Who Should Use This Book?

Do you want to learn how to create dynamic database-driven web applications? This book guides you through building a typical CRUD (Create-Read-Update-Delete) application with PHP and MySQL.

### Introductory Programming Knowledge

If you have an introductory understanding of programming concepts, this book is for you.
You should be familiar with the following concepts:

- How to create variables
- The following kinds of logic:
  - sequential
  - conditional
  - looping
- Modularization using functions and object methods
- Arrays

You should be familiar with all of the above concepts using any modern programming language you are familiar with.

### Basic HTML/CSS Knowledge

You should have a basic understanding of how to create simple static web pages using HTML and CSS. A good place to brush up on these skills is https://www.w3schools.com.

### Introductory Knowledge of Databases and SQL

Although not required, it is helpful to understand how relational databases work and have some introductory knowledge of the Standard Query Language (SQL).

## INTRODUCTION

### Why PHP and MySQL?

Both PHP and MySQL are open source which means you can freely download them and modify the source code if you so desire. Moreover, PHP and MySQL are commonly used together.

Both PHP and MySQL have a low barrier to entry. All you need to develop dynamic web applications with databases is access to a computer. All the applications necessary to develop using PHP and MySQL are freely available at no cost.

### Who This Book is NOT For?

If you are unfamiliar with any of these concepts, you would be best served by first getting a hold of an introductory programming book. While we introduce how PHP implements common programming concepts like loops and arrays, we expect you to know how and when to use them. Likewise, if you are not comfortable with basic HTML/CSS, you should spend some time brushing up on these skills as well.

### PHP Versions, MySQL, and This Book

PHP version 7.0 provides a significant upgrade over version 5.6 in both performance and security. Therefore, all PHP code and concepts presented in this book will be based on version 7.0.

There are many database management systems (DBMS). However, this book uses a DBMS based on the Standard Query Language (SQL). We use the MySQL DBMS because it is frequently used with PHP, free to download and use, and it is the most popular DBMS in the world.

### How Code Samples are Presented

Code samples are used throughout the book to illustrate each topic. Longer code listings are numbered and include line numbers for ease of reference. Syntax highlighting similar to what you find in a modern text editor or integrated development environment (IDE) is used to make the code more readable by making variables, strings, and keywords stand out. Finally, you can also download the code samples from the phparch.com website.

Bear in mind that the code samples in the book have been formatted to fit in the narrower widths afforded by the screens for PDF and electronic readers as well as the printed page. None of the changes made to accommodate this limitation affect the functionality of the code. As such, the code archive for this book also includes the unaltered versions of the application code found here.

### How to Use This Book

This book is split into two major parts. Part one is a basic reference to the PHP language. While not an exhaustive reference, it explains all the features needed for the web applications presented in this book. As more web applications are presented, you will be applying more of the PHP language concepts. Part two shows how to apply the PHP language through the presentation of various web applications. It is intended to give the web developer a complete understanding of how to apply PHP and MySQL for many of the most common web development challenges. To illustrate the process, it works through the development of a full-featured application implementing the typical CRUD (Create-Read-Update-Delete) operations found in one.

### A Brief History of PHP

PHP was created in 1994[1] by Rasmus Lerdorf and was originally designed to be a simple set of Common Gateway Interface (CGI) binaries written using the C-programming language for interacting with HTML forms. Rasmus called this suite of scripts “Personal Home Page Tools.” Rasmus continued to add more functionality to his toolset, including database interaction and a framework for developing dynamic web applications. In early June of 1995, Rasmus released PHP Tools to the public through the comp.infosystems.www.authoring. CGI newsgroup. In October of that year, Rasmus released a new version that consisted of an advanced scripting interface that resembled C and Perl. In April of the next year, Rasmus added database support for several DBMSs, and in June of 1996, version 2 of PHP was released. In May of 1998, 1% (approximately 60000) web servers had PHP/FI installed.

In 1997, Andi Gutmans and Zeev Suraski collaborated with Rasmus to rewrite the PHP Parser. When they released version 3 (in June of 1998), the programming language was renamed “PHP,” which is a recursive acronym meaning “PHP: Hypertext Preprocessor.” PHP 3 allowed for easy extensibility, with many developers contributing useful modules. PHP 3 also included Object-Oriented Programming (OOP) extensions to the language. PHP 3, at one point, was installed on 10% of the web servers on the internet.

During the winter of 1998, Andi Gutmans and Zeev Suraski started working on performance and modularity improvements to the PHP interpreter. This rewrite of the core of PHP came to be known as the ‘Zend Engine’ (named for Zeev and Andi’s first names) and

[1] PHP was created in 1994: http://php.net/en/history.php
