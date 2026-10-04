
## Introduction and Installation Configuration

## AMP Installers

Now we've taken your entire Saturday afternoon to install and configure each of these components, we can tell you about some third-party software programs that will complete the installation for you. You can find an extended list of these types of installers at www.httpscripts.com.

## Foxserv

This is an Apache/MySQL/PHP installer that can be found at www.foxserv.net. It is offered as an open source program and is free to the general public. Foxserv allows you to customize your configuration files during installation and also allows for PEAR modules to be downloaded. (You can read more about the use of PEAR in Appendix H) This installer is compatible with both Windows and Linux systems.

## PHPTriad

This is another open source installer that is available at no charge. It is available for download at http://sourceforge.net/projects/phtriad/ but is currently applicable to Windows systems only. Along with Apache, PHP, and MySQL, the package includes Perl and phpMyAdmin (another powerful database administration system we discuss in Chapter 3).

## NuSphere Technology Platform

The creators of the popular PHP editing program PHPEd have also developed an AMP installer, which they provide as a free download on their Web site at www.nuspphere.com. This installer covers Apache, MySQL, PHP, and PERL, and offers downloads for both Windows and Linux systems.

## Summary

Now, you should be well versed in AMP and open source. You know that the abbreviation AMP refers to Apache, MySQL, and PHP, all of which work together to help you develop dynamic Web sites.

So now you've installed, configured, and tested the installation for Apache, MySQL, and PHP should be ready to start making some Web sites!

## Part II: Movie Review Web Site

### Chapter 2: Creating PHP Pages

### Chapter 3: Using PHP with MySQL

### Chapter 4: Using Tables to Display Data

### Chapter 5: Form Elements: Letting the User Work with Data

### Chapter 6: Letting the User Edit the Database

### Chapter 7: Validating User Input

### Chapter 8: Handling and Avoiding Errors

## Creating PHP Pages

In this chapter, we discuss the basics of PHP and start you on your way to creating your first complete Web site, one featuring movie reviews. After you complete your Web site, your visitors will be able to locate information about a particular movie, and you will be able to program in PHP.

In this chapter, we cover the following basic PHP commands and structures:

- Using echo to display text
- Formatting text with both HTML and PHP
- Constants and variables
- Using a URL to pass variable values
- Sessions and cookies
- HTML forms
- if/else statements
- Includes
- Functions
- Arrays and foreach
- while and do/while

By the end of this chapter, if you actually try the “Try It Out” exercises, you will be able to create a simple login form, give your users an option to either see a review of your favorite movie or see a list of your top favorite movies, and offer them a numbered list of your movies based on how many they decide they want to see. You can even alphabetize the list for them, if so desired.

## Chapter 2

## Overview of PHP Structure and Syntax

PHP programs are written using a text editor, such as Notepad or WordPad, just like HTML pages. However, PHP pages, for the most part, in a .php extension. This extension signifies to the server that it needs to parse the code before sending the HTML code to the viewer's Web browser.

In a five-star restaurant, patrons use a plate full of beautiful food served up just for them. They don't see where the food comes from, nor how it was prepared. In a similar fashion, PHP fits right into your HTML code and is invisible to the people visiting your site.

## How PHP Fits with HTML

We assume that you know some HTML before you embark on your PHP/Apache/MySQL journey, and you've undoubtedly seen how JavaScript code and other languages are interspersed within the HTML code in an HTML page. What makes PHP so different is it not only allows HTML pages to be created by file; it is invisible to your Web sites. The only thing they see when they view the source of your code is the resulting HTML output. This gives you more security for your PHP code and more flexibility in writing it.

HTML can also be written inside the PHP section of your page; this allows you to format text while keeping blocks of code together. This will also help you write organized, efficient code, and the browser (and, more important, the viewer) won't know the difference.

PHP can also be written as a standalone program, with no HTML at all. This is helpful for storing your connection variables, redirecting your visitors to another page of your site, or performing other functions that we discuss in this book.

## The Rules of PHP Syntax

One of the benefits of using PHP is that it is relatively simple and straightforward. As any programming language, there is usually more than one way to perform the same function. Once you feel comfortable writing some PHP programs, you can research shortcuts to make yourself and your code more efficient. For the sake of simplicity, we cover only the most common uses, rules, and functions of PHP.

You should keep in mind these two basic rules of PHP:

- PHP is denoted in the page with opening and closing tags as follows:

```php
<?php
?>
```

- PHP lines end with a semicolon, generally speaking:

```php
<?php
// First line of code goes here;
// Second line of code goes here;
// Third line of code goes here;
?>
```

## Creating PHP Pages

Comments can be added to your program as we just did through slashes ( // ) for one-liners or /* and */ for opening and closing comment tags that may extend over several lines of code. Indents don't matter, and, speaking, neither line returns. This gives you freedom as a programmer, but a little freedom be a dangerous thing, as we discuss in the next section.

And you have it! You're an expert. Okay—there might be a few more things you need to learn, but this gets you started.

## The Importance of Coding Practices

Before we jump in, it is important to realize how the structure of your code can affect your program. As far as the Web server parsing the PHP code, the structure of your code doesn't matter. To the server, your code will show up as one continuous line regardless of tabs, indents, and line returns. But to the human eye, how well your code is organized really makes a difference.

Take a look at these examples:

```php
<?php
if (true) {
    echo "Hello";
} else {
    echo "World";
}
?>
```

## Chapter 2

In addition, while there may be more than one syntax for accomplishing the goal, you should simply pick one and stick with it throughout your program. For example, as far as PHP is concerned, the two snippets mean the same thing:

```php
<?php
?>
```

```php
<?php
?>
```

## What Makes a Great Program?

It's important to follow good coding practices for three reasons:

- For efficiency: The easier your code is to read and follow, the easier it will be to keep track of where you are with your code, and the quicker it will be
- For debugging: Knowing where your problem lies is a major debugging tool. If you have comments, you can easily follow your logic, and if you have line numbers and consistent formatting, you can easily scan your document to pinpoint a trouble area.
- For future expansions and modifications: Using comments in your code is especially important for future changes, not all of us can remember the logic behind the code that was written years or even months ago. Also, if you are working on a project that involves a team, if everyone using the same coding styles, it will be much easier to make changes or additions to someone else's work down the road.

## Creating Your First Program

You can't get much simpler than this first program, but try out to get a feel for what the results like. The PHP function echo, seen in the material that follows, is one of the most commonly used PHP functions and that, undoubtedly, will become intimate with it. It is used to send text (or variable values or varieties of other things) to the browser.
