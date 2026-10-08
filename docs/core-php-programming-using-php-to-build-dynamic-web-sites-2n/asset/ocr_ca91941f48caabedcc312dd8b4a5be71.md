```
apache_note("session_id", $session_id);?>
```

# array getallheaders()

The getallheaders function returns every header sent by both the server and the browser. Some of these are PHP script. are then turned into environment variables, which are made available as variables inside your PHP script. Since this function relies on the Apache API, it is available only when you run PHP as an Apache module.

Figure 14-2. getallheaders.