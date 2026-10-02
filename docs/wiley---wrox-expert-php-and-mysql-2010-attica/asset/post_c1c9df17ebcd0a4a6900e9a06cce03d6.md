
The final two pieces are to add an entry to the functions table and add a prototype to the headers. Adding the prototype to the header is easy. There is already a macro to expand function definitions so there is just one simple line to add to the header:

```
PHP_FUNCTION(function_name);
```

The semicolon at the end is important because the macro is used both for prototypes in the header and complete function definitions in the extension’s C code.

Assuming that you used one of the generator scripts, you already have a function table. For the helloworld module it would be called helloworld_functions. If helloworld_say is the only function in the extension, the table entry will look like this:

```
const zend_function_entry helloworld_functions[] = {
    PHP_FE(helloworld_say, NULL),
    {NULL, NULL, NULL}  /* Must be the last line in helloworld_functions[] */
};
```

The macro PHP_FE is for a function entry. The preceding one expands to this:

```
{ "helloworld_say", "zif_helloworld_say", NULL,
  (zend_uint) (sizeof(NULL)/sizeof(struct _zend_arg_info)-1), 0 },
```

You may recall the “zif_” value as a prefix added by the PHP_FUNCTION macro. That is because the PHP_FE macro actually uses other macros internally to do its job. One such macro is ZEND_FN, which adds the prefix.

The second parameter to the PHP_FE macro is the arg_info structure. This is covered in the section “Defining Argument Information.”

## Using Arguments

The previous section went over all the parameters to PHP function calls. However, they can all be safely forgotten for most extensions. The first step with any function is to parse the parameters into usable values. For that there is a helper function.

The function zend_parse_parameters takes arguments specifying the number of parameters to expect, the signature of the parameters, and pointers, and in turn stores all of them for easy retrieval. Additionally, it has the ability to validate the parameters against data types. If the user calls it with an invalid number of arguments or an argument of an incompatible type it will issue a warning and return FAILURE.

The function looks like this:

```
char *name;
int name_len;

if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s",
    &name, &name_len) == FAILURE) {
    RETURN_NULL();
}
```

You saw the ZEND_NUM_ARGS macro earlier. The second argument (actually, the third, but there will be more on that later) is for the parameters. There is one character per parameter and it indicates the type. For example, the preceding function accepts a string. If it were to accept two strings it would look like “ss” instead.

The valid values are:
- Array (a) as zval **
- Boolean (b) as zend_bool *
- Double (d) as zval **
- Long (l) as zval **
- Object (o) as zval **
- Object of a specific class (o) as zval ** and zend_class_entry *
- String (s) as char ** and int *
- Zval (z) as zval **
- Zval reference (z) as zval ***

Additionally, a few other options are available. It is easy to make arguments optional simply by specifying a pipe. Everything after the pipe is optional. Now would be a good time to demonstrate how to accept the arguments for the helloworld_say function that you have seen so many times in this chapter:

```
char *name;
int name_len;
zend_bool do_return;

if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "s|b",
    &name, &name_len, &do_return) == FAILURE) {
    ...
}
```

Return values from functions are covered later. You may have noticed that there are three remaining parameters. They are used to store the values passed into the function. Strings take two variables (to deal with binary data) while most others only take one.

All parameters are passed as pointers to the original zval. The Zend engine does not make copies (or references) unless you explicitly ask it to. As a result, changes made to the zval will change the original in PHP. In order to perform calculations on the value without affecting the outside data it is necessary to make a copy.

Separation is the process of taking one zval and creating a new one that is initially a reference to the first; however, it will dereference and create a new value if you try to write to it. In PHP 5 it can be done implicitly by flagging the argument for separation. To flag a value for separation you can put a slash (/) after it.

So what happens when you pass a value that isn’t a string to a function that only accepts “s” as a type of value? There are two possible outcomes. If the value can be safely converted to a string without data loss, then PHP will do it. That includes longs, doubles, and Booleans. If it can’t be converted without losing any data (object, arrays, and resources), PHP will print a warning and the parameter parsing function will return FAILURE.

Alternatively, it is possible to accept a zval instead and convert to a string. Say that you have a function foo() that expected a string. You could do something like this:

```
zval *my_str;

if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "z", &my_str) == FAILURE) {
    RETURN_NULL();
}
convert_to_string( my_str );
```

There are a few problems with this code. The first is that convert_to_string issues a warning if you pass an array — or anything else that can’t be converted to a string without data loss — to the function. The second is that, because all values are passed to the extension as a pointer to the original variable in PHP, the code will change the value of the variable in PHP. Take this code, for example:

```
<?php
$bar = array( 1, 2, 3 );
helloworld_foo($bar);
echo '$bar IS '.(is_array($bar) ? '' : 'NOT ').'an array.';
?>
```

Using the parameter parsing code from before, this code will print $bar IS NOT an array. At that point $bar is equal to the string literal Array instead of the original actual array.

That is where separation comes in. There are two ways to do separation of parameters in PHP5. They both work fine; one is just newer and a little bit less code. The following pieces of code are functionally identical. One way is:

```
zval **my_str;
if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "Z", &my_str) == FAILURE) {
    RETURN_NULL();
}
SEPARATE_ZVAL_IF_NOT_REF(my_str);
```

Another way is:

```
zval *my_str;
if (zend_parse_parameters(ZEND_NUM_ARGS() TSRMLS_CC, "z/", &my_str) == FAILURE) {
    RETURN_NULL();
}
```

The biggest difference is that one requires that the zval be a double pointer and the other method requires a single pointer. Both options separate the value only if it is not a reference, which means that if the user does this:

```
$foo = "world";
helloworld_say( &$foo );
```

it will not get separated. The end result is that any changes you make to the zval inside of the function still affect the original variable in memory. This is a problem that affects a good number of extensions and even some built-in functionality. The way to avoid that is by using the SEPARATE_ZVAL macro instead of its conditional equivalent.

## Defining Argument Information

The arg_info is the second argument to the PHP_FE macro. It provides information about the arguments for a function, which in turn can be used with the PHP inspection APIs and is new in PHP 5. As a result, ext_skel does not use it (as of PHP 5.3) but CodeGen_PECL does. So, if you were to add arguments you would define the argument list in the header file:

```
#if (PHP_MAJOR_VERSION >= 5)
ZEND_BEGIN_ARG_INFO_EX(helloworld_say_arg_info, ZEND_SEND_BY_VAL,
    ZEND_RETURN_VALUE, 1)
    ZEND_ARG_INFO(0, name)
    ZEND_ARG_INFO(0, return)
ZEND_END_ARG_INFO()
#else /* PHP 4.x */
#define helloworld_say_arg_info NULL
#endif
```

The arguments for the highlighted macro are, in order:
- The first argument is the name of the variable to store the information in. Do not define the variable ahead of time because the macro does it for you.
- The second flag indicates how the user should pass the additional arguments in a variable argument function. The most common and recommended value is ZEND_SEND_BY_VAL. You also have ZEND_SEND_BY_REF and ZEND_SEND_BY_PREFER_REF; however, they are rarely used and usually the sending by value is the right flag.
- The third is whether the return value is by value or reference. Just like the argument list there is a way to return by reference but it is not used very often. If you are returning by reference, odds are that you really want to create a new resource type.
- The final argument is the number of required arguments. In the preceding example there are two arguments, but only one is required.

After the argument information is started it is time to define individual arguments using ZEND_ARG_INFO. The macro is fairly self-explanatory. The first is a 1 or 0 depending on whether the argument should be passed by reference. The second is the name of the argument. The argument names should not be quoted (the macro does that for you).

Documentation systems and some extensions rely on being able to inspect functions, so a valid argument list is very helpful. Once the list is complete it can be passed to the PHP_FE macro as the second argument.

## Returning Values

Once you have your function set up and your parameters are being passed, returning a value back to PHP is the easy part. The return set of functions is analogous to the zval assignment macros. As a general rule, if you can assign to a zval with a macro you can return a value with a similar macro.
