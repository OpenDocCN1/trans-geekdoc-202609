When we link \(\mathcal{L}^* \diamond \mathcal{L}_{\text{samp-L}}\) we obtain \(\mathcal{L}_{\text{prf-rand}}\) since the values in \(T[x]\) are sampled uniformly. When we link \(\mathcal{L}^* \diamond \mathcal{L}_{\text{samp-R}}\) we obtain \(\mathcal{L}_{\text{prp-rand}}\) since the values in \(T[x]\) are sampled uniformly subject to having no repeats (consider \(R\) playing the role of \(T\).values in \(\mathcal{L}_{\text{prp-rand}}\)). Then from Lemma 4.11, we have:

```
\(\mathcal{L}_{\text{prf-rand}} \equiv \mathcal{L}^* \diamond \mathcal{L}_{\text{samp-L}} \approx \mathcal{L}^* \diamond \mathcal{L}_{\text{samp-R}} \equiv \mathcal{L}_{\text{prp-rand}},\)
```

which completes the proof.

Using the switching lemma, we can conclude that every PRP (with \(blen = \lambda\)) is also a PRF:

# **Corollary 6.8** _Let_ \(F : \{0, 1\}^\lambda \times \{0, 1\}^\lambda \rightarrow \{0, 1\}^\lambda\) _be a secure PRP (with_ \(blen = \lambda\)_). Then_ \(F\) _is also a secure PRF._

# **Proof**

As we have observed above, \(\mathcal{L}^F_{\text{prf-real}}\) and \(\mathcal{L}^F_{\text{prp-real}}\) are literally the same library. Since \(F\) is a secure PRP, \(\mathcal{L}^F_{\text{prp-real}} \approx \mathcal{L}^F_{\text{prp-rand}}\). Finally, by the switching lemma, \(\mathcal{L}^F_{\text{prp-rand}} \approx \mathcal{L}^F_{\text{prf-rand}}\). Putting everything together:

```
\(\mathcal{L}^F_{\text{prf-real}} \equiv \mathcal{L}^F_{\text{prp-real}} \approx \mathcal{L}^F_{\text{prp-rand}} \approx \mathcal{L}^F_{\text{prf-rand}},\)
```

hence \(F\) is a secure PRF.

Keep in mind that the switching lemma applies only when the blocklength is sufficiently large (at least \(\lambda\) bits long). This comes from the fact that \(\mathcal{L}_{\text{samp-L}}\) and \(\mathcal{L}_{\text{samp-R}}\) in the proof are indistinguishable only when sampling with long (length-\(\lambda\)) strings (look at the proof of Lemma 4.11 to recall why). Exercise 6.14 asks you to show that a random permutation over a _small domain_ can be distinguished from a random (unconstrained) function; so, a PRP with a small blocklength is **not** a PRF.

# **Constructing a PRP from a PRF: The Feistel Construction**

How can you build an _invertible_ block cipher out of a PRF that is not necessarily invertible? In this section, we show a simple technique called the **Feistel construction** (named after IBM cryptographer Horst Feistel).

The main idea in the Feistel construction is to convert a not-necessarily-invertible function \(F : \{0, 1\}^n \rightarrow \{0, 1\}^n\) into an invertible function \(F^* : \{0, 1\}^{2n} \rightarrow \{0, 1\}^{2n}\). The function \(F^*\) is called the **Feistel round with round function** \(F\) and is defined as follows:

+   **Construction 6.9 (Feistel round)**
+   
+   \(F^*(x||y)\):
+   // each of \(x, y\) are \(n\) bits
+   return \(y || (F(y) \oplus x)\)
+   
+   ![Feistel round diagram]

No matter what \(F\) is, its Feistel round \(F^*\) is invertible. Not only that, but its inverse is a kind of “mirror image” of \(F^*\):