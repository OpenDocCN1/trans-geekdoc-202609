
If you cannot find the parse error in a complex script, begin by using the `/* */` comments to render the entire PHP code inert. Then continue to uncomment sections at a time (by moving the opening or closing comment characters) and rerun the script until you deduce what lines are causing the error. Watch how you comment out control structures, though, as the curly braces must continue to be matched in order to avoid parse errors. For example:

```
if (condition) {  

    /* Start comment.  

    Inert code.  

    End comment. */  

}
```

---

**Tip**

To make the results of `print_r()` more readable in the Web browser, wrap it within HTML `<pre>` (preformatted) tags. This one line is one of my favorite debugging tools:

```
echo '<pre>' . print_r($var, 1) . '</pre>';
```

---

### SQL and MySQL Debugging Techniques

The most common SQL errors are caused by the following issues:

*   Unbalanced use of quotation marks or parentheses
*   Unescaped apostrophes in column values
*   Misspelling a column name, table name, or function
*   Ambiguously referring to a column in a join
*   Placing a query's clauses (`WHERE`, `GROUP BY`, `ORDER BY`, `LIMIT`) in the wrong order

Furthermore, when using MySQL you can also run across the following:

*   Unpredictable or inappropriate query results
*   Inability to access the database

Since you'll be running the queries for your dynamic Web sites from PHP, you need a methodology for debugging SQL and MySQL errors within that context (PHP will not report a problem with your SQL).

#### Debugging SQL problems

To decide if you are experiencing a MySQL (or SQL) problem rather than a PHP one, you need a system for finding and fixing the issue. Fortunately, the steps you should take to debug MySQL and SQL problems are easy to define and should be followed without thinking. If you ever have any MySQL or SQL errors to debug, just abide by this sequence of steps.

> **To hammer the point home, this next sequence of steps is probably the most useful debugging technique in this chapter and the entire book. You'll likely need to follow these steps in any PHP-MySQL Web application when you're not getting the results you expected.**

#### To debug your SQL queries

**1.** Print out any applicable queries in your PHP script.

Knowing exactly what query a PHP script is attempting to execute is the most useful first step for solving SQL and MySQL problems.

As you'll see in the next chapter, SQL queries will often be assigned to a variable, particularly when you use PHP to dynamically create them. Using the code `echo $query` (or whatever the query variable is called) in your PHP scripts, you can send to the browser the exact query being run. Sometimes this step alone will help you see what the real problem is.

**2.** Run the query in the mysql client or other tool.

To understand what result a PHP script is receiving, run the same query through a separate interface. In this case the problem is the reference to the `password` column, when the table's column is actually called just `pass`.

The most foolproof method of debugging an SQL or MySQL problem is to run the query used in your PHP scripts through an independent application: the mysql client, phpMyAdmin, or the like. Doing so will give you the same result as the original PHP script receives but without the overhead, hassle, or mystery.

If the independent application returns the expected result but you are still not getting the proper behavior in your PHP script, then you will know that the problem lies within the script itself, not your SQL command or the MySQL database.

**3.** If the problem still isn't evident, rewrite the query in its most basic form, and then keep adding dimensions back in until you discover which clause is causing the problem. Continue to use a third-party interface to MySQL to do this (i.e., put away the PHP script until you've got the SQL query working properly).

Sometimes it's difficult to debug a query because there's too much going on. Like commenting out most of a PHP script, taking a query down to its bare minimum structure and slowly building it back up can be the easiest way to debug complex SQL commands.

#### Debugging access problems

Access-denied error messages are the most common problem beginning developers encounter when using PHP to interact with MySQL. These are among the common solutions:

*   Reload MySQL after altering the privileges so that the changes take effect. Either use the mysqladmin tool or run `FLUSH PRIVILEGES` in the mysql client. You must be logged in as a user with the appropriate permissions to do this (see [Appendix A](#app01.html#app01) for more).
*   Double-check the password used. The error message `Access denied for user: 'user@localhost' (Using password: YES)` frequently indicates that the password is wrong or mistyped. (This is not always the cause but is the first thing to check.)
*   The error message `Can't connect to...` (error number 2002) indicates that MySQL either is not running or is not running on the socket or TCP/IP port tried by the client.

---

**Tip**

MySQL keeps its own error logs, which are very useful in solving MySQL problems (like why MySQL won't even start). MySQL's error log will be located in the MySQL data directory and titled `hostname.err`.

---

---

**Tip**

The MySQL manual is very detailed, containing SQL examples, function references, and the meanings of error codes. Make the manual your friend and turn to it when confusing errors pop up.

---

### Review and Pursue

If you have any problems with the review questions or the pursue prompts, turn to the book's supporting forum ([www.LarryUllman.com/forums/](http://www.LarryUllman.com/forums/)).

#### Review

*   Why must PHP scripts be run through a URL?
*   What version of PHP are you using? What version of MySQL? What version of what Web server application are you using? On what operating system?
*   What debugging steps should you take if the rendered Web page doesn't look right in your Web browser?
*   Do you have `display_errors` enabled on your server? Why is enabling `display_errors` useful on development servers? Why is revealing errors a bad thing on production servers?
*   How does the level of `error_reporting` affect PHP scripts? To what level of `error_reporting` is your PHP server set?
*   What does the `@` operator do?
*   What are the benefits of using your own error-handling function? What impact does the error reporting level have when using your own error-handling function?
*   How can `print` or `echo` be used as debugging tools? Hint: There are many correct answers.
*   What is the method for fixing PHP-SQL-MySQL bugs?

#### Pursue

*   Install the Firebug and Web Developer extensions for Firefox, if you have not already. Install Firefox if you haven't already installed it!
*   Enable `display_errors` on your development server, if you can.
*   If you can, set PHP's level of error reporting to `E_ALL | E_STRICT` on your development server.
*   Check out the PHP manual's page for the `debug_print_backtrace()` function to learn more about it.
*   Consider using a professional-grade IDE that provides built-in debugging tools.

## 9. Using PHP with MySQL

In This Chapter

*   [Modifying the Template](#ch09.html#ch09lev1sec1) [266](#ch09.html#ch09lev1sec1)
*   [Connecting to MySQL](#ch09.html#ch09lev1sec2) [268](#ch09.html#ch09lev1sec2)
*   [Executing Simple Queries](#ch09.html#ch09lev1sec3) [273](#ch09.html#ch09lev1sec3)
*   [Retrieving Query Results](#ch09.html#ch09lev1sec4) [281](#ch09.html#ch09lev1sec4)
*   [Ensuring Secure SQL](#ch09.html#ch09lev1sec5) [285](#ch09.html#ch09lev1sec5)
*   [Counting Returned Records](#ch09.html#ch09lev1sec6) [290](#ch09.html#ch09lev1sec6)
