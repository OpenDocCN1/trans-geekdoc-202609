# The function call

```
create_table($my_data, 'I would like this to be the caption');
```

is perfectly legal and results in $header set to 'I would like this to be the caption' and $caption being set to the default, that is, NULL.

One workaround is to pass in NULL as the header, as follows:

```
create_table($my_data, NULL, 'I would like this to be the caption');
```

You can consider functions that accept a variable number of parameters. You can find out how many parameters are passed and what their values are with the aid of three functions: $func_num_args(), $func_get_arg(), and $func_get_args().

For example, consider this function:

```
function var_args() {
    echo 'Number of parameters:';
    echo $func_num_args();

    echo '<br />';
    $args = func_get_args();
    foreach ($args as $arg) {
        echo $arg.'br />';
    }
}
```

This function returns the number of parameters passed to it and prints out each of them. The $func_get_args function returns the number of arguments passed. Alternatively, you can access the arguments one at a time using the $func_get_arg() function, passing the argument number you want to access. (Arguments are numbered starting from zero).

# Understanding Scope

You might have noticed that when we needed to use variables inside a required or included file, we simply declared them in the script before the require() or include() statement. When using a function, we explicitly passed these variables into the function because no mechanism exists for explicitly passing variables to a required or included file or because variable scope behaves differently for functions.

A variable's scope controls where it is visible and usable. Different programming languages have different rules that set the scope of variables. PHP has fairly simple rules:

+   - Variables declared inside a function are in scope from the statement in which they are declared to the closing brace at the end of the function. This is called function scope. These variables are called local variables.

+   - Variables declared outside functions are in scope from the statement in which they are declared to the end of the file, but not inside functions. This is called global scope. These variables are called global variables.