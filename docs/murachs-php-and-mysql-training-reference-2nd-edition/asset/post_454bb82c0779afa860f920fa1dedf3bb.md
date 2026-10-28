
## The Product Discount application with a logic error

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_216_0.png)

### The goal of testing

- To find all errors before the application is put into production.

### The goal of debugging

- To fix all errors before the application is put into production.

### Three test phases

- Check the user interface to make sure that it works correctly.
- Test the application with valid input data to make sure the results are correct.
- Test the application with invalid data or unexpected user actions. Try everything you can think of to make the application fail.

### The three types of errors that can occur

- *Syntax errors* violate the rules for how PHP statements must be written. These errors cause the PHP interpreter to display an error and to stop execution of the script.
- *Runtime errors* don’t violate the syntax rules, but they cause the PHP interpreter to display an error that may or may not stop execution of the script.
- *Logic errors* are statements that don’t cause syntax or runtime errors, but produce the wrong results.

### Description

- To *test* a PHP application, you run it to make sure that it works properly no matter what combinations of valid or invalid data you enter or what sequence of controls you use.
- When you *debug* an application, you find and fix all of the errors (*bugs*) that you find when you test the application.

Figure 6-1    An introduction to testing and debugging

## Common PHP errors

Figure 6-2 presents some of the coding errors that are commonly made as you write a PHP application. By now, you probably have made most of these errors as you’ve done the exercises. But if you study this figure, you’ll have a better idea of what to watch out for.

The code at the top of this figure checks the price entered by a user. However, this code has three errors. The first one is in the first line. Here, the assignment operator (=) is used to check equality instead of the equality operator (==). The second error is the string literal that starts with a double quote and ends with a single quote. The third error is the statement in the else clause that doesn’t end with a semicolon.

The NetBeans editor in this figure shows how this code is displayed by that IDE. Here, the error marks (red circles) to the left of statements indicate syntax errors. In this example, the cursor is over one of these error marks so the related error message is displayed.

Note, however, that these error marks aren’t on the statements that are in error. This shows that some errors aren’t correctly identified by NetBeans. In that case, you need to look at the statements above the error marks to see what code might be causing the errors. As you fix those errors, the error marks on the statements below will disappear. In most cases, though, NetBeans will mark your errors as you enter a statement so you can correct them right away.

### PHP code that contains errors

```php
// validate the list price entry
if ( $list_price = NULL || $list_price == FALSE ) {
    $error = "Please enter a valid number.';
} else {
    $error = ''
}
```

### The PHP code that contains errors in NetBeans

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_218_0.png)

### Common syntax errors

- Misspelling keywords.
- Forgetting an opening or closing parenthesis, bracket, brace, or comment character.
- Forgetting to end a PHP statement with a semicolon.
- Forgetting an opening or closing quotation mark.
- Not using the same opening and closing quotation mark.

### Problems with variable names

- Misspelling or incorrectly capitalizing a variable name.
- Using a keyword as a variable name.

### Problems with values

- Not checking that a value is the right data type before processing it. For example, you expect the user to enter a number, but the user enters a name instead.
- Using one equal sign instead of two when testing for equality.

Figure 6-2  Common PHP errors

## An easy way to trace the execution of your PHP code

When you *trace* the execution of an application, you add statements to your code that display messages or variable values at key points in the code. This is typically done to help you find the cause of a logic error.

If, for example, you can’t figure out why the future value that’s calculated by the Future Value application is incorrect, you can insert echo statements into the code for the application as shown in figure 6-3. These statements display the values for two of the variables as the code in the for loop is executed. That should help you determine where the calculation is going wrong. Then, when you find and fix the problem, you can remove the echo statements.

In this example, the tracing statements show that the loop was executed the right number of times. It also shows the future value after each time through the loop so you can make sure the calculation within the loop is correct. In this example, the value of an investment of $10,000 at 5% after the first year is $60,000 so it’s obvious that the calculation within the loop is wrong, not the number of times through the loop.

When you use this technique, you usually start by adding just a few echo statements to the code. Then, if that doesn’t help you solve the problem, you can add more. This works well for simple applications, but has its limitations. In the next few figures, then, you’ll learn how you can use an IDE like NetBeans to get the same result without having to write and then remove echo statements.

### PHP with echo statements that trace the execution of the code

```php
// calculate the future value
$future_value = $investment;
echo '$future_value: ' . $future_value . '<br>';
echo '$interest_rate: ' . $interest_rate . '<br>';
echo '$years: ' . $years . '<br>';
echo 'For loop for calculating future value is starting...<br><br>';
for ($i = 1; $i <= $years; $i++) {
    $future_value = ($future_value + ($future_value * $interest_rate));
    echo '$i: ' . $i . '<br>';
    echo '$future_value: ' . $future_value . '<br>';
}
```

### The data displayed in a browser

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_220_0.png)

### Description

- An easy way to trace the execution of a PHP application is to insert echo statements at key points in the code.
- The echo statements can display the values of variables or display messages that indicate what portion of the code is being executed.
- When you see an incorrect value displayed, there is a good chance that you have a logic error between the current echo statement and the previous one.

Figure 6-3 — An easy way to trace the execution of your PHP code

## How to debug with xDebug and NetBeans

XAMPP includes a powerful debugging tool, or *debugger*, named xDebug that you can use with an IDE such as NetBeans. Before you can use xDebug with NetBeans, however, you must configure xDebug as described in the appendix.

The topics that follow show you how to use this debugger with NetBeans. If you aren’t using NetBeans, you can of course skip these topics. But if you’re interested in what an IDE can do, you may want to read them anyway.

### How to set and remove breakpoints

The first step in debugging an application is to figure out what is causing the bug. To do that, it’s often helpful to view the values of the variables at different points in the application as it’s executing. This helps you determine the cause of the bug, which is critical to debugging the application.

The easiest way to view the variables at a particular point in an application is to set a *breakpoint* as shown in figure 6-4. To do that, you click on the vertical bar to the left of a line of code in the code editor window. Then, the breakpoint is marked by a red square in the bar. Later, when you run the application with the debugger, execution stops before executing the statement at the breakpoint, and you can view the variables that are available at that point in the application.

When debugging, it’s important to set the breakpoints before the line or lines that are causing bugs. Sometimes, you can decide where to set a breakpoint by reading the runtime error that’s displayed in the browser when your application stops. Other times, you may need to experiment a little before finding a good location for a breakpoint. In the example in this figure, the breakpoint is set on the statement before the for loop in the Future Value application.

After you set the breakpoint, you need to run the application with the debugger attached. To do that, you can use the Debug Project button that’s available from the toolbar (just to the right of the Run Project button). Or, if you want to debug a project that isn’t the main project, you can right-click on the project folder in the Projects tab and select the Debug command.

When you run an application with the debugger, NetBeans displays the debugging windows and buttons that are shown in the next figure. After you run the application with the debugger, the breakpoints remain where you set them. If you want to remove a breakpoint, you can do that by clicking on the red square for the breakpoint.
