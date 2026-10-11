
```
import_request_variables("GPC",$prefix);
```

where "GPC" indicates that key-value pairs copied from `$_GET`, `$_POST` and `$_COOKIE` will be registered as local variables. `$prefix` defines a prefix string that are to be added to variable names.

To test this, I turned on the `register_globals` setting in `php.ini` and wrote this sample script, `RequestVariables.php`:

```
<?php
#  RequestVariables.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "<pre>\n";
   print "\nContents of \$_REQUEST:\n";
   foreach ($_REQUEST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nLocal imported variables from the request:\n";
   import_request_variables("GPC","r_");
   print "   \$r_lang = $r_lang\n";
   print "   \$r_search = $r_search\n";
#
   print "\nGlobally imported variables from the request:\n";
   print "   \$lang = $lang\n";
   print "   \$search = $search\n";
   print "</pre>\n";
?>
```

Open this script with `http://localhost/RequestVariables.php?lang=PHP&search`, you will get:

```
Contents of $_REQUEST:
   lang = PHP
   search =

Local imported variables from the request:
   $r_lang = PHP
   $r_search =

Globally imported variables from the request:
   $lang = PHP
   $search =
```

# PHP Tutorials - Herong's Tutorial Examples

## Creating and Managing Sessions in PHP Scripts

This chapter provides tutorial examples and notes about session. Topics include understanding of the session concept; writing scripts to create and use a session; storing data in the current session; managing session IDs as cookies and URL transparent parameters.

> [What Is a Session](#part0108.xhtml)
>
> [How Sessions Are Supported in PHP](#part0109.xhtml)
>
> [SessionPage*.php - Session Test Script Pages](#part0110.xhtml)
>
> [Running Session Test Script Pages](#part0111.xhtml)
>
> [Managing Session IDs without Cookies](#part0112.xhtml)
>
> [Where Is Session Data Stored](#part0113.xhtml)

### Takeaways:

*   A session ID must be passed between HTTP requests and responses to link them into a single sequence.
*   Passing the session ID as a cookie value is more secure.
*   Passing the session ID as a transparent URL variable is less secure, because the session ID will be displayed in the Web page address field.
*   You must call the built-in function, `session_start()`, at the beginning of the PHP script to start a new session, or continue with an existing session.
*   The built-in array, `$_SESSION`, can be used to pass information from one script to another script that shares the same session as the first script.
*   Session data is persisted to the hard disk permanently on the server side.

# PHP Tutorials - Herong's Tutorial Examples

## Creating and Managing Sessions in PHP Scripts

### What Is a Session

This section describes the session concept used by Web server side applications. A Web session represents a series of HTTP requests and responses exchanged between a browser and a Web server. Usually, a cookie is used to carry the ID of a Web session.

#### What Is a Session?

A session is an abstract concept to represent a series of HTTP requests and responses exchanged between a specific Web browser and a specific Web server. The session concept is very useful for Web based applications to pass and share information from one Web page (request) to another Web page (request).

Since the current design of HTTP protocol does not support session concept, all Web server side scripting technologies, including PHP, have designed their own ways to support the session concept. The key design element of session support is about how to identify a session with an ID (identification) and how to maintain the session ID. One common way to maintain the session ID is use the cookie technology. The following diagram shows you how to do this:

```
           Server                Browser
ID created  | <-- Request #1  --- |
            | --- Response #1 --> | ID kept as cookie
            | <-- Request #2  --- | ID send back to server
            | --- Response #2 --> |
            | <-- Request #3  --- | ID send back to server
            | --- Response #3 --> |
            |     ......          |
```

The session concept should be managed by the server. When the first request comes from a browser on a client host, the server should create a new session, and assigns a new session ID. The session ID will be then sent back to the same browser as a cookie. The browser will remember this ID, and send the ID back to the server in subsequent requests. When the server receives a request containing the same session ID, it knows that this request is a continuation of an existing session.

When the server receives a request from a browser on a new client host (request without a session ID), the server should not only create a new session ID, it should also create a new session object associated with the new session ID. This session object should become the storage place for different requests of the same session to store and share information between requests containing the same session ID.

If there is no subsequent request coming back for a long time for a particular session ID, that session should be timed out. After the session has been timed out, if the browser comes back again with the same session ID, the server should give an invalid session error.

# PHP Tutorials - Herong's Tutorial Examples

## Creating and Managing Sessions in PHP Scripts

### How Sessions Are Supported in PHP

This section describes how sessions are supported in PHP. Session IDs are passed as cookies or GET/POST variables. `session_start()` is the built-in function to start a session. `$_SESSION` is the built-in array to manage session data.

PHP supports Web sessions with following main elements in the configuration file, `php.ini`:

1.  `session.use_cookies = 1/0` - A setting to determine if the session ID should be stored and managed as a cookie.
    *   `session.use_cookies = 1` (the default setting) - Managing the session ID as a cookie. The session ID is stored in a cookie with a default name of "PHPSESSID". This "PHPSESSID" cookie will be automatically inserted into HTTP responses and retrieved from HTTP requests by the PHP engine.
    *   `session.use_cookies = 0` - Stop storing the session ID as a cookie.

2.  `session.use_trans_sid = 1/0` - A setting in the configuration file, `php.ini`, to control if the session ID should be stored and managed transparently as a parameter in the URL.
    *   `session.use_trans_sid = 1` - Managing the session ID as an extra transparent parameter in the URL. The extra URL parameter contains the session ID value with a default name of "PHPSESSID". This "PHPSESSID" parameter will be automatically inserted into all links in the HTTP response, and retrieved from HTTP requests by the PHP engine.
    *   `session.use_trans_sid = 0` (the default setting) - Stop storing the session ID as a URL transparent parameter.

3.  `session.save_handler = files/mm/user` - A setting in the configuration file, `php.ini`, to control how session data should be stored.
    *   `session.save_handler = files` (the default setting) - Storing session data as files in a directory defined in the `session.save_path = "/tmp"` setting.
    *   `session.save_handler = mm` - Storing session data in shared memory.
    *   `session.save_handler = user` - Storing session data through user-defined functions.

4.  `session_start()` - A built-in function to create a new session or resume an existing session. When `session_start()` is called, the PHP engine will check the current HTTP request to see if an existing session ID is included or not.
    *   If no session ID is found, the PHP engine will create a new session with a new session ID.
    *   If a session ID is found, the PHP engine will restore the session identified by this session ID. If the restored session has been timed out, an error will be issued.
