7.8. Suppose $F$ is a secure PRP with blocklength $n + \lambda$. Below is the encryption algorithm for a scheme that supports plaintext space $\mathcal{M} = \{0, 1\}^n$:

```
Enc(k, m):
  r <- \{0, 1\}^\lambda
  return F(k, m||r)
```

+   (a) Describe the corresponding decryption algorithm.
+   (b) Prove that the scheme satisfies CPA$ security.

★ 7.9. Suppose $F$ is a secure PRP with blocklength $\lambda$. Give the decryption algorithm for the following scheme and prove that it does **not** have CPA security:

```
K = \{0, 1\}^\lambda                     Enc(k, m1||m2) :
M = \{0, 1\}^{2\lambda}                   r <- \{0, 1\}^\lambda
C = (\{0, 1\}^\lambda)^3                 s := F(k, r \oplus m_1)
                                             t := F(k, r \oplus m_1 \oplus F(k, m_1) \oplus m_2)
                                              return (r, s, t)
KeyGen :
  k <- \{0, 1\}^\lambda
  return k
```

★ 7.10. Suppose $F$ is a secure PRP with blocklength $\lambda$. Give the decryption algorithm for the following scheme and prove that it satisfies CPA$ security:

```
K = (\{0, 1\}^\lambda)^2               Enc((k, r), m) :
M = \{0, 1\}^\lambda                     s <- \{0, 1\}^\lambda
C = (\{0, 1\}^\lambda)^2                 x := F(k, s)
                                             y := F(k, s \oplus m \oplus r)
                                              return (x, y)
KeyGen :
  k <- \{0, 1\}^\lambda
  r <- \{0, 1\}^\lambda
  return (k, r)
```

Hint: You may find it useful to divide the Enc algorithm into two cases by introducing 'if m = ...'. Note: If $r = 0^\lambda$ then the scheme reduces to Exercise 7.7 (f). So it is important that $r$ is secret and random.

7.11. Let $\Sigma$ be an encryption scheme with plaintext space $\mathcal{M} = \{0, 1\}^n$ and ciphertext space $\mathcal{C} = \{0, 1\}^n$. Prove that $\Sigma$ cannot have CPA security.

Conclude that direct application of a PRP to the plaintext is not a good choice for an encryption scheme.

★ 7.12. In all of the CPA-secure encryption schemes that we’ll ever see, ciphertexts are at least $\lambda$ bits longer than plaintexts. This problem shows that such **ciphertext expansion** is essentially unavoidable for CPA security.

Let $\Sigma$ be an encryption scheme with plaintext space $\mathcal{M} = \{0, 1\}^n$ and ciphertext space $\mathcal{C} = \{0, 1\}^{n+\ell}$. Show that there exists a distinguisher that distinguishes the two CPA libraries with advantage $\Omega(1/2^\ell)$. 

Hint: As a warning, consider the case where each plaintext has exactly $2^\lambda$ possible ciphertexts. However, this need not be true in general. For the general case, choose a random plaintext $m$ and argue that with good probability, (that is, you should precisely quantify $m$) has at most $2^{\ell+1}$ possible ciphertexts.