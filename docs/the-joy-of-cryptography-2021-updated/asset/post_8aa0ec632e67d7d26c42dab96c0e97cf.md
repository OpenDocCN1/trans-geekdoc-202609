
SALVIATI: Oh Simplicio, now you are becoming bothersome! This value $r$ is $\lambda$ bits long and chosen uniformly at random each time. Do you not recall our agonizingly long discussion about the birthday paradox?

SIMPLICIO: Oh yes, now I remember it well. Now I believe I understand all of your reasoning: Across all ciphertexts that are generated, $r$ is unlikely to repeat because of the birthday paradox. Now, provided that $r$ never repeats, Alice invokes the PRF on distinct inputs. A PRF invoked on distinct inputs provides outputs that are uniformly random for all intents and purposes. Hence, using these outputs as one-time pads completely hides the plaintext. Is that right, Salviati?

SALVIATI: Excellent! Now we may return to discussing the motion of the Sun and Earth . . .

Look for Simplicio's final summary to be reflected in the sequence of hybrids used in the formal proof:

Proof We prove that \(\mathcal{L}^\Sigma_{\text{cpa\$-real}} \approx \mathcal{L}^\Sigma_{\text{cpa\$-rand}}\) using the hybrid technique:

```
\mathcal{L}^\Sigma_{\text{cpa\$-real}}

k \leftarrow \{0, 1\}^\lambda

\underline{\text{CTXT}(m)}:
  r \leftarrow \{0, 1\}^\lambda
  x := F(k, r) \oplus m
  return (r, x)
```

The starting point is \(\mathcal{L}^\Sigma_{\text{cpa\$-real}}\). The details of \(\Sigma\) have been filled in and highlighted.

```
\underline{\text{CTXT}(m)}:
  r \leftarrow \{0, 1\}^\lambda
  z := \text{LOOKUP}(r)
  x := z \oplus m
  return (r, x)
```

```
\mathcal{L}^F_{\text{prf-real}}

k \leftarrow \{0, 1\}^\lambda

\underline{\text{LOOKUP}(r)}:
  return F(k, r)
```

The statements pertaining to the PRF have been factored out in terms of the \(\mathcal{L}^F_{\text{prf-real}}\) library.

```
\underline{\text{CTXT}(m)}:
  r \leftarrow \{0, 1\}^\lambda
  z := \text{LOOKUP}(r)
  x := z \oplus m
  return (r, x)
```

```
\mathcal{L}^F_{\text{prf-rand}}

T := empty

\underline{\text{LOOKUP}(r)}:
  if T[r] undefined:
    T[r] \leftarrow \{0, 1\}^\text{out}
    return T[r]
```

We have replaced \(\mathcal{L}^F_{\text{prf-real}}\) with \(\mathcal{L}^F_{\text{prf-rand}}\). From the PRF security of F, these two hybrids are indistinguishable.

At this point in the proof, it is easy to imagine that we are done. Ciphertexts have the form \((r, x)\), where \(r\) is chosen uniformly and \(x\) is the result of encrypting the plaintext with what appears to be a “one-time pad key” is T[r] — a value that could potentially be used more than once if r is ever repeated!

As Simplicio rightly pointed out, a PRF gives independently random(-looking) outputs when called on distinct inputs. But in our current hybrid there is no guarantee that PRF inputs are distinct! Our proof must explicitly contain reasoning about why PRF inputs are unlikely to be repeated. We do so by appealing to the sampling-with-replacement lemma of Lemma 4.11.

We first factor out the sampling of r values into a subroutine. The subroutine corresponds to the L_samp-L library of Lemma 4.11:

```
CTXT(m):
r ← SAMP()
z := LOOKUP(r)
x := z ⊕ m
return (r, x)

L^F_prf-rand
T := empty
LOOKUP(r):
if T[r] undefined:
  T[r] ← {0, 1}^out
return T[r]

L_samp-L
SAMP():
r ← {0, 1}^λ
return r
```

Next, L_samp-L is replaced by L_samp-R. By Lemma 4.11, the difference is indistinguishable:

```
CTXT(m):
r ← SAMP()
z := LOOKUP(r)
x := z ⊕ m
return (r, x)

L^F_prf-rand
T := empty
LOOKUP(r):
if T[r] undefined:
  T[r] ← {0, 1}^out
return T[r]

L_samp-R
R := ∅
SAMP():
r ← {0, 1}^λ \ R
R := R ∪ {r}
return r
```

Inspecting the previous hybrid, we can reason that the arguments to LOOKUP are guaranteed to never repeat. Therefore the L_prf-rand library can be greatly simplified. In particular, the if-condition in L_prf-rand is always true. Simplifying has no effect on the library’s output behavior:

```
CTXT(m):
r ← SAMP()
z := LOOKUP(r)
x := z ⊕ m
return (r, x)

LOOKUP(r):
t ← {0, 1}^out
return t

L_samp-R
R := ∅
SAMP():
r ← {0, 1}^λ \ R
R := R ∪ {r}
return r
```

Now we are indeed using unique one-time pads to mask the plaintext. We are in much better shape than before. Recall that our goal is to arrive at a hybrid in which the outputs of CTXT are chosen uniformly. These outputs include the value r, but now r is no longer being chosen uniformly! We must revert r back to being sampled uniformly, and then we are nearly to the finish line.

```
CTXT(m):
  r <- SAMP()
  z := LOOKUP(r)
  x := z $\oplus$ m
  return (r, x)
```

```
LOOKUP(r):
  t <- {0, 1}$^{\text{out}}$
  return t
```

```
$\mathcal{L}_{\text{samp-L}}$
SAMP():
  r <- {0, 1}$^\lambda$
  return r
```

As promised, $\mathcal{L}_{\text{samp-R}}$ has been replaced by $\mathcal{L}_{\text{samp-L}}$. The difference is indistinguishable due to Lemma 4.11.

```
CTXT(m):
  r <- {0, 1}$^\lambda$
  z <- {0, 1}$^{\text{out}}$
  x := z $\oplus$ m
  return (r, x)
```

All of the subroutine calls have been inlined; no effect on the library’s output behavior.

```
$\mathcal{L}^\Sigma_{\text{cpa\$-rand}}$:
CTXT(m):
  r <- {0, 1}$^\lambda$
  x <- {0, 1}$^{\text{out}}$
  return (r, x)
```

We have applied the one-time pad rule with respect to variables $z$ and $x$, but omitted the very familiar steps (factor out, replace library, inline) that we have seen several times before. The resulting library is precisely $\mathcal{L}^\Sigma_{\text{cpa\$-rand}}$ since it samples uniformly from $\Sigma.\mathcal{C} = \{0, 1\}^\lambda \times \{0, 1\}^{\text{out}}$.

The sequence of hybrids shows that $\mathcal{L}^\Sigma_{\text{cpa\$-real}} \approx \mathcal{L}^\Sigma_{\text{cpa\$-rand}}$, so $\Sigma$ has pseudorandom ciphertexts.

## Exercises

### 7.1. Let $\Sigma$ be an encryption scheme, and suppose there is a program $\mathcal{A}$ that recovers the key from a chosen plaintext attack. More precisely, $\Pr[\mathcal{A} \diamond \mathcal{L} \text{ outputs } k]$ is non-negligible, where $\mathcal{L}$ is defined as:

```
$\mathcal{L}$
k <- $\Sigma$.KeyGen
CHALLENGE($m \in \Sigma.\mathcal{M}$):
  c := $\Sigma$.Enc(k, m)
  return c
```

Prove that if such an $\mathcal{A}$ exists, then $\Sigma$ does not have CPA security. Use $\mathcal{A}$ as a subroutine in a distinguisher that violates the CPA security definition.

In other words, CPA security implies that it should be hard to determine the key from seeing encryptions of chosen plaintexts.

### 7.2. Let $\Sigma$ be an encryption scheme with CPA$ security. Let $\Sigma'$ be the encryption scheme defined by:

$\Sigma'.\text{Enc}(k, m) = 00 || \Sigma.\text{Enc}(k, m)$

The decryption algorithm in \(\Sigma'\) simply throws away the first two bits of the ciphertext and then calls \(\Sigma\).Dec.

- (a) Does \(\Sigma'\) have CPA$ security? Prove or disprove (if disproving, show a distinguisher and calculate its advantage).
- (b) Does \(\Sigma'\) have CPA security? Prove or disprove (if disproving, show a distinguisher and calculate its advantage).

### 7.3. Suppose a user is using Construction 7.4 and an adversary observes two ciphertexts that have the same \(r\) value.

- (a) What exactly does the adversary learn about the plaintexts in this case?
- (b) How do you reconcile this with the fact that in the proof of Claim 7.5 there is a hybrid where \(r\) values are *never* repeated?

### 7.4. Construction 7.4 is a randomized encryption scheme, but we could also consider defining it as a **nonce-based** scheme, interpreting \(r\) as the nonce: Enc\((k, r, m) = (r, F(k, r) \oplus m)\). Formally prove that it is secure as a deterministic, nonce-based scheme. In other words, show that the following two libraries are indistinguishable, where \(\Sigma\) refers to Construction 7.4.

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

### 7.5. Let \(F\) be a secure PRP with blocklength \(blen = \lambda\). Consider the following randomized encryption scheme:

| | KeyGen | Enc(k, m) |
|---|---|---|
| $\mathcal{K} = \{0, 1\}^\lambda$ | | |
| $\mathcal{M} = \{0, 1\}^\lambda$ | $k \leftarrow \{0, 1\}^\lambda$ | $v \leftarrow \{0, 1\}^\lambda$ |
| $\mathcal{C} = (\{0, 1\}^\lambda)^2$ | return k | $x := F(k, v \oplus m)$ |
| | | return $(v, x)$ |

- (a) Give the decryption algorithm for this scheme.
- (b) Prove that the scheme has CPA$ security.
- (c) Suppose that we interpret this scheme as a nonce-based scheme, where \(v\) is the nonce. Show that the scheme does **not** have nonce-based CPA security. The libraries for this definition are given in the previous problem.

Note: Even in the standard CPA libraries, \(v\) is given to the adversary and it is unlikely to repeat. However, in the nonce-based libraries the adversary can *choose* \(v\), and this is what leads to problems.
