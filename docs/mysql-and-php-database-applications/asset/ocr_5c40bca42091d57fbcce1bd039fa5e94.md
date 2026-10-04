# Part V: Appendixes

TABLE E-22 BCMATH FUNCTIONS
| Function | Returns | Action |
| --- | --- | --- |
| bcsub(string left_operand, string right_operand [, int scale]) | string | Returns the difference between two arbitrary-precision numbers |
| bcmul(string left_operand, string right_operand [, int scale]) | string | Returns the multiplication of two arbitrary-precision numbers |
| bcdiv(string left_operand, string right_operand [, int scale]) | string | Returns the quotient of two arbitrary-precision numbers (division) |
| bcmod(string left_operand, string right_operand) | string | Returns the modulus of the two arbitrary-precision operands |
| bcpow(string x, string y [, int scale]) | string | Returns the value of an arbitrary-precision number raised to the power of another |
| bcqsrt(string operand [, int scale]) | string | Returns the square root of an arbitrary-precision number |
| bbcc(string left_operand, string right_operand [, int scale]) | string | Compares two arbitrary-precision numbers |
| bcscale(int scale) | string | Sets default scale parameter for all bc math functions |

> Note Use of the bcmath functions requires PHP to be complied with --enable-bc-math.

TABLE E-23 CALENDAR FUNCTIONS
| Function | Returns | Action |
| --- | --- | --- |
| jdtounix(int jday) | int | Converts Julian Day to Unix timestamp |