
Note

Since PHP 8, it is already possible to define `null` as one of the types in a union type declaration. This is a syntactic alternative to the type declaration with the preceding `?` from the previous section. This means that `int|null` corresponds to `?int`.

## Intersection and DNF Types

Intersection types are new since PHP 8.1, and disjunctive normal form (DNF) types are new in PHP 8.2, extending the capabilities of union types.

Intersection types are not intended for scalar types such as strings, integers, and the like, but only for class types. They allow different class types to be combined using an ampersand (`&`) to check the type:

```
function functionname(): type1&type2 {
```

The DNF types extend PHP from version 8.2 with the option of combining union types and intersection types. Here, an intersection type is one of several options within a union type. In the following example, the return of the function can therefore be an integer, a string, or an object of `type1` or `type2`:

```
function functionname(): (type1&type2)|int|string {
```

The following example is an excerpt from the full script.

```
function sum(int|string|float ...$a): (type1&type2)|int|float {
```

**Listing 6.28 DNF Types Allow a Wild Mix ("dnf_types.php")**

### Type Declaration with Mixed

The `mixed` type is new in PHP 8 and is used when you cannot or do not want to specify a type, but still want to make a type declaration.

Basically, `mixed` means nothing other than that any type can be passed or returned here. If you were to write this as a union type, it would look like this:

```
array|bool|callable|int|float|object|resource|string|null
```

The following example shows this for our example function for adding up parameters.

```
function sum(mixed ...$a): mixed {
    return array_sum($a);
}

$result = sum(1, '2', 3.7);
var_dump($result);
```

**Listing 6.29 Type Declaration with Different Types ("type_declaration_mixed.php")**

**Tip**
Because PHP automatically allows any type in PHP 8 even when the type declaration is omitted, the question arises as to why mixed is necessary at all. There is a fundamental decision behind this: if you consistently use typing, there are still sometimes cases in which you cannot or do not want to specify the type. In this case, you use mixed to mark precisely these occurrences.

### Type Declaration with Never

The never type is new since PHP 8.1 and is a pure return type that indicates that the function does not end and therefore returns nothing. This means that the function must either be exited with exit() or an infinite loop or exception is generated.

```
<?php
function output(string $a): never {
    echo $a;
    exit();
}
$result = output('output');
?>
```

**Listing 6.30 Type Declaration for a Function Return with "never" ("never.php")**

**Note**
If exit() was missing in the preceding script, the result would be a fatal error.

## 6.1.8 Enumerations

Enumerations, often referred to as enums for short, are lists that specify which values are possible for a parameter, a return value, or another type of datum. In development, they also occur at the database level and describe which values a data field can take. They have been available in PHP since version 8.1. They are mainly used in object-oriented development but can also be used for function types.

The notation is very simple. The keyword is enum, followed by the name. The individual values are declared with the case keyword:

```
enum values
{
    case case1;
    case case2;
    case case3;
    case case4;
}
```

A value is then accessed using the double colon notation:

```
$value = values::case3;
```

Used completely, it looks like the following. The enum is specified as a type in the function call for the respective function parameter:

```
function output(values $parameter) {
```

The parameter can then be used in the function. In the following simple example, a switch case distinction accesses the individual values and executes an output in each case.

```
<?php
enum values
{
    case case1;
    case case2;
    case case3;
    case case4;
}
```

```
function output(values $parameter) {
switch ($parameter) {
    case values::case1:
        echo "case1";
        break;
    case values::case2:
        echo "case2";
        break;
    ...
}
}
```

```
$value = values::case3;
output($value);
?>
```

**Listing 6.31 Enumerations Define Fixed Values ("enumerations.php")**

### Enumerations with Scalar Values

Enumerations are also available in a combination with scalar values; the technical term for this is backed enums. Here, either an integer or a string is assigned to the enumeration as a value.

This is always practical when the enums are used to convert data fields from a database or an import because the data fields there often have simple scalar values.

The declaration is again simple. The enum is supplemented by a type declaration—that is, int or string. You define the values in the individual cases:

```
enum values : int
{
    case case1 = 1;
    case case2 = 2;
    case case3 = 3;
    case case4 = 4;
}
```

To access the correct case with the scalar values, PHP offers two methods for enums:

- from(value) returns the matching enum case for the scalar value. If the value does not exist, PHP throws a ValueError.
- tryFrom(value) basically does the same thing, except that it returns zero if a value does not exist. This variant is therefore suitable if, for example, unreliable values can also come from the data source and a separate error handling function is to be implemented.

In the following example, case2 is output.

```
<?php
enum values : int
{
    case case1 = 1;
    case case2 = 2;
    case case3 = 3;
    case case4 = 4;
}

function output(values $parameter) {
    ...
}

$value = values::from(2);

output($value);
?>
```

**Listing 6.32 Enumerations with Scalar Values ("enumerations_scalar.php")**

## 6.1.9 Helpful and Useful Information

This section summarizes some interesting help functions and code snippets that are needed from time to time.

### Test Functions

If you use functions, you should also check whether a function exists, especially for more extensive scripts. This is also important if you are using an external function from a library, for example.

The simplest approach would look like this:

```
if (output()) {
    echo output();
}
```

Unfortunately, this check fails if the function does not exist (see Figure 6.18). In this respect, it is unacceptable.

![](img/ae7820c36e8f24c1623d26668b28e80e_186_0.png)

Figure 6.18 The Function Does Not Exist

The check works better with the `function_exists(function_name)` auxiliary function. It receives the function name as a parameter and returns a truth value. In the following lines, the function is only executed if it exists:

```
if (function_exists("output")) {
    echo output();
}
```

**Tip**
You can also test the data type with the exact equality for strings:

```
if (function_exists("output") && output() == "") {
    echo output();
}
```

### "isset()"

The isset(Parameter) function is already familiar to you from variables. It checks whether a variable has been declared. You can also use this function within functions for their parameters. For parameters that have the value NULL (no value), isset() sees them as not set and therefore returns false. An empty string (""), on the other hand, is set.

```
function output($par = NULL) {
    if (isset($par)) {
        return "Hello $par";
    } else {
        return "Hello without parameters";
    }
}
$return = output();
echo $return;
```

**Listing 6.33 "isset()" ("isset.php")**

The preceding script returns hello without parameters, as the parameter has not been set and therefore the default value NULL is used.

> **Note**
> Caution: If the default value is not set to NULL, then the PHP interpreter will generate a warning because the parameter does not exist!

### "create_function()"

The create_function(parameters, statements) helper function is only available up to PHP 7.3. In PHP 8, it has been abolished as the anonymous functions provide a useful alternative. This means that even with older PHP versions it is better not to use it.

If you stumble across the function in old code, you will usually see it being used when dynamically creating a function without a function name (see Figure 6.19). This procedure is also called _lambda style_. Dynamically created functions are useful if code or parameters are to change during program execution (runtime).

```
<?php
$function = create_function('$par', 'echo "Hello " . $par;');
$function("World");
?>
```

**Listing 6.34 "create_function()" ("create_function.php")**
