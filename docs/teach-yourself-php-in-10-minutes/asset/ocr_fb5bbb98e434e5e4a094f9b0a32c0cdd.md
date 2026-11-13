# PHP Basics

There is a good chance you already know a bit about what PHP can do—that is probably why you have picked up this book. PHP is hugely popular, and rightly so. Even if you haven't come across an existing user singing its praises, you've almost certainly used a website that runs on PHP. This lesson clarifies what PHP does, how it works, and what it is capable of.

PHP is a programming language that was designed for creating dynamic websites. It slots into your web server and processes instructions contained in a web page before that page is sent through to your web browser. Certain elements of the page can therefore be generated on-the-fly so that the page changes each time it is loaded. For instance, you can use PHP to show the current date and time at the top of each page in your site, as you'll see later in this lesson.

The name PHP is a recursive acronym that stands for *PHP: Hypertext Preprocessor*. It began life called PHP/FI, the "FI" part standing for *Forms Interpreter*. Though the name was shortened a while back, one of PHP's most powerful features is how easy it becomes to process data submitted in HTML forms. PHP can also talk to various database systems, giving you the ability to generate a web page based on a SQL query.

For example, you could enter a search keyword into a form field on a web page, query a database with this value, and produce a page of matching results. You will have seen this kind of application many times before, at virtually any online store as well as many websites that do not sell anything, such as search engines.

The PHP language is flexible and fairly forgiving, making it easy to learn even if you have not done any programming in the past. If you already know another language, you will almost certainly find similarities here. PHP looks like a cross between C, Perl, and Java, and if you are familiar with any of these, you will find that you can adapt your existing programming style to PHP with little effort.

# Server-Side Scripting

The most important concept to learn when starting out with PHP is where exactly it fits into the grand scheme of things in a web environment. When you understand this, you will understand what PHP can and cannot do.

The PHP module attaches to your web server, telling it that files with a particular extension should be examined for PHP code. Any PHP code found in the page is executed with any PHP code replaced by the output it produces before the web page is sent to the browser.

**File Extensions** The usual web server configuration is that `somefile.php` will be interpreted by PHP, whereas `somefile.html` will be passed straight through to the web browser, without PHP getting involved.