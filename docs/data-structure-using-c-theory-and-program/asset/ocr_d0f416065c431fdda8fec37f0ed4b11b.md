# Chapter 4 Stack

c. If a right parenthesis is the current symbol, pop the stack down to (and including) the left parenthesis. Write all the symbols except the left parenthesis to the output (i.e. write the operators to the output).

d. After the last token is read, pop the remainder of the stack and write any symbol (except left parenthesis) to output.

# Q1. P + Q - R

Solution: (PQ+) - R where X=PQ+

X - R-
XR-

Put the value of X, we get
PQ + R-

# Q2. P * Q + R / S

Solution: P*Q + RS/ where X=RS/

P*Q+X
PQ* +X where Y=PQ*
Y+X
YX-

Put the value of X and Y, we get
P Q * RS / +

# Q3. (P + Q) * R / S + T ^ U / V

Solution: (PQ+) * R/S+T^U/V where A=PQ+

A * R / S + ( T U ) / V where B=TU^
A * R / S + B / V where C=RS/
A * ( RS ) + B / V where D=BV/
A * C + ( BV ) /
A * C + D

( AC*) + D where E=AC*
E + D\ED +

Put the values of A, B, C, D, E, we get
AC * D + 
PQ + C * D +
PQ + RS / * BV / +
PQ + RS / * TU^ / +