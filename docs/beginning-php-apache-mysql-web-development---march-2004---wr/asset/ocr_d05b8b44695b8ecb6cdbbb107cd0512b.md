# Using Logins, Profiles, and Personalization

```
$_POST['hobbies']) echo ' selected';
<option value="Computers">?php if (in_array('Computers',
$_POST['hobbies']) echo ' selected';??>Computers</option>
<option value="Other Than Listed">?php if (in_array('Other Than Listed',
$_POST['hobbies']) echo ' selected';??>Other Than Listed</option>
</select><br>
<input type="submit" name="submit" value="Register">&amp; <input
type="reset" value="Clear"><br>
<?php
</form>
n}
else
?>
Welcome to the registration page!
<form action="register.php" method="post">
Username: <input type="text" name="username"><br>
Email: <input type="text" name="email"><br>
First Name: <input type="text" name="first_name"><br>
Last Name: <input type="text" name="last_name"><br>
city: <input type="text" name="city"><br>
State: <input type="text" name="state"><br>
Hobbies: (choose at least one)
<select name="hobbies[]" size="10" multiple>
<option value="Golfing">Golfing</option>
<option value="Hunting">Hunting</option>
<option value="Reading">Reading</option>
<option value="Dancing">Dancing</option>
<option value="Internet">Internet</option>
<option value="Flying">Flying</option>
<option value="Traveling">Traveling</option>
<option value="Exercising">Exercising</option>
<option value="Computers">Computers</option>
<option value="Other Than Listed">Other Than Listed</option>
</select><br>
<input type="submit" name="submit" value="Register">&amp; <input type="reset"
value="Clear"><n</form>
<?php
}
?>
<body>
</html>
```

Let's recap what you've done:

+   - You have an index page that checks whether or not a user is logged in.
- Based on that check, it allows the user to log in or register allow access to their personal information.