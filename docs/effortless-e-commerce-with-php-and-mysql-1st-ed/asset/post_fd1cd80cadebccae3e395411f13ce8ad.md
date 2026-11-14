
tion in the string, requires what's called a _zero-width positive lookahead assertion_, represented by the ?=. The positive lookahead makes matches based upon what follows a character. Rather than reading a page of explanation as to how this pattern works beyond that simple definition, you can test it for yourself to confirm that it does and research zero-width positive lookahead assertions online if you're really curious.

- 8. If there are no errors, check the availability of the email address and username:

```
if (empty($reg_errors)) {
    $q = "SELECT email, username FROM users WHERE email='$e' OR 
    \tusername='$u'";
    $r = mysqli_query ($dbc, $q);
    $rows = mysqli_num_rows($r);
    if ($rows == 0) { // No problems!
}
```

If $reg_errors array is still empty, then no errors occurred (because even one error would add an element to this array, making it no longer empty). Next, a query looks for any existing record that has the submitted email address or username. In theory, this query could return up to 2 records (one for the email address and one for the username); if it returns no records, it's safe to proceed.

> **note**
> 
> In truth, I just added the username field to demonstrate how to guarantee both unique email addresses and usernames.

- 9. Add the user to the database:

```
$q = "INSERT INTO users (username, email, pass, first_name,
    \tlast_name, date_expires) VALUES ('$u', '$e', ''
    . create_password_hash($p) . '', '$fn', '$ln', ADDDATE(NOW(),
    \tINTERVAL 1 MONTH))";
$r = mysqli_query ($dbc, $q);
```

The query uses the submitted values to create a new record in the database. Note that for the password value, the get_password_hash() function is called. The user's type does not need to be set because if no value is provided for an ENUM column, the first enumerated value—here, _member_—will be used.

Until PayPal is integrated in Chapter 6, “Using PayPal,” I’m setting the account expiration date to a month from now. Once PayPal has been integrated, the expiration will be set to yesterday. In that case, when PayPal returns an indication of successful payment, the user’s account will be set to expire in a year.

> **note**
> 
> As a security measure, the user's type can only ever be _member_ after going through the registration process. You must go into the database and change a user's type manually in order to create an administrator.

- 10. If the query created one row, thank the new customer and send out an email:

```
if (mysqli_affected_rows($dbc) == 1) {
echo '<h3>Thanks!</h3><p>Thank you for registering! You may now
\ log in and access the site's content.</p>';
$body = "Thank you for registering at <whatever site>. Blah. Blah.
\ Blah.\n\n";
mail($_POST['email'], 'Registration Confirmation', $body, 'From:
\ admin@example.com');
include ('./includes/footer.html');
exit();
}
```

> **tip**
> 
> You could define an email address in the configuration file to be used as the “from” address in messages to customers.

First, a Thanks! page is displayed (Figure 4.9). The next step would be to send them off to PayPal, which we’ll add in Chapter 6. Also, an email can be sent to the user saying whatever you want, although do not include the user’s password in that email. Finally, the footer is included and a call to exit() stops the page. This is necessary so that the registration form isn’t shown again, thereby confusing the user.

![](img/4f47e47c67bd619ac73250f11c9fc7ce_104_0.png)

Figure 4.9

- 11. If the query didn't work, create an error:

```
} else {
 trigger_error('You could not be registered due to a system error. We
\ apologize for any inconvenience.');
}
```

At this point, if the query didn't create a new row, there was a database or query error. In that case, the trigger_error() function is used to generate an error that will be managed by the error handler in the configuration file. On a live, already tested site, this would likely occur only if the database server is down or overloaded.

- 12. If the email address or username is unavailable, create errors:

```
} else {
if ($rows == 2) { // Both are taken.
$reg_errors['email'] = 'This email address has already been
registered. If you have forgotten your password, use the link at
right to have your password sent to you.';
$reg_errors['username'] = 'This username has already been
registered. Please try another.';
}
```

The else clause applies if the SELECT query returns any records. This means that the email address and/or the username have already been registered. Now we need to determine which of the two values is the culprit. If two rows were returned, then both have already been registered. The assumption then is that the same customer already registered (because their email address is in the system) and another customer already has that username (because it's associated with a different email address). The error messages are added to the $reg_errors array, indexed at email and username, so that they'll appear beside the appropriate form input when the form is redisplayed.

- 13. Confirm which item has been registered:

```
} else { // One or both may be taken.
$row = mysqli_fetch_array($r, MYSQLI_NUM);
if (($row[0] == $_POST['email']) && ($row[1] == $_POST['username'])) { // Both match.
$reg_errors['email'] = 'This email address has already been
registered. If you have forgotten your password, use the link at
right to have your password sent to you.';
$reg_errors['username'] = 'This username has already been
registered with this email address. If you have forgotten your
password, use the link at right to have your password sent to
you.';
} elseif ($row[0] == $_POST['email']) { // Email match.
$reg_errors['email'] = 'This email address has already been
registered. If you have forgotten your password, use the link at
right to have your password sent to you.';
} elseif ($row[1] == $_POST['username']) { // Username match.
$reg_errors['username'] = 'This username has already been
registered. Please try another.';
}
} // End of $rows == 2 ELSE.
```

If only one row was returned, then the code needs to figure out if the username matched, the email address matched, or both matched in the same record. Three conditionals test for each possibility, with appropriate error messages assigned (Figures 4.10 and 4.11).

![](img/4f47e47c67bd619ac73250f11c9fc7ce_106_0.png)

![](img/4f47e47c67bd619ac73250f11c9fc7ce_106_1.png)

> **note**
> The character after $rows == is a zero.

- 14. Complete the conditionals:
- } // End of $rows == 0 IF.
- } // End of empty($reg_errors) IF.
- } // End of the main form submission conditional.
- 15. Save and test the registration script.

# ACTIVATING ACCOUNTS

On a site that doesn't require payment, I would normally include an activation process:

- 1. When the user registers, a random code is stored in the users table.
- 2. An email is sent to the registered email address, which includes a link to an activation page on the site. The link passes the user's email address and the specific code to the PHP page: https://www.example.com/activate.php?x=email@example.com&y=CODE
- 3. The PHP page confirms that there is a record in the table with that combination of email address and code, then activates that account (normally by setting the code column to NULL).
- 4. When the user logs in, the query must confirm that the email and password combination is correct, and that the code column in the table has a NULL value.

This is called a “closed-loop” confirmation process and prevents fake registrations. In this Knowledge is Power site, using PayPal will prevent fake registrations, because hackers don't normally spend money in their hack attempts.

# LOGGING IN

Logging in to the site is a two-step process: completing the form and validating the submitted values against the database. The login form is not its own page — it's shown in the sidebar to all non-logged-in users, so it cannot use the same single-script approach as in register.php. The question, then, was where the user should end up when they do successfully log in and when they don't. In both cases, I decided they should end up back on the home page; for this reason, the login form gets submitted to index.php. Therefore, the index page needs to be updated with the code for handling the form. Rather than write that code directly into the home page, it's best included as a separate file, just after the database connection but prior to the inclusion of the header file:

```
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    include('./includes/login.php');
}
```

This works because normally index.php will be requested via GET. If it's a POST request, the login form has been submitted, so this script includes the file that will test the login credentials.

### Processing the Form

I think it will actually be easier to follow the login process if I talk about the form last, so let's look at the code that handles the login form first. That process needs to:

- 1. Validate the submitted email address and password.
- 2. Compare the submitted values with those in the database.
- 3. Create errors if the values are incorrect.
- 4. Store data in a session if the values are correct.

Here's how all of that works in actual code:

- 1. Create a new PHP script in your text editor or IDE to be named login.inc.php.
- This will be stored in the **includes** directory.

- 2. Create an empty array for recording errors:

```
<?php
$login_errors = array();
```

This errors array will be used just like $reg_errors in the registration script.

> By including the login processing code, instead of writing it to the index.php file, I'm maintaining better separation of code.

> It's best to give variables in included files unique names so they don't overwrite any variables created by the parent script.
