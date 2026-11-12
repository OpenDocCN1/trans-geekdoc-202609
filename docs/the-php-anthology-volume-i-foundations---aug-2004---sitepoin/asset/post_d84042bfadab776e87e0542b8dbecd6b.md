
```
Array
(
    [0] => forums
    [1] => discussion
    [2] => php
)
```

In terms of your code, you need to have some kind of decision logic that passes the handling of each variable to code that knows what to do with it. In this example,

- 1. From the “root” PHP script of your site (e.g. index.php), examine path variable 0 to find out which code to pass this job to. In this case, it’s the forums code.
- 2. From the forums code, examine path variable 1 to find out which code within the forum application should deal with this. In this case, it’s the discussion code.
- 3. In the discussion code, examine path variable 2 to find out which discussion should be displayed.

In each case, the code delegates the work to some other code until it reaches the point where it’s time to do some real work (e.g. the discussion code performs a database query to select all threads in the requested discussion, and displays them as an HTML table).

How you actually handle the delegation of work is a matter of preference and experience. You might simply use an include statement to load the correct PHP script each time a decision is made. More complex, but often more flexible approaches use object orientation, where the decision-making process is based on the selection of the correct class to deal with each step.

Either way, this takes your Website down the road to becoming a framework—a structured environment to which you add the code for your applications, which the framework executes on demand. While considering how you’ll do this, it’s worth investigating some of the other PHP frameworks available, such as eZ publish[16], Phrame[17] and Ambivalence[18] for further insight into the design issues you’ll need to take into account.

- [16] http://developer.ez.no/
- [17] http://phrame.sourceforge.net/
- [18] http://amb.sourceforge.net/

## Further Reading

- Object Oriented PHP: Paging Result Sets: http://www.sitepoint.com/article/662

This article provides a basic introduction to object oriented programming and uses in its final example a paging result set similar to the one in this chapter.

- Building an Extensible Menu Class: http://www.devshed.com/Server_Side/PHP/ExtensibleMenuClass/

This article presents an alternative view of building a menu class that uses MySQL to do most of the work, rather than PHP.

- Storing Hierarchical Data in a Database: http://www.sitepoint.com/article/1105

A detailed look at the adjacency model and nest set approaches is presented in this article.

- PEAR::Tree Tutorial: http://www.phpkitchen.com/article.php?story=20030427152620585

See this article for an explanation of the use of PEAR::Tree, which provides an API for dealing with nested set data structures.

- Search Engine-Friendly URLs: http://www.sitepoint.com/article/485

This article explains the ins and outs of search engine friendly URLs.

- Apache's ForceType directive: http://www.devarticles.com/art/1/143/2

This tutorial provides more detail on how to use the ForceType directive.

- mod_rewrite: A Beginner's Guide to URL Rewriting: http://www.sitepoint.com/article/910

Apache's mod_rewrite is examined here.

- eZ Publish: PHP's Killer App: http://www.sitepoint.com/article/917

This three part series examines the eZ publish framework from scratch.

## 10 Error Handling

In Chapter 1, I introduced PHP’s in-built error handling mechanism, and we discussed that errors in general are usually broken into four basic types:

- **Syntax Errors**: The script fails to obey the basic language rules of PHP and cannot be executed.
- **Semantic Errors**: In executing the code, PHP encountered a situation that is illegal in terms of the “grammar” of PHP, such as passing a string to a function that expects an array.
- **Environment Errors**: A problem has been encountered in the environment used by the PHP script during execution, such as the MySQL server being unavailable.
- **Logic Errors**: The script executes correctly as far as the PHP engine is concerned, but does not do what the designer expected.

In this chapter, we’ll look at the mechanisms PHP provides to extend the native error reporting mechanism and give you greater control over how errors are handled. The benefit of these mechanisms is generally realized in dealing with environment errors; the mechanisms provide your code the opportunity to gracefully exit execution, and allow you to hide errors from your site’s visitors while receiving private notifications of the errors.

## Error Handling in PHP 5

The soon-to-be-released PHP 5 will include a new error handling mechanism that should radically improve the way errors are handled in PHP 4. PHP 5 will provide a try-catch control structure that’s common to languages such as Java. It’s worth keeping in mind the fact that this change is on the horizon, so that you can easily modify your code when the time comes. Those modifications might simply involve a search and replace operation for all instances where you used trigger_error. Or perhaps they’ll be more elaborate, passing all calls to trigger_error through a single function you’ve defined yourself, which will allow you to switch to the new mechanism for generating errors simply by modifying that function.

## How do I implement a custom error handler with PHP?

By now you’re probably well acquainted with PHP’s native error reporting; possibly you’re acquainted with it more closely than you’d like, thanks to those inevitable syntax errors. PHP 4 provides for generating and handling errors additional mechanisms that you can control; these are described in the PHP Manual[1]. Being able to generate your own error messages allows you to add additional error reporting to your application, helping you track down problems and bugs after they occur. Meanwhile, the ability to create your own error handler allows you to log error messages and control the output delivered to your site’s visitors.

## Error Levels

Once a PHP script has been parsed to rule out syntax errors, PHP can generate three categories of error while running a script:

- Errors fatal errors that result in PHP halting further execution of the script
- Warnings general environment errors from which PHP can recover
- **Notices** potential problems that PHP doesn’t really care about, but which may reflect bugs in your code

An understanding of this categorization will prove useful when it comes to generating your own errors.

The **error reporting level** determines which of the above categories of error will cause PHP to display an error message. The default error reporting level for a PHP installation is set by the `error_reporting` option in `php.ini`. For example, setting it to `E_ALL` tells PHP to report all error types:

```
error_reporting = E_ALL
```

Except for this special case, telling PHP to use a particular error level will see PHP report errors from that level only; the levels must be **combined** using **bitwise operators** if you want PHP to report multiple error types. For example, to report all error types *except* notices, the setting is often configured as follows:

```
error_reporting = E_ALL & ~E_NOTICE
```

You can determine the current error reporting level within a PHP script using the `error_reporting` function:

```
<?php
echo error_reporting();
?>
```

This will display the current level as an integer (e.g. 2047 for `E_ALL`). You can also set the error level using the `error_reporting` function. For example:

```
<?php
error_reporting(E_ALL ^ E_NOTICE); // Report all except notices
echo error_reporting(); // Displays 2039?>
```

In the above example, we tell PHP to report all errors except notices, using the bitwise XOR operator, `^`, to subtract the `E_NOTICE` error level from the `E_ALL` error level.

Some other illustrative examples follow:

`File: 3.php`

```php
<?php
error_reporting(E_ALL); // Report all errors
error_reporting(2047); // Report all errors
error_reporting(0); // Turn off error reporting
?>
```

Generally, you won't need to change the error levels beyond the examples above.

> **Which Error Reporting Level?**
> 
> When developing your code, always set the error level to its highest value, E_ALL (or 2047). This will inform you of all errors. In particular, it'll display notices that help you find uninitialized variables—the source of many a logic error. This error level will also ensure maximum portability for others using your code, who may prefer to run PHP at this level and not see any error messages generated by your work.
> 
> The best way to set this error level is in php.ini, using the error_reporting setting. If this is not possible, the next best solution is to use a .htaccess file with the following command:
> 
> ```
> php_value error_reporting 2047
> ```
> 
> However you do it, it's important to apply the setting globally to all your code.
> 
> Remember, too, that the simple fact that you've told PHP not to report certain errors doesn't mean they aren't happening! Be careful when developing code and use full error reporting.

An important thing to note is that the error reporting level applies to the in-built PHP error handler, not to error handlers you define yourself (which we'll be looking at shortly). In other words, you can switch off error reporting as far as the default PHP error reporting mechanism is concerned, while still catching errors with an error handler you've defined yourself.

One more mechanism that is available for controlling error behavior is the error suppression operator, @, which can be used to suppress error messages generated by PHP functions and expressions. For example:

`File: 4.php`

```php
<?php
// Use error reporting operator
if (!@mysql_connect('localhost', 'wronguser', 'wrongpassword')) {
    echo 'Error connecting to MySQL Server: ' . mysql_error();
}
```
