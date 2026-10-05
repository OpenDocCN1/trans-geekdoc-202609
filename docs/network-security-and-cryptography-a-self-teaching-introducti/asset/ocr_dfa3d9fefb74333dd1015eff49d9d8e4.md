# 8.8.3.5 Why Are r and v Computed (mod p) and Then (mod q) but s and t Are Computed Directly (mod q)?

$r = (g^k \mod p) \mod q$

The argument for computation of $r$ is $g$, which is computed $(mod p)$. That is why $r$ is first computed $(mod p)$ and then $(mod q)$.

Similarly, $v = ((g^y)^k \mod p) \mod q$.

The arguments for $v$ are $g$ and $y$ and both have been computed $(mod p)$. That is why $v$ also first computed $(mod p)$ and then $(mod q)$.

$s = k^{-1} (m + rx) \mod q$.

All the arguments of $s$, that is, $k, m, r$, and $x$, are integers less than $q$. That is why $s$ is computed $(mod q)$.

$T = s^{-1} \mod q$

This argument holds for $s$ also holds for $t$.

![](bbox=[0.169, 0.452, 0.869, 0.676])

**FIGURE 8.19** A schematic diagram depicting DSA.

where

M: Message to be sent

H: Hash Function

$KR_s = (p, q, g, x)$ : Private Key of Sender

$p$: Prime Number (512 to 1024 bits long)

$q$: prime (160 bits long) such that $q$ divides $\Phi (p)$