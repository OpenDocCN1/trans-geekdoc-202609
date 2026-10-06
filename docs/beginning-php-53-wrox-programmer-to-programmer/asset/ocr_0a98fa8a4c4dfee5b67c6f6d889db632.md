# Chapter 10: Preserving State With Query Strings

| Directive | Description |
| --- | --- |
| session.cookie_lifetime | How long the cookie should last for (in seconds). The default is zero, which expires the cookie when the browser is closed. Set it to a long value (for example, 1 year) to make a permanent session for storing data such as user preferences. Alternatively, to increase security for sessions such as long sessions, set it to a short value, such as 20 minutes, the session will time out if the user waits more than 20 minutes between page requests. |
| session.cookie_path | The path field for the session cookie. Defaults to '/' (the entire site). Set it to a subdirectory of your Web site if you want to limit the session to scripts inside that folder. |
| session.cookie_domain | The domain field for the session cookie. Defaults to '** (the current server). Change this if you want the session to be available to more than one host in the same domain. |
| session.cookie_httponly | The HttpOnly field for the session cookie. Defaults to false. Change this to true if you want to prevent JavaScript from accessing the session cookie. |
| session.auto_start | Defaults to false. Change it to true and PHP automatically starts a session the moment your script starts, saving you from calling session_start(). Be careful; if set to true you cannot store objects in sessions (because your classes won't be defined at the time the session data is loaded). |

You can alter these directives directly in your php.ini file, if you have access to it (see Appendix B for details), or you can set them on a per-script basis using the ini_set() PHP function:

```
ini_set("session.cookie_lifetime", 1200); // Set session timeout to 20 minutes
```

As well as altering session behavior, you can write your own custom code to store the session data on the server. For example, instead of letting PHP store the data in temporary files, you might prefer to store it in a database. How to do this out of the scope of this book, you can find out more by reading http://www.php.net/manual/en/function.session-set-handler.php.

291