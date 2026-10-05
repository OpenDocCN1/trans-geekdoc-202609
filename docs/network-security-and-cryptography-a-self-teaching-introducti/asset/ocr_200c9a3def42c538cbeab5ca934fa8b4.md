384 • NETWORK SECURITY AND CRYPTOGRAPHY

+   3. Computes $r = (g^k \bmod p) \bmod q$.
4. Computes $s = k^{-1} (m + rx) \bmod q$.

+   5. If $((r=0)$ or $(s=0))$ then repeats steps 1 to 4 by choosing another value of $k$. The parameters have to be non-zero, so that $s^{-1} \bmod q$ is defined.

+   6. Now, $(r, s)$ forms the digital signature which is sent to the intended recipient along with the message $M$.

# 8.8.3.4 Signature Verification Algorithm

Knowing the Public Key $(p, q, g, y)$ of use “A,” the recipient will verify the digital signature $(r, s)$ as follows:

+   1. Compute $m = H(M).$.

+   2. Verify that $t < r$ and $0 < s < q$; else reject the signature.

+   3. Compute $t = s^{-1} \bmod q$.

+   4. Compute $v = ((gm^y)^r \bmod p) \bmod q$

+   5. If $v = r$ then accept the signature; else reject it.

# Proof

$v = ((gm^y)^r \bmod p) \bmod q$
$= ((gm^{yr}) \bmod p) \bmod q$
$= ((g^{s+ry}}) \bmod p) \bmod q$
Since $s = k^{-1}(m+rx)$
.: $(m+rx) = ks$
.: $v = ((g^{kst} \bmod q) \bmod p) \bmod q$
Since $t = s^{-1} \bmod q$
.: $st \bmod q = 1$
.: $v = (g^k \bmod p) \bmod q = r$
Thus, the Proof.