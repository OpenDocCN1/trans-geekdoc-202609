
Speaking of calculations, the rest of the function declaration is the code that performs the calculation, or does whatever else the function is supposed to do. That code must be enclosed in a set of braces (`{ … }`). You can write nearly any code you like between the opening and closing braces, but the code for the area function is as follows:

```
return $width * $height;
```

You can think of the code within those braces as a miniature PHP script. This function is a simple one, because it contains just a single statement—a `return` statement.

A `return` statement can be used in the code of a function to send data out of the function back into the place it was called. In this case, we’re sending the result of the `$width * $height` calculation out of the function in the same way the `rand()` function sends a random number from the function to the variable we’re storing the number in.

In addition, the `return` statement jumps back into the main script immediately. When the PHP interpreter hits a `return` statement, it immediately stops running the code of this function and goes back to where the function was called. It’s sort of an ejector seat for functions!

Writing a function on its own does nothing. No code inside the function is run until the function is called. Like the `rand()` function we used at the start of this book, it just sits there waiting to be called.

You can think of writing a function like installing an app on your computer or phone. You need it there to use it, but once installed, it’s dormant and available for use, but won’t actually do anything until you run it.

Although it’s possible to write the function in the same file that we want to run it in, that’s a bad idea. We might want to run the function from different files, and like the database connection above, repeating code isn’t good. Instead, we can put it in its own file (such as `areaOfRectangle.php`) in the `includes` directory, and then include it in the script we wish to use it in:

```
include_once  __DIR__ . '/../includes/areaOfRectangle.php';

$areaOfRectangle = areaOfRectangle(3, 5);

include 'output.html.php';
```

Avoid using `include` or `require` to load include files that contain functions. As explained in the “Types of Includes” section earlier in this chapter, that would risk defining the functions in the library more than once and covering the user’s screen with PHP warnings.

It’s standard practice (but not required) to include your function libraries at the top of the script, so that you can quickly see which include files containing functions are used by any particular script.

What we have here are the beginnings of a **function library**—an include file that contains declarations for a group of related functions. If you wanted to, you could rename the include file to `geometry.php`, add a whole bunch of functions to it, and perform various geometrical calculations.

## Variable Scope

One big difference between custom functions and include files is the concept of **variable scope**. Any variable that exists in the main script will also be available and can be changed in the include file. While this is useful sometimes, more often it’s a pain in the neck. Unintentionally overwriting one of the main script’s variables in an include file is a common cause of errors—and ones that can take a long time to track down and fix! To avoid such problems, you need to remember the variable names in the script that you’re working on, as well as any that exist in the include files your script uses.

Functions protect you from such problems. A function is like its own independent mini program with inputs (arguments) and an output (a return value). Anything the function does is effectively hidden from the script that calls it. The script calling the function sends it some values and then receives the return values. It doesn’t matter what the function does in between receiving the arguments and returning the value.

Variables created inside a function (including any argument variables) exist only within that function, and disappear when the function has run its course. In addition, variables created outside the function are completely inaccessible inside it. The only variables a function has access to are the ones provided to it as arguments.

In programmer-speak, the **scope** of these variables is the function; they’re said to have **function scope**. In contrast, variables created in the main script, outside of any function, are unavailable inside functions. The scope of these variables is the main script, and they’re said to have **global scope**.

Okay, but beyond the fancy names, what does this really *mean* for us? It means that you could have a variable called `$width` in your main script, and another variable called `$width` in your function, and PHP would treat these as two entirely separate variables! Perhaps more usefully, you can have two different functions each using the same variable names, and they’ll have no effect on each other, because their variables are kept separate by their scope.

On some occasions, you may actually *want* to use a global-scope variable (**global variable** for short) inside one of your functions. For example, the `DatabaseConnection.php` file creates a database connection for use by your script and stores it in the global variable `$pdo`. You might then want to use this variable in a function that needed to access the database.

Let’s create a function that queries the database and returns to us the number of jokes that are currently held in the `joke` table. Disregarding variable scope, here’s how you might expect such a function to work:

```
include_once __DIR__ . '/../includes/DatabaseConnection.php';

function totalJokes() {
  $stmt = $pdo->prepare('SELECT COUNT(*) FROM `joke`');
  $stmt->execute();

  $row = $stmt->fetch();

  return $row[0];
}

echo totalJokes();
```

### Be Careful Where You Place Your Files

Note that the first line of this controller script uses a shared copy of the `DatabaseConnection.php` file in the `includes` directory. Make sure you’ve placed a copy of this file in the `includes` directory. Otherwise, PHP will complain that it’s unable to find the `DatabaseConnection.php` file.

The file `DatabaseConnection.php` creates the variable `$pdo`, which we’re referencing inside the function.

The `DatabaseConnection.php` include file creates the variable `$pdo` in the script. The problem here is that the `$pdo` variable is unavailable within the scope of the function. If you attempt to call this function as it is, you’ll receive the errors shown in the following image.

![The totaljokes function cannot access $pdo](Images/scope-error.png)

The reason for this error is **scope**. The `$pdo` variable was created outside the function, so it’s not available for use inside it.

Although there *is* [a way](http://php.net/manual/en/reserved.variables.globals.php) to make the same `$pdo` variable available in the function, it’s a very bad idea. (Seriously, don’t do this!) If, for example, the function changed the `$pdo` by accident to a string—`$pdo = 'select * from joke';`—the `$pdo` variable would now be a string everywhere else in the PHP script. Global variables are a *very* bad idea and lead to problems that are very difficult to track down and fix. You should avoid global variables at any cost.

### Why Global Variables Are Bad

For more information on why global variables are bad, see one of the following links:

*   “[Global Variables are Evil](https://www.cs.usfca.edu/%7Ewolber/courses/110/lectures/globals.htm)”

*   “[Wow, They Were Right, Global Variables Are Bad](https://blog.cranksoftware.com/wow-they-were-right-global-variables-are-bad/)”

*   “[Global Variables Are Bad](http://wiki.c2.com/?GlobalVariablesAreBad)”

To avoid this, you can use `$pdo` as an argument and pass in the required variables to your function:
