# Chapter 3: PHP Language Basics

| Operator | Description | Example |
| --- | --- | --- |
| ^ (Xor) | Bits set in either value (but not both) are set in the result | 14 ^ 3 = 13
00001110 | 00000011 = 00001101 |
| ~ (Not) | Bits that are not set in the result, and vice versa | ~14 = -15
-0000000000000000000000001110=
1111111111111111111111110001 |
| << (Shift left) | Shifts all bits in the first value a number of places to the left (specified by the second value) | 3 << 2 = 12
00000011 << 2 = 00001100 |
| >> (Shift right) | Shifts all bits in the first value a number of places to the right (specified by the second value) | 8 >> 2 = 2
00001000 >> 2 = 00000010 |

You can see that (Not) inverts all the bits in the number. Notice that PHP uses 32-bit integers. (The other examples show only the last 8 bits of each value, for brevity.) The resulting values (1111111111111111111111110001) represent -15, because PHP uses the two's complement system to represent negative numbers (http://en.wikipedia.org/wiki/Two%27s_complement_for_explanation_of_two%27s_complement).

A common usage of bitwise operators is to combine values together to make a bit mask. For example, consider the constants representing PHP's error levels (described in detail in Chapter 20). The E_NOTICE constant has an integer value of 8 (00001000 in binary), and the E_PARSE constant has an integer value of 4 (00000100 in binary). To combine these two constants that both E_NOTICE and E_PARSE levels are reported, you'd use the (bitwise OR) operator:

+   - E_NOTICE | E_PARSE

This combines the bits of the two integers constants together to create a new integer (12) whose bit values represent E_NOTICE (8) and E_PARSE (4):

```
00001000 (8) | 00000100 (4) = 00001100 (12)
```

# Comparison Operators

As you might imagine from the name, comparison operators let you compare one operand with the other in various ways. If the comparison is successful, the expression evaluates to true; otherwise, it evaluates to false. You often use comparison operators with decision and looping statements such as if and while (these are covered in Chapter 4).