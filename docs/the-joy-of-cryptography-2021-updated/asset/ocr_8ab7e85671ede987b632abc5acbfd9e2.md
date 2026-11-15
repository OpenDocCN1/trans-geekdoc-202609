Having made this crucial change, we can now perform the same sequence of steps, but in reverse.

```
EAVESDROP(m_L, m_R):
c := CTXT(m_R)
return c
```

```
L^\Sigma_{\text{ots\$-real}}
CTXT(m):
k \leftarrow \Sigma.\text{KeyGen}
c \leftarrow \Sigma.\text{Enc}(k, m)
return c
```

\mathcal{L}^\Sigma_{\text{ots\$-rand}} has been replaced with \mathcal{L}^\Sigma_{\text{ots\$-real}}. This is another application of the chaining lemma.

```
L^\Sigma_{\text{ots-R}}
EAVESDROP(m_L, m_R):
k \leftarrow \Sigma.\text{KeyGen}
c \leftarrow \Sigma.\text{Enc}(k, m_R)
return c
```

A subroutine call has been inlined, which has no effect on the library’s behavior. The result is exactly \mathcal{L}^\Sigma_{\text{ots-R}}.

Putting everything together, we showed that \mathcal{L}^\Sigma_{\text{ots-L}} \equiv \mathcal{L}_{\text{hyb-1}} \equiv \cdots \equiv \mathcal{L}_{\text{hyb-4}} \equiv \mathcal{L}^\Sigma_{\text{ots-R}}. This completes the proof, and we conclude that \Sigma satisfies the definition of one-time secrecy.

# One Security Definition Doesn’t Imply Another

Another way we might compare security definitions is to identify any schemes that satisfy one definition without satisfying the other. This helps us understand the boundaries and “edge cases” of the definition.

A word of warning: If we have two security definitions that both capture our intuitions rather well, then any scheme which satisfies one definition and not the other is bound to appear unnatural and contrived. The point is to gain more understanding of the security definitions themselves, and unnatural/contrived schemes are just a means to do that.

**Theorem 2.16** _There is an encryption scheme that satisfies one-time secrecy (Definition 2.6) but not one-time uniform ciphertexts (Definition 2.5). In other words, one-time secrecy **does not** necessarily imply one-time uniform ciphertexts._

**Proof** One such encryption scheme is given below:

| K = {0, 1}^\lambda | KeyGen: | Enc(k, m \in {0, 1}^\lambda): | Dec(k, c \in {0, 1}^{\lambda+2}): |
|---|---|---|---|
| M = {0, 1}^\lambda | k \leftarrow {0, 1}^\lambda | c' := k \oplus m | c' := first \lambda bits of c |
| C = {0, 1}^{\lambda+2} | return k | c := c' || 00 | return k \oplus c' |
| | | return c | |

This scheme is just OTP with the bits 00 added to every ciphertext. The following facts about the scheme should be believable (and the exercises encourage you to prove them formally if you would like more practice at that sort of thing):

+   \blacktriangleright This scheme satisfies one-time one-time secrecy, meaning that encryptions of m_L are distributed identically to encryptions of m_R, for any m_L and m_R of the attacker’s choice. We can characterize the ciphertext distribution in both cases as “\lambda uniform