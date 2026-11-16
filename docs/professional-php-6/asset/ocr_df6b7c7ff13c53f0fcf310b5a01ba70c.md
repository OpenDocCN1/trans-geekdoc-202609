# The Constructor

You want your class to be plug-and-play. This enables the programmer to instantiate it once and forget about it.

The constructor does the following:

+   Sets up the database connection. This would normally be handled by another class in a production environment.

+   Tells PHP how to handle session events in the custom class (discussed in further detail shortly)

+   Checks whether an existing session identifier is being offered by the client before PHP has a chance to get its hands on it (which would be the case if the user is in the middle of a session instead of starting a new one). It also performs various checks on age, inactivity, and the consistency of the reported HTTP user agent. If it fails, remove it altogether (and any garbage found) so that PHP can issue a new session from scratch.

+   Sets up the session lifespan parameter (which PHP will obey when issuing the cookie itself)

+   Tells PHP to go ahead and start the session in the normal way

Note the interesting syntax used for session_set_save_handler:

```
session_set_save_handler(
 array(&$this, '_session_open_method'),
 array(&$this, '_session_close_method'),
 array(&$this, '_session_read_method'),
 array(&$this, '_session_write_method'),
 array(&$this, '_session_destroy_method'),
 array(&$this, '_session_gc_method')
 );
```

Although largely undocumented, parameters for this method do not necessarily have to be strings representing procedural function names within current PHP scope.

Instead, you may pass an array of two components. The first is a reference to an instance of a class (in this case, &$this refers to this instance of the class). The second is the name of the method of that class.

# The session_read_method() Handler

Because the first method called by PHP's own session management after a valid session ID has been decided upon (through generation of a brand-new session or the presentation of a still-valid cookie by the Web browser), you use this method to ensure that the session database is kept fully up-to-date.

If the 32-character session identifier supplied by PHP does exist in the database, then the class member variables (logged_in and user_id) are updated against the database record. If it does not, then it is inserted with defaults in place.

# The Impress() Function

This method touches the session to indicate that a new page impression has taken place. Generally, this method would be called on any page that uses the session class directly after it has been instantiated.