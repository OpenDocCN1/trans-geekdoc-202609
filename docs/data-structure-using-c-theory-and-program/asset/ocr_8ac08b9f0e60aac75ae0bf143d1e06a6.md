# Chapter 4 Stack

175

+   28. end of step 25 loop

+   29. end of step 23 if structure

+   30. end of step 4 loop

+   31. stop

Example: Consider the following arithmetic infix expression Arithmetic Expression AE: P + (Q * R – (S / ^) * V) * W

| Symbol Scanned | Stack | Expression (Postfix) |
| --- | --- | --- |
| P | ( | P |
| + | (+ | P |
| ( | (+ | P |
| Q | (+ | PQ |
| * | (+* | PQ |
| R | (+* | PQR |
| - | (+- | PQR* |
| ( | (+-(- | PQR* |
| S | (+-(- | PQR*S |
| / | (+-(-/ | PQR*S |
| T | (+-(/T | PQR*ST |
| ^ | (+-(/^ | PQR*ST |
| U | (+-(/^ | PQR*STU |
| ) | (+- | PQR*STU^/ |
| * | (+-* | PQR*STU^/ |
| V | (+-* | PQR*STU^/V |
| ) | (+ | PQR*STU/V*- |
| * | (+* | PQR*STU/V*- |
| W | (+* | PQR*STU/V*-W |
| ) | | PQR*STU/V*-W++ |

# Program: Write a program to convert infix expression to postfix expression

```
#include<stdio.h>
#include<ctype.h>
#include<string.h>
int top=-1,i=0,l;
```