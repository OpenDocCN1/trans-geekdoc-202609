
  1 1 0 1
+ 1 1 0 1
---------
  1 0 1 0

The result is 0b1010, or decimal 10.

## 5.9 SHIFTERS FOR MULTIPLICATION AND DIVISION

In computer architecture, a shifter shifts bits in a register left or right by a specified number of positions. Bit-shifting is an efficient way for the machine to do multiplication and division. Each left shift doubles a binary number. Each right shift halves a binary number.

A logical left-shift is symbolized by <<, and a logical right-shift is symbolized by >>. Each logical shift operation moves bits to the next place, with 0s shifted in. If the next place is beyond the width of the bit field, then those bits may be discarded. For a right-shift, a 0 becomes the most significant bit. For a left-shift, a 0 becomes the least significant bit.

For example, two logical right shifts of 1111 result in 0011.

```
1111₂ >> -> 0011
```

Conversely, two logical left shifts of 1111 result in 1100.

```
1111₂ << -> 1100
```

Another type of shift is an arithmetic shift, symbolized by <<< and >>>. These maintain the sign bit of signed (non two's complement) numbers by filling shifted bits with a copy the sign bit, be it 0 or 1.²

²It should be noted that in some architectures a left-arithmetic shift gives the same result as a left-logical shift.

For example, two arithmetic right shifts of 1000 result in 1110.

```
1000₂ >>> → 1110
```

Conversely, two arithmetic left shifts of 0111 result in 0100.

```
0111₂ <<< → 0100
```

## 5.10 MULTIPLICATION BY LEFT-SHIFT & ADDITION

Multiplication at the machine level can be accomplished with a combination of left-shifting and addition.

One left shift doubles a number, meaning the number is multiplied by 2¹. Two left shifts double a number twice, meaning the number is multiplied by 2². In general, N left shifts multiply a number by a factor of 2ᴺ.³

To emulate a machine's multiplication by left-shift & addition, consider the doubling progression of magnitudes of 2^i, for i = 0 to N - 1. Thus, for a 5-bit number, we have 5 multiplier bits in positional alignment with the progression 16 8 4 2 1, where the least significant digit is the rightmost digit where i = 0. N = 5

In decimal terms, the effects of binary left-shift & addition operations on a decimal number are:

\(\sum_{i=0}^{N-1} multiplier\_bit_i \times multiplicand_{10} \times 2^i\)

where _i_ represents the position of the bits in the binary multiplier, from right to left.

Thus, for an operation of 0d3 × 1, we have 1 × 3 × 2⁰ = 0d3, or 0b11, as no shift occurred. (In 0b11, _i_₀ = 1 and _i_₁ = 1.)

For 0d3 × 0d2, we have 0 × 3 × 2⁰ + 1 × 3 × 2¹ = 0d6, or 0b110, as one shift occurred and it doubled the number. (In 0b110, _i_₀ = 0, _i_₁ = 1, and _i_₂ = 1.)

| i | bit_i | 2^i |
|---|---|---|
| 0 | 1 × 3 × 2⁰ = 3 | |
| 1 | 1 × 3 × 2¹ = 6 | |
| 2 | 0 × 3 × 2² = 0 | |
| 3 | 0 × 3 × 2³ = 0 | |
| | sum = 9 | |

³The same effect applies to other bases. Recall the power series of baseⁱ.

We could continue with this progression of shifts and additions until overflowing the register capacity of the machine, which would mean losing some significant digits.

## 5.11 DIVISION BY RIGHT-SHIFT & SUBTRACT

Division at the machine level can be accomplished with a combination of right-shifting and subtraction.

One right shift halves a number, meaning the number is divided by 2¹. Two right shifts halve a number twice, meaning the number is divided by 2². In general, N right shifts divide a number by 2ᴺ. However, binary division is prone to lost precision in the fractional part of numbers.⁴

To emulate a machine's division by right-shift & subtraction, consider the doubling progression of magnitudes of 2ⁱ for i = N − 1 to 0. Thus, for a 5-bit number, we have 5 divisor bits in positional alignment with the progression 16 8 4 2 1, where the least significant digit is the rightmost digit where i = 0. N = 5

In decimal terms, the effects of binary right-shift & subtraction operations on a decimal number are:

\(\sum_{i=N-1}^{0} \, divisor\_bit_i \div dividend_{10} \times 2^i\)

where i represents the position of the bits in the binary divisor, from left to right.

⁴To get more accurate floating point results, we should use numbers in the IEEE 754 Floating Point form, as shown below.

Suppose that we want to divide 0b10000 by 0b1000 (16 ÷ 8 in decimal):

| i | bit_i | 2^i |
|---|---|---|
| 3 | 1 | 1 × 16 ÷ 2³ = 2 |
| 2 | - | 0 × 16 ÷ 2² = 0 |
| 1 | - | 0 × 16 ÷ 2¹ = 0 |
| 0 | - | 0 × 16 ÷ 2⁰ = 0 |
| | | sum = 2 |

## 5.12 PRECISION LOSS WITH RIGHT SHIFT

Because the right shift eliminates the lower bits, we lose precision. For example, a single right shift halves a number, so you might expect that a single right shift of the decimal number 7 will result in 3.5 in decimal. Consider the following postfix right-shift operation:

```
01111 >>>
```

This right shift results in 0011, or 3 in decimal, because the rightmost 1 was discarded.

Consider 4 ÷ 3. The result is the decimal 0d1.33..., which repeats infinitely. The digits to the right of the decimal place can be represented as a binary floating point number.

Let's examine the precision loss of converting 4 ÷ 3 to decimal.

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

which results in 1.25 + 0.0625 = 1.3125, not the expected 1.333....

Thus, we had some precision loss converting back to decimal.

## 5.13 ARITHMETIC ON IEEE 754 FRACTIONAL VALUES

We might attempt binary arithmetic on floating point numbers as performed above by hand, aligning the respective decimal points of the operands. That approach is tedious and error prone, requiring extra steps for negative values, such as taking their two's complement. All of this can be accomplished instead by using the IEEE 754 Floating Point Standard. This is the approach taken by modern CPUs.⁵

As an example, let's add together 0d7.875 and 0d0.1875. In fixed point binary the initial expression is:

```
111.111 + 0.0011
```

To convert fixed point binary into the IEEE 754 Standard, first convert the values into a 32-bit normalized form.⁶ Note that 111.111 can be written as:

```
1.11111 × 2²
```

Note that 2² is the largest magnitude of 2 that will go 7.875. Note that 0.0011 can be written as:

```
1.1 × 2⁻³
```

2⁻³ is the smallest magnitude of 2 that will go 0.1875.

| sign | exponent | fraction (ignoring the implicit leading bit) |
| :--- | :--- | :--- |
| 0 | 10000001 | 111 1100 0000 0000 0000 0000 0000 |
| 0 | 01111100 | 100 0000 0000 0000 0000 0000 0000 |

For the exponents, note that 10000001 is 2 + 127 in binary and 01111100 is -3 + 127 in binary.

Reminder: the exponent here is a *biased exponent*. So, to add the numbers, pre-append the implicit leading 1 to the 23 bit fraction field, which makes it the mantissa. We get:

```
0 10000001 1.111 1100 0000 0000 0000 0000
0 01111100 1.100 0000 0000 0000 0000 0000
```

Since we add numbers with common exponents, to get the exponents the same, subtract the smaller exponent from the larger exponent:

```
  1 0 0 0 0 0 0 1
- 0 1 1 1 1 1 0 0  <- replace this with
+ 1 0 0 0 0 1 0 0  <- two's complement here
-------------------
  0 0 0 0 0 1 0 1  <- sum of 1st and 3rd lines
```

Now shift the mantissa of the smaller number rightward by 5 (0b101), the difference found between the exponents. Now we can write both numbers with the same exponent:

```
0100000011.11111000000000000000000000
0100000010.000011000000000000000000 -> 00000 discarded
```

Next add the mantissas:

```
  1.111 1100 0000 0000 0000 0000
+ 0.000 1100 0000 0000 0000 0000
--------------------------------
  10.000 0010 0000 0000 0000 0000
```
