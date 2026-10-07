# The user log-in form

A typical log-in page asks that the user's name and password should be entered into form text inputs. When the form is submitted, these values can be checked by PHP against a table of authorized users.

The simple HTML page below names the input fields as "username" and "password" and their values are retrieved by the PHP script opposite in variables $username and $password.

```
<html><head><title>Log-In Page</title></head>
<body>
  Please enter your user details to log-in here...

  <form action="authenticate.php" method="post">
    Username:<br>
    <input type="text" name="username">
    <br>
    Password:<br>
    <input type="text" name="password">
    <br>
    <input type="submit" value="Log In">
  </form>

</body></html>
```

![](bbox=[0.168, 0.233, 0.283, 0.355])

The form's action attribute is assigned the name of the script on the opposite form handler.

![](bbox=[0.068, 0.396, 0.148, 0.455])

![](bbox=[0.283, 0.584, 0.963, 0.933])

PHP 5 in easy steps