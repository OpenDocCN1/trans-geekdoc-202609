

39  self._gross_sales = sales
40
41  @property
42  def commission_rate(self):
43      return self._commission_rate
44
45  @commission_rate.setter
46  def commission_rate(self, rate):
47      """Set commission rate or raise ValueError if invalid."""
48      if not (Decimal('0.0') < rate < Decimal('1.0')):
49          raise ValueError(
50          'Interest rate must be greater than 0 and less than 1')
51
52      self._commission_rate = rate
53
54  def earnings(self):
55      """Calculate earnings."""
56      return self.gross_sales * self.commission_rate
57
58  def __repr__(self):
59      """Return string representation for repr()."""
60      return ('CommissionEmployee: ' +
61      f'{self.first_name} {self.last_name}\n' +
62      f'social security number: {self.ssn}\n' +
63      f'gross sales: {self.gross_sales:.2f}\n' +
64      f'commission rate: {self.commission_rate:.2f}')

Properties first_name, last_name 和 ssn 属性是只读的。我们选择不对它们进行验证，尽管本可以验证。例如，我们可以验证名和姓——或许通过确保它们的长度合理。我们可以验证社会安全号码，以确保它包含九位数字，可以带连字符，也可以不带（例如，确保其格式为 ###-##-#### 或 ##########，其中每个 # 都是数字）。

## 所有类直接或间接继承自类 object

你使用继承从现有类中创建新类。事实上，每个 Python 类都继承自一个现有类。当你没有为新类显式指定基类时，Python 假设该类直接继承自类 object。Python 类层次结构从类 object 开始，它是每个类的直接或间接基类。因此，类 CommissionEmployee 的定义本可以写成

```python
class CommissionEmployee(object):
```

CommissionEmployee 后面的括号表示继承，可以包含用于单继承的单个类，或用于多继承的逗号分隔的基类列表。再次说明，多继承超出了本书的范围。

类 CommissionEmployee 继承类 object 的所有方法。类 object 没有任何数据属性。从 object 继承的许多方法中，有两个是 __repr__ 和 __str__。因此，每个类都有这些方法，用于返回其被调用对象的字符串表示。当基类方法实现不适合派生类时，可以在派生类中用适当的实现覆盖（即重新定义）该方法。方法 __repr__（第 58–64 行）覆盖了类 CommissionEmployee 从类 object 继承的默认实现。6

6 https://docs.python.org/3/reference/datamodel.html 关于对象的可覆盖方法。

## 测试类 CommissionEmployee

让我们快速测试 CommissionEmployee 的一些功能。首先，创建并显示一个 CommissionEmployee：

单击此处查看代码图像

```python
In [1]: from commissionemployee import CommissionEmployee

In [2]: from decimal import Decimal

In [3]: c = CommissionEmployee('Sue', 'Jones', '333-33-3333',
   ...:                    Decimal('10000.00'), Decimal('0.06'))
   ...:

In [4]: c
Out[4]:
CommissionEmployee: Sue Jones
social security number: 333-33-3333
gross sales: 10000.00
commission rate: 0.06
```

接下来，让我们计算并显示 CommissionEmployee 的收入：

单击此处查看代码图像

```python
In [5]: print(f'{c.earnings():,.2f}')
600.00
```

最后，让我们更改 CommissionEmployee 的总销售额和佣金率，然后重新计算收入：

单击此处查看代码图像

```python
In [6]: c.gross_sales = Decimal('20000.00')

In [7]: c.commission_rate = Decimal('0.1')

In [8]: print(f'{c.earnings():,.2f}')
2,000.00
```

## 10.8.2 子类 SalariedCommissionEmployee

使用单继承时，子类在本质上与基类相同。继承的真正强大之处在于能够在子类中定义对从基类继承的功能进行添加、替换或改进。

SalariedCommissionEmployee 的许多功能与类 CommissionEmployee 的功能相似，甚至相同。两种类型的员工都具有名、姓、社会安全号码、总销售额和佣金率数据属性，以及用于操作这些数据的属性和方法。若要不使用继承来创建类 SalariedCommissionEmployee，我们本可以复制类 CommissionEmployee 的代码并将其粘贴到类 SalariedCommissionEmployee 中。然后我们本可以修改新类，以包含基本工资数据属性，以及用于操作基本工资的属性和方法，包括一个新的 earnings 方法。这种复制粘贴方法往往容易出错。更糟的是，它可以将同一代码（包括错误）的多个物理副本散布到整个系统中，使你的代码可维护性降低。继承使我们能够在不重复代码的情况下“吸收”一个类的功能。让我们看看如何实现。

### 声明类 SalariedCommissionEmployee

我们现在声明子类 SalariedCommissionEmployee，它继承了类 CommissionEmployee 的大部分功能（第 6 行）。SalariedCommissionEmployee 是一种 CommissionEmployee（因为继承传递了类 CommissionEmployee 的功能），但类 SalariedCommissionEmployee 还具有以下功能：

- 方法 __init__（第 10–15 行），用于初始化从类 CommissionEmployee 继承的所有数据（我们稍后会详细说明），然后使用 base_salary 属性的 setter 来创建 __base_salary 数据属性。
- 可读写属性 base_salary（第 17–27 行），其中 setter 执行数据验证。
- 方法 earnings 的自定义版本（第 29–31 行）。
- 方法 __repr__ 的自定义版本（第 33–36 行）。

单击此处查看代码图像

```python
# salariedcommissionemployee.py
"""SalariedCommissionEmployee derived from   CommissionEmployee."""
from commissionemployee import   CommissionEmployee
from decimal import Decimal

class SalariedCommissionEmployee(CommissionEmployee):
   """An employee who gets paid a salary plus
   commission based on gross sales."""
```

```python
10 def __init__(self, first_name, last_name, ssn,
11 gross_sales, commission_rate, base_salary):
12 """Initialize SalariedCommissionEmployee's attributes."""
13 super().__init__(first_name, last_name, ssn,
14 gross_sales, commission_rate)
15
16 self.base_salary = base_salary # validate via property
17
18 @property
19 def base_salary(self):
20 return self._base_salary
21
22 @base_salary.setter
23 def base_salary(self, salary):
24 """Set base salary or raise ValueError if invalid."""
25 if salary < Decimal('0.00'):
26 raise ValueError('Base salary must be >= to 0')
27
28 self._base_salary = salary
29
30 def earnings(self):
31 """Calculate earnings."""
32 return super().earnings() + self.base_salary
33
34 def __repr__(self):
35 """Return string representation for repr()."""
36 return ('Salaried' + super().__repr__() +
37 f'\nbase salary: {self.base_salary:.2f}')
```

## 从类 CommissionEmployee 继承

要从一个类继承，必须先导入其定义（第 3 行）。第 6 行

```python
class SalariedCommissionEmployee(CommissionEmployee):
```

指定类 SalariedCommissionEmployee 继承自 CommissionEmployee。虽然你在类 SalariedCommissionEmployee 中看不到类 CommissionEmployee 的数据属性、属性和方法，但它们 nevertheless 是新类的一部分，你很快就会看到。

## 方法 __init__ 和内置函数 super

每个子类的 __init__ 必须显式调用其基类的 __init__ 来初始化从基类继承的数据属性。此调用应为子类 __init__ 方法中的第一条语句。SalariedCommissionEmployee 的 __init__ 方法显式调用类 CommissionEmployee 的 __init__ 方法（第 13–14 行）来初始化 SalariedCommissionEmployee 对象的基类部分（即来自类 CommissionEmployee 的五个继承数据属性）。super().__init__ 表示法使用内置函数 super 来定位并调用基类的 __init__ 方法，传递用于初始化继承数据属性的五个参数。

## 覆盖方法 earnings

