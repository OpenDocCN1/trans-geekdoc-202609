
# Syntax

PHP code always starts with `<?php` and `?>`. Each line of PHP code must end with a semicolon. The semicolon is used to distinguish one set of instructions from another. A PHP scripting block can be placed anywhere on the page. A PHP file will contain HTML and PHP. Below is a basic example that displays the text FileMaker API for PHP to a web browser. To output information to the browser you can use the PHP method echo or print. Echo is the more common, modern method.

```html
<body>

<?php
echo "FileMaker API for PHP";
?>

</body>
</html>
```

# Includes

You can insert the contents of other PHP files into your PHP file before the server executes it. This is done with either the `include()` or `require()` function. This is very useful to perform tasks such as create a single database connection for your entire site, create custom functions, and insert headers, or other elements that will be reused more than once. It's very similar to creating a sub-script in FileMaker with the point being to organize your code more logically and reuse as much code as possible. The `include` and `require()` functions are the same except how they handle errors when they can't find the file.

- `include()` generates a fatal error, but the script will still continue to execute.
- `require()` generates a fatal error and stops the script at that.

Every PHP file in this book will start with the `include()` to connect to the database using a predefined account name and password. Notice the `../Conn/` path. This relative path is up two folders from the current folder and into the `Conn` to find the `dbaccess.php` file. `Conn` is short for connection. Without connecting to the database, none of the FileMaker API methods will be able to retrieve any data from the database. This is a good example of reusing code more than one time. If you need to change the account name and password you only have to modify the `dbaccess.php` file once rather than every file in your web site.

```php
<?php
include("../Conn/dbaccess.php");
?>
```

# Comments

There are two basic methods to comment your code. You can comment one or more lines of `<!-- HTML code -->` inside. A PHP tag you can use a single line comment with `//` or `#`. If you want to comment a large block using `/*` and `*/`. It's a good idea to comment your code so you know what the script is to do. HTML comments show up on the page source code of the user's browser. Whereas PHP is a server-side scripting language, the PHP comments are stripped from the page before they are returned to the browser. In any case it's probably wise not to include comments in your code such as account names and passwords that might create a security issue. I have seen bugs with Firefox that allow the browser to download the source code from the server!

```php
<!--
HTML
comment
-->

<?php
// Single line comment
?>
```

# Single line comment

/*
Multiple
Line
Comment
*/
?>

# Quotes

'Single' and "double" quotes behave differently in PHP. Single quotes display the exact contents between the quotes. Double quotes allow PHP to process variables inside the quotes. In some cases you may also need to escape special characters using a backslash `\`. That will allow you to display special characters as text on the web browser. The following example will differ based on which style of quotes are used.

```php
<?php
$text = "FileMaker API for PHP";
echo "We are learning the $text";
echo "<br>";
?>
```

1. It must start with a lower letter or an underscore `_`
2. It can only contain a-z, 0-9, or an underscore `=`
3. It should not contain spaces. However, multiple words can use capitalization as `$myVariable`

Using the example code you can create two variables for `$foundRecords` and `$maxRecords`. Then use the PHP engine to execute some simple math that displays the integer value of `$foundRecords` divided by `$maxRecords`.

```php
<?php
$foundRecords = "25";
$maxRecords = "5";
echo "The total number of pages to display: " 
intval($foundRecords/$maxRecords);
?>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_64_0.png)

Figure 5-13: Variables

Concatenation fields, variables, and text together is a basic technique using a FileMaker calculation. FileMaker concatenates two or more items together by using the ampersand `"&"` symbol. The FileMaker concatenation symbol is the period `.`. There's a lesser documented trick that lets you concatenate existing values together using `.`. Take a look at the following example:

```php
<?php
$firstName = "Todd";
$lastName = "Duell";
$text = "FileMaker API for PHP";

$html = $firstName . " " . $lastName;
$html .= ". says it is fun to learn the ";
$html .= $text;
echo $html;
?>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_64_1.png)

Todd Duell says it is fun to learn the FileMaker API for PHP

Figure 5-14: Concatenation

# Operators

Operators are used for math, to compare values, and to combine values together. The table below shows the common PHP operators.

| Operator | Description | Example |
| :--- | :--- | :--- |
| `+` | Addition | `5+2` |
| `-` | Subtraction | `5-2` |
| `*` | Multiplication | `5*2` |
| `/` | Division | `5/2` |
| `%` | Modulo | `5%2` |
| `++` | Increment | `5++` |
| `--` | Decrement | `5--` |
| `=` | Assignment | `x=5` |
| `+=` | Addition Assignment | `x+=5` |
| `-=` | Subtraction Assignment | `x-=5` |
| `*=` | Multiplication Assignment | `x*=5` |
| `/=` | Division Assignment | `x/=5` |
| `%=` | Modulo Assignment | `x%=5` |
| `==` | Equal to | `x==5` |
| `!=` | Not equal to | `x!=5` |
| `<` | Less than | `x<5` |
| `>` | Greater than | `x>5` |
| `<=` | Less than or equal to | `x<=5` |
| `>=` | Greater than or equal to | `x>=5` |
| `&&` | And | `x&&y` |
| `||` | Or | `x||y` |
| `!` | Not | `!x` |

# If/Else

Using the conditional statement to execute code based on conditions. Let's look at some examples with the `if` and `else` statements.

```php
<?php
if ($day == "Friday") {
    echo "It is Friday";
} else {
    echo "It is not Friday";
}
?>
```

If you need to check several different conditions you can utilize the `elseif` statement.

```php
<?php
if ($day == "Friday") {
    echo "It is Friday";
} elseif ($day == "Saturday") {
    echo "It is Saturday";
} else {
    echo "It is not Friday or Saturday";
}
?>
```

# Looping

Looping will execute a section of code for a specified number of times. FileMaker script has looping capabilities. PHP looping is easier to perform because it has more logical choices in terms of how many times it will run and when the loop will end. There are four basic looping mechanisms: while, do...while, for, and foreach.

While loops through a section of code where the condition is true. Do...while loops through a section as long as the code is true. For loops through a specific number of times. For is by far the most common that you'll encounter when extracting data from an array from the database. It loops through the code for each element in the array. It's very similar to the FileMaker step Go to Next Record [Exit After Last]. You don't have to tell it to stop.

The while loop below will run as long as the counter is less than 5. The counter will increase by 1 for each loop. This is very to a mechanism you might use a FileMaker script with a counter to execute a loop.

```php
<?php
$counter=1;
while($counter<=5){
    echo "Number " . $counter . "<br>";
    $counter++;
}
?>
```

The do...while loop is similar to the while loop. The difference is how you arrange the order of the methods in the code may vary to accommodate the logic and the exit condition is always at the end of the code.

```php
<?php
$counter=1;
do {
    echo "Number " . $counter . "<br>";
    $counter++;
} while($counter<=5);
?>
```

The for loop is used when you know exactly how many times the loop should execute — for(Counter Initialization, Exit Condition, Counter Increment). Counter Initialization is usually used to start a counter. Exit Condition is evaluated for each loop. If the condition is true, the loop continues. If the condition is false, the loop stops. Counter Increment is used to increment the counter. The example below achieves exactly the same results as the previous methods.

```php
<?php
for ($i=1; $i<=5; $i++) {
    echo "Number " . $i . "<br>";
}
?>
```
