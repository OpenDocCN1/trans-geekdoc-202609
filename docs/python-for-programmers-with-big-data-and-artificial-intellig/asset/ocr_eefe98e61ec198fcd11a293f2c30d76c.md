You also can prove that the argument and the parameter refer to the same object with Python's is operator, which returns True if its two operands have the same identity:

lick here to view code image

```
In [5]: def cube(number):
    ...:     print('number is x:', number is x) # x is a global variab
    ...:     return number ** 3
    ...:

In [6]: cube(x)
number is x: True
Out[6]: 343
```

# Immutable Objects as Arguments

When a function receives as an argument a reference to an immutable (unmodifiable) object—such as an int, float, string or tuple—even though you have direct access to the original object in the caller, you cannot modify the original immutable object's value. To prove this, first let's have cube display id(number) before and after assigning a new object to the parameter number via an augmented assignment:

lick here to view code image

```
In [7]: def cube(number):
    ...:     print('id(number) before modifying number:', id(number))
    ...:     number **= 3
    ...:     print('id(number) after modifying number:', id(number))
    ...:     return number
    ...:

In [8]: cube(x)
id(number) before modifying number: 4350477840
id(number) after modifying number: 4396653744
Out[8]: 343
```

When we call cube(x), the first print statement shows that id(number) initially is the same as id(x) in snippet [2]. Numeric values are immutable, so the statement

```
number **= 3
```

actually creates a new object containing the cubed value, then assigns that object's reference to parameter number. Recall that if there are no more references to the