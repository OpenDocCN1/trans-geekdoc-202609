| Operator | Example | Description |
| :--- | :--- | :--- |
| `&` | `1010 & 0011
//Result: 0010 = 2` | Bitwise AND; writes a 1 to the places where both operands have a 1. |
| `|` | `1010 | 0011
//Result: 1011 = 11` | Bitwise OR; writes a 1 to the positions where one or both operands contain 1. |
| `^` | `1010 ^ 0011
//Result: 1001 = 9` | Bitwise EITHER OR; writes a 1 to the bits where only one of the two operands has a 1. |
| `~` | `~1010
//Result: 0101 = -11` | Bitwise negation; converts a 0 into a 1 and a 1 into a 0. However, the base is an integer with 32 bits (signed), which is why the result is not a direct inversion of the value. |
| `<<` | `1010 << 1
//Result: 10100 = 20` | Bitwise shift to the left; shifts the binary pattern of the left operand to the left by the digits specified in the right operand. The right-hand side is filled with zeros. The shift by one place corresponds to multiplication by 2, by two places to multiplication by 4, by three places to multiplication by 8, and so on. |
| `>>` | `1010 >> 1
//Result: 0101 = 5` | Bit-by-bit shift to the right by the digits specified by the right operand. The bits that remain on the right are deleted. If the left operand has a negative sign, the left side is filled with ones, otherwise with zeros. Shifting by one bit corresponds to division by 2 (without remainder), shifting by two bits corresponds to division by 4, shifting by four bits corresponds to division by 8, and so on. |

# Table 5.5 The Bitwise Operators

> The bitwise shift is one of the most frequently used bitwise operators as it offers a simple option for division and multiplication by powers of two.

All binary operators are also available in the short form with the assignment operator. The following lines change the value of the $a variable from 10 to 40:

```
$a = 10;
$a <<= 2;
```