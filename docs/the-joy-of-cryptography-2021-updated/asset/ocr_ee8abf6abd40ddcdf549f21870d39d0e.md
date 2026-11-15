**Definition 6.1 (PRF security)** Let $F : \{0, 1\}^\lambda \times \{0, 1\}^{in} \to \{0, 1\}^{out}$ be a deterministic function. We say that $F$ is a secure pseudorandom function (PRF) if $\mathcal{L}_{\text{prf-real}}^F \approx \mathcal{L}_{\text{prf-rand}}^F$, where:

| $\mathcal{L}^F_{\text{prf-real}}$ |
|---|
| $k \leftarrow \{0, 1\}^\lambda$ |
| $\underline{\text{LOOKUP}(x \in \{0, 1\}^{in}): \text{return } F(k, x)}$ |

| $\mathcal{L}^F_{\text{prf-rand}}$ |
|---|
| $T := \text{empty assoc. array}$ |
| $\underline{\text{LOOKUP}(x \in \{0, 1\}^{in}):}$ |
| if $T[x]$ undefined: |
| $T[x] \leftarrow \{0, 1\}^{out}$ |
| return $T[x]$ |

# Discussion, Pitfalls

The name “pseudorandom function” comes from the perspective of viewing $T$ not as an (associative) array, but as a function $T : \{0, 1\}^{in} \to \{0, 1\}^{out}$. There are $2^{out \cdot 2^{in}}$ possible functions for $T$ (an incredibly large number), and $\mathcal{L}_{\text{prf-rand}}$ chooses a “random function” by uniformly sampling its truth table as needed.

For each possible seed $k$, the residual function $F(k, \cdot)$ is also a function from $\{0, 1\}^{in} \to \{0, 1\}^{out}$. There are “only” $2^\lambda$ possible functions of this kind (one for each choice of $k$), and $\mathcal{L}_{\text{prf-real}}$ chooses one of these functions randomly. In both cases, the libraries give the calling program input/output access to the function that was chosen. You can think of this in terms of the picture from Section 5.1, but instead of strings, the objects are functions.

Note that even in the case of a “random function” ($\mathcal{L}_{\text{prf-rand}}$), the function $T$ itself is still **deterministic**! To be precise, this library chooses a deterministic function, uniformly, from the set of all possible deterministic functions. But once it makes this choice, the input/output behavior of $T$ is fixed. If the calling program calls lookup twice with the same $x$, it receives the same result. The same is true in $\mathcal{L}_{\text{prf-real}}$, since $F$ is a deterministic function and $k$ is fixed throughout the entire execution. To avoid this very natural confusion, it is perhaps better to think in terms of “randomly initialized lookup tables” rather than “random functions.”

# How NOT to Build a PRF

We can appreciate the challenges involved in building a PRF by looking at a natural approach that doesn’t quite work.

**Example** Suppose we have a length-doubling PRG $G : \{0, 1\}^\lambda \to \{0, 1\}^{2\lambda}$ and try to use it to construct a PRF $F$ as follows:

```
F(k, x):
return G(k) ⊕ x
```

You might notice that all we have done is rename the encryption algorithm of “pseudo-OTP” (Construction 5.2). We have previously argued that this algorithm is a secure method for one-time encryption, and that the resulting ciphertexts are pseudorandom. Is this enough for a secure PRF? No, we can attack the security of this PRF.