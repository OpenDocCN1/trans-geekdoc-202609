# 22. CREATING SECURE WEB APPLICATIONS

The issue with using mysql_real_escape_string() is that it escapes the form field entry without the context of the underlying SQL query using it. The reasons why this fails sometimes are pretty technical. However, take a look at http://phpa.me/so-sqli-edgecase for an edge case that fails sanitation.

# Prepared Statements

Prepared Statements are a better guard against SQL injection. A more robust method for mitigating SQL injections is to use prepared statements, also known as parameterized queries. The problem with mysql_real_escape_string() is that it doesn't separate your input from the query itself, but in effect, it inserts it into the query. However, prepared statements will separate your database inputs from your queries and not allow you to insert SQL commands (like subqueries). Let's look at prepared statements and how to use them.

The PHP language, via the mysqli extension, provides two functions to parameterize our database inputs: mysqli_prepare() and mysqli_stmt_bind_param(). We can use these functions together to parameterize database queries. mysqli_prepare() is used to parameterize the SQL query into a statement that will be bound to the input parameters using the mysqli_stmt_bind_param() function.

Listing 22.2 shows how to use these functions.

```
```php
<?php
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
or trigger_error(
'Error connecting to MySQL server for' . DB_NAME,
E_USER_ERROR
);

$search_term = isset($_POST['search']) ? $_POST['search'] : '';

$sql = "SELECT some_field_1, some_field_2, some_field_3 "
. " FROM Sometable WHERE some_field_n LIKE ?";

$stmt = mysqli_prepare($dbc, $sql);

$search_term = '%' . $search_term . '%';

mysqli_stmt_bind_param($stmt, 's', $search_term);
```
```

> [8] mysqli_prepare(): https://php.net/mysqli_prepare
> [9] mysqli_stmt_bind_param(): https://php.net/mysqli_stmt_bind_param
> [10] mysqli_stmt_bind_param(): https://php.net/mysqli_stmt_bind_param