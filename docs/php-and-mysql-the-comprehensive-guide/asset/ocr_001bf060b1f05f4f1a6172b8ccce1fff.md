> > Note
> The type conversion from float to int is not rounded; instead, the decimal places are discarded! Therefore it is deprecated.

![](bbox=[0.145, 0.2, 0.756, 0.43])

Figure 6.13 Thanks to Type Conversion, The Output Returns an Integer with the Value "6" – But Also Shows It's Deprecated

If you vary the script shown previously and use `float` instead of `int` for the parameters and for the return, then 6.7 is output as `float` (see Figure 6.14):

```
function sum(float ...$a): float {
    return array_sum($a);
}
```

![](bbox=[0.145, 0.612, 0.726, 0.772])

Figure 6.14 If "float" Is Specified for Parameter and Return, the Result Is "6.7"

# Strict Typing

By default, PHP converts the type automatically. However, this can sometimes lead to errors in your own programming, which are difficult to find in debugging. For this