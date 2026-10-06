# Chapter 9: Handling HTML Forms with PHP

Here's a quick example of a form handler script that redirects to a thank-you page:

```
<?php

if (isset($_POST['submitButton'])) {
    // (deal with the submitted fields here)
    header("Location: thanks.html");
    exit;
} else {
    displayForm();
}

function displayForm() {
?>
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/html1/html1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" lang="en">
<head>
    <title>Membership Form</title>
    <link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>

<h1>Membership Form</h1>

<form action="form_handler_redirect.php" method="post">
    <div style="width:30cm;">
        <label for="firstName">First name</label>
        <input type="text" name="firstName" id="firstName" value="" />
        <label for="lastName">Last name</label>
        <input type="text" name="lastName" id="lastName" value="" />
        <div style="clear: both;">
            <input type="submit" name="submitButton" id="submitButton" value="Send Details"
        </div>
    </div>
</form>
</body>
</html>
<?php
?>
```

Notice that the script doesn't output anything to the browser until either the header() function is called, or until the membership form is displayed. Also notice that the script terminates with the exit statement after calling header() to avoid any further output to the browser.