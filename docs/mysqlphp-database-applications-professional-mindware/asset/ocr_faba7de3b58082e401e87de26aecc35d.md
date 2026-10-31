When accessed the first time, this page will start a session, and depending on the configuration either the script will send a cookie or a session id will be appended to relative links. The session_register command tells PHP to search the session file for the variable $mystring. If it exists, it will become available as a global, or if you wish you can access it through the $HTTP_SESSION_VARS array. After the page is processed the most current value for the registered variables is written to the session file. So if you have another page that contains the following code:

```
<?
session_start();
session_register("mystring");

echo $mystring;
?>
```

It will print “testing for a string”.

The fact is that the session_start() function isn’t really necessary; if you have a session_register() in your code, PHP is smart enough to start the session for you.

Note that although in the preceding code the variable is a simple string, you are by no means limited to a string. Simple arrays, complex arrays, and objects are all viable session variables.

Here are some other session functions that you may find useful.

# SESSION_DESTROY()

This function kills a session and all of the variables associated with it.

# SESSION_UNREGISTER()

This function erases the value of a variable in the session file.

# SESSION_SET_SAVE_HANDLER()

This interesting function allows you to set your own methods for storing, retrieving, and writing your own session handlers.

```
void session_set_save_handler (string open, string close, string read, string write, string destroy, string gc)
```

For a good deal of the time, the file-based session management in PHP will be fine. However, there are a couple of circumstances in which it may not suit you. If you happen to be working in a clustered environment, where several machines are serving the same site, writing to the local filesystem really won’t work. Similarly, your SSL-enabled Apache installation may sit on a different box than your main server.