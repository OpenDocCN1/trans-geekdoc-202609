# 1.12 Proposition. The volume of the ball of radius i is

$$V_q(i,n)=\sum_{j=0}^{i}\binom{n}{j}(q-1)^j.$$

We are close to our bound. Let $\mathcal{C}$ be a code $(n,M,d)_q$. Let $e=\lfloor(d-1)/2\rfloor$ (the largest integer less than or equal to $(d-1)/2$). We have chosen $e$ such that $2e+1<d$. Our standard argument shows that the balls of radius $e$ centered at the codewords must be disjoint. As each such ball has $V_q(e,n)$ vectors, we must have $M V_q(e,n)\le q^n$ (counting all vectors in these balls, we cannot get more vectors than the whole space contains).

# 1.13 Theorem (sphere packing bound). Each $q$-ary code $\mathcal{C}$ of length $n$ and minimum distance $d$ satisfies

$$|\mathcal{C}|\le\frac{q^n}{V_q(e,n)}.$$

Here $e=\lfloor(d-1)/2\rfloor$.

Codes for which equality holds in Theorem 1.13 are known as **perfect codes**. The parameters of perfect codes have all been classified. Our first code was a $(6,8,3)_2$. What is the maximum $M$ for a code $(6,M,3)_2$? Here $e=1$. We have $V_2(1,6)=7$. The sphere-packing bound says $7M\le64$, hence $M\le9$. We claim that a code $(6,9,3)_2$ cannot exist. The reader is asked to provide a proof along the lines sketched in Exercises 1.6.4 and 1.6.5. Here is a nice parameter situation: consider a possible code $(11,729,5)_3$. Observe that $729=3^6$. We have $e=2$ and $V_3(2,11)=1+11\cdot2+\binom{11}{2}\cdot4=1+22+220=243=3^5$ (quite a coincidence). It follows that a ternary code $(11,M,5)_3$ has $M\le3^{11}/3^5=3^6=729$. We see that the parameters $(11,3^6,5)_3$ are extremal. If such a code exists, then it is perfect. A perfect code $(11,729,5)_3$ does indeed exist. It is uniquely determined by its parameters and known as the **ternary Golay code**, named after the Swiss engineer who described it in 1949 (see Golay [94], reprinted in Berlekamp [13]).

# A betting system

Here is how the ternary Golay code can be used in a betting system: in most European countries it is popular to bet on the results of football matches (**football** is not to be confused with American football. In the US the game is known by the bizarre name of **soccer**). Each match has one of three possible results: 1= home team wins, 2=guest wins, or 0= a draw. This is why we use ternary codes. There are 11 or more matches in the pool. If there are