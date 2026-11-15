| float | multiplier | result | whole part | float part | binary result |
|---|---|---|---|---|---|
| | | | 1 | 0.33 | 1. |
| 0.33 | ×2 | 0.66 | 0 | 0.66 | 0 |
| 0.66 | ×2 | 1.32 | 1 | 0.32 | 1 |
| 0.32 | ×2 | 0.64 | 0 | 0.64 | 0 |
| 0.64 | ×2 | 1.28 | 1 | 0.28 | 1 |

The binary equivalent of the result of 4 ÷ 3 is 1.0101. Of course, the number of repeating digits is limited by the width of the bit field, which in this case is four bits wide.

To convert back to decimal, establish values and indices to the right of the decimal. For precision to four decimal places, the exponents are 4 3 2 1 0 -1 -2 -3 -4. Applied as 2⁴ 2³ 2² 2¹ 2⁰ 2⁻¹ 2⁻² 2⁻³ 2⁻⁴, the resulting series is 16 8 4 2 1 0.5 0.25 0.125 0.0625.

Looking at that series, the applicable exponents for the floating point binary number 1.0101 are 0 -2 and -4, such as:

```
1 × 2⁰ + 0 × 2⁻¹ + 1 × 2⁻² + 0 × 2⁻³ + 1 × 2⁻⁴
```

which results in 1.25 + 0.06235 = 1.31235, not the expected 1.333....

Thus, we had some precision loss converting back to decimal.

# 5.13 ARITHMETIC ON IEEE 754 FRACTIONAL VALUES

We might attempt binary arithmetic on floating point numbers as performed above by hand, aligning the respective decimal points of the operands. That approach is tedious and error prone,