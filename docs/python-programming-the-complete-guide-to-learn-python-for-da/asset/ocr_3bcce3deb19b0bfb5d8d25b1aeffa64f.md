```
>>> b = 'house'
>>> id (a)
123917904
>>> id (b)
123917904
>>> a is b
True
```

You can see that both variables a and b are referred to the same object, which has a 'house' value and occupies the memory position 123917904 (this position is arbitrary). The instruction a is b is true.

![](bbox=[0.122, 0.372, 0.285, 0.455])

In string data types, being immutable, Python creates only one object per memory economy and both variables are referred to the same object. However, with the lists, being mutable, although two lists with the same values are formed, Python creates two objects, which occupy different memory locations:

```
>>> a = [1, 2, 3]
>>> b = [1, 2, 3]
>>> id(a)
123921992
>>> id(b)
123923656
>>> a is b
False
```

![](bbox=[0.122, 0.792, 0.385, 0.842])

The lists assigned to variables a and b, although with the same value, are different objects. But you have to be careful with the variable assignments to the