
An element is an individual value in the list that is assigned a unique index. For all list operations, if a list index is less than 1 or greater than the length of the list, an error message is produced and the program will terminate.

![image](images/common.jpg)

### Example Nineteen

```
namesOfMyDogs ← [ “Waffles”, “Novack the 3rd”, “Benji”]
newList = namesOfMyDogs
a ← newList [0]
```

This code causes an error. This index will be out of bounds since `newList` has only the indexes 1, 2, and 3.

![Images](images/p0194-01.jpg)

This code causes an error. This index will be out of bounds since `newList` has only the indexes 1, 2, and 3.

## Display Operators

![Images](images/t0194-01.jpg)

![image](images/common.jpg)

### Example Twenty

What will the following program display?

```
a ← 3
b ← 17
a ← b
DISPLAY(a)
```

As shown by the following chart, all variables must be initialized before `a` can be printed. Note that `a` is initialized to the value of 3 and `b` is set to 17. The next step sets the value of `a` to the value of `b`, which is 17.

![Images](images/p0194-01a.jpg)

**Answer: 17**

![image](images/common.jpg)

### Example Twenty-One

What will the following program display?

```
a ← 3
b ← 14
c ← 5
a ← c
b ← a
DISPLAY(a)
DISPLAY(b)
DISPLAY(c)
```

**Answer: 5 5 5**

| *a* | *b* | *c* |
| --- | --- | --- |
| ~~3~~ | ~~14~~ | 5 |
| 5 | 5 |   |

![image](images/common.jpg)

### Example Twenty-Two

What will the following program display?

![Images](images/p0195-01.jpg)

| *a* | *b* | DISPLAY |
| --- | --- | --- |
| 5 + 8 = 13 | 4 MOD 5 = 4 | 17 |

**Answer: 17**

## Input Operators

| Text: `INPUT()` Block: `INPUT` | Accepts a value from the user and returns it. |
| --- | --- |

![image](images/common.jpg)

### Example Twenty-Three

What will the following program display if the `INPUT` function reads an even number such as 4?

```
a ← INPUT()
a ← a MOD 2
DISPLAY(a)
```

For 4 (or any even number) divided by 2, the remainder will always be 0.

**Answer: 0**

![image](images/common.jpg)

### Example Twenty-Four

What will the following program display if the `INPUT` function reads an odd number such as 5?

```
a ← INPUT()
a ← a MOD 2
DISPLAY(a)
```

An odd number will always have a remainder of 1 when divided by 2.

**Answer: 1**

## Relational and Boolean Operators

| Text and block: | The relational operators `=`, `≠`, `>`, `<`, `≥`, and `≤` are used to test the relationship between two variables, expressions, or values. |
| --- | --- |

| `a = b` | `a = b` evaluates to true if `a` and `b` are equal; otherwise, it evaluates to false. For example, when `a` is 3 and `b` is 3, `a = b` evaluates to true. However, when `a` is 3 and `b` is 5, `a = b` evaluates to false. |
| `a ≠ b` | `a ≠ b` evaluates to true if `a` and `b` are not equal; otherwise, it evaluates to false. |
| `a > b` | `a > b` evaluates to true if `a` is greater than `b`; otherwise, it evaluates to false. |
| `a < b` | `a < b` evaluates to true if `a` is less than `b`; otherwise, it evaluates to false. |
| `a ≥ b` | `a ≥ b` evaluates to true if `a` is greater than or equal to `b`; otherwise, it evaluates to false. |
| `a ≤ b` | `a ≤ b` evaluates to true if `a` is less than or equal to `b`; otherwise, it evaluates to false. |

![image](images/common.jpg)

### Example Twenty-Five

What will the following program display?

![Images](images/p0196-02.jpg)

| ***a*** | *b* | DISPLAY |
| --- | --- | --- |
| 3 | 3 MOD 5 = 3 | true |

`a` is initialized to 3; `b` is initialized to the remainder when 3 is divided by 5. Since 3 is equal to 3, the program will display true.

**Answer: True**

![image](images/common.jpg)

### Example Twenty-Six

What will the following program display?

```
a ← 4 * (3 + 6)
b ← 4 * 3 + 6
DISPLAY (a ≤ b)
```

| *a* | *b* | DISPLAY |
| --- | --- | --- |
| 36 | 18 | false |

Using the order of operations, `a` will be initialized to 36 since the addition occurs first due to the parentheses. Note that `b` will be initialized to 18 since the multiplication occurs first due to operator precedence. Because 36 is not less than or equal to 18, this program displays false.

**Answer: False**

### Numeric Procedures

| Text: `RANDOM(a, b)` Block: ![Images](images/p0197-02.jpg) | Evaluates to a random integer from `a` to `b`, including `a` and `b`. For example, `RANDOM(1, 3)` could evaluate to 1, 2, or 3. |
| --- | --- |

![image](images/common.jpg)

### Example Twenty-Seven

If the below code was executed several times, what is the percentage of times “true” would be expected to be displayed?

![Images](images/p0197-03.jpg)

`RANDOM` can pick 1 or 2. The chance of 1 being picked is 1/2 or 50%.

**Answer: 50%**

![image](images/common.jpg)

### Example Twenty-Eight

If the below code was executed several times, what is the percentage of times “false” would be expected to be displayed?

![Images](images/p0197-04.jpg)

The numbers 1, 2, 3, and 4 are all possible selections. The chance of 3 being selected is 1/4 or 25%. The chance of 3 not being selected is 3/4, which is 75%.

**Answer: 75%**

![image](images/common.jpg)

### Example Twenty-Nine

If the below code was executed several times, what is the percentage of times “true” would be expected to be displayed?

![Images](images/p0198-01.jpg)

The numbers 1, 2, 3, 4, 5, 6, 7, 8, 9, and 10 can all be selected. Since `a ≤ 3` includes 1, 2, and 3, the answer is 3/10 = 30%.

**Answer: 30%**

### Boolean Tables

| **Instruction** | **Explanation** |
| --- | --- |
| Text: `NOT condition` Block: ![Images](images/p0198-02.jpg) | Evaluates to “true” if condition is false; otherwise evaluates to “false.” |
| Text: `condition1 AND condition2` Block: ![Images](images/p0198-03.jpg) | Evaluates to “true” if both condition1 and condition2 are true; otherwise, evaluates to “false.” |
| Text: `condition1 OR condition2` Block: ![Images](images/p0198-04.jpg) | Evaluates to “true” if either condition1 is true or condition2 is true or if both condition1 and condition2 are true; otherwise, evaluates to “false.” |

A Boolean value is a data type that has only two possible values, true or false. On your AP exam, you will be tested on three Boolean operators. Those operators are `AND`, `OR`, and `NOT`.

Boolean questions simplify if you can use noncomputer science terms. For example, if you are a picky eater and you will be happy only if you have both of your favorite foods (Pizza `AND` Yams), ask yourself if you are happy in the following conditions.

| Happy with…. | Pizza `AND` Yams = Happy |
| --- | --- |
|   | True `AND` True = True |
| Happy with…. | Pizza `AND` Peanuts = Unhappy |
|   | True `AND` False = False |
| Happy with…. | Peas `AND` Peanuts = Unhappy |
|   | False `AND` False = False |
| Happy with…. | Tuna `AND` Pizza = Unhappy |
|   | False `AND` True = False |
| Actually |   |
| Happy with…. | Tuna `AND` Anything in the world = Unhappy |
|   | False `AND` Anything in the world = False |

Now let’s assume that you are not a picky eater and you will be happy if you have only one of your favorite foods (Pizza `OR` Yams). Ask yourself are you happy in the following conditions.

| Happy with…. | Pizza `OR` Yams = Happy |
| --- | --- |
|   | True `OR` True = True |
| Happy with…. | Pizza `OR` Peanuts = Happy |
|   | True `OR` False = True |
| Happy with…. | Peas `OR` Peanuts = Unhappy |
|   | False `OR` False = False |
| Happy with…. | Tuna `OR` Pizza = Happy |
|   | False `OR` True = True |
| Actually |   |
| Happy with…. | Pizza `OR` Anything in the world = Happy |
|   | True `OR` Anything in the world = True |

The operator `NOT` reverses the Boolean value.

`NOT` Happy = Unhappy

`NOT` True = False

`NOT` Unhappy = Happy

`NOT` False = True

The above results are summarized in the Boolean table below.

![Images](images/t0199-01.jpg)
