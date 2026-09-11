   

## PHP CLI

### Create effective CLI scripts using PHP

 

#### Rob Aley

 

This book is for sale at [http://leanpub.com/phpcli](http://leanpub.com/phpcli)

This version was published on 2016-01-27

![publisher's logo](images/00001.jpeg)

\*   \*   \*   \*   \*

This is a [Leanpub](http://leanpub.com) book. Leanpub empowers authors and publishers with the Lean Publishing process. [Lean Publishing](http://leanpub.com/manifesto) is the act of publishing an in-progress ebook using lightweight tools and many iterations to get reader feedback, pivot until you have the right book and build traction once you do.

\*   \*   \*   \*   \*

© 2016 Rob Aley 

## Table of Contents

1.  [Welcome](#part0002.html#leanpub-auto-welcome) 
    1.  [About the author](#part0002.html#leanpub-auto-about-the-author)
    2.  [Acknowledgements](#part0002.html#leanpub-auto-acknowledgements)
2.  [1\. Introduction](#part0003.html#leanpub-auto-introduction) 
    1.  [1.1 “Use PHP? We’re not building a website, you know!”.](#part0003.html#leanpub-auto-use-php-were-not-building-a-website-you-know)
    2.  [1.2 Are you new to PHP?](#part0003.html#leanpub-auto-are-you-new-to-php)
    3.  [1.3 Reader prerequisites. Or, what this book isn’t](#part0003.html#leanpub-auto-reader-prerequisites-or-what-this-book-isnt)
    4.  [1.4 An important note for Windows and Mac users](#part0003.html#leanpub-auto-an-important-note-for-windows-and-mac-users)
    5.  [1.5 About the sample code](#part0003.html#leanpub-auto-about-the-sample-code)
    6.  [1.6 External resources](#part0003.html#leanpub-auto-external-resources)
    7.  [1.7 English. The Real English.](#part0003.html#leanpub-auto-english-the-real-english)
3.  [2\. Getting away from the Web - an overview of CLI programming in PHP](#part0004.html#leanpub-auto-getting-away-from-the-web---an-overview-of-cli-programming-in-php) 
    1.  [2.1 PHP without a web server](#part0004.html#leanpub-auto-php-without-a-web-server)
    2.  [2.2 PHP versions - what’s yours?](#part0004.html#leanpub-auto-php-versions---whats-yours)
    3.  [2.3 A few good reasons NOT to do it in PHP](#part0004.html#leanpub-auto-a-few-good-reasons-not-to-do-it-in-php)
    4.  [2.4 Thinking about security](#part0004.html#leanpub-auto-thinking-about-security)
    5.  [2.5 CLI specific Code Frameworks](#part0004.html#leanpub-auto-cli-specific-code-frameworks)
4.  [3\. Understanding and using the CLI SAPI](#part0005.html#leanpub-auto-understanding-and-using-the-cli-sapi) 
    1.  [3.1 What’s different about the CLI SAPI?](#part0005.html#leanpub-auto-whats-different-about-the-cli-sapi)
    2.  [3.2 CLI SAPI installation](#part0005.html#leanpub-auto-cli-sapi-installation)
    3.  [3.3 PHP command line options](#part0005.html#leanpub-auto-php-command-line-options)
    4.  [3.4 Command line arguments for your script](#part0005.html#leanpub-auto-command-line-arguments-for-your-script)
    5.  [3.5 The many ways to call PHP scripts](#part0005.html#leanpub-auto-the-many-ways-to-call-php-scripts) 
        1.  [3.5.1 From a file](#part0005.html#leanpub-auto-from-a-file)
        2.  [3.5.2 From a string](#part0005.html#leanpub-auto-from-a-string)
        3.  [3.5.3 From STDIN :](#part0005.html#leanpub-auto-from-stdin-)
        4.  [3.5.4 As a self executing script : Unix/Linux](#part0005.html#leanpub-auto-as-a-self-executing-script--unixlinux)
        5.  [3.5.5 As a self executing script : Windows](#part0005.html#leanpub-auto-as-a-self-executing-script--windows)
        6.  [3.5.6 Windows php-win.exe](#part0005.html#leanpub-auto-windows-php-winexe)
    6.  [3.6 Quitting your script](#part0005.html#leanpub-auto-quitting-your-script)
    7.  [3.7 PHP REPLs](#part0005.html#leanpub-auto-php-repls)
5.  [4\. User facing software](#part0006.html#leanpub-auto-user-facing-software) 
    1.  [4.1 Command line interface basics](#part0006.html#leanpub-auto-command-line-interface-basics)
    2.  [4.2 Advanced command line input](#part0006.html#leanpub-auto-advanced-command-line-input)
    3.  [4.3 Using STDIN, STOUT & STDERR](#part0006.html#leanpub-auto-using-stdin-stout--stderr)
    4.  [4.4 CLI helper libraries](#part0006.html#leanpub-auto-cli-helper-libraries)
6.  [5\. PHP CLI scripts and your system](#part0007.html#leanpub-auto-php-cli-scripts-and-your-system) 
    1.  [5.1 Starting external processes from PHP, or “shelling out”](#part0007.html#leanpub-auto-starting-external-processes-from-php-or-shelling-out)
    2.  [5.2 File Status and Realpath caches](#part0007.html#leanpub-auto-file-status-and-realpath-caches)
    3.  [5.3 APC and other code caches](#part0007.html#leanpub-auto-apc-and-other-code-caches)
7.  [6\. Where now? or, Thanks & feedback](#part0008.html#leanpub-auto-where-now-or-thanks--feedback) 
    1.  [6.1 Upgrade to “PHP Beyond The Web” for only $5!](#part0008.html#leanpub-auto-upgrade-to-php-beyond-the-web-for-only-5)
    2.  [6.2 Giving feedback, and getting help and support](#part0008.html#leanpub-auto-giving-feedback-and-getting-help-and-support)
    3.  [6.3 Are you reading a “pirated” copy?](#part0008.html#leanpub-auto-are-you-reading-a-pirated-copy)
8.  [Appendix A : Compiling and installing PHP, extensions and libraries](#part0009.html#leanpub-auto-appendix-a--compiling-and-installing-php-extensions-and-libraries) 
    1.  [Compiling and installing PHP itself](#part0009.html#leanpub-auto-compiling-and-installing-php-itself)
    2.  [Compiling and installing (extra) core extensions](#part0009.html#leanpub-auto-compiling-and-installing-extra-core-extensions)
    3.  [Installing multiple versions of PHP](#part0009.html#leanpub-auto-installing-multiple-versions-of-php)
    4.  [PEAR and PECL](#part0009.html#leanpub-auto-pear-and-pecl)
    5.  [Composer](#part0009.html#leanpub-auto-composer)
    6.  [Symfony2 bundles](#part0009.html#leanpub-auto-symfony2-bundles)
9.  [Appendix B : Sources of help](#part0010.html#leanpub-auto-appendix-b--sources-of-help) 
    1.  [The PHP manual](#part0010.html#leanpub-auto-the-php-manual)
    2.  [Official mailing lists](#part0010.html#leanpub-auto-official-mailing-lists)
    3.  [Stack Overflow](#part0010.html#leanpub-auto-stack-overflow)
    4.  [Other books](#part0010.html#leanpub-auto-other-books)
    5.  [Newsgroups](#part0010.html#leanpub-auto-newsgroups)
    6.  [PHP Subredit](#part0010.html#leanpub-auto-php-subredit)
    7.  [PHP on Github](#part0010.html#leanpub-auto-php-on-github)
    8.  [PHP news sites](#part0010.html#leanpub-auto-php-news-sites)

## Guide

1.  [Begin Reading](#part0002.html#1T140-89b0fa556d1946adbe34489539d937fa)

## Welcome

### About the author

I’ve been programming in PHP since late 2000. Initially it wasn’t by choice as my preferred languages at the time were Perl and Delphi (also known as Object Pascal). Things began to change after I graduated from the University of Leeds with a degree in Computer Science in 1999 and started out in a career as a freelance web developer. After only a couple of months I was offered the opportunity to take over a (relatively speaking) substantial government website contract from a friend who was exiting the freelance world for the safer and saner world of full-time employment. The only catch was that several thousand lines of code had already been written, and they were written in a relatively new language called “PHP”. Oh, and the only other catch was that I had about a week to learn it before taking over the site. So, as was the way at the time, I popped down to the local Waterstones bookshop (for the younger among you that’s where we used to get books. Books made of paper. And we had to go out and get them. Or order online and wait days for them to be delivered. Did I mention they were made of paper?). With my paper copy of “The Generic Beginners Complete Guide to PHP and MySQL for Dummies Compendium” book in hand (I may not have recalled the title completely correctly) I settled down with a pint of ale (I’m in Yorkshire at this point, remember) and set about reading it. A few days later I was coding like a pro (well, stuff was working) and 12 years later I haven’t looked back. After a varied career as a freelancer and starting up a couple of, er, start-ups (IT related and not) with varying (usually dismal) success, I’m now a full-time programmer at The University of Oxford. My day job involves medium-scale data acquisition and management, statistical analysis and providing user interfaces for researchers and the public. The majority of my development work is done in PHP, either developing new projects or gluing together other peoples software, systems and databases.

Through-out my career I’ve always used PHP for web development, but for Desktop GUI work I initially used Delphi (and then Free-Pascal/Lazarus), complimented with bash shell scripting for other tasks. This was mainly due to learning them while at University. However, as PHP has matured I’ve increasingly used it beyond the web, and now I rarely use anything else for any programming or scripting task I encounter. Having been immersed in other languages like C++, Javascript, Fortran, Lisp (and probably others that my brain has chosen deliberately not to remember) by necessity during University and in some of my freelance jobs, I can honestly say that PHP is now my language of choice, rather than of necessity.

When I’m not tied to a computer, I would like to say I have lots of varied and interesting hobbies. I used to have. I could write a whole book (which wouldn’t sell well) about where I’ve been and what I’ve done and I’d like to think it’s made me a well rounded person. But these days I don’t. In large part this is due to the demands of my three gorgeous young daughters Ellie, Izzy and Indy, my gorgeous wife Parv and my even more gorgeous cat Mia. And I wouldn’t have it any other way. That’s what I tell myself, anyway…

### Acknowledgements

Isaac Newton said “If I have seen further, it is by standing on the shoulders of giants”. This book builds on, and hopefully adds to, the work of many others. The most notable of whom I would like to acknowledge below.

**The authors of, and contributors to, the official PHP manual**  
An invaluable reference for PHP functions and syntax, to which I referred frequently during writing this book, both for fact checking and as an aide-memoir. Thanks!

**The collective PHP wisdom of the Internet**  
For over 12 years I’ve used you for learning, research, play and profit. Too many sites & too many people to list here, if you’ve written about PHP on web then you may well be one of them. Thanks!

**My Family**  
For allowing me a modicum of time to write this book, and supporting me unconditionally in everything I do. Usually. If I ask first. And there’s not something more important going on. And usually with conditions. Thanks!

## 1\. Introduction

If your e-reader has bought you directly to this page, or your fingers have flipped straight through the pages of the paper copy to here, then you have (perhaps wisely) skipped the books “front matter”, containing the front cover, table of contents, about-the-author section, acknowledgements and a few more bits and bobs. If that interests you, then scroll or flip backwards. Otherwise, read on to start your journey through the wider world of PHP software.

### 1.1 “Use PHP? We’re not building a website, you know!”.

Both it’s current recursive moniker (“PHP : PHP HyperText Preprocessor”), as well as the name originally bestowed upon it by it’s creator Rasmus Lerdorf (“PHP : Personal Home Page”) reinforce the widely held view that PHP is a scripting language for the web. And that was true, back in 1995 when PHP was first created, and for a number of years afterwards. In the web arena PHP excels : it’s easy to use, quick to develop in, widely deployed, tightly integrated into web stacks (it’s usually the P in LAMP,WAMP,MAMP etc.), and of course because it is free and open source.

But many people don’t realise (or haven’t noticed, or choose not to notice) that PHP has evolved and grown up. It now closely resembles a modern, general purpose programming language. This lack of recognition is partly PHP’s own fault as it took a long time to get some of the fundamentals in place, such as OOP language constructs and even the ability to run at all without a web server being involved. However the programming community hasn’t helped; many programmers had a hard time seeing the potential for PHP to bring its rapid dynamic development model out of the web and into the wider computing environment, and many simply stuck with the “web scripting for beginners” dogma that was only really true of its early years.

Recent releases in particular have brought mainstream language features (e.g. closures, traits, better language support, namespaces & late static binding among many others) to the table. Performance has jumped up and up and up, memory usage (a bugbear of older versions) has dropped considerably, and PHP is now one of the more lean popular scripting languages. For even higher performance needs PHP 7 has dramatically rewritten Zend Engine (giving up to twice the performance of 5.6), and Facebook (the biggest user of PHP around) are one of several groups who are releasing alternative interpreters/VM’s, leading to performance increases of up to 6 times that achievable with the old Zend Engine. The recent release of PHP 7, and the upswing in community involvement, are indicative that reports of PHP’s demise are quite premature!

But why, why, oh why create Command Line Scripts in PHP? Why not whip up a bash shell script? Why not learn C++ or another language typically used for software projects? The truth is these are valid options, and life may well work out just fine for you. But why turn down the opportunity to use your existing skills? Why not use PHP’s integrated database access, reuse existing code and data from your web projects, take advantage of PHP’s easy to use network libraries and functions, wallow in flexible text and data handling, and mix shell commands and other languages into PHP as needed to get best of both worlds? In short, why the heck not?

Hopefully I’ve sold you on the story that PHP is a cross-platform, rapid-development focused, versatile language and is ideal for many different types of software. The aim of this book is to give you, the PHP coder, an insight into one specific type of software : using PHP to build command line tools that live beyond the web. I’ll show you the essential ingredients needed to transform your existing web based PHP skills to the command line, to allow you to get up and running as quickly as possible with the tools you already know.

And if this book whets your appetite for web-less PHP programming, you can get a large discount on “PHP Beyond The Web”, my other book that covers many more types of PHP software and off-line programming topics. See the last Chapter for details.

### 1.2 Are you new to PHP?

This book is aimed at showing PHP developers how they can use their existing skills to write CLI software instead of web pages. However I appreciate that some readers may be new to PHP and are reading this book to get a feel for what PHP is capable of. If you’re already a programmer, albeit not well versed in PHP, the comprehensive official PHP manual may be the best place to begin to get a feel for the differences between PHP and the languages you are used to.

If you’re not already a programmer, there are numerous “beginning PHP” books available from your favourite e-book retailer. In either case, the wider web also provides its usual breadth of in-depth knowledge and tutorials, just a judicious google away.

And finally, newcomer or experienced programmer, if you’re thinking of getting serious about PHP, it may be worth having a look at some PHP “best practice” websites before diving headlong into coding. It may save you a lot of trouble in the long run.

### 1.3 Reader prerequisites. Or, what this book isn’t

To make the most of this book, you should have basic experience of programming in PHP (most likely for the web), a general programming or IT background, and a willingness to learn and be taken outside of your comfort zone.

This book isn’t an introduction to PHP or programming in general. Although you don’t need a computing degree or knowledge of advanced programming concepts, the book is hopefully pitched to the level of an average PHP programmer (one who has explored more than the very basics of PHP) and tries to explain any necessary concepts as we go along. It is also useful for advanced programmers who may choose to use it as a quick reference for exploring the PHP CLI features.

### 1.4 An important note for Windows and Mac users

Most of the examples given in the book are run and tested under Linux (the latest Ubuntu Desktop/Server flavour in most cases). PHP runs on many operating systems, including MS Windows and Apple OS X, and code often runs in an identical manner. However there are, of course, differences due to the file system, OS, available libraries etc., but to cover these all in this book would not be practical. In addition, some features such as those reliant on POSIX standards aren’t (easily) available on some systems like Windows. As OS X was derived from a POSIX compliant operating system, you will likely find more of the code compatible than with Windows, but your experience may still vary. A good source of information for OS specific issues is the official PHP online manual, and in particular the user comments at the bottom of each page. Where possible areas specific to these other OSes have also been covered, for instance we will look at how to access the Windows Registry.

### 1.5 About the sample code

As you’ll see throughout the book I mainly use “traditional” imperative/procedural PHP in my coding examples to keep things as simple as possible for coders of all abilities. This book isn’t designed to be a lesson in coding best practices or style, a guide to OOP programming or to push any kind of programming model or dogma. I also avoid the use of any code frameworks. Many frameworks are based around the web model and don’t always perform as intended in the kind of applications we’ll be looking at, although some do now have “console” or “cli” modules. MVC style frameworks can be useful when building GUI applications (indeed the MVC paradigm pre-dates the web considerably!), but because of the many different implementation details and styles we’ll stick to framework-less code here.

It should be clear from the plain, straight forward PHP code presented how it can be used or adapted to suit your own programming style, framework or model. We will be mainly looking at task specific implementation details, leaving the hot topic of programming itself to the many other books available.

All of the sample PHP source code in this book is available for you to use and do with as you please without limit or license. Use or abuse it as you see fit!

If you have trouble running or understanding the sample code, see the feedback section in the last chapter of this book for details on how to contact the author for help.

### 1.6 External resources

Through out the book we will point you in the direction of external tools, resources and information, in one of two ways :

### 1.7 English. The Real English.

Just a quick note to say that, no, those aren’t spelling mistakes, it’s British English (you know, the one that kicked it all off) as your humble author hails from the other side of the pond. Deal with it, we spell things differently. Any genuine spelling mistakes you spot will be dismissed as part of an evolving language, and then quietly fixed while you’re not looking.

## 2\. Getting away from the Web - an overview of CLI programming in PHP

This chapter takes a look at the basic steps involved in breaking free from the web with PHP. We’ll cover the technical steps involved, and also at the differences in programming practises and focus.

### 2.1 PHP without a web server

Most PHP programmers have used PHP strictly in a web-server environment. In such an environment PHP is a CGI/Fast GGI or server module, called and controlled by the HTTP server (usually Apache, IIS, Nginx or similar). The HTTP server receives a request for a PHP based web page and calls the PHP process to execute it, which usually returns output back to the HTTP server to be sent on to the end user.

There have been a number of attempts to create local applications (scripting systems, desktop apps and so forth) with PHP using a locally installed web server, with some success. However the downsides of using this web-type model for local apps are numerous:

*   For the value they provide in these scenarios, web servers such as Apache are often very over specified and resource hungry
*   Unless properly locked down, a web server running locally introduces a point of access to your machine for malicious visitors from the outside world
*   HTTP is a verbose protocol and (arguably) ideally suited for the web, however it’s often overkill for local inter-process communication and adds another resource and complexity overhead to your application
*   Your application interface typically runs in a web browser, and therefore looks anything but local (and comes with additional support/upgrade headaches unless you install a browser specifically for your app)

PHP, as of version 5.4, includes a built-in web-server which removes some of the problems described above. However it was designed for local testing of PHP scripts designed to be deployed on a fully-fledged HTTP server such as Apache in a live environment. It is a route that can be explored for some local apps, particularly where you want to run a private instance of a PHP web app that already exists. However its stability, reliability and suitability for production-ready local apps is yet to be proven, and it still comes with the baggage of HTTP and web browsers.

Since version 4.3, PHP has had an ace hidden up its sleeve which solves all of these problems. The PHP CLI SAPI (“Command Line Interface” “Server Application Programming Interface”), to give it its formal name, is essential a long way of saying “stand-alone PHP”. It cuts out the need for a web server and provides a stand alone PHP binary for you to interact with. For instance, typing the following at a shell prompt

```
1 ~$ php /home/myfiles/myprogram.php
```

will simply execute your `myprogram.php` file (which you write mostly like any other PHP script) and return any output back to the terminal (unless you tell it otherwise) instead of being sent to the web server (which doesn’t exist!).

In general, PHP scripts called directly using the PHP CLI SAPI will behave in the same way as when called through a web server, although there are some differences. For instance, you won’t find any `$_GET` or `$_POST` arrays, and PHP won’t send any HTTP headers by default, as these concepts don’t mean much beyond the web. Default settings like `max_execution_time` are set to sensible values for local use (in this case to 0 so your scripts won’t time out), output buffering is turned off, and error messages are displayed in plain text rather than HTML.

Full details of how to install (if necessary) and use the CLI SAPI are given in the next chapter.

### 2.2 PHP versions - what’s yours?

PHP has supported the CLI SAPI since version 4.3.0, so many of the examples in this book will run on any PHP version since then. At the time of writing, the current version of PHP is 7.02 and the code in this book has been tested against this version. If you find that a particular function doesn’t appear to exist or work as expected, check the online PHP manual for that function. This shows which versions support which functions, and describe any breaking changes created by newer versions.

If you are using an older version, there are some very good reasons to upgrade.

*   Performance has increased markedly (and, correspondingly, resources used have decreased) in recent versions
*   Although security is not always as critical with non-web applications (see the discussion on security later in this chapter for caveats), the security enhancements and security related bug fixes in recent versions are essential if you’re handling data from external sources, and if you’re using the same version for web work as well
*   Modern language features are available, which can help your coding productivity, as well as helping others take your code more seriously

As with the web versions of PHP, you can compile your own version of the CLI SAPI if you find the need. If you want to include extensions not pre-packaged by your OS software repositories, remove non essential code for performance reasons, or use any of the other compile-time options that PHP supports then learning to “roll your own” version may be worthwhile. A starter guide to compiling and installing PHP and related extensions can be found in Appendix A.

### 2.3 A few good reasons NOT to do it in PHP

Tell someone you’re going to be writing CLI scripts in PHP, and often they’ll rail about how PHP is a web language, that you should choose a language “more suitable” to the task. This book is focused on doing everything in PHP, and for 90% of tasks PHP will do all that is asked of it. PHP is now a general purpose language, it’s Turing complete, and while it’s still used in the main to run “websites”, more and more that means backend services as well. But before you commit to rewrite your world in PHP, there are a few pertinent issues that you may want to consider carefully before jumping in.

*   **High performance requirements**

If you need very high performance, particularly on limited hardware, PHP may not be for you. Performance has come on leaps and bounds in recent versions of PHP and regularly trounces languages like Python and frameworks like Ruby-on-Rails in benchmarks. However at its heart PHP is an abstracted scripting language which is never going to get the same performance for some tasks as lower level languages like C, which are closer to the bare metal. Don’t write it off for all high-performance tasks though, if you’re looking at performance with an eye to costs, you may find that the cost savings on developer time through speed of development in PHP outweighs the cost of the extra hardware you throw at it to get the performance.

*   **Don’t (necessarily) re-invent the wheel**

You *can* write a web server in PHP (see Appendix D for examples), but won’t *existing* servers like Apache do what you need? For many or most infrastructure “itches”, software exists (written in many different languages) that will give you the “scratch” you need. Unless you really need other features, the time spent writing your own is usually going to be greater than the time learning and implementing an existing piece of software. Of course, for some people the converse is true. “Because I can” can be a valid reason, and writing software is always a valuable learning experience.

*   **Keeping the source closed**

PHP is a scripting language, and this means that if you are writing software to sell or deploy elsewhere, you will be revealing your source code to the recipients. Many (including your author) will argue that being “open-source”, even commercially, is a good thing. But if that’s not your bag then you will need to go to greater lengths to protect your code. Source code obfuscaters are available online which use various tricks to make your code hard (but not impossible) to read, and a number of PHP compilers are available to produce binary programs (albeit with limitations in terms of syntax and extension coverage). But the main PHP project hasn’t expressed any intention to support code hiding or compiling, and so the viability of such methods long term is not certain. The business case for closed-source software is also not a done-deal in the medium to long term.

### 2.4 Thinking about security

Every programmer worth their salt is at least aware of the security implications of building web sites and online apps. You deliberately expose your code to the public, to the world, to anyone and everyone who will come (good people and bad). One of the early failings of PHP was to prioritise ease of use over security of code (the horror stories from relics like `register_globals` are only a quick google away). With newer, more secure defaults and functions like `register_globals` being depreciated PHP is safer than ever online. And although most security problems are caused by the programmer rather than the language, even the newest web coders seem to have an appreciation of security issues right off the bat these days.

Step into the world of off-line software, however, and things are markedly different. Typically we see software for trusted users only, deployed locally on trusted machines and under the full control of the benevolent user. The user isn’t going to deliberately attack the software or machine, they’re working with their own data. Functionality absolutely can’t be compromised. Security is rarely considered at all when developing command line programs and desktop apps, let alone being features specified at design time, because it’s not “necessary”.

Except the world doesn’t work like that. Take a look at any software vulnerability mailing list like BugTraq and you’ll find an abundance of vulnerabilities in “offline” apps like Adobe Reader, Microsoft Word and even open-source stalwarts like GIMP. The fact is, security is important even in local apps, for two main reasons. The first is the perennial problem of “typical user” behaviour. This is not a problem for an intelligent tech-literate user who never makes mistakes (like you dear reader), but for any software used by the rest of us disaster is only an accidental-click-on-a-dodgy-email away. The second reason security is important is that for most machines, many non-web applications aren’t really “off-line”. Even when a desktop app or a system daemon doesn’t interact with the web, local network or other external services itself, the machine it is connected to will invariably have an Ethernet cable plugged into it or a WiFi/3G/4G connection active. Your software will not run in its own cosy little realm, insulated from the world outside. Perfectly sand-boxed virtual machines not withstanding, of course.

Software security is the topic of a whole other book (of which others have written plenty, see the further reading section below), and many of the same principles apply to systems software as to web software so you will be able to use your existing knowledge of web based PHP security practices to guide you. The following list of typical vulnerability types and attack vectors in both user-facing and systems software should be considered when planning your script security measures and monitoring.

*   **Compromised data files**

Compromised files from external sources (loaded deliberately or accidentally by users). These are usually data files, and particularly at risk is software registered as a default viewer for a particular file type, as accidental and malicious file activation is much easier.

*   **Exploitation by malware**

Malware looking for innocent software to exploit to gain privilege escalation. Scripted software like PHP code can be easier for malware to re-write or alter, and the availability of the source code in an un-compiled form can be of help to the malware authors.

*   **User misbehaviour**

Legitimate users misbehaving. John Smith looking for a way to view the files or surfing history of his boss Jane Doe on their shared business system, for instance.

*   **Privilege escalation**

Similar to legitimate users misbehaving, this is legitimate software misbehaving, either accidentally or deliberately trying to gain & use access permissions it does not have.

*   **Dependency vulnerability**

PHP vulnerabilities, and vulnerabilities in other dependencies and related software. Your software will be completely free of security issues, of course, but it invariably depends on other libraries, software and PHP extensions, and of course lets not forget the PHP interpreter itself. Any of these can contain security bugs and attack vectors.

The above section lists common sources of security issues in all types of software, not just in PHP. Minimise your risks by planning for these in the design stage, and testing for them before deployment. Then cross your fingers…

### 2.5 CLI specific Code Frameworks

There are many coding frameworks for PHP, and many of them can be used with CLI applications, although there is only one that is specifically created for non-web programming. Code in various frameworks may assume that it will be called in an http related context, so you may need to do extra work to code around this. When deciding whether to use a Framework, or which one to use, you should bear in mind their applicability (in terms of their focus on the web) and whether your application’s performance will suffer from the overhead they may bring. You will usually also need to look at their license, as they will usually have components that need to be distributed with your scripts. That’s not to say that they can’t be useful in general purpose programming, however there are none that your author can currently recommend specifically for non-web projects. If you’re currently comfortable using a particular framework on your web projects, it may be worth seeing if there is a CLI/Console module or recommended code path for that particular framework.

## 3\. Understanding and using the CLI SAPI

As we mentioned in the previous chapter, PHP CLI scripting involves using the PHP CLI SAPI. It’s therefore important to have a good grasp of how to use it, the options for configuring and running it, and how it differs from the web based SAPIs you are used to. Luckily the differences are minimal, and many are intuitive.

### 3.1 What’s different about the CLI SAPI?

The following are the main differences between the CLI SAPI and the standard web implementation :

*   No HTTP headers are written to the output by default. This makes sense as they hold no meaning in the command line and so would be just extraneous text printed above your genuine output. If your output will later be funnelled out to a web browser, you will need to manually add any necessary headers (for instance by using the `header()` PHP function).
*   PHP does not change the working directory to that of the PHP script being executed. To do this manually, use `getcwd()` and `chdir()` to get and set the current directory. Otherwise, the current working directory will be that from which you invoked the script. For instance, if you are currently in `/home/rob` and you type `php /home/peter/some_script.php`, the working directory used in PHP will be `/home/rob`, not `/home/peter`.
*   Any error or warning messages are output in plain text, rather than HTML formatted text. If you want HTMLified errors, for instance if you are producing static HTML files, you can override this by setting the `html_errors` runtime configuration directive to true in your script using `ini_set('html_errors', 1);`
*   PHP implicitly ‘flushes’ all output immediately and doesn’t buffer by default. Online performance can often be harmed by sending output straight to a browser, so instead output is buffered and sent in optimal sized chunks when the chunk is full. Off-line this is not likely to be an issue, and so HTML blocks and output from constructs like print and echo are sent to the shell straight away. There is no need to use `flush()` to clear a buffer when you are waiting for further output. You can still use PHP’s output buffering functions to capture and control output if you wish, see the “Output Control Functions” section in the PHP manual for more information.
*   There is no execution time limit set. Your script will run continuously until it exits of its own volition, PHP will not terminate it even if it hangs. If you want to set a time limit to reign in misbehaving scripts you can do so from within the script using the `set_time_limit()` function.
*   The variables `$argc` and `$argv` which describe any command line arguments passed to your script are automatically set. These are discussed fully later in this chapter.
*   PHP defines the constants `STDIN`, `STDOUT` and `STDERR` relating to the standard streams of the same name, and automatically opens I/O streams for them. These give your application instant access to “standard input” (STDIN), “standard output” (STDOUT) and “standard error” (STDERR) streams.

### 3.2 CLI SAPI installation

To use the PHP CLI SAPI, you may need to install it first. Appendix A gives details on installing (and compiling, where necessary) PHP. However you may find that it is already installed if you have PHP installed (often in a folder called sapi/cli in the PHP program folders), and if not it is usually available in modern OS software repositories (e.g. in Ubuntu a package called `php5-cli` exists and can be installed from any package manager or via the command line with `sudo apt-get install php5-cli`). If it is installed in the command line search path, typing `php -v` on the command line will print the version details, confirming it is indeed installed.

### 3.3 PHP command line options

The PHP binary will accept a number of command line options/switches/arguments which affect its operation. A full list can be seen by typing `php -h`. Although some apply only to the CGI SAPI (used when there is not a “module” such as the PHP Apache module), the following are some of the more interesting and common ones used when interacting with the CLI SAPI:

*   `-f` *or* `--file`

This allows you to specify the filename of the script to be run, and is optional. The `-f` option exists to allow compatibility with software and scripts such as automation software which can programmatically call command line programs but require filename arguments to be formed in this way. It also allows default filetype handlers to be easily set on Windows for PHP scripts. The only real difference in usage between the two versions of the command above come when interpreting command line arguments passed to the script, which we look at in the “Command line arguments for your script” section below. In most cases, the two following lines are mostly equivalent :

```
1 ~$ php -f myscript.php
2 ~$ php myscript.php
```

*   `-a` *or* `--interactive`

Runs PHP interactively. This allows you to type in PHP code, line by line, rather than executing a saved PHP script. This mode of operation is often called a “REPL” (Read-Eval-Print-Loop). As well as providing an interactive interface for testing and developing code, it can also act as an enhanced PHP enabled shell or command-line, and we’ll look at this more closely later in this chapter.

*   `-c` *or* `--php-ini`

Specifies the PHP ini file that PHP will use for this application. This is particularly useful if you are also running web services using PHP on the same machine, as if it is not specified PHP will look in various default locations for `php.ini` and may end up using the same one as your web service. By providing one specifically for your CLI applications you can “open up” various restrictions that make more sense for offline applications. Note that by using the CLI SAPI, PHP will automatically override several `php.ini` settings regardless of whether you specify a custom ini file using this option. These overridden settings are those that affect the behaviour outlined in the “Whats different about the CLI SAPI?” above, and while the `php.ini` file is ignored in these cases you can revert or change these settings directly in your code using `ini_set()` function or similar. You can also use the -d or `--define` option to set options (e.g. `php -d max_execution_time=2000 myscript.php`). If you are deploying software onto machines that you do not control (e.g. if you are selling software for users to install on their own machines), it makes sense to use one of these mechanisms to ensure that PHP will be running with the settings you expect, not the settings the user may happen to have. See `-n` below as well.

*   `-n` *or* `--no-php-ini`

This tells PHP not to load a `php.ini` file at all. This can be useful if you do not wish to ship one with your application and instead set all of the settings directly within your code using `ini_set()` or similar. PHP will use its default settings if no ini file is provided, and it is worth remembering that these default settings may change from version to version of PHP (and indeed have done so in the past). You shouldn’t rely on the current defaults being suitable for your application. You can use `php --ini` to show the default path that PHP will look for ini files when the `-n` option isn’t used and `-c` isn’t used to specify a file.

*   `-e` *or* `--profile-info`

This puts PHP into “Extended Information Mode”. EIM generates extra information for use by profilers and debuggers. If you’re not using a profiler or debugger that requires this mode, you should not enable it as it can degrade performance. More information on profilers and debuggers can be found in the next chapter.

*   `-i` *or* `--info`

Calls the `phpinfo()` function and prints the output. This outputs a *large* range of information about the PHP installation, in plain text format rather than the usual HTML (it detects we are calling it from the CLI SAPI). This can be useful in tracking down issues with the installation itself, as well as giving you version information, lists of extensions installed, relevant file paths etc. As with any other shell command, the output can be piped to other commands, e.g. grep. So if you wanted to check if IPv6 was enabled in your PHP binary for instance, you could try :

```
1 ~$ php -i | grep -i "ipv6"
```

*   `-l` *or* `--syntax-check`

Parses the file, checking for syntax errors. This is a basic “lint” type checker, more advanced static code analysis tools are discussed in the next chapter. Be aware that this option only checks for basic syntax errors, the sort that cause the PHP engine to fail. More subtle bugs, problems in your program logic, and errors that are created at run time will not be detected. Your code is not executed, so it can help pick up basic errors before running code that may alter data and cause problems if it fails. Even when you run such code in a testing environment, resetting data and setting up for another test can take time, so a quick check for basic syntax errors first can be a time saver. Some IDE’s and text editors run `php -l` in the background to highlight syntax errors as you type. For instance the linter-php1 package in Github’s Atom editor uses this method for live linting of PHP code.

*   `-m` *or* `--modules`

Lists all of the loaded PHP & Zend modules/extensions. These are modules that PHP has been compiled with, and may include things like “core”, “mysql”, “PDO”, “json” and more. This is useful for checking the PHP installation has the functionality that your application requires. You can also check from within your scripts using the `extension_loaded()` function or by calling the `phpinfo()` function. `-m` provides a subset of the information given with the `-i` flag described above, and `-i` (or the `phpinfo()` function) will return more information about the configuration, version etc. of the modules.

*   `-r` *or* `--run`

Runs a line of PHP code supplied as the argument, rather than executing it from a file. The line of code should be enclosed by single quotes, as shells like bash will try and interpolate PHP variables as if they were shell variables if you use double quotes. This performs a similar role to the `-a` interactive mode, except that PHP’s “state” is cleared after each line is executed. This means that the line of code supplied is treated as the whole script to be executed, and execution is terminated once it has been run. An Example would be:

```
1 ~$ php -r 'echo (2+2)."\n";'
```

which will print out `4` followed by a new line character. Note that the line must be well-formed syntactically correct PHP, so don’t miss out the semi-colon at the end! We will return to `-r` later in this chapter in the section “The many ways to call PHP scripts”.

*   `-B` *or* `--process-begin`  
    `-R` *or* `--process-code`  
    `-F` *or* `--process-file`  
    `-E` *or* `--process-end`

These four arguments allow you to specify PHP code to be executed before, during and after input from `STDIN` is processed by PHP. `-B` specifies a line of code to execute before the input is processed, `-R` specifies a line of code to execute for every line of input whilst `-F` specifies a PHP file to execute for each line. Finally `-E` executes a line of code at the end of the input process. In `-R` and `-F`, two special variables are available; `$argn` - the text of the line being processed, and `$argi` - the number of the line being processed. This is mainly useful when using PHP directly in shell scripts. For instance, to print out a text file with line numbers, you can do something like:

```
1 ~$  cat my_text_file.txt | php -B 'echo "Lets add line numbers...\n";'
2         -R 'echo "$argi: $argn\n";' -E 'echo "That''s the end folks\n";'
```

which will output something like

```
1 Lets add line numbers...
2 1: Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do 
3 2: eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad
4 3: minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip
5 4: ex ea commodo consequat. Duis aute irure dolor in reprehenderit in 
6 That's the end folks
```

*   `-s` *or* `--syntax-highlight`

This outputs an HTML version of the PHP script, with coloured syntax highlighting. The PHP script is not executed or validated, it’s simply made “pretty”. The pretty HTML is printed to STDOUT, and can be useful when pouring over code looking for errors, issues and optimisations. This only works with PHP in files, not with code provided by the `-r` option. Most modern IDE’s and code editors provide syntax highlighting by default, however this can be useful if your only access to a machine is on the command line and the editor you are using doesn’t do syntax highlighting. In this case, use `-s` to create a coloured version of your script, and either download it or view it through your web browser if the machine has a web server installed.

*   `-v` *or* `--version`

This outputs the PHP version information. This can also be found in amongst the output of the `-i` option described above. Be careful when assuming a particular format, some package repositories (Ubuntu for instance) include their name and their own build numbers in the version string, so don’t just filter it for any numerics.

*   `-w` *or* `--strip`

This outputs the contents of the source code with any unnecessary white space and any comments removed. This can only be used with code files (not with lines of code supplied by `-r`) and does not work with the syntax highlighting option above. This is used to “minify” a file, i.e. reduce the file size. Contrary to popular opinion, this will not speed up most scripts, the overhead of parsing comments and white space is extremely negligible. You should also be wary of support & debugging issues even if a copy of the “full” code is kept, as line numbers in error reports will no longer match between the original and stripped versions. It also does not minify identifies like variable names, and so cannot be used to obfuscate your code. There are very few reason to use this option these days. To make a file smaller for distribution, using proper compression (e.g. adding it to a zip file) is usually a better method.

*   `-z` *or* `--zend-extension`

This specifies the filename/path for a Zend Extension to be loaded before your script is run. This allows dynamic loading of extensions, which can alternatively be specified in the `php.ini` file if they are always to be loaded.

*   `--rf` *or* `--rfunction`  
    `--rc` *or* `--rclass`  
    `--re` *or* `--rextension`  
    `--rz` *or* `--rzendextension`  
    `--ri` *or* `--rextinfo`

These options allow you to explore PHP structures using reflection. Reflection is the process by which PHP can perform runtime “introspection”, which is the means to allow you to look into elements and structures of your code at run time. The first three options above print reflection information about a named function, class or extension. The last two print basic information about a Zend extension or a standard extension, as returned by the `phpinfo()` function. This reflection information, which is very detailed, is only available if PHP is compiled with reflection support. These options can be used as a quick but precise reference guide to the entities listed above, and are particularly useful in interrogating unknown code written by others.

### 3.4 Command line arguments for your script

As we’ve seen above, passing arguments to PHP itself is straightforward and done in the normal way. However passing arguments for use by your PHP script is a little more complicated, as PHP needs to know where its own arguments stop and where your script’s start. The best way to examine how PHP deals with this is through some examples. Consider the following PHP script:

```
1 <?
2 
3 echo "Number of arguments given :".$argc."\n";
4 
5 echo "List of arguments given :\n";
6 
7 print_r($argv);
```

There are two special variables in the script above :

*   `$argc` : This records the number of command line arguments passed to the script
*   `$argv` : This is an array of the actual arguments passed.

Lets save the script as `arguments.php`. Now lets call it as follows :

```
1 ~$ php -e arguments.php -i -b=big -l red white "and blue"
```

You will get the following output :

```
 1 Number of arguments given :7
 2 List of arguments given :
 3 Array
 4 (
 5     [0] => arguments.php
 6     [1] => -i
 7     [2] => -b=big
 8     [3] => -l
 9     [4] => red
10     [5] => white
11     [6] => and blue
12 )
```

As you can see, all of the arguments given from the filename onwards in the command are passed to the script. The first, `-e`, which is used by PHP itself is not passed through. So, as a general rule, everything after the filename is treated as an argument to the script, anything before the filename is treated as an argument for PHP itself, and the filename is shared between the two.

There is, of course, an exception. As we learned above, in addition to specifying the filename of your script on its own, we can also pass it as part of the -f flag. So if we execute the following command:

```
1 ~$ php -e -f arguments.php -i -b=big -l red white "and blue"
```

we get the following unexpected output :

```
 1 phpinfo()
 2 PHP Version => 5.4.6-1ubuntu1.3
 3 
 4 System => Linux dev-system 3.5.0-37-generic #58-Ubuntu SMP Mon Jul 8 22:10:2\
 5 8 U
 6 TC 2013 i686
 7 Build Date => Jul 15 2013 18:23:34
 8 Server API => Command Line Interface
 9 Virtual Directory Support => disabled
10 Configuration File (php.ini) Path => /etc/php5/cli
11 <rest of output removed for brevity>
```

You may recognise this as the output of calling `php -i`. Rather than treating arguments after the filename as belonging to the script, PHP has treated the -i argument (and those afterwards) as one of it’s own. As `-i` is a valid PHP argument, it decides that it was what you wanted and invokes its “information” mode. If you need to pass the filename as part of the -f flag rather than as an argument on it’s own, you will need to separate your scripts arguments using `--`. So, for the command above to work as expected, we need to alter it to read:

```
1 ~$ php -e -f arguments.php -- -i -b=big -l red white "and blue"
```

Everything after the `--`, plus the script filename, is passed as arguments to the script, and we get the output we were expecting.

This can make your scripts a little messy, particularly if you are passing lots of arguments, so you may want to look at the sub-section on self-executing scripts in the next section, which will show you how to embed PHPs arguments in the script itself, allowing the script to claim any and all arguments passed as its own.

### 3.5 The many ways to call PHP scripts

As you can probably tell from the command line options in the previous section, there are several different ways to execute PHP code when using the CLI SAPI. Although we’ve covered a couple of these already, they are discussed here again for completeness.

#### 3.5.1 From a file

You can tell PHP to execute a particular PHP source code file. For instance:

```
1 php myscript.php
2 php -f myscript.php
```

Note that -f is optional, the above two lines are functionally equivalent. The PHP command line options detailed above, where appropriate, work in this method. E.g.

```
1 ~$ php -e myscript.php
```

will execute the file `myscript.php` in Extended Information Mode.

As with the web version of PHP, source files can be interpolated (mixed) with HTML (or, more usefully on the command line, plain text). So you will still need your opening `<?` or `<?php` tags, otherwise your source code will just be printed straight out without being executed.

#### 3.5.2 From a string

You can execute a single line of code with the `-r` flag :

```
1 ~$ php -r 'echo("Hello World!\n");'
```

Many of the other command line options are not available with the `-r` method, such as syntax highlighting. Watch out for shell variable substitution (use single quotes rather than double quotes around your code) and other mangling of your code by the shell. Unless it really is a quick one-off, it is likely safer and easier to pop the relevant line into a file and execute that instead. One common use of the `-r` option is for executing PHP generated by other (possibly non-PHP) shell commands where the whole shell script needs to execute in memory without touching disk (for instance where permissions prohibit disk write access).

#### 3.5.3 From STDIN :

If you do not specify a file or use the `-r` option, PHP will treat the contents of `STDIN` as the PHP code to be executed, as shown here:

```
1 ~$ echo '<? echo "hello\n";?>' | php
```

You can also use this method with `-B`,`-R`,`-F` and `-E` to makes PHP a first class citizen in shell scripting, giving you the ability to pipe data in and out of PHP. For instance, to reverse every line of a file (or any data source that you pipe into it), use

```
1 ~$ cat file.txt | php -R 'echo strrev($argn)."\n";' | grep php
```

In this line of code, we pipe the contents of a text file into PHP. The `-R` option tells PHP to execute the following PHP code on each line of input, where the line is stored in the special variable `$argn`. In this case, we reverse `$argn` using the string reversing function `strrev()` and then echo the reversed string out again. Any `echo`‘d output goes to `STDOUT`, which is either printed to the shell or, as in this case, can be piped to another shell command. In our case we then use `grep` to only display the lines containing the string ‘php’, which is ‘php’ backwards. More details on `-R` and its siblings are given in the previous section.

If you want to use options like `-R`, but have too much PHP code to fit comfortably on the command line, you can put the code in a normal PHP source code file and `include()` it, e.g.

```
1 ~$ cat something.txt > php -R 'include("complicated.php");'
```

If it is a non-trivial PHP script, it may be more efficient to package it up into functions and include it once with -B (-B means it’s executed before the main code), and then execute the function each time with -R. The following example loads the content of `my_functions.php` once at the start, and then the function `complicated()` from that file is called on each line (each `$argn`) from the data file (`data.txt`).

```
1 php -B 'include("my_functions.php");' -R 'complicated($argn);'
2 	-f 'data.txt'
```

Although these commands look relatively simple, there is of course no arbitrary limit to the PHP code you can put behind them. You can use classes and objects, multiple files, and most of the code and techniques explored in this book, exposing only functions or methods at the shell level as an interface for the user. You can also open the standard streams as PHP streams within PHP and access their file pointers to read data in from, negating the need to use -R, as discussed in the next chapter.

#### 3.5.4 As a self executing script : Unix/Linux

On Unix/Linux type systems you can make a PHP script file into a directly executable shell command. Simply make the very first line of the script file a `#!` line (usually pronounce “shebang line” or “hashbang line”) with path to the PHP binary, e.g.

```
1 #!/usr/bin/php
2 <?
3 
4 echo('Hello World!');
```

and set the executable bit using `chmod` or similar, e.g.

```
1 ~$ chmod a+x myscript.php
```

Then simply typing `./myscript.php` at the command line to execute it. You can also rename the file to remove the `.php` extension (assuming you had one in the first place), so you would just type

```
1 ~$ ./myscript
```

at the shell prompt to run it. You can further simplify it to remove the initial `./` by moving it to a directory somewhere in your shell’s search path. Note that when running a script in this manor, any command line options are passed directly to the script and not to PHP. In fact, you cannot pass extra command line parameters to PHP at runtime using this method, you must include them in the “shebang” line when constructing your script. For instance, in the example above, if you wanted to use “Extended Information Mode”, you would alter the first line of the script to read:

```
1 #!/usr/bin/php -e
```

If you were to instead call the script as follows :

```
1 ~$ myscript -e
```

then the `-e` flag would be passed as an argument to the script, not to PHP directly, and so PHP would not enter EIM. This is useful for scripts that have lots of user supplied arguments, but also makes options like `-B` and `-R` discussed in the method above cumbersome to use for processing `STDIN` data, as you have to include all of the PHP on the shebang line where it is harder to change. However you can simply `include()` the necessary files and use standard file streams to process the `STDIN` stream (created and opened by the CLI SAPI automatically for you) line by line instead.

If your script may be used on other systems, please bear in mind that the PHP binary will quite often be located in a different directory to the one on your system. In this scenario, you will need to change the shebang line for each system if you hard-code the location in it. Fortunately, if installed correctly, PHP sets an environment variable with its location, available via the `/usr/bin/env` shell command. So if you change the shebang line as follows, your script should be executable wherever PHP is located :

```
1 #!/usr/bin/env php
```

On Windows, the “shebang” line can be left in, as PHP will recognise it and ignore it. However it will not execute the file as it does on \*nix.

#### 3.5.5 As a self executing script : Windows

In a similar manner, scripts can be executed by calling them directly under Windows. However, the process for setting Windows up to do this is slightly more involved, requiring changes to the Registry and file type associations. I therefore recommend reading the official PHP documentation which covers this in detail.

#### 3.5.6 Windows php-win.exe

PHP for Windows also ships with php-win.exe, which is similar to the CLI build of PHP, except that it does not open a command line window. This is useful for running system software in the background or running scripts which create their own graphical interface.

### 3.6 Quitting your script

We’ve looked at starting your scripts, but what happens when it comes time to finish running them?

Like web based PHP scripts, CLI scripts will terminate happily when we hit the end of the script file, and will tidy up all the resources used in the same way. Likewise, if we want to end early, we can call the `exit` (or equivalent `die`) language construct.

However in the world of CLI scripts this isn’t considered very polite. Because CLI command are designed to work together, often in chains of commands, most shell programs and scripts will provide an “exit code” when they terminate to let the other programs around them know *why* they finished. Were they done? Did they encounter an error? Were they called incorrectly? Enquiring minds want to know.

It is particularly important to supply an exit code when your script may be the last item in a shell script, as the exit code of the shell script as a whole is taken to be the last exit code returned within it. We can make our PHP script provide an exit code, simply by including it as a parameter to `exit` or `die`. An exit code is an integer, and there are a number of common exit codes :

*   **0** : Success - we’ve exited normally.
*   **1** : General Error - usually used for application/language specific errors and syntax errors
*   **2** : Incorrect Usage
*   **126** : Command is not executable - usually permissions related
*   **127** : Command Not Found
*   **128+N** (up to **165**): Command terminated by POSIX Signal number N - e.g. In the case of `kill -9 myscript.php` it should return code 137 (128+9)
*   **130** : Command terminated by Ctrl-C (Ctrl-C is POSIX code 2, so as above 128+2 = 130)

Any other positive integer is generally construed as exiting due to an unspecified error. So, for instance, if you decide the command line arguments provided by your user are not in the correct format, you should terminate your script using `exit(2)`. If instead all goes well and your script continues to the end of its script file, you can actually let it exit by itself (or by calling `exit` without a parameter), as it returns status code 0 by default.

As with web scripts, you can register functions to be executed when your PHP script exits using the `register_shutdown_function()` function. One use for this may be to check that all is well and evaluate which exit code should be returned. The exit code used as the parameter to `exit` or `die` within a registered shutdown functions overrides the code used in the initial exit call that initiated shutdown. This means that you can happily `exit(0)` everywhere, then `exit(76)` from your shutdown function if you detect that the foo conflaganation isn’t aligned with the bar initispations in your metaspacialatific object. Or similar.

### 3.7 PHP REPLs

When you want to test out a few lines of PHP, your default instinct may be to create a new PHP file, save it, and then execute it with PHP. There is a better, faster and more interactive, way however. The PHP “Interactive Shell”, also known as the PHP REPL (Read-Eval-Print-Loop), is a quick and easy way to type in code and have it execute immediately. Unlike executing single lines of code using `php -r`, the REPL (started by calling `php -a`) keeps the scripts state (e.g. contents of variables and objects) in-between each line that you type, until you exit. You can use all of PHP’s functions, although no libraries are loaded by default, and you can `include()` or `require()` existing files of PHP code. This latter capability is useful for debugging the final output of a problematic script; simply `include()` your script which will execute the script and, as long the script doesn’t terminate prematurely, then you can `echo()` or `print_r()` or otherwise explore the state of the variables and other resources at the end of the run. Other brands of REPL are available, and are listed later in this section. By it’s nature, it can also be used as a CLI / Shell in it’s own right, calling other PHP and non-PHP programs as you would in, for instance, a bash shell.

The following example is a capture of an actual interactive REPL session using the standard PHP REPL.

```
 1 ~$ php -a
 2 Interactive shell
 3 
 4 php > # As we can type any valid PHP, I have added comments
 5 php > # directly to the REPL, rather than afterwards in editing!
 6 php > 
 7 php > # Lets start with some simple assignments :
 8 php > 
 9 php > $a = 5;
10 php > $b = 6;
11 php > 
12 php > # The REPL will throw Notices, Warnings and Errors as appropriate, 
13 php > # in real-time :
14 php > 
15 php > $c = nothingdefined;
16 PHP Notice:  Use of undefined constant nothingdefined - assumed 
17 'nothingdefined' in php shell code on line 1
18 php > 
19 php > # Just as with normal PHP source files, we can split commands across 
20 php > # lines. The interpreter only kicks in when it hits the terminating 
21 php > # semicolon :
22 php > 
23 php > $d 
24 php > =
25 php > 7
26 php > ;
27 php > 
28 php > # The following shows that the state in the variables above has been
29 php > # kept :
30 php >
31 php > echo $a + $b + $c + $d ."\n";
32 18
33 php > 
34 php > # Next, a more interesting example. Use the REPL instead of the 
35 php > # shell to get the first line from a file :
36 php > 
37 php > echo file ('/proc/version')[0];
38 Linux version 3.5.0-21-generic (buildd@roseapple) (gcc version 4.7.2 
39 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #32-Ubuntu SMP Tue Dec 11 18:52:46 UTC 
40 2012
41 php >
42 php > # Of course all of the usual protocol wrappers are available, so we 
43 php > # can see what is happening in the world...
44 php > 
45 php > $page = file ('http://news.bbc.co.uk');
46 php > 
47 php > echo $page[0];
48 <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML+RDFa 1.0//EN" "http://www.w3.org/
49 MarkUp/DTD/xhtml-rdfa-1.dtd">
50 php > 
51 php > # and maybe get a hash of that...
52 php > 
53 php > echo md5 ( implode ( $page, "\n" ) ) . "\n";
54 0319bf4e62db39fb2c89210e48783d70
55 php > 
56 php > # when we are done ...
57 php > 
58 php > exit;
59 php > 
60 php > # doesn't work, as its just evaluated as PHP (and the REPL ignores
61 php > # exit/die calls. To exit the REPL, enter the word 'exit' on its own
62 php > # on a new line
63 php > 
64 php > exit
65 ~$
```

Sometimes you’ll want to execute your commands within the “environment” of other scripts. For instance, you may have a script that declares constants, sets up database connections and does other routine tasks that you normally `include()` at the start of your main PHP scripts. As noted above you can `include()` these files in the REPL too, but you may forget to do so and then wonder why things didn’t work as they should. One facility PHP offers us, which applies not only to the REPL but to all forms of PHP execution, is the `auto_prepend_file` configuration directive. This tells PHP to execute a given file each time PHP is run before it starts to do anything else (like executing the script you have asked it to). This can either be set in php.ini, or via the `-d` flag on the command line. The following is an example of presetting some constants/variables. First, we create a script called `initialise.php` with the following content.

```
1 <?
2 
3 const FOUR = 4; # Declare a constant value
4 
5 $five = 5; # Instantiate a variable with another value
```

and then, at the command line, start and run a REPL session as follows, using `-d` to execute the `initialise.php` script first.

```
1 $> php -d auto_prepend_file=initialise.php -a
2 Interactive shell
3 
4 php > echo (FOUR + $five)."\n";
5 9
6 php > exit
7 $>
```

As you can see, the constant and variable we had set up in the initialise.php file were available for use from the REPL without having to manually declare them. The `-d` flag is used here, but the option could be set in php.ini as well if you want to always use the same file. If you regularly use a few different initialisation files like this, you can create shell aliases to commands using the `-d` flag. For instance, you could add lines similar to the following to your `~/.bash_profile`:

```
1 alias php-cl="php -d auto_prepend_file=clientSetup.php -a"
2 alias php-in="php -d auto_prepend_file=ourSiteSetup.php -a"
```

As well as the built in PHP REPL explored above, there are a number of third-party REPLs available, some of which include features such as a history of commands typed, tab-completion of commands, protection from fatal errors and even abbreviated function documentation.

## 4\. User facing software

After slugging through the preliminary information necessary to understand developing PHP in a non-web context, we’re now getting to the nitty-gritty of how to start communicating with our users without the rendering engine of a web browser.

### 4.1 Command line interface basics

Although graphical interfaces seem to rule the roost these days, there are still plenty of uses for text-based interfaces, particularly in environments with technically-adept users. When creating a text based program to run on the command line, there are three primary considerations over-and-above the PHP you are already accustomed to. These are

1.  Getting keyboard input
2.  Outputting text (and graphics) to the screen
3.  Program flow control

Rather than describe each one in isolation, we will instead look through a simple program that contains elements of each. Read through the code and comments below. The program is a screen-saver type routine which fills the shell with colour via a wiggling snake-like cursor.

```
  1 <?
  2 
  3 # First we will define some named constants.
  4 # These are shell escape codes, used for formatting
  5 # Defining them as named constants helps to make our code more readable.
  6 
  7 define("ESC", "\033");
  8 define("CLEAR", ESC."[2J");
  9 define("HOME", ESC."[0;0f");
 10 
 11 # We will output some instructions to the user. Note that we use
 12 # fwrite rather than echo. The aim is to write our output back to the 
 13 # shell where the user will see it. fwrite(STDOUT... writes to the
 14 # php://stdout stream. Echo (and print) write to the php://output
 15 # stream. Usually these are both the same thing, but they don't have to
 16 # be. Additionally php://output is subject to the Output control &
 17 # buffering functions (http://www.php.net/manual/en/book.outcontrol.php) 
 18 # which may or may not be desirable. 
 19 
 20 fwrite(STDOUT, "Press Enter To Begin, And Enter Again To End");
 21 
 22 # Now we wait for the user to press enter. By default, STDIN is
 23 # a blocking stream, which means that when we try to read from it,
 24 # our script will stop and wait some input. Keyboard input to the shell
 25 # is passed to our script (via fread) when the user presses Enter.
 26 
 27 fread(STDIN,1);
 28 
 29 # We want the program to run until the user presses enter again. This 
 30 # means that we want to periodically check for input with fread, but not 
 31 # to pause/block the program if there isn't any input. So we set STDIN to
 32 # be non-blocking.
 33 
 34 stream_set_blocking(STDIN, 0);
 35 
 36 # In preparation for our output, we want to clear the terminal and draw a
 37 # pretty frame around it. To do this we need to know how big the terminal
 38 # window currently is. There is no in-built way to do this, so we call an
 39 # external shell command called tput, which gives information about the
 40 # current terminal.
 41 
 42 $rows = intval(`tput lines`);
 43 $cols = intval(`tput cols`);
 44 
 45 # We now write two special escape codes to the terminal, the first 
 46 # of which (\033[2J) clears the screen, the second of which (\033[0;0f)
 47 # puts the cursor at the top left of the screen. We've already defined 
 48 # these as the constants CLEAR and HOME at the start of the script
 49 
 50 fwrite(STDOUT, CLEAR.HOME);
 51  
 52 # Now we want to draw a frame around our window. The simplest way to draw
 53 # "graphics" (or "semigraphics") in the terminal is to use box drawing
 54 # characters that are included with most fixed-width fonts used in 
 55 # terminals.
 56 
 57 # Draw the vertical frames by moving the cursor step-by-step down each
 58 # side. The cursor is moved with the escape code generated by 
 59 # ESC."[$rowcount;1f"
 60 
 61 for ($rowcount = 2; $rowcount < $rows; $rowcount++) {
 62 	fwrite(STDOUT, ESC."[$rowcount;1f"."║"); # e.g. \033[7;1f║ for line 7
 63 	fwrite(STDOUT, ESC."[$rowcount;${cols}f"."║");
 64 }
 65 
 66 # Now do the same for the horizontal frames.
 67 
 68 for ($colcount = 2; $colcount < $cols; $colcount++) {
 69 	fwrite(STDOUT, ESC."[1;${colcount}f"."═");
 70 	fwrite(STDOUT, ESC."[$rows;${colcount}f"."═");
 71 }
 72 
 73 # And finally fill in the corners.
 74 
 75 fwrite(STDOUT, ESC."[1;1f"."╔");
 76 fwrite(STDOUT, ESC."[1;${cols}f"."╗");
 77 fwrite(STDOUT, ESC."[$rows;1f"."╚");
 78 fwrite(STDOUT, ESC."[$rows;${cols}f"."╝");
 79 
 80 # You can see the range of box drawing characters available at 
 81 # http://en.wikipedia.org/wiki/Box-drawing_character
 82 # They are just "text" like any other character, so you can easily copy
 83 # and paste them into most editors.
 84 
 85 # $p is an array [x,y] that holds the position of our cursor. We will
 86 # initialise it to be the centre of the screen.
 87 
 88 $p = ["x"=>intval($cols/2), "y"=>intval($rows/2)];
 89 
 90 # Now for our first element of flow control. We need to keep the program
 91 # running until the user provides input. The simplest way to do this is to
 92 # use a never-ending loop using while(1). "1" always evaluates to true, so
 93 # the while loop will never end. When we (or the user) are ready to end 
 94 # the program, we can use the "break" construct to step out of the loop
 95 # and continue the remaining script after the end of the loop.
 96 
 97 while (1) {
 98 
 99 	# Each time we go through the loop, we want to check if the user has
100 	# pressed enter while we were in the last loop. Remember that STDIN is
101 	# no longer blocking, so if there is no input the program continues
102 	# immediately. If there is input we use break to leave the while loop.
103 
104 	if (fread(STDIN,1)) { break; };
105 
106 	# We will step the position of the cursor, stored in $p, by a random
107 	# amount in both the x and y axis. This makes our snake crawl!
108 
109 	$p['x'] = $p['x'] + rand(-1,1);
110 	$p['y'] = $p['y'] + rand(-1,1);
111 
112 	# We check that our snake won't step onto or over the frame, to keep
113 	# it in its box!
114 
115 	if ($p['x'] > ($cols-1)) { $p['x'] = ($cols-1);};
116 	if ($p['y'] > ($rows-1)) { $p['y'] = ($rows-1);};
117 	if ($p['x'] < 2) { $p['x'] = 2;};
118 	if ($p['y'] < 2) { $p['y'] = 2;};
119 
120 	# We want a pretty trail, so we need to pick random colours for the
121 	# foreground and background colour of our snake, that change at 
122 	# each step. Colours in the terminal are set with yet more escape 
123 	# codes, from a limited palette, specified by integers.
124 
125 	$fg_color = rand(30,37);
126 	$bg_color = rand(40,47);
127 
128 	# Once chosen, we set the colours by outputting the escape codes. This
129 	# doesn't immediately print anything, it just sets the colour of 
130 	# whatever else follows.
131 
132 	fwrite(STDOUT, ESC."[${fg_color}m"); # \033[$32m sets green foreground
133 	fwrite(STDOUT, ESC."[${bg_color}m"); # \033[$42m sets green background 
134 
135 	# Finally we output a segment of snake (another box drawing character)
136 	# at the new location. It will appear with the colours we just set, at
137 	# the location stored in $p
138 
139 	fwrite(STDOUT, ESC."[${p['y']};${p['x']}f"."╬");
140 
141 	# Before we let the while loop start again, we need to do one more 
142 	# very important thing. We need to give your processor a rest.
143 	# If we just continued our loop straight away, you would find your
144 	# processor being hammered, just for our relatively simple program.
145 	# Our snake would also consume the screen at super-speed!
146 	# usleep pauses execution of the program, so others can use the 
147 	# processor or the processor can "rest". Every little bit helps the
148 	# responsiveness of your machine, so even if you need your program
149 	# to loop as fast as possible, consider even a small usleep if you can
150 
151 	usleep(1000);
152 };
153 
154 # If this line of code has been reached, it means that we have 'break'd
155 # from the while loop.
156 
157 # To be a good citizen of the terminal, we need to clean up the screen
158 # before we exit. Otherwise, the cursor will remain on which-ever line
159 # our snake left it, and the background/foreground colours will be
160 # the last ones chosen for our snake segment. 
161 
162 # The following escape code tells the terminal to use its default colours.
163 
164 fwrite(STDOUT, ESC."[0m");
165 
166 # We then clear the screen and put the cursor at the top-left, as we
167 # did earlier.
168 
169 fwrite(STDOUT, CLEAR.HOME);
```

This program should demonstrate the three basics we listed earlier.

1.  Getting keyboard input. You can read from `STDIN` in the same way you would any stream.
2.  Outputting text (and graphics) to the screen. You can output to `STDOUT` (or use `echo`/`print`), control the appearance and cursor with escape characters, and use block drawing characters to make “semigraphics”.
3.  Program flow control. A `while(1)` loop is useful for keeping a program running, with `break` to continue flow outside the loop. It’s important to use `usleep` or `sleep` to stop your process hogging a processor.

### 4.2 Advanced command line input

In the section above we used `fread()` to read keyboard input. This is suitable for simple programs, but if you are looking to create a more complex interface to allow users to issue commands then you may wish to look at the readline extension, which you can use to implement a shell-like editable command line program.

The following example script shows how to implement a simple bespoke command line type interface with the readline library.

```
  1 <?
  2 
  3 # Create arrays to hold our command history and list of valid commands.
  4 
  5 $history = array();
  6 $validCommands = array();
  7 
  8 # Define some valid commands.
  9 
 10 $validCommands[] = 'kill';
 11 $validCommands[] = 'destroy';
 12 $validCommands[] = 'obliterate';
 13 $validCommands[] = 'history';
 14 $validCommands[] = 'byebye';
 15 
 16 # We want to enable tab-completion of commands, which allows the user to
 17 # start typing a command and then press tab to have it completed, as 
 18 # happens in Bash shells and the like. We need to provide a function (via
 19 # readline_completion_function) that will provide an array of possible 
 20 # functions names. This can be based on the $partial characters the user
 21 # has typed or the point in the program we are at, or any other 
 22 # factors we want. In our case, we'll simply provide an array of ALL of
 23 # the valid commands we have.
 24 
 25 function tab_complete ($partial) {
 26 	global $validCommands;
 27 	return $validCommands;
 28 };
 29 
 30 readline_completion_function('tab_complete');
 31 
 32 # We now enter our main program loop. Note that we don't include a usleep,
 33 # as readline pauses our program execution while it waits for input from
 34 # the user.
 35 
 36 while (1) {
 37 
 38 	# We call readline with a string that forms the command prompt. In our
 39 	# case we'll put the date & time in there to show that we can change 
 40 	# it each time its called. Whatever the user enters is returned. This 
 41 	# one simple line implements most of the readline magic. At this stage 
 42 	# the user can take advantage of tab-completion, history (use up/down 
 43 	# cursor keys) and so on.
 44 
 45 	$line = readline(date('H:i:s')." Enter command > ");
 46 
 47 	# We need to manually add commands to the history. This is used for 
 48 	# the command history that the user accesses with the up/down cursor 
 49 	# keys. We could choose to ignore commands (mis-typed ones or
 50 	# intermediate input, for example) if we want.
 51 	
 52 	readline_add_history($line);
 53 	
 54 	# If we want to programmatically retrieve the history, we can use a 
 55 	# function called readline_list_history(). However, this is only
 56 	# available if PHP has been compiled using libreadline. In most cases,
 57 	# modern distributions compile it using the compatible libedit library
 58 	# for licensing and other reasons. So we will keep a parallel copy of
 59 	# the history in an array for programatic access.
 60 
 61 	$history[] = $line;
 62 
 63 	# Now we decide what to do with the users input. In real life, we may
 64 	# want to trim(), strtolower() and otherwise filter the input first.
 65 
 66 	switch ($line) {
 67 
 68 	    case "kill":
 69 	        echo "You don't want to do that.\n";
 70 	        break;
 71 
 72 	    case "destroy":
 73 	        echo "That really isn't a good idea.\n";
 74 	        break;
 75 
 76 	    case "obliterate":
 77 	        echo "Well, if we really must.\n";
 78 	        break;
 79 
 80 		case "history":
 81 
 82 			# We will use the parallel copy of the command history that we
 83 			# created earlier to display the command history.
 84 
 85         	$counter = 0;
 86 
 87 			foreach($history as $command) {
 88 				$counter++;
 89 				echo("$counter: $command\n");
 90 			};
 91 
 92 	        break;
 93 
 94 	    case "byebye":
 95 
 96 	    	# If it's time to leave, we want to break from both the switch
 97 	    	# statement and the while loop, so we break with a level of 2.
 98 
 99     	    break 2;
100 
101     	default : 
102 
103     		# Always remember to give feedback in the case of user error.
104 
105     		echo("Sorry, command ".$line." was not recognised.\n");
106 	}
107 
108 };
109 
110 # If we reached here, the user typed byebye. 
111 
112 echo("Bye bye, come again soon!\n");
```

You may have noticed that I chose to use `byebye` as the command to quit the program. This was not just a whimsical choice on my part, but to illustrate the need to think about discoverability. If you were presented with this program, without seeing the source code above, and asked to close it, it’s likely you would try `quit`, `exit`, `end` and so on, before resorting to a good old `Ctrl-C`. In a GUI interface, you would have no such problems when faced with a button that said “Bye Bye!”. With text based input, it is best to stick to common and memorable formats for commands, provide visual guidance and clues where possible, and aid in discoverability with good documentation, a `help` command, and user training.

### 4.3 Using STDIN, STOUT & STDERR

The PHP CLI SAPI automatically opens the standard streams for you when your script starts, so there is no need to issue commands like `fopen('php://stdin', 'r')`. You can treat these streams just like any other PHP stream, and start using them straight away. We’ve included some examples above, but here are a few more to illustrate the options available.

```
 1 <?
 2 
 3 # Get one line of input from STDIN
 4 
 5 echo ('Please Type Something In : >');
 6 
 7 $line1 = fgets(STDIN);
 8 
 9 echo ('**** Line 1 : '.$line1." ****\n\n");
10 
11 # Get one line of input, without the newline character
12 
13 echo ('Please Type Something Else In : >');
14 
15 $line2 = trim(fgets(STDIN));
16 
17 echo ('**** Line 2 : '.$line2." ****\n\n");
18 
19 # Write an array out to STDOUT in CSV format.
20 # First, create an array of arrays...
21 
22 $records[] = array('User', 'Full Name', 'Gender');
23 $records[] = array('Rob', 'Robert Aley', 'M');
24 $records[] = array('Ada', 'Augusta Ada King, Countess of Lovelace', 'F');
25 $records[] = array('Grete', 'Grete Hermann', 'F');
26 
27 echo ("The following is your Data in CSV format :\n\n");
28 
29 # ...then convert each array to CSV on the fly as we write it out
30 
31 foreach ($records as $record) {
32 	fputcsv(STDOUT, $record);
33 };
34 
35 echo ("\n\nEnd of your CSV data\n");
36 
37 # Pause until the user enters something starting with a number 
38 
39 echo ('Please type one or more numbers : >');
40 
41 while (! fscanf(STDIN, "%d\n", $your_number) ) { 
42 
43 	echo ("No numbers found :>"); 
44 
45 };
46 
47 echo ("Your number was $your_number\n\n");
48 
49 # Send the text of a web page to STDOUT
50 
51 echo ("Press enter for some interwebs :\n\n");
52 
53 fread(STDIN, 1); # fread blocks until enter pressed
54 
55 fwrite(STDOUT, strip_tags( file_get_contents('http://www.cam.ac.uk') ) );
56 
57 # Send an error message to STDERR. You can just fwrite(STDERR,...
58 # if you want, or you can use the error_log function, which uses the 
59 # defined error handling routine. By default for the CLI SAPI this is
60 # printing to STDERR. 
61 
62 error_log('System ran out of beer. ABORT. ABORT.',4);
```

The error logged on the last line will usually appear in your shell along with the other output, as that is where most shells put `STDERR` by default. If you want to check that it did come via `STDERR` rather than `STDOUT`, the following bash command will highlight any `STDERR` output (denoted by the `2>`) in red. It uses escape codes to colour the error (31 sets the colour to red, 07 reverses it, then 0 clears it) :

```
1 php script.php 2> >(while read errors; do echo -e "\e[07;31m$errors\e[0m" 
2 	>&2;  done)
```

In short, we can use the standard streams in any number of ways, often treating them as standard file pointers or streams.

### 4.4 CLI helper libraries

There are some pre-written libraries/components available that can take some of the effort out of creating interactive console software. I’ve listed three common ones below. As with most libraries of this type, they are quite “opinionated” in how your program should be structured, so do look thoroughly through the documentation of each before choosing which best suites your project. The Symfony console (part of the Symfony Framework project) is well tested and very stable, as with most Symfony components it is well documented and supported. If you are familiar with the Symfony Framework then the code style should be familiar, but it is equally at home with other Frameworks (it is used for the Laravel Framework Artisan Console tool). The Webmozart Console toolkit is a re-factored version of the Symfony Console component, so has similar features, but a different coding style. It is also currently still in Beta. Finally, the Hoa Console is perhaps the most distinct of the three, with a coding style that focuses on real-world tasks and is arguably easier to get to grips with as a developer.

## 5\. PHP CLI scripts and your system

There are a number of areas where PHP CLI scripts typically interact with your system. While most system interactions are identical to those you’re used to with web scripts, there are a few area’s that you may not have used much, and we’ll look at a few gotcha’s that might trip you up.

### 5.1 Starting external processes from PHP, or “shelling out”

A common feature of CLI scripts is calling and interacting with other scripts and processes. Using other scripts and programs as “building blocks” within your script is a common pattern of CLI programming. As we’ve seen earlier, you can often combine your PHP script with others in general purpose shell scripts, but often it is useful for the PHP script itself to start other software when it needs to. This is often referred to as “shelling out”.

There are a number functions available in PHP to achieve this, each doing it in a slightly different way and with different benefits:

*   `exec()` : Executes a program and sends the text output to the user
*   `passthru()` : Executes a program and sends the binary output to the user
*   `system()` : Executes a program and gathers the output for use by PHP
*   `shell_exec()` : Executes a command via a shell and gathers it’s output for use by PHP
*   Backtick operator (e.g. `\`command``) : identical to `shell_exec()` above
*   `pcntl_exe()` : Executes a program in the current process space, that is to say it stops the current PHP script and replaces it with the specified program
*   `popen()` : Executes a program and opens a file pointer (identical to the pointers returned by `fopen()` for example) to read or write to the process via STDOUT or STDIN. Can only read or write, not both.
*   `proc_open()` : Like `popen`(), but with more control. Allows both reading and writing at the same time. Not as simple to use as `popen()`.

Which method you choose depends on what you intend to do with the newly opened process and how (or indeed if) you want to talk to it. If you’re not sure from the descriptions above which function is appropriate for your use, the Further Reading list below gives some pointers, information and examples of implementations which should give you some direction.

When calling external scripts, remember that using untrusted user input in command names or options is a recipe for a bad security day! The `escapeshellarg()` function can protect you from some inadvertent mistakes, but won’t stop you executing “bad” functions or files.

### 5.2 File Status and Realpath caches

On the web, speed is king. PHP operates two information caches to speed up access to the filesystem. The first is the file status cache, which caches information about a given file (like whether it exists, whether it is readable, it’s size and type, and so on). The second is the realpath cache, which caches the actual, real path for a given file or directory (expanding out symlinks, relative paths, ‘.’ and ‘..’ paths, include\_path’s and so on). Information is added to the cache automatically by PHP each time it encounters a new file, and is then used by any number of functions the next time they attempt to look at that same file. With a web page that’s gone in the blink of an eye where little may have happened on the filesystem, this is often a good trade-off for increased performance.

However the chances that the details of a file or path may change while your script runs obviously increase with the length of time that your script takes to execute. Therefore PHP gives us a couple of options for working with these two caches.

The following example shows the file status cache in action, and how to use `clearstatcache()` to clear it.

```
 1 <?
 2 
 3 # Create a file and add some text to it
 4 
 5 $filename = 'test.txt';
 6 
 7 $handle = fopen($filename, 'w+');
 8 
 9 fwrite($handle, 'test');
10 
11 # The following should print 4
12 
13 echo stat($filename)["size"]."\n";
14 
15 # Now write some data to the file, increasing the file size.
16 
17 fwrite($handle, 'more test');
18 
19 # Intuitively, the following command should print 13 as the file is now
20 # bigger than before. However it still prints 4, because the filesize 
21 # value for this file is now cached.
22 
23 echo stat($filename)["size"]."\n";
24 
25 # If we clear the cache ....
26 
27 clearstatcache();
28 
29 # then the next line should print 13 as expected
30 
31 echo stat($filename)["size"]."\n";
32 
33 fclose($handle);
```

The realpath cache operates in a similar way, and can be cleared by calling `clearstatcache(true)`, i.e. by calling it with true as the first parameter. You can also clear the cache for just one particular file by calling `clearstatcache(true, 'myfile.txt')`, where the second parameter is the filename (and the first must be set to true, that is, you must also clear the realpath cache).

Of course clearing these caches may not be necessary in your application and doing so has performance implications. Consider each file access on a case-by-case basis.

### 5.3 APC and other code caches

You may be aware of the APC caching system and other code caching systems that act to speed up the startup time of your script. APC, and most other systems, will not work with CLI scripts (or at least not add any benefit) as they work on a shared process model found with webservers such as Apache. As PHP CLI scripts (typically) terminate their own process when they complete, these will not work.

## 6\. Where now? or, Thanks & feedback

If you’ve read this far, thank you. I sincerely hope that this book has held your interest and at the very least informed some areas of your future PHP programming. If it has, I would encourage you to start some coding right now based on one or more topics in this book while they are still fresh in your mind. People far smarter than me have shown that the sooner relevant activity occurs after learning, the easier it is to retain information and techniques over the longer term. If you use any of the techniques presented in the book in “real-life”, I would be very interested to know! Finally, if you’ve not already headed for the keyboard, don’t forget to glance through the Appendices that follow. There may be something interesting or useful in there for you (either to use now or to be aware of for the future).

### 6.1 Upgrade to “PHP Beyond The Web” for only $5!

The content in this book is an adapted subset of one of another book I wrote called “PHP Beyond The Web” . As well as CLI scripts, it covers the many other things you can do with PHP including (but not limited to) writing software daemons, desktop GUI applications, interface with other software processes and hardware like printers, and even control electronics with a Raspberry Pi. It also looks further into topics like performance, development tools, garbage collection and other topics that get more revelant when you build big off-line systems.

As a reader of this book, you can check out a sample, peruse the table of contents and can get PHP Beyond The Web for only $5 USD (+VAT where applicable) from Leanpub simply by visiting [http://leanpub/php/c/upgrade](http://leanpub/php/c/upgrade) . And even at that price, it still comes with the Leanpub unconditional, no risk, 100% happiness guarantee, which is a long way of saying an unconditional 45-day two-click refund.

### 6.2 Giving feedback, and getting help and support

E-mail : author@phpbeyondtheweb.com

Your feedback on this book, good or bad, fundamental or trivial, is solicited and very much welcomed. Tell me what you thought about the book, overall or a particular section. Let me know if any areas weren’t covered in enough depth (or in too much detail), if any topics you were expecting weren’t present, or any of the information wasn’t clear. Likewise, if you have any problems getting the sample code to run, or issues implementing the techniques discussed please do drop me a line and I’ll see if there is any way I can help.

### 6.3 Are you reading a “pirated” copy?

There are times in my life when I have read “unauthorised” copies of books; when I couldn’t afford them, when they weren’t easily available through legitimate channels (local bookshops, online sales, libraries), or (for e-books) when DRM thwarted my efforts to read them on the devices I had available. So I quite understand if you are in this position, and I don’t want to criticise your choice. If you are unable to afford this book, perhaps you could consider purchasing it in the future when you are able, and in the meantime I would ask that you do me a favour in return - please consider helping me to promote it by recommending it to those that can afford it, have a go at reviewing it online, and otherwise spread the word. If you’re reading an unauthorised copy because there was something else (other than cost) blocking your access to a legitimate copy, please let me know and I’ll do my very best to remove that obstacle. I want to enable everybody who wants to buy and read this book to be able to do so with the minimum of fuss. This is why I won’t employ DRM on my work, because for every “pirate” that it stops (and it won’t be many), there are likely to be ten times as many legitimate readers who it annoys.

If you are reading an unauthorised copy because you simply don’t want to pay for it, then that is between you and your conscience.

## Appendix A : Compiling and installing PHP, extensions and libraries

There are a dozen different ways to get PHP, including downloading & compiling it yourself, downloading pre-compiled binaries, using package managers and software repositories, and finding it pre-installed by a forward thinking administrator. On most Linux distributions, PHP can be installed with a one-line command such as `sudo apt-get install php5` or through graphical package managers like the Synaptic Package Manager or the Ubuntu Software Centre. Many common PHP extensions and add-ons are likewise available as pre-built packages or alternatively through the PECL and PEAR systems.

However there are times when it becomes necessary to do a little more work to install PHP, such as :

*   when your project has requirements for a specific version of PHP that is different to the one shipped with your OS
*   where you need extensions not available as packages,
*   or when you want to compile a customised version of PHP specific to your needs.

Like anything involved in computers and software development, compiling PHP can take you down a rabbit-hole of options, customisations, compatibility issues, libraries and dependencies. A whole book could be written about the different possibilities (and possible headaches) involved. Luckily for us, in most use cases, the basics of compiling a standard version are quite straightforward. And like most things in life, it gets easier once you have done it once. The first section below will go over the steps necessary for getting, compiling and installing PHP and its core extensions. PHP is written in C, and as many of you may not be familiar with the process of compiling C programs, I have tried to explain each step below to give you an idea of what is happening. This makes the process seem a little more verbose, but in reality it is quite straightforward. Go ahead and try it if you don’t believe me! The next sections are also worth a read, as they cover installing extras like libraries and extensions from the PECL, PEAR and Packagist repositories.

### Compiling and installing PHP itself

Note for Windows devs - These steps are for Linux/Unix type systems, and use free compiler tools almost always included with the OS. For Windows, the proprietary Visual Studio compiler is required, and the steps are somewhat different and beyond the scope of this book. Windows source code, pre-built binaries and instructions for compiling can be found at [http://windows.php.net/download/](http://windows.php.net/download/) , with older versions in the archive at [http://windows.php.net/downloads/releases/archives/](http://windows.php.net/downloads/releases/archives/).

Note for OS X devs - while the steps below are similar to those on a Mac, there are some issues you may run into depending on the version of OS X you are using. A great look at getting PHP (and related software) up and running on OS X Mavericks can be found at [http://akrabat.com/computing/setting-up-php-mysql-on-os-x-mavericks/](http://akrabat.com/computing/setting-up-php-mysql-on-os-x-mavericks/).

On \*nix machines, our first step is to download the PHP source code from the PHP website at [http://www.php.net/downloads.php](http://www.php.net/downloads.php) . This page lists the current stable release and the previous supported stable release. Newer versions which are still under development are available at [http://snaps.php.net/](http://snaps.php.net/), and older end-of-life versions are available at [http://museum.php.net/](http://museum.php.net/) . Git users can also pull the source code down from the official mirror at [https://github.com/php](https://github.com/php).

When you have identified which version you want, make a note of the URL of the .tar.gz source code file which we will use later.

```
1 ~$ mkdir php5.4
2 ~$ cd php5.4
3 ~$ wget http://uk3.php.net/get/php-5.4.6.tar.gz/from/uk.php.net/mirror 
4 	-o php-5.4.6.tar.gz
5 ~$ tar zxvf php-5.4.6.tar.gz
6 ~$ cd php-5.4.6
```

The first two lines creates a directory for our work and steps into it. The directory holds the source code and intermediate files, and can be deleted once PHP is installed if you want. However it is often a good idea to keep it in-case you need/want to re-install or check what version of the file you downloaded later. The third line downloads a copy of the source code file into our directory. Change the URL in the third line to that of the .tar.gz file you want to use, and the `-o` option to the name of the file (otherwise, in the above example, wget will simply call your file “mirror”). The fifth line unpacks the archive into a directory containing the individual source code files, change the name of the file to the one you used on line 3. Finally, the last line steps us into the source code directory. Now we start the actual compilation process.

```
1 ~$ ./configure
```

The configure command creates the “setup” for compilation. We use it to provide the settings and arguments we want for our compilation session. For instance, we can specify which core extensions we want to include in our build. If we don’t specify any arguments as above, the defaults provided by the PHP dev team are used. This is a good choice if you don’t have any particular needs and want a version that is fairly similar/compatible with the versions included with most distributions. You can also install extensions at a later date either individually or by re-compiling PHP from scratch, which we will discuss in the next section. If you want to include an extension at this stage that’s not included in the default settings, then this is the place to do it. For example, if you wanted to include the ldap extension, then you would change the command above to `./configure --with-ldap[=DIR]` where `[=DIR]` is the base installation directory of ldap on your system. The exact option to use and any necessary dependencies can be found in the PHP manual, under the “Installing/Configuring” section for the extension in question. For example, details for the ldap extension can be found at [http://www.php.net/manual/en/ldap.setup.php](http://www.php.net/manual/en/ldap.setup.php). A (slightly out-of-date) list of options that you can pass to the configure command can be found at [http://www.php.net/manual/en/configure.about.php](http://www.php.net/manual/en/configure.about.php) or, for a full list of those supported on your system in the current version you are trying to compile, you can issue the command `autoconf` followed by `./configure --help`. More information about the configure command can be found at [http://www.airs.com/ian/configure/](http://www.airs.com/ian/configure/). Now we will actually compile PHP.

```
1 ~$ make clean
2 ~$ make
3 ~$ sudo make install
```

We compile the binary PHP files using the “make” tool. The first line removes any previously created files and resets us to the start of the “make” process. This is not strictly necessary on your first run at compiling, but it can help if your attempt fails for some reason (such as missing dependencies, incorrect settings, unintended interruptions to the process etc.) so including it by default is often a good choice. The second line does the actual building and compiling of the files. The third line then takes those files and installs them on the system. By default, PHP will usually be installed in the `/usr/bin` directory on Linux. However you can choose where to install it by specifying a “prefix” directory at the `./configure` stage above. Simply add the switch `--prefix=/path/to/dir` where `/path/to/dir` is the directory into which you want PHP to be installed. This is often useful if you want to install multiple versions on the same machine (although be aware that there are other considerations when doing so). Note that the `make install` line must be run with higher permissions (`sudo`) to allow it to copy files into “privileged” locations.

If all goes well, congratulations, you have installed PHP! To check that the correct version is installed and available, use `php -v` at the command line and PHP will display the current version number. If you have installed PHP in a location outside of your search path you will need to specify the full path name, e.g. `/path/to/dir/php -v`. To check which extensions and other options were installed, use `php -i` at the command line to run the `phpinfo()` function. As well as extension information (and a lot more besides), this returns a list of the options used with the `./configure` command. This can be useful when re-installing PHP or when trying to clone an installation on another machine (where the same binaries cannot just be re-used).

If all doesn’t go well, have a close look at the errors produced. The most common type of errors happen when your system doesn’t have the relevant dependencies installed for a particular extension. Often the error message will say this explicitly, but even if it just gives you an obscure error message mentioning the name of an extension, the best advice is to double-check the installation section for that extension in the the PHP manual to find out exactly what dependencies are required. Missing dependencies can often be installed using your systems package manager rather than having to manually compile them. You should also check that you have provided the location of any dependencies at the configure stage above if required.

If all else fails, copy and paste the exact error message into your favourite internet search engine, probably starting with the first error message shown if multiple errors appear. Many, many people have compiled PHP, and most errors have been encountered and documented online. Don’t let all this talk of errors put you off having a go at compiling PHP. Errors are more likely to occur the more complicated you make your configuration, and if you’re careful about dependencies you can often avoid them altogether. So have a go at a straight forward compilation with the default options to get the hang of things, and take it from there!

More information on installations, with a general focus on web servers but otherwise useful, can be found in the PHP manual at [http://www.php.net/manual/en/install.php](http://www.php.net/manual/en/install.php).

### Compiling and installing (extra) core extensions

As we saw in the previous section, the most common way to install core extensions is to enable the relevant flags at the configure stage during compilation of the main PHP installation (note by default, many extensions are automatically enabled). However it’s not uncommon to come across the need to install an additional extension later on, for instance as the requirements for your program change from its initial design. There are two ways to approach this. The first, which you’ll find recommended a lot online, is to re-do the compilation/installation of PHP from scratch, adding the newly required modules at the configure stage (after issuing `php -i` to remember what configure options you used the first time). While this works perfectly well, compiling the full PHP binaries is a bit of a slog which can take older PCs in particular a long time to complete. There is a short cut however.

Each of the core extensions is actual a separate .so binary, and can be compiled independently. To do this, follow the first steps in the previous section to download and unpack the PHP source code and step into the directory. If you haven’t deleted it from when you compiled PHP itself, it should be ready to go. Within the source code is a directory called ext, inside of which are separate directories for each of the extensions.

```
1 ~$ cd ext
2 ~$ ls
```

This will show you all of the core extensions available. For instance, if we want to add the pcntl extension (used in this book for daemon software), we can enter the pnctl directory and compile/install just that extension in a similar manner to how we compiled the whole PHP package in the previous section.

```
1 ~$ cd pcntl
2 ~$ phpize
3 ~$ ./configure
4 ~$ make clean
5 ~$ make
6 ~$ sudo make install
```

The additional command above, `phpize`, is used to prepare the build environment for the extension. This is not necessary when building the full PHP binaries, but it is when building individual extensions. If you find that you don’t have phpize on your system, it is often available through your systems package manager in the `php-dev` package (e.g. on Ubuntu it is available as `phpize5` in the `php5-dev` package). More details about phpize and getting it can be found at [http://us.php.net/manual/en/install.pecl.phpize.php](http://us.php.net/manual/en/install.pecl.phpize.php).

Once the commands above have been run, you should find that a `.so` file (`pcntl.so` in our example) has been compiled and placed in PHP’s extension directory. The final step is to tell PHP about it, by adding the following line somewhere in your `php.ini` file:

```
1 extension=pcntl.so
```

If you’re not sure where your `php.ini` file is, you can run `php -i | grep "Loaded Configuration File"` on the command line to find out. You can also use `php -i` to check that your extension is now correctly installed and available for use.

### Installing multiple versions of PHP

Sometimes (particularly on development machines) you may want to install multiple versions of PHP at the same time, for instance if you are deploying to end users with PHP already installed but who may have different versions. One straight forward way to achieve this is to create a set of virtual machines (I use VirtualBox for this) with a different version of PHP installed in each. In this scenario you can always be sure which version you are running and that the installation and configuration of one version isn’t interfering with that of another. The downside is that it can be slow to start up and shut down different VMs (or a hit on resources to run them all at once), and if you are using proprietary OSes like Windows you can incur additional licensing costs. As I noted in a previous section, it is possible to have multiple versions installed and running directly on the same machine. However if you are not careful it can become a nightmare trying to keep the versions and their dependencies separate and making sure you know which version you are using at all times. As such I am not going to delve into it in this book. However below are two articles from respected PHP community members who have done just that, which may give you some pointers on what to do and the pitfalls involved. I would suggest that before you try this, you become intimately familiar with compiling and installing PHP, the file and directory structures and locations that PHP uses, and how to check which versions of PHP and extensions are running.

There are also a couple of relevant tools listed below. The first is php-build, which automatically builds multiple versions of PHP from source, although you still need to exercise care installing and using them simultaneously. The second is 3v4l.org, a web service which allows you to test chunks of code in 90+ versions of PHP at the same time. This may avoid the need for installing multiple versions at all. And the final tool is a library which simulates many functions from newer versions for use with older versions.

### PEAR and PECL

PEAR (PHP Extension and Application Repository) is a library of code and extensions written in PHP, with an easy to use packaging and distribution system. PECL (PHP Extension Community Library) is essentially the same, but for extensions written in C.

Both PECL and PEAR work in a similar way to package managers such as Debians apt-get. For example to install the Cairo graphics extension from PECL, simply do `sudo pecl install cairo` at the command line. This will download, compile and install Cairo for you and you can then start using it from within your PHP scripts. Similarly, to install the RDF extension from PEAR, use `pear install rdf`.

The `pear` and `pecl` commands are included as standard with PHP, however some package managers put them in the optional `php-dev` or `php-pear` package. On Ubuntu, for instance, use `sudo apt-get install php-pear` to install it.

More information on both as well as the hundreds of extensions and libraries available, can be found at [http://pear.php.net](http://pear.php.net) and [http://pecl.php.net](http://pecl.php.net) respectively.

### Composer

Composer is a dependency manager. While it deals with packages, it is not a package manager like PEAR. Rather than installing packages centrally, it deals with them on a per-project basis, ensuring that the appropriate versions of the relevant packages, and their dependencies, are installed automatically for that project.

The basic Composer workflow happens as follows :

*   You install Composer.
*   In the base directory of your project, you create a json-formatted file called `composer.json` that specifies which packages (and versions) your project needs
*   In that directory, you run Composer. It will fetch and install of the specified packages, and will automatically also install any of the other packages that those you have specified depend on (and so on until all dependencies are satisfied)
*   In your PHP code, simply add the function `require 'vendor/autoload.php';` and your libraries will be automatically available when you use them.

Fully comprehensive documentation, aimed at beginners as well as advanced users, is available on the composer website. Composer itself doesn’t host any packages, that is the job of package repositories. Packagist is the main, and currently the only, comprehensive public repository, and is the default used by Composer. You can browse the thousands of available packages on the Packagist website. You can of course specify a different repository and indeed create and use your own packages privately if you need to.

### Symfony2 bundles

If you’re using the Symfony2 framework, you can choose from and download over a thousand useful code bundles from knpbundles. These can be installed manually, or often using the Composer dependency system (see the section above). Visit [http://knpbundles.com/](http://knpbundles.com/) for more information and to browse the available code.

## Appendix B : Sources of help

Even with excellent books like this on on the market, you will sometimes need a little additional help when you come across a tricky problem with PHP. Below are some potential sources of help.

### The PHP manual

The official PHP manual can be found online at [http://php.net/docs.php](http://php.net/docs.php). The manual provides fairly comprehensive documentation in the main on PHP installation, syntax, functions and many extensions. Of particular note are the user comments at the bottom of each page. These are generally helpful and offer real-world advice related to the function or topic of the page. Occasionally some duff advice is given in the comments, however this is usually corrected or mentioned in a subsequent comment, so it’s worth reading through all of the comments on a given page.

A handy function of the online manual is that you can do a quick look up of a function or topic by typing it as the first part of a URL. For instance, if you can’t remember what the parameters of `strripos()` are, you can simply type [http://php.net/strripos](http://php.net/strripos) into your browser and you will be sent straight to the relevant page. Likewise, if you want a quick refresher on how PHP handles arrays, visit [http://php.net/array](http://php.net/array) and you’ll go straight to the array page in the language/types section of the manual.

If you don’t always have an internet connection, you can also download a copy of the manual from [http://www.php.net/download-docs.php](http://www.php.net/download-docs.php). It is available as HTML, Unix style man pages, and Microsoft Compiled HTML Manual (CHM) format.

### Official mailing lists

There are a number of official mailing lists at [http://php.net/mailing-lists.php](http://php.net/mailing-lists.php) covering a wide variety of topics. Of note for getting help are the “General user list” for general queries, and the “Windows PHP users list” for Windows specific questions. Beware if subscribing that some of the lists area quite busy and you will get a large number of emails each day. The archives are available online if you just want to browse or get a feel for the volume generated on each list.

### Stack Overflow

If you’re not familiar with it, Stack Overflow ([http://stackoverflow.com](http://stackoverflow.com)) is a prolific “Question and Answer” site aimed at programmers. Unlike some Q&A sites, you don’t need to join or pay to view the answers to questions, adverts are limited and there are literally millions of answered questions on the board. This includes a good chunk of PHP related questions.

All questions and answers are “tagged” with their topics so that you can find the ones relevant to you. To browse questions tagged with PHP, visit [http://stackoverflow.com/questions/tagged/php](http://stackoverflow.com/questions/tagged/php). You can also use the sites search facility, and to narrow you search to only PHP related answers add “\[tag\]” to your search. For example, if you want to search for questions about the `date` function, which is a common word in English and a common function name in many programming languages, search for “[php] date” to only get PHP specific information.

At the time of writing, there were 864,182 questions tagged with “php”, 1,087 tagged with “php” AND “command-line”, and 1,094 tagged with “php” AND “cli”. The moderators are usually very quick at shutting down duplicate questions, so you can see from these numbers that there is a lot of relevant information available.

### Other books

While you may think that this is the only book on PHP you will ever need, I have been told that there may be other PHP books available out there. While I can’t recommend any specifically (other than those I have already noted in the relevant chapters), if you browse any big name bookseller you will find a plethora of PHP related titles. If do want to purchase another book, and would like to help support the PHP.net project, follow the links from the books section at [http://php.net/support.php](http://php.net/support.php) to a well known book store, and PHP.net will receive a commission for anything that you buy after following their link.

### Newsgroups

PHP has a set of official newsgroups listed and archived at [http://news.php.net/](http://news.php.net/) which cover a wide range of PHP topic areas. These may be worth a browse, and sometimes can elicit a response to queries (although some of the internals lists are definitely not for the faint-hearted).

### PHP Subredit

The PHP “Subredit” on reddit.com at [http://www.reddit.com/r/PHP/](http://www.reddit.com/r/PHP/) is a mixture of PHP news, opinions, useful links and requests for help. Although usually genuinely interesting with helpful responses to questions, an occasional assortment of trolls and unhelpful/rude people can be found here as well.

### PHP on Github

Sometimes the best way to solve a problem is to look at similar code other people have written. Github, the popular source repository website, has tons of the stuff to plough through. You can search all of the code repositories at [https://github.com/search](https://github.com/search), and use the modifier “language:php” in your search terms to narrow your results to projects using our favourite language. If you just want to keep an eye on what PHP projects are popular these days, you can check out the PHP trending list at [https://github.com/trending?l=php](https://github.com/trending?l=php).

### PHP news sites

Although not usually good for direct help, PHP news sites and mailing lists can keep you up to date with essentials like security alerts, useful and interesting articles, and announcements of new projects, libraries and tutorials that you may not even know you needed yet! Some of the more popular ones are listed below.