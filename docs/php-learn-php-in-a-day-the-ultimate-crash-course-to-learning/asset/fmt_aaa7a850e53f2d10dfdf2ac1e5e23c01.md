
# Preface

## 1. Introduction to the Course

Welcome to this Introductory Course to PHP. Throughout this course, you will learn the basics behind using PHP in your own projects. You will be introduced to some of the most commonly used functions and methods as well as PHP best practices. This course will mostly teach by example, emphasizing a “show, don’t tell” approach. We will guide you through different real-world examples of PHP applications and explain every step of the process so that you understand not only how, but also why we are writing our application the way we are.

The course is structured around different chapters, where each chapter focuses on a particular aspect of programming with PHP. At the end of each chapter, there will be a chapter summary and a chapter exercise that will test all the skills you have learned in the chapter thus far, as well as build on top of previous knowledge.

You will be presented with code at every step of the way. Code will be easily recognized as it will be separated from the rest of the text and formatted differently. Here is an example of a code block:

![](images/00001.jpeg)

With all of that out of the way, let’s get started with the course!

# Chapter One – Introduction, Setup and “Hello World”

## Introduction to PHP

PHP stands for PHP: Hypertext Preprocessor (originally it meant Personal Home Page) and is one of the most widely used web programming languages (installed on more than 250 million websites). It is similar to languages such as C. But let’s not spend too much time in historical references and get to work!

## Setting up Our Work Environment

In order to start working with PHP on your local computer, you need to install a development environment. Why is this so? PHP is a server-side language; so in essence, you need to install a “local server” on your computer in order to run PHP code. There are many solutions that provide PHP packages, but the most common form is known as a LAMP bundle. There are many LAMP bundles out there that fit different operating systems. The most common are:

*   **XAMPP** – an Apache distribution with PHP, MySQL and Perl. Support available for Windows, Linux and Mac;
*   **WAMP** – specific for Windows;
*   **MAMP** – specific for Mac;

Pick one, type the name in Google, follow the download link and instructions and you’ll be all set to go.

Also, you will need some form of text editor. There are many free and paid programs you can find. The one we are using for this course is called **Notepad++**.

## Our Very First PHP file

After having installed your LAMP bundle, you undoubtedly want to create your very first PHP file. If you haven’t already, make sure that you have Apache and MySQL active. To check, go to the control panel of your LAMP setup and you should see something like this:

![](images/00002.jpeg)

Navigate to the installation directory of your LAMP bundle. In my case it looks something like: `C:\xampp\htdocs`. `htdocs` is the directory that contains all of your websites. Generally, for the sake of clarity, I like creating a `websites` directory inside of `htdocs` and working from there. In either case, create a new folder for your website and give it a name. Try to refrain from using spaces (use `_` instead). Inside that folder, create an `index.php` file. Open the file in your text editor and type the following lines of code:

![](images/00003.jpeg)

All PHP code is wrapped within the PHP tags (`<?php ?>`). Notice that we say all PHP code, not all PHP files. That is, you can have things such as HTML inside a `.php` file. More on that in another chapter, though.

Some more rules to keep in mind in terms of syntax:

*   In PHP every statement ends with a semicolon.
*   **Comments:**

    Comments in PHP can be single-line or multi-line. Single line comments start with two backslashes (`//`). Anything placed after these slashes is considered a comment and will not be executed by the compiler. Multi-line comments start with a forward slash and a star and end with a star and forward slash (`/* Comment goes here */`). Again, the compiler will ignore anything placed inside of these symbols.

    Here is an example of comments in code:

    ![](images/00004.jpeg)

    Multi-line comments are usually used for longer descriptions of blocks of code, while single-line comments are used (as in the example above), when you want to describe what a certain line of code does. Multi-line comments can be also useful for debugging. For example, if you have a portion of code that is not working the way you want it to, you can “comment it off” by using multi-line comments and tests bits of it to see what exactly goes wrong.

    There is no rule in PHP that tells you whether to use comments or not to, but it is considered good practice to use comments. If you are going to share your code with other people, you should definitely (and by definitely, we mean always!) use comments. What seems obvious to you will not be so obvious to another coder. Furthermore, even if you are not going to be sharing your code, but are instead just writing some file that you know will be for yourself, you should still make use of comments (even if you don’t comment as extensively as you would if you were sharing). Very often you will find yourself needing to revisit old code and when that happens you would want to quickly be able to remember what you were doing and why you were doing it. Although they don’t add functionality to your code, comments are just as important as the code you write, so don’t ignore them!

Okay, after that digression, let’s return to our first PHP file. Open your web browser of choice and enter the following URL: `localhost/websites/your_folder_name_here/index.php` or remove the `websites` if your new website is in the `htdocs` folder.

You should see the words “Hello World!” being displayed at the top of the web page.

Hurray! Our very first PHP file is done! But that wasn’t very interesting, was it? Let’s move on to chapter two where we learn about the different types of variables inside PHP and start having some more fun!

# Chapter Two – Variables

## Introduction to Variables

### Basics

In PHP, variables are declared using the dollar sign (`$`):

![](images/00005.jpeg)

This declares, or creates, the variable. Important to note is that before you create the variable, it is considered unset. It doesn’t exist. Kind of intuitive, but this can sometimes lead to some unexpected errors as we are going to see later on.

Here we have created a string variable (note that we don’t declare the type). We’ll look at the different variable types a bit later in this chapter.

### Rules

There are rules to keep in mind when creating variables inside of PHP. We’ll list all of them and after that we will take a look at code that shows these. Here are the basic rules:

*   Variable names start with a letter or underscore;
*   Variable names cannot start with a number;
*   A variable name can have any number of letters, underscores or numbers;
*   Valid letters are all ASCII hexadecimal letters from 00 to FF;

Let’s take a look at an example of code declaring variables:

![](images/00006.jpeg)

If we test our file we will get the following error message:

![](images/00007.jpeg)

This tells us that we have an error in declaring our variable.

## Variable Types and Typecasting
