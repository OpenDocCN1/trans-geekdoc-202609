The form variable username holds the value of the user's name:

```
<td><input type="text" name="username"/></td>
</tr>
<tr>
<td> Password: </td>
```

The form variable password holds the value of the user's password:

```
<td><input type="password" name="password"/></td>
</tr>
<tr>
<td></td>
<td><input type="submit" value="Submit"/></td>
</tr>
</table>
</form>
</body>
</html>
```

The following file (login.php) does the user authentication. If the authentication succeeds then it displays the main page, otherwise it displays the error page:

```
<?php
include_once("common.php");
```

Make sure that the username and password values entered by the user are not null:

```
$username = trim($username);
$password = trim($password);
// Authenticate the User
if (($username == "") || ($password == "")) {
sendErrorPage("The username and password you have entered are invalid.
Please try again");
exit;
}
```

Check if the user's profile file exists:

```
$UserProfileFile = $UserProfileDir . $fileSeparator . $username;
// Check if the user profile file exists
if (!file_exists($UserProfileFile)) {
sendErrorPage("The username and password you have entered are invalid.
Please try again");
exit;
}
```

Get the value of username and the password hash value from the profile file:

```
// Read the profile file
$fileContent = file($UserProfileFile);
if ($fileContent == null) {
sendErrorPage("Internal Error: Could not read ".
```