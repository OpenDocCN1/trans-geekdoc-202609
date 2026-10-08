Data Stream Mining for Big Data

# 1.3.3 COUNT UNIQUE ITEMS IN A DATA STREAM

Counting the number of unique items in the stream presents an interesting problem. Formally, this problem can be posed as follows. Suppose the domain of the random variable is $\{0, 1, \dots, n\}$ and the stream looks like:

0, 1, 0, 0, 0, 1, 2, 3, 3...

$n = 3$. A trivial solution is to store all new items in a hash map whose size grows like $O(n)$. However, we want a solution which runs only in $O(\log(n))$. One elegant solution is given by Flajolet and Martin (FM) (1985). FM is given in Algorithm 1.1. Let us work through the algorithm step-by-step.

+   - Initialize a BITMAP to all 0.
- For each item $x$ in the stream, compute a hash value for it. Call it $h(x)$.
- The binary representation of the hash value is $bin(h(x))$.
- The function $p$ gives the position of the least significant set-bit. This also occurs if $p$ returns 0 for the 0 bit.
- Finally set the BITMAP[i] = 1.

```
Algorithm L1: Flajolet and Martin (FM) Algorithm
Input: stream $M$
Output: Cardinality of $M$
1 initialization: BITMAP OF $L$ bits initialized to 0;
2 for each $x$ in $M$ do
  * Calculate hash function $h(x)$;
  * get binary representation of hash output, call it $bin(h(x))$;
  * Calculate the index $i$ such that $i = p(bin(h(x)))$, where $ho(i)$ is such that it outputs the position of the least-significant set-bit, i.e., position of $i$;
  * set BITMAP[$i$] = 1;
3 end
4 Let $R$ denote the largest index such that BITMAP[$i$] = 1;
5 Cardinality of $M$ is $2^R/\phi$ where $\phi=0.77351;
```

The above steps are repeated until the end of the stream. Let $R$ denote the most significant set-bit. Then, the number of unique items is given by $2^R/\phi$ where $\phi \approx 0.77351$ is a correction factor.

The intuition behind the working of the FM algorithm is as follows. The FM-algorithm uses a hash function that maps the strings in the stream to thoroughly generate random integers in the range $[0, \dots, 2^l-1]$. Thus, we expect that:

+   - 1/2 of the numbers will have their binary representation in 0 (divisible by 2).
- 1/4 of the numbers will have their binary representation in 00 (divisible by 4).
- 1/8 of the numbers will have their binary representation in 000 (divisible by 8).
- In general, $1/2^k$ of the numbers will have their binary representation in $0^k$.