so in 1984, in a paper in which he showed that an insider posed a much greater threat than Eve. He could, like Eve, read $M$, but he could also break the system completely, and be able to view all messages and sign with anybody's key.$^3$

# 17.2.2 Attack 14. Insider's Factoring Attack on the Common Modulus

Suppose Mallet is the insider. We represent his enciphering and deciphering exponents by $e_M$ and $d_M$, respectively. His modulus, which is also held by all other users is represented by $n$. Mallet can multiply his two exponents together and subtract 1 and then factor out the highest power of 2 that divides this number to get

$(e_M)(d_M) - 1 = (2^k)(s)$

where $s$ is an integer that must be odd.

Mallet may then choose a random integer $a$, such that $1 < a < n - 1$. If $a$ and $n$ have a common divisor greater than 1, then the Euclidean algorithm can be used to find it, and it will be one of the primes, $p$ or $q$, used to generate $n$. Knowing the factorization of $n$ would then allow him to determine the private key of anyone in the system. Thus, we assume $a$ and $n$ are relatively prime.

If Mallet can find a value $x \neq \pm 1$ such that $x^2 = 1 \pmod n$, he can use $x$ to factor $n$ by writing $x^2 - 1 = 0 \pmod n$ and $(x - 1)(x + 1) = 0 \pmod n$. A prime factor of $n$ will then be provided by either $\gcd(x - 1, n)$ or $\gcd(x + 1, n)$. We'll return to this idea, but first, we make a few observations.

Because $(e_M)(d_M) = 1 \pmod{\varphi(n)}$, by definition, we have $(e_M)(d_M) - 1 = 0 \pmod{\varphi(n)}$. Mallet can substitute into this last equality using the identity $(e_M)(d_M) - 1 = (2^k)(s)$ to get $(2^k)(s) = 0 \pmod{\varphi(n)}$. In other words $(2^k)(s)$ is a multiple of $\varphi(n)$. Thus,

$a^{2^k s} = 1 \pmod n$.

It might be possible to replace $k$ with a smaller nonnegative integer such that the equality still holds. Let $k' > 0$ denote the smallest such number. Then, $a^{2^{k'} s} = 1 \pmod n$. So, $\left(a^{2^{k'-1} s}\right)^2 = 1 \pmod n$

Thus, Mallet has the desired value $x$ in the form $a^{2^{k'-1} s}$ He could be unlucky and have $a^{2^{k'-1} s} = -1 \pmod n$ in which case it is a square root of 1 $\pmod n$, but not one that is useful for factoring $n$. DeLaurentis showed that this happens at most half of the time. So, if Mallet is unlucky, he can simply randomly

$^3$ DeLaurentis, John M., “A Further Weakness in the Common Modulus Protocol for the RSA Cryptosystem,” Cryptologia, Vol. 8, No. 3, July 1984, pp. 253–259.