

And here is one possible calling program:

```
A:
m ← {0, 1}^λ
c := CTXT(m)
return m = c ?
```

You can hopefully convince yourself that

Pr[A ∘ L ⇒ true] = 1/2^λ.

If this A is linked to a different library, its output probability may be different. If a different calling program is linked to this L, the output probability may be different.

**Example** A library can contain several subroutines and private variables that are kept static between subroutine calls. For example, here is a simple library that picks a string s uniformly and allows the calling program to guess s.

```
L
s ← {0, 1}^λ
RESET():
s ← {0, 1}^λ
GUESS(x ∈ {0, 1}^λ):
return x = s
```

Our convention is that code outside of a subroutine (like the first line here) is run once at initialization time. Variables defined at initialization time (like s here) are available in all subroutine scopes (but not to the calling program).

## Interchangeability

The idea that “no calling program behaves differently in the presence of these two libraries” still makes sense even for libraries with several subroutines. Since this is such a common concept, we devote new notation to it:

### Definition 2.4
**(Interchangeable)** Let L_left and L_right be two libraries that have the same interface. We say that L_left and L_right are **interchangeable**, and write L_left ≡ L_right , if for all programs A that output a boolean value,

Pr[A ∘ L_left ⇒ true] = Pr[A ∘ L_right ⇒ true].

This definition considers calling programs that give boolean output. Imagine a calling program / attacker whose only goal is to distinguish two particular libraries (indeed, we often refer to the calling program as a **distinguisher**). A boolean output is enough for that task. You can think of the output bit as the calling program’s “guess” for which library the calling program thinks it is linked to.

The distinction between “calling program outputs true” and “calling program outputs false” is not significant. If two libraries don't affect the calling program's probability of outputting true, then they also don't affect its probability of outputting false:

```
Pr[A ∘ L_left ⇒ true] = Pr[A ∘ L_right ⇒ true]
<=> 1 - Pr[A ∘ L_left ⇒ true] = 1 - Pr[A ∘ L_right ⇒ true]
<=> Pr[A ∘ L_left ⇒ false] = Pr[A ∘ L_right ⇒ false].
```

## Example

Here are some very simple and straightforward ways that two libraries may be interchangeable. Hopefully it's clear that each pair of libraries has identical behavior, and therefore identical effect on all calling programs.

Despite being very simple examples, each of these concepts shows up as a **building block** in a real security proof in this book.

```
FOO(x):
  if x is even:
    return 0
  else if x is odd:
    return 1
  else:
    return -1
```

```
FOO(x):
  if x is even:
    return 0
  else if x is odd:
    return 1
  else:
    return ∞
```

Their only difference happens in an unreachable block of code.

```
FOO(x):
  return BAR(x, x)
BAR(a, b):
  k <- {0, 1}^λ
  return k ⊕ a
```

```
FOO(x):
  return BAR(x, 0^λ)
BAR(a, b):
  k <- {0, 1}^λ
  return k ⊕ a
```

Their only difference is the value they assign to a variable that is never actually used.

```
FOO(x, n):
  for i = 1 to λ:
    BAR(x, i)
```

```
FOO(x, n):
  for i = 1 to n:
    BAR(x, i)
  for i = n + 1 to λ:
    BAR(x, i)
```

Their only difference is that one library unrolls a loop that occurs in the other library.

```
FOO(x):
  k <- {0, 1}^λ
  y <- {0, 1}^λ
  return k ⊕ y ⊕ x
```

```
FOO(x):
  k <- {0, 1}^λ
  return k ⊕ BAR(x)
BAR(x):
  y <- {0, 1}^λ
  return y ⊕ x
```

Their only difference is that one library inlines a subroutine call that occurs in the other library.

## Example

Here are more simple examples of interchangeable libraries that involve randomness:

```
FOO():
  x <- {0, 1}^\lambda
  y <- {0, 1}^\lambda
  return x || y

=

FOO():
  z <- {0, 1}^{2\lambda}
  return z
```

The uniform distribution over strings acts independently on different characters in the string ("||" refers to concatenation).

```
k <- {0, 1}^\lambda

FOO(x):
  return k \oplus x

=

FOO(x):
  if k not defined:
    k <- {0, 1}^\lambda
  return k \oplus x
```

Sampling a value “eagerly” (as soon as possible) vs. sampling a value “lazily” (at the last possible moment before the value is needed). We assume that k is static/global across many calls to FOO, and initially undefined.

## Formal Restatements of Previous Concepts

We can now re-state our security definitions from the previous section, using this new terminology.

Our “real-vs-random” style of security definition for encryption can be expressed as follows:

### Definition 2.5 (Uniform ctxts)

An encryption scheme $\Sigma$ has **one-time uniform ciphertexts** if:

| L_ots$-real^\Sigma | L_ots$-rand^\Sigma |
|---|---|
| CTXT(m \in \Sigma.M): | CTXT(m \in \Sigma.M): |
| k <- $.KeyGen | c <- $.C |
| c <- $.Enc(k, m) | return c |
| return c | |

(Visual representation of two interchangeable libraries)

In other words, if you fill in the specifics of $\Sigma$ (i.e., the behavior of its KeyGen and Enc) into these two library “templates,” and you get two libraries that are interchangeable (i.e., have the same effect on all calling programs), we will say that $\Sigma$ has one-time uniform ciphertexts.

Throughout this course, we will use the “$” symbol to denote randomness (as in real-vs-random).3

Our “left-vs-right” style of security definition can be expressed as follows:

### Definition 2.6 (One-time secrecy)

An encryption scheme $\Sigma$ has **one-time secrecy** if:

| L_ots-L^\Sigma | L_ots-R^\Sigma |
|---|---|
| EAVESDROP(mL, mR \in \Sigma.M): | EAVESDROP(mL, mR \in \Sigma.M): |
| k <- $.KeyGen | k <- $.KeyGen |
| c <- $.Enc(k, mL) | c <- $.Enc(k, mR) |
| return c | return c |

3 It is quite common in CS literature to use the “$” symbol when referring to randomness. This stems from thinking of randomized algorithms as algorithms that “toss coins.” Hence, randomized algorithms need to have spare change (i.e., money) sitting around. By convention, randomness comes in US dollars.

Previously in Claim 1.3 we argued that one-time-pad ciphertexts follow the uniform distribution. This actually shows that OTP satisfies the uniform ciphertexts definition:

### Claim 2.7 (OTP rule)

One-time pad satisfies the one-time uniform ciphertexts property. In other words:

```
L_otp-real
EAVESDROP(m ∈ {0, 1}^λ):
k ← {0, 1}^λ // OTP.KeyGen
return k ⊕ m // OTP.Enc(k, m)

=

L_otp-rand
EAVESDROP(m ∈ {0, 1}^λ):
c ← {0, 1}^λ // OTP.C
return c
```

Because this property of OTP is quite useful throughout the course, I’ve given these two libraries special names (apart from $\mathcal{L}_{\text{ots\$-real}}^{\text{OTP}}$ and $\mathcal{L}_{\text{ots\$-rand}}^{\text{OTP}}$).

## Discussion, Pitfalls

It is a common pitfall to imagine the calling program $\mathcal{A}$ being *simultaneously* linked to both libraries, but this is not what the definition says. The definition of $\mathcal{L}_1 \equiv \mathcal{L}_2$ refers to two different executions: one where $\mathcal{A}$ is linked only to $\mathcal{L}_1$ for its entire lifetime, and one where $\mathcal{A}$ is linked only to $\mathcal{L}_2$ for its entire lifetime. There is never a time where some of $\mathcal{A}$’s subroutine calls are answered by $\mathcal{L}_1$ and others by $\mathcal{L}_2$. This is an especially important distinction when $\mathcal{A}$ makes several subroutine calls in a single execution.

Another common pitfall is confusion about the difference between the algorithms of an encryption scheme (e.g., what is shown in Construction 1.1) and the libraries used in a security definition (e.g., what is shown in Definition 2.6). The big difference is:

- ▶ The algorithms of the scheme show a regular user’s view of things. For example, the Enc algorithm takes two inputs: a key and a plaintext. Is there any way of describing an algorithm that takes two arguments other than writing something like Construction 1.1?

- ▶ The libraries capture the attacker’s view of of a particular scenario, where the users *use the cryptographic algorithms in a very specific way*. For example, when we talk about security of encryption, we don’t guarantee security when Alice lets the attacker choose her encryption key! But letting the attacker choose the plaintext is fine; we can guarantee security in that scenario. That’s why Definition 2.5 describes a subroutine that calls Enc on a plaintext that is chosen by the calling program, but on a key $k$ chosen by the library.

A security definition says that some task (e.g., distinguishing ciphertexts from random junk) is impossible, when the attacker is allowed certain influence over the inputs to the algorithms (e.g., full choice of plaintexts, but no influence over the key), and is allowed to see certain outputs from those algorithms (e.g., ciphertexts).

It’s **wrong** to summarize one-time secrecy as: “I’m not allowed to choose what to encrypt, I have to ask the attacker to choose for me.” The correct interpretation is: “If I encrypt only one plaintext per key, then I am safe to encrypt things even if the attacker sees the resulting ciphertext and even if she has some influence or partial information on what I’m encrypting, because this is the situation captured in the one-time secrecy library.”

