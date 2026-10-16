# Log the User In

Let's add code to log the user in upon successful validation of their credentials.

Right before the if (empty($_SESSION['user_id']));, add a condition that checks for the user_id session variable being empty and the user submitted the form (Listing 23.19).

# Listing 23.19.

```
```php
1. <h1>Login to Movie Reservations Account</h1>
2. <hr/>
3. <?php
4. if (empty($_SESSION['user_id']) && isset($_POST['login_submission']))
5. {
6. }
7. 
8. if (empty($_SESSION['user_id'])):
9. ?>
10. <form ...>
```
```

Inside this condition (Listing 23.20), grab the user_name and password fields from the $_POST superglobal, and add a condition verifying the user entered values for the fields, otherwise output an error that they need to fill out the form correctly:

# Listing 23.20.

```
```php
1. if (empty($_SESSION['user_id']) && isset($_POST['login_submission']))
2. {
3. // Get user name and password
4. $user_name = $_POST['user_name'];
5. $password = $_POST['password'];
6. 
7. if (!empty($user_name) && !empty($password))
8. {
9. }
10. else
11. {
12. // Output error message
13. echo "<h4><p class='text-danger'>You must enter both a user name
14. and password.</p></h4><hr/>";
15. }
16. }
```
```