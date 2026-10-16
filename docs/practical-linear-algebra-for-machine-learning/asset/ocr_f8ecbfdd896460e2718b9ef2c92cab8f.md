**PROOF:** Look at the below equations to see how **w** is also a solution:

$Aw = A\{\beta v + (1-\beta)u\} = \beta Av + Au - \beta Au = \beta b + b - \beta b = b$ ▲

So the above proves shows that if we have more than one solution, then we can say we have infinite number of solutions! The **following two conditions** determine the number of solutions if there is at least one solution. Try to prove them based on what you learned so far:

+   - $A^{m\times n}x^{n\times 1}=b^{m\times 1}$ has at least one solution if $m\le n$ and $\operatorname{Rank}(A)=m$.
+   - $A^{m\times n}x^{n\times 1}=b^{m\times 1}$ has exactly one solution if $m=n$ and $\operatorname{Rank}(A)=m$.

# 6.6.  **Conclusion**

In this chapter, you learned the concept of linear independence of the vectors and their associates with the system of linear equations. This concept is crucial, especially in Machine Learning and optimization theory, in which we are dealing with all sorts of mathematical proofs necessary to justify why a method should work!