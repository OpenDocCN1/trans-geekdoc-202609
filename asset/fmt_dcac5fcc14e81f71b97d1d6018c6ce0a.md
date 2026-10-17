
The online version of the documentation is organized according to categories. Two of the most useful are string functions and array functions. To access the documentation quickly from Dreamweaver, click the link at the top of the page that is displayed with the code hints to go to the same page in the online documentation. Click the link for related functions in the navigation menu on the left of the page to view a useful page with a one-line description of each function.

Visiting the PHP online manual like this is a good way to learn more about PHP.

![Image](img/fig03_14.jpg)

### Creating your own functions

With so many functions in core PHP, the idea of creating your own might sound odd. But this is what makes languages like PHP so powerful. Building your own functions is a way of combining existing functions to fit your needs. If you have a routine that needs to be repeated several times, a custom function saves time and effort. It also helps reduce mistakes. Once you have created and tested a function, you can use it repeatedly and be confident that it will always work the same way—and if there’s an error, you need to correct it in only one place.

You define a function with the `function` keyword, followed by the name of the function, and a pair of parentheses. Any arguments go between the parentheses as a comma-separated list, and the code that you want the function to execute goes between a pair of curly braces.

You can name a function anything you like, following the same rules as a variable. It should contain only alphanumeric characters and the underscore, and shouldn’t begin with a number. You also must avoid using the name of an existing function.

#### TIP

If you choose a name that is already in use, PHP generates an error message telling you that you cannot redeclare the function of that name.

You saw how `strtoupper()` converts a string to uppercase. Another function called `strrev()` reverses the order of a string. Let’s say that for some mad reason you need to reverse text and display it in uppercase. The PHP code in `function_03.php` passes a variable containing the title of this book first to `strrev()` and then to `strtoupper()` like this:

```
$title = 'Adobe Dreamweaver CS5 with PHP';  
echo $title;  
$title = strrev($title);  
echo $title;  
$title = strtoupper($title);  
echo $title;
```

This does the job as expected.

![Image](img/fig03_15.jpg)

If you need to do this repeatedly, you can modularize your script as a function like this:

```
function upBack($text) {  
  $text = strrev($text);  
  echo strtoupper($text);  
}
```

Then all that’s necessary is to pass the value to `upBack()` as an argument like this:

```
upBack($title);
```

#### NOTE

This example is for illustrative purposes only. Using `echo` in a function is generally considered bad practice. You should normally return a value from a function as described next.

You can find the code in `function_04.php`. If you examine the page in Code view, you’ll see that the function definition is at the bottom of the page, way after the function has already been used. As long as the function definition is in the same page, it doesn’t matter where you define it, so it’s often convenient to keep all function definitions together rather than mix them in with the rest of the script.

This function automatically displays the converted string, so the original value is preserved. However, to assign the result to a variable, you need to use the `return` keyword like this:

```
function upBack2($text) {  
  $text = strrev($text);  
  return strtoupper($text);  
}
```

The code in `function_05.php` reassigns the value of `upBack2($title)` to the `$title` variable like this:

```
$title = upBack2($title);
```

As a result, `$title` now contains the value returned from `upBack2()`, permanently changing the string.

![Image](img/fig03_16.jpg)

### Understanding Variable Scope

Functions act rather like a black box. What happens inside the box is invisible to everything outside. Normally, when you pass a variable as an argument to a function, only the value is passed to the function. In the case of `upBack2()`, the value is passed as an argument to `$text`. Once the function completes its task, `$text` ceases to exist, and it is created again only if the function is reused.

The *scope* of a variable—in other words, where it can be used—depends entirely on where the variable is defined. A variable defined in a function or as one of its parameters is limited in scope to that function. It cannot be seen outside the function. Equally, a function has no knowledge of or influence over variables outside. In the example in `function_06.php`, there’s no cause for confusion, because the external and internal variables have different names.

However, what happens if both variables have the same name? In `function_07.php`, `$title` has been changed to `$text`, and it’s passed as an argument to `upBack2()`. If you test the page, you’ll see the value of `$text` that was declared outside the function remains unchanged.

![Image](img/fig03_17.jpg)

In a small script, it’s easy to keep track of variable names. But as your project grows, you could easily end up reusing the same name for a variable that’s used inside a function. By keeping the internal working of functions separate from everything else, variable scope reduces the need to worry about names clashing.

This change in the value of `$title` comes about only through capturing the return value. Forgetting to capture the return value of a function is a common beginner’s mistake. The code in `function_06.php` shows what happens when the return value of `upBack2($title)` is not assigned to a variable.

![Image](img/fig03_18.jpg)

As soon as a function encounters the `return` keyword, it processes the rest of the line and returns the value. Any other code inside the function is ignored.

### Using Objects and Resources

The name “object” comes from *object-oriented programming* (OOP), a practice common in most modern programming languages. As projects get bigger, code becomes more complex. Mistakes become not only more likely, but also more difficult to detect. OOP tackles this problem by breaking down complex tasks into simple units—the idea being that small units of code are easy to maintain. Once a unit has been tested, you know it will produce reliable results.

OOP also promotes the reuse of code, so you’re not constantly reinventing the wheel. The code that defines an object’s features is called a *class*, which can be regarded as a blueprint for making objects. Some classes are built into core PHP, but you can also create your own, or use a third-party class library, such as the Zend Framework. What makes OOP attractive and powerful is that most classes can be extended, and the new class inherits all the features of its parent. As a result, objects are becoming an increasingly important part of PHP.

PHP is not an object-oriented language, but it does have strong support for OOP. Since the release of PHP 5 in 2004, many classes have been built into the language, and the Zend Framework that you will use later in this book is written entirely in OOP. At this stage, all you really need to know about objects is what they are and how to use them.

In practical terms, an object is a variable capable of storing multiple values—called *properties*—in the same way as an associative array. An object also has access to functions—called *methods*—that are directly associated with it.

#### Creating an object

You create—or *instantiate*—an object in a similar way to assigning the return value of a function to a variable. The function that creates an object is known as a class *constructor*. Like a function, the constructor may take a number of arguments. The difference is that the constructor is preceded by the keyword `new`.
