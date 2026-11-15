A bit assumes the values 0 or 1. As there are two possible values, this is also called a binary value. The corresponding notation for data is binary notation. Every integer can be written in bits.

The binary notation consists of a pattern. The pattern has as many digits as the number has bits. A number with four bits therefore has four digits and can represent 2^4 numbers—that is, 16 numbers.

0010 stands for the number 2. The bit pattern is read from right to left. The right-hand number stands for 1, the second from the right for 2, the third for 4, the fourth for 8—and so on. These numbers are added together to give the integer.

Consider some examples:

+   1111 stands for 8 + 4 + 2 + 1, which equals 15.

+   1010 stands for 8 + 0 + 2 + 0, which equals 10.

> Note
> In PHP, you can also enter numbers directly in binary notation. To do this, the number is preceded by 0b—for example, 0b1111 for 15.

The bitwise operators work with integers as binary patterns. The bitwise AND (&) sets a 1 wherever both operands have a 1.

```
10 & 3
```

is therefore first converted internally by PHP into this binary pattern:

```
1010 & 0011
```

Or you can write directly:

```
0b1010 & 0b0011
```

The comparison does not result in a 1 for both operands at the first position from the right. Therefore, the number resulting from the comparison is 0 at this position. At the second position, both operands have a 1, so the result is 1. If this continues, the following binary pattern is created:

```
0b0010
```

This corresponds to the integer 2.

Table 5.5 shows all bitwise operators with simple examples in binary patterns. To implement the examples in PHP, you must write the binary patterns as integers.