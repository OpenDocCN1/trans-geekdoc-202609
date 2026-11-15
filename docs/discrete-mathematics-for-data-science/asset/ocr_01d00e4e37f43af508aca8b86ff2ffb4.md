4. Putting all of those parts together, with a sign bit in front, gives us:
0 10000101 1110110111101100 00000000, which is concatenated as: 010000010111101101111011011010000000000000
Represented as bytes, we would have:
01000010 111101110 1111011000 00000000

# 4.6 SIMPLISTIC CONVERSIONS

Given smaller registers, such as 8 or 16 bit, one approach is to not use IEEE 754, but to instead scale the number by a magnitude large enough to eliminate the floating point. For example, the floating point number 3.625 can be scaled up by multiplying it by 1000, making it 3625.

3With IEEE 754 for binary32, that fractional 0d0.456 is actually: 0b011110100101111000110101001111110111110011101110111001001. But, we truncated that long bit string to 8 bits to avoid the tedium of calculations by hand.

Alternatively, we could first convert the real number 3.625 to fixed point binary, where one 4-bit register is used to represent the whole number part, and another 4-bit register is used to represent the floating point decimal part.

We already know that 3 decimal is 0011 in binary. Using a table representing components of the power method, lets convert 0.625 to binary as well:

| | 2⁻¹ | 2⁻² | 2⁻³ | 2⁻⁴ |
|---|---|---|---|---|
| | 0.5000 | 0.2500 | 0.1250 | 0.0625 |
| 0.625 >= 0.5000? | 1 | | | |
| 0.125 >= 0.2500? | | 0 | | |
| 0.125 >= 0.1250? | | | 1 | |