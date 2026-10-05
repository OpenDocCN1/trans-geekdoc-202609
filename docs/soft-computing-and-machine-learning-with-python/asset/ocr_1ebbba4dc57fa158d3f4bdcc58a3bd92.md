# A Python 2.7 Programming Tutorial 215

```
47 48 3.5
>>> f(47, 48, 29)
47 48 49
>>> f(47, 48, 49, 50)
Traceback (most recent call last):
File "stdin>", line 1, in =
TypeError: f() takes at most 3 arguments (4)
>>>
```

Here is another feature: the caller of a function can supply what are called keyword parameters of the form "name=value". If the function has an argument with a matching keyword, that argument will be set to value.

+   - If the caller's caller supplies both positional and keyword parameters, all positional parameters must precede all keyword parameters.
- Keyword parameters may occur in any order.
- Here are some examples of calling a function with keyword parameters.

```
>>> g(p0, p1, k0="K-0", k1="K-1")
...\    print p0, p1, k0
>>> g(33,44)
33 44 K-0 K-1
>>> g(33,44,"K-9","beep")
33 44 K-9 beep
>>> g(55,66,k1="whirr")
55 66 K-0 whirr
>>> g(7,8,k0="click",k1="clank")
7 8 clank clank
>>>
```

# Extra Positional Arguments

You can declare your function in such a way that it will accept any of positional parameters. To do this, use an argument of the form "*name" in your argument list.

+   - If you use this special argument, it must follow all the positional and keyword parameters in the list.
- When the function is called, this name will be bound to a tuple containing any positional parameters that the caller supplied, and over above parameters that corresponded to other parameters.