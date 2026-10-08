
## Examining Basic Function Structure

you do the same way as anywhere else in the script—with a closing PHP tag followed by the
HTML: The following is a legal modification of the preceding example and produces the same
output:

```php
<?php
function my_function() {
?>
My function was called
<?php
)
?>
```

Note that the PHP code is enclosed within matching opening and closing PHP tags. For most of
the small code examples in this book, we do not show these tags. We show them here
because they are required within the example as well as above and below it.

## Naming Your Function

The most important point to consider when naming your functions is that the name should be
short but descriptive. If you create a page header, pageheader(), page_header(),
draw_header(), and so on might be good names.

A few restrictions follow:

- Your function name cannot have the same name as an existing function.
- Your function name can contain only letters, digits, and underscores.
- Your function name cannot begin with a digit.

Many languages allow you to reuse function names. This feature is called function
overloading. However, PHP does not support function overloading, so your function cannot
have the same name as any built-in function or an user-defined function. (There is
a form of overloading within classes, which we discuss in Chapter 6, "Object-Oriented PHP",
but it is different from most language's version of overloading.) Note that although PHP
script knows all about the built-in functions in the global scope, user-defined functions exist
only in scripts where they are declared. This means that you could reuse a function name in
different file, which would lead to confusion and should be avoided.

The following function names are legal:

```php
name()
name2()
name_three()
name_four()
```

These names are illegal:

```php
name()
name-six()
fopen()
```

The last would be legal if it didn't already exist as part of PHP itself.

Note that although $name is not a valid name for a function, a function call like
$name();

May well execute, depending on the value of $name. The reason is that PHP takes the value stored in name, looks for a function with that name, and tries to call it for. This type of function is referred to as a variable function.

## Using Parameters

To do your work, functions require one or more parameters. A parameter allows you to pass data into a function. Here is a sample function that requires a parameter; it takes a one-dimensional array and displays it as a table:

```php
function create_table($data) {
  echo '<<table>>';
  reset($data);
  $value = current($data);
  while ($value) {
    echo '<tr><td>$value</td></tr>\n';
    $value = next($data);
  }
  echo '</table>';
}
```

If you call the create_table() function as follows

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
create_table($my_data);
```

you will see output as shown in Figure 5.4.

![](img/654520c37415debd4290b9b4aa2c03f2_177_0.png)

Figure 5.4 This HTML table is the result of calling create_table()

## Using Parameters 147

Passing a parameter allows you to get data created outside the function—in this case, the array $my_data—into the function.

As with built-in functions, user-defined functions can have multiple parameters and optional parameters. You can improve the `create_table()` function in many ways, one might be to allow the caller to specify other attributes but you to optionally set the table's caption and here is an improved version of the function; it is similar but allows you to optionally set the table's caption:

```php
function create_table($data, $header=NULL, $caption=NULL) {
  echo '<<table>>';
  if ($caption) {
    echo "<caption>$caption</caption>";
  }
  if ($header) {
    echo "<tr><td>$header</th></tr></tr>";
  }
  reset($data);
  $value = current($data);
  while ($value) {
    echo "<tr><td>$value</td><td>$value</td></tr>\n";
    $value = next($data);
  }
  echo '</table>';
}
```

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
$my_header = 'Data about something';
$my_caption = '$my_data, $my_header, $my_caption';
create_table($my_array);
```

The first parameter for `create_table()` is still required. The next two are optional because default values are defined for them. You can create similar output to that shown in Figure 5.4 with this call to `create_table()`:

```php
create_table($my_array, 'A header');
```

If you want the same data displayed with a header but no caption, you could call the function as follows:

Optional values do not all need to be provided; you can provide some and ignore some. Parameters are assigned from left to right.

Keep in mind that you cannot leave out one optional parameter but include a later listed one. In this example, if you want to

The last would be legal if it didn't already exist as part of PHP itself.

Note that although $name is not a valid name for a function, a function call like
$name();

May well execute, depending on the value of $name. The reason is that PHP takes the value stored in name, looks for a function with that name, and tries to call it for. This type of function is referred to as a variable function.

## Using Parameters

To do your work, functions require one or more parameters. A parameter allows you to pass data into a function. Here is a sample function that requires a parameter; it takes a one-dimensional array and displays it as a table:

```php
function create_table($data) {
  echo '<<table>>';
  reset($data);
  $value = current($data);
  while ($value) {
    echo '<tr><td>$value</td></tr>\n';
    $value = next($data);
  }
  echo '</table>';
}
```

If you call the create_table() function as follows

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
create_table($my_data);
```

you will see output as shown in Figure 5.4.

![](img/654520c37415debd4290b9b4aa2c03f2_177_0.png)

Figure 5.4 This HTML table is the result of calling create_table()

## Using Parameters 147

Passing a parameter allows you to get data created outside the function—in this case, the array $my_data—into the function.

As with built-in functions, user-defined functions can have multiple parameters and optional parameters. You can improve the `create_table()` function in many ways, one might be to allow the caller to specify other attributes but you to optionally set the table's caption and here is an improved version of the function; it is similar but allows you to optionally set the table's caption:

```php
function create_table($data, $header=NULL, $caption=NULL) {
  echo '<<table>>';
  if ($caption) {
    echo "<caption>$caption</caption>";
  }
  if ($header) {
    echo "<tr><td>$header</th></tr></tr>";
  }
  reset($data);
  $value = current($data);
  while ($value) {
    echo "<tr><td>$value</td><td>$value</td></tr>\n";
    $value = next($data);
  }
  echo '</table>';
}
```

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
$my_header = 'Data about something';
$my_caption = '$my_data, $my_header, $my_caption';
create_table($my_array);
```

The first parameter for `create_table()` is still required. The next two are optional because default values are defined for them. You can create similar output to that shown in Figure 5.4 with this call to `create_table()`:

```php
create_table($my_array, 'A header');
```

If you want the same data displayed with a header but no caption, you could call the function as follows:

Optional values do not all need to be provided; you can provide some and ignore some. Parameters are assigned from left to right.

Keep in mind that you cannot leave out one optional parameter but include a later listed one. In this example, if you want to

The last would be legal if it didn't already exist as part of PHP itself.

Note that although $name is not a valid name for a function, a function call like
$name();

May well execute, depending on the value of $name. The reason is that PHP takes the value stored in name, looks for a function with that name, and tries to call it for. This type of function is referred to as a variable function.

## Using Parameters

To do your work, functions require one or more parameters. A parameter allows you to pass data into a function. Here is a sample function that requires a parameter; it takes a one-dimensional array and displays it as a table:

```php
function create_table($data) {
  echo '<<table>>';
  reset($data);
  $value = current($data);
  while ($value) {
    echo '<tr><td>$value</td></tr>\n';
    $value = next($data);
  }
  echo '</table>';
}
```

If you call the create_table() function as follows

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
create_table($my_data);
```

you will see output as shown in Figure 5.4.

![](img/654520c37415debd4290b9b4aa2c03f2_177_0.png)

Figure 5.4 This HTML table is the result of calling create_table()

## Using Parameters 147

Passing a parameter allows you to get data created outside the function—in this case, the array $my_data—into the function.

As with built-in functions, user-defined functions can have multiple parameters and optional parameters. You can improve the `create_table()` function in many ways, one might be to allow the caller to specify other attributes but you to optionally set the table's caption and here is an improved version of the function; it is similar but allows you to optionally set the table's caption:

```php
function create_table($data, $header=NULL, $caption=NULL) {
  echo '<<table>>';
  if ($caption) {
    echo "<caption>$caption</caption>";
  }
  if ($header) {
    echo "<tr><td>$header</th></tr></tr>";
  }
  reset($data);
  $value = current($data);
  while ($value) {
    echo "<tr><td>$value</td><td>$value</td></tr>\n";
    $value = next($data);
  }
  echo '</table>';
}
```

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
$my_header = 'Data about something';
$my_caption = '$my_data, $my_header, $my_caption';
create_table($my_array);
```

The first parameter for `create_table()` is still required. The next two are optional because default values are defined for them. You can create similar output to that shown in Figure 5.4 with this call to `create_table()`:

```php
create_table($my_array, 'A header');
```

If you want the same data displayed with a header but no caption, you could call the function as follows:

Optional values do not all need to be provided; you can provide some and ignore some. Parameters are assigned from left to right.

Keep in mind that you cannot leave out one optional parameter but include a later listed one. In this example, if you want to

The last would be legal if it didn't already exist as part of PHP itself.

Note that although $name is not a valid name for a function, a function call like
$name();

May well execute, depending on the value of $name. The reason is that PHP takes the value stored in name, looks for a function with that name, and tries to call it for. This type of function is referred to as a variable function.

## Using Parameters

To do your work, functions require one or more parameters. A parameter allows you to pass data into a function. Here is a sample function that requires a parameter; it takes a one-dimensional array and displays it as a table:

```php
function create_table($data) {
  echo '<<table>>';
  reset($data);
  $value = current($data);
  while ($value) {
    echo '<tr><td>$value</td></tr>\n';
    $value = next($data);
  }
  echo '</table>';
}
```

If you call the create_table() function as follows

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
create_table($my_data);
```

you will see output as shown in Figure 5.4.

![](img/654520c37415debd4290b9b4aa2c03f2_177_0.png)

Figure 5.4 This HTML table is the result of calling create_table()

## Using Parameters 147

Passing a parameter allows you to get data created outside the function—in this case, the array $my_data—into the function.

As with built-in functions, user-defined functions can have multiple parameters and optional parameters. You can improve the `create_table()` function in many ways, one might be to allow the caller to specify other attributes but you to optionally set the table's caption and here is an improved version of the function; it is similar but allows you to optionally set the table's caption:

```php
function create_table($data, $header=NULL, $caption=NULL) {
  echo '<<table>>';
  if ($caption) {
    echo "<caption>$caption</caption>";
  }
  if ($header) {
    echo "<tr><td>$header</th></tr></tr>";
  }
  reset($data);
  $value = current($data);
  while ($value) {
    echo "<tr><td>$value</td><td>$value</td></tr>\n";
    $value = next($data);
  }
  echo '</table>';
}
```

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
$my_header = 'Data about something';
$my_caption = '$my_data, $my_header, $my_caption';
create_table($my_array);
```

The first parameter for `create_table()` is still required. The next two are optional because default values are defined for them. You can create similar output to that shown in Figure 5.4 with this call to `create_table()`:

```php
create_table($my_array, 'A header');
```

If you want the same data displayed with a header but no caption, you could call the function as follows:

Optional values do not all need to be provided; you can provide some and ignore some. Parameters are assigned from left to right.

Keep in mind that you cannot leave out one optional parameter but include a later listed one. In this example, if you want to

The last would be legal if it didn't already exist as part of PHP itself.

Note that although $name is not a valid name for a function, a function call like
$name();

May well execute, depending on the value of $name. The reason is that PHP takes the value stored in name, looks for a function with that name, and tries to call it for. This type of function is referred to as a variable function.

## Using Parameters

To do your work, functions require one or more parameters. A parameter allows you to pass data into a function. Here is a sample function that requires a parameter; it takes a one-dimensional array and displays it as a table:

```php
function create_table($data) {
  echo '<<table>>';
  reset($data);
  $value = current($data);
  while ($value) {
    echo '<tr><td>$value</td></tr>\n';
    $value = next($data);
  }
  echo '</table>';
}
```

If you call the create_table() function as follows

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
create_table($my_data);
```

you will see output as shown in Figure 5.4.

![](img/654520c37415debd4290b9b4aa2c03f2_177_0.png)

Figure 5.4 This HTML table is the result of calling create_table()

## Using Parameters 147

Passing a parameter allows you to get data created outside the function—in this case, the array $my_data—into the function.

As with built-in functions, user-defined functions can have multiple parameters and optional parameters. You can improve the `create_table()` function in many ways, one might be to allow the caller to specify other attributes but you to optionally set the table's caption and here is an improved version of the function; it is similar but allows you to optionally set the table's caption:

```php
function create_table($data, $header=NULL, $caption=NULL) {
  echo '<<table>>';
  if ($caption) {
    echo "<caption>$caption</caption>";
  }
  if ($header) {
    echo "<tr><td>$header</th></tr></tr>";
  }
  reset($data);
  $value = current($data);
  while ($value) {
    echo "<tr><td>$value</td><td>$value</td></tr>\n";
    $value = next($data);
  }
  echo '</table>';
}
```

```php
$my_data = ['First piece of data','Second piece of data','And the third'];
$my_header = 'Data about something';
$my_caption = '$my_data, $my_header, $my_caption';
create_table($my_array);
```

The first parameter for `create_table()` is still required. The next two are optional because default values are defined for them. You can create similar output to that shown in Figure 5.4 with this call to `create_table()`:

```php
create_table($my_array, 'A header');
```

If you want the same data displayed with a header but no caption, you could call the function as follows:

Optional values do not all need to be provided; you can provide some and ignore some. Parameters are assigned from left to right.

Keep in mind that you cannot leave out one optional parameter but include a later listed one. In this example, if you want to

[Rest of the text follows similar logic based on OCR content]

## Understanding Scope

You might have noticed that when we use require() and include(), the scope behaves differently. PHP has fairly simple rules:

- Variables declared inside a function are in scope from the statement in which they are declared until the end of the function. This is called function scope. These are called local variables.
- Variables declared outside functions are in scope from the statement in which they are declared to the end of the file. This is called global scope. These are called global variables.

- Special superglobal variables are visible both inside and outside functions. (See Chapter 1, "PHP Course," for more information on these.)

- Using require() and include() statements do not affect scope. If the statement is within a function, function scope applies. If it is not inside a function, global scope applies.

- The keyword global can be used to manually specify that a variable defined or used within a function will have global scope.

- Variables can be manually deleted by unset($variable_name). A variable is no longer in scope if it has been unset.

The following examples may help to clarify scope:
The following code produces no output. Here, we declare a variable $var inside the fn(). Because this is inside a function, it has function scope and exists only where it is declared until the end of the function. When you refer to $var outside the function, the new variable called $var is created. This new variable has global scope and will be visible until the end of the file. Unfortunately, if the only statement you use with this $var is echo, it will never have a value.

```php
function fn() {
$var = "contents";
}
fn();
echo $var;
```

The following example is the inverse. Here, you declare a variable outside the function and then to use it within a function:

```php
<?php
function fn() {
echo 'inside the function, at first $var = ''.$var.'<br />';
$var = 2;
echo 'then, inside the function, $var = ''.$var.'<br />';
}
$var = 1;
fn();
echo 'outside the function, $var = ''.$var.'<br />';
?>
```

The output of this code is as follows:
inside the function, at first $var =
then inside the function, $var = 2
outside the function, $var = 1
