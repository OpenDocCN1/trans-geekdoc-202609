+   8. Complete the script:
+   } // End of $login_errors IF.
+   As with all other scripts that will be included by other scripts, I'm omitting the closing PHP tag.
+   
+   9. Save the file.

# Creating the Form

The last script to discuss, login_form.inc.php, is actually the first step in the process. It needs to do just two things: present a form and report any errors that occurred when the form was submitted. The form contains two inputs: one for the email address and one for the password. Both are created using the same create_form_input() function, which means that the form_functions.inc.php script must be included. The function needs to take an array of errors — $login_errors — as its third argument. That array is created in login.inc.php. However, if the user is just loading the login form for the first time, $login_errors won't exist, so this script should initialize an empty array in that case. As a second complication, on the register.php and forgot_password.php pages, the form_functions.inc.php script will already have been included, making require_once() the appropriate way to include that file here.

Here's the complete login_form.inc.php:

# includes/login_form.inc.php

```
1 <?php
2 if (!isset($login_errors)) $login_errors = array();
3 require_once ('. ./includes/form_functions.inc.php');
4 ?><div class="title">
5 <h4>Login</h4>
6 </div>
7 <form action="index.php" method="post" accept-charset="utf-8">
8 <?php if (array_key_exists('login', $login_errors)) {
9 echo '<span class="error">'. $login_errors['login'] .'</span><br />';
10 }?><label for="email"><strong>Email Address</strong></label>
   <br /> <?php create_form_input('email', 'text', $login_errors); ?>
   <br /> <label for="pass"><strong>Password</strong></label>
   <?php create_form_input('pass', 'password', $login_errors); ?>
   <a href="forgot_password.php" align="right">Forgot?</a><br />
   <input type="submit" value="Login &rarr;"/></p>
11 </form>
```