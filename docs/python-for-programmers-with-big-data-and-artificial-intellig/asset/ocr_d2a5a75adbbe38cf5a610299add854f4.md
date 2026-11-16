```
In [12]: print(f'{s.earnings():.2f}')
500.00
```

Now, let's modify the gross_sales, commission_rate and base_salary properties, then display the updated data via the Salaried-Commission-Employee's __repr__ method:

lick here to view code image

```
In [13]: s.gross_sales = Decimal('10000.00')

In [14]: s.commission_rate = Decimal('0.05')

In [15]: s.base_salary = Decimal('1000.00')

In [16]: print(s)
SalariedCommissionEmployee: Bob Lewis
social security number: 444-44-4444
gross sales: 10000.00
commission rate: 0.05
base salary: 1000.00
```

Again, because this method is called on a SalariedCommissionEmployee object, the subclass version of the method executes. Finally, let's calculate and display the Salaried-Commission-Employee's updated earnings:

lick here to view code image

```
In [17]: print(f'{s.earnings():.2f}')
1,500.00
```

# Testing the “is a” Relationship

Python provides two built-in functions—issubclass and isinstance—for testing “is a” relationships. Function issubclass determines whether one class is derived from another:

lick here to view code image

```
In [18]: issubclass(SalariedCommissionEmployee, CommissionEmployee)
Out[18]: True
```

Function isinstance determines whether an object has an “is a” relationship with a specific type. Because SalariedCommissionEmployee inherits from CommissionEmployee, both of the following snippets return True, confirming the “is a” relationship

lick here to view code image

```
In [19]: isinstance(s, CommissionEmployee)
```