
# Core PHP Programming

The next logical step is to add another table for storing the information you need to know about the person browsing your site. One of the columns should be for storing the session identifier from the session table. I'll leave this as an exercise for you.

# Storing Content in a Database

Information stored in a database is not limited to short strings, like the 32-character item name from Listing 17.3. You can create 64K blocks, which are more than enough to store a good web page. The advantage is that pages exist in a very structured environment. They can be identified by a number, and relationships can be drawn between them using these numbers. The disadvantage is that, since the information is now in a database, you can't just lose the file into your favorite editor. You have to balance the costs and benefits; Web sites don't need every piece of content stored in a database.

A situation where it makes a lot of sense to put the content in a database is a Bulletin Board System, or BBS. The system stores messages, which are more than just Web pages. Each message has its own title, creation date, and author. This structure can be conveniently wrapped into a database table. Furthermore, since each message can be given a unique identifier, we can associate messages in a parent-child tree. A user can create a new thread of discussion that spawns many other messages. Messages can be displayed in this hierarchical structure to facilitate browsing.

As with database-related systems, the first step is to create a table. Listing 17.6 creates a table for storing messages. Each message has a title, the name of the person who posted the message, when the message was posted, a parent message, and the body of the text. The parent ID might be zero, in which case we understand the message to be the beginning of a thread. The body doesn't have to be plain text. It can contain HTML. In this way allows users to create their own Web pages using their browsers.

The script in Listing 17.7 has two modes: listing message titles and viewing a single message. If the messageID variable is empty, then a list of every message in the system is organized by thread. This is accomplished by the showMessages function. You might want to turn to Chapter 4, "Functions," specifically the section on recursion. The showMessages function uses recursion to travel to every branch of the tree of messages. It starts by getting a list of all the messages that have no parents. After showing each root-level message, showMessages is called for the thread. This process continues until a message is found with no children. UL tags are used to display the message titles. The indentation allows the user in understanding the hierarchy.

# Listing 17.6 Create Message Table

```
CREATE TABLE Message
(
  ID INT NOT NULL AUTO_INCREMENT,
  Title VARCHAR(64),
  Poster VARCHAR(64),
  Created DATETIME,
  Parent INT,
  Body BLOB,
  PRIMARY KEY(ID)
);
```

Listing 17.7 A Simple BBS

# Core PHP Programming

For the efficiency-minded, this use of recursion is not optimal. Each thread will cause another call to showMessages, which causes another query to the database. There is a way to query the database once and traverse the tree of messages in memory, but I'll leave that as exercise for you.

If a message title is clicked on, the page is reloaded with messageID set. This causes the script to switch over into the mode where a message is displayed. The fields of the message are displayed in a table. If the message contains any HTML, it will be rendered by the browser, because no attempt is made to filter it out. This restriction is applied as part of the code that adds a new message.

Regardless of the two modes, a form is shown for adding a message. If a message is added while the list is shown, the message will be added to the root level. If a message is added while the user is viewing a message, then it will be considered a reply. The new message will be made a child of the viewed message.

This BBS is simple, but the core functionality extends. A more sophisticated solution might involve only authenticated users to add messages, or keeping messages until approved by a moderator. You can use this structure to build any application that manages user-submitted data, such as a guest book. If you are searching for a sophisticated BBS solution, I suggest checking out Brian Moon's Phorum project <http://www.phorum.org/>.

# Database Abstraction Layers

Imagine creating a Web application that uses MySQL and later needing to work with Oracle. All the PHP functions are different, so you'd have to change every one. In addition, MySQL and Oracle each use slightly different SQL, you will probably have to change most of your queries. One solution to this problem is adding an abstraction layer. This separates your business logic—the rules of your application—from the code that interfaces with the database. A single function calls the right function based on the type of database you need to query.

The most popular database abstraction layer is part of the PHP Base Library <http://phpplib.netuse.de/>. This library also contains code for session management. Another abstraction layer is Metabase, at the PHP Classes Repository <http://phpclasses.upperdesign.com/>.

Despite abstraction, incompatibilities between databases continue to offer challenges. MySQL uses a special qualifier for column definitions called AUTO_INCREMENT. It causes a column to be populated automatically with integers in ascending order. In Oracle this functionality can be approximated using a sequence and a trigger. The differences are difficult to reconcile systematically. In 1999, Scott Ambler proposed a solution in his white paper "The Design of a Robust Persistence Layer for Relational Databases" <http://www.ambysoft.com/persistenceLayer.html>. A careful analysis of the problems is explored as well as a detailed design, neither of which I can do justice to in the context of this chapter.

An abstraction layer trades some performance in favor of robustness. Certain unique, high-performance features of each database must be abandoned. The abstraction layer will provide the common set of functionality. But what you gain is independence from any particular database.

# Chapter 18. NETWORK

- HTTP Authentication
- Controlling Browser Cache
- Setting Document Type
- Email with Attachments
- Verifying an Email Address

Most anything you write in PHP will be in the context of a network. It's a language intended primarily to produce HTML documents via the HTTP protocol. PHP allows you to code without worrying about the underlying protocols, but it also allows you to address the protocols directly when necessary. This chapter deals intimately with two important protocols, HTTP and SMTP. These are the protocols for transferring Web documents and I've attempted to describe common problems and provide solutions. This chapter may address a particular problem you face, such as protecting a Page with basic HTTP authentication, but it also illustrates generally how to use HTTP headers and communicate with remote servers.

# HTTP Authentication

If you have any experience with the Web, you're familiar with basic HTTP authentication. You request a page, and a dialog dialog appears asking for username and password. As described in Chapter 8, "I/O Functions," PHP allows you to open URLs with the fopen function. You can even specify a username and password in the URL in the same way you do in Navigator's location box. Authentication is implemented using HTTP headers, and you can protect your PHP pages using the header function.

To protect a page with basic HTTP authentication, you must send two headers. The WWW-Authenticate header tells the browser that a username and password are required. It also specifies a realm that groups pages. A username and password are good for an entire realm, so users don't need to authenticate themselves with each page request. The other header is, which should be HTTP/1.0 401 Unauthorized. Compare this to the usual header, HTTP/1.0 200 OK.

Listing 18.1 is an example of practicing a single page. The HTML to make a page is put into functions because it needs to be printed when the authentication succeeds or fails. The PHP_AUTH_USER and PHP_AUTH_PW variables are created automatically by PHP if a username and password are passed by the browser. The example requires my name, leon, for the username and secret for the password. A more complex scheme might match username and password against a list stored in a file or a database.
