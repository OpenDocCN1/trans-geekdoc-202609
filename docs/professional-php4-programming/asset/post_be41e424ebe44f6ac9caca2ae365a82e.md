
$fWage = 30.0;
echo($fWage); // (local variable)
}

$fWage = 40.0;
echo($fWage); // Prints 40 (global variable)
printWage(); // Prints 30 (local variable)
echo($fWage); // Prints 40 (global variable)

To access a global (outside) variable from within a function you can declare the variable as global:

```
function printWage()
{
    // Print fWage to the browser

    global $fWage;

    $fWage = 30.0; // Change global variable
    echo($fWage);
}

$fWage = 40.0;
echo($fWage); // Prints 40
printWage(); // Prints 30
echo($fWage); // Prints 30
```

Global variables can also be accessed through the $GLOBALS array. This is an associative array that is available in all functions. Its elements contain all of the global variables in the program:

```
function printWage()
{
    // Print fWage to the browser

    $GLOBALS["fWage"] = 30.0; // Change global variable
    echo($GLOBALS["fWage"]);
}

$fWage = 40.0;
echo($fWage); // Prints 40
printWage(); // Prints 30
echo($fWage); // Prints 30
```

The use of global variables is widely considered to be poor programming style. Since global variables can be changed anywhere in a program, they often result in complex errors that are difficult to identify and repair. In addition, overuse of global variables leads to the development of monolithic software, when well-designed software should consist of modular, individual units that interact among each other.

> Unless absolutely necessary, global variables should be avoided.

## Variable Lifetime

A local variable only retains its value while the function is executing and it is re-initialized with each invocation of the function. The following function would return the value 1 every time:

```
function counter()
{
    // Increment the count
    $iCounter = 0;
    return ++$iCounter;
}
```

To make a local variable static, use the static declaration. Static variables retain their previous value with each invocation of the function:

```
function counter()
{
    // Increment the count
    static $iCounter = 0;
    return ++$iCounter;
}
```

In this example, $iCounter is set to zero the first time the function is called. On all subsequent function calls $iCounter "remembers" what its value was the last time the function was executed. Be aware that static variables only retain their values during the execution of the script. If the user reloads the web page, thus causing the script to re-execute, the variable will re-initialize.

## Recursion

Recursion is when a function invokes itself. This circular quality can be useful, especially with some repetitive algorithms. While recursion often leads to an elegant solution to a problem, more often than not it is also difficult to follow the logic of recursion as opposed to a simple loop. Furthermore, recursion is usually inefficient, and it could lead to catastrophic errors if care is not taken to avoid infinite invocations of the function.

The following example is based on the recognition that x ^ y is mathematically equivalent to x * x ^(y-1):

```
function power($iBase, $iExponent)
{
    // Returns iBase to the power of iExponent
    if ($iExponent) {
        return $iBase * power($iBase, $iExponent - 1);
    }
    return 1;
}
```

This code takes a problem such as "5 to the power of 3" and breaks it down to "5 times (5 to the power of 2)". It then breaks "5 to the power of 2" down to "5 times (5 to the power of 1)" and so on until the exponent is zero. The loop-based equivalent to this function is:

```
function power($iBase, $iExponent)
{
    // Returns iBase to the power of iExponent

    for ($iAnswer = 1; $iExponent > 0; --$iExponent) {
        $iAnswer *= $iBase;
    }
    return $iAnswer;
}
```

This is a bit easier to follow and more efficient, but if you're a mathematical show-off, you'll probably prefer the recursion. Both of these functions work only for positive integer values of $iExponent.

## Assigning Functions to Variables

In PHP, variables can refer to functions. This feature is seldom used, but one possible use might be when dynamic conditions determine which function should be used in a program:

```
switch ($sClientType) {
case "PC":
    $output_function = "print_XHTML";
    break;

case "Mobile":
    $output_function = "print_WML";
    break;

default:
    $output_function = "print_text";
    break;
}

// Now call the appropriate output function:
$output_function("Welcome");
```

## Using Functions to Organize Code

As we have seen in the previous sections, functions provide the ability to sensibly structure code in a way that makes it reusable. They also allow developers to break up a potentially large, monolithic program into smaller, more manageable parts that can be tested, debugged, and modified *relatively* independently.

A typical PHP script performs many different but related tasks. A single script might validate form data received from the browser, perform database queries based on those data, and display a set of results back to the user. Writing this all in a linear monolithic script can make it difficult to maintain or even to follow:

```
<?php
...

// Code to receive and validate form data
if (isset($name)) {
    ...
}
// Code to determine user's actions
if ($Action == "Create") {
    // Code to perform INSERT database queries
    ...
    ...
} elseif ($Action == "Display") {
    // Code to perform SELECT database queries
    ...
    ...
}

// Code to display results
echo(...);
?>
```

This code becomes increasingly complex to write as a single unit. We may need to display different result screens depending on query results or user actions. Furthermore, another developer looking at this code needs to read the whole script to understand the basic flow of control. In addition, a small error anywhere in the script would be difficult to isolate.

With functions, we can divide these tasks into smaller, more robust units that can be pieced together like blocks to build the whole. We can also include a `main()` function that controls the flow of execution and allows a developer to determine the basic logic at a glance. In the outline below, we are supposing that the variable `$action` holds the results of the submit buttons on a web page (that is, every submit button has the attribute name="action"):

```php
<?php
// maintain.data.php

function validateData()
{
    // Validate all outside data
    ...
} // end validateData()

function createRecord()
{
    // Code to perform insert database queries
    ...
} // end createRecord()

function deleteRecord()
{
    // Code to perform delete database queries
    ...
} // end deleteRecord()

function getData()
{
    // Code to perform select database queries
    ...
} // end getData()

function displayMenu()
{
    // Display menu in XHTML
    ...
    <form action="maintain.data.php" ...
    ...
} // end displayMenu()

function displayResults()
{
    // Display query confirmation in XHTML
    ...
} // end displayResults()

function displayData()
{
    // Display records in XHTML
    ...
} // end displayData()

function main()
{
    // Flow control
    if ( ! validateData() ) {
    ...
    }

    switch ($action) {
    // Determine user action
    case "":
    // No submit button was clicked
    // first time visiting page
    displayMenu();
    break;
case "Create":
    $bSuccess = createRecord();
    displayResults($bSuccess);
    break;
case "Delete":
    $bSuccess = deleteRecord();
    displayResults($bSuccess);
    break;
case "View":
    $aData = getData();
    displayData($aData);
    break;
} // end main()
/*************************/
// Call the main() function
main();
/*************************/
?>
```

This design has many advantages. One of them concerns the use of local variables. Since we have organized our code into functions, variables associated with one task, such as database querying, cannot interfere with variables associated with another task, such as page generation. Without functions, such interference could occur, especially with very commonly used variable names, like $i for loop control variables.

Perhaps the most significant advantage to the design above is that all of the client-side code is now centralized in a few specialized functions. Separating the application logic from the presentation code is extremely beneficial. Changes to either can be made easily without affecting the other (unless you want to). A less obvious benefit of this separation has to do with the built-in header() function. header() can be used to send HTTP header strings, and is very often used to redirect the user to a different PHP program.

For header() to work, it must be invoked before any character is sent to the browser. In a normal (non-function-based) page in which PHP and (X)HTML are interspersed throughout, this could be a problem: by the time you know that you want to call header(), you may have already sent a lot of output to the browser. In our new design, it is very easy for our main() function to determine the flow of execution, including any redirects, well before any client-side code is generated.

Of course, the outline above is a simplified example. In your site, you might have a standard navigation bar at the top of every page. You could create a function that generates the top of a page, and then call this function at the beginning of all of the other displayXxx() functions.

In addition to basic flow control, the main() function has a more subtle role. Through its analysis of the user's action, it is determining the state of the page. If $action has no value, then we know that the user has arrived at the page for the first time, because no submit button was clicked. If $action's value is "View", then we know that the user clicked the "View" submit button from the menu.
