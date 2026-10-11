
# Python OOP Concepts

## Class Definition and Private Attributes

The program defined a class `Tv` and used `__init__` methods to hold the final offering price of the TV. Along the way, we attempted to change the price but could not manage. The reason for the inability to change is because Python treated the `_finalprice` as private attributes. The only way to modify this value was through using a setter function, `setMaxPrice()` that takes price as a parameter.

## Polymorphism

In Python, polymorphism refers to the ability to use a shared interface for several data types.

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

![Polymorphism Example](Images/image00223.gif)

### Explanation

The program above has defined two classes `Tilapia` and `Shark` all of which share the method `jump()` even though they have different functions. By creating common interface `jumping_test()` we allowed polymorphism in the program above. We then passed objects `bonny` and `biggy` in the `jumping_test()` function.

### Exercise

a. In a doctor consultation room suggest the class and objects in a programming context.

b. In a football team, suggest programming class and objects.

c. In a grocery store, suggest programming class and objects.

## Class Definition in Python

The keyword `class` is used to define a class in Python. The first string in a Python class is used to describe the class even though it is not always needed.

### Example 1

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
class Dog:
    '''Briefly taking about class Dog using this docstring'''
    pass
```

### Example 2

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
class Bright:
    "My other class"
    b = 10

    def salute(self):
        print('Welcome')

print(Bright.b)
print(Bright.salute)
print(Bright.__doc__)
```

## Object Creation in Python

### Example from the previous class

Open the previous program file with class `Bright`:

```python
student1 = Bright()
```

### Explanation

The last program will create object `student1`, a new instance. The attributes of objects can be accessed via the specific object name prefix. The attributes can be a method or data including the matching class functions. In other terms, `Bright.salute` is a function object and `student1.salute` will be a method object.

### Example

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
class Bright:
    "Another class again!"
    c = 20

    def salute(self):
        print('Hello')

student2 = Bright()

print(Bright.salute)
print(student2.salute)

student2.salute()
```

### Explanation

We invoked the `student2.salute()` despite the parameter `self` and it still worked without placing arguments. The reason for this phenomenon is because each time an object calls its method, the object itself is passed as the first argument. The implication is that `student2.salute()` translates into `student2.salute(student2)`. It is the reason for the `self` name.

## Constructors

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
class ComplexNumber:
    def __init__(self, realnum=0, i=0):
        self.real = realnum
        self.imaginarynum = i

    def getData(self):
        print("{0}+{1}j".format(self.real, self.imaginarynum))

complex1 = ComplexNumber(2, 3)
complex1.getData()

complex2 = ComplexNumber(5)
complex2.attribute = 10
print((complex2.real, complex2.imaginarynum, complex2.attribute))

# complex1.attribute  # This would raise an AttributeError
```

## Deleting Objects and Attributes

The `del` statement is used to delete attributes of an object at any instance.

### Example

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
complex1 = ComplexNumber(2, 3)
del complex1.imaginarynum
complex1.getData()

del ComplexNumber.getData
complex1.getData()
```

## Deleting the Entire Object

### Example

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
complex1 = ComplexNumber(1, 3)
del complex1
```

### Explanation

When `complex1 = ComplexNumber(1, 3)` is done, a new instance of the object gets generated in memory and the name `complex1` ties with it. The object does not immediately get destroyed as it temporarily stays in memory before the garbage collector purges it from memory. The purging of the object helps free resources bound to the object and enhances system efficiency. Garbage collection in Python refers to automatic destruction of unreferenced objects.

## Inheritance in Python

In Python inheritance allows us to specify a class that takes all the functionality from the base class and adds more. It is a powerful feature of OOP.

### Syntax

```python
class ParentClass:
    # Body of parent class

class ChildClass(ParentClass):
    # Body of derived class
```

### Example 1

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
class Shape:
    def __init__(self, sides):
        self.sides = sides

    def count_sides(self):
        return self.sides

class Rect_mine(Shape):
    def __init__(self):
        Shape.__init__(self, 4)

    def getArea(self):
        s1, s2, s3, s4 = self.count_sides()
        perimeter = (s1 + s2 + s3 + s4)
        area = (s1 * s2)
        print('The rectangle area is: %s' % area)
```

### Example 2

```python
r = Rect_mine()
r.inputSides()
# Type b1 : 4
# Type l1 : 8
# Type b2 : 4
# Type l1:    8

r.dispSides()
# Type b1 is 4.0
# Type l1 is 8.0
# Type b2 is 4.0
# Type l1 is 8.0

r.getArea()
```

## Method Overriding in Python

When a method is defined in both the base class and the derived class, the method in the child class/derived class will override the parent/base class. In the above example, the `__init__()` method in `Rect_mine` class will override the `__init__()` in `Shape` class.

## Multiple Inheritance

### Example

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

![Multiple Inheritance Example](Images/image00224.gif)

In this case, `MultiInherit` is derived from class `Parent1` and `Parent2`.

## Multilevel Inheritance

Inheriting from a derived class is called multilevel inheritance.

### Example

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
class Parent:
    pass

class Multilevel1(Parent):
    pass

class Multilevel2(Multilevel1):
    pass
```

### Explanation

`Multilevel1` derives from `Parent`, and `Multilevel2` derives from `Multilevel1`.

## Method Resolution Order

### Example

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
print(issubclass(list, object))
print(isinstance(6.7, object))
print(isinstance("Welcome", object))
```

### Explanation

The particular attribute in a class will be scanned first. The search will continue into parent classes. This search does not repeat searching for the same class twice. The approach or order of searching is sometimes called linearization of multi derived class in Python. The Method Resolution Order (MRO) refers to the rules needed to determine this order.

## Operator Overloading

Inbuilt classes can use operators and the same operators will behave differently with different types. An example is the `+` that depending on context will perform concatenation of two strings, arithmetic addition on numbers, or merge lists. Operator overloading is an OOP feature that allows assigning varying meaning to an operator subject to context.

## Making Class Compatible with Inbuilt Special Functions

### Example

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
class Planar:
    def __init__(self, x_axis=0, y_axis=0):
        self.x_axis = x_axis
        self.y_axis = y_axis

    def __str__(self):
        return "({0},{1})".format(self.x_axis, self.y_axis)

planar1 = Planar(3, 5)
print(planar1)  # The output will be (3,5)
```

## Using More Inbuilt Methods

### Example

1. Start IDLE.
2. Navigate to the File menu and click New Window.
3. Type the following:

```python
class Planar:
    def __init__(self, x_axis=0, y_axis=0):
        self.x_axis = x_axis
        self.y_axis = y_axis

planar1 = Planar(3, 5)
str(planar1)
format(planar1)
```

### Explanation

The `__str__` method allows the `str()` and `format()` functions to work with custom objects.
