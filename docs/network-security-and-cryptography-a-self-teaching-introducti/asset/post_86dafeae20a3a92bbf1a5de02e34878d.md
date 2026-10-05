
$p_0 = 2^q q = q$

$\cdot X_0 = a'' \pmod{n}$

$p_k = 2^k q = n-1$

$\cdot X_k = a^{n-1} \pmod{n}$

In general, $X_i = (X_{i-1})^2 \pmod{n}$ for $1 \le i \le k$, that is, each term in the series is a square of the previous term $\pmod{n}$.

- 3. If $n$ is a prime then $X_k = a^{n-1} \pmod{n} = 1$ (by Fermat's Theorem).

- 4. If $n$ is a prime and $a$ is not a primitive root of $n$, then some other term lower than $X_k$ will also be equal to 1.

Let $X_j(j<k)$ be the lowest term equal to 1.

Then there are two possibilities:

Case I: $j=0$

$X_0 = a^q \pmod{n}$

Case II: $1 \le j \le k$

$X_j = 1$,

$X_j \pmod{n} = 1$, implies that $(X_{j-1})^2 \pmod{n} = 1$

$\cdot (X_{j-1}) \pmod{n} = \pm1$

$(X_{j-1}) \pmod{n}$ cannot be assumed that $X_j$ is, since we have the lowest term equal to 1.

$\cdot (X_{j-1}) \pmod{n} = -1$ will hold.

$(X_{j-1}) \pmod{n} = -1$ implies that $(X_{j-1}) \pmod{n} = (n-1)$

Note: If $X_j \pmod{n} = 1$, then all terms $X_{j+1}$ onward will be equal to 1, since $(X_{j+1}) \pmod{n} = (X_j)^2 \pmod{n}$.

- 5. It can be concluded from the preceding arguments that an Integer $n$ is likely to be prime either $X_0 = 1$ OR any of the terms (other than $X$) will be equal to $(n-1)$; if not, $n$ will be a composite integer.

## 4.13.1.1 Miller-Rabin Algorithm

Test ($n$) where $n$ is an odd integer $\geq 3$.

Step 1: Find integers $k, q$ such that $(n-1)=2^k q, //q$ is an odd integer and $k>0$

Step 2: Select random integer $a$ such that $1<a<(n-1)$

Step 3: Compute $X_0 \leftarrow a^k \pmod n$

Step 4: If $(X_0=1)$ or $(X_j=(n-1))$ then return (“$n$ likely to be Prime”)

Step 5: For $j=1$ to $k-1$ do

```
Begin
$X_j \leftarrow (X_{j-1})^2 \pmod n$;
If $(X_j=(n-1))$ then return (“$n$ likely to be Prime”);
End;
```

Step 6: Return (“$n$ is Composite”)

## Algorithm to determine $k$ and $q$

- Step 1: $q \leftarrow n-1; k \leftarrow 0$;

- Step 2: $Temp \leftarrow q \pmod 2$;

- Step 3: If $(Temp=1)$ then return $k$ and $q$

- Step 4: $k \leftarrow k+1$;

- Step 5: $q \leftarrow q \div 2$;

- Step 6: GOTO step 2

## Example 4.39

Use the Miller-Rabin Method to determine whether a given odd number $n=13$ is likely to be prime or not.

## Solution

$n=13; (n-1)=12=2^2 \times 3$

$\cdot k=2$ and $q=3$

Choose $a=5$
$X_0=a^3 \text{mod} 13=5^3 \text{mod} 13 \neq 1$
$X_1=a^6 \text{mod} 13=(8)^2 \text{mod} 13=12=(n-1)$
$\cdot$ Test returns: "13 is likely to be prime".

## Example 4.40

Use the Miller-Rabin Method to determine whether a given odd number $n=9$ is likely to be prime or not.

## Solution

$n=9; (n-1)=8=2^3 \times 1$
$\cdot k=3$ and $q=1$
Choose $a=5$
$X_0=a^1 \text{mod} 9=5^1 \text{mod} 9 \neq 1$
$X_1=a^2 \text{mod} 9=5^2 \text{mod} 9=7 \neq (n-1)$
$X_2=a^4 \text{mod} 9=(7)^2 \text{mod} 9=4 \neq (n-1)$
$\cdot$ It returns: "9 is Composite".

## Example 4.41

Use Miller-Rabin Method to determine whether a given odd number $n=17$ is likely to be prime or not.

## Solution

$n=17; (n-1)=16=2^4 \times 1$
$\cdot k=4$ and $q=1$
Choose $a=5$
$X_0=a^1 \text{mod} 17=5^1 \text{mod} 17 \neq 1$
$X_1=a^2 \text{mod} 17=5^2 \text{mod} 17=8 \neq (n-1)$
$X_2=a^4 \text{mod} 17=(8)^2 \text{mod} 17=13 \neq (n-1)$
$X_3=a^8 \text{mod} 17=(13)^2 \text{mod} 17=16=(n-1)$
$\cdot$ Test returns: "17 is likely to be prime".

## When an integer passes Miller-Rabin’s Test, why does it return “Likely to be prime” and not “Certainly Prime”?

- If $n$ is prime then it passes the Miller-Rabin Test for all possible values of “a” ($1<a<(n-1)$). But it is only one-way implication.

- Any integer $n$ passes Miller-Rabin Test, there is a likelihood that $n$ may not be prime, since a composite number may also pass Miller-Rabin Test for certain values, but not for all possible values of “a” ($1<a<(n-1)$).

- If an integer $n$ passes the Miller-Rabin Test for one value of “a” $(1<a<(n-1))$ then the probability $n$ is not prime is less than $1/4$ and the probability that $n$ is prime greater than $1/4$.

- If an integer passes the Miller-Rabin Test with $t$ random values of “a,” then the probability that $n$ is prime greater than $(1-1/4)^t$.

## Example 4.42

Show that a composite number $n=25$ passes the Miller-Rabin test for some value of $a$.

## Solution

When $n=25$, $n-1=24=2^3 \times 3$.
$\cdot k=3$ and $q=3$

Let $a=7$
$X_0=a^q \pmod n=7^3 \pmod{25}=(49 \times 7) \pmod{25}=(24 \times 7) \pmod{25}=18$
$X_1=(X_0)^2 \pmod n=18^2 \pmod{25}=24=(n-1)$
Thus, 25, a composite number, passes the test with $a=7$.

Let us try with $a=11$
$X_0=a^3 \pmod n=11^3 \pmod{25}=(121 \times 11) \pmod{25}=(21 \times 11) \pmod{25}=6 \neq 1$
$X_1=a^6 \pmod{25}=(36) \pmod{25}=11 \neq (n-1)$
$X_2 = a^{12} \mod 25 = (11 \times 11) \mod 25 = 21 \neq (n - 1)$
$\cdot 25 returns “Composite” with $a = 11$.
Thus, 25 does not pass the test with $a = 11$.

**Procedure to determine a Prime Number with very high degree of certainty (using the Miller-Rabin Algorithm repeatedly):**

If the Miller-Rabin Test is invoked repeatedly for a given value of $n$, each time selecting a different randomly selected value of “a”, and the test returns “Likely to be prime” contiguously $t$ times, then the probability that $n$ is greater than $1-1/4$. If $t=10$, then the probability that $n$ is greater than $0.999999$.

**The Flow Chart in Figure 4.1 can be explained by the following:**

- Step 1: Choose a large odd integer $n$
- Step 2: Choose an integer “a” such that $1 < a < n-1$
- Step 3: Perform Miller-Rabin Test
- Step 4: If Miller-Rabin Test does not pass, reject the current value of $n$ since it is a composite number, and go back to Step 1 and choose another odd integer $n$.
- Step 5: If Miller-Rabin Test is passed, then check whether the current value of $n$ has passed the Miller-Rabin Test with $t \geq 10$ different selected values of “a”. If “No,” then go back to Step 2 and choose another value of “a” for Miller-Rabin Test.
- Step 6: If the current value of $n$ has passed the Miller-Rabin Test with $t$ randomly selected values of “a,” then “n is a prime number, with high degree of certainty.”

![img/d3b56042c756fbcc01ff06f1b9f530_212_0.png](img/d3b56042c756fbcc01ff06f1b9f530_212_0.png)
![img/d3b56042c756fbcc01ff06f1b9f530_212_1.png](img/d3b56042c756fbcc01ff06f1b9f530_212_1.png)
![img/d3b56042c756fbcc01ff06f1b9f530_212_2.png](img/d3b56042c756fbcc01ff06f1b9f530_212_2.png)
![img/d3b56042c756fbcc01ff06f1b9f530_212_3.png](img/d3b56042c756fbcc01ff06f1b9f530_212_3.png)
![img/d3b56042c756fbcc01ff06f1b9f530_212_4.png](img/d3b56042c756fbcc01ff06f1b9f530_212_4.png)
![img/d3b56042c756fbcc01ff06f1b9f530_212_5.png](img/d3b56042c756fbcc01ff06f1b9f530_212_5.png)
**FIGURE 4.1** Flow chart for the procedure to determine a Prime Number with high degree of certainty (using Miller-Rabin Algorithm repeatedly).

## 4.14 CHINESE REMAINDER THEOREM

**Example 4.43**

Show that $p=3$ and $q=4$ are two co-prime integers, and then each integer in the range $0–11$ can be uniquely represented by a pair of residues ($mod 3$ and mod 4$).

**Solution**

Table 4.27 illustrates the calculation of $(N \pmod 3)$ and $(N \pmod 4)$.

TABLE 4.27 Calculation of $(N \pmod 3)$ and $(N \pmod 4)$

| N | N mod 3 | N mod 4 |
|---|---|---|
| 0 | 0 | 0 |
| 1 | 1 | 1 |
| 2 | 2 | 2 |
| 3 | 0 | 3 |
| 4 | 1 | 0 |
| 5 | 2 | 1 |
| 6 | 0 | 2 |
| 7 | 1 | 3 |
| 8 | 2 | 0 |
| 9 | 0 | 1 |
| 10 | 1 | 2 |
| 11 | 2 | 3 |

- As illustrated in Table 4.27, each integer $N$ in the range $(0–11)$ is represented by a unique ordered pair of values $(N \pmod 3, N \pmod 4)$; for example, 5 can be represented by $(2, 1)$ and 9 can be represented by $(0, 1)$.

- This implies that each integer $N$ in the range $(0,...,11)$ can be reconstructed from the distinct ordered pair of values $(N \pmod 3, N \pmod 4)$.

- The set of values in the previous table will be repeated for the ranges $(12–23)$, $(24–35)$, and so on. For example, 13 in the range $(12–23)$ will be represented by unique pair of values (1, 1) and 25 in the range (24–35) will also be represented by (1, 1). All integers in a given range can be uniquely reconstructed from their residues (mod 3) and (mod 4).

## 1.1.4.1 Alternate Interpretation of the Chinese Remainder Theorem

Suppose $m_1, m_2, \dots, m_n$ be positive integers, pair-wise relatively prime to each other, that is, $GCD(m_i, m_j)$ where $i \le j$.

Let $m = m_1 \times m_2 \times \dots \times m_n$.

Then, the following set of congruence (mod $m$) has a unique solution, that is, $x$ has a unique solution in the range $0 \le x \le m$.

```
$x \equiv a_1 \pmod{m_1}$
$x \equiv a_2 \pmod{m_2}$
```

```
$x \equiv a_n \pmod{m_n}$
```

**Proof.**

Let $M_k = m / m_k,(1 \le k \le n)$, that is, $M_k$ is the product of all the moduli, except $m_k$. Since $m_k$ is relatively prime to all the other moduli in the previous set, $m_k$ will be relatively prime to their product $M_k$ too.

$\cdot GCD(M_k, m_k)=1$

Thus, there exists a multiplicative inverse $y_k$ of $M_k (mod \ m_k)$.

$\cdot y_k M_k \equiv 1 \pmod{m_k}$

$\cdot M_k y_k \equiv 1 \pmod{m_k},(1 \le k \le n)$

Multiplying both sides by $a_k$

```
$a_k M_k y_k \equiv a_k \pmod{m_k}$
```
