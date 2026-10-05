# Lesson 15: Log Out Inactive Users

**Objective:** In this lesson you will learn how to perform a login procedure and automatically log out inactive users to protect your web pages The basic premise is to start at the Timeout.php page. If the login is successful and you are able to find a matching record in the database the user is redirected to the protected TimeoutSuccess.php page if the user tries to open a protected web page without logging in they will be redirected back to the Login.php page. Finally, although not required, it's also nice to have a Logout.php page to end the user's session.

**Difficulty:** Difficult

**Sample Files:**
LoginTimeout.php
LoginSuccess.php
Logout.php

Page Navigation:

![](bbox=[0.07912000000000001, 0.33635000000000004, 0.415, 0.48635])

**FileMaker API Methods:**
newFindCriterion()
addFindCriterion()
execute()
newFindAllCommand()
getFoundSetCount()

Code:
LoginTimeout.php

Web pages require the use of sessions. PHP is really nice in that it handles the session for you virtually no effort. The only special rule that you have to follow is the code must be BEFORE the HTML tag. I prefer to place it as the very first code on the page. To start a session you only need to use the PHP method session_start(). I'm also going to declare the $_SESSION superglobal named 'login' so I can track the login status on every protected page. To keep it simple, if login = 0 the user is not logged in. If login = 1 the user is logged in. Notice on the login page that I'm starting by declaring that user is NOT logged in. That way if they were on a page where they were logged in they would be automatically logged out to protect your site by default.

```
<?php
session_start();
$_SESSION['login'] =;
?>

<html>
<head>
<title>Login</title>
</head>
<body>
```