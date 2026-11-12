If you want to explore the PDF features of PHP, you can visit www.php.net/manual/en/ref.pdf.php. This page includes several examples as well as a link to the page describing the PDFLib library.

In this book, I cover only the function categories that don't require a special library. (The exception is in Book VI, where I discuss PHP in conjunction with MySQL. To use MySQL functions in PHP, you need to have MySQL installed, which is a separate installation.) If you're interested in using the additional libraries, the PHP online manual (www.php.net/docs.php) provides the information you're looking for.

# Adding Dynamic Content

The most important application of PHP is dynamic content. Using PHP, you can create Web sites that give out customized pages based on different criteria, such as who the user is or what information the user is looking for.

For example, suppose you're writing a page that lets users of your Web server write an e-mail message. The user types the e-mail message into an edit box and then clicks Send. Now suppose another page opens showing the name of the recipient of the e-mail and a friendly confirmation that the message has been sent. How can you generate a page that shows the recipient's name? When you create the site, you can't create millions of Web pages, each with a different recipient name and then just pick the correct one later on when a user types in a message. That's akin to leaving a million monkeys alone at a typewriter for a million years to see if they accidentally write a Shakespearean play. Instead, you want to dynamically generate a Web page that prints out the recipient's name.

Instead, you want to create a Web site that dynamically builds each Web page, filling it with pertinent information, such as the current e-mail message the user is viewing. How do you do that? Through PHP!

When you write PHP code, you are writing a program that runs within a Web page, and that program can modify the page, customizing it as needed. This is what dynamic content is all about.

For example, take a look at the todaysdate.php file that follows:

```
<html>
<head>
<title>Today's Date</title>
</head>
```