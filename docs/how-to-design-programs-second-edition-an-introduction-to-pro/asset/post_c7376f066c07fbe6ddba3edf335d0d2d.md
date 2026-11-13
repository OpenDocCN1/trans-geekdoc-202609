
Suppose we can use four digits to represent numbers. If we represent natural numbers, one representable range is [0,10000). For real numbers, we could pick 10,000 fractions between 0 and 1 or 5,000 between 0 and 1 and another 5,000 between 1 and 2, and so on. In either case, four digits can represent at most 10,000 numbers for some chosen interval, while the number line for this interval contains an infinite number of numbers.

The common choice for hardware numbers is to use so-called scientific notation, meaning numbers are represented with two parts:

*For pure scientific notation, the base is between 0 and 9; we ignore this constraint.*

- a mantissa, which is a base number, and
- an exponent, which is used to determine a 10-based factor.

Expressed as a formula, we write numbers as

$m \cdot 10^e$

where m is the mantissa and e the exponent. For example, one representation of 1200 with this scheme is

$120 \cdot 10^1,$

another one is

$12 \cdot 10^2.$

In general, a number has several equivalents in this representation.

We can also use negative exponents, which add fractions at the cost of one extra piece of data: the sign of the exponent. For example,

$1 \cdot 10^{-2}$

stands for \(\frac{1}{100}\).

To use a form of mantissa-exponent notation for our problem, we must decide how many of the four digits we wish to use for the representation of the mantissa and how many for the exponent. Here we use two for each plus a sign for the exponent; other choices are possible. Given this decision, we can still represent 0 as

\(0 \cdot 10^0\)

The maximal number we can represent is

\(99 \cdot 10^{99}\)

which is 99 followed by 99 0’s. Using the negative exponents, we can add fractions all the way down to

\(01 \cdot 10^{-99}\)

which is the smallest representable number. In sum, using scientific notation with four digits (and a sign), we can represent a vast range of numbers and fractions, but this improvement comes with its own problems.

To understand the problems, it is best to make these choices concrete with a data representation in ISL+ and by running some experiments. Let’s represent a fixed-size number with a structure that has three fields:

```scheme
(define-struct inex [mantissa sign exponent])
; An Inex is a structure:
;   (make-inex N99 S N99)
; An S is one of:
; -- 1
; -- -1
; An N99 is an N between 0 and 99 (inclusive).
```

Because the conditions on the fields of an Inex are so stringent, we define the function create-inex to instantiate this structure type definition; see figure 143.

### Figure 143: Functions for inexact representations

The figure also defines inex->number, which turns Inexes into numbers using the above formula.

```scheme
; N Number N -> Inex
; makes an instance of Inex after checking the arguments
(define (create-inex m s e)
  (cond
    [(and (<= 0 m 99) (<= 0 e 99) (or (= s 1) (= s -1)))
     (make-inex m s e)]
    [else (error "bad values given")]))
; Inex -> Number
; converts an inex into its numeric equivalent
(define (inex->number an-inex)
  (* (inex-mantissa an-inex)
     (expt
      10 (* (inex-sign an-inex) (inex-exponent an-inex))))))
```

Let's translate the above example, 1200, into our data representation:

```
(create-inex 12 1 2)
```

Representing 1200 as 120 · 10¹ is illegal, however, according to our Inex data definition:

```
> (create-inex 120 1 1)
bad values given
```

For other numbers, though, we can find two Inex equivalents. One example is 5e-19:

```
> (create-inex 50 -1 20)
(make-inex 50 -1 20)
> (create-inex 5 -1 19)
(make-inex 5 -1 19)
```

Use inex->number to confirm the equivalence of these two numbers.

With create-inex it is also easy to delimit the range of representable numbers, which is actually quite small for many applications:

```scheme
(define MAX-POSITIVE (create-inex 99 1 99))
(define MIN-POSITIVE (create-inex 1 -1 99))
```

The question is which of the real numbers in the range between 0 and MAX-POSITIVE can be translated into an Inex. In particular, any positive number less than

10⁻⁹⁹

has no equivalent Inex. Similarly, the representation has gaps in the middle. For example, the immediate successor of

```
(create-inex 12 1 2)
```

is

```
(create-inex 13 1 2)
```

The first Inex represents 1200, the second one 1300. Numbers in the middle, say 1240, can be represented as one or the other—no other Inex makes sense. The standard choice is to round the number to the closest representable equivalent, and that is what computer scientists mean with inexact numbers. That is, the chosen data representation forces us to map mathematical numbers to approximations.

Finally, we must also consider arithmetic operations on Inex structures. Adding two Inex representations with the same exponent means adding the two mantissas:

```
(inex+ (create-inex 1 1 0) (create-inex 2 1 0))
==
(create-inex 3 1 0)
```

Translated into mathematical notation, we have

1·10⁰
+ 2·10⁰
───────
3·10⁰

When the addition of two mantissas yields too many digits, we have to use the closest neighbor in Inex. Consider adding 55 · 10⁰ to itself. Mathematically we get

110 · 10⁰,

but we can’t just translate this number naively into our chosen representation because 110 > 99. The proper corrective action is to represent the result as

11 · 10¹.

Or, translated into ISL+, we must ensure that inex+ computes as follows:

```
(inex+ (create-inex 55 1 0) (create-inex 55 1 0))
==
(create-inex 11 1 1)
```

More generally, if the mantissa of the result is too large, we must divide it by 10 and increase the exponent by one.

Sometimes the result contains more mantissa digits than we can represent. In those cases, inex+ must round to the closest equivalent in the Inex world. For example:

```
(inex+ (create-inex 56 1 0) (create-inex 56 1 0))
==
(create-inex 11 1 1)
```

Compare this with the precise calculation:

56 · 10⁰ + 56 · 10⁰ = (56 + 56) · 10⁰ = 112 · 10⁰

Because the result has too many mantissa digits, the integer division of the result mantissa by 10 produces an approximate result:

11 · 10¹.

This is an example of the many approximations in Inex arithmetic.

> And *inexact* is appropriate.

We can also multiply Inex numbers. Recall that

```
(a · 10^n) · (b · 10^m)
= (a · b) · 10^n · 10^m
= (a · b) · 10^(n+m)
```

Thus we get:

```
2 · 10^{+4} · 8 · 10^{+10} = 16 · 10^{+14}
```

or, in ISL+ notation:

```
(inex* (create-inex 2 1 4) (create-inex 8 1 10))
==
(create-inex 16 1 14)
```

As with addition, things are not straightforward. When the result has too many significant digits in the mantissa, inex* has to increase the exponent:

```
(inex* (create-inex 20 1 1) (create-inex 5 1 4))
==
(create-inex 10 1 6)
```

And just like inex+, inex* introduces an approximation if the true mantissa doesn't have an exact equivalent in Inex:

```
(inex* (create-inex 27 -1 1) (create-inex 7 1 4))
==
(create-inex 19 1 4)
```

### Exercise 412.

Design inex+. The function adds two Inex representations of numbers that have the same exponent. The function must be able to deal with inputs that increase the exponent. Furthermore, it must signal its own error if the result is out of range, not rely on create-inex for error checking.

### Challenge

Extend inex+ so that it can deal with inputs whose exponents differ by 1:

```
(check-expect
 (inex+ (create-inex 1 1 0) (create-inex 1 -1 1))
 (create-inex 11 -1 1))
```

Do not attempt to deal with larger classes of inputs than that without reading the following subsection.

### Exercise 413.

Design inex*. The function multiplies two Inex representations of numbers, including inputs that force an additional increase of the output’s exponent. Like inex+, it must signal its own error if the result is out of range, not rely on create-inex to perform error checking.

### Exercise 414.

As this section illustrates, gaps in the data representation lead to round-off errors when numbers are mapped to Inexes. The problem is, such round-off errors accumulate across computations.

Design add, a function that adds up n copies of #i1/185. For your examples, use 0 and 1; for the latter, use a tolerance of 0.0001. What is the result for (add 185)? What would you expect? What happens if you multiply the result with a large number?

Design sub. The function counts how often 1/185 can be subtracted from the argument until it is 0. Use 0 and 1/185 for your examples. What are the expected results? What are the results for (sub 1) and (sub #i1.0)? What happens in the second case? Why?

## Overflow

While scientific notation expands the range of numbers we can represent with fixed-size chunks of data, it is still finite. Some numbers are just too big to fit into a fixed-size number representation. For example,

$99 \cdot 10^{500}$

can’t be represented because the exponent 500 won’t fit into two digits, and the mantissa is as large as legally possible.
