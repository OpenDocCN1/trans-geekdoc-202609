
An else is not required and is placed after all other conditional checks, such as elseif, which is in the next section.

## elseif

The elseif is the combination of an if and an else. This statement is placed after an if and allows the code to match another condition, which can be completely different than the if run before.

> An else or else if will only be evaluated if the preceding conditional is not met.

```
$loggedIn = false;
$colorOfSky = "blue";

if($loggedIn)
{
   // user logged in
}
elseif($colorOfSky == "blue")
{
   // color of sky is blue, log user in??
}
```

## while

The while is a type of loop. The code within the curly braces {} runs "while" the condition is met. Once the condition is no longer valid, the loop stops.

> Loops in PHP can run forever if not programmed correctly. Use caution when working with loops and always check for valid data first.

```
while($x < 50)
{
   print "x=" . $x . "<br />";
   $x++;
}
```

## for

A for loop is the most complex loop in PHP. Here is an example:

```
for ($x=0; $x < 10; $x++)
{
   print "x=" . $x . "<br />";
}
```

The first expression ($x=0) is executed unconditionally once at the start of the loop. The second expression ($x < 10) is evaluated on each pass and the loop will continue until this condition is met or the loop is stopped using a break. On each pass, the third expression ($x++) is executed. In this example, it increments $x on each pass.

You can nest `for` loops and even define multiple variables in the first expression. This can make your code faster, but harder to read.

## foreach

The `foreach` loop is used to iterate over an array. You assign the loop variable to the desired array, and on each pass the value is stored in that loop variable.

```php
$fruits = array("Orange", "Apple", "Banana", "Grapefruit");
foreach($fruits as $fruit)
{
    print "Fruit: " . $fruit;
}
```

> The variable `$fruit` will still exist once a `foreach` loop has been completed, so it is a good idea to destroy the variable using `unset()`, such as `unset($fruit)`.

## break

The `break` control ends the execution of a loop, regardless if the condition is met or not. You can place an optional numeric value informing PHP of how many levels it should break out. This is useful when you have a nested loop that needs to tell the parent to exit if an error occurs.

```php
for($i=0; $i < count($users); $i++)
{
    for($j=0; $j < 5; $j++)
    {
        if($users[$i][$j]['valid'] == false)
        {
            // found invalid user, group is compromised
            // exit both loops
            break 2;
        }
    }
}
```

## continue

Unlike `break`, `continue` will exit the current iteration of a loop, but allow the remaining iterations to continue on.

This is useful when you are looping through a bunch of data and only want to act on valid data.

```php
for($i=0; $i < count($users); $i++)
{
    if($users[$i]['valid'] == false)
    {
        // invalid user, continue with remaining list
        continue;
    }
    // more code logic here
}
```

Just like the `break`, `continue` will also accept a numeric argument telling it how many levels of enclosing loops to skip over.

## switch

A switch is similar to a series of if statements using the same expression (variable). You would generally use a switch when you want to test a variable against a lot of conditions.

```
switch($userLevel)
{
    case 'ADMIN':
        print "User is an admin";
        break;
    case 'MODERATOR':
        print "User is a mod";
        break;
    case 'MEMBER':
        print "User is a member";
        break;

    case 'GUEST':
        print "User is a guest";
        break;
}
```

A break is used to ensure the remaining checks will not run; in fact, if you remove the breaks, every condition will be checked, which can cause problems if you intend to do a multilevel validation.

## require

The require() statement attempts to load a file and will exit the script with a Fatal Error if that file is not found. This function checks for the file against the current include_path as well as the directory the file is running in.

```
require("importantFile.php");
```

The error that is displayed (see Figure 2.3) can sometimes cause a potential security concern in that it will display the path the file exists on. A better way to handle this is to create a check for the file first and display a cleaner, less crucial message to the user.

```
if(!file_exists("importantFile.php"))
{
    $error = "Sorry, one of the core components could not be loaded";
    exit($error); // display clean error and exit remaining script
}
require("importantFile.php"); // never runs, if file doesn't exist
```

## FIGURE 2.3

PHP require() error as seen in the browser

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_76_0.png)

## include

The include() statement is similar to the require with the exception it will display an error but not stop the execution of the script.

```
include("optionalFile.php");
```

## require_once

The require_once statement behaves similarly to require, with the exception that if the current file is already loaded it will not attempt to load it again. This is more useful as you continue to build large applications that sometimes share many files. This ensures that no redundant code is loaded.

```
require_once("requiredFile.php");
// ... other code here
require_once("requiredFile.php");
```

The second require_once will not run because the file has already been loaded in the previous portion of the code.

## include_once

The include_once() statement is similar to the require_once with the exception that if the file is not found, it only displays a simple error.

## Using type checking in PHP

Unlike most programming languages, PHP doesn't require strict typing of variables. This means you don't have to define what type of data a variable will hold.

This may seem like a good thing because variables can be shared. However the potential downside to this approach is that a variable that you expect to be a string could potentially show up as an array. This would most likely break your code or cause an exploitable portion of code. Imagine code similar to the following:

```php
$id = -1;

if(isset($id))
{
    // sql call here, set id to a string, for some reason
    $id = "user id";
}

// more logic here
if($id == -1)
{
    // user not logged in
}
else
{
    // user logged in
}
```

This is an overly dramatic example because it is full of worst-case scenarios, but you can see how untyped variables can cause headaches.

## Type checking functions

PHP does offer some special functions that allow you to check the type of a variable, but this does not stop other code from overwriting the variables.

An example of one of these functions would be is_string, which checks to see if the passed-in variable's contents are a string.

```php
$saying = "Hello, World!";

if(is_string($saying))
{
    print "$saying is a string";
}
```

PHP offers the ability to test for arrays, numbers, strings, and empty values.

## Future version support

It has been mentioned that future versions of PHP could include strict type checking, but for now,
these functions, when needed, will provide a higher level of integrity for your application.

## Exploring the Basics of MySQL

MySQL is the storage application used with PHP to create a dynamic application. You can store
pretty much any type of data in a MySQL database and have the ability to share that information
with other applications and systems. Oftentimes a database is used when searching needs to be
done or if data is changing frequently and many people will be requesting this updated data.

The alternative to a database is a flat file (text file) that has many limitations, the most devastating
being the fact that only so many instances of the file can be used at once. Another limitation is the
ability to quickly index and search a text file.

## Using statements

The contents in a MySQL database are stored in tables. These tables are stored in databases that
make up the MySQL system. The data stored in those tables is accessed using various statements
and conditions, which are called queries.

There are many statements that can be used in SQL queries.

## SELECT

The SELECT statement is the most common statement, which tells MySQL what contents
(columns) you want returned from a table.

```sql
SELECT id,name,ip, bio FROM users WHERE id=3
```

You can select data from multiple tables using commas (,) to separate the column and table
names.

```sql
SELECT users.id, users.name, members.posts, members.subs FROM
users, members WHERE members.userID=users.id AND users.id=3
```

## INSERT

The INSERT statement is used to add new rows to an existing table. There are multiple ways to
define an INSERT.

If you only want to insert some columns you need to define those columns.

```sql
INSERT INTO members (name, bio, ip) VALUES ($name, $bio, $ip);
```
