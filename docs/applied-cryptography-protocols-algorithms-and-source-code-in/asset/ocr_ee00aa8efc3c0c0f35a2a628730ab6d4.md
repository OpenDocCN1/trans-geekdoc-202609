# 9.8 Output-feedback Mode

# # Insertion Attack

Synchronous stream ciphers are vulnerable to an insertion attack [93]. Mallory has recorded a ciphertext stream, but does not know the ciphertext or the keystream used to encrypt the plaintext.

```
Original plaintext:      p_1 p_2 p_3 ...
Original keystream: k_1 k_2 k_3 ...
Original ciphertext: c_1 c_2 c_3 ...
```

Mallory inserts a single known bit, p', into the plaintext p_i, and then manages to get the modified plaintext encrypted with the same keystream. He records the new ciphertext:

```
New plaintext:       p'_1 p'_2 p'_3 ...
Original keystream: k_1 k_2 k_3 ...
Updated ciphertext:  c'_1 c'_2 c'_3 ...
```

Assuming he knows the value of p'_i, he can determine the entire plaintext bit from the original ciphertext and new keystream:

```
k_i = c'_i ⊕ p'_i, and then p_i = c_i ⊕ k_i
k_j = c'_j ⊕ p'_j, and then p_j = c_j ⊕ k_j
k_k = c'_k ⊕ p'_k, and then p_k = c_k ⊕ k_k
```

Mallory doesn't have to know the exact position in which the bit was inserted, he can just compare the original and updated ciphertexts to see where they begin to differ. To protect against this attack, never use the same keystream to encrypt two different messages.

# 9.8 OUTPUT-FEEDBACK MODE

Output-feedback (OFB) mode is a method of running a block cipher as a synchronous stream cipher. It is similar to CFB, except n bits of the previous output block are moved into the right-most positions of the queue [See Figure 11]. Decryption is the reverse of this process. This is n-bit OFB. On both the encryption and decryption sides, the block algorithm is used in its encryption mode. This is sometimes called internal feedback, because the feedback mechanism is independent of the plaintext and the ciphertext streams [291]. If n is the block size of the algorithm, n-bit OFB looks like (See Figure 12):

```
C_i = P_i ⊕ S_i, S_i = E_k(S_{i-1})
P_i = C_i ⊕ S_i, S_i = E_k(S_{i-1})
```

S_i is the state, which is independent of either the plaintext or the ciphertext. One nice feature of OFB mode is that most of the work can occur offline, before the plaintext message exists. When the message arrives, it can be XORed with the output of the algorithm to produce the ciphertext.