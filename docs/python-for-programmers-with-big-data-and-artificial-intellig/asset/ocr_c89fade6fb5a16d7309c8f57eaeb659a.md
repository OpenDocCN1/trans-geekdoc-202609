combinations of `False` and `True` values for `expression1` and `expression2`—such tables are called `truth tables`:

| expression1 | expression2 | expression1 and expression2 |
|---|---|---|
| False | False | False |
| False | True | False |
| True | False | False |
| True | True | True |

# Boolean Operator `or`

Use the **Boolean `or` operator** to test whether one _or_ both of two conditions are `True`. The following code tests a condition that’s `True` if either _or_ both simple conditions are `True`—the entire condition is `False` only if _both_ simple conditions are `False`:

lick here to view code image

```
In [4]: semester_average = 83

In [5]: final_exam = 95

In [6]: if semester_average >= 90 or final_exam >= 90:
    ...:     print('Student gets an A')
    ...:
Student gets an A
```

Snippet [6] also contains two simple conditions:

+   • `semester_average >= 90` determines whether a student’s average was an A (90 or above) during the semester, and