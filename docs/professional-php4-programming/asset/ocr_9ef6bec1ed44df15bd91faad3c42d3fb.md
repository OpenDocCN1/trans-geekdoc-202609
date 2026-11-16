```
$UserProfileFile . " file");
exit;
}
// Get the username and password
for($i=0; $i < sizeof($fileContent); $i++) {
$line = trim($fileContent[$i]);
list ($name, $value) = split(":", $line);
if ($name == "username") {
$uName = $value;
} else if ($name == "password") {
$uPassword = $value;
}
}
```

Check if the password entered by the user matches the password in the profile file. Note that we had stored only the hash value of the password in the profile file, so, for matching, compare the hash value of the password entered by user with the hash value stored in the user's profile file:

```
if (($uName != $username) ||
($uPassword != crypt($password, CRYPT_STD_DES))) {
sendErrorPage("The username and password you have entered is invalid.
Please try again");
exit;
}
```

If the user is authenticated then create a PHP session:

```
// User authenticated
// Create a session for the User and set authenticated flag
if (!session_start()) {
sendErrorPage("Internal Error: Could not create user session");
exit;
}
```

Register session variable isAuthenticated:

```
if (!session_register("isAuthenticated")) {
sendErrorPage("Internal Error: Could not add isAuthenticated variable
to the user session");
exit;
}
$isAuthenticated=true;
```

Register session variable username:

```
if (!session_register("username")) {
sendErrorPage("Internal Error: Could not add username variable
to the user session");
exit;
}
```