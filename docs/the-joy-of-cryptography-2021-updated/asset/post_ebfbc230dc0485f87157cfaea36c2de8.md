
```
$\mathcal{L}_{\text{hyb-4}}$:
EAVESDROP($m_L, m_R$):
$z \leftarrow \{0, 1\}^{\lambda + \ell}$
$c := z \oplus m_R$
return $c$
```

The (perfect) one-time secrecy of rOTP allows us to replace $\mathcal{L}^{\text{OTP}}_{\text{ots-L}}$ with $\mathcal{L}^{\text{OTP}}_{\text{ots-R}}$; they are interchangeable.

The rest of the proof is essentially a “mirror image” of the previous steps, in which we perform the same steps but in reverse (and with \(m_R\) being used instead of \(m_L\)).

```
EAVESDROP($m_L, m_R$):
$z \leftarrow$ QUERY()
$c := z \oplus m_R$
return $c$
```

```
$\mathcal{L}^G_{\text{prg-rand}}$
QUERY():
$r \leftarrow \{0, 1\}^{\lambda + \ell}$
return $r$
```

A statement has been factored out into a subroutine, which happens to exactly match $\mathcal{L}^G_{\text{prg-rand}}$.

```
EAVESDROP($m_L, m_R$):
$z \leftarrow$ QUERY()
$c := z \oplus m_R$
return $c$
```

```
$\mathcal{L}^G_{\text{prg-real}}$
QUERY():
$s \leftarrow \{0, 1\}^\lambda$
return $G(s)$
```

From the PRG security of $G$, we can replace $\mathcal{L}^G_{\text{prg-rand}}$ with $\mathcal{L}^G_{\text{prg-real}}$. The resulting library is indistinguishable from the previous one.

```
$\mathcal{L}^{\text{pOTP}}_{\text{ots-R}}$
EAVESDROP($m_L, m_R$):
\(k \leftarrow \{0, 1\}^\lambda\)
\(c := G(k) \oplus m_R\)
return \(c\)
```

A subroutine has been inlined. The result is $\mathcal{L}^{\text{pOTP}}_{\text{ots-R}}$.

Summarizing, we showed a sequence of hybrid libraries satisfying the following:

\(\mathcal{L}^{\text{pOTP}}_{\text{ots-L}} \equiv \mathcal{L}_{\text{hyb-1}} \approx \mathcal{L}_{\text{hyb-2}} \equiv \mathcal{L}_{\text{hyb-3}} \equiv \mathcal{L}_{\text{hyb-4}} \equiv \mathcal{L}_{\text{hyb-5}} \approx \mathcal{L}_{\text{hyb-6}} \equiv \mathcal{L}^{\text{pOTP}}_{\text{ots-R}}.\)

Hence, $\mathcal{L}^{\text{pOTP}}_{\text{ots-L}} \approx \mathcal{L}^{\text{pOTP}}_{\text{ots-R}}$, and pOTP has (computational) one-time secrecy.

## 5.4 Extending the Stretch of a PRG

The stretch of a PRG measures how much longer its output is than its input. Can we use a PRG with small stretch to construct a PRG with larger stretch? The answer is yes, but only if you do it the right way!

### Two Approaches to Increase Stretch

Suppose \(G : \{0, 1\}^\lambda \rightarrow \{0, 1\}^{2\lambda}\) is a length-doubling PRG (i.e., a PRG with stretch \(\lambda\)). Below are two ideas for constructing a PRG with longer stretch:

![](img/da79fa21b263fe549aecaabd2a0a41c8_103_0.png)

Although the constructions are similar, only one of them is secure. Before reading any further, can you guess which of \(H_1, H_2\) is a secure PRG and which is insecure? By carefully comparing these two approaches, I hope you develop a better understanding of the PRG security definition.

### A Security Proof

I think it’s helpful to illustrate the “strategy” of security proofs by starting from the desired conclusion and working backwards. What better way to do this than as a Socratic dialogue in the style of Galileo?²

SALVIATI: I’m sure that \(H_1\) is the secure PRG.

SIMPLICIO: If I understand the security definition for PRGs correctly, you mean that the output of \(H_1\) looks indistinguishable from uniform, when the input to \(H_1\) is uniform. Why do you say that?

SALVIATI: Simple! \(H_1\)’s output consists of segments called \(x\), \(u\), and \(v\). Each of these are outputs of \(G\), and since \(G\) itself is a PRG its outputs look uniform.

SIMPLICIO: I wish I had your boldness, Salviati. I myself am more cautious. If \(G\) is a secure PRG, then its outputs are indeed indistinguishable from uniform, but surely only when its input is uniform! Are you so sure that’s the case here?

SALVIATI: You raise a good point, Simplicio. In these endeavors it is always preferable to err on the side of caution. When we want to claim that \(H_1\) is a secure PRG, we consider the nature of its outputs when its seed \(s\) is uniform. Since \(H_1\) sends that seed \(s\) directly into \(G\), your concern is addressed.

SIMPLICIO: Yes, I can see how in the expression \(x||y := G(s)\) the input to \(G\) is uniform, and so its outputs \(x\) and \(y\) are indistinguishable from random. Since \(x\) is part of \(H_1\)’s output, we are making progress towards showing that the entire output of \(H_1\) is indistinguishable from random! However, the output of \(H_1\) also contains terms \(u\) and \(v\). When I examine how they are generated, as \(u||v := G(y)\), I become concerned again. Surely \(y\) is not uniform, so I see no way to apply the security of \(G\)!

SALVIATI: Oh, bless your heart. The answer could not be any more obvious! It is true that y is not uniformly distributed. But did you not just convince yourself that y is indistinguishable from uniform? Should that suffice?

SIMPLICIO: Incredible! I believe I understand now. Let me try to summarize: We suppose the input s to H1 is chosen uniformly, and examine what happens to H1's outputs. In the expression x||y := G(s), the input to G is uniform, and thus x and y are indistinguishable from uniform. Now, considering the expression u||v := G(y), the result is indistinguishable from a scenario in which y is truly uniform. But if y were truly uniform, those outputs u and v would be indistinguishable from uniform! Altogether, x, u, and v (the outputs of H1) are each indistinguishable from uniform!

I hope that was as fun for you as it was for me.³ The formal security proof and its sequence of hybrids will follow the outline given in Simplicio's summary. We start by applying the PRG security definition to the first call to G, and replace its outputs with truly uniform values. After this change, the input to the second call to G becomes uniform, allowing us to apply the PRG security definition again.

Claim 5.5 If G is a secure length-doubling PRG, then H1 (defined above) is a secure (length-tripling) PRG.

Proof One of the trickier aspects of this proof is that we are using a secure PRG G to prove the security of another PRG H1. That means both \(\mathcal{L}^{H_1}_{\text{prg-star}}\) and \(\mathcal{L}^G_{\text{prg-star}}\) will appear in this proof. Both libraries/interfaces have a subroutine named "QUERY", and we will rename these subroutines QUERY_{H1} and QUERY_{G} to disambiguate.

We want to show that \(\mathcal{L}^{H_1}_{\text{prg-real}} \approx \mathcal{L}^{H_1}_{\text{prg-rand}}\). As usual, we do so with a hybrid sequence.

Since we assume that G is a secure PRG, we are allowed to use the fact that \(\mathcal{L}^G_{\text{prg-real}} \approx \mathcal{L}^G_{\text{prg-rand}}\).

```
$\mathcal{L}^{H_1}_{\text{prg-real}}$
QUERY_{H1}():
  $s \leftarrow \{0, 1\}^\lambda$
  $x||y := G(s)$
  $u||v := G(y)$
  return $x||u||v$
```

The starting point is \(\mathcal{L}^{H_1}_{\text{prg-real}}\), shown here with the details of H1 filled in.

```
QUERY_{H1}():
  $x||y := QUERY_G()$
  $u||v := G(y)$
  return $x||u||v$

$\mathcal{L}^G_{\text{prg-real}}$
QUERY_G():
  $s \leftarrow \{0, 1\}^\lambda$
  return $G(s)$
```

The first invocation of G has been factored out into a subroutine. The resulting hybrid library includes an instance of \(\mathcal{L}^G_{\text{prg-real}}\).

³If you're wondering what the hell just happened: In Galileo's 1632 book Dialogue Concerning the Two Chief World Systems, he lays out the arguments for heliocentrism using a dialog between Salviati (who advocated the heliocentric model) and Simplicio (who believed the geocentric model).

From the PRG security of G, we can replace the instance of $\mathcal{L}^G_{\text{prg-real}}$ with $\mathcal{L}^G_{\text{prg-rand}}$. The resulting hybrid library is indistinguishable.

A subroutine has been inlined.

Choosing $2\lambda$ uniformly random bits and then splitting them into two halves has exactly the same effect as choosing $\lambda$ uniformly random bits and independently choosing $\lambda$ more.

The remaining appearance of G has been factored out into a subroutine. Now $\mathcal{L}^G_{\text{prg-real}}$ makes its second appearance.

Again, the PRG security of G lets us replace $\mathcal{L}^G_{\text{prg-real}}$ with $\mathcal{L}^G_{\text{prg-rand}}$. The resulting hybrid library is indistinguishable.

A subroutine has been inlined.

Similar to above, concatenating $\lambda$ uniform bits with $2\lambda$ independently uniform bits has the same effect as sampling $3\lambda$ uniform bits. The result of this change is $\mathcal{L}^{H_1}_{\text{prg-rand}}'$.
