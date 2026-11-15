1. Divide 19 by 8 to get a quotient of 2 with a remainder of 3.
2. Divide the prior quotient of 2 by 8. Since 2 is less than 8, the remainder is 2 (the same as the previous quotient).

Therefore, 0d19 = 0o23.

**Problem:** Convert 0d127 to base 8 using the remainder method.

+   1. Divide 127 by 8 to get a quotient of 15 and a remainder of 7.
+   2. Divide the prior quotient of 15 by 8 to get a quotient of 1 and a remainder of 7.
+   3. Divide the prior quotient of 1 by 8 to get a quotient of 0 and a remainder of 1. Note that since the prior quotient was less than 8, the prior quotient is the same as the remainder, 1, in this step. We could just skip this step and use the prior quotient for this position.

Therefore, 0d127 = 0o177.

# 4.4 MACHINE REPRESENTATION OF NEGATIVE NUMBERS

In computing systems, negative numbers may be represented using various conversions, the following of which we cover:

+   - Signed Magnitude.
+   - One's Complement.
+   - Two's Complement.
+   - The IEEE 754 Floating Point Standard.

A computing system will be designed to deal with one of those representations. That said, most commercial computers today implement the IEEE 754 Floating Point Standard.

Since machines really only perform addition, “subtraction” is actually the addition of a number that has been made negative.