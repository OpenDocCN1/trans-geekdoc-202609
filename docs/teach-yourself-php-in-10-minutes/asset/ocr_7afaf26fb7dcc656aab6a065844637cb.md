Although this information can sometimes be useful when you're debugging, it is a lot of information to store to a log file or table. Furthermore, because the value passed is an array, you need to pass $errocontext through the serialize function in order to store it to a database or text file.

**Context Data** Most likely you are interested in only a small part of the context data passed to your error handler function, so you can have the function extract as much information as is necessary and discard the rest.

# Raising User Errors

You can use the trigger_error function to raise an error on demand. If a custom error handler has been defined, it handles this user error. Otherwise, the default PHP error handler takes the appropriate action.

You should pass an error message string to the Trigger_error function, and you can optionally give an error type constant. If no error type is given, E_USER_NOTICE is used.

For example, to raise a user notice type, you use this statement:

```
trigger_error("Some kind of error happened");
```

The error message displayed will look similar to the following:

```
Notice: Some kind of error happened in /home/chris/error.php on line 3
```

To raise an error with the same message text but as a fatal error, you use this statement instead:

```
trigger_error("Some kind of error happened", E_USER_ERROR);
```

**Error Types** You have to use the E_USER_ERROR and E_USER_WARNING types, not E_ERROR and E_WARNING , for user errors. An E_USER_ERROR type error is still treated as a fatal error, however, and script execution ends immediately when it occurs.