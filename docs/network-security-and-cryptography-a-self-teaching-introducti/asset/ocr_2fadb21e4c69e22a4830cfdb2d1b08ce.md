# Example 4.28

Let $G=\{0,1,2,3,4,5\}$ be a cyclic group of order 6. Determine the Generators of $G$.

# Solution

$|G|=6$. The group is called cyclic, since all its elements can be generated as a power $a^k \mod 6$, where $a^k \mod 6=(a+a+\dots+a)\mod 6=(k\times a)\mod 6$ $k$-times

Where $a^0=0$ and $a^{-k}=(-a)^k$

Let us now check for generators of $G$.
As obvious, 0 is not a generator of $G$.
Let us check 1, 2, 3, 4, and 5.

+   $1^0 \mod 6=0\n$1^1 \mod 6=1\mod 6=1\n$1^2 \mod 6=(1+1)\mod 6=2\n$1^3 \mod 6=(1+1+1)\mod 6=3\n$1^4 \mod 6=(1+1+1+1)\mod 6=4\n$1^5 \mod 6=(1+1+1+1+1)\mod 6=5\n$1^6 \mod 6=(1+1+1+1+1+1)\mod 6=0$

The cycle repeats after $1^5 \mod 6$, and all elements of $G$ appear in the cycle.

+   $\.\$ 1 is a generator of $G$.
Let us now check for 2.

+   $2^0 \mod 6=0\n$2^1 \mod 6=2\mod 6=2\n$2^2 \mod 6=(2+2)\mod 6=4\n$2^3 \mod 6=(2+2+2)\mod 6=0\n$2^4 \mod 6=(2+2+2+2)\mod 6=2\n$2^5 \mod 6=(2+2+2+2+2)\mod 6=4$