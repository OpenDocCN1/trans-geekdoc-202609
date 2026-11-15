![](bbox=[0.325, 0.105, 0.785, 0.235])

The only difference between these two libraries is that a subroutine call has been inlined.
This difference has no effect on the calling program.

![](bbox=[0.405, 0.3, 0.705, 0.42])

The only difference between these two libraries is that the two highlighted lines have been
removed. But it should be clear that these lines have no effect: k1 is used only to compute
c1, which is never used again. Hence, this difference has no effect on the calling program.

The final hybrid is exactly L_ots$-rand (although with a variable name changed). We
have shown that L_ots$-rand == L_ots$-real', meaning that this encryption scheme has one-time
uniform ciphertexts.

# Summary of the Hybrid Technique

We have now seen our first example of the hybrid technique for security proofs. All secu-
rity proofs in this book use this technique.

+   Proving security means showing that two particular libraries, say L_left and L_right,
+   are interchangeable.

+   Often L_left and L_right are significantly different, making them hard to compare di-
+   rectly. To make the comparison more manageable, we can show a sequence of hybrid
+   libraries, beginning with L_left and ending with L_right. The idea is to break up the
+   large “gap” between L_left and L_right into smaller ones that are easier to justify.

+   It is helpful to think of “starting” at L_left, and then making a sequence of small
+   modifications to it, with the goal of eventually reaching L_right. You must justify
+   why each modification doesn’t affect the calling program (i.e., why the two libraries
+   before/after your modification are interchangeable).

+   As discussed in Section 2.2, simple things like inlining/factoring out subroutines,
+   changing unused variables, changing unreachable statements, or unrolling loops
+   are always “allowable” modifications in a hybrid proof since they have no effect on