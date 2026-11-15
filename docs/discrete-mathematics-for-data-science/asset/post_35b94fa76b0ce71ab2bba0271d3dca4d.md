
1 0 1
_______
1 0 0 | 1 0 1 0 0 0
      - 1 0 0
      -------
        1 0 0 0
      -   1 0 0
      ---------
            0

That is, 0b10100 ÷ 0b100 = 0b101.

Due to the tedium of computing binary multiplication and division by hand, it seems more reasonable to define algorithms that utilize repeated addition and subtraction. After all, this is essentially what computers do. In that regard, please refer to *Machine Approaches to Multiplication & Division* section below.

## 5.5 BOOLEAN LOGIC

Boolean logic is the conceptual basis for digital logic, which takes a binary input, such as 0 or 1 representing true or false, and outputs a binary result. Only a few rules of digital logic are needed for some complex decision making in general purpose computers.

In order of simplicity, the typical digital logic conditions are NOT, AND, OR, XOR, NAND, NOR and XNOR. These are described as follows using data x and output y.

### NOT

NOT inverts a single input. Thus, it is also called an inverter. It is commonly symbolized by the ¬ character and has the following functional form:

y = ¬x

Or:

x NOT

The tabular form representing all input combinations for NOT:

| X | ¬X |
|---|---|
| 0 | 1 |
| 1 | 0 |

### AND

AND yields 1 (true) if both of its two input values are true. It is commonly symbolized by the × character and has the following functional form:

y = x₁ × x₂

Or:

x₁ x₂ AND

Note the use of × for both binary multiplication and logical AND. Both yield the same result for single bit operands.

The tabular form representing all input combinations for AND:

| x₁ | x₂ | y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

### OR

OR yields 1 (true) if either of the input values is true. It is commonly symbolized by the + character and has the following functional form:

```
y = x₁ + x₂
```

Or:

x₁ x₂ OR

The tabular form representing all input combinations for OR:

| x₁ | x₂ | y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

### XOR

XOR (exclusive or) yields 1 (true) if only one of the input values is true. It is commonly symbolized by the ⊕ character and has the following functional form:

$$y = x_1 \oplus x_2$$

Or:

$x_1 \ x_2 \ \text{XOR}$

The tabular form representing all input combinations for XOR:

| $x_1$ | $x_2$ | $y$ |
| :---: | :---: | :---: |
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Note the use of $\oplus$ for both binary addition and logical XOR. Both yield the same result for single bit operands.

### NOR

NOR inverts the result of OR. It has the following functional form:

$$y = \neg(x_1 + x_2)$$

Or:

$x_1 \ x_2 \ \text{NOR}$

The tabular form representing all input combinations for NOR:

| x₁ | x₂ | y |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |

### NAND

NAND inverts the result of AND. It has the following functional form:

$y = \neg(x_1 \times x_2)$

Or:

$x_1 x_2$ NAND

The tabular form representing all input combinations for AND have an opposite result for y in NAND:

| x₁ | x₂ | y |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

### XNOR

XNOR inverts the result of XOR. It has the following functional form:

$y = \neg(x_1 \oplus x_2)$

Or:

$x_1 x_2$ XNOR

The tabular form representing all input combinations for XNOR:

| x₁ | x₂ | y |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

## 5.6 MACHINE APPROACHES TO MULTIPLICATION & DIVISION

Machine arithmetic is done using register shifts as well as repeated addition and subtraction operations. A counter register (or variable) is also used. As mentioned in the Numbers chapter, a computer's Central Processing Unit (CPU) operates on binary numbers in CPU registers, a series of 1s and 0s.

Machine multiplication done using only repeated addition stores intermediate results in an accumulator register or variable until the count equals the multiplier. For example, 5 × 3 in binary is effectively:

```
  0 0 0 0
+ 0 1 0 1
---------
  0 1 0 1 <- interim accumulation
+ 0 1 0 1
---------
  1 0 1 0 <- interim accumulation
+ 0 1 0 1
---------
  1 1 1 1 <- final accumulation, 3 steps
```

Machine division is done similarly. Store the intermediate results of repeated subtraction in the accumulator until the accumulator is 0 or less. For example, 15 ÷ 5 in binary is effectively:

```
  1 1 1 1
- 0 1 0 1
---------
  1 0 1 0 <- interim accumulation
- 0 1 0 1
---------
  0 1 0 1 <- interim accumulation
- 0 1 0 1
---------
  0 0 0 0 <- final accumulation, 3 steps
```

Such repetitive algorithms can be implemented in a programming language. For example, the following pseudo-code computes 5 × 4 using repeated additions, effectively 5 + 5 + 5 + 5.

```
five = 5 ( Initialize variable.)
accumulator = 0 ( Initialize accumulator variable.)
counter = 4 ( Initialize counter variable.)
```

```
while counter < five { ( Repeat until counter is 0.)
accumulator = accumulator + five ( Add five to accumulator.)
counter = counter + 1 ( Increment counter by 1.)
}
```

For the same 4 x 5 operation, multiplication by repeated addition can be represented by the following epop code.

```
0 { 5 + } 4 LREPEAT
```

The general form for division by repeated subtraction, assuming positive numbers, is:

```
divisor = 4 ( Initialize variable.)
dividend = 20 ( Initialize variable.)
quotient = 0 ( quotient will be counter and result.)
```

```
while dividend >= divisor { ( Repeat until dividend >= divisor.)
dividend = dividend - divisor ( Subtract divisor from dividend.)
quotient = quotient + 1 ( Increment counter by 1.)
}
```

The answer is the final quotient. The remainder is the final dividend.

Division by repeated subtraction can be represented by the following epop code, which determines how many times 4 goes into 20 (Note the recursive word 20div4).

```
20 dividend !
4 divisor !
0 quotient !
{ quotient @ 1 + quotient } quotient+ WORD
{ quotient+ dividend @ divisor @ - dividend ! } next WORD
{ next dividend @ divisor @ >= 20div4 ? } 20div4 WORD
```

## 5.7 BINARY SUBTRACTION USING ONE'S COMPLEMENT

The algorithm for subtraction using one's complement is as follows:

- 1. Take the one's complement of the subtrahend.
- 2. Add the result from step 1 to the minuend.
- 3. Add any overflow from step 2 to the non-overflow result in step 2.

For example, consider 13 minus 3 in binary using one's complement.

```
  1 1 0 1
- 0 0 1 1
---------
```

Compute one's complement of the subtrahend, flipping its 1s to 0s and its 0s to 1s. For this we can perform an XOR operation, symbolized by ⊕, versus a bitmask of 1111, which will invert each bit from its current state.

```
  0 0 1 1
⊕ 1 1 1 1
———
  1 1 0 0
```

Add the result to the minuend, noting the overflow on the left.

```
  1 1 0 1
+ 1 1 0 0
———
1 1 0 0 1 ← leftmost overflow from here
+ 0 0 0 1 ← ...added here
———
  1 0 1 0
```

¹A bitmask is a bit sequence that is useful for setting or clearing certain bits of binary number.

## 5.8 BINARY SUBTRACTION USING TWO'S COMPLEMENT

We covered two's complement numbers in the _Number Conversion_ chapter. Recall that to find the two's complement, we add 1 to the one's complement.

Using two's complement, we can obtain the difference of two positive numbers. The procedure entails adding the two's complement of the subtrahend to the minuend.

Binary subtraction of two negative numbers that are not already in two's complement notation, requires taking the two's complement of both the minuend and the subtrahend, and then adding the results.

For example, consider 13 minus 3 in binary using two's complement.

```
1 1 0 1
- 0 0 1 1
-----------
```

Compute two's complement of the subtrahend. First, take the one's complement, inverting via an XOR with a bitmask of 1111, as discussed for one's complement above.

```
0 0 1 1
⊕ 1 1 1 1
-----------
1 1 0 0
```

Next, add one to the result:

```
1 1 0 0
+ 0 0 0 1
-----------
1 1 0 1
```

Add the result to the minuend, ignoring the 1-bit overflow assuming a 4-bit wide register).
