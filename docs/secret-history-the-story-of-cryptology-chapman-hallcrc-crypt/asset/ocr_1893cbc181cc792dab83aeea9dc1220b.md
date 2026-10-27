# 15.1.7.1 The Chinese Remainder Theorem

Given *k* congruences

\[
\begin{aligned}
x &= a_1 \pmod{n_1}\\
x &= a_2 \pmod{n_2}\\
x &= a_3 \pmod{n_3}\\
&\vdots\\
x &= a_k \pmod{n_k}
\end{aligned}
\]

such that the \(n_i\) are positive integers and pairwise relatively prime, and the \(a_i\) are integers, there exists values for \(x\) satisfying all of the equations. If one solution is given by \(x'\), then the set of all solutions is given by \(x=x'+yn\), where \(y\) takes every integer value and \(n=n_1n_2n_3\ldots n_k\).

Gauss expressed the solution as

\[
x=\sum_{i=1}^{k}a_iN_iM_i\pmod{n}
\]

where \(N_i=n/n_i\) and \(M_i=N_i^{-1}\pmod{n_i}\). The easiest way to see how a solution may be obtained is through an example.

# Example 1

Suppose we have

\[
\begin{aligned}
x &= 5\pmod{9}\\
x &= 8\pmod{11}\\
x &= 6\pmod{14}.
\end{aligned}
\]

For convenience, we label the moduli as \(n_1=9\), \(n_2=11\), and \(n_3=14\). We compute the product of the moduli \(n=n_1n_2n_3=(9)(11)(14)=1,386\). Using Gauss’s formula, we have

\[
x=\sum_{i=1}^{k}a_iN_iM_i\pmod{n}=a_1N_1M_1+a_2N_2M_2+a_3N_3M_3\pmod{n}
\]

The values for the \(a_i\) were given in the problem, and the \(N_i\) are very easy to calculate. To get the \(M_i\), we could use a technique from [Section 14.3](#) (the Euclidean algorithm), but for such small values, it is easier to do the calculations in one’s head. For large numbers we’d resort to the algorithm. We have

\[
\begin{aligned}
M_1&=N_1^{-1}=(154)^{-1}=(1)^{-1}=1\pmod{9}\\
M_2&=N_2^{-1}=(126)^{-1}=(5)^{-1}=9\pmod{11}\\
M_3&=N_3^{-1}=(99)^{-1}=(1)^{-1}=1\pmod{14}
\end{aligned}
\]

So, plugging in these values along with the \(n_i\) and \(N_i\), we have

\[
\begin{aligned}
x&=(5)(154)(1)+(8)(126)(9)+(6)(99)(1)\pmod{1,386}\\
&=10,436\pmod{1,386}\\
&=734\pmod{1,386}
\end{aligned}
\]

Checking against our original three equations, we see that the answer, \(x=734\), works.