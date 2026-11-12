Warning: if you try to use a global variable inside a function without declaring it with the global keyword:

```
<?php
$global_variable = "I am a global variable";
function display_global_variable() {
    echo $global_variable;
}

display_global_variable(); // Call function
?>
```

In this case, you'll get an error similar to the following message:

![](bbox=[0.04, 0.53, 0.96, 0.75])

# Local scope

In local scope, variables are declared inside a function and can only be accessed within that function. These variables exist only as long as the function is running, and are destroyed as soon as the function ends. This