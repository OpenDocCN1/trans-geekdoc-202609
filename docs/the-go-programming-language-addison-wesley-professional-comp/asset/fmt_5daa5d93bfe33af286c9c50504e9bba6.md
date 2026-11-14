
Go’s types fall into four categories: `basic types`, `aggregate types`, `reference types`, and `interface types`. Basic types, the topic of this chapter, include numbers, strings, and booleans. Aggregate types—arrays ([§4.1](#part0036.html#id-arrays)) and structs ([§4.4](#part0039.html#id-structs))—form more complicated data types by combining values of several simpler ones. Reference types are a diverse group that includes pointers ([§2.3.2](#part0023.html#id-pointers)), slices ([§4.2](#part0037.html#id-slices)), maps ([§4.3](#part0038.html#id-maps)), functions ([Chapter 5](#part0042.html#id-functions)), and channels ([Chapter 8](#part0076.html#id-concurrency)), but what they have in common is that they all refer to program variables or state *indirectly*, so that the effect of an operation applied to one reference is observed by all copies of that reference. Finally, we’ll talk about interface types in [Chapter 7](#part0060.html#id-interfaces).

## 3.1 Integers

Go’s numeric data types include several sizes of integers, floating-point numbers, and complex numbers. Each numeric type determines the size and signedness of its values. Let’s begin with integers.

Go provides both signed and unsigned integer arithmetic. There are four distinct sizes of signed integers—8, 16, 32, and 64 bits—represented by the types `int8`, `int16`, `int32`, and `int64`, and corresponding unsigned versions `uint8`, `uint16`, `uint32`, and `uint64`.

There are also two types called just `int` and `uint` that are the natural or most efficient size for signed and unsigned integers on a particular platform; `int` is by far the most widely used numeric type. Both these types have the same size, either 32 or 64 bits, but one must not make assumptions about which; different compilers may make different choices even on identical hardware.

The type `rune` is a synonym for `int32` and conventionally indicates that a value is a Unicode code point. The two names may be used interchangeably. Similarly, the type `byte` is a synonym for `uint8`, and emphasizes that the value is a piece of raw data rather than a small numeric quantity.

Finally, there is an unsigned integer type `uintptr`, whose width is not specified but is sufficient to hold all the bits of a pointer value. The `uintptr` type is used only for low-level programming, such as at the boundary of a Go program with a C library or an operating system. We’ll see examples of this when we deal with the `unsafe` package in [Chapter 13](#part0121.html#id-lowlevelprogramming).

Regardless of their size, `int`, `uint`, and `uintptr` are different types from their explicitly sized siblings. Thus `int` is not the same type as `int32`, even if the natural size of integers is 32 bits, and an explicit conversion is required to use an `int` value where an `int32` is needed, and vice versa.

Signed numbers are represented in 2’s-complement form, in which the high-order bit is reserved for the sign of the number and the range of values of an *n*\-bit number is from −2^(*n*−1) to 2^(*n*−1)−1. Unsigned integers use the full range of bits for non-negative values and thus have the range 0 to 2^(*n*)−1. For instance, the range of `int8` is −128 to 127, whereas the range of `uint8` is 0 to 255.

Go’s binary operators for arithmetic, logic, and comparison are listed here in order of decreasing precedence:

```
*    /    %    <<    >>    &    &^
+    -    |    ^
==   !=   <    <=    >     >=
&&
||
```

There are only five levels of precedence for binary operators. Operators at the same level associate to the left, so parentheses may be required for clarity, or to make the operators evaluate in the intended order in an expression like `mask & (1 << 28)`.

Each operator in the first two lines of the table above, for instance `+`, has a corresponding *assignment operator* like `+=` that may be used to abbreviate an assignment statement.

The integer arithmetic operators `+`, `-`, `*`, and `/` may be applied to integer, floating-point, and complex numbers, but the remainder operator `%` applies only to integers. The behavior of `%` for negative numbers varies across programming languages. In Go, the sign of the remainder is always the same as the sign of the dividend, so `-5%3` and `-5%-3` are both `-2`. The behavior of `/` depends on whether its operands are integers, so `5.0/4.0` is `1.25`, but `5/4` is `1` because integer division truncates the result toward zero.

If the result of an arithmetic operation, whether signed or unsigned, has more bits than can be represented in the result type, it is said to *overflow*. The high-order bits that do not fit are silently discarded. If the original number is a signed type, the result could be negative if the leftmost bit is a 1, as in the `int8` example here:

```
var u uint8 = 255
fmt.Println(u, u+1, u*u) // "255 0 1"

var i int8 = 127
fmt.Println(i, i+1, i*i) // "127 -128 1"
```

Two integers of the same type may be compared using the binary comparison operators below; the type of a comparison expression is a boolean.

| Operator | Description |
| --- | --- |
| `==` | equal to |
| `!=` | not equal to |
| `<` | less than |
| `<=` | less than or equal to |
| `>` | greater than |
| `>=` | greater than or equal to |

In fact, all values of basic type—booleans, numbers, and strings—are *comparable*, meaning that two values of the same type may be compared using the `==` and `!=` operators. Furthermore, integers, floating-point numbers, and strings are *ordered* by the comparison operators. The values of many other types are not comparable, and no other types are ordered. As we encounter each type, we’ll present the rules governing the *comparability* of its values.

There are also unary addition and subtraction operators:

| Operator | Description |
| --- | --- |
| `+` | unary positive (no effect) |
| `-` | unary negation |

For integers, `+x` is a shorthand for `0+x` and `-x` is a shorthand for `0-x`; for floating-point and complex numbers, `+x` is just `x` and `-x` is the negation of `x`.

Go also provides the following bitwise binary operators, the first four of which treat their operands as bit patterns with no concept of arithmetic carry or sign:

| Operator | Description |
| --- | --- |
| `&` | bitwise AND |
| `|` | bitwise OR |
| `^` | bitwise XOR |
| `&^` | bit clear (AND NOT) |
| `<<` | left shift |
| `>>` | right shift |

The operator `^` is bitwise exclusive OR (XOR) when used as a binary operator, but when used as a unary prefix operator it is bitwise negation or complement; that is, it returns a value with each bit in its operand inverted. The `&^` operator is bit clear (AND NOT): in the expression `z = x &^ y`, each bit of `z` is 0 if the corresponding bit of `y` is 1; otherwise it equals the corresponding bit of `x`.

The code below shows how bitwise operations can be used to interpret a `uint8` value as a compact and efficient set of 8 independent bits. It uses `Printf`’s `%b` verb to print a number’s binary digits; `08` modifies `%b` (an adverb!) to pad the result with zeros to exactly 8 digits.

```
var x uint8 = 1<<1 | 1<<5
var y uint8 = 1<<1 | 1<<2

fmt.Printf("%08b\n", x)    // "00100010", the set {1, 5}
fmt.Printf("%08b\n", y)    // "00000110", the set {1, 2}

fmt.Printf("%08b\n", x&y)  // "00000010", the intersection {1}
fmt.Printf("%08b\n", x|y)  // "00100110", the union {1, 2, 5}
fmt.Printf("%08b\n", x^y)  // "00100100", the symmetric difference {2, 5}
fmt.Printf("%08b\n", x&^y) // "00100000", the difference {5}

for i := uint(0); i < 8; i++ {
    if x&(1<<i) != 0 { // membership test
        fmt.Println(i) // "1", "5"
    }
}

fmt.Printf("%08b\n", x<<1) // "01000100", the set {2, 6}
fmt.Printf("%08b\n", x>>1) // "00010001", the set {0, 4}
```
