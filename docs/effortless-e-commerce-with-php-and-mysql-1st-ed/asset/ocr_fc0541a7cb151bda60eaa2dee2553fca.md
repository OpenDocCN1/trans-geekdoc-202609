# # LOGGING IN

Logging in to the site is a two-step process: completing the form and validating the submitted values against the database. The login form is not its own page — it's shown in the sidebar to all non-logged-in users, so it cannot use the same single-script approach as in register.php. The question, then, was where the user should end up when they do successfully log in and when they don't. In both cases, I decided they should end up back on the home page; for this reason, the login form gets submitted to index.php. Therefore, the index page needs to be updated with the code for handling the form. Rather than write that code directly into the home page, it's best included as a separate file, just after the database connection but prior to the inclusion of the header file:

```
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    include('./includes/login.php');
}
```

This works because normally index.php will be requested via GET. If it's a POST request, the login form has been submitted, so this script includes the file that will test the login credentials.

# ## Processing the Form

I think it will actually be easier to follow the login process if I talk about the form last, so let's look at the code that handles the login form first. That process needs to:

+   1. Validate the submitted email address and password.
+   2. Compare the submitted values with those in the database.
+   3. Create errors if the values are incorrect.
+   4. Store data in a session if the values are correct.

Here's how all of that works in actual code:

+   1. Create a new PHP script in your text editor or IDE to be named login.inc.php.
+   This will be stored in the **includes** directory.

+   2. Create an empty array for recording errors:

```
<?php
$login_errors = array();
```

This errors array will be used just like $reg_errors in the registration script.

> By including the login processing code, instead of writing it to the index.php file, I'm maintaining better separation of code.

> It's best to give variables in included files unique names so they don't overwrite any variables created by the parent script.