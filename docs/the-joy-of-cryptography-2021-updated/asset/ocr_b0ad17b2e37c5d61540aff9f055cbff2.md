Let’s consider a 5-out-of-5 secret-sharing scheme. This means we want to split a secret into 5 pieces so that any 4 of the pieces leak nothing. One way you might think to do this is to *literally chop up the secret* into 5 pieces. For example, if the secret is 500 bits, you might give the first 100 bits to user 1, the second 100 bits to user 2, and so on.

**Construction 3.4**
**(Insecure TSSS)**

| | Share(m): | Reconstruct(s1, ..., s5): |
|---|---|---|
| $\mathcal{M} = \{0, 1\}^{500}$ | split $m$ into $m = s_1 || \cdots || s_5$, | return $s_1 || \cdots || s_5$ |
| $t = 5$ | where each $|s_i| = 100$ | |
| $n = 5$ | return $(s_1, \dots, s_5)$ | |

It is true that the secret can be constructed by concatenating all 5 shares, and so this construction satisfies the correctness property. (The only authorized set is the set of all 5 users, so we write Reconstruct to expect all 5 shares.)

However, the scheme is **insecure** (as promised). Suppose you have even just 1 share. It is true that you don't know the secret _in its entirety_, but the security definition (for 5-out-of-5 secret sharing) demands that a single share reveals _nothing_ about the secret. Of course knowing 100 bits of something is not the same as than knowing _nothing_ about it.

We can leverage this observation to make a more formal attack on the scheme, in the form of a distinguisher between the two $\mathcal{L}_{\text{tsss-}\star}$ libraries. As an extreme case, we can distinguish between shares of an all-0 secret and shares of an all-1 secret:

```
$\mathcal{A}$
$s_1 := \text{SHARE}(0^{500}, 1^{500}, \{1\})$
return $s_1 \stackrel{?}{=} 0^{100}$
```

Let’s link this calling program to both of the $\mathcal{L}_{\text{tsss-}\star}$ libraries and see what happens:

| $\mathcal{A}$ | $\mathcal{L}_{\text{tsss-L}}$ | When $\mathcal{A}$ is linked to $\mathcal{L}_{\text{tsss-L}}$, it receives a share of $0^{500}$, which will itself be a string of all zeroes. In this case, $\mathcal{A}$ outputs 1 with probability 1. |
|---|---|---|
| $s_1 := \text{SHARE}(0^{500}, 1^{500}, \{1\})$
return $s_1 \stackrel{?}{=} 0^{100}$ | $\text{SHARE}(m_L, m_R, U)$:
if $|U| \geqslant t$: return err
\(\boldsymbol{s} \leftarrow \text{Share}(\boldsymbol{m_L})\$)
return $\{s_i \mid i \in U\}$ |

| $\mathcal{A}$ | $\mathcal{L}_{\text{tsss-R}}$ | When $\mathcal{A}$ is linked to $\mathcal{L}_{\text{tsss-R}}$, it receives a share of $1^{500}$ which will be a string of all ones. In this case, $\mathcal{A}$ outputs 1 with probability 0. |
|---|---|---|
| $s_1 := \text{SHARE}(0^{500}, 1^{500}, \{1\})$
return $s_1 \stackrel{?}{=} 0^{100}$ | $\text{SHARE}(m_L, m_R, U)$:
if $|U| \geqslant t$: return err
\(\boldsymbol{s} \leftarrow \text{Share}(\boldsymbol{m_R})\$)
return $\{s_i \mid i \in U\}$ |

We have constructed a calling program which behaves very differently (indeed, as differently as possible) in the presence of the two libraries. Hence, this secret-sharing scheme is not secure.

Hopefully this example demonstrates one of the main challenges (and amazing things) about secret-sharing schemes. It is easy to reveal information about the secret gradually as