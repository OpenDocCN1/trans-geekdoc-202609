Finally, discard the implicit leading bit of the mantissa to convert the number back into the binary32 fraction:

| sign | exponent | fraction (ignoring the implicit leading bit) |
|---|---|---|
| 0 | 10000001 | 000 0001 0000 0000 0000 0000 |

# 5.14 DIVISION WITH IEEE 754 FLOATING POINT NUMBERS

Division with IEEE 754 floating point numbers can be done by hand by dividing the fractions and then subtracting the exponents. Division is done by right shifts, denoted as >>, and subtraction.

For example, to compute C = A/B:

C = 1^signA×1×(fractionA×2^exponentA) / -1^signB×1×fractionB×2^exponentB

C = -1^signC×1×(fractionA / fractionB) × 2^exponentA-exponentB

where:

signC = exponentA XOR exponentB

and:

fractionC = fractionA / fractionB

That is a right shift of fractionA by the amount of fractionB:

(fractionB - 1) >> fractionA

The resulting exponent is:

exponentC = (exponentA - exponentB) + bias