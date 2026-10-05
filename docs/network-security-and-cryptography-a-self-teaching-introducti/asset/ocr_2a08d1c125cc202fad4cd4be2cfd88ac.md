Then Euler's Totient Function of $n$ will be:

```
$\phi(n)=p_1^{k_1-1}\phi(p_1)p_2^{k_2-1}\phi(p_2)\dots p_k^{k_k-1}\phi(p_k)=\prod_{i=1}^{k}(p_i^{k_i-1}\phi(p_i)) \quad (4.11)$
```

# Example 4.26

Determine $\phi(n)$ for the following values of $n$:

+   **A.** 735
**B.** 400
**C.** 3375

# Solution

+   **A.** $735=7^2	imes5	imes3$
$\phi(735)=\phi(7^2)	imes\phi(5)	imes\phi(3)$
$=7	imes\phi(7)	imes4	imes2$\n$=7	imes6	imes4	imes2$\n$=336$

+   **B.** $400=2^4	imes5^2$
$\phi(400)=\phi(2^4)	imes\phi(5^2)$
$=2^3	imes\phi(2)	imes5	imes\phi(5)$
$=8	imes1	imes5	imes4$\n$=160$

+   **C.** $3375=5^3	imes3^3$
$\phi(3375)=\phi(5^3)	imes\phi(3^3)$
$=5^2	imes\phi(5)	imes3^2	imes\phi(3)$
$=25	imes4	imes9	imes2$\n$=1800$

# 4.10 EULER'S THEOREM

If $a$ and $n$ are two integers relatively prime to each other, then $a^{\phi(n)}\equiv 1 \pmod{n}$.