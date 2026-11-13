
equal), < (less than), > (greater than), and != (not equal). That last one also works when comparing text strings, by the way.

Another type of loop that is designed specifically to handle examples like that above, where we are counting through a series of values until some condition is met, is called a for loop. Here's what they look like

```
for ( initialize; condition; update ) {
    // statement(s) to execute over
    // and over as long as condition
    // remains true after each update
}
```

Here's what the above while loop example looks like when implemented as a for loop:

```
for ( $count = 1; $count <= 10; $count++ ) {
    echo( "$count " );
}
```

## Multi-Purpose Pages

Let's say you wanted to construct your site so that it showed the visitor's name at the top of every page. With our custom welcome message example above, we're halfway there already. Here are the problems we'll need to overcome to extend the example into what we need:

- We need the name on every page of the site, not just one.

- We have no control over which page of our site users will view first.

The first problem isn't too hard to overcome. Once we have the user's name in a variable on one page, we can pass it with any request to another page by adding the name to the query string of all links:

```
<a href="newpage.php?name=<?php echo(urlencode($name)); ?>"> A link </a>
```

Notice that we've embedded PHP code right in the middle of an HTML tag. This is perfectly legal, and will work just fine. A shortcut exists for those times when you simply want to echo a PHP value in the middle of your HTML code. The shortcut looks like this:

```
<a href="newpage.php?name=<?=urlencode($name)?>"> A link </a>
```

The tags <?= ... ?> perform the same function as the much longer code <?php echo( ... ) ; ?>. This is a handy shortcut that I'll use several times through the rest of this book.

You're familiar with the echo function, but urlencode is probably new to you. This function takes any special characters in the string (for example,
spaces) and converts them into the special codes they need to be in order to appear in the query string. For example, if the $name variable had a value of "Kevin Yank", then as spaces are not allowed in the query string, the output of urlencode (and thus the string output by echo) would be "Kevin+Yank". This would then be automatically converted back by PHP when it created the $name variable in newpage.php.

Okay, so we've got the user's name being passed with every link in our site. Now all we need is to get that name in the first place. In our welcome message example, we had a special HTML page with a form in it that prompted the user for his or her name. The problem with this (identified by the second point above) is that we couldn't -- nor would we wish to -- force the user to enter our Web site by that page every time he or she visited our site.

The solution is to have every page of our site check to see if a name has been specified, and prompt the user for a name if necessary. This means that every page of our site will either display its content, or a prompt the user to enter a name, depending on whether the $name variable is found to have a value. If this is beginning to sound to you like a good place for an if-else statement, you're a quick study!

We'll refer to pages that are capable of displaying completely different content depending on some condition, as "multi-purpose pages". The code of a multi-purpose page looks something like this:

```
<html>
<head>
<title> Multi-Purpose Page Outline </title>
</head>
<body>
<?php if (condition) { ?>
<!-- HTML content to display if condition is true -->
<?php } else { ?>
<!-- HTML content to display if condition is false -->
<?php } ?>
</body>
</html>
```

This may confuse you at first, but in fact this is just a normal if-else statement with HTML code sections that depend on the condition, instead of PHP statements. This example illustrates one of the big selling points of PHP: that you can switch in and out of "PHP mode" whenever you like. If you think of <?php as the command to switch into "PHP mode", and ?> as the command to go back into "normal HTML mode", the above example should make perfect sense.

There's an alternate form of the if-else statement that can make your code more readable in situations like this. Here's the outline for a multi-purpose page using the alternate if-else form:

```
<html>
<head>
<title> Multi-Purpose Page Outline </title>
</head>
<body>

<?php if (condition): ?>

<!-- HTML content to display if condition is true -->

<?php else: ?>

<!-- HTML content to display if condition is false -->

<?php endif; ?>

</body>
</html>
```

Okay, now that we have all the tools we need in hand, let's look at a sample page of our site (samplepage.php in the code archive located at http://www.sitepoint.com/books/):

```
<html>
<head>
<title> Sample Page </title>
</head>
<body>

<?php if ( !isset($name) ): ?>

<!-- No name has been provided, so we
prompt the user for one. -->

<form action="<?= $PHP_SELF ?>" method="get">
Please enter your name: <input type="text" name="name"
/>
<input type="submit" value="GO" />
</form>

<?php else: ?>

<p>Your name: <?=$name?></p>

<p>This paragraph contains a <a
href="newpage.php?name=<?=urlencode($name)?>">link</a>
that passes the name variable on to the next
document.</p>
<?php endif; ?>
</body>
</html>
```

There are two new tricks in the above code, but overall you should be pretty comfortable with the way it works. First of all, we’re using a new function called isset in the condition. This function returns (outputs) a value of true if the variable it is given has been assigned a value (i.e. if a name has been provided), and false if the variable does not exist (i.e. if a name has not yet been given). The exclamation mark (also known as the negation operator, or the not operator) that appears before the name of the function reverses the returned value from true to false or vice-versa. Thus, the form is displayed when the $name variable is not set. The second new trick is the use of the variable $PHP_SELF to specify the action attribute of the form tag. This variable is one of several that PHP always gives a value to automatically. In particular, $PHP_SELF will always be set to the URL of the current page. This gives us an easy way to create a form that, when submitted, will load the very same page, but this time with the $name variable specified.

If we structure all the pages on our site in this way, visitors will be prompted for their name by the first page they attempt to view, whichever page this happens to be. Once they enter their name and click "GO", they’ll be presented with the exact page they requested. The name they entered is then passed in the query string of every link from that point onward, ensuring that they are prompted only the once.

## Summary

In this chapter, we’ve had a taste of the PHP server-side scripting language by exploring all the basic language features: statements, variables, operators, and control structures. The sample applications we’ve seen have been pretty simple, but don’t let that dissuade you. The real power of PHP is in the hundreds of built-in functions that let you do everything: access data in a MySQL database, send e-mail, dynamically generate images, and even create Adobe Acrobat PDF files on the fly.

In Chapter 4, we’ll delve into the MySQL functions in PHP, to show how to publish the joke database that we created in Chapter 2 on the Web. This will set the scene for the ultimate goal of this series – creating a complete content management system for your Web site in PHP and MySQL.

## Publishing MySQL Data on the Web

This is it -- the stuff you signed up for! In this chapter, you'll learn how to take information stored in a database and display it on a Web page for all to see. So far you have installed and learned the basics of MySQL, a relational database engine, and PHP, a server-side scripting language. Now you'll see how to use these two new tools together to create a true database-driven Web site!

## A Look Back at First Principles

Before we leap forward, it’s worth a brief look back to remind ourselves of the goal we’re working toward. We have two powerful, new tools at our disposal: the PHP scripting language, and the MySQL database engine. It’s important to understand how these two will fit together.

The whole idea of a database-driven Web site is to allow the content of the site to reside in a database, and for that content to be dynamically pulled from the database to create Web pages for people to view with a regular Web browser. So on one end of the system you have a visitor to your site who uses a Web browser to load http://www.yoursite.com/, and expects to view a standard HTML Web page. On the other end you have the content of your site, which sits in one or more tables in a MySQL database that only understands how to respond to SQL queries (commands).

![](img/8345fab290b1af6acfffd37582f5eaf4_64_0.png)

As shown in the diagram above, the PHP scripting language is the go-between that speaks both languages. It processes the page request and fetches
