
## Listing 23.3.

```
<body>
<div class="card">
  <div class="card-body">
    <h1>Sign up for a Movie Reservations Account</h1>
    <hr>
    <form ...>
      ...
    </form>
  </div>
</div>
<script>
// JavaScript for disabling form submissions if there are invalid fields
(function () {
'use strict';
window.addEventListener('load', function () {
// Fetch all the forms we want to apply custom Bootstrap validation styles to
var forms = document.getElementsByClassName('needs-validation');
// Loop over them and prevent submission
var validation = Array.prototype.filter.call(forms, function (form) {
  form.addEventListener('submit', function (event) {
    if (form.checkValidity() === false) {
      event.preventDefault();
      event.stopPropagation();
    }
    form.classList.add('was-validated');
  }, false);
});
}, false);
})();
</script>
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"
integrity="sha384-DfXdz2htPH0lsSsSsNCTpuJ/zy4C+OGpamoFvy38MVBN..."
crossorigin="anonymous"></script>
```

Also, notice I added a checkbox to show the password as you type it in as in Figure 23.4. Figure 23.5 shows it when checked.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_349_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_349_1.png)

## 23. ADDING USER LOGINS

The checkbox field is set to call a JavaScript function called togglePassword() when the onclick event occurs:

```
<input type="checkbox" class="form-check-input" id="show_password_check" onclick="togglePassword()">
```

Add JavaScript function togglePassword() from Listing 23.4 below the form field validation function we just added before the closing </script> tag.

```
// Disable form submissions if there are invalid fields
(function () {
    ...
})();

// Toggles between showing and hiding the entered password
function togglePassword() {
    var password_entry = document.getElementById("password");
    if (password_entry.type === "password") {
        password_entry.type = "text";
    } else {
        password_entry.type = "password";
    }
}
```

When the user submits the form, we'll validate the credentials and either create an account or redirect them to correct their entries. Therefore, we need to add conditional logic to ensure the form only displays when we want it to.

Right before the form, add the Boolean variable (Listing 23.5) set to display a form, and move the form within an if() statement that checks this condition.

```
<h1>Sign up for a Movie Reservations Account</h1>
<hr />
<?php
$show_sign_up_form = true;
if ($show_sign_up_form):
?>
<form ...>
...
</form>
<?php
endif;
?>
```

### Create a Signup.php script

### Create a New User

Let’s add code to create a new user in the Movie database when successfully signing up a new user. Right after setting `$show_sign_up_form` to true, add a condition for when the user submits the form:

```php
<?php
    $show_sign_up_form = true;

    if (isset($_POST['signup_submission']))
    {
    }
```
```

Inside this condition, grab the user_name and password fields from the $_POST superglobal, and add a condition verifying the user entered values for the fields, otherwise output and error that they need to fill out the form correctly as in Listing 23.6

## Listing 23.6.

```php
if (isset($_POST['signup_submission']))
{
    // Get user name and password
    $user_name = $_POST['user_name'];
    $password = $_POST['password'];

    if (!empty($user_name) && !empty($password))
    {
    }
    else
    {
        // Output error message
        echo "<h4><p class='text-danger'>You must enter both a "
             . "user name and password.</p></h4><hr/>";
    }
}
```
```

Inside the condition where the $user_name and $password are not empty, we must first query if the user already exists in the database. However, we need to practice safe database parameterization, and as I mentioned in the last chapter on securing our web applications, this is quite a bit more code to write. This is an excellent opportunity to abstract out the common calls we would need to make for parameterized queries by creating a helper function.

## 23. ADDING USER LOGINS

### Create a parameterizedQuery() Function

Let’s take a slight detour and create a function we can use to parameterize all our inputs to our database queries. This function safeguards our SQL queries by using prepared statements. Create a new script called `queryutils.php` we can include in our scripts where we will need to query the database.

First, we need to identify all the PHP functions and their input parameters to parameterize our queries. They would be:

| Function | Parameters | Return | Reference |
|---|---|---|---|
| `mysqli_prepare()` | connection, string query | statement | https://php.net/mysqli.prepare |
| `mysqli_stmt_bind_param()` | statement, string data types, variables (specified by their types) | true or false | https://php.net/mysqli-stmt.bind-param |
| `mysqli_stmt_execute()` | statement | true or false | https://php.net/mysqli-stmt.execute |
| `mysqli_stmt_get_result()` | statement | true or false | https://php.net/mysqli-stmt.get-result |
| `mysqli_errno()` | connection | error code | https://php.net/mysqli.errno |

Another thing to consider when creating queries is that we can have a varying number of query parameters that need to be parameterized. A cool thing about PHP is that we can create functions that take a variable number of parameters by preceding the last variable in an argument list with .... See the online documentation for more information on variable length parameters[4].

Whenever you create a function, it is a good practice to have a function header that describes the function, any input parameters, and any return values. It serves as excellent documentation on how to use your function, primarily if you use DocBlocks[5] to describe the parameters and return values. Keep in mind that you must update this comment if you change the parameters to your function or how it works.

> Another option afforded by PHP 7 is to use scalar and class type hints to indicate what kinds of arguments your function expects and what values it returns.

[4] variable length parameters: https://php.net/functions.arguments.php#functions.variable-arg-list
[5] DocBlocks: https://docs.phpdoc.org/3.0/guide/guides/docblocks.html

In the script queryutils.php, here is a function header I wrote for this function along with the function signature:

## Listing 23.7.

```
1. <?php
2.
3. /**
4.  * Purpose:      Parameterizes a database query
5.  *
6.  * Description:  Parameterizes an SQL query given a database connection, a query string, a data
7.  *               types string, and a variable number of parameters to be used in the query. If
8.  *               the query is successful, the database results object will be returned (or TRUE
9.  *               if no results set and the query was successful), otherwise FALSE will be returned
10.  *               and the connection will have to be queried for the last error.
11.  *
12.  * @param         $dbc database connection
13.  * @param         $sql_query SQL statement
14.  * @param         $data_types string containing one character for each parameter's type
15.  * @param         $query_parameters a variable list of parameters representing each query parameter
16.  *
17.  * @return string Database results set, otherwise false if there is a database error, or true if successful.
18.  */
19. function parameterizedQuery($dbc, $sql_query, $data_types, ...$query_parameters)
20. {
21. }
```

$data_types is a string that must contain one character representing the data type for each query parameter. Consider a query with two parameters where both parameters are integers. The $data_types parameter must be the string: 'ii'. You would pass two variables into the function for ...$query_parameters. Here's our example using these two parameters:

```
$query = "DELETE FROM reservation WHERE user_id = ? AND movieListing_id = ?";

$result = parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_to_delete);
```

Another helpful thing about using DocBlock function headers is that most Integrated Development Environments (IDEs), like Visual Studio Code, PhpStorm, etc., display the info in a tooltip when you call the function as in Figure 23.6. So let's fill in the guts of this function with the code from Listing 23.8.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_353_0.png)
