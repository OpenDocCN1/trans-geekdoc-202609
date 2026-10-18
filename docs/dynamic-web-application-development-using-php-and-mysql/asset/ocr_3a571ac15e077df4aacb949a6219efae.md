The confirm dialog is similar to the alert in that it will contain some type of message. However it has two buttons, ‘OK’ and ‘Cancel’. If the user clicks ‘OK’, the box returns true. If the user clicks ‘Cancel’, the box returns false.

```
confirm("message");
```

Unlike the other two dialogs, the prompt dialog asks the user to enter a value. As well as a text entry field, it contains ‘OK’ and ‘Cancel’ buttons. If the user clicks ‘OK’ the box returns the input value, but if the user clicks ‘Cancel’ the box returns null. A null value in JavaScript means that the variable has no value.

```
var returnValue=prompt("prompt text", "default value");
```

Here is a simple JavaScript function that creates all three of these dialog types in turn. When the function is called, the dialogs appear one after the other.

```
// File: showdialogs.js
function showDialogs()
{
  alert("This is an alert");
  confirm("This message wants confirmation");
  prompt("Please enter something in the text area", "I'm a default");
}
```

Here is an XHTML page that calls this function when it loads:

```
<?xml version="1.0"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<meta http-equiv="Content-Script-Type" content="text/javascript"/>
<title>JavaScript Dialogs</title>
<script type="text/javascript" src="showdialogs.js">
</script>
</head>
<body onload="showDialogs()">
<!-- File: example7-9.htm -->
</body>
</html>
```

Figure 7.9 shows how the three dialogs look when displayed by the Mozilla Firefox 2 browser. They look a little different in other browsers but the content and buttons are very much the same.

# Using dialogs in validation routines

All three of these dialog types could be used in validation routines. However, perhaps the simplest approach is to use an alert to inform the user if there errors in the form data.

Here is a complete ‘validate’ function, using a form parameter and an alert. The function checks if either the username or password text fields in the login form are empty. In each