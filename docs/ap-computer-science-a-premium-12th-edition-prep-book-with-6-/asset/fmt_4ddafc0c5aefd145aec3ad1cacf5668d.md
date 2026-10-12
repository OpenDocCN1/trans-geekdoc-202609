
## 4. The arithmetic operators follow the normal precedence rules (order of operations):

![images](images/f068-04.jpg)

Here operators on the same line have the same precedence, and, in the absence of parentheses, are invoked from left to right. Thus, the expression `19 % 5 * 3 + 14 / 5` evaluates to `4 * 3 + 2 = 14`. Note that casting has precedence over all of these operators. Thus, in the expression `(double) 3/4`, `3` will be cast to `double` before the division is done.

### Relational Operators

![images](images/f068-05.jpg)

#### Note

**1.** Relational operators are used in *boolean expressions* that evaluate to `true` or `false`.

![images](images/f069-01.jpg)

Do not routinely use `==` to test for equality of floating-point numbers.

**2.** If the operands are an `int` and a `double`, the `int` is promoted to a `double` as for arithmetic operators.

**3.** Relational operators should generally be used only in the comparison of primitive types (i.e., `int`, `double`, or `boolean`). Strings are compared using the `equals` and `compareTo` methods. (See [p. 157](#50_Chapter42.xhtml#page_157).)

**4.** Be careful when comparing floating-point values! Since floating-point numbers cannot always be represented exactly in the computer memory, a round-off error could be introduced, leading to an incorrect result when `==` is used to test for equality.

#### Optional Topic: Comparing Floating-Point Numbers

You can’t rely on using the `==` or `!=` operators to compare two `double` values for equality. They may differ in their last significant digit or two because of round-off error. Instead, you should test that the magnitude of the difference between the numbers is less than some number about the size of the machine precision. The machine precision is usually denoted *ɛ* and is typically about 10^(−16) for double precision (i.e., about 16 decimal digits). So you would like to test something like |*x* − *y*| ≤ *ɛ*. But this is no good if *x* and *y* are very large. For example, suppose *x* = 1234567890.123456 and *y* = 1234567890.123457. These numbers are essentially equal to machine precision, since they differ only in the 16th significant digit. But |*x* − *y*| = 10^(−6), not 10^(−16). So in general you should check the *relative* difference:

![images](images/f069-02.jpg)

To avoid problems with dividing by zero, code this as

![images](images/f069-03.jpg)

### Logical Operators

A *logical operator* (sometimes called a *boolean operator*) is one that returns a `boolean` result that is based on the `boolean` result(s) of one or two other `boolean` expressions. The three logical operators are shown in the table below.

![images](images/f069-04.jpg)

#### Note

**1.** Logical operators are applied to boolean expressions to form *compound boolean expressions* that evaluate to `true` or `false`.

**2.** Values of `true` or `false` are assigned according to the truth tables for the logical operators.

![images](images/f070-01.jpg)

For example, F `&&` T evaluates to F, while T `||` F evaluates to T.

**3.** *Short-circuit evaluation.* The subexpressions in a compound boolean expression are evaluated from left to right, and evaluation automatically stops as soon as the value of the entire expression is known. For example, consider a boolean OR expression of the form `A || B`, where `A` and `B` are some boolean expressions. If `A` is `true`, then the expression is `true` irrespective of the value of `B`. Similarly, if `A` is `false`, then `A && B` evaluates to `false` irrespective of the second operand. So in each case the second operand is not evaluated. For example,

![images](images/f070-02.jpg)

will not cause a run-time `ArithmeticException` (division-by-zero error) if the value of `numScores` is `0`. This is because `numScores != 0` will evaluate to `false`, causing the entire boolean expression to evaluate to `false` without having to evaluate the second expression containing the division.

### Assignment Operators

![images](images/f070-03.jpg)

#### Note

**1.** All these operators, with the exception of simple assignment, are called *compound assignment operators.*

**2.** *Chaining* of assignment statements is allowed, with evaluation from right to left. (This is not tested on the AP exam.)

![images](images/f070-04.jpg)

### Increment and Decrement Operators

![images](images/f070-05.jpg)

Note that `i++` (postfix) and `++i` (prefix) both have the net effect of incrementing `i` by `1`, but they are not equivalent. For example, if `i` currently has the value `5`, then `System.out.println(i++)` will print `5` and then increment `i` to `6`, whereas `System.out.println(++i)` will first increment `i` to `6` and then print `6`. It’s easy to remember: If the `++` is first, you first increment. A similar distinction occurs between `k--` and `--k`. (Note: You do not need to know these distinctions for the AP exam.)

### Operator Precedence

![images](images/f071-01.jpg)

Here operators on the same line have equal precedence. The evaluation of the operators with equal precedence is from left to right, except for rows (1) and (8) where the order is right to left. It is easy to remember: The only “backward” order is for the unary operators (row 1) and for the various assignment operators (row 8).

#### Example

What will be output by the following statement?

![images](images/f071-02.jpg)

#### Solution

Since `+` and `-` have precedence over `<`, `5 + 3` and `6 - 1` will be evaluated before evaluating the boolean expression. Since the value of the expression is false, the statement will output `false`.

### Input/Output

#### Input

Since there are so many ways to provide input to a program, user input is not a part of the AP Java subset. If reading input is a necessary part of a question on the AP exam, it will be indicated something like this:

![images](images/f071-03.jpg)

##### Note

The `Scanner` class simplifies both console and file input. It will not, however, be tested on the AP exam.

#### Output

Testing of output will be restricted to `System.out.print` and `System.out.println`. Formatted output will not be tested.

`System.out` is an object in the `System` class that allows output to be displayed on the screen. The `println` method outputs an item and then goes to a new line. The `print` method outputs an item without going to a new line afterward. An item to be printed can be a string, or a number, or the value of a boolean expression (`true` or `false`). Here are some examples:

![images](images/f072-01.jpg)

In the last example, the value of `x`, `27`, is converted to the string `“27”`, which is then concatenated to the string `“Value of x is ”`.

To print the “values” of user-defined objects, the `toString()` method is invoked. (See [p. 153](#50_Chapter42.xhtml#page_153).)

### Escape Sequences

An *escape sequence* is a backslash followed by a single character. It is used to print special characters. The three escape sequences that you should know for the AP exam are

![images](images/f072-02.jpg)

Here are some examples:

![images](images/f072-03.jpg)

prints

![images](images/f072-03a.jpg)

The statement

![images](images/f072-03b.jpg)

prints

![images](images/f072-04.jpg)

The statement

![images](images/f073-01.jpg)

prints

![images](images/f073-02.jpg)

### Control Structures

Control structures are the mechanism by which you make the statements of a program run in a nonsequential order. There are two general types: decision-making and iteration.

### Decision-Making Control Structures
