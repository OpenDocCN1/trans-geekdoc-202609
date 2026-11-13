the data from the MySQL database, then spits it out dynamically as the nicely-formatted HTML page that the browser expects. With PHP, you can write the presentation aspects of your site (the fancy graphics and page layouts) as "templates" in regular HTML. Where the content belongs in those templates, you use some PHP code to connect to the MySQL database and -- using SQL queries just like those you used to create a table of jokes in Chapter 2 -- retrieve and display some content in its place.

Just so it's clear and fresh in your mind, this is what will happen when someone visits a page on our database-driven Web site:

+   - The visitor's Web browser requests the Web page using a standard URL.
+   - The Web server software (Apache, IIS, or whatever) recognizes that the requested file is a PHP script, and so the server interprets the file using its PHP plug-in, before responding to the page request.
+   - Certain PHP commands (which we have yet to learn) connect to the MySQL database and request the content that belongs in the Web page.
+   - The MySQL database responds by sending the requested content to the PHP script.
+   - The PHP script stores the content into one or more PHP variables, and then uses the now-familiar `echo` function to output the content as part of the Web page.
+   - The PHP plug-in finishes up by handing a copy of the HTML it has created to the Web server.
+   - The Web server sends the HTML to the Web browser as it would a plain HTML file, except that instead of coming directly from an HTML file, the page is the output provided by the PHP plug-in.

# Connecting to MySQL with PHP

Before you can get content out of your MySQL database for inclusion in a Web page, you must first know how to establish a connection to MySQL from inside a PHP script. Back in Chapter 2, you used a program called `mysql` that allowed you to make such a connection. PHP has no need of any special program, however; support for connecting to MySQL is built right into the language. The following PHP function call establishes the connection:

```
mysql_connect(address, username, password);
```

Here, `address` is the IP address or hostname of the computer on which the MySQL server software is running ("`localhost`" if it's running on the same