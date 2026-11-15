> > **Note**
> > You can also combine several logical operations. However, we recommend using brackets for reasons of clarity.

Table 5.4 provides an overview of the logical operators.

| Operator | Example | Description |
| :--- | :--- | :--- |
| && and | 7 > 3 && 2 < 4; //true | Logical AND. Returns true if both operands return true. |
| || or | 7 < 3 || | 2 < 4; //true | Logical OR. Returns true if one or both operands return true. |
| xor | 7 > 3 xor 2 < 4; //false | Logical EITHER OR. Only returns true if one of the two operands is true. Returns false if neither or both operands are true. |
| ! | !false; //true | Negation. Reverses a truth value. True becomes false and false becomes true. |

Table 5.4 The Logical Operators

There are two variants of logical AND and logical OR in PHP: one with symbols and one with letters. The only difference is that the variant with symbols has a higher operator precedence (Section 5.16).

# Short-Circuit Evaluation

The short-circuit evaluation is a PHP programming concept designed to increase performance. If a comparison with a logical operator is already fulfilled for the first operand and or fails, then the second operand is no longer checked. In the following example, the first comparison already returns false. Because the logical AND already returns false, the second comparison is no longer checked:

```
7 < 3 && 2 < 4;
```

In practice, this behavior of PHP usually has no effect on your programming. Function calls are an exception. Here it makes sense to carry out simple comparisons first if you want to ensure that both functions are called in any case.

# 5.1.4 Binary Numbers and Bitwise Operators

The bitwise operators are rarely used. They are used to work directly at bit level. However, before you get to know the operators in more detail, you will learn the basics of bit mapping of numbers.