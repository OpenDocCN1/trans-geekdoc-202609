```
counter();
counter();
counter();
?>
```

In this example, the $counter variable is declared as static inside the counter() function, using the static keyword. Each time the counter() function is called, the $counter variable is incremented by 1 and its value is retained between successive calls to the function. In this way, each call displays the total number of function calls, which is incremented with each call.

![](bbox=[0.04, 0.44, 0.96, 0.82])

In short, variable scope in PHP is an essential concept that determines where and when a variable can be used in a script. In the foregoing, we've looked at three types of variable scope: global, local and static.