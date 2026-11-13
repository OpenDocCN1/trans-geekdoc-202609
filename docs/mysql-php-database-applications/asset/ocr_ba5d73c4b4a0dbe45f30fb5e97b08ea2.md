```
if ($result == FALSE)
{
    // if there was an error executing the query, write out the
    // details to the error log
    $private_error = 'ack! query failed: '
        .'<li>errono='.mysql_errno()
        .'<li>error='.mysql_error()
        .'<li>query='.$query
    ;

    // just in case we were in a transaction
    @mysql_query('rollback');

    // send a generic error message to the user
    user_error('There was an error executing a query. Please '
        .'contact the system administrator.', E_USER_ERROR);
}
```

You use the $private_error variable, which your error-handling function checks for, to store the query that failed and the error message. Then the error-causing query can be written out to the server error log, or right to the screen if you're debugging the application. Meanwhile, the user gets a less revealing (and less frightening) error message.

# Error-handling and debugging functions

Unlikely as it seems, sometimes you make mistakes in your code. Or the database server won't be running because someone forgot to restart it. Errors happen. When they do, it's useful to have a uniform way of responding to them. PHP enables you to set up a function that gets all the errors in your application (those that come from PHP itself--most of them, at least) and errors you raise in your own code when something doesn't seem right. In this section we cover a set of functions that we use throughout the rest of the book to handle errors. The same functions also prepare your code for debugging in a number of ways, without interfering with its normal use.

PHP has its own error-handling functions. And obviously, doing work that someone else is perfectly willing to do for you is not the simplest path you can take. However, setting up your own error handler is worthwhile for a couple of reasons.

+   One, it enables you to exercise a little more control over the user's experience. When something breaks, if you choose, the user sees only a calm report that there seems to be a little problem, while MySQL still writes the scary original error message out to a log file where you can use it to fix whatever's wrong.