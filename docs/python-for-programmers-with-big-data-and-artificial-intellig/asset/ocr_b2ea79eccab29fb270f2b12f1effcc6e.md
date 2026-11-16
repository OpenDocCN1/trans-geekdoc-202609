```
def deposit(self, amount):
    """Deposit money to the account."""
    # if amount is less than 0.00, raise an exception
    if amount < Decimal('0.00'):
        raise ValueError('amount must be positive.')
    self.balance += amount
if __name__ == '__main__':
    import doctest
    doctest.testmod(verbose=True)
```

# Module __main__

When you load any module, Python assigns a string containing the module's name to a global attribute of the module called __name__. When you execute a Python source file (such as accountdoctest.py) as a script, Python uses the string '__main__' as the module's name. You can use __name__ in an if statement like lines 40–42 to specify code that should execute only if the source file is executed as a script. In this example, line 41 imports the doctest module and line 42 calls the module's testmod function to execute the docstring unit tests.

# Running Tests

Run the file accountdoctest.py as a script to execute the tests. By default, if you call testmod with no arguments, it does not show test results for successful tests. In that case, if you get no output, all the tests executed successfully. In this example, line 42 calls testmod with the keyword argument verbose=True. This tells testmod to produce verbose output showing every test's results:

lick here to view code image

```
Trying:
    account1 = Account('John Green', Decimal('50.00'))
Expecting nothing
ok
Trying:
    account1.name
Expecting:
    'John Green'
ok
Trying:
    account1.balance
Expecting:
    Decimal('50.00')
ok
Trying:
    account2 = Account('John Green', Decimal('-50.00'))
Expecting:
    Traceback (most recent call last):
      ...
    ValueError: Initial balance must be >= to 0.00.
ok
```