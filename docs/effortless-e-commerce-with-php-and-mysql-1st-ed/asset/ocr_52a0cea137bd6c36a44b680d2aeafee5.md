Just before the email address label, you'll see this code:

```
<?php if (array_key_exists('login', $login_errors)) {
echo '<span class="error">' . $login_errors['login'] . '</span><br />';
} ?>
```

By default, all errors are reported via the create_form_input() function. However, this form is a bit different in that login.inc.php could create an error (that is, an element in the $login_errors array) not associated with a particular form input. That error occurs when both fields are properly filled out but the values don't, together, match a record in the database. In that case, the $login_errors['login'] element is assigned an error message. Therefore, the form first checks if that array element exists in $login_errors, in which case the error message will be displayed just before the two inputs (Figure 4.12). Other error messages are associated with the offending form input (Figure 4.13).

![](bbox=[0.067, 0.406, 0.353, 0.582])

Figure 4.12

![](bbox=[0.383, 0.406, 0.683, 0.582])

Figure 4.13

> You could also change the header file so that the register tab is not shown to users that are logged in.

After you've done all this, you can now test the login process.

# LOGGING OUT

Logging out is the simplest part of the process. The logout.php page starts off as a standard script, including the configuration file, the header, the MySQL connection, and the footer. Only logged-in users should be able to access this page, though, so a call to redirect_invalid_user() is included just after the configuration file is defined.

To wipe out the session, three steps are required. First, clear out the $_SESSION array that represents the variables available to this script:

```
$_SESSION = array();
```