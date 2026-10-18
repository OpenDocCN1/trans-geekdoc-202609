
try
{
    xhrRequest = getXMLHttpRequest();
}
catch(error)
{
    document.write("Cannot run Ajax code using this browser");
}
if(xhrRequest != null)
{
    xhrRequest.onreadystatechange = processYahooNewsFeed;
    xhrRequest.open("GET", "http://rss.news.yahoo.com/rss/topstories", true);
    xhrRequest.send(null);
}
</script>
</body>
</html>

Figure 7.16 shows how the page looks when it has retrieved the first item from the feed. Of course the actual content changes on a daily basis.

FIGURE 7.16 Part of the Yahoo news feed included in a web page using Ajax

![](img/b2471264f405d17994ef173e4b9cec92_240_0.png)

and use it to validate a form containing fields such as credit card numbers, dates and floating point numbers.

### 7.4

In an external file called ‘mouseover.js’, write two JavaScript functions to animate the WebHomeCover logo by using two different versions of the logo and switching between them when the mouse passes over the logo position. Here is an XHTML page that includes an anchor that uses the ‘onmouseover’ and ‘onmouseout’ events to trigger JavaScript functions.

```
<?xml version="1.0"?>
<!DOCTYPE html PUBLIC
    "-//W3C//DTD XHTML 1.1//EN"
    "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
    <head>
        <meta http-equiv="Content-Script-Type" content="text/javascript"/>
        <title>Mouse over logo</title>
        <script type="text/javascript" src="mouseover.js"></script>
    </head>
    <body>
        <!-- File: Exercise7-4.htm -->
        <h2>WebHomeCover Logo</h2>
        <div>
            <a href="http://www.webhomecover.com" onmouseover="mouseOver()" onmouseout="mouseNotOver()">
            <img src="webhomecoverlogo.gif" alt="WebHomeCover logo" id="logo"/>
            </a>
        </div>
    </body>
</html>
```

You will need to implement the ‘mouseOver’ and ‘mouseNotOver’ functions. In these functions, use the getElementById method to navigate to the ‘logo’ (the ‘img’ element) and set the name of the ‘src’ attribute to one of the two image file names (one in each function). The two files (supplied on the CD) are ‘webhomecoverlogo.gif’ and ‘webhomecoverinverted.gif’.

### 7.5

Write an Ajax function called ‘processWeatherFeed’ that accesses the first title element and second description element of an RSS document, concatenates them together and writes their content to an element of an XHTML document. You can use the URIs of various RSS weather feeds. Yahoo, for example, provides a simple RSS URI for weather feeds where you append a ‘p’ request parameter that has the value of a location. For example, the following URI would get the weather in London, UK.

http://weather.yahooapis.com/forecastrss?p=UKXX0085

You can find out the code for any global weather location by navigating from the main Yahoo weather page:

http://weather.yahoo.com/

There are other weather feeds that you can also use, for example RSSWeather.com. Here is the URL for accessing the weather in London using their RSS feed

```
http://www.rssweather.com/icao/EGLC/rss.php
```

You will find other feeds on the web that you may be able to connect to, depending on how they are configured. Remember that all RSS feeds use the same XML document structure, so you can create a generic function that is able to read data from any RSS feed, not just news or weather as we have done so far.

### SUMMARY

In this chapter, we built on the basics of JavaScript syntax introduced previously to explore some aspects of DHTML, form validation and Ajax. We began the chapter by describing some features of JavaScript that let us navigate to parts of an XHTML document using the DOM and dynamically change their state. We then looked at an important aspect of JavaScript, which is client-side validation. We concluded the chapter by looking at some fundamental aspects of Ajax, which uses JavaScript to communicate with the server and change the content of the current page without needing to reload it.

### References and further reading

- Dutta, S. (2006) *Native XMLHttpRequest object*. http://blogs.msdn.com/ie/archive/2006/01/23/516393.aspx
- Garrett, J.J. (2005) *Ajax: A New Approach to Web Applications*. http://www.adaptivepath.com/publications/essays/archives/000385.php
- Zakas, N., McPeak, J. and Fawcett, J. (2006) *Professional Ajax*. Wrox/Wiley 2006

## Introduction to PHP

### LEARNING OBJECTIVES

- Be aware of the PHP language and understand what it can be used for
- Understand that PHP can be embedded within (X)HTML documents using tags to denote the start and end of PHP code
- Understand how it is possible to jump in and out of PHP within a document and what the PHP parser does when it interprets a document
- Understand and be able to use the echo construct effectively
- Understand how PHP instructions should be separated
- Understand why you should comment your PHP scripts and be able to do so
- Understand the different PHP types that are supported and how to use PHP variables
- Understand what a PHP constant and a predefined variable are and be able to use them
- Understand what an expression is, the role of operators and operands and operator precedence

### INTRODUCTION

Welcome to the PHP scripting language. In this chapter, we begin by introducing you to the PHP language. We explain what PHP is and how it works by introducing you to your first PHP script and show you how you can view the output that it generates within a Web browser.

We shall provide an introduction to script syntax and explain how and why it is important for you to comment your PHP scripts carefully. We shall introduce the concept of variables and describe how you use them. We shall examine the different types of data which a variable can store and the differences between them. We will also examine PHP operands and operators and explain how these go together to form expressions.

In conclusion, we cover all the basic fundamental PHP constructs and syntax you need to know before you can start doing some of the really interesting and powerful things we cover in later chapters. By the end of this chapter, you will be familiar with creating PHP scripts, saving them and viewing their output using a browser of your choice. It is worthwhile pointing out that PHP is widely supported by a large community of developers and you will find a comprehensive annotated manual online at http://www.php.net/manual/en/ if there are some PHP language concepts we introduce that you would like to investigate further. Anyway, we have a lot to get through, so let’s get started.

### 8.1 Welcome to PHP

According to the PHP web site (www.php.net) ‘PHP is a widely-used general-purpose scripting language that is especially suited for Web development and can be embedded into HTML’.

PHP is a scripting language which can be combined within (X)HTML documents to enable the creation of dynamic web systems. By doing this you can overcome one of the more serious limitations of (X)HTML documents – they are static in nature. What we mean by this

FIGURE 8.1 How PHP works

![](img/b2471264f405d17994ef173e4b9cec92_245_0.png)

is that a standard (X)HTML document is stored on a server and, when requested, displayed to a user via a web browser. The document that is displayed does not change. It might have some clever JavaScript or plug-in which provides a degree of user interaction but it cannot change the fundamental content it contains nor interface with a database to reflect new dynamic up-to-date content each time it is loaded. By using PHP, you can accomplish all of these things.

PHP is a hypertext pre-processor (it's where the name PHP comes from) which means that it processes the hypertext document before it is served to the browser. PHP is therefore a server-side scripting language and all the work is done at the server before it is sent to the client (your web browser). Figure 8.1 illustrates how PHP works.

If you look closely at Figure 8.1, you see that a user has requested a PHP document from a web server. If the document had been a simple (X)HTML document, the server would have simply sent it to the client web browser. Because the document is a PHP document, the server passes the document to the PHP interpreter. This parses through the document searching for any PHP commands. When it finds any it removes them and replaces them with any output that the PHP commands generate. When it has finished parsing the document, the resulting document with the PHP removed is sent to the user's browser. It sounds complex but it is easier if you see it working for yourself.

### 8.2 Your first PHP script

Welcome to your first PHP script, which is commonly known as a 'hello world' application, as all it does is display the words 'Hello, World':

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>PHP Script</title>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />
</head>
<body>
<?php
echo "<p>Hello, World</p>";
?>
</body>
</html>
```

Okay, this does look very complicated for an introductory script but that is because we have chosen to embed the PHP script into an (X)HTML document which conforms to the W3C recommendations and standards. This is a very good thing to do as it ensures the quality and consistency of web documents, but it does make things a little complex for the beginner.

Don’t worry about understanding the script at the moment but type the script into your chosen editor and save it as ‘example8-1.php’ in your web server directory. Exactly how you do this depends on the editor you are using, the web server and the PHP environment
