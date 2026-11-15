```
  1 1 0 1
+ 1 1 0 1
---------
  1 0 1 0
```

The result is 0b1010, or decimal 10.

# 5.9 SHIFTERS FOR MULTIPLICATION AND DIVISION

In computer architecture, a shifter shifts bits in a register left or right by a specified number of positions. Bit-shifting is an efficient way for the machine to do multiplication and division. Each left shift doubles a binary number. Each right shift halves a binary number.

A logical left-shift is symbolized by <<, and a logical right-shift is symbolized by >>. Each logical shift operation moves bits to the next place, with 0s shifted in. If the next place is beyond the width of the bit field, then those bits may be discarded. For a right-shift, a 0 becomes the most significant bit. For a left-shift, a 0 becomes the least significant bit.

For example, two logical right shifts of 1111 result in 0011.

```
11112 >> -> 0011
```

Conversely, two logical left shifts of 1111 result in 1100.

```
11112 << -> 1100
```

Another type of shift is an arithmetic shift, symbolized by <<< and >>>. These maintain the sign bit of signed (non two's-