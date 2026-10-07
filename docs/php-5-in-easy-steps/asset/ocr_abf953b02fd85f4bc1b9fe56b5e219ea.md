# Setting session preferences

This example demonstrates how to access a user's chosen preference across multiple pages using a session variable called "font". The session ID is passed with the URL links, appending the SID constant, so that the user's preference can be accessed from any page – even if cookies are disabled.

```
<?php session_start();

if ($_POST['font'] != null) {
    $_SESSION['font'] = $_POST['font'];
    header("Location:prefs2.php?" . SID); exit();
}

?>

<html><head><title>Session preferences</title></head>
<body>
<h3>Select Your Preferred Font Family</h3>
<form action="<?php echo $_SERVER['PHP_SELF']; ?>">
<input type="radio" name="font" value="serif">Serif
<input type="radio" name="font" value="sans-serif">Sans-serif
<input type="radio" name="font" value="monospace">Mono
<input type="radio" name="font" value="cursive">Cursor
<input type="radio" name="font" value="fantasy">Fantasy
<br>
<input type="submit" value="Submit">
</form>
</body>
</html>
```

![](bbox=[0.203, 0.235, 0.295, 0.318])

Notice that each of these pages begins by calling the session_start() to enable session variables to be used.

![](bbox=[0.048, 0.385, 0.14, 0.467])

When this form is submitted with one of the radio buttons selected, the session named "font" gets the chosen button's value and the browser is redirected.

| Session preferences |
| File Edit View Go Bookmarks Tools Window Help |
| Select Your Preferred Font Family |
| Serif Sans Mono Cursive Fantasy |
| Submit |
| Done |

![](bbox=[0.048, 0.627, 0.14, 0.708])