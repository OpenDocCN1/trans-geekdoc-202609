# Creating the Form

The registration form contains six inputs: four text and two password (plus
the submit button). We’ve already defined a function for creating these
inputs, so the first thing the registration form needs to do is include the
form_functions.inc.php file. I did this just before the page-specific content:

```
require('./includes/form_functions.inc.php');
?><h3>Register</h3>
```

The form itself looks like:

```
<form action="register.php" method="post" accept-charset="utf-8"
style="padding-left:100px">
<p><label for="first_name"><strong>First Name</strong></label>
<br /><?php create_form_input('first_name', 'text', $reg_errors); ?>
</p>
<p><label for="last_name"><strong>Last Name</strong></label>
<br /><?php create_form_input('last_name', 'text', $reg_errors); ?>
</p>
<p><label for="username"><strong>Desired Username</strong></label>
</label><br /><?php create_form_input('username', 'text',
$reg_errors); ?> <small>Only letters and numbers are allowed.</small></p>
<p><label for="email"><strong>Email Address</strong></label>
<br /><?php create_form_input('email', 'text', $reg_errors); ?></p>
<p><label for="pass1"><strong>Password</strong></label><br />
<?php create_form_input('pass1', 'password', $reg_errors); ?>
<small>Must be between 6 and 20 characters long, with at least one
lowercase letter, one uppercase letter, and one number.</small></p>
<p><label for="pass2"><strong>Confirm Password</strong></label>
</label><br /><?php create_form_input('pass2', 'password',
$reg_errors); ?></p>
<input type="submit" name="submit_button" value="Next &rarr;"
id="submit_button" class="formbutton" />
</form>
```

You’ll see that with the aid of the create_form_input() function, all the code
for creating each input plus handling all the errors is extremely simple. As
an example, for the first-name input, the function is called indicating that
the input should have name and id values of first_name and should be of
text type. The third argument to the function is an array of errors named
$reg_errors. In a few pages, this array will be added to the registration script,

![](bbox=[0.71, 0.79, 0.77, 0.83])

# tip

In theory, the user's name may be used to greet them personally on the site or in emails sent to them.