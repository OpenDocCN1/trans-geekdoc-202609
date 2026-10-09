
# 3

## Working with PHP Functional Programming

In this chapter we will cover the following topics:

- Developing functions
- Hinting at data types
- Using return value data typing
- Using iterators
- Writing your own iterator using generators

### Introduction

In this chapter we will consider recipes that take advantage of PHP's **functional programming** capabilities. Functional, or **procedural**, programming is the traditional way PHP code was written prior to the introduction of the first implementation of **object-oriented programming (OOP)** in PHP version 4. Functional programming is where program logic is encapsulated into a series of discrete **functions**, which are generally stored in a separate PHP file. This file can then be included in any future scripts, allowing the functions that are defined to be called at will.

### Developing functions

The most difficult aspect is deciding how to break up programming logic into functions. The mechanics of developing a function in PHP, on the other hand, are quite easy. Just use the `function` keyword, give it a name, and follow it with parentheses.

#### How to do it...

1. The code itself goes inside curly braces as follows:

```php
function someName ($parameter)
{
    $result = 'INIT';
    // one or more statements which do something
    // to affect $result
    $result .= ' and also ' . $parameter;
    return $result;
}
```

2. You can define one or more **parameters**. To make one of them optional, simply assign a default value. If you are not sure what default value to assign, use `NULL`:

```php
function someOtherName ($requiredParam, $optionalParam = NULL)
{
    $result = 0;
    $result += $requiredParam;
    $result += $optionalParam ?? 0;
    return $result;
}
```

You cannot redefine functions. The only exception is when duplicate functions are defined in separate namespaces. This definition would generate an error:

```php
function someTest ()
{
    return 'TEST';
}
function someTest ($a)
{
    return 'TEST: ' . $a;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_76_0.png)

3. If you don't know how many parameters will be supplied to your function, or if you want to allow for an infinite number of parameters, use `...` followed by a variable name. All parameters supplied will appear as an array in the variable:

```php
function someInfinite(...$params)
{
    // any params passed go into an array $params
    return var_export($params, TRUE);
}
```

4. A function can call itself. This is referred to as **recursion**. The following function performs a recursive directory scan:

```php
function someDirScan($dir)
{
    // uses "static" to retain value of $list
    static $list = array();
    // get a list of files and directories for this path
    $list = glob($dir . DIRECTORY_SEPARATOR . '*');
    // loop through
    foreach ($list as $item) {
        if (is_dir($item)) {
            $list = array_merge($list, someDirScan($item));
        }
    }
    return $list;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_77_0.png)

> Usage of the **static** keyword inside functions has been in the language for more than 12 years. What **static** does is to initialize the variable once (that is, at the time **static** is declared), and then retain the value between function calls within the same request.

If you need to retain the value of a variable between HTTP requests, make sure the PHP session has been started and store the value in `$_SESSION`.

5. Functions are constrained when defined within a PHP **namespace**. This characteristic can be used to your advantage to provide additional logical separation between libraries of functions. In order to *anchor* the namespace, you need to add the **use** keyword. The following examples are placed in separate namespaces. Notice that even though the function name is the same, there is no conflict as they are not visible to each other.

6. We define `someFunction()` in namespace `Alpha`. We save this to a separate PHP file, `chap_03_developing_functions_namespace_alpha.php`:

```php
<?php
namespace Alpha;

function someFunction()
{
    echo __NAMESPACE__ . ':' . __FUNCTION__ . PHP_EOL;
}
```

7. We then define `someFunction()` in namespace `Beta`. We save this to a separate PHP file, `chap_03_developing_functions_namespace_beta.php`:

```php
<?php
namespace Beta;

function someFunction()
{
    echo __NAMESPACE__ . ':' . __FUNCTION__ . PHP_EOL;
}
```

8. We can then call `someFunction()` by prefixing the function name with the namespace name:

```php
include ( __DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_namespace_alpha.php');
include ( __DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_namespace_beta.php');
Alpha\someFunction();
Beta\someFunction();
```

> **Best practice**
> It is considered best practice to place function libraries (and classes too!) into separate files: one file per namespace, and one class or function library per file.
> It is possible to define many classes or function libraries in a single namespace. The only reason you would develop into a separate namespace is if you want to foster logical separation of functionality.
