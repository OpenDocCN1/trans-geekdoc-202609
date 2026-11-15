Note
Unfortunately, this does not always work. You should therefore use a cron job or the Windows scheduler to ensure that files with an old modification date are regularly removed from the session directory. Consider an example for Unix/Linux. With the following, all files in the current directory (i.e., they should be in the session directory) that have not been changed for more than 24 minutes are deleted:
find -cmin +24 | xargs rm

# 15.3 Working with Sessions in PHP

In contrast to programming with cookies, working with sessions is very easy. Although there are some functions for session management, most of the time the programming effort is limited to reading and writing the $_SESSION superglobal array.

# 15.3.1 Write Data

Two steps are necessary to store data in the session:

+   - Start session management with session_start(), if not already done (e.g., by setting session.auto_start = 1 in php.ini).
+   - Write the data in $_SESSION.

Note
As cookies may be used, you must start the session management before sending HTML to the client, so call session_start() in the header of the page. The data can be written anywhere on the page, however, as only the session ID is sent to the client. This is already defined when session_start() is called.

The following listing offers a small example.

```
<?php
session_start();
?>
<html>
<head>
<title>Sessions</title>
</head>
<body>
```