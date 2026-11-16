
Method call takes on “many forms,” hence the term “polymorphism.” We’ll explain how to implement polymorphism through inheritance and a Python feature called duck typing. We’ll explain both and show examples of each.

## An Entertaining Case Study: Card-Shuffling-and-Dealing Simulation

You’ve already used a random-numbers-based die-rolling simulation and used those techniques to implement the popular dice game craps. Here, we present a card-shuffling-and-dealing simulation, which you can use to implement your favorite card games. You’ll use Matplotlib with attractive public-domain card images to display the full deck of cards both before and after the deck is shuffled.

## Data Classes

Python 3.7’s new data classes help you build classes faster by using a more concise notation and by autogenerating portions of the classes. The Python community’s early reaction to data classes has been positive. As with any major new feature, it may take time before it’s widely used. We present class development with both the older and newer technologies.

## Other Concepts Introduced in This Chapter

Other concepts we present include:

- How to specify that certain identifiers should be used only inside a class and not be accessible to clients of the class.
- Special methods for creating string representations of your classes’ objects and specifying how objects of your classes work with Python’s built-in operators (a process called operator overloading).
- An introduction to the Python exception class hierarchy and creating custom exception classes.
- Testing code with the Python Standard Library’s doctest module.
- How Python uses namespaces to determine the scopes of identifiers.

## 10.2 CUSTOM CLASS ACCOUNT

Let’s begin with a bank Account class that holds an account holder’s name and balance. An actual bank account class would likely include lots of other information, such as address, birth date, telephone number, account number and more. The Account class accepts deposits that increase the balance and withdrawals that decrease the balance.

### 10.2.1 Test-Driving Class Account

Each new class you create becomes a new data type that can be used to create objects. This is one reason why Python is said to be an extensible language. Before we look at class Account's definition, let's demonstrate its capabilities.

### Importing Classes Account and Decimal

To use the new Account class, launch your IPython session from the ch10 examples folder, then import class Account:

Click here to view code image

```
In [1]: from account import Account
```

Class Account maintains and manipulates the account balance as a Decimal, so we also import class Decimal:

Click here to view code image

```
In [2]: from decimal import Decimal
```

### Create an Account Object with a Constructor Expression

To create a Decimal object, we can write:

```
value = Decimal('12.34')
```

This is known as a **constructor expression** because it builds and initializes an object of the class, similar to the way a house is constructed from a blueprint then painted with the buyer's preferred colors. Constructor expressions create new objects and initialize their data using argument(s) specified in parentheses. The parentheses following the class name are required, even if there are no arguments.

Let's use a constructor expression to create an Account object and initialize it with an account holder's name (a string) and balance (a Decimal):

Click here to view code image

```
In [3]: account1 = Account('John Green', Decimal('50.00'))
```

### Getting an Account's Name and Balance

Let's access the Account object's name and balance attributes:

Click here to view code image

```
In [4]: account1.name
Out[4]: 'John Green'
```

```
In [5]: account1.balance
Out[5]: Decimal('50.00')
```

### Depositing Money into an Account

An Account's deposit method receives a positive dollar amount and adds it to the balance:

Click here to view code image

```
In [6]: account1.deposit(Decimal('25.53'))

In [7]: account1.balance
Out[7]: Decimal('75.53')
```

### Account Methods Perform Validation

Class Account's methods validate their arguments. For example, if a deposit amount is negative, deposit raises a ValueError:

Click here to view code image

```
In [8]: account1.deposit(Decimal('-123.45'))
---------------------------------------------------------------
ValueError Traceback (most recent call last)
<ipython-input-8-27dc468365a7> in <module>()
----> 1 account1.deposit(Decimal('-123.45'))

~/Documents/examples/ch10/account.py in deposit(self, amount)
21 # if amount is less than 0.00, raise an exception
22 if amount < Decimal('0.00'):
---> 23 raise ValueError('Deposit amount must be positive.')
24
25 self.balance += amount

ValueError: Deposit amount must be positive.
```

### 10.2.2 Account Class Definition

Now, let's look at Account's class definition, which is located in the file account.py.

### Defining a Class

A class definition begins with the keyword class (line 5) followed by the class's name and a colon (:). This line is called the class header. The Style Guide for Python Code recommends that you begin each word in a multi-word class name with an uppercase letter (for example, CommissionEmployee). Every statement in a class's suite is indented.

Click here to view code image

```
1 # account.py
2 """Account class definition."""
3 from decimal import Decimal
4
5 class Account:
6     """Account class for maintaining a bank account balance."""
```

Each class typically provides a descriptive docstring (line 6). When provided, it must appear in the line or lines immediately following the class header. To view any class's docstring in IPython, type the class name and a question mark, then press Enter:

Click here to view code image

```
In [9]: Account?
init signature: Account(name, balance)
Docstring: Account class for maintaining a bank account balance.
Init docstring: Initialize an Account object.
File: ~/Documents/examples/ch10/account.py
Type:      type
```

The identifier Account is both the class name and the name used in a constructor expression to create an Account object and invoke the class's __init__ method. For this reason, IPython's help mechanism shows both the class's docstring ("Docstring:") and the __init__ method's docstring ("Init docstring:").

### Initializing Account Objects: Method __init__

The constructor expression in snippet [3] from the preceding section:

Click here to view code image

```
account1 = Account('John Green', Decimal('50.00'))
```

creates a new object, then initializes its data by calling the class's __init__ method. Each new class you create can provide an __init__ method that specifies how to initialize an object's data attributes. Returning a value other than None from __init__ results in a TypeError. Recall that None is returned by any function or method that does not contain a return statement. Class Account's __init__ method (lines 8–16) initializes an Account object's name and balance attributes if the balance is valid:

Click here to view code image

```
8 def __init__(self, name, balance):
9     """Initialize an Account object."""
10
11     # if balance is less than 0.00, raise an exception
12     if balance < Decimal('0.00'):
13         raise ValueError('Initial balance must be >= to 0.00.')
14
15     self.name = name
16     self.balance = balance
```

When you call a method for a specific object, Python implicitly passes a reference to that object as the method's first argument. For this reason, all methods of a class must specify at least one parameter. By convention most Python programmers call a method's first parameter `self`. A class's methods must use that reference (`self`) to access the object's attributes and other methods. Class `Account`'s `__init__` method also specifies parameters for the `name` and `balance`.

The `if` statement *validates* the `balance` parameter. If `balance` is less than `0.00`, `__init__` raises a `ValueError`, which terminates the `__init__` method. Otherwise, the method creates and initializes the new `Account` object's `name` and `balance` attributes.

When an object of class `Account` is created, it does not yet have any attributes. They're added *dynamically* via assignments of the form:

```
self.attribute_name = value
```

Python classes may define many **special methods**, like `__init__`, each identified by leading and trailing double-underscores (`__`) in the method name. Python class **object**, which we'll discuss later in this chapter, defines the special methods that are available for *all* Python objects.

### Method deposit

The `Account` class's `deposit` method adds a positive `amount` to the account's `balance` attribute. If the `amount` argument is less than `0.00`, the method raises a `ValueError`, indicating that only positive deposit `amount`s are allowed. If the `amount` is valid, line 25 adds it to the object's `balance` attribute.

Click here to view code image

```
18     def deposit(self, amount):
19         """Deposit money to the account."""
21     # if amount is less than 0.00, raise an exception
22     if amount < Decimal('0.00'):
23         raise ValueError('amount must be positive.')
24
25     self.balance += amount
```

### 10.2.3 Composition: Object References as Members of Classes

An `Account` *has a* `name`, and an `Account` *has a* `balance`. Recall that “everything in Python
