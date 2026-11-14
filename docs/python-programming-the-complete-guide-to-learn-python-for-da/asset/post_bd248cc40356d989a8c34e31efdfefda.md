

| Operation | Operator | Expression | Result type |
| :--- | :--- | :--- | :--- |
| Sum | + | a+b | Integer if a and b integers; real if any is real |
| Subtraction | - | a-b | Integer if a and b integers; real if any is real |
| Multiplication | * | a*b | Integer if a and b integers; real if any is real |
| Division, a ÷ b (integer) | / | a/b | Always real |
| Division, integer | // | a//b | Returns the whole part of the quotient a ÷ b |
| Modulo, remainder | % | a%b | Returns the rest of the division a ÷ b |
| Exponentiation, a^b | ** | a**b | Integer if a and b integers; real if any is real |

## Examples:

```
>>> 14/4 # Integer Division
3.5
>>> 14 // 4 # Division, returns whole part of dividing 14 by 4
3
>>> 14% 4 # Module, returns the rest of dividing 14 by 4
2
```

Arithmetic operators that operate on a single operand are called unary: sign change operator - and identity + operator. For example, -4, +4, --4 equals 4.

## Arithmetic operators with assignments

The action of increasing the value of a variable is very common in computer programs.

For example, in an event counter, the counter c is incremented by 1.

```
>>> c = c + 1 # the variable c is increased by 1
>>> d = d - 1   # the variable d is decremented by 1
```

Python includes statements that compact the assignment operator with any arithmetic operator. In cases of increase or decrease of a variable we have,

```
>>> c += 1      # equals: c = c + 1
>>> x += 0.01   # equals: x = x + 0.01
>>> d -= 2      # equals: d = d - 2
```

The other arithmetic operators (*, /, //, %, **) can also be used in this compacted form. Expressions such as increment, or other operation may also be included:

```
>>> y *= d+1          # equals: y = y * (d + 1)
>>> n = 7
>>> n //= 2           # equals: n = n // 2
>>> n
3
>>> n **= 2           # equals: n = n ** 2
>>> n
9
```

| Operation | Operator | Expression | Equals to |
|---|---|---|---|
| Add and assign | += | a += b | a = a+b |
| Subtract and assign | -= | a -= b | a = a-b |
| Multiply and assign | *= | a *= b | a = a*b |
| Divide and assign | /= | a /= b | a = a/b |
| Divide and assign the integer part | //= | a //= b | a = a//b |
| Modulo and assign | %= | a %= b | a = a%b |
| Power and assign | **= | a **= b | a = a**b |

| A | B | A or B | A and B | Not A |
|---|---|---|---|---|
| False | False | False | False | True |
| False | True | True | False | True |
| True | False | True | False | False |
| True | True | True | True | False |

Equals:

| A | B | A or B | A and B | Not A |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 1 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 | 0 |

For example,

```
>>> A = True
>>> type(A)
<class 'bool'>
>>> B = False
>>> A or B
True
```

The following table summarizes some logical laws useful for dealing with Boolean expressions. They can be demonstrated using the truth table on each side of equality.

```
not not A = A
A and True = A
A and False = False
A or False = A
A or True = True
not (not A and not B) = A or B
not (not A or not B) = A and B
```

Python and other languages such as C++ include logical operators on binary numbers, performed bit-by-bit. These bitwise operators perform the logical operations on the bits of the binary number equivalent to the decimal number entered. For example, 5 = 101 and 6 = 110. If you make a “and logical” bit by bit you will have binary 100, which is equivalent to 4 = 100. At the machine language level, the operator or exclusive (xor) is also used, which returns 1 when only one of the operands is 1. In Python, as in C++, the bit operators are.

| Bit operation | Operator | Expression | Result |
|---|---|---|---|
| "and logical", and | & | 5 & 6 | 101 and 110 -> 100, 4 decimals |
| "or logical", or | \| | 5 \| 6 | 101 or 110 -> 111, 7 decimals |
| exclusive or | ^ | 5 ^ 6 | 101 xor 110 -> 011, 3 decimals |
| Complement, not | ~ | ~x | switch 0's by 1's and 1's by 0's. Equals to -x -1 |
| Left shift | << | x << n | Returns x with bits shifted n places to the left. Equivalent to x * 2 **n |
| Right shift | >> | x >> n | Returns x with bits shifted n places to the right. Equivalent to x // 2 ** n |

## Relational Operators (comparison)

They are used to compare 2 expressions or values and the result is always true or false, that is, Boolean.

| Math | In Python | Meaning | Example | Result |
| :--- | :--- | :--- | :--- | :--- |
| = | == | Equal to | 'a' == 'b' | False |
| ≠ | != | Different to | 'b' != 'B' | True |
| < | < | Smaller than | 7 < 3 | False |
| > | > | Greater than | 7 > 3 | True |
| ≤ | <= | Smaller than or equal to | 7 <= 7 | True |
| ≥ | >= | Greater than or equal | 7 >= 3 | True |

In the following example we will use the relational operators to check that the measured temperature, which we will assign to the variable temp, is between 37 and 42 °C, inclusive.

```
>>> temp = 38 # measured temperature
>>> (temp >= 37) and (temp <= 42)
True
```

The expression (temp >= 37) and (temp <= 42) can go without parentheses since the relational operators have a higher priority or precedence than the Booleans. Python has the characteristic that this type of expression can be written as in mathematical notation: 37 <= temp <= 42. Expressions of the type a < b < c in Python mean (a < b) and (b < c), which improves the readability of language.

The characters of the alphabet (without the ñ) that belong to the ASCII table are ordered. The lower-case letters of the decimal equivalent binary 97 to 122 and the upper-case letters from 65 to 90. Although in Python the characters are of type string, we can compare characters and their True or False result will be given according to their ASCII position. For example, 'b' > 'a' will return True. Similarly, 'B' > 'a' will return False.

In the following exercise we will look for an expression that is true when, given a variable car, this is a symbol of the alphabet:

```
>>> car = 'q'
>>> (car >= 'a') and (car <= 'z') or (car >= 'A') and (car <= 'Z')
True
>>> # Equals to
>>> 'a' <= car <= 'z' or 'A' <= car <= 'Z'
True
>>> car = '&'
>>> 'a' <= car <= 'z' or 'A' <= car <= 'Z'
False
```

The result can be assigned to a Boolean variable:

```
>>> is_letter = 'a' <= car <= 'z' or 'A' <= car <= 'Z'
>>> is_letter
False
```

In most languages, including Python, the Boolean value True (1 logical) is greater than False (0 logical):

```
>>> True > False
True
```

## Use of functions. Internal and module functions.

In various examples of programs, people use internal functions and functions of the mathematics module (math) and of which it generates random values. Among the functions already applied are:

| Internal Function | Returns |
|---|---|
| type | datatype |
| id | Identity or memory location |
| bin | binary string equivalent to the given integer |
| int, float, str | integer, real, string of the given value |
| input | reads a value from the keyboard |
| print | prints text to the screen |
| abs | absolute value of a number |
| round | rounds a real to the specified decimals |
| Math module | |
| pi | pi value (not function) |
| sqrt | square root of a number |
| Random module | |
| randint | random integer in the given range |

In mathematics a function returns a result depending on each value of its independent variable (s). For example: f (x) = 3x2 + 1 calculates, for x = 2, the value f (2) = 13;

f2 (x, y) = x2 + y2 calculates f (2.2) = 8; f (x) = √ calculates f (9) = 3. The functions that return results in the programming languages behave similarly.

In the context of computer languages, a function is an instruction or a block of instructions that perform a calculation or a task, and that has an identifier as a name (identifier like variables). Of the previously used functions their names (identifiers) are type, int, abs, sqrt, round, etc. In the first example of data type we already use the call to a function (it is also said to invoke the function):

```
>>> type (7)
<class 'int'>
```

The name of the function is type and, in this case, the value 7 is its argument. The arguments are the values that we pass to the functions. Example:

```
from math import sqrt
x = abs (-9) + 3
y = sqrt(x)
print ('Square of ',x, '=',y)
```

