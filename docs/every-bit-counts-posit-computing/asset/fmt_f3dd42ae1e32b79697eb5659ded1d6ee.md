
# IEEE 754 标准的历史与缺陷

After many years of intense argument (mostly over Kahan's insistence on subnormal number support, also called "gradual underflow"), IEEE Std 754 was approved and published in 1985. It is not free; anyone wanting to use it has to pay $100 to IEEE for a copy of the Standard. Palmer once told me, chortling, that "Whatever was in the 8087, that's what's in the IEEE Standard." Intel had won its battle. While IBM and Cray resisted following the Standard for the next decade, most vendors adopted (most of) the Standard, believing it would lead to data portability (which it did), and identical results on different computer systems (which it did not).

When a format starts with a few dubious choices, such as underflow to zero, that leads to the need for other dubious choices such as "gradual underflow" that complicate the circuitry and create numerical hazards. The format ignored the 1950s lesson of *not* using sign-magnitude arithmetic, so once again there was "positive zero" and "negative zero." Are they equal? Yes, they decided. The two kinds of zero should test as equal. But their reciprocals should be *positive infinity* and *negative infinity*, so now you have a format where `x` can equal `y` but a function `f(x)` can be as far different from `f(y)` as you can get. When an engineer creates a hasty solution with flaws and then adds more hasty solutions to patch those flaws, it is called a *kludge*.

Palmer decided to have a special bit pattern for indeterminate results like `0/0`, `log(-2)`, and he called it "NaN" for "Not a Number," even though imaginary numbers and complex numbers are, well, numbers. The bit test only applied to the exponent bits, however, leaving a vast set of bit patterns representing the same NaN. Two of the patterns were carved out to mean –∞ and ∞. Here are how many bit patterns were wasted saying a result is a NaN (IEEE half was added to the Standard in 2008):

| **Precision** | **Number of NaN Patterns** |
| --- | --- |
| IEEE half (16 bits) | 4094 (over 6 percent of the bit patterns) |
| IEEE single (32 bits) | 16,777,214 |
| IEEE double (64 bits) | 9,007,199,254,740,990 (slightly over 9 trillion) |

How would NaN work in comparison operations if it was not a specific bit string? The first axiom of Aristotelian logic is that A is A; a thing is equal to itself. But incredibly, the decision was made that NaN is *not* equal to itself. The web got ever more tangled. The mathematically absurd concepts of "positive zero" and "negative zero" created a mess of contradictory statements about how they should be handled. The 754 Standard is almost 100 pages long.

To support the Standard in hardware, the logic circuitry has to handle this set of exception cases:

![The IEEE Std 754 format, 32-bit example, and the exception cases in a nutshell](images/pg90_1.jpg)

While I suspect Kahan was initially appalled at being tasked with defending signed zero, he eventually did the mental gymnastics required and pronounced it a Good Thing because it could help with a concept called "branch cuts" in complex arithmetic. To make this work, the Standard requires yet another counterintuitive exception that the square root of "negative zero" should be "negative zero." I am not making this up.

There were originally four rounding modes; more have been added in revisions of the Standard, but once you have multiple rounding modes, you remove any hope of guaranteeing the same results across different computing systems, even if all you do is plus-minus-times-divide. Scientific computing favors banker's rounding (round to nearest, with ties to even), but graphics accelerators favor truncation (round toward zero) since it is faster and usually has an imperceptible effect on image quality.

Another guarantee of Never Twice the Same Answer was that the *transcendental* math library functions (logarithms, exponentials, trigonometric and inverse trigonometric functions) do not have to be correctly rounded, according to the Standard. Correct rounding would mean different computing systems would get the same result down to the last bit, if they used the same rounding mode.

Kahan reversed his initial demand for reproducibility and wrote position papers about how difficult and utterly impractical it would be to have such a requirement. Like a lawyer, he proved able to take either side of any design decision. He advocated for Intel by citing mathematics when Intel's choice improved accuracy or correctness, and by citing practicality when the choice worsened either one.

## 4.7.5 A Bold Claim of Round-Trip Perfection

In his 1983 commentary "Mathematics Written in Sand," Kahan boasts that you can square an IEEE float, and if it does not overflow or underflow, you can then take the square root and get back the absolute value of the original number exactly. *Always*. What a marvelous property! Here is the relevant text from that commentary:

<https://people.eecs.berkeley.edu/~wkahan/MathSand.pdf>

An overflow would produce infinity and remain infinity when we take the square root, letting us know that something went wrong. Similarly, an underflow would presumably produce zero, and remain zero when we then take the square root, also informing the user that the value is wrong.

Shall we give it a try?

Let's set `x = 2.646978 × 10^(−23)` as a single-precision IEEE float. Now square it and round it with the default rounding mode (banker's rounding), and you get

`y = x² ≈ 1.401298 × 10^(−45)`.

So it did not underflow to zero. The Standard states that square roots must be correctly rounded, so now try taking the square root and see if we get back `2.646978 × 10^(−23)`, the `x` we started with, down to the last decimal:

```
z = √y = 3.743392 × 10^(-23)
```

Not a single decimal in the answer is right. How could a mathematician like Kahan be *that* wrong? The explanation reveals something about IEEE floats that very few computer technologists seem to know: IEEE floats have *tapered accuracy*. Not the same kind of tapered accuracy as posits, but it is there.

Remember the decimal accuracy plots from [Chapter 2](#chapter2.xhtml)? Here is what the decimal accuracy plot looks like for IEEE single precision:

![Accuracy plot for IEEE standard 32-bit precision floats, with tapered accuracy on the left](images/pg92_1.jpg)

For most of the range (from about `10^(−38)` to `10^38`), decimal accuracy wobbles between about 7.2 to 7.5 decimals. But what is that ramp over on the left, from about `10^(−45)` to `10^(−38)`? The accuracy ramps down to almost nothing, with no decimal digits correct. Those are the *subnormal* floats, and every IEEE precision has them. So the `x` that I chose has its square at the low end of that ramp, which is why not a single decimal digit was correct in computing `√(x²)`.

Realizing this could happen, Kahan came up with a "read the fine print" workaround: He created his own definition of what "underflow" means. To every other computer programmer and user I have known, "underflow" means "what happens when a result is too small to represent" and you know it happens by looking at the output, zero. But the IEEE Standard says that the underflow flag must also be set if the result of an operation lands in the subnormal region *and is not exact*. But it is *not* too small to represent; it simply had to be rounded. So now that is "underflow"? How is anyone supposed to know that a processor flag was set? By using a low-level debugging tool and stepping through the compiled code one machine instruction at a time, watching the processor flags?
