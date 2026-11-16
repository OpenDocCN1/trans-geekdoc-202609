# 3.11 USING TYPE DECIMAL FOR MONETARY AMOUNTS

In this section, we introduce Decimal capabilities for precise monetary calculations. If you’re in banking or other fields that require “to-the-penny” accuracy, you should investigate Decimal’s capabilities in depth.

For most scientific and other mathematical applications that use numbers with decimal points, Python’s built-in floating-point numbers work well. For example, when we speak of a “normal” body temperature of 98.6, we do not need to be precise to a large number of digits. When we view the temperature on a thermometer and read it as 98.6, the actual value may be 98.5999473210643. The point here is that calling this number 98.6 is adequate for most body-temperature applications.

Floating-point values are stored in binary format (we introduced binary in the first chapter and discuss it in depth in the online “Number Systems” appendix). Some floating-point values are represented only approximately when they’re converted to binary. For example, consider the variable amount with the dollars-and-cents value 112.31. If you display amount, it appears to have the exact value you assigned to it:

```
In [1]: amount = 112.31

In [2]: print(amount)
112.31
```

However, if you print amount with 20 digits of precision to the right of the decimal point, you can see that the actual floating-point value in memory is not exactly 112.31 —it’s only an approximation:

lick here to view code image

```
In [3]: print(f'{amount:.20f}')
112.31000000000000227374
```

Many applications require precise representation of numbers with decimal points. Institutions like banks that deal with millions or even billions of transactions per day have to tie out their transactions “to the penny.” Floating-point numbers can represent some but not all monetary amounts with to-the-penny precision.

The Python Standard Library 1 provides many predefined capabilities you can use in your Python code to avoid “reinventing the wheel.” For monetary calculations and other applications that require precise representation and manipulation of numbers