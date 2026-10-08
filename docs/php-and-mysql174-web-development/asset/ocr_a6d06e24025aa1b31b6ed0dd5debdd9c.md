# Table 1.4 PHP's Logical Operators

| Operator | Name | Use | Result |
|---|---|---|---|n| ! | NOT | | Returns true if $b is false and vice versa |
| && | AND | $a && $b | Returns true if both $a and $b are true; otherwise false |
| || | OR | $a || $b | Returns true if either $a or $b are both true; otherwise false |
| and | AND | $a and $b | Same as &&, with lower precedence |
| or | OR | $a or $b | Same as ||, with lower precedence |
| xor | XOR | $a xor $b | Returns true if either $a$ or $b$ is true, and false if they are true or false |

The and and or operators have lower precedence than the && and || operators. We cover precedence in more detail later in this chapter.

# Bitwise Operators

The bitwise operators enable you to treat an integer as the series of bits used to represent it. You will probably not find a lot of use for the bitwise operators in PHP, but a summary is shown in Table 1.5.

# Table 1.5 PHP's Bitwise Operators

| Operator | Name | Use | Result |
|---|---|---|---|n| & | Bitwise AND | $a & $b | Bits set in $a and $b are set in the result |
| | | Bitwise OR | $a | $b | Bits set in $a or $b are set in the result |
| - | Bitwise NOT | -$a | Bits set in $a are not set in the result and vice versa |
| ^ | Bitwise XOR | $a ^ $b | Bits set in $a or $b but not both are set in the result |
| << | Left shift | $a << $b | Shifts $a left $b bits |n| >> | Right shift | $a >> $b | Shifts $a right $b bits |

# Other Operators

In addition to the operators we have covered so far, you can use several others.

The comma operator (,) separates function arguments and other lists of items. It is normally used incidentally.