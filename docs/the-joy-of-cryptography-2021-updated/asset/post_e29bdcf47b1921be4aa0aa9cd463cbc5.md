
Yes, this question is referring to the awful ECB encryption mode (Construction 8.1). Describe an attack that efficiently recovers all of s using access to ECBORACLE. Assume that if the length of m||s is not a multiple of the blocklength, then ECB mode will pad it with null bytes.

(b) Now suppose you have access to a CBC encryption oracle, where you can control the IV that is used:

```
CBCORACLE(iv, m):
// k, s are secret
return CBC.Enc(k, iv, m||s)
```

Describe an attack that efficiently recovers all of s using access to CBCORACLE. As above, assume that m||s is padded to a multiple of the blocklength in some way. It is possible to carry out the attack no matter what the padding method is, as long as the padding method is known to the adversary.

## ⋆ 9.5. Show how a padding oracle (for CBC-mode encryption with X.923 padding) can be used to **generate a valid encryption** of any chosen plaintext, under the same (secret) key that the padding oracle uses. In this problem, you are not given access to an encryption subroutine, or any valid ciphertexts — only the padding oracle subroutine.

## 9.6. Prove formally that CCA$ security implies CCA security.

## 9.7. Let $\Sigma$ be an encryption scheme with message space $\{0, 1\}^n$ and define $\Sigma^2$ to be the following encryption scheme with message space $\{0, 1\}^{2n}$:

```
KeyGen:          Enc(k, m):                 Dec(k, (c1, c2)):
k <- Sigma.KeyGen c1 := Sigma.Enc(k, mleft)  m1 := Sigma.Dec(k, c1)
return k         c2 := Sigma.Enc(k, mright)  m2 := Sigma.Dec(k, c2)
                 return (c1, c2)             if err in {m1, m2}:
                                             return err
                                             else return m1 || m2
```

- (a) Prove that if $\Sigma$ has CPA security, then so does $\Sigma^2$.

- (b) Show that even if $\Sigma$ has CCA security, $\Sigma^2$ does not. Describe a successful distinguisher and compute its distinguishing advantage.

## 9.8. Show that the following block cipher modes do not have CCA security. For each one, describe a successful distinguisher and compute its distinguishing advantage.

- (a) OFB mode (b) CBC mode (c) CTR mode

## 9.9. Show that none of the schemes in Exercise 7.7 have CCA security. For each one, describe a successful distinguisher and compute its distinguishing advantage.

## 9.10. Let F be a secure block cipher with blocklength $\lambda$. Below is an encryption scheme for plaintexts $\mathcal{M} = \{0, 1\}^\lambda$. Formally describe its decryption algorithm and show that it does **not** have CCA security.

```
KeyGen:
  k <- {0, 1}^\lambda
  return k

Enc(k, m):
  r <- {0, 1}^\lambda
  c1 := F(k, r)
  c2 := r \oplus F(k, m)
  return (c1, c2)
```

## 9.11. Let F be a secure block cipher with blocklength $\lambda$. Below is an encryption scheme for plaintexts $\mathcal{M} = \{0, 1\}^\lambda$. Formally describe its decryption algorithm and show that it does **not** have CCA security.

```
KeyGen:
  k1 <- {0, 1}^\lambda
  k2 <- {0, 1}^\lambda
  return (k1, k2)

Enc((k1, k2), m):
  r <- {0, 1}^\lambda
  c1 := F(k1, r)
  c2 := F(k1, r \oplus m \oplus k2)
  return (c1, c2)
```

## 9.12. Alice has the following idea for a CCA-secure encryption. To encrypt a single plaintext block m, do normal CBC encryption of $0^{blen}||m$. To decrypt, do normal CBC decryption but give an error if the first plaintext block is not all zeroes. Her reasoning is:

- The ciphertext has 3 blocks (including the IV). If an adversary tampers with the IV or the middle block of a ciphertext, then the first plaintext block will no longer be all zeroes and the ciphertext is rejected.
- If an adversary tampers with the last block of a ciphertext, then the CBC decryption results in $0^{blen}||m'$ where m' is unpredictable from the adversary’s point of view. Hence the result of decryption ($m'$) will leak no information about the original m.

More formally, let CBC denote the encryption scheme obtained by using a secure PRF in CBC mode. Below we define an encryption scheme $\Sigma'$ with message space $\{0, 1\}^{blen}$ and ciphertext space $\{0, 1\}^{3blen}$:

```
$\Sigma'.KeyGen$:
  k <- CBC.KeyGen
  return k

$\Sigma'.Enc(k, m)$:
  return CBC.Enc(k, $0^{blen}||m$)

$\Sigma'.Dec(k, c)$:
  m1 || m2 := CBC.Dec(k, c)
  if m1 = $0^{blen}$:
    return m2
  else return err
```

Show that $\Sigma'$ does **not** have CCA security. Describe a distinguisher and compute its distinguishing advantage. What part of Alice’s reasoning was not quite right?

Hint:
Ask the library to decrypt c = c0 || c1 || c2 || c3 with both known plaintexts
Obtain a ciphertext c = c0 || c1 || c2 || c3 and another ciphertext c' = c'0 || c'1 || c'2 || c'3 with both known plaintexts

## 9.13. CBC and OFB modes are malleable in very different ways. For that reason, Mallory claims that encrypting a plaintext (independently) with both modes results in CCA security, when the Dec algorithm rejects ciphertexts whose OFB and CBC plaintexts don’t match. The reasoning is that it will be hard to tamper with both ciphertexts in a way that achieves the same effect on the plaintext.

Let CBC denote the encryption scheme obtained by using a secure PRF in CBC mode. Let OFB denote the encryption scheme obtained by using a secure PRF in OFB mode. Below we define an encryption scheme $\Sigma'$:

```
$\Sigma'.\text{KeyGen}$:
\(k_{\text{cbc}} \leftarrow \text{CBC.KeyGen}\)
\(k_{\text{ofb}} \leftarrow \text{OFB.KeyGen}\)
return \((k_{\text{cbc}}, k_{\text{ofb}})\)

$\Sigma'.\text{Enc}((k_{\text{cbc}}, k_{\text{ofb}}), m)$:
\(c := \text{CBC.Enc}(k_{\text{cbc}}, m)\)
\(c' := \text{OFB.Enc}(k_{\text{ofb}}, m)\)
return \((c, c')\)

$\Sigma'.\text{Dec}((k_{\text{cbc}}, k_{\text{ofb}}), (c, c'))$:
\(m := \text{CBC.Dec}(k_{\text{cbc}}, c)\)
\(m' := \text{OFB.Dec}(k_{\text{ofb}}, c')\)
if \(m = m'\):
    return \(m\)
else return \(\text{err}\)
```

Show that $\Sigma'$ does **not** have CCA security. Describe a distinguisher and compute its distinguishing advantage.

## 9.14. This problem is a generalization of the previous one. Let $\Sigma_1$ and $\Sigma_2$ be two (possibly different) encryption schemes with the same message space $\mathcal{M}$. Below we define an encryption scheme $\Sigma'$:

```
$\Sigma'.\text{KeyGen}$:
\(k_1 \leftarrow \Sigma_1.\text{KeyGen}\)
\(k_2 \leftarrow \Sigma_2.\text{KeyGen}\)
return \((k_1, k_2)\)

$\Sigma'.\text{Enc}((k_1, k_2), m)$:
\(c_1 := \Sigma_1.\text{Enc}(k_1, m)\)
\(c_2 := \Sigma_2.\text{Enc}(k_2, m)\)
return \((c_1, c_2)\)

$\Sigma'.\text{Dec}((k_1, k_2), (c_1, c_2))$:
\(m_1 := \Sigma_1.\text{Dec}(k_1, c_1)\)
\(m_2 := \Sigma_2.\text{Dec}(k_2, c_2)\)
if \(m_1 = m_2\):
    return \(m_1\)
else return \(\text{err}\)
```

Show that $\Sigma'$ does **not** have CCA security, even if both $\Sigma_1$ and $\Sigma_2$ have CCA (yes, CCA) security. Describe a distinguisher and compute its distinguishing advantage.

## 9.15. Consider any padding scheme consisting of subroutines $\text{PAD}$ (which adds valid padding to its argument) and $\text{VALIDPAD}$ (which checks its argument for valid padding and returns true/false). Assume that $\text{VALIDPAD}(\text{PAD}(x)) = \text{true}$ for all strings $x$.

Show that if an encryption scheme $\Sigma$ has CCA security, then the following two libraries are indistinguishable:

```
L^\Sigma_{pad-L}

k \leftarrow \Sigma.KeyGen
\underline{eavesdrop(m_L, m_R \in \Sigma.M):}
if |m_L| \neq |m_R| return err
return \Sigma.Enc(k, pad(m_L))
\underline{paddingoracle(c \in \Sigma.C):}
return validpad(\Sigma.Dec(k, c))
```

```
L^\Sigma_{pad-R}

k \leftarrow \Sigma.KeyGen
\underline{eavesdrop(m_L, m_R \in \Sigma.M):}
if |m_L| \neq |m_R| return err
return \Sigma.Enc(k, pad(m_R))
\underline{paddingoracle(c \in \Sigma.C):}
return validpad(\Sigma.Dec(k, c))
```

That is, a CCA-secure encryption scheme hides underlying plaintexts in the presence of padding-oracle attacks.

Note: The distinguisher can even send a ciphertext c obtained from eavesdrop as an argument to paddingoracle. Your proof should somehow account for this when reducing to the CCA security of \(\Sigma\).

## 9.16. Show that an encryption scheme \(\Sigma\) has CCA$ security if and only if the following two libraries are indistinguishable:

```
L^\Sigma_{left}

k \leftarrow \Sigma.KeyGen
\underline{eavesdrop(m \in \Sigma.M):}
return \Sigma.Enc(k, m)
\underline{decrypt(c \in \Sigma.C):}
return \Sigma.Dec(k, c)
```

```
L^\Sigma_{right}

k \leftarrow \Sigma.KeyGen
D := empty assoc. array
\underline{eavesdrop(m \in \Sigma.M):}
c \leftarrow \Sigma.C(|m|)
D[c] := m
return c
\underline{decrypt(c \in \Sigma.C):}
if D[c] exists: return D[c]
else: return \Sigma.Dec(k, c)
```

Note: In \(\mathcal{L}_{left}\), the adversary can obtain the decryption of *any* ciphertext via decrypt. In \(\mathcal{L}_{right}$, the decrypt subroutine is “patched” (via D) to give reasonable answers to ciphertexts generated in eavesdrop.
