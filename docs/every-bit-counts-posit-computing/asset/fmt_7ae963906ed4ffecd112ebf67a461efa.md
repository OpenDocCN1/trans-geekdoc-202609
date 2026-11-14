
![Square root rounding error for 8-bit posits (magenta) and 8-bit fixed-point (blue)](images/pg36_1.jpg)

Square root rounding error for 8-bit posits (magenta) and 8-bit fixed-point (blue)

While this shows posits to be superior for square root operations for accuracy, remember that the hardware for fixed-point arithmetic is simpler and faster than that for posits, so there is an engineering tradeoff.

### 2.10.2 A Two-Input Example: Multiplication

For two-input functions (like `a + b`, `a − b`, `a × b`, `a / b`, and `a^b`) and small sets of possible inputs, we can exhaustively tabulate the errors for all possible pairs of inputs. Let's try that with multiplication, again comparing `fixed8` and `posit8`. It is sufficient to test the nonnegative numbers since negating an input does not change the error. But unlike the square root, it is possible for multiplication to overflow or underflow. We can count the number of times that the result

*   overflows
*   underflows
*   is exactly representable in the format
*   is rounded to the nearest number in the format

In the last case, we compute the relative error from rounding, and find the worst-case relative error, and the average error including results with no error (exact). Start with `fixed8`.

![Sorted errors for 8-bit fixed-point multiplication (much of the graph is off-scale)](images/pg37_1.jpg)

Sorted errors for 8-bit fixed-point multiplication (much of the graph is off-scale)

If we lay out the multiplication table graphically, using colors to indicate what happens to this imperfect representation of real values, it looks like this:

| Exact | Rounded | Underflow | Overflow |
| --- | --- | --- | --- |
| 1197 | 10503 | 20 | 4664 |
| 7% | 28% | 0.12% | 64% |

![Closure plot for 8-bit fixed-point multiplication](images/pg38_1.jpg)

Closure plot for 8-bit fixed-point multiplication

The `black` pixels indicate an exact result, that is, cases where the product just happens to be exactly representable as a fixed-point number. `Light Blue` indicates overflow, which occurs for an alarmingly large fraction of the multiplication table. `Red` indicates underflow. Both use the careful definition that the number cannot legitimately round to the nearest representable real. The `green` pixels are where the result is rounded to a number that the format can represent; the brighter the color, the larger the relative error.

For the `posit8` set, the average relative error appears to be greater at first glance:

![Sorted errors for 8-bit posit multiplication](images/pg39_1.jpg)

Sorted errors for 8-bit posit multiplication

However, that is a small price to pay for a massive increase in the resilience to overflow, as the graphical table of errors from multiplication shows:

| Exact | Rounded | Underflow | Overflow |
| --- | --- | --- | --- |
| 1992 | 14151 | 119 | 122 |
| 12% | 86% | 0.73% | 0.74% |

![Closure plot for 8-bit posit multiplication](images/pg39_2.jpg)

Closure plot for 8-bit posit multiplication

The area of overflow has been reduced to a tiny fillet in the table, very similar (but not identical) to the area of underflow.

Now that we are armed with tools for measuring inaccuracy accurately, we can start comparing number formats and ways to use them for calculations.

![](images/pg40_1.jpg)

# 3 More Power!

![Exponentially increasing power in the classic 1956 sci-fi movie Forbidden Planet](images/pg41_1.jpg)

Exponentially increasing power in the classic 1956 sci-fi movie *Forbidden Planet*

The first explanations of the full posit format were published in 2017, and in the intervening years much has improved about how to explain it more clearly. If you have already seen explanations of the posit format, do not be surprised if the following differs slightly from the early papers on the subject.

## 3.1 Increasing Posit Dynamic Range

Start with a three-bit posit ring, but instead of the regime bits representing a power of 2, let them represent a power of 2² = 4. That doubles the dynamic range:

![Squaring the northwest value (and adjusting the reflected values) doubles dynamic range.](images/pg41_2.jpg)

Squaring the northwest value (and adjusting the reflected values) doubles dynamic range.

It also creates a new rule for inserting values when we append bits. As usual, appending a `0` bit does not change the value; but when we append a `1` bit we now can insert an integer power of 2 between the values.

![Between powers of 2 that differ by more than 1 in the exponent, insert the geometric mean.](images/pg42_1.jpg)

Between powers of 2 that differ by more than 1 in the exponent, insert the geometric mean.

When a bit is appended after a regime termination bit, we call that an `exponent bit` and color code it in `blue`. If it is a `1` bit, the flanking values are `2^k` and `2^m` and the inserted value is `2^((k+m)/2)`. The regime bits now serve as a kind of super-exponent, where the value they represent is a power of 4 scaling, not a power of 2. The exponent bit then lets us fill in the gap between 1 and 4, or between 1/4 and 1. To make it clearer, we can append one more bit so that some fraction bits appear for magnitudes 1/4 to 3 (shown in `black` as usual). The exponent bit lets us fill the gap between 4 and 4² = 16 with 4² · 2¹ = 8. Integer powers of 2 still have perfect reciprocals, their mirror image about the horizontal axis. The mapping to 2's complement integers is still monotone, as shown in this ring plot:

![Ring plot of 5-bit posits with 1 exponent bit](images/pg42_2.jpg)

Ring plot of 5-bit posits with 1 exponent bit

Suppose we want still more dynamic range. We can square the meaning of each regime bit again, to 4² = 16, so the value in the northeast position is 16. To fill in between 16⁰ = 1 and 16¹ = 16 means scaling by 1, 2, 4, or 8, that is, `2^e` where `e` ranges from 0 to 3. As an unsigned binary, we can do that with exponent bits `00`, `01`, `10`, and `11`. Here is the ring plot for a 5-bit posit with a 2-bit exponent field:

![Ring plot of 5-bit posits with 2 exponent bits](images/pg43_1.jpg)

Ring plot of 5-bit posits with 2 exponent bits

The number of bits in the exponent field is `eS`, short camelCode for `exponentSize`. The value in the northeast position is called the `uSeed`, and it is equal to `2^(2*eS)`. Every time `eS` goes up by 1, the `uSeed` is squared and the dynamic range doubles in size, at the expense of taking away one bit from the significant bits in the fraction part. As `eS` increments starting at 0, `uSeed` is 2, 4, 16, 256, 65 536,… a *very* rapidly-increasing series. Be careful with it.

[Chapter 1](#chapter1.xhtml) introduced the simplest form of posit with no exponent bits (`eS` = 0), but by introducing exponent bits we have considerably more power. Here are the complete rules for introducing new values on the posit ring as the precision `n` grows:

*   Appending a `0` bit to an existing posit does not change the represented value.
*   Between `NaR` and a real number, insert the real number times `uSeed`.
*   Between 0 and a real number, insert the real number divided by `uSeed`.
*   Between `2^k` and `2^m` where `k` and `m` differ by more than one, insert `2^((k+m)/2)`.
*   Otherwise, between `x` and `y`, insert their average, `(x + y)/2`.

We also generalize the formula for a posit value. With `eS` = 0 in [Chapter 1](#chapter1.xhtml), we had
