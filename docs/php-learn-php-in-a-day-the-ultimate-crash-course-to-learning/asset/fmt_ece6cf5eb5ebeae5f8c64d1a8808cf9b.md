
In this case, the variable `$var` can be used by any code that is included inside of `functions.php`. The context of a variable, however, changes when we create our own functions.

Within user-defined functions a local function scope is introduced. Any variable used inside a function is by default limited to the local function scope. For example:

![](images/00074.jpeg)

This script will not produce any output because the `echo` statement refers to a local version of the `$a` variable, and it has not been assigned a value within this scope. You may notice that this is a little bit different from the C language in that global variables in C are automatically available to functions unless specifically overridden by a local definition. This can cause some problems in that people may inadvertently change a global variable. In PHP global variables must be declared global inside a function if they are going to be used in that function.

Let’s look at how to declare variables as global.

![](images/00075.jpeg)

## Pre-defined functions

PHP comes built with many pre-defined functions and this is what makes PHP so efficient and useful. We cannot possibly examine all of the PHP functions as this will take another book itself (currently, the PHP documentation lists 9457 built in functions.). Let’s start with the most basic functions that can be used inside of PHP.

### Echo, Print, exit, die

#### Echo

`Echo` is the language construct in PHP that allows us to output string data. PHP will automatically convert numerical variables to strings. We’ve already used `echo` in previous examples in this book, so you should be familiar with this function by now.

#### Print

`Print` is another language construct that does the same thing as `echo`, but it is older and a bit slower. Therefore, it is usually better to use `echo`.

A function that is not exactly related to print but shares enough of the name for us to place it here, is the `print_r()` function. This function allows us to print the contents of an array to the screen.

#### Exit and Die

These functions allow you to print out a message to the screen and terminate the script. The two functions are equivalent to one another and you can use whichever. The syntax for both is:

![](images/00076.jpeg)

### String functions

PHP comes with a wide range of functions for string manipulation.

#### Word count

PHP comes with a pre-built function that will count the number of words in a string for you. It is of the following form:

![](images/00077.jpeg)

The second argument of the function is optional and can take 3 values. Here are the supported values and the result returned from each:

*   **0** - returns the number of words found
*   **1** - returns an array containing all the words found inside the `string`
*   **2** - returns an associative array, where the key is the numeric position of the word inside the `string` and the value is the actual word itself

The function takes a third optional argument that we didn’t specify here. The third parameter is a list of additional characters that you want to be considered as words. You just put the symbols next to each other in a string with no other formatting.

#### String Shuffle

This function allows you to randomly shuffle the characters inside of a string. This comes in handy if you want to create pseudo-unique names for files or something like that.

![](images/00078.jpeg)

#### Replace parts of a string

PHP has a number of different functions that can help you with this. The simplest one is the `str_replace()` function. It takes the form:

![](images/00079.jpeg)

The arguments can be strings or arrays. If `needle` and `replacement` are arrays, then `str_replace()` takes a value from each array and uses them to search and replace on `haystack`. If `replacement` has fewer values than `needle`, then an empty string is used for the rest of replacement values. If `needle` is an array and `replacement` is a string, then this replacement string is used for every value of `haystack`. The converse would not make sense, though.

There is an optional fourth argument that could be passed which will be set to the number of replacements performed.

There is a modification to the `str_replace` function that will replace without regard to case. In other words, it will do a case-insensitive replace. This function is called `str_ireplace` and takes the same arguments.

#### String length

There are a number of functions in PHP that will return the length of a string. The simplest to use is the following:

![](images/00080.jpeg)

Another function you can utilize to do this is the `mb_strlen()`;

![](images/00081.jpeg)

This function has an optional parameter which is the encoding of the string. For example, if you want to set the encoding to UTF-8, you just provide the string `'UTF-8'`. PHP supports numerous encoding types which you can easily find by going to the official PHP manual.

Another way to count the number of characters is to use the `iconv_strlen()` function. It works very much like the `mb_strlen()` function and takes the same parameters, except it is a lot stricter when it comes to bad sequences inside your string.

The reason for the different functions is that they actually count different things. `strlen()` counts the number of bytes inside of a string. Usually a character is equivalent to one byte, but that is not always the case. This is why the other functions exist.

Sometimes you will find that you have a string that has unneeded whitespace at the end of it. To get rid of whitespace on both sides of a string, you can use the `trim()` function. A useful feature of the `trim()` function is that it can trim not only whitespace but any additional characters that you specify. Alternatively, if you only want to trim from the left or the right, there are the `ltrim()` and `rtrim()` functions.

![](images/00082.jpeg)

#### Finding substrings in a string

The simplest way to return a part of a string is to use the `substr()` function. This function takes two required parameters and one optional parameter. The first parameter is the string that you are referencing. The second parameter is the start of the portion of the string. This parameter can be either positive or negative. If positive, the returned string will be the string that starts from the specified location within the main string. If negative, the returned string will start from the end of the main string. The third parameter is optional and is the length of the string you want returned. It can also be positive or negative. If it is positive, the returned string will contain at most, that number of characters. If the value is negative, the value specifies how many characters will be omitted from the main string. Here are examples:

![](images/00083.jpeg)

If you want to find the number of times a string occurs inside another string you can use the `substr_count()` function. This function takes two required parameters and two optional parameters. Here is the syntax for the function and some examples on how to use it in your own code:

![](images/00084.jpeg)

The first parameter is the string to check. The second parameter is the string to search for. The third parameter specifies where in the string to start searching. The third parameter specifies the length of the search.

![](images/00085.jpeg)

Another function that finds a substring inside a larger string is the `strpos()` function. This function finds the position of the first occurrence of a string inside another string. Let’s look at the syntax for the function as well as a couple of different examples to understand it:

![](images/00086.jpeg)

The first parameter is the string to check. The second parameter is the string to search for. The third parameter specifies where in the string to start searching.

![](images/00087.jpeg)
