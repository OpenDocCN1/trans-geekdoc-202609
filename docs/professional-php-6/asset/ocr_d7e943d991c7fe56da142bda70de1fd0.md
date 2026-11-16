The key to all this is just one PHP function: session_set_save_handler. If you take a look at the PHP manual reference entry for the function, you can see its syntax quite clearly:

```
bool session_set_save_handler ( string open, string close, string read, string write, string destroy, string gc)
```

The idea is simple. You call this function before session_start() is used on any page that employs sessions. The function instructs PHP as to which custom functions to call when certain session behavior takes place (such as when a session is started, finished, read to, written from, or destroyed). There are certain requirements regarding the parameters passed into these methods, as well as the value they must return. These are outlined in some detail on the PHP manual page for session_set_save_handler, but the following sections cover the basics.

# The open() Function

The open() function is called whenever session_start() is called. PHP passes two values: the path in which it thinks the session should be stored if it is to be saved on disk (which can be ignored for the purposes of this discussion) and the cookie name (for example, PHPSESSID) it is using for the session. It needs to return a true value in order for the session to be regarded by PHP as having been successfully created.

# The close() Function

The close() function (not to be confused with the destroy() function) is called at what is effectively the end of the execution of any PHP script that uses session handling. For your purposes, it need do nothing other than return a true value, although it might be nice to close its database connection if it isn’t going to be used anymore. In most production environments, you’ll be using a globally accessible handle to a database that’s already open for other purposes, so you’ll no doubt have code in place to close it down again at the end of the script anyway. In practice, therefore, all this function needs to return is a true value.

# The read() Function

The read() function is used whenever an attempt to retrieve a variable from the $_SESSION hash is made. It takes the session identifier as its sole operand, and expects a serialized representation of $_SESSION in its entirety to be returned. You won’t actually be using this in your class because you’ll be doing your own session variable handling.

# The write() Function

The write() function is used whenever an attempt to change or add to $_SESSION is made. It takes the session identifier, followed by the preserialized representation of $_SESSION, as its two parameters. It expects true to returned if the data is successfully committed. This method is called even if no session variables are registered, and it is the first time the generated session ID is revealed to you.

# The destroy() Function

The destroy() function is called whenever the session_destroy function is used in code. It must return true upon execution.