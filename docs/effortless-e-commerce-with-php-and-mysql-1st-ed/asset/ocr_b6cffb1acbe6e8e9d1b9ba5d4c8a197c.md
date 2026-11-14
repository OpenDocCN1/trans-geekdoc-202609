so that it's already defined prior to this point. This same function is called for all six inputs, changing the arguments accordingly.

For the username and passwords, note that that the user is being presented with a clear indication of what's expected of them. It drives me crazy when sites complain that I did not complete a form properly (such as by not using at least one number or capital letter in a password) when no such instructions were included.

# Processing the Form

The bulk of the register.php script is the validation of the form and the insertion of the new record into the database. That part of the script is over 100 lines of code, so I'll walk through it more deliberately. Figure 4.8 shows a flowchart of how this entire page will be used and may help you understand what's going on with the code. Note that all the code in the steps that follow gets placed after the MySQL connection script is included—because you'll need access to the database—but before the form_functions.inc.php include and the page-specific content. Again, see the downloadable scripts if you're confused about the order of things.

![](bbox=[0.32, 0.5, 0.93, 0.78])

Figure 4.8

+   1. Create an empty array for storing errors:

```
$reg_errors = array();
```

This array will be used to store any errors that occur during the validation process. Normally, I might include this line within the section that begins the validation process (see Step 2), but because the create_form_input()