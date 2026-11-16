is an object.” This means that an object’s attributes are references to objects of other classes. For example, an Account object’s name attribute is a reference to a string object and an Account object’s balance attribute is a reference to a Decimal object. Embedding references to objects of other types is a form of software reusability known as composition and is sometimes referred to as the “has a” relationship. Later in this chapter, we’ll discuss inheritance, which establishes “is a” relationships.

# 10.3 CONTROLLING ACCESS TO ATTRIBUTES

Class Account’s methods validate their arguments to ensure that the balance is always valid—that is, always greater than or equal to 0.00. In the previous example, we used the attributes name and balance only to get the values of those attributes. It turns out that we also can use those attributes to modify their values. Consider the Account object in the following IPython session:

lick here to view code image

```
In [1]: from account import Account

In [2]: from decimal import Decimal

In [3]: account1 = Account('John Green', Decimal('50.00'))

In [4]: account1.balance
Out[4]: Decimal('50.00')
```

Initially, account1 contains a valid balance. Now, let’s set the balance attribute to an invalid negative value, then display the balance:

lick here to view code image

```
In [5]: account1.balance = Decimal('-1000.00')

In [6]: account1.balance
Out[6]: Decimal('-1000.00')
```

Snippet [6]’s output shows that account1’s balance is now negative. As you can see, unlike methods, data attributes cannot validate the values you assign to them.

# Encapsulation

A class’s client code is any code that uses objects of the class. Most object-oriented programming languages enable you to encapsulate (or hide) an object’s data from the client code. Such data in these languages is said to be private data.

# Leading Underscore (_) Naming Convention

Python does not have private data. Instead, you use naming conventions to design classes