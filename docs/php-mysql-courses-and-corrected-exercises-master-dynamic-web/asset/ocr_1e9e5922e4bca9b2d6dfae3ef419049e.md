```
global $global_variable;
echo $global_variable;
}
display_global_variable(); // Call function
?>
```

In this example, $global_variable is a global variable because it is declared outside any function. It can be used inside the display_global_variable() function, but only if the global keyword is used.

It's important to note that the use of global variables can make code less readable and more difficult to maintain, as they can be modified unpredictably at different points in the script. It is therefore recommended to limit the use of global variables.

Executing this code displays the result:

![](bbox=[0.039, 0.611, 0.959, 0.91])