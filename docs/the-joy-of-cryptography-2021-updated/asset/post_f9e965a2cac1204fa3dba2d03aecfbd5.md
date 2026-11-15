
the calling program. As we progress in the course, we will see more kinds of useful modifications.

## A Contrasting Example

Usually the boundary between secure and insecure is razor thin. Let’s make a small change to the previous encryption scheme to illustrate this point. Instead of applying OTP to the plaintext twice, with independent keys, what would happen if we use the same key?

| Construction 2.14 ("Double OTP") | \(\mathcal{K} = \{0, 1\}^\lambda\) | KeyGen: | Enc(\(k, m\)): | Dec(\(k, c_2\)): |
|---|---|---|---|---|
| | \(\mathcal{M} = \{0, 1\}^\lambda\) | \(k \leftarrow \{0, 1\}^\lambda\) | \(c_1 := k \oplus m\) | \(c_1 := k \oplus c_2\) |
| | \(\mathcal{C} = \{0, 1\}^\lambda\) | return \(k\) | \(c_2 := k \oplus c_1\) | \(m := k \oplus c_1\) |
| | | | return \(c_2\) | return \(m\) |

You probably noticed that the ciphertext \(c_2\) is computed as \(c_2 := k \oplus (k \oplus m)\), which is just a fancy way of saying \(c_2 := m\). There is certainly no way this kind of “double-OTP” is secure.

For educational purposes, let’s try to repeat the steps of our previous security proof on this (insecure) scheme and see where things break down. If we wanted to show that Construction 2.14 has uniform ciphertexts, we would have to show that the following two libraries are interchangeable:

![](img/da79fa21b263fe549aecaabd2a0a41c8_47_0.png)

In the previous hybrid proof, the first step was to factor out the statements “\(k_2 \leftarrow \{0, 1\}^\lambda\); \(c_2 := k_2 \oplus c_1\)” into a separate subroutine, so we could argue that the result of \(c_2\) was uniformly distributed. If we do something analogous with this example, we get:

![](img/da79fa21b263fe549aecaabd2a0a41c8_47_1.png)

Do you see the problem? In “\(\mathcal{L}_{\text{hyb}}\)”, we have tried to move the variable \(k\) into \(\mathcal{L}_{\text{otp-real}}\). Since this scope is private, every operation we want to do with \(k\) has to be provided by its container library \(\mathcal{L}_{\text{otp-real}}\). But there is a mismatch: \(\mathcal{L}_{\text{otp-real}}\) only gives us a way to use \(k\) in one xor expression, whereas we need to use the same \(k\) in two xor expressions to match the behavior of $\mathcal{L}_{\text{ots\$-real}}$. The compound library $\mathcal{L}_{\text{hyb}}$ has an unresolved reference to $k$ in the line “$c_1 := k \oplus m$,” and therefore doesn’t have the same behavior as $\mathcal{L}_{\text{ots\$-real}}$. This is the step of the security proof that breaks down.

4 I would say that the library “doesn’t compile” due to a scope/reference error.

Here’s a more conceptual way to understand what went wrong here. The important property of OTP is that its ciphertexts look uniform *when the key is used to encrypt only one plaintext*. This “double OTP” variant uses OTP in a way that doesn’t fulfill that condition, and therefore provides no security guarantee. The previous (successful) proof was able to factor out some xor’s in terms of $\mathcal{L}_{\text{otp-real}}$ without breaking anything, and that’s how we know the scheme was using OTP in a way that is consistent with its security guarantee.

As you can hopefully see, the process of a security proof provides a way to catch these kinds of problems. It is very common in a hybrid proof to factor out some statements in terms of a library from some other security definition. This step can only be done successfully if the underlying cryptography is being used in an appropriate way.

## 2.5 How to Compare/Contrast Security Definitions

In math, a definition can’t really be “wrong,” but it can be “not as useful as you hoped” or it can “fail to adequately capture your intuition” about the concept.

Security definitions are no different. In this chapter we introduced two security definitions: one in the “real-vs-random” style and one in the “left-vs-right” style. In this section we treat the *security definitions themselves* as objects worth studying. Are both of these security definitions “the same,” in some sense? Do they both capture all of our intuitions about security?

### One Security Definition Implies Another

One way to compare/contrast two security definitions is to prove that one implies the other. In other words, if an encryption scheme satisfies definition #1, then it also satisfies definition #2.

**Theorem 2.15** If an encryption scheme $\Sigma$ has one-time uniform ciphertexts (Definition 2.5), then $\Sigma$ also has one-time secrecy (Definition 2.6). In other words:

$$\mathcal{L}^{\Sigma}_{\text{ots\$-real}} \equiv \mathcal{L}^{\Sigma}_{\text{ots\$-rand}} \implies \mathcal{L}^{\Sigma}_{\text{ots-L}} \equiv \mathcal{L}^{\Sigma}_{\text{ots-R}}.$$

If you are comfortable with what all the terminology means, then the meaning of this statement is quite simple and unsurprising. “If all plaintexts $m$ induce a *uniform* distribution of ciphertexts, then all $m$ induce the *same* distribution of ciphertexts.”

This fairly straight-forward statement can be proven formally, giving us another example of the hybrid proof technique:

**Proof** We are proving an if-then statement. We want to show that the “then”-part of the statement is true; that is, $\mathcal{L}^{\Sigma}_{\text{ots-L}} \equiv \mathcal{L}^{\Sigma}_{\text{ots-R}}$. We are allowed to use the fact that the “if”-part is true; that is, $\mathcal{L}^{\Sigma}_{\text{ots\$-real}} \equiv \mathcal{L}^{\Sigma}_{\text{ots\$-rand}}$.

The proof uses the hybrid technique. We will start with the library $\mathcal{L}_{\text{ots-L}}$, and make a small sequence of justifiable changes to it, until finally reaching $\mathcal{L}_{\text{ots-R}}$. Along the way, we can use the fact that $\mathcal{L}_{\text{ots\$-real}} \equiv \mathcal{L}_{\text{ots\$-rand}}$. This suggests some “strategy” for the proof: if we can somehow get $\mathcal{L}_{\text{ots\$-real}}$ to appear as a component in one of the hybrid libraries, then we can replace it with $\mathcal{L}_{\text{ots\$-rand}}$ (or vice-versa), in a way that hopefully makes progress towards our goal of transforming $\mathcal{L}_{\text{ots-L}}$ to $\mathcal{L}_{\text{ots-R}}$.

Below we list the sequence of hybrid libraries, and justify why each one is interchangeable with the previous library.

```
$\mathcal{L}^\Sigma_{\text{ots-L}}$
EAVESDROP($m_L, m_R$):
  \( k \leftarrow \Sigma.\text{KeyGen} \)
  \( c \leftarrow \Sigma.\text{Enc}(k, m_L) \)
  return c
```

The starting point of our hybrid sequence is $\mathcal{L}^\Sigma_{\text{ots-L}}$.

```
$\mathcal{L}^\Sigma_{\text{ots\$-real}}$
CTXT(m):
  \( k \leftarrow \Sigma.\text{KeyGen} \)
  \( c \leftarrow \Sigma.\text{Enc}(k, m) \)
  return c
```

Factoring out a block of statements into a subroutine makes it possible to write the library as a _compound_ one, but does not affect its external behavior. Note that the new subroutine is exactly the $\mathcal{L}^\Sigma_{\text{ots\$-real}}$ library from Definition 2.5. This was a strategic choice, because of what happens next.

```
$\mathcal{L}^\Sigma_{\text{ots\$-rand}}$
CTXT(m):
  \( c \leftarrow \Sigma.\mathcal{C} \)
  return c
```

$\mathcal{L}^\Sigma_{\text{ots\$-real}}$ has been replaced with $\mathcal{L}^\Sigma_{\text{ots\$-rand}}$. The chaining lemma Lemma 2.11 says that this change has no effect on the library’s behavior, since the two $\mathcal{L}_{\text{ots-}\star}$ libraries are interchangeable.

```
$\mathcal{L}^\Sigma_{\text{ots\$-rand}}$
CTXT(m):
  \( c \leftarrow \Sigma.\mathcal{C} \)
  return c
```

The argument to CTXT has been changed from \( m_L \) to \( m_R \). This has no effect on the library’s behavior since CTXT does not actually use its argument in these hybrids!

The previous transition is the most important one in the proof, as it gives insight into how we came up with this particular sequence of hybrids. Looking at the desired endpoints of our sequence of hybrids – $\mathcal{L}^\Sigma_{\text{ots-L}}$ and $\mathcal{L}^\Sigma_{\text{ots-R}}$ – we see that they differ only in swapping \( m_L \) for \( m_R \). If we are not comfortable eyeballing things, we’d like a better justification for why it is “safe” to exchange \( m_L \) for \( m_R \) (i.e. why it has no effect on the calling program). However, the uniform ciphertexts property shows that $\mathcal{L}^\Sigma_{\text{ots-L}}$ in fact has the same behavior as a library $\mathcal{L}_{\text{hyb-2}}$ that doesn’t use either of \( m_L \) or \( m_R \). In a program that doesn’t use \( m_L \) or \( m_R \), it is clear that we can switch them!
