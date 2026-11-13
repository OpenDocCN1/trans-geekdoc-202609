+   - Binary operator: an operator that requires two operands (values).
+   - Operand: a value used in a mathematical expression.
+   - Unary operator: an operator that requires one single operand.
+   - Integer division: division in which the fractional part is discarded.
+   - Floating-point division: division in which the fractional part is kept.

Arithmetic operators are used to perform calculations such as addition, multiplication, subtraction, and so on. The arithmetic operators presented so far are binary operators, meaning they require two operands (two values) to apply the calculation on. There are also unary operators (that require only one operand), such as:

| Unary operator | Meaning |
| --- | --- |
| - | negative numbers |
| ++ | incrementing the value by 1 |
| -- | decrementing the value by 1 |

While it is quite straightforward to understand when you would use the addition, subtraction or multiplication operators, it might be a bit trickier to understand what the div and mod operators are.

# Div: division operator

In Java and Python, there are two types of division: integer division and floating-point division. Both types use the same symbol (forward slash) in Java. However, when dividing two integer values, the result will be an integer (integer division); when dividing two floating-point numbers or a decimal and an integer, the result will be a decimal number (floating-point division).

```
Java
int no1 = 7;
int no2 = 2;
System.out.println(no1/no2);
```

In the example above, even if the result would be 3.5, the answer displayed would be 3, as the two numbers are whole numbers (integers).

```
Java
double no1 = 7.0;
double no2 = 2.0;
System.out.println(no1/no2);
```

However, in this example, as both variables store decimal numbers, the result displayed is a decimal number as well (3.5).

```
Java
float no1 = 7.0;
int no2 = 2;
System.out.println(no1/no2);
```

In the example above, the values stored are numbers of mixed data types, and the result will be a decimal number: 3.5.