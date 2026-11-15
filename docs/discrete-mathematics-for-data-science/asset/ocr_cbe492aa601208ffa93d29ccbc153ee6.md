+   4. Repeat steps 2 and 3 until through all of the multiplier digits.
+   5. Sum up the resulting partial products (apply the binary addition rules) to get the result.

For example, let's multiply 4 times 5, in binary.

```
   1 0 0
 x   1 0 1
 -------
   1 0 0
 0 0 0
1 0 0
 -------
1 0 1 0 0
```

That is 20 in decimal.

# 5.4 BINARY DIVISION

The rules of binary division, with postfix expressions:

| Expression | Result |
|---|---|
| 0 0 ÷ | undefined |
| 0 1 ÷ | 0 |
| 1 0 ÷ | undefined |
| 1 1 ÷ | 1 |

Long division with binary numbers is just like long division of decimal whole numbers. For example, let's divide 20 by 4, in binary (0b10100 ÷ 0b100).