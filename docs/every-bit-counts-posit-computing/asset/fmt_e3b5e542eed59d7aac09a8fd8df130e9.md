
## Posit Rounding Algorithm

This is a formal algorithm for posit rounding, and it expresses the process slightly differently from the description in [Chapter 3](#chapter3.xhtml). If `x` is exactly expressible as a posit, there is nothing to do. If `x` is outside the dynamic range, saturate to signed `minPos` or `maxPos`. Otherwise, `x` lies between two adjacent `n`-bit posit values `u` and `w`. A diagram may be helpful in visualizing the above algorithm. Recall the projective reals and the ring plots of [Chapters 1](#chapter1.xhtml) and [3](#chapter3.xhtml), and zoom in on just one part of the ring:

![The real value in question, x, lies between posit values represented by U and one ULP higher](images/pg124_1.jpg)

The real value in question, `x`, lies between posit values represented by `U` and one ULP higher.

The real values are on the outside of the ring. Values `u` and `w` are successive posit values (no other posits lie between them). We need to round to either `u` or `w`.

When you append a `0` bit to a posit, it does not change what it represents, but appending a `1` bit represents a new in-between value; the algorithm appends a `1` bit to `U` and writes it as `U1`. The real value represented by `U1` is `v`, as shown below:

![If there were n + 1 bits instead of n, the introduced new point tells us which way to round x.](images/pg125_1.jpg)

If there were `n` + 1 bits instead of `n`, the introduced new point tells us which way to round `x`.

In the figure, that determines that `x` should round to `u` since `x` is between `u` and `v`. If `x` had been between `v` and `w`, it should round to `w`. If `x = v`, the tie case goes to whichever of `u` or `w` is represented by a bit string ending in a `0` bit (“round to even”).

Many essential operations in scientific computing can make use of the quire to stay in the Math Layer as long as possible. If we use `i` to represent the imaginary number `$\sqrt{-1}$`, then multiplying two complex numbers `a + b i` and `c + d i` requires evaluating two expressions for the real and imaginary parts:

Both `a·c − b·d` and `a·d + b·c` are dot products. Doing them in the quire and then converting back to posit format reduces the number of roundings from three to one.

Using the quire also solves a classic problem when using complex arithmetic based on pairs of floats: Programmers discover that if they declare a variable to be complex and let the computer take care of operations like the above multiplication, it runs significantly and inexplicably slower than writing out the product as shown above, with real variables instead of complex variables. Why? It is because routines for complex numbers are trying to avoid catastrophic underflow or overflow when computing `a·c, b·d`, and so on. The programmer may know that there is no danger of overflow, but the math library routines do not know that and assume the worst, so they go through considerable machinations to avoid overflow and underflow and produce a correctly-rounded answer.

When computing a fused operation in parallel, it might be tempting to round the intermediate results before sending them to another processor. That is not permitted, because it leads to irreproducibility. For example, a single processor might compute a sum of posits `a + b + c + d` using a quire variable `q`, then round `q` to a posit `s`. That is, `$s = \overline{a+b+c+d}.` If one processor computes `a + b` and another computes `c + d` in respective quire variables `q[0]` and `q[1]`, they need to exchange `q[0]` and `q[1]`, and not first round them to a local sum. That keeps fused parallel operations in the Math Layer until they are complete. Posits can restore the associative property of addition, up to some extremely large number of additions (the quire sum limit).

That said, the quire can be overkill. Doing a fused multiply-add, for example, requires fewer than `16*n` bits, so a system designer may choose to do fused multiply-add operations by some other means that is more economical. This is explicitly permitted in the Posit Standard, in the last sentence of the quoted paragraph.

The footnote points out that any operation in the list of math functions (the next section of the Posit Standard) made of composite operations must behave like a fused function. For example, computing `rSqrt(x)` means `$\overline{1/\sqrt{x}}` and not `$\overline{1/\overline{\sqrt{x}}}`.

Many language environments offer optimizations that increase speed at the expense of portability (and compliance with a standard). Sometimes portability is much less important than going as fast as possible, and the Working Group recognized that. However, for a computing environment to be posit-compliant, there has to be at least one mode of operation that follows the Posit Standard. The Posit Standard does not specify, for example, the order of operations when expressions are not parenthesized, but it does require that there be at least one mode where the ordering is `deterministic` by the source code and the grammar rules of the language, and only those modes are posit-compliant.

## 5.6 Posit Standard Functions

It was difficult to write this section without bringing in concepts from calculus; our goal was to keep everything understandable to anyone with a secondary school mathematics education. The phrase “arbitrarily close to a unique real number” evokes the concept of a `limit`. One way to express the rule in simple English is this: We are comfortable saying 2 times 3 is 6 for real numbers because approximately 2 times approximately 3 is approximately 6. But what is zero divided by zero? Approximately zero divided by approximately zero is `indeterminate`. If “approximately zero” means, say, between −0.001 and 0.001, that would include `$\frac{-0.001}{0.001} = -1`$, and `$\frac{-0.0001}{0.000001} = 100`$, and `$\frac{-0.001}{0} = \pm \infty`$. It could be any real number, as well as ±∞. That is why `$\frac{0}{0}`$ must evaluate to `NaR`. The divide operation is not `continuous` in its inputs when the denominator is zero.

The math gets a little heavy here. Instead of “approximately” we say “in an `open neighborhood` of the value in the complex plane.”

The figure below shows the neighborhoods to be circles, but they can be any connected region that is open, that is, does not include its boundary.

![A function f of input arguments x and y, with their open neighborhoods in the complex plane](images/pg128_1.jpg)

A function `f` of input arguments `x` and `y`, with their open neighborhoods in the complex plane.

If we cannot make the Result region arbitrarily small about a real-valued result by making the input neighborhoods arbitrarily small, then the result is `NaR`. Call it “the neighborhood rule.” It is not the same as saying “the function must be continuous” because it might be continuous in the complex plane yet not be real, like the arcsin function for a value greater than 1.

The power function is `pow(x, y) = x^y`. By the neighborhood rule, `pow(0, 0)` must return `NaR`. In any open neighborhood containing 0, `y` has both negative and positive values. Zero to a negative power is ±∞.

The IEEE Std 754 has a very different philosophy. It says `pow(x, ±0) = 1`, even if `x` is a (quiet) `NaN`. That is one of several ways that an indeterminate `NaN` result with floats can be made to disappear in a computation, and the user will never know anything went wrong. The IEEE Standard lists no fewer than `twenty` exception cases to the power function, things like, “`pow(±0, y) is ±0 for finite y > 0 an odd integer`.” The Posit Standard handles all those exceptions with the simple rule above, which is much more careful to propagate a `NaR` value and not regard inputs as exact numbers, since they will in general `have come from a rounded result`.

Graphs show the reason for “except for discontinuous functions of [Section 5.2](#chapter5.xhtml#sec5_2)”:
