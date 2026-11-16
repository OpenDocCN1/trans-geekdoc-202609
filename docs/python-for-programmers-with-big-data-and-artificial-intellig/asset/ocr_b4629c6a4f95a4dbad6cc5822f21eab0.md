# The statement

lick here to view code image

```
print(f'{year:>2} {amount:>10.2f}')
```

uses an f-string with two placeholders to format the loop’s output.

# The placeholder

```
{year:>2}
```

uses the format specifier >2 to indicate that year’s value should be **right aligned (>)** in a field of width 2—the **field width** specifies the number of character positions to use when displaying the value. For the single-digit year values 1–9, the format specifier >2 displays a space character followed by the value, thus right aligning the years in the first column. The following diagram shows the numbers 1 and 10 each formatted in a field width of 2:

![](bbox=[0.35, 0.48, 0.7, 0.58])

You can **left align** values with <.

# The format specifier 10.2f in the placeholder

```
{amount:>10.2f}
```

formats amount as a floating-point number (f) right aligned (>) in a field width of 10 with a decimal point and two digits to the right of the decimal point (.2). Formatting the amounts this way **aligns their decimal points vertically**, as is typical with monetary amounts. In the 10 character positions, the three rightmost characters are the number’s decimal point followed by the two digits to its right. The remaining seven character positions are the leading spaces and the digits to the decimal point’s left. In this example, all the dollar amounts have four digits to the left of the decimal point, so each number is formatted with three **leading spaces**. The following diagram shows the formatting for the value 1050.00: