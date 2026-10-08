([userid] => testuser
[password] => password)

```
<!-- BEGIN SESSION VARS -->
<!-- Array
(
<!-- BEGIN COOKIE VARS -->
<!-- Array
(
  [PHPSESSID] => b2b5f56fad986dd73af33470f3c1865
)
)
<!-- END VARIABLE DUMP -->
```

You can see that it displays the POST variables from the login form on the previous page: userid and password. It also shows the session variable used to link the user's name in: valid_user. As discussed in Chapter 22, PHP uses a cookie to link session variables to particular users. The script echoes the pseudo-random number, PHPSESSID, which is stored in that cookie to identify a particular user.

# Error Reporting Levels

PHP allows you to set how fussy it is with errors. You can modify what types of events generate messages. By default, PHP reports all other than notices.
The error reporting level is assigned using a set of predefined constants, shown in Table 26.1.

Table 26.1 Error Reporting Constants

| Value | Name | Meaning |
| 1 | E_ERROR | Report fatal errors at runtime |
| 2 | E_WARNING | Report nonfatal errors at runtime |
| 4 | E_PARSE | Report parse errors |
| 8 | E_NOTICE | Report notices, notifications that something you have done might be an error |
| 16 | E_CORE_ERROR | Report failures in the startup of the PHP engine |
| 32 | E_CORE_WARNING | Report nonfatal failures during the startup of the PHP engine |
| 64 | E_COMPILE_ERROR | Report errors in compilation |