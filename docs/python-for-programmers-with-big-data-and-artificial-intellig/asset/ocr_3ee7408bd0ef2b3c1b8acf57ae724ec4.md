implementation is inappropriate for a derived class, that method can be overridden (i.e., redefined) in the derived class with an appropriate implementation. Method __repr__ (lines 58–64) overrides the default implementation inherited into class CommissionEmployee from class object. 6

+   6 ee tps://docs.python.org/3/reference/datamodel.html for objects overridable methods.

# Testing Class CommissionEmployee

Let's quickly test some of CommissionEmployee's features. First, create and display a CommissionEmployee:

lick here to view code image

```
```
In [1]: from commissionemployee import CommissionEmployee

In [2]: from decimal import Decimal

In [3]: c = CommissionEmployee('Sue', 'Jones', '333-33-3333',
   ...:                     Decimal('10000.00'), Decimal('0.06'))
   ...:

In [4]: c
Out[4]:
CommissionEmployee: Sue Jones
social security number: 333-33-3333
gross sales: 10000.00
commission rate: 0.06
```
```

Next, let's calculate and display the CommissionEmployee's earnings:

lick here to view code image

```
```
In [5]: print(f'{c.earnings():,.2f}')
600.00
```
```

Finally, let's change the CommissionEmployee's gross sales and commission rate, then recalculate the earnings:

lick here to view code image

```
```
In [6]: c.gross_sales = Decimal('20000.00')

In [7]: c.commission_rate = Decimal('0.1')

In [8]: print(f'{c.earnings():,.2f}')
2,000.00
```
```