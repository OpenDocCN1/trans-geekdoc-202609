+   The meaning of how an operator works on objects of built-in types cannot be changed. You cannot, for example, change + so that it subtracts two integers.

+   Operator overloading works only with objects of custom classes or with a mixture of an object of a custom class and an object of a built-in type.

# Complex Numbers

To demonstrate operator overloading, we’ll define a class named Complex that represents complex numbers. 8 Complex numbers, like –3 + 4i and 6.2 – 11.73i, have the form

8 Python has built-in support for complex values, so this class is simply for demonstration purposes.

```
realPart + imaginaryPart * i
```

where i is √-1. Like ints, floats and Decimals, complex numbers are arithmetic types. In this section, we’ll create a class Complex that overloads just the + addition operator and the += augmented assignment, so we can add Complex objects using Python’s mathematical notations.

# 10.10.1 Test-Driving Class Complex

First, let’s use class Complex to demonstrate its capabilities. We’ll discuss the class’s details in the next section. Import class Complex from complexnumber.py:

lick here to view code image

```
In [1]: from complexnumber import Complex
```

Next, create and display a couple of Complex objects. Snippets [3] and [5] implicitly call the Complex class’s __repr__ method to get a string representation of each object:

lick here to view code image

```
In [2]: x = Complex(real=2, imaginary=4)

In [3]: x
Out[3]: (2 + 4i)

In [4]: y = Complex(real=5, imaginary=-1)

In [5]: y
Out[5]: (5 - 1i)
```

We chose the __repr__ string format shown in snippets [3] and [5] to mimic the __repr__ strings produced by Python’s built-in complex type. 9