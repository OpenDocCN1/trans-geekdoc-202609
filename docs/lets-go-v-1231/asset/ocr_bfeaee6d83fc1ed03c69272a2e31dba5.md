![](bbox=[0.113, 0.066, 0.883, 0.458])

# # Validating the user input

When this form is submitted the data will end up being posted to the `userSignupPost` handler that we made earlier.

The first task of this handler will be to validate the data to make sure that it is sane and sensible before we insert it into the database. Specifically, we want to do four things:

+   1. Check that the provided name, email address and password are not blank.
+   2. Sanity check the format of the email address.
+   3. Ensure that the password is at least 8 characters long.
+   4. Make sure that the email address isn't already in use.

We can cover the first three checks by heading back to our `internal/validator/validator.go` file and creating two helper new methods — `MinChars()` and `Matches()` — along with a regular expression for sanity checking an email address.

Like this: