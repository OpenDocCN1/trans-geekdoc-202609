
## Part V Appendixes
- Appendix A HTML Forms ........................................................ 405
- Appendix B Brief Guide to PHP/MySQL Installation and Configuration ........................................................ 413
- Appendix C MySQL Utilities ........................................................ 423
- Appendix D MySQL User Administration ........................................................ 439
- Appendix E PHP Function Reference ........................................................ 447
- Appendix F Regular Expressions Overview ........................................................ 507
- Appendix G Helpful User-Defined Functions ........................................................ 517
- Appendix H PHP and MySQL Resources ........................................................ 543
- Appendix I MySQL Function Reference ........................................................ 551
- Appendix J What’s on the CD-ROM ........................................................ 585
- Index ........................................................ 587
- End-User License Agreement ........................................................ 599
- GNU General Public License ........................................................ 602
- CD-ROM Installation Instructions ........................................................ 608

## Introduction
SOON WE WILL HEAD OFF on a fabulous journey, a journey on which we will explore the ins and outs of MySQL and PHP database applications in great detail. It’s going to be a fun trip; we just know it.

OK, maybe we’re being a bit optimistic. If you’re anything like us, there will be points when this particular journey will be a lot more tedious than it is exciting. Let’s face facts: application development isn’t always the most exciting thing in the world. And as with any other venture that involves programming, there are sure to be some very frustrating times, whether because of a syntax error you can’t find or a piece of code that won’t do what you think it ought to do. But despite all that, here you are, and I think there is a very good reason for your being here.

Web applications are the present and the future. No matter your background, whether it be Visual Basic or COBOL, or maybe you know just some HTML and JavaScript, your résumé is only going to improve with some Web applications development experience. We don’t think there’s a better combination of tools to have under your belt than PHP and MySQL. The numbers bear us out. PHP and MySQL are becoming increasingly popular, and the demand for people who can use these tools will only increase.

But a bit later there will be more details on why you should use PHP and MySQL. Before we can get into the details of that, we want to take a bit of time to go over the architecture of Web applications. Once we’ve done this, we will be able to explain in detail why PHP and MySQL should be the centerpieces of your application development environment. Once we’ve sold you on these tools, we’ll present a very quick and grossly under-coded application. As you look over this application, you will see the basic syntax and principles behind PHP and MySQL.

![](img/de0823012275cf4ceebdb822a56e6b71_19_0.png)

As we proceed with the book, we will assume that you have read and understand everything presented in this introduction.

## Basic Architecture
At the most basic level, the Web works off of a client/server architecture. Simply stated, that means that both a central server and a client application are responsible for some amount of processing. This differs from a program such as Microsoft Word, which operates just fine without any help from a server. Those of you who used older VAX machines will remember the days of dumb terminals, which had no processing power whatsoever. Depending on where you work today, perhaps in a university or a bank, you may still use applications that are in no way dependent on the client. In other words, all the work is done on the central computer.

### The client
The applications you can develop with MySQL and PHP make use of a single client: the Web browser. This is not the only possibility for Internet-based applications. For very sophisticated applications that require more client-side processing or that need to maintain state (we will talk about maintaining state later in the Introduction), a Java applet may be necessary. But unless you're coding something like a real-time chat program, client-side Java is completely unnecessary.

So the only client you should be concerned with is the Web browser. The applications will need to render in the browser. As you probably already know, the primary language of browsers is the hypertext markup language or HTML. HTML provides a set of tags that describe how a Web page should look. If you are new to the concept of HTML, get on the Web and read one of the many tutorials out there. It shouldn't take that much time to learn the basics.

Of course, most browsers will accept more than HTML. There are all kinds of plug-ins, including RealPlayer, Flash, and Shockwave. Most browsers also have some level of support for JavaScript, and some of the newer ones can work with XML. But, like most Web developers, we will be taking a lowest-common-denominator approach in this book. We're going to create applications that can be read in any browser. There will be no JavaScript, XML, or anything else that could prevent some users from rendering the pages we serve. HTML it is.

### The server
Almost all of the work of Web applications takes place on the server. A specific application, called a Web server, will be responsible for communicating with the browser. A relational database server stores whatever information the application requires. Finally, you need a language to broker requests between the Web server and the database server; it will also be used to perform programmatic tasks on the information that comes to and from the Web server. Figure I-1 represents this system.

But of course none of this is possible without an operating system. The Web server, programming language, and database server you use must work well with your operating system.

### OPERATING SYSTEM
There are many operating systems out there. Windows 98 and Macintosh OS are probably the most popular. But that's hardly the end of it. Circumstances may have forced you to work with some obscure OS for the past few years. You may even be under the impression that your OS is the best thing going. That's fine. But if you're planning on spending a lot of time on the Web and are planning on running applications, you're best off getting to know either Windows NT/2000 or Unix. These two account for well over 90 percent of all the Web servers on the Web. It is probably easier for you to learn a little NT/2000 or Unix than it is to convince everybody else that the AS/400 is the way to go.

![](img/de0823012275cf4ceebdb822a56e6b71_21_0.png)

Figure I-1: Architecture of Web applications

Which should you use? Well, this is a complex question, and the answer for many will be based partially on religion. In case you're unaware of it, let's take a moment to talk about the broad topics in this religious war.

If you don't know what we are talking about, here are the basics. PHP and MySQL belong to a class of software known as open source. This means that the source code to the heart of their applications is available to anyone who wants to see it. They make use of an open-source development model, which allows anyone who is interested to participate in the development of the project. In the case of PHP, coders all over the world participate in the development of the language and see no immediate pay for their substantial work. Most of the people who participate are passionate about good software and code for the enjoyment of seeing people like you and me develop with their tools.

This method of development has been around for some time, but it has gained prominence as Linux has become increasingly popular. More often than not, open-source software is free. You can download the application, install it, and use it without getting permission from anyone or paying a dime to anyone.

Suffice it to say that Microsoft, Oracle, and other traditional software companies do not make use of this method of development.

If you are not an open-source zealot, there are excellent reasons to choose NT/2000. Usually, the thing that steers people towards NT/2000 is inertia. If you or your company has been developing with Microsoft products for years, it is probably going to be easier to stay within that environment. If you have a team of people who
