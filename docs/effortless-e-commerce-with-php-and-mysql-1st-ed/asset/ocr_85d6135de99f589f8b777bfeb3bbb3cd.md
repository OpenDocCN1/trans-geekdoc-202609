# Creating the Basic Script

To start, you'll create the PHP script, which displays and handles the form. Then you'll integrate the WYSIWYG editor in a separate series of steps.

+   1. Create a new PHP script in your text editor or IDE to be named add_page.php and stored in the Web root directory.

+   2. Include the configuration file:
+   <?php
+   require_once('./includes/config.inc.php');

+   3. Redirect non-administrators:
+   redirect_invalid_user('user_admin');
+   
+   The redirect_invalid_user() function, defined in config.inc.php (in Chapter 4, “User Accounts”), will redirect invalid users to another page. That function’s first argument is the session variable to check for. In this case, it’ll be user_admin, because $_SESSION['user_admin'] is set only if the user is an administrator.

+   4. Include the header file:
+   $page_title = 'Add a Site Content Page';
+   include('./includes/header.html');
+   
+   It's important that the redirection take place before you include the header file.

+   5. Require the database connection:
+   require(MYSQL);

+   6. Create an array for storing errors:
+   $add_page_errors = array();
+   
+   Just like the registration, login, and password forms, this script will use one array for storing any problems with the user-supplied form data.

+   7. Validate the page title:
+   if ($_SERVER['REQUEST_METHOD'] == 'POST') {
+       if (!empty($_POST['title'])) {
+           $st = mysqli_real_escape_string($dbc, strip_tags($_POST['title']));
+       } else {
+           $add_page_errors['title'] = 'Please enter the title!';
+       }
+   }
+   
+   Simply by restricting access to this page to administrative users, there's less risk of it being abused, so the validation routines do not need to be

> tip
> Validation of administrator-generated content does not need to be as strict as public content as long as there is restricted access to the admin pages.