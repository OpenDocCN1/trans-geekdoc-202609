When PHP is installed, the Web server is configured to expect certain file extensions to contain PHP language statements. Often the extension is .php or .phtml, but any extension can be used. When the Web server gets a request for a file with the designated extension, it sends the HTML statements as-is, but PHP statements are processed by the PHP software before they’re sent to the requester.

When PHP language statements are processed, only the output is sent by the Web server to the Web browser. The PHP language statements are not included in the output sent to the browser, so the PHP code is secure and transparent to the user. For instance, in this simple PHP statement:

```
<?php echo "<p>Hello World"; ?>
```

<?php is the PHP opening tag, and ?> is the closing tag. echo is a PHP instruction that tells PHP to output the upcoming text. The PHP software processes the PHP statement and outputs this:

```
<p>Hello World
```

which is a regular HTML statement. This HTML statement is delivered to the user’s browser. The browser interprets the statement as HTML code and displays a Web page with one paragraph — Hello World. The PHP statement is not delivered to the browser, so the user never sees any PHP statements.

PHP and the Web server must work closely together. PHP is not integrated with all Web servers, but it does work with many of the most popular Web servers. PHP is developed as a project of the Apache Software Foundation — consequently, it works best with Apache. PHP also works with Microsoft IIS/PWS, iPlanet (formerly Netscape Enterprise Server), and others.

![](bbox=[0.11, 0.63, 0.2, 0.75])

Although PHP works with several Web servers, it works best with Apache. If you can select or influence the selection of the Web server used in your organization, select Apache. By itself, Apache is a good choice. It is free, open source, stable, and popular. It currently powers over 60 percent of all Web sites, according to the Web server survey at www.netcraft.com. It runs on Windows, Linux, Mac OS, and most flavors of Unix.

# MySQL and PHP, the Perfect Pair

MySQL and PHP are frequently used together. They are often called the dynamic duo. MySQL provides the database part, and PHP provides the application part of your Web database application.