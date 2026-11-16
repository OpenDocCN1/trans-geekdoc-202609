ensure that the method works correctly:

+   • The test in line 11 creates a sample `Account` object named `account1`. This statement does not produce any output.

+   • The test in line 12 shows what the value of `account1`'s `name` attribute should be if line 11 executed successfully. The sample output is shown in line 13.

+   • The test in line 14 shows what the value of `account1`'s `balance` attribute should be if line 11 executed successfully. The sample output is shown in line 15.

+   • The test in line 18 creates an `Account` object with an invalid initial balance. The sample output shows that a `ValueError` exception should occur in this case. For exceptions, the doctest module's documentation recommends showing just the first and last lines of the traceback. 8

8 https://docs.python.org/3/library/doctest.html?highlight=doctest#module-doctest.

You can intersperse your tests with descriptive text, such as line 17.

lick here to view code image

```
1 # accountdoctest.py
2 """Account class definition."""
3
4 from decimal import Decimal
5
6 class Account:
7     """Account class for demonstrating doctest."""
8
9     def __init__(self, name, balance):
10         """Initialize an Account object."""
11
12         >>> account1 = Account('John Green', Decimal('50.00'))
13         >>> account1.name
14         'John Green'
15         >>> account1.balance
16         Decimal('50.00')
17
18         The balance argument must be greater than or equal to 0.
19         >>> account2 = Account('John Green', Decimal('-50.00'))
20         Traceback (most recent call last):
21         ...
22         ValueError: Initial balance must be >= to 0.00.
23         """
24
25         # if balance is less than 0.00, raise an exception
26         if balance < Decimal('0.00'):
27             raise ValueError('Initial balance must be >= to 0.00.')
28
29         self.name = name
30         self.balance = balance
```