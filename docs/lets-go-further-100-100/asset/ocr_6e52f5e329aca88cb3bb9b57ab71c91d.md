# Adding Validation Checks

Let’s move on and create some validation checks for our User struct. Specifically, we want to:

+   - Check that the `Name` field is not the empty string, and the value is less than 500 bytes long.
+   - Check that the `Email` field is not the empty string, and that it matches the regular expression for email addresses that we added in our `validator` package earlier in the book.
+   - If the `Password.plaintext` field is not `nil`, then check that the value is not the empty string and is between 8 and 72 bytes long.
+   - Check that the `Password.hash` field is never `nil`.

**Note:** When creating a bcrypt hash the input is truncated to a maximum of 72 bytes. So, if someone uses a very long password, it means that any bytes after that would effectively be ignored when creating the hash. To avoid any confusion for users, we’ll simply enforce a hard maximum length of 72 bytes on the password in our validation checks. If you don’t want to enforce a maximum length, you could pre-hash the password instead.

Additionally, we’re going to want to use the email and plaintext password validation checks again independently later in the book, so we’ll define those checks in some standalone functions.

Go ahead and update the `internal/data/users.go` file like so: