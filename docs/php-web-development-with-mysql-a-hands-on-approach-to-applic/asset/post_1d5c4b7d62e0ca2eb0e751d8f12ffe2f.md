
## INTRODUCTION

was released in the middle of 1999. The official release of PHP 4 occurred in May of 2000 and added support for more web servers and session management.

In July of 2004, PHP 5 was released and was powered by the "Zend Engine 2.0." This release included improvements for OOP, PHP Data Objects (PDO - which defines connections and interactions with databases), and other features.

In December of 2015, the PHP development team released version 7.0 of PHP[2]. This release improved the performance of PHP applications up to twice as fast as version 5.6. It also included a number of security enhancements and improved Exception handling.

PHP 8.0[3] was released in November of 2020. It further enhances the language’s type hinting system and adds named arguments while making the language more consistent and performant. Like previous releases, the core contributors have worked to minimize the impact of backward-incompatible changes such that upgrading from PHP 7 is not a monumental undertaking for most code bases.

### An Even Briefer History of PHP

- June 8, 1995 PHP 1.0 is posted to the usenet group comp.infosystems.www.authoring.cgi
- It was created by Rasmus Lerdorf[4] as PHP Tools
- Then Rasmus set to work integrating his tools with the Apache web server, and less than a year later, PHP 2.0 was posted to the same Usenet group
- PHP originally stood for “Personal Home Pages.”
- PHP now stands for “PHP Hypertext Preprocessor” (a recursive acronym)
- It is most likely the fastest and simplest tool available for creating database-enabled websites
- It will work with any UNIX-based web server on every UNIX flavor out there. The package is completely free of charge for all uses, including commercial

Here is how Rasmus described PHP at the time:

> *PHP/FI is a server-side HTML embedded scripting language. It has built-in access logging and access restriction features and also support for embedded SQL queries to mSQL and/or Postgres95 backend databases.*

[2] 7.0 of PHP: http://php.net/releases/7_0_0.php
[3] PHP 8.0: https://www.php.net/releases/8.0/en.php
[4] Rasmus Lerdorf: https://en.wikipedia.org/wiki/Rasmus_Lerdorf

## Chapter 1 The Life and Times of a PHP Script

> Most good programmers do programming not because they expect to get paid or get adulation by the public, but because it is fun to program.
> 
> - Linus Torvalds

## 1. THE LIFE AND TIMES OF A PHP SCRIPT

### Static Vs. Dynamic Websites

HTML alone only allows you to create static web pages. This approach is fine if you just want to display images of your cat. However, if you want a web application with the ability to interact with a database and for your web pages to update based on content that can change, you need a dynamic website. This is where PHP comes in. The PHP interpreter runs in the webserver. PHP will deliver HTML to the webserver, and since PHP is also a programming language, it allows you to build the HTML dynamically.

### The Browser and the Server

HyperText Transfer Protocol (HTTP) is the protocol used to communicate between a web server (which I will call the server) and the web browser (which I will call the client).

### HTTP Requests and Responses

When you open up a web browser on your computer and type in a Uniform Resource Locator (URL) in the address bar (let's say flibbertigiblets.com)...

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_22_0.png)

As soon as you press the Return key on your computer, your browser sends an HTTP Request to the web server at flibbertigiblets.com. That request might look something like Listing 1.1.

Listing 1.1.

```
```
1. GET /phpWebDevMySQL/ HTTP/1.1
2. Host: flibbertigibets.com
3. Connection: keep-alive
4. Cache-Control: max-age=0
5. Authorization: Basic ZmFsbDIwMTdwaHA6dXNlIHRoZSBMb3Jj3jZQ==
6. Upgrade-Insecure-Requests: 1
7. User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_6)
8. AppleWebKit/537.36 (KHTML, like Gecko) Chrome/62.0.3202.94 Safari/537.36
9. Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,
10. image/apng,*/*;q=0.8
11. Accept-Encoding: gzip, deflate
12. Accept-Language: en-US,en;q=0.9
13. If-Modified-Since: Mon, 13 Nov 2017 21:51:51 GMT
```
```

The server can send various responses back to your browser (the client). However, the most common is a 200 OK response that looks like:

```
HTTP/1.1 200 OK
Server: nginx/1.12.2
Date: Fri, 17 Nov 2017 00:31:35 GMT
Content-Type: text/html
Transfer-Encoding: chunked
Connection: keep-alive
Last-Modified: Mon, 13 Nov 2017 21:51:51 GMT
Content-Encoding: gzip
```

Assuming everything is OK with the header, the server sends HTML to the browser, so you should see the web page shown in Figure 1.2.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_23_0.png)

### The Server and PHP

As previously mentioned, PHP runs with the web server and is responsible for interpreting PHP code.

### What the PHP Interpreter Does

When the web server encounters PHP code, it hands the code to the PHP interpreter. The interpreter executes the code according to the rules of the PHP language. Within the code, text will frequently need to be echoed or printed out to the web page. This text will be sent from the PHP interpreter back to the web server to be rendered as HTML back to the browser.

Let’s take a look at a simple web page with HTML and PHP integrated together that outputs today’s date:

```
<html>
  <head>
    <title>My Awesome Page</title>
  </head>
  <body>
    <h1>Today is <?php echo date("m-d-Y"); ?></h1>
  </body>
</html>
```

## 1. THE LIFE AND TIMES OF A PHP SCRIPT

When the web browser encounters the <?php tag, everything from the opening <?php to the closing ?> tag is handed off to the PHP interpreter for processing. When the PHP script is done processing, any resulting HTML is sent back to the web server for output to the client.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_24_0.png)

The output of the above script is shown in Figure 1.3.

### The php.ini File and Important Settings

The php.ini file is where we set and change directives to configure PHP. This file is read every time the web server is started or restarted, and it is how PHP is initialized. This file is well documented with comments regarding the various directives. Visit the PHP manual[1] for a detailed explanation of the php.ini directives. Many directives can affect the security and behavior of your application, so change them with care.

To find the php.ini file used by the PHP interpreter, you can inspect the output of phpinfo() in a browser or look at the output of php -i at the command line.

### Error Reporting Settings

When working through this book, you should tell PHP to show any errors it encounters in your browser. You'll get feedback about parse errors, uninitialized variables, and more. Otherwise, when you run your code, you may get the dreaded White Screen of Death (WSOD) when PHP encounters a syntax error like a missing semi-colon. In your php.ini file, check to verify that display_errors is enabled:

```
display_errors = On;
```

In a production environment, this setting should be off to prevent disclosing sensitive information.

[1] PHP manual: http://php.net/ini

## Chapter 2 Writing Your First PHP Script

> I have always wished for my computer to be as easy to use as my telephone; my wish has come true because I can no longer figure out how to use my telephone.
> 
> - Bjarne Stroustrup

## 2. WRITING YOUR FIRST PHP SCRIPT

### Setting Up a Development Environment

To write PHP, all you need is a text editor. However, since PHP runs with a web server, you need access to a PHP development environment. I will show you how to install and configure a Unix-based development environment for writing and debugging your PHP web applications.

### Downloading a Unix Operating System (OS)

Since most PHP web applications run on a Linux distribution of the Unix OS, it makes sense to develop on one. I find Ubuntu Desktop one of the easiest operating systems to develop in. As of this writing, the current version is Ubuntu 20.04.1 LTS.

> LTS stands for long-term support. Canonical, the organization that maintains Ubuntu, guarantees free security and maintenance updates for five years on LTS releases.

The first thing we need to do is head over to https://www.ubuntu.com/download/desktop and download the latest 64-bit version of Ubuntu Desktop and press the Download button as in Figure 2.1.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_26_0.png)

Figure 2.1.
