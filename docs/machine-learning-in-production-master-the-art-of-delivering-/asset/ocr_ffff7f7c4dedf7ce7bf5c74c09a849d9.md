```
5. def add():
6.     print(a+b)
7.
8. # Calling a function
9. add()
10.
11. # Output
12. 7
```

# # Object Oriented Programming (OOP)

Python is an object-oriented language, so everything in Python is an object. Let’s understand its key concepts and their importance:

**Class:** A class acts like a template for the objects. It is defined using the **class** keyword like the **def** keyword is used while creating a new function. A Python class contains objects and methods, and they can be accessed using the period (.).

**Object:** An object is an instance of a class. It depicts the structure of the class and contains class variables, instance variables, and methods.

**Method:** In simple words, it is a function defined while creating a class.

**__init__:** For the automatic initialization of data members by assigning values, you should use the **__init__** method while creating an instance of a class. It gets called every time you create an object of the class. The usage is equivalent to the constructor in C++ and Java.

**Self:** It helps us access the methods and attributes of the class. You are free to name it anything; however, as per convention and for readability, it is better to declare it as self.

# ## Example: 1.14 Class definition

```
1. class Multiply:
2.     def mul(self):
3.         result = self.num1 * self.num2       Class definition
4.         return result
5.
6.     def __init__(self,num1,num2):
7.         self.num1 = num1
8.         self.num2 = num2
```