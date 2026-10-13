
To see how the error handler behaves with a live site, just change this one value.

***

Tip

If your PHP page uses special HTML formatting—like CSS tags to affect the layout and font treatment—add this information to your error reporting function.

***

Tip

Obviously in a live site you’ll probably need to do more than apologize for the inconvenience (particularly if the error significantly affects the page’s functionality). Still, this example demonstrates how you can easily adjust error handling to suit the situation.

***

Tip

If you don’t want the error-handling function to report on every notice, error, or warning, you could check the error number value (the first argument sent to the function). For example, to ignore notices when the site is live, you would change the main conditional to

```
if (!LIVE) {
    echo '<pre>' . $message . "\n";
    debug_print_backtrace();
    echo '</pre><br />';
} elseif ($e_number != E_NOTICE) {
    echo '<div class="error">A system error occurred. We apologize for the inconvenience.</div><br />';
}
```

### PHP Debugging Techniques

When it comes to debugging, what you’ll best learn from experience are the causes of certain types of errors. Understanding the common causes will shorten the time it takes to fix errors. To expedite the learning process, **[Table 8.2](#ch08.html#ch08table02)** lists the likely reasons for the most common PHP errors.

**Table 8.2. Common PHP Errors**

![Image](graphics/08tab02.jpg)

The first, and most common, type of error that you’ll run across is syntactical and will prevent your scripts from executing. An error like this will result in messages like the one in ![Image](graphics/circle-a.jpg), which every PHP developer has seen too many times. To avoid making this sort of mistake when you program, be sure to:

![Image](graphics/08_figure_18_a.jpg)

![Image](graphics/circle-a.jpg)The parse error prevents a script from running because of invalid PHP syntax. This one was caused by failing to enclose `$array['key']` within curly braces when printing its value.

- End every statement (but not language constructs like loops and conditionals) with a semicolon.
- Balance all quotation marks, parentheses, curly braces, and square brackets (each opening character must be closed).
- Be consistent with your quotation marks (single quotes can be closed only with single quotes and double quotes with double quotes).
- Escape, using the backslash, all single-and double-quotation marks within strings, as appropriate.

One thing you should also understand about syntactical errors is that just because the PHP error message says the error is occurring on line 12, that doesn’t mean that the mistake is actually on that line. At the very least, it is not uncommon for there to be a difference between what PHP thinks is line 12 and what your text editor indicates is line 12. So while PHP’s direction is useful in tracking down a problem, treat the line number referenced as more of a starting point than an absolute.

If PHP reports an error on the last line of your document, this is almost always because a mismatched parenthesis, curly brace, or quotation mark was not caught until that moment.

The second type of error you’ll encounter results from misusing a function. This error occurs, for example, when a function is called without the proper arguments. This error is discovered by PHP when attempting to execute the code. In later chapters you’ll probably see such errors when using the `header()` function, cookies, or sessions.

To fix errors, you’ll need to do a little detective work to see what mistakes were made and where. For starters, though, always thoroughly read and trust the error message PHP offers. Although the referenced line number may not always be correct, a PHP error is very descriptive, normally helpful, and almost always 100 percent correct.

#### To debug your scripts

- Turn on `display_errors`.

Use the earlier steps to enable `display_errors` for a script, or, if possible, the entire server, as you develop your applications.

- Use comments.

Just as you can use comments to document your scripts, you can also use them to rule out problematic lines. If PHP is giving you an error on line 12, then commenting out that line should get rid of the error. If not, then you know the error is elsewhere. Just be careful that you don’t introduce more errors by improperly commenting out only a portion of a code block: the syntax of your scripts must be maintained.

- Use the `print` and `echo` functions.

In more complicated scripts, I frequently use `echo` statements to leave me notes as to what is happening as the script is executed ![Image](graphics/circle-b.jpg). When a script has several steps, it may not be easy to know if the problem is occurring in step 2 or step 5. By using an `echo` statement, you can narrow the problem down to the specific juncture.

![Image](graphics/08_figure_19_b.jpg)

![Image](graphics/circle-b.jpg)More complex debugging can be accomplished by leaving yourself notes as to what the script is doing.

- Check what quotation marks are being used for printing variables.

It’s not uncommon for programmers to mistakenly use single quotation marks and then wonder why their variables are not printed properly. Remember that single quotation marks treat text literally and that you must use double quotation marks to print out the values of variables.

- Track variables ![Image](graphics/circle-c.jpg).

![Image](graphics/08_figure_20_c.jpg)

![Image](graphics/circle-c.jpg)Printing the names and values of variables is the easiest way to track them over the course of a script.

It is pretty easy for a script not to work because you referred to the wrong variable or the right variable by the wrong name or because the variable does not have the value you would expect. To check for these possibilities, use the `print` or `echo` statements to print out the values of variables at important points in your scripts. This is simply a matter of

```
echo "<p>\$var = $var</p>\n";
```

or

```
echo "<p>\$var is $var</p>\n";
```

The first dollar sign is escaped so that the variable’s name is printed. The second reference of the variable will print its value.

***

**Using `die()` and `exit()`**

Two functions that are often used with error management are `die()` and `exit()`, (they’re technically language constructs, not functions, but who cares?). When a `die()` or `exit()` is called in your script, the entire script is terminated. Both are useful for stopping a script from continuing should something important—like establishing a database connection—fail to happen. You can also pass to `die()` and `exit()` a string that will be printed out in the browser.

You’ll commonly see `die()` or `exit()` used in an `OR` conditional. For example:

```
include('config.inc.php') OR die ('Could not open the file. ');
```

With a line like that, if PHP could not include the configuration file, the `die()` statement will be executed and the “Could not open the file.” message will be printed. You’ll see variations on this throughout this book and in the PHP manual, as it’s a quick, but potentially excessive, way to handle errors without using a custom error handler.

***

- Print array values.

For more complicated variable types (arrays and objects), the `print_r()` and `var_dump()` functions will print out their values without the need for loops. Both functions accomplish the same task, although `var_dump()` is more detailed in its reporting than `print_r()`.

***

Tip

Many text editors include utilities to check for balanced parentheses, brackets, and quotation marks.

***

Tip
