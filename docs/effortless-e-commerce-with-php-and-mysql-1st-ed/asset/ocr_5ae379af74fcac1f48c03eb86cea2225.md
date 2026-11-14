![](bbox=[0.106, 0.116, 0.609, 0.296])

Figure 4.16

+   9. Print a message and wrap up:

```
echo '<h3>Your password has been changed.</h3><p>You will receive
\ the new, temporary password via email. Once you have logged in
\ with this new password, you may change it by clicking on the "Change
\ Password" link.</p>';
include('./includes/footer.html');
exit();
```

As with any process, you want to indicate to the user what should happen next (Figure 4.17). The exit() line terminates the script so that the form is not shown again.

![](bbox=[0.106, 0.555, 0.621, 0.615])

Figure 4.17

+   10. If the database update couldn't run, generate an error:

```
} else { // If it did not run OK.
    trigger_error('Your password could not be changed due to a system
   \ error. We apologize for any inconvenience.');
}
```

This else clause applies if the database query didn't work, indicating a system error.

+   11. Complete the processing section of the script:

```
} // End of $uid IF.
} // End of the main Submit conditional.
```

+   12. Create the form: