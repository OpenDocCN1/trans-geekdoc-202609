# # Is Symfony for Me?

Whether you are a PHP expert or a newcomer to web application programming, you will be able to use symfony. The main factor in deciding whether or not to do so is the size of your project.

If you want to develop a simple website with five to ten pages, limited access to a database, and no obligations to ensuring its performance or providing documentation, then you should stick with PHP alone. You wouldn't gain much from a web application framework, and using object orientation or an MVC model would likely only slow down your development process. As a side note, symfony is not optimized to run efficiently on a shared server where PHP scripts can run only in Common Gateway Interface (CGI) mode.

On the other hand, if you develop more complex web applications, with heavy business logic, PHP alone is not enough. If you plan on maintaining or extending your application in the future, you will need your code to be lightweight, readable, and effective. If you want to use the latest advances in user interaction (like Ajax) in an intuitive way, you can't just write hundreds of lines of JavaScript. If you want to have fun and develop fast, then PHP alone will probably be disappointing. In all these cases, symfony is for you.

And, of course, if you are a professional web developer, you already know all the benefits of web application frameworks, and you need one that is mature, well documented, and has a large community. Search no more, for symfony is your solution.

> > If you would like a visual demonstration, take a look at the screencasts available from the symfony website. You will see how fast and fun it is to develop applications with symfony.

# ## Fundamental Concepts

Before you get started with symfony, you should understand a few basic concepts. Feel free to skip ahead if you already know the meaning of OOP, ORM, RAD, DRY, KISS, TDD, and YAML.

# ### PHP

Symfony is developed in PHP (http://www.php.net/) and dedicated to building web applications with the same language. Therefore, a solid understanding of PHP and object-oriented programming is required to get the most out of the framework. The minimal version of PHP required to run symfony is PHP 5.2.4.

# ### Object-Oriented Programming (OOP)

Object-oriented programming (OOP) will not be explained in this chapter. It needs a whole book itself! Because symfony makes extensive use of the object-oriented mechanisms available as of PHP 5, OOP is a prerequisite to learning symfony.

Wikipedia explains OOP as follows:

> > "The idea behind object-oriented programming is that a computer program may be seen as comprising a collection of individual units, or objects, that act on each other, as opposed to a traditional view in which a program may be seen as a collection of functions, or simply as a list of instructions to the computer."

PHP implements the object-oriented paradigms of class, object, method, inheritance, and much more. Those who are not familiar with these concepts are advised to read the related PHP documentation, available at http://www.php.net/manual/en/language.oop5.basic.php.