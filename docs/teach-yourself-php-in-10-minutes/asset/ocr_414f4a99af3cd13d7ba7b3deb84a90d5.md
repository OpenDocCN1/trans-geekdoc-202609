**Submit Buttons** Many modern web browsers submit a form when you press the Enter key when focused on any of the input fields. Even if there is only one submit button on a form, its value is not sent to PHP unless it is actually clicked with the mouse.

# Hidden Inputs

One other type of form input is available, and it can be used to pass values between scripts without their being visible on the web page itself.

The HIDDEN type takes NAME and VALUE attributes, as usual, but it simply acts a placeholder for that value.

The following hidden input is passed to the PHP script when the form is submitted, and $_POST["secret"] contains the value from the form:

```
<INPUT TYPE="HIDDEN" NAME="secret" VALUE="this is a secret">
```

Be aware, however, that HIDDEN attribute inputs are not secure for transmitting passwords and other sensitive data. Although they do not appear on the web page, if you view the page source, you can still see hidden values in the HTML code.