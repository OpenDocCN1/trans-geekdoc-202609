```
Username: <input type="text" name="user" /><br />
Password: <input type="password" name="password" /><br />
<input type="submit" value="Login" />
</form>
</body>
</html>
```

# Listing 32.1 A Bad Login Page ("login.php")

This page checks the specified user name and password and displays a corresponding message if they match (as you can see, the example is greatly simplified). But if you look closely, you will discover a major design error in the code. The programmer has assumed that the $loggedIn variable has not been initialized and therefore has the value false. But if register_globals was set to On, then the access protection could be overridden easily. By calling up the page with login.php?loggedIn=1, a $loggedIn vari- able with the value 1 would automatically be created and the user would be authenticated.

This—admittedly somewhat contrived—example was one of the reasons for disabling register_globals by default from PHP 4.2 on. This decision was not uncontroversial; PHP inventor Rasmus Lerdorf in particular was actually against it. Much worse, how- ever, was the fact that even specialist magazines with a good reputation and renowned publishers continued to publish code for months, sometimes even years, in which this change was apparently not taken into account. These embarrassing incidents have once again shown that it is essential to keep in touch with the technology you are writing about. By the way: In current PHP versions, register_globals no longer exists at all. Our grief is limited.

> **Note**
> 
> It should not go unmentioned that Listing 32.1 could be secured. To do so, either the
> $loggedIn variable is initialized correctly:
> 
> $loggedIn = false;
> 
> Or an else branch is added to the if query:
> 
> if (isset($_POST["user"]) &&
>     isset($_POST["password"]) &&
>     $_POST["user"] == "Christian" &&
>     $_POST["password"] == "*secret*") {
>     $loggedIn = true;
> } else {
>     $loggedIn = false;
> }