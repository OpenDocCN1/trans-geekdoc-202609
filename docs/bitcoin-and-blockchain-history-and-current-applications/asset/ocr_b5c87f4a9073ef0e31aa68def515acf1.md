# 8.4.3.3 Logical Operators

# TABLE 8.6
Logical Operators

| Operations | Symbol | Explanation | Example (X = 10, Y = 5) |
|---|---|---|---|
| Logical AND | && | Returns true only when both operands are true, otherwise false | X && X, will return true
X && Y, will return false |
| Logical OR | || | Returns true even when one operand is true, otherwise false | X || Y, will return true
Y || Y, will return false |
| Logical NOT | ! | Returns true even when one operand is true, otherwise false | !(X), will return false
!(Y), will return true |

# 8.4.3.4 Assignment Operators

# TABLE 8.7
Assignment Operators

| Operations | Symbol | Explanation | Example (A = 10 and B ≡ 5) |
|---|---|---|---|
| Simple assignment | = | Assigns a value to a variable | A = B, now the value of both A and B is 5 |
| Add and assignment | += | Adds and assigns to a variable | A += B, means A = A + B, which is 15 |
| Subtraction and assignment | -= | Subtracts and assigns to a variable | A -= B, means A = A - B, which is 5 |
| Multiplication and assignment | *= | Multiplies and assigns to a variable | A *= B, means A = A * B, which is 50 |
| Division and assignment | /= | Divides and assigns to a variable | A /= B, means A = A / B, which is 2 |
| Modulus and assignment | %= | Finds Modulus and assigns to a variable | A %= B, means A = A%B, which is 0 |

# 8.4.3.5 Conditional Operator (? : (conditional))

If condition is true? The value X : Otherwise Y.

For Example:

+   i. A = (5==5)? 10 : 20, here the value of A will be assigned 10, as the condition is true.
+   ii. B = (5==10)? 10 :20, here the value of B will be assigned 20, as the condition is false.

# 8.5 CONTROL STRUCTURES

Solidity establishes control structures like other curly bracket languages. It implements if, else, else if, while, do, for, continue, and break semantics similar to C or JavaScript.

Let us understand the syntax for each type.