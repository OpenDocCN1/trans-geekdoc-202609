# Linear Feedback Shift Registers

*Linear feedback shift registers (LFSRs)* are FSRs with a linear feedback function—namely, a function that’s the XOR of some bits of the state, such as the example of a 4-bit FSR in the previous section and its feedback function returning the XOR of the register’s 4 bits. Recall that in cryptography, linearity is synonymous with predictability and suggestive of a simple underlying mathematical structure. And, as you might expect, thanks to this linearity, we can analyze LFSRs using notions like linear complexity, finite fields, and primitive polynomials—but I’ll skip the math details and just give you the essential facts.

> **NOTE**  
> *In linear algebra, we define a linear transform* f *as a function that satisfies* f(u + v) = f(u) + f(v). *If you know* f(u) *and* f(v), *you can then determine* f(u + v) *without knowing* u *or* v. *With a nonlinear function, it’s much more complicated; you can’t easily find* f(u + v) *from* f(u) *and* f(v).

The choice of which bits to XOR together is crucial for the period of the LFSR and thus for its cryptographic value. The good news is that we know how to select the position of the bits to guarantee a maximal period of $2^n - 1$. Specifically, we take the indices of the bits, from 1 for the rightmost to $n$ for the leftmost, and write the polynomial expression $1 + X + X^2 + \ldots + X^n$, where we include the term $X^i$ only if the ith bit is one of the bits XORed in the feedback function. The period is maximal *if and only if* that polynomial is *primitive*. To be primitive, the polynomial must have the following qualities:

+   - The polynomial must be irreducible, meaning that it can’t be factorized—that is, written as a product of smaller polynomials. For example, $X + X^3$ is not irreducible because it’s equal to $(1 + X)(X + X^2)$:
+   
+     $(1 + X)(X + X^2) = X + X^2 + X^2 + X^3 = X + X^3$
+   
+   - The polynomial must satisfy certain other mathematical properties that cannot be easily explained without nontrivial mathematical notions but are easy to test.

> **NOTE**  
> *The maximal period of an n-bit LFSR is* $2^n - 1$, *not* $2^n$, *because the all-zero state always loops on itself infinitely. Because the XOR of any number of zeros is zero, new bits entering the state from the feedback function will always be zero; hence, the all-zero state is doomed to stay all zeros.*

For example, Figure 5-5 shows a 4-bit LFSR with the feedback polynomial $1 + X + X^3 + X^4$ in which we XOR the bits at positions 1, 3, and 4 together to compute the new bit set to $L_1$. However, this polynomial isn’t primitive because we can factorize it into $(1 + X^3)(1 + X)$.