The decryption algorithm in \(\Sigma'\) simply throws away the first two bits of the ciphertext and then calls \(\Sigma\).Dec.

+   (a) Does \(\Sigma'\) have CPA$ security? Prove or disprove (if disproving, show a distinguisher and calculate its advantage).

+   (b) Does \(\Sigma'\) have CPA security? Prove or disprove (if disproving, show a distinguisher and calculate its advantage).

# 7.3. Suppose a user is using Construction 7.4 and an adversary observes two ciphertexts that have the same \(r\) value.

+   (a) What exactly does the adversary learn about the plaintexts in this case?

+   (b) How do you reconcile this with the fact that in the proof of Claim 7.5 there is a hybrid where \(r\) values are *never* repeated?

# 7.4. Construction 7.4 is a randomized encryption scheme, but we could also consider defining it as a **nonce-based** scheme, interpreting \(r\) as the nonce: Enc\((k, r, m) = (r, F(k, r) \oplus m)\). Formally prove that it is secure as a deterministic, nonce-based scheme. In other words, show that the following two libraries are indistinguishable, where \(\Sigma\) refers to Construction 7.4.

```
k \(\leftarrow\Sigma\).KeyGen
V := \(\emptyset\)
EAVESDROP(v, m_L, m_R \(\in\Sigma.\mathcal{M}\)):
if v \(\in\) V: return err
V := \(V \cup \{v\}\)
c := \(\Sigma\).Enc(k, v, m_L)
return c
```

```
k \(\leftarrow\Sigma\).KeyGen
V := \(\emptyset\)
EAVESDROP(v, m_L, m_R \(\in\Sigma.\mathcal{M}\)):
if v \(\in\) V: return err
V := \(V \cup \{v\}\)
c := \(\Sigma\).Enc(k, v, m_R)
return c
```

# 7.5. Let \(F\) be a secure PRP with blocklength \(blen = \lambda\). Consider the following randomized encryption scheme:

```
\mathcal{K} = \{0, 1\}^\lambda      KeyGen :       Enc(k, m) :
\mathcal{M} = \{0, 1\}^\lambda      k \leftarrow \{0, 1\}^\lambda   v \leftarrow \{0, 1\}^\lambda
\mathcal{C} = (\{0, 1\}^\lambda)^2    return k          x := F(k, v \oplus m)
                                    return (v, x)
```

+   (a) Give the decryption algorithm for this scheme.

+   (b) Prove that the scheme has CPA$ security.

+   (c) Suppose that we interpret this scheme as a nonce-based scheme, where \(v\) is the nonce. Show that the scheme does **not** have nonce-based CPA security. The libraries for this definition are given in the previous problem.

Note: Even in the standard CPA libraries, \(v\) is given to the adversary and it is unlikely to repeat. However, in the nonce-based libraries the adversary can *choose* \(v\), and this is what leads to problems.