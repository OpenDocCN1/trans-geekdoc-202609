
This script is very simple, but let’s break it down line-by-line to explore a few features of PHP.

The first line tells the PHP engine to expect some PHP code to follow:

```
<?php
```

Why do you need this line? This is due to the fact that PHP can be embedded within HTML Web pages. When the PHP engine first starts processing the page, it assumes it’s dealing with plain old HTML until told otherwise. By using the PHP delimiter, `<?php`, you’re telling the PHP engine to treat anything following the `<?php` as PHP code, rather than as HTML.

The next line displays the message “Hello, world!”:

```
echo "Hello, world! ";
```

PHP’s `echo()` statement takes a string of text — in this case, "Hello, world!" — and sends it as part of the Web page to the browser. The browser then displays the “Hello, world!” text to the visitor. Notice the semicolon (`;`) at the end of the line; this tells PHP that you’ve reached the end of the current statement, and it should look for a new statement (or the end of the PHP code) to follow.

`echo()` doesn’t have to be given a string of text; it can display anything that can be displayed, such as numbers or the results of expressions. You find out more about data types and expressions in the next chapter.

An alternative to `echo()` is the `print()` statement, which works in exactly the same way except that it also returns a value (`true`). Generally speaking, you can use `print()` instead of `echo()` in your code if you prefer.

The final line of your simple script tells the PHP engine that it’s reached the end of the current section of PHP code, and that the following lines (if any) contain plain HTML again:

```
?>
```

## Embedding PHP within HTML

As you’ve gathered by now, one of the nice things about PHP is that you can embed PHP code within HTML. In fact, each `.php` script that you write is essentially treated as an HTML page by default. If the page contains no `<?php ... ?>` tags, the PHP engine just sends the contents of the file as-is to the browser.

## Try It Out Creating a Stylish Page

You can use this feature to make your “Hello, world!” example prettier by adding a proper HTML header and footer and including a CSS style sheet. Enter the following code and save it as `hello_pretty.php` in your document root folder:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Hello</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1><?php echo "Hello, world!"; ?></h1>
</body>
</html>
```

Next, enter the following CSS code and save it as common.css in the same folder:

```
/* Page body */
body { font-family: Arial, Helvetica, sans-serif; }

/* Definition lists */
dl { width: 100%; margin: 2em 0; padding: 0; clear: both; overflow: auto; }
dt { width: 30%; float: left; margin: 0; padding: 5px 9.5% 5px 0;
border-top: 1px solid #DDDB7; font-weight: bold; overflow: auto;
clear: left; }
dd { width: 60%; float: left; margin: 0; padding: 6px 0 5px 0; border-top:
1px solid #DDDB7; overflow: auto; }

/* Headings */
h1 { font-weight: bold; margin: 35px 0 14px; color: #666; font-size: 1.5em; }
h2 { font-weight: bold; margin: 30px 0 12px; color: #666; font-size: 1.3em; }
h3 { font-weight: normal; margin: 30px 0 12px; color: #666; font-size:
1.2em; }
h4 { font-weight: bold; margin: 25px 0 12px; color: #666; font-size: 1.0em; }
h5 { font-weight: bold; margin: 25px 0 12px; color: #666; font-size: 0.9em; }

/* Forms */
label { display: block; float: left; clear: both; text-align: right;
margin: 0.6em 5px 0 0; width: 40%; }
input, select, textarea { float: right; margin: 1em 0 0 0; width: 57%; }
input { border: 1px solid #666; }
input[type=radio], input[type=checkbox],
input[type=reset], input[type=button], input[type=image] { width: auto; }
```

Run your new PHP script by typing http://localhost/hello_pretty.php into your browser's address bar. You should see a more stylish page, such as the one shown in Figure 2-13.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_63_0.png)

Figure 2-13

## How It Works

This example shows how you can embed PHP within an HTML page. The PHP code itself is exactly the same — echo "Hello, world!" — but by surrounding the PHP with HTML markup, you’ve created a well-formed HTML page styled with CSS.

First, a DOCTYPE and the opening html tag are used to declare that the page is an XHTML 1.0 Strict Web page:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
```

Next, the head element of the Web page gives the page a title — “Hello” — and links to a style sheet file, common.css:

```
<head>
<title>Hello</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
```

Finally, the body element includes an h1 (top-level heading) element containing the output from the PHP code — echo "Hello, world!"; — and the page is then finished with a closing html tag:

```
<body>
<h1><?php echo "Hello, world!"; ?></h1>
</body>
</html>
```

Note that you don’t need to have the `<?php` and `?>` tags on separate lines. In this case, the tags and enclosed PHP code are all part of a single line.

Meanwhile, the common.css style sheet file contains selectors to style some common HTML elements — including the h1 heading used in the page — to produce the nicer-looking result.

> Keep this common.css file in your document root folder, because it’s used throughout other examples in this book.

If you view the source of the resulting Web page in your browser, you can see that the final page is identical to the original HTML markup, except that the PHP code — `<?php echo "Hello, world!"; ?>` — has been replaced with the code’s output (“Hello, world!”). The PHP engine only touches the parts of the page that are enclosed by the `<?php ... ?>` tags.

## Enhancing the Script Further

The “Hello, world!” example shows how you can write a simple PHP script, but the code does nothing useful — you could just as easily achieve the same effect with a simple HTML page. In this section you enhance the script to display the current time. In doing so, you move from creating a static Web page to a dynamic page; a page that changes each time you view it.

Here’s the modified “Hello, world!” script:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Hello</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>
<?php
$currentTime = date( "g:i:s a" );
echo "Hello, world! The current time is $currentTime";
?>
</h1>
</body>
</html>
```

Save the script as hello_with_time.php and open its URL in your browser to run it. You’ll see something along the lines of Figure 2-14.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_65_0.png)

Figure 2-14

If, when running this script, you see a lengthy warning message telling you that it is not safe to rely on the system’s time zone settings, you need to configure PHP’s time zone. See the “Setting Your Time Zone” section earlier in the chapter for instructions.

The majority of the code is exactly the same as before. The only difference is the PHP code itself:

```
<?php
$currentTime = date( "g:i:s a" );
echo "Hello, world! The current time is $currentTime";
?>
```

The first line of PHP code takes the current time and formats it as a readable string of text, then stores this string of text in a variable called $currentTime. (Variables are containers that store data. You learn all about them in the next chapter.) To format the time, the script uses the built-in date() function. The string of characters between the quotation marks tells PHP how to format the time, as follows:

- g, i, and s tell PHP to output the current hour, minute, and second, respectively
- a tells PHP to display either “am” or “pm” as appropriate
- The colons (:) and the space character are not processed by the date() function, so they’re displayed as-is

You learn all the ins and outs of PHP's date() function in Chapter 16.

Then the second line of code displays the “Hello, world!” message, including the current time. Reload the page in your browser and you’ll see the time change.

Notice how PHP lets you include variable names within text strings, as is the case with the $currentTime variable. This makes it easy for you to create text messages containing dynamic information.

This simple example is the essence of a dynamic Web page — a page whose content is potentially different each time the page is viewed. In this book you learn how to use PHP to add all sorts of dynamic content to your sites.

## Using Comments to Make Code More Readable

To round off this chapter, you learn about another basic feature of PHP: comments. A comment is simply text that is ignored by the PHP engine. The purpose of comments is to let you add messages to yourself (and other programmers) that explain what your code does. It’s always a good idea to add comments to your code, even if you’re the only programmer working on it. Sometimes code that makes sense when you write it can seem as clear as mud in three months’ time, so comments can really help!

PHP supports single-line comments and multi-line comments. To write a single-line comment, start the line with either two slashes (//) or a hash symbol (#). For example:

```
// This code displays the current time
# This code displays the current time
```
