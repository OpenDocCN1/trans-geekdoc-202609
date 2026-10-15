
The Manage Sites dialog box handles only the site settings, such as server details and the location of files. It does not create a backup of the files within a site. You need to do that separately. Similarly, selecting a site and clicking the Remove button removes only the site definition. It does not delete the site files from your computer. Back up your site definitions regularly. On Windows, they’re stored in the Windows Registry, so restoring them is impossible without a backup. On Mac OS X, you can recover them from a copy of Macintosh HD:<username>:Library:Application Support:Adobe:Common:11:Sites:Site Prefs.

### What You Have Learned

***In this lesson, you have:***

• Installed and tested a local PHP development environment consisting of a web server, PHP, MySQL, and phpMyAdmin ([pages 28–32](#ch02.html#page_28))

• Checked and changed the configuration settings, if necessary ([pages 32–39](#ch02.html#page_32))

• Learned the difference between links relative to the document and links relative to the site root ([page 40](#ch02.html#page_40))

• Seen how to create virtual hosts ([pages 40–47](#ch02.html#page_40))

• Defined and tested a PHP site in Dreamweaver CS5 ([pages 47–54](#ch02.html#page_47))

• Seen how to edit, back up, and restore site definitions ([pages 54–56](#ch02.html#page_54))

Where you go from here depends on your experience and interests. The next lesson provides an introduction to the most important features of PHP for the benefit of readers who are new to the subject or those who need a refresher. If you’re familiar with PHP, you can jump ahead to [Lesson 4](#ch04.html#ch04) to experiment with WordPress.

## Lesson 3. A Quick Crash Course in PHP

### **What You Will Learn**

***In this lesson, you will:***

• See how to embed PHP code in a page and store values in variables and arrays

• Discover how PHP gathers information from an online form

• Explore the use of conditional statements to make decisions

• Learn about functions, objects, and resources

• See how PHP handles arithmetical calculations

• Explore the use of loops for repetitive tasks

• Include external files into a web page

• Decode the mysteries of PHP error messages

### **Approximate Time**

The time required for this lesson depends on your previous experience. Don’t attempt to memorize everything on a first read through; instead, refer back to this lesson when you need to refresh your understanding of PHP.

### **Lesson Files**

***Media Files:***

images/birds_of_a_feather.jpg

styles/examples.css

styles/include_examples.css

***Starting Files:***

lesson03/start/includes_start.php

lesson03/test_includes/year_01.inc.php

***Completed Files:***

lesson03/completed/function_01.php

lesson03/completed/function_02.php

lesson03/completed/function_03.php

lesson03/completed/function_04.php

lesson03/completed/function_05.php

lesson03/completed/function_06.php

lesson03/completed/function_07.php

lesson03/completed/get_01.php

lesson03/completed/get_02.php

lesson03/completed/includes_01.php

lesson03/completed/includes_02.php

lesson03/completed/includes_03.php

lesson03/completed/includes_04.php

lesson03/completed/includes_05.php

lesson03/completed/includes_06.php

lesson03/completed/includes_07.php

lesson03/completed/loops_01.php

lesson03/completed/loops_02.php

lesson03/completed/loops_03.php

lesson03/completed/loops_04.php

lesson03/completed/loops_05.php

lesson03/completed/loops_06.php

lesson03/completed/loops_07.php

lesson03/completed/post_01.php

lesson03/completed/post_02.php

lesson03/completed/post_03.php

lesson03/completed/post_04.php

lesson03/completed/quotes_01.php

lesson03/completed/quotes_02.php

lesson03/completed/quotes_03.php

lesson03/completed/quotes_04.php

lesson03/completed/quotes_05.php

lesson03/completed/strings_01.php

lesson03/completed/strings_02.php

lesson03/completed/strings_03.php

lesson03/completed/time.php

lesson03/test_includes/header_01.html

lesson03/test_includes/header_02.html

lesson03/test_includes/year_02.inc.php

lesson03/test_includes/year_03.inc.php

PHP makes a website dynamic through the ability to organize and manipulate information drawn from various sources, such as an online form, database, or even another website.

This lesson is aimed principally at readers who have no PHP experience, but it should also be a useful refresher if your knowledge is a little rusty or uncertain. It provides you with the basic knowledge that you need to start working with PHP. Skim each section, and work through the various exercises to get a basic feel for how different features work. Then move on to the rest of the book. Come back to this lesson when you need reminders of the language details.

*PHP captures and processes the input of online forms.*

![Image](graphics/fig03_01.jpg)

### **How PHP Makes Pages Dynamic**

PHP uses a number of techniques common to most programming languages:

• *Variables* store information that isn’t fixed or known in advance.

• *Arrays* store multiple values, usually of related information.

• *Conditional statements* make decisions, based on such things as the size of a number, the date, or whether something is true.

• *Functions* perform tasks, such as transforming and sorting information, or querying a database.

• *Operators* add, subtract, multiply, divide, and so on.

• *Loops* perform repetitive actions.

#### **Embedding PHP code in a page**

The web server needs to recognize PHP code so that it can process it and send the output to the browser. In addition to giving your pages a `.php` filename extension, you signal the start of any PHP code within a page by using the opening PHP tag, which looks like this:

```php
<?php
```

### ![Image](graphics/caution.jpg)**CAUTION!**

There must be no space between any of the characters in the opening tag.

You also have the option of using short opening tags, which consist of the first two characters `<?`. Not all servers support short opening tags. To ensure that your scripts will work everywhere, stick to the full version `<?php`.

You signal the end of a PHP code block with a closing tag, which looks like this:

```php
?>
```

You can have as many PHP code blocks as you like within a page, but you cannot nest them inside each other. In other words, this will work:

**<?php**  

// some PHP code  

**?>**  

<p>A bit of HTML.</p>  

**<?php**  

// some more PHP code  

**?>**

However, the following *won’t* work:

<?php  

// some PHP code  

**<?php**  

**// you cannot do this**  

**?>**  

?>

### ![Image](graphics/note.jpg)**NOTE:**

To save space, most code examples in this book omit the opening and closing PHP tags except where they are needed to show the transition from HTML to PHP and back.

#### **Using comments in PHP scripts**

The examples in the preceding section contain lines beginning with two forward slashes. This is one of the ways of creating a comment in PHP. Comments are ignored by the PHP engine. They’re simply for your benefit.

It’s easy to forget what code is for, so it’s a good idea to add brief comments to your scripts. There are three ways to do so in PHP:

• Everything following two forward slashes is ignored until the end of the line.

• Everything following a hash or number sign (`#`) is ignored until the end of the line.

• Everything between `/*` and `*/` is treated as a comment. This type of comment can stretch across multiple lines.

For example:

// This is a comment  

$name = 'David'; // This comment is alongside code  

\# This is another style of writing a comment  

$name = 'David'; # This type of comment can also go alongside code  

/\* This is a comment that stretches  

   across two lines. \*/

You can also create multiline comments by beginning each line with two forward slashes or the number sign.
