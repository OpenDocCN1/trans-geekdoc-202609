

## 8.7. Prove that there is an attacker that runs in time \(O(2^{\lambda/2})\) and that can break CPA security of CBC mode encryption with constant probability.

## 8.8. Below are several block cipher modes for encryption, applied to a PRF \(F\) with blocklength \(blen = \lambda\). For each of the modes:

- Describe the corresponding decryption procedure.
- Show that the mode does **not** have CPA-security. That means describe a distinguisher and compute its advantage.

```
Enc(k, m_1 || ... || m_\ell):
r_0 \leftarrow \{0, 1\}^\lambda
c_0 := r_0
for i = 1 to \ell:
  r_i := F(k, m_i)
  c_i := r_i \oplus r_{i-1}
return c_0 || ... || c_\ell
```

```
Enc(k, m_1 || ... || m_\ell):
c_0 \leftarrow \{0, 1\}^\lambda
m_0 := c_0
for i = 1 to \ell:
  c_i := F(k, m_i) \oplus m_{i-1}
return c_0 || ... || c_\ell
```

```
Enc(k, m_1 || ... || m_\ell):
c_0 \leftarrow \{0, 1\}^\lambda
for i = 1 to \ell:
  c_i := F(k, m_i) \oplus c_{i-1}
return c_0 || ... || c_\ell
```

```
Enc(k, m_1 || ... || m_\ell):
c_0 \leftarrow \{0, 1\}^\lambda
r_0 := c_0
for i = 1 to \ell:
  r_i := r_{i-1} \oplus m_i
  c_i := F(k, r_i)
return c_0 || ... || c_\ell
```

Mode (a) is similar to CBC, except the xor happens after, rather than before, the block cipher application. Mode (c) is essentially the same as CBC decryption.

## 8.9. Suppose you observe a CBC ciphertext and two of its blocks happen to be identical. What can you deduce about the plaintext? State some non-trivial property of the plaintext that doesn’t depend on the encryption key.

## 8.10. The CPA$-security proof for CBC encryption has a slight complication compared to the proof of OFB encryption. Recall that an important part of the proof is arguing that all inputs to the PRF are distinct.

In OFB, outputs of the PRF were fed directly into the PRF as inputs. The adversary had no influence over this process, so it wasn’t so bad to argue that all PRF inputs were distinct (with probability negligibly close to 1).

By contrast, CBC mode takes an output block from the PRF, xor’s it with a plaintext block (which is after all *chosen by the adversary*), and uses the result as input to the next PRF call. This means we have to be a little more careful when arguing that CBC mode gives distinct inputs to all PRF calls (with probability negligibly close to 1).

### (a) Prove that the following two libraries are indistinguishable:

```
\mathcal{L}_{\text{left}}
\text{SAMP}(m \in \{0, 1\}^\lambda):
r \leftarrow \{0, 1\}^\lambda
\text{return } r

\mathcal{L}_{\text{right}}
R := \emptyset
\text{SAMP}(m \in \{0, 1\}^\lambda):
r \leftarrow \{r' \in \{0, 1\}^\lambda \mid r' \oplus m \notin R\}
R := R \cup \{r \oplus m\}
\text{return } r
```

Hint: Use Lemma 4.12.

### (b) Using part (a), and the security of the underlying PRF, prove the CPA$-security of CBC mode.

Hint: call that will be on a 'fresh' input. It is never been seen before. This Guarantees that the next PRF call is uniformly random in $\mathcal{L}_{\text{right}}$. Let $m$ correspond to the next plaintext block $m$ has already been sampled $r$ (the output of the PRF before it). Then $m$ corresponds to the next plaintext block $m$ call it $\mathcal{L}_{\text{right}}$. Let $R$ correspond to the set of all inputs sent to the PRF.

Note: Appreciate how important it is that the adversary chooses plaintext block $m$ before "seeing" the output $r$ from the PRF (which is included in the ciphertext).

## ★ 8.11. Prove that CTR mode achieves CPA$ security.

Hint: Use Lemma 4.12 to show that here it is only negligible probability of choosing the IV so that the block cipher gets called on the same value twice.

## 8.12. Let $F$ be a secure PRF with $out = in = \lambda$ and let $F^{(2)}$ denote the function $F^{(2)}(k, r) = F(k, F(k, r))$.

### (a) Prove that $F^{(2)}$ is also a secure PRF.

### (b) What if $F$ is a secure PRP with blocklength $blen$? Is $F^{(2)}$ also a secure PRP?

## 8.13. This question refers to the nonce-based notion of CPA security.

### (a) Show a definition for CPA$ security that incorporates both the nonce-based syntax of Section 7.1 and the variable-length plaintexts of Section 8.2.

### (b) Show that CBC mode **not** secure as a nonce-based scheme (where the IV is used as a nonce).

### (c) Show that CTR mode is **not** secure as a nonce-based scheme (where the IV is used as a nonce). Note that if we restrict (randomized) CTR mode to a single plaintext block, we get the CPA-secure scheme of Construction 7.4, which **is** secure as a nonce-based scheme. The attack must therefore use the fact that plaintexts can be longer than one block. (Does the attack in part (b) work with single-block plaintexts?)

## 8.14. One way to convert a randomized-IV-based construction into a nonce-based construction is called the **synthetic IV** approach.

### (a) The synthetic-IV (SIV) approach applied to CBC mode is shown below. Prove that it is CPA/CPA$ secure as a nonce-based scheme (refer to the security definitions from the previous problem):

```
SIV-CBC.Enc((k1, k2), v, m1 || ... || ml):
c0 := F(k1, v)
for i = 1 to l:
  ci := F(k2, mi ⊕ c(i-1))
return c0 || c1 || ... || cl
```

Instead of choosing a random IV c0, it is generated deterministically from the nonce v using the block cipher F. In your proof, you can use the fact that randomized CBC mode has CPA$ security, and that F is also a secure PRF.

### (b) It is important that the SIV construction uses two keys for different purposes. Suppose that we instead used the same key throughout:

```
BadSIV-CBC.Enc(k, v, m1 || ... || ml):
c0 := F(k, v)
for i = 1 to l:
  ci := F(k, mi ⊕ c(i-1))
return c0 || c1 || ... || cl
```

Show that the resulting scheme does not have CPA$ security (in the nonce-based sense). Ignore the complication of padding, and only consider plaintexts that are a multiple of the blocklength. Describe a successful distinguisher and compute its advantage.

### (c) For randomized encryption, it is necessary to include the IV in the ciphertext; otherwise the receiver cannot decrypt. In the nonce-based setting we assume that the receiver knows the correct nonce (e.g., from some out-of-band communication). With that in mind, we could modify the scheme from part (b) to remove c0, since the receiver could reconstruct it anyway from v.

Show that even with this modification, the scheme still fails to be CPA-secure under the nonce-based definition.

## 8.15. Implementers are sometimes cautious about IVs in block cipher modes and may attempt to “protect” them. One idea for protecting an IV is to prevent it from directly appearing in the ciphertext. The modified CBC encryption below sends the IV through the block cipher before including it in the ciphertext:

```
Enc(k, m1 || ... || ml):
c0 ← {0, 1}^blen
c’0 := F(k, c0)
for i = 1 to l:
  ci := F(k, mi ⊕ c(i-1))
return c’0 || c1 || ... || cl
```

This ciphertext can be decrypted by first computing $c_0 := F^{-1}(k, c'_0)$ and then doing usual CBC decryption on $c_0 || \cdots || c_\ell$. Show that this new scheme is **not** CPA-secure (under the traditional definitions for randomized encryption).

## 8.16. Suppose a bad implementation leads to two ciphertexts being encrypted with the same IV, rather than a random IV each time.

### (a) Characterize as thoroughly as you can what information is leaked about the plaintexts when CBC mode was used and an IV is repeated.

### (b) Characterize as thoroughly as you can what information is leaked about the plaintexts when CTR mode was used and an IV is repeated.

## 8.17. Describe how to extend CTR and OFB modes to deal with plaintexts of arbitrary length (without using padding). Why is it so much simpler than CBC ciphertext stealing?

## 8.18. The following technique for ciphertext stealing in CBC was proposed in the 1980s and was even adopted into commercial products. Unfortunately, it’s insecure.

Suppose the final plaintext block \( m_\ell \) is \( blen - j \) bits long. Rather than padding the final block with zeroes, it is padded with *the last \( j \) bits of ciphertext block \( c_{\ell-1} \). Then the padded block \( m_\ell \) is sent through the PRP to produce the final ciphertext block \( c_\ell \). Since the final \( j \) bits of \( c_{\ell-1} \) are recoverable from \( c_\ell \), they can be discarded. If the final block of plaintext is already *blen* bits long, then standard CBC mode is used.

![](img/da79fa21b263fe549aecaabd2a0a41c8_170_0.png)

Show that the scheme does **not** satisfy CPA$ security. Describe a distinguisher and compute its advantage.

Hint: Ask for several encryptions of plaintexts whose last block is blen - 1 bits long.

## 8.19. Prove that *any* CPA-secure encryption remains CPA-secure when augmented by padding the input.

## 8.20. Prove that CBC with ciphertext stealing has CPA$ security. You may use the fact that CBC mode has CPA$ security when restricted to plaintexts whose length is an exact multiple of the blocklength (i.e., CBC mode without padding or ciphertext stealing).
