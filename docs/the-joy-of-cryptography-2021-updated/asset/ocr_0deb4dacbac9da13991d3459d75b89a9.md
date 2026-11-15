blocks. CBC mode does not have this property, as it is inherently sequential. Both modes have a parallelizable decryption algorithm, though.

+   - If calls to the block cipher are expensive, it might be desirable to pre-compute and store them before the plaintext is known. CTR mode allows this, since only the IV affects the input given to the block cipher. In CBC mode, the plaintext influences the inputs to the block cipher, so these calls cannot be pre-computed before the plaintext is known.

+   - It is relatively easy to modify CTR to support plaintexts that are not an exact multiple of the blocklength. (This is left as an exercise.) We will see a way to make CBC mode support such plaintexts as well, but it is far from trivial.

+   - So far all of the comparisons have favored CTR mode, so here is one important property that favors CBC mode. It is common for implementers to misunderstand the security implications of the IV in these modes. Many careless implementations allow an IV to be reused. Technically speaking, reusing an IV (other than by accident, as the birthday bound allows) means that the scheme was not implemented correctly. But rather than dumping the blame on the developer, it is good design practice to anticipate likely misuses of a system and, when possible, try to make them non-catastrophic.

The effects of IV-reuse in CTR mode are quite devastating to message privacy (see the exercises). In CBC mode, reusing an IV can actually be safe, if the two plaintexts have different first blocks!

# ## 8.2 CPA Security and Variable-Length Plaintexts

Here's a big surprise: none of these block cipher modes achieve CPA security, or at least CPA security as we have been defining it.

**Example** Consider a block cipher with $\text{blen} = \lambda$, used in CBC mode. As you will see, there is nothing particularly specific to CBC mode, and the same observations apply to the other modes.

In CBC mode, a plaintext consisting of $\ell$ blocks is encrypted into a ciphertext of $\ell + 1$ blocks. In other words, the ciphertext **leaks the number of blocks in the plaintext**. We can leverage this observation into the following attack:

```
```
\(\mathcal{A}\):
\(c := \text{EAVESDROP}(0^\lambda, 0^{2\lambda})\)
\(\text{return } |c| \stackrel{?}{=} 2\lambda\)
```
```

The distinguisher chooses a 1-block plaintext and a 2-block plaintext. If this distinguisher is linked to \(\mathcal{L}_{\text{cpa-L}}\), the 1-block plaintext is encrypted and the resulting ciphertext is 2 blocks (\(2\lambda\) bits) long. If the distinguisher is linked to \(\mathcal{L}_{\text{cpa-R}}\), the 2-block plaintext is encrypted and the resulting ciphertext is 3 blocks (\(3\lambda\) bits) long. By simply checking the length of the ciphertext, this distinguisher can tell the difference and achieve advantage 1.