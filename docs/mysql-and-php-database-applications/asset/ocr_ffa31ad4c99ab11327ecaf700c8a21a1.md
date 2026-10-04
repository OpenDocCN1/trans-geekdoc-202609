# Introduction

# The client

The applications you can develop with MySQL and PHP make use of a single client: the Web browser. This is not the only possibility for Internet-based applications. For very sophisticated applications that require more client-side processing or that need to maintain state (we will talk about maintaining state in the Introduction), a Java applet may be necessary. Unless you are coding something like a real-time chat program, client-side Java is completely unnecessary.

The only client you should be concerned with is the Web browser. The applications need to render in the browser. As you already know, the primary language of browsers is the hypertext markup language or HTML. HTML provides a set of tags that describe how a page should look. If you are new to the concept of HTML, get on the Web and read one of the many tutorials out. It shouldn't take much time to learn the basics.

Of course, most browsers accept more than HTML. There are all kinds of plug-ins, including RealPlayer, Flash, and Shockwave. Most browsers also have some level of support for JavaScript, and some of the newer ones can use XML. But like most developers, we will be taking a lowest-common-denominator approach in this book. We are going to create applications that can be read in any browser. There will be no JavaScript, XML, or anything else that could prevent some users from rendering the pages we serve. HTML it is.

# The server

Almost all of the work of Web applications takes place on the server. A specific application, called a Web server, will be responsible for communicating with the browser. A relational database server stores whatever information the application requires. Finally, you need a language to book requests between the Web server and the database server; it is used to perform programmatic tasks on the information that comes to and from the Web server. Figure I-1 represents this system.

But of course this is possible without an operating system. The Web server, programming language, and database server you must work well with with your operating system.

# OPERATING SYSTEM

There are many operating systems out there. Windows 99 and Macintosh OS are probably the most popular. But that's hardly the end of it. Circumstances may have forced you to work with some obscure OS or may even be under the impression that your OS is the best thing going. That's fine. If you're planning on spending a lot of time on the Web and are planning on running applications, you're best off getting to know either Windows NT/2000 or Unix. These two account for well over 90 percent of all the Web servers on the Web. It is probably easier for you to learn a little NT/2000 or Unix than it is to convince everybody else that the AS/400 is the way to go.