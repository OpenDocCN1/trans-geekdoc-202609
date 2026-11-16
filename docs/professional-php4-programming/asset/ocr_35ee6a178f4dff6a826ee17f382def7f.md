```
CS_ExitMethod("reset");
}
}
?>
```

We have added phpCodeSite functions in the code. The available phpCodeSite functions are listed below:

| Functions | Description |
| :--- | :--- |
| CS_EnterMethod() | Call this function at the start of each function/method with the name of the function or method as the argument. |
| CS_ExitMethod() | Call this function at the end of a function/method or before a return or exit statement. The argument is the name of the function or method. |
| CS_SendError() | To log an error, call this function with an error message as the argument. The message appears in the log prefixed with an [E]. |
| CS_SendNote() | This function logs a simple notification passed as an argument to it. The message appears in the log prefixed with an [N]. |
| CS_SendMessage() | This function logs a simple message passed to it as an argument. The message appears in the log prefixed with an [M]. |
| CS_SendVar() | This method is used to report the value of a variable. The first argument is the name of the variable and the second the value of it. |

Remember to change the argument to the CS_SetEnabled() function at the beginning of Stack1.php to TRUE so that tracing is enabled. On the same note, we can turn off tracing without removing any code by changing the argument to FALSE.

Include stack1.php in the MyStack.php in the place of Stack.php and rename it to MyStack1.php. When you run MyStack1.php the tracing output should look like below:

![](bbox=[0.247, 0.634, 0.727, 0.917])