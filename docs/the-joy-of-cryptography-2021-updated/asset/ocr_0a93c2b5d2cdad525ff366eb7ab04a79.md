# # Malleability of CBC Encryption

Recall the definition of CBC decryption. If the ciphertext is \( c = c_0 \cdots c_\ell \) then the \( i \)th plaintext block is computed as:

\( m_i := F^{-1}(k, c_i) \oplus c_{i-1} \) .

From this we can deduce two important facts:

+   - Two consecutive blocks \( (c_{i-1}, c_i) \) taken in isolation are a valid encryption of \( m_i \). Looking ahead, this fact allows the attacker to focus on decrypting a single block at a time.

+   - xoring a ciphertext block with a known value (say, \( x \)) has the effect of xoring the corresponding plaintext block by the same value. In other words, for all \( x \), the ciphertext \( (c_{i-1} \oplus x, c_i) \) decrypts to \( m_i \oplus x \):

\(\text{Dec}(k, (c_{i-1} \oplus x, c_i)) = F^{-1}(k, c_i) \oplus (c_{i-1} \oplus x) = (F^{-1}(k, c_i) \oplus c_{i-1}) \oplus x = m_i \oplus x\) .

If we send such a ciphertext \( (c_{i-1} \oplus x, c_i) \) to the padding oracle, we would therefore learn whether \( m_i \oplus x \) is a (single block) with valid padding. Instead of thinking in terms of padding, it might be best to think of the oracle as telling you whether \( m_i \oplus x \) ends in one of the suffixes `01`, `00 02`, `00 00 03`, etc.

By carefully choosing different values \( x \) and asking questions of this form to the padding oracle, we will show how it is possible to learn *all* of \( m_i \). We summarize the capability so far with the following subroutine:

```
// suppose c encrypts an (unknown) plaintext \( m_1 \| \cdots \| m_\ell \)
// does \( m_i \oplus x \) end in one of the valid padding strings?
CHECKXOR(c, i, x):
    return PADDINGORACLE(\( c_{i-1} \oplus x, c_i \))
```

Given a ciphertext \( c \) that encrypts an unknown message \( m \), we can see that an adversary can generate another ciphertext whose contents are *related* to \( m \) *in a predictable way*. This property of an encryption scheme is called **malleability**.

# ## Learning the Last Byte of a Block

We now show how to use the CHECKXOR subroutine to determine the last byte of a plaintext block \( m \). There are two cases to consider, depending on the contents of \( m \). The attacker does not initially know which case holds:

For the first (and easier) of the two cases, suppose the second-to-last byte of \( m \) is nonzero. We will try every possible byte \( b \) and ask whether \( m \oplus b \) has valid padding. Since \( m \) is a block and \( b \) is a single byte, when we write \( m \oplus b \) we mean that \( b \) is extended on the left with zeroes. Since the second-to-last byte of \( m \) (and hence \( m \oplus b \)) is nonzero, only one of these possibilities will have valid padding — the one in which \( m \oplus b \) ends in byte `01`. Therefore, if \( b \) is the candidate byte that succeeds (i.e., \( m \oplus b \) has valid padding) then the last byte of \( m \) must be \( b \oplus \mathtt{01} \).