
# Introduction

## p2p.wrox.com

For author and peer discussion, join the P2P forums at p2p.wrox.com. The forums are a Web-based system for you to post messages to Wrox books and related technologies and interact with other readers and technology users. The forums offer a subscription feature to e-mail you topics of interest your choosing when new posts are made to the forums. Wrox authors, editors, other industry experts, and your fellow readers are present on these forums.

At http://p2p.wrox.com you will find a number of different forums that will help you not only as you read this book, but also as you develop your applications. To join the forums, just follow these steps:

- 1. Go to p2p.wrox.com and click the Register link.
- 2. Read the terms of use and click Agree.
- 3. Complete the required information to join as well as any optional information you wish to provide and click Submit.
- 4. You will receive an e-mail with information describing how to verify your account and complete the joining process.

You can read messages in the forums without joining P2P in order to post your own messages, you must join.

Once you join, you can post new messages and respond to messages other users post. You can read messages at any time on the Web. If you would like to have new messages from a particular forum e-mailed to you, click the Subscribe to this forum icon by the Wrox name in the forum listing.

For more information about how to use the Wrox P2P, be sure to read the P2P FAQs for answers to questions about how the Wrox software works as well as many common questions specific to P2P and Wrox books. To read the FAQs, click the FAQ link on any P2P page.

# Beginning
PHP 5.3

## Part I
Getting Up and Running with PHP

Chapter 1: Introducing PHP

Chapter 2: Your First PHP Script

# 1

## Introducing PHP

Welcome to the world of PHP, one of the Web's most popular programming languages. According to Netcraft (www.netcraft.com), PHP was running on more than 20 million Web servers in July 2007 (http://www.php.net/usage.php). At the time of writing, it's the fourth most popular programming language in the world according to TIOBE (http://www.tiobe.com/index.php/content/paperinfo/tpci/), beaten only by Java, and C++. With the introduction of version 5.3, there's never been a better time to learn PHP.

In this chapter:

- Get a gentle introduction to PHP in general, and the new features of PHP 5.3 in particular
- Learn what PHP is, what it can be used for, and how it stacks up against other dynamic Web technologies
- Take a look at the history of PHP, so how it has evolved over the years, from its humble beginnings to the rich Web development framework it is today

### What Is PHP?

PHP is a programming language for building dynamic, interactive Web Sites. As PHP runs on a Web server, and serve Web pages to visitors on request. One of the key features of PHP is that you can embed PHP code within HTML Web pages, making it very easy for you to create dynamic content quickly.

What exactly does the phrase “dynamic, interactive Web sites” mean? A dynamic Web page is a page whose content change automatically each time the page is viewed. Contrast this with a static Web page, such as a simple HTML file, which looks the same each time it's displayed (at least until the page is next edited). Meanwhile, an interactive Web site is a site that responds to input from its visitors. A Web forum is a good example — users can post messages to the forum, which are then displayed on the site for all to see. Another simple example is a “contact us” form,

## Part I: Getting Up and Running with PHP

where visitors interact with the page by filling out and sending a form, which is then emailed to the Webmaster.

PHP stands for PHP: Hypertext Preprocessor, which gives you a good idea of its core purpose: to process information and produce hypertext (HTML) as a result. (Developers love acronyms, and PHP: Hypertext Preprocessor is a good example of.)

PHP is a server-side scripting language, which means that PHP scripts, programs, usually run on a Web browser. (A good example of a client-side scripting language is JavaScript, which commonly runs within a Web browser). Furthermore, PHP is an interpreted language —

### Chapter 1: Introducing PHP

PHP 5.3

### Part I
Getting Up and Running with PHP

Chapter 1: Introducing PHP

Chapter 2: Your First PHP Script

# 1

## Introducing PHP

Welcome to the world of PHP, one of the Web's most popular programming languages. According to Netcraft (www.netcraft.com), PHP was running on more than 20 million Web servers in July 2007 (http://www.php.net/usage.php). At the time of writing, it's the fourth most popular programming language in the world according to TIOBE (http://www.tiobe.com/index.php/content/paperinfo/tpci/), beaten only by Java, and C++. With the introduction of version 5.3, there's never been a better time to learn PHP.

In this chapter:

- Get a gentle introduction to PHP in general, and the new features of PHP 5.3 in particular
- Learn what PHP is, what it can be used for, and how it stacks up against other dynamic Web technologies
- Take a look at the history of PHP, so how it has evolved over the years, from its humble beginnings to the rich Web development framework it is today

### What Is PHP?

PHP is a programming language for building dynamic, interactive Web Sites. As PHP runs on a Web server, and serve Web pages to visitors on request. One of the key features of PHP is that you can embed PHP code within HTML Web pages, making it very easy for you to create dynamic content quickly.

What exactly does the phrase “dynamic, interactive Web sites” mean? A dynamic Web page is a page whose content change automatically each time the page is viewed. Contrast this with a static Web page, such as a simple HTML file, which looks the same each time it's displayed (at least until the page is next edited). Meanwhile, an interactive Web site is a site that responds to input from its visitors. A Web forum is a good example — users can post messages to the forum, which are then displayed on the site for all to see. Another simple example is a “contact us” form,

## Part I: Getting Up and Running with PHP

where visitors interact with the page by filling out and sending a form, which is then emailed to the Webmaster.

PHP stands for PHP: Hypertext Preprocessor, which gives you a good idea of its core purpose: to process information and produce hypertext (HTML) as a result. (Developers love acronyms, and PHP: Hypertext Preprocessor is a good example of.)

PHP is a server-side scripting language, which means that PHP scripts, programs, usually run on a Web browser. (A good example of a client-side scripting language is JavaScript, which commonly runs within a Web browser). Furthermore, PHP is an interpreted language —

### Why Use PHP?

One of the best things about PHP is the large number of service providers (ISPs) that support it. Hundreds of thousands of developers are using PHP, and it's not surprising that several million sites have PHP installed.

Another great feat of PHP is that it's cross-platform — you can run PHP on Windows, Linux, FreeBSD, Mac OS. The PHP engine can integrate with common web servers, including Apache, Internet Information Services (IIS), Zeus. This means you can develop and test your PHP site on one, then deploy on another, if you ever need to.

How does PHP compare with other programming technologies? At the time of writing, the following technologies are presented:

- ASP (Server Pages): This venerable Microsoft technology has around since 1997, and was one of the first Web application technologies to integrate closely with the server. ASP scripts are usually written in VBScript, a language derived from BASIC. This contrasts with PHP's C-like syntax. Both languages have the same fans, I personally find that it's easier to write structured, modular code in PHP than in VBScript.
- ASP.NET: This is the latest iteration of ASP; in fact it has been built from the ground up. Actually it is a framework that can be used to build Web sites, and you have a choice of languages to use, including C#, VB.NET (Visual Basic), and Java. Because ASP.NET gives you a large library of code for things like making HTML forms and searching database tables, you can get a Web application up and running very quickly. PHP although has a rich library of functions, doesn't give you a structured framework to the extent that ASP.NET does. On the other hand, plenty of free framework and libraries are available for PHP, such as PEAR (discussed later in this book) and the Zend Framework. Many argue that C# is a nicer, better-organized language to program in than PHP; although C# is arguably harder to learn. Another advantage of ASP.NET is that C# is a compiled language, which generally means it runs faster than PHP's interpreted scripts (although).

ASP and ASP.NET have a couple of other disadvantages to PHP. First of all, they have a commercial license, which can mean spending additional money on server software, and hosting is more expensive as a result. Secondly, ASP.NET are fairly heavily tied to the Windows platform, whereas the other technologies in this list are more cross-platform.
