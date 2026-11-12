
## Designing database applications

One powerful aspect of PHP is its ability to interface with various databases. Most people who use PHP use the MySQL database, which is the database I focus on throughout this book.

Using a database, you can store large volumes of information, and using PHP, you can give your Web site users access to this data. For example, you may have a database containing user preferences for the Web site, such as content layout or font colors. You store this information in the database. Then when a user connects to your Web site and logs in with a username, PHP looks up the user's preferences in the database.

PHP dynamically generates Web pages, so if you want to provide customized font colors, for example, you would include PHP code that writes out a FONT tag in HTML, containing the colors chosen in the user preferences. Then when the client computer receives the Web page, it contains the color information already hardcoded into it.

Similarly, you can retrieve more complex information from a database. For example, suppose a university wants to include an office directory on its Web site. It wants users to be able to type a last name into the online directory and then see a Web page displaying a list of professors with that last name, along with e-mail addresses and office locations. You can easily do this with PHP: You take the requested last name, perform a database search, and retrieve all the rows in the table (a row is the preferred term for a record) where the last name column contains the requested value.

Then the dynamic content begins. In your PHP code, you display an HTML line containing the professor's name, e-mail address, and office location that the program found in the database. You might use an HTML table to carefully format the data. And you might even include an anchor tag <A that contains mailto: HREF around the e-mail address so the user can click the link to send an e-mail to that address. All this dynamic HTML is up to your PHP code, which displays the formatted HTML; the data in the database doesn't contain any HTML code -- just data. Again, that's what dynamic content is all about.

## Chapter 2: Writing Server-Side Scripts

### In This Chapter

- Exploring the PHP processor
- Creating PHP scripts
- Using appropriate filename extensions
- Embedding HTML in a PHP script
- Dealing with errors in your PHP code

When you’re surfing the Web in your free time, you occasionally come to Web sites that request that you first log in. If you look at the HTML source for such Web sites, you might expect to see a silly little JavaScript program with a password hardcoded right in the script. But the truth is that most (better!) Web sites don’t use such a simple script.

A simple JavaScript program is a *client-based script*, meaning the code runs on the user’s computer — the client computer. These scripts are freely readable by Web surfers. The alternative to running scripts on the client computer is to use a server-side script. A *server-side script* is a program that runs on the server, the computer that dishes out Web pages to users. When you log into a server, the server runs its own scripts, including those that test for a password.

Many languages are available for server-side scripts, but at least only one language allows you to write scripts right into the HTML files. This language is called PHP, which is an acronym for PHP: Hypertext Preprocessor. Yup, the letter *P* stands for PHP, which is an acronym whose first letter stands for PHP, which ... well, you get the idea. Bizarre? Yes. True? Still yes.

PHP is a *preprocessor* because it processes an HTML file before the Web server dishes out the HTML page. Typically, without the presence of PHP, the Web server receives a request from the client computer (the Web surfer’s computer) for a particular file, and the server then happily sends back the page as is. But with PHP present, first the PHP preprocessor reads the HTML file, looking for statements written in the PHP language. It then executes these statements and spits out a possibly different-looking, final HTML page. The Web server then happily sends this page to the client machine. Figure 2-1 shows you this process. (Note that in this minibook I refer to the PHP “processor” simply because it’s a bit shorter than “preprocessor.”)

![](img/3f967ab8a8fddc723173059f56621648_383_0.png)

As you study PHP, remember that you’re writing a file that is processed by the PHP preprocessor and that the output from the processor is a valid HTML file. Keeping this in mind will help you stay sane during your development, because at times you will start to feel like you’re working on some abstracted level several steps away from the actual HTML files. That’s because you are, and it can get a little mind-numbing at times. But fear not; I’m here to help you get through it.

![](img/3f967ab8a8fddc723173059f56621648_383_1.png)

When you're doing a lot of PHP development, you should have access to the online PHP manual. This manual is an excellent supplement to the For Dummies book in your hands. You can find it at www.php.net/docs.php. From there, you can access the manual in many different languages in various file formats. For an English version in online HTML format, you can go right to www.php.net/manual/en/. And incidentally, you probably already noticed from these URLs that the main PHP home page is www.php.net.

Figure 2-1: The PHP processor reads in a file containing PHP code and spits out a valid HTML file.

![](img/3f967ab8a8fddc723173059f56621648_383_2.png)

## Referencing self-referential references

The idea of an acronym, PHP, referring to itself, PHP: Hypertext Preprocessor, may seem a little bizarre. People call this a self-referential or recursive acronym. Really, it doesn't make much sense. You could just as easily call it ZHP and claim it stands for ZHP: Hypertext Preprocessor. But the truth is, the acronym PHP originally stood for Personal Home Page. But as the language advanced, people realized the name Personal Home Page wasn't very descriptive. So they decided to change the name to something more meaningful. The HP part was easy, Hypertext Preprocessor. But oh, what to do with that first letter P? Apparently they couldn't think of a good name, so they made it a recursive acronym. The P now stands for nothing at all!

### Exploring the PHP Processor

The PHP processor is a stand-alone program that runs on the Web server, independently from the Web server software. When a Web browser requests from the server a file ending in .php, the Web server software calls the PHP processor and passes to the processor the HTML file containing the PHP code.

The PHP processor takes as input the name of a file, and it writes out a new file. It writes the file to the standard output, which means that if you run the PHP program from a command line (such as in Unix or Linux), you see the output right on the screen.

Because PHP is a stand-alone program, nothing is stopping you from running it from the command prompt, passing in a file with PHP code, and checking out the resulting HTML. Here's a quick PHP session. Using my favorite text editor, I created a file that looks like this:

```php
<?php
    print "Hi\n";
?>
```

This is a simple PHP program that prints out a Hi message. The first line tells the PHP processor that PHP code follows. The next line tells the PHP processor to print something, in this case, the word Hi followed by a new-line. The line ends with a semicolon, as do all PHP lines inside the <?php and ?> tags. Finally, ?> tells the PHP process that the PHP code ends.

I saved this file as myfile.php. Next, I type the following line at the Linux command prompt:

```
php myfile.php
```

The PHP processor reads the myfile.php file and displays the following output on-screen (you might see different numbers if you’re using a different version of PHP):

```
X-Powered-By: PHP/4.1.2
Content-type: text/html

Hi
```

You can see that the processor output the word Hi. It also output a carriage return, which is the \n inside the double quotes. (The \n stands for newline.)

But what’s all that junk that appears at the beginning of the output? These “junk” lines at the beginning of the output tell the browser what type of information follows. In this case, HTML follows, which is what text/html means. The other part, X-Powered-By, tells how the HTML was generated, in case the browser wants this information.

Say you take the myfile.php file and put it on a Web server, and then go to a client computer and browse to the .php file like so:

```
www.jeffcogswell.com/myfile.php
```

You see the word Hi appear in your Web browser. Now when you view the source for the file in the Web browser, you see this:

```
Hi
```

The output includes a newline at the end, exactly as the PHP program requested. This is getting pretty nifty!

For a .php file to get processed, the PHP processor must be present on the Web server. The Web server also must be configured to send .php files through the PHP processor.

You can’t simply open a .php file in your browser. If you store a local .php file on your computer and open it in the browser, the browser treats it as an .html file and ignores all your PHP code.

If you want to try out some PHP at home, you can use one of the following two methods:
