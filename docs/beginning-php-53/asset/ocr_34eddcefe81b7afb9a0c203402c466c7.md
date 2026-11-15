# Part I: Getting Up and Running with PHP

where visitors interact with the page by filling out and sending a form, which is then emailed to the Webmaster.

*PHP stands for PHP: Hypertext Preprocessor, which gives you a good idea of its core purpose: to process information and produce hypertext (HTML) as a result. (Developers love recursive acronyms, and PHP: Hypertext Preprocessor is a good example of one.)*

PHP is a *server-side scripting language*, which means that PHP scripts, or programs, usually run on a Web server. (A good example of a *client-side scripting language* is JavaScript, which commonly runs within a Web browser.) Furthermore, PHP is an *interpreted language* — a PHP script is processed by the PHP engine each time it’s run.

The process of running a PHP script on a Web server looks like this:

+   1. A visitor requests a Web page by clicking a link, or typing the page’s URL into the browser’s address bar. The visitor might also send data to the Web server at the same time, either using a form embedded in a Web page, or via AJAX (Asynchronous JavaScript And XML).
+   
+   2. The Web server recognizes that the requested URL is a PHP script, and instructs the PHP engine to process and run the script.
+   
+   3. The script runs, and when it’s finished it usually sends an HTML page to the Web browser, which the visitor then sees on their screen.

The interesting stuff happens when a PHP script runs. Because PHP is so flexible, a PHP script can carry out any number of interesting tasks, such as:

+   ☐ Reading and processing the contents of a Web form sent by the visitor
+   ☐ Reading, writing, and creating files on the Web server
+   ☐ Working with data in a database stored on the Web server
+   ☐ Grabbing and processing data from other Web sites and feeds
+   ☐ Generating dynamic graphics, such as charts and manipulated photos

And finally, once it’s finished processing, it can send a customized HTML Web page back to the visitor.

In this book you learn how to write scripts to do all of these, and more.

All these great features mean that you can use PHP to create practically any type of dynamic Web application you can dream of. Common examples of PHP scripts include:

+   ☐ Web forums that allow visitors to post messages and discuss topics
+   ☐ Search engines that let people search the contents of a Web site or database
+   ☐ Straw poll scripts that enable visitors to vote in polls and surveys
+   ☐ Content management systems and blogs, which enable Webmasters to create sites easily with minimal technical knowledge
+   ☐ Webmail applications, allowing people to send and receive email using their Web browser
+   ☐ Online stores, allowing shoppers to purchase products and services over the Internet