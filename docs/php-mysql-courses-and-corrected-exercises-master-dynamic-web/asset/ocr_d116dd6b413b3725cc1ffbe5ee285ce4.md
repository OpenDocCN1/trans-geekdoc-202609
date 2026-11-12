```
<input type="text" id="username" name="username">
</div>
<br>
<div>
<label for="password">Password:</label>
<input type="password" id="password" name="password">
</div>
<div>
<input type="submit" value="Login">
</div>
</form>
</body>
</html>
```

This form sends the data entered by the user to a verification script named "verification.php" via the POST method. It contains two fields: one for the username ("text" type) and one for the password ("password" type).

The "verification.php" file will be responsible for verifying the information provided by the user to authorize or deny access to the member area. But for the purposes of this example, our aim is to explain how sessions work, so that data can be passed on from page to page.

To put our example into practice, we create a file named "verification.php" where we define a basic