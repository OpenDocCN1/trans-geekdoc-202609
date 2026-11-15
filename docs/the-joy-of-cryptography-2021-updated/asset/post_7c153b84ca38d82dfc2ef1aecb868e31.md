
Example Using `LEARNPREVBYTE` to learn the 4th-to-last byte when the last 3 bytes of the block are already known.

```
... ?? a0 42 3c   m = partially unknown plaintext block
⊕ ... 00 00 00 04   p = string ending in 04
⊕ ... 00 a0 42 3c   s = known bytes of m
⊕ ... b 00 00 00   y = candidate byte b shifted into place
= ... 00 00 00 04   valid padding <=> ?? = b
```

Since we know the last 3 bytes of $m$, we can calculate a string $x$ such that $m \oplus x$ ends in `00 00 04`. Now we can try xor'ing the 4th-to-last byte of $m \oplus x$ with different candidate bytes $b$, and asking the padding oracle whether the result has valid padding. Valid padding only occurs when the result has `00` in its 4th-to-last byte, and this happens exactly when the 4th-to-last byte of $m$ exactly matches our candidate byte $b$.

The process is summarized in the `LEARNPREVBYTE` subroutine in Figure 9.1. In the worst case, this subroutine makes 256 queries to the padding oracle.

**Putting it all together.** We now have all the tools required to decrypt *any ciphertext* using only the padding oracle. The process is summarized below in the `LEARNALL` subroutine.

In the worst case, 256 queries to the padding oracle are required to learn each byte of the plaintext. However, in practice the number can be much lower. The example in this section was inspired by a real-life padding oracle attack which includes optimizations that allow an attacker to recover each plaintext byte with only 14 oracle queries on average.

## 9.2 What Went Wrong?

CBC encryption provides CPA security, so why didn’t it save us from padding oracle attacks? How was an attacker able to completely obliterate the privacy of encryption?

- 1. First, CBC encryption (in fact, every encryption scheme we’ve seen so far) has a property called **malleability**. Given an encryption $c$ of an *unknown* plaintext $m$, it is possible to generate another ciphertext $c'$ whose contents are *related* to $m$ in a *predictable way*. In the case of CBC encryption, if ciphertext $c_0 || \cdots || c_\ell$ encrypts a plaintext $m_1 || \cdots || m_\ell$, then ciphertext $(c_{i-1} \oplus x, c_i)$ encrypts the *related* plaintext $m_i \oplus x$.

In short, if an encryption scheme is malleable, then it allows information contained in one ciphertext to be “transferred” to another ciphertext.

2 It might take more than 256 queries to learn the last byte. But whenever `LEARNLASTBYTE` uses more than 256 queries, the side effect is that you’ve also learned that some other bytes of the block are zero. This saves you from querying the padding oracle altogether to learn those bytes.
3 *How to Break XML Encryption*, Tibor Jager and Juraj Somorovsky. ACM CCS 2011.

```
CHECKXOR(c, i, x):
  // if c encrypts (unknown)
  // plaintext m1 ... ml; then
  // does m_i xor x (by itself)
  // have valid padding?
  return PADDINGORACLE(c_{i-1} xor x, c_i)

LEARNLASTBYTE(c, i):
  // deduce the last byte of
  // plaintext block m_i
  B := \emptyset
  for b = 00 to ff:
    if CHECKXOR(c, i, b):
      B := B union {b}
  if |B| = 1:
    b := only element of B
    return b xor 01
  else:
    for each b in B:
      if CHECKXOR(c, i, 01 b):
        return b xor 01

LEARNPREVBYTE(c, i, s):
  // knowing that m_i ends in s,
  // find rightmost unknown
  // byte of m_i
  p := |s| + 1
  for b = 00 to ff:
    y := b 00 ... 00
           |___|  (underbrace |s|)
    if CHECKXOR(c, i, p xor s xor y):
      return b

LEARNBLOCK(c, i):
  // learn entire plaintext block m_i
  s := LEARNLASTBYTE(c, i)
  do 15 times:
    b := LEARNPREVBYTE(c, i, s)
    s := b || s
  return s

LEARNALL(c):
  // learn entire plaintext m1 ... ml
  m := epsilon
  l := number of non-IV blocks in c
  for i = 1 to l:
    m := m || LEARNBLOCK(c, i)
  return m
```

### Figure 9.1: Summary of padding oracle attack.

- 2. Second, you may have noticed that the CPA security definition makes no mention of the Dec algorithm. The Dec algorithm shows up in our definition for correctness, but it is nowhere to be found in the L_cpa-* libraries. Decryption has no impact on CPA security!

But the padding oracle setting involved the Dec algorithm — in particular, the adversary was allowed to see some information about the result of Dec applied to adversarially-chosen ciphertexts. Because of that, the CPA security definition does not capture the padding oracle attack scenario.

The bottom line is: give an attacker a malleable encryption scheme and access to any partial information related to decryption, and he/she can get information to leak out in surprising ways. As the padding-oracle attack demonstrates, even if only a single bit of information (i.e., the answer to a yes/no question about a plaintext) is leaked about the result of decryption, this is frequently enough to extract the entire plaintext.

If we want security even under the padding-oracle scenario, we need a better security definition and encryption schemes that achieve it. That’s what the rest of this chapter is about.

## Discussion

- Is this a realistic concern? You may wonder whether this whole situation is somewhat contrived just to give cryptographers harder problems to solve. That was probably a common attitude towards the security definitions introduced in this chapter. However, in 1998, Daniel Bleichenbacher demonstrated a devastating attack against early versions of the SSL protocol. By presenting millions of carefully crafted ciphertexts to a webserver, an attacker could eventually recover arbitrary SSL session keys.

In practice, it is hard to make the external behavior of a server *not* depend on the result of decryption. This makes CPA security rather fragile in the real world. In the case of padding oracle attacks, mistakes in implementation can lead to different error messages for invalid padding. In other cases, even an otherwise careful implementation can provide a padding oracle through a timing side-channel (if the server’s response time is different for valid/invalid padded plaintexts).

As we will see, it *is* in fact possible to provide security in these kinds of settings, and with low additional overhead. These days there is rarely a good excuse for using encryption which is only CPA-secure.

- Padding is in the name of the attack. But padding is not the culprit. The culprit is using a (merely) CPA-secure encryption scheme while allowing some information to leak about the result of decryption. The exercises expand on this idea further.

- If padding is added to only the *last block* of the plaintext, how can this attack recover the *entire* plaintext? This common confusion is another reason to not place so much blame on the padding scheme. A padding oracle has the following behavior: “give me an encryption of $m_1 || \cdots || m_\ell$ and I’ll tell you some information about $m_\ell$ (whether it ends with a certain suffix).” Indeed, the padding oracle checks only the last block. However, CBC mode has the property that if you have an encryption of $m_1 || \cdots || m_\ell$, then you can easily construct a different ciphertext that encrypts $m_1 || \cdots || m_{\ell-1}$. If you send *this* ciphertext to the padding oracle, you will get information about $m_{\ell-1}$. By modifying the ciphertext (via the malleability of CBC), you give different plaintext blocks the chance to be the “last block” that the padding oracle looks at.

- The attack seems superficially like brute force, but it is not: The attack makes 256 queries per byte of plaintext, so it costs about $256\ell$ queries for a plaintext of $\ell$ bytes. Brute-forcing the entire plaintext would cost $256^\ell$ since that’s how many $\ell$-byte plaintexts there are. So the attack is exponentially better than brute force. The lesson is: brute-forcing small pieces at a time is much better then brute-forcing the entire thing.

## 9.3 Defining CCA Security

Our goal now is to develop a new security definition — one that considers an adversary that can construct malicious ciphertexts and observe the effects caused by their decryption. We will start with the basic approach of CPA security, with left and right libraries that differ only in which of two plaintexts they encrypt.

In a typical system, an adversary might be able to learn only some specific *partial information* about the Dec process. In the padding oracle attack, the adversary was able to learn only whether the result of decryption had valid padding.

However, we are trying to come up with a security definition that is useful *no matter* how the encryption scheme is deployed. How can we possibly anticipate every kind of partial information that might make its way to the adversary in every possible usage of the encryption scheme? The safest choice is to be as pessimistic as possible, as long as we end up with a security notion that we can actually achieve in the end. So **let’s just allow the adversary to totally decrypt arbitrary ciphertexts of its choice.** In other words, if we can guarantee security when the adversary has *full information* about decrypted ciphertexts, then we certainly have security when the adversary learns only *partial information* about decrypted ciphertexts (as in a typical real-world system).

But this presents a significant problem. An adversary can do \(c^* := \text{EAVESDROP}(m_L, m_R)\) to challenge ciphertext, and then immediately ask for that ciphertext \(c^*\) to be decrypted. This will obviously reveal to the adversary whether it is linked to the left or right library.

So, simply providing unrestricted Dec access to the adversary cannot lead to a reasonable security definition (it is a security definition that can never be satisfied). The simplest way to patch this obvious problem with the definition is to allow the adversary to ask for the decryption of **any ciphertext, except those produced in response to EAVESDROP queries**. In doing so, we arrive at the final security definition: security against chosen-ciphertext attacks, or CCA-security:

### Definition 9.1 (CCA security)

Let \(\Sigma\) be an encryption scheme. We say that \(\Sigma\) has **security against chosen-ciphertext attacks (CCA security)** if \(\mathcal{L}^{\Sigma}_{\text{cca-L}} \approx \mathcal{L}^{\Sigma}_{\text{cca-R}}\), where:

| \(\mathcal{L}^{\Sigma}_{\text{cca-L}}\) | \(\mathcal{L}^{\Sigma}_{\text{cca-R}}\) |
|---|---|
| \(k \leftarrow \Sigma.\text{KeyGen}\) | \(k \leftarrow \Sigma.\text{KeyGen}\) |
| \(\mathcal{S} := \emptyset\) | \(\mathcal{S} := \emptyset\) |
| \(\text{EAVESDROP}(m_L, m_R \in \Sigma.\mathcal{M})\): | \(\text{EAVESDROP}(m_L, m_R \in \Sigma.\mathcal{M})\): |
| if \|m_L\| \neq \|m_R\| return err | if \|m_L\| \neq \|m_R\| return err |
| \(c := \Sigma.\text{Enc}(k, m_L)\) | \(c := \Sigma.\text{Enc}(k, m_R)\) |
| \(\mathcal{S} := \mathcal{S} \cup \{c\}\) | \(\mathcal{S} := \mathcal{S} \cup \{c\}\) |
| return \(c\) | return \(c\) |
| \(\text{DECRYPT}(c \in \Sigma.\mathcal{C})\): | \(\text{DECRYPT}(c \in \Sigma.\mathcal{C})\): |
| if \(c \in \mathcal{S}\) return err | if \(c \in \mathcal{S}\) return err |
| return \(\Sigma.\text{Dec}(k, c)\) | return \(\Sigma.\text{Dec}(k, c)\) |
