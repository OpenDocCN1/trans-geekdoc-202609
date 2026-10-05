
# 9.6 Cipher-feedback Mode

![](img/e08b4270295105438dabfbd9a81857bf_223_0.png)

9.10 n-bit CFB with an n-bit algorithm.

$C_i = P_i \oplus E_k[C_{i-1}]$
$P_i = C_i \oplus E_k[C_{i-1}]$

Like CBC mode, CFB mode links the plaintext characters together so that the ciphertext depends on all the preceding plaintext.

## Initialization Vector

To initialize the CFB mode, the input to the block algorithm must be initialized with an IV. The IV used in CBC mode, need not be secret.

The IV must be unique, though. (This is different from the IV in CBC mode, which should be unique but does not have to be). If the IV in CFB is not unique, a cryptanalyst can recover the corresponding plaintext. The IV must be changed with every message. It can be a serial number, which increments after each message and does not repeat during the lifetime of the key. For data encrypted for storage, it can be a function of the index used to look up the data.

## Error Propagation

With CFB mode, an error in the plaintext affects all subsequent ciphertext and reverses itself at decryption. An error in the ciphertext is more interesting. The first effect of a single-bit error in the ciphertext is to cause a single error in the plaintext. After that, the error enters the shift register, where it causes ciphertext to be garbled until it falls off the other end of the register. In 8-bit mode, 9 bytes of decrypted are garbled by a single-bit error in the ciphertext. After that the decryption is correct. Generally, in n-bit CFB a single error will affect the decryption of the current and following m/n-1 blocks, where m is the block size.

One problem with this kind of error propagation is that if Mallory knows the plaintext of a transmission, he can toggle bits in a given block and make it decrypt to whatever he wants. The next block will decrypt garbage, but the damage may already be done. And he can change the final bits of a message without detection.

CFB is self-recovering with respect to synchronization errors as well. The error enters the shift register, where it garbles 8 bytes of data until it falls off the other end. CFB is an example of block cipher used as a self-synchronizing stream cipher (at the block level).

## 9.7 SYNCHRONOUS STREAM CIPHERS

In a synchronous cipher the keystream is generated independent of the message stream. The military calls this Key Auto-Key (KAK). On the encryption side, keystream generator spits out keystream bits, one after the other. On the decryption side, another keystream generator spits out identical keystream bits, one after the other. This works, as long as the two keystream generators are synchronized. If one of them skips a cycle or if the keystream bit gets lost during transmission, then every ciphertext character after the error will decrypt incorrectly.

If this happens, the sender and receiver must resynchronize their keystream generator before they can proceed. Matters even further, they must do this in a way so that no part of the keystream is repeated, so the obvious resetting the keystream generator to an earlier state won't work.

On the plus side, synchronous ciphers do not propagate transmission errors. If a bit is garbled during transmission, which is more likely than being lost also, only the garbled bit will be decrypted incorrectly. All preceding and subsequent bits will be unaffected.

Since a keystream generator must generate the same output on both the encryption ends, it must be deterministic. Because it is implemented in a finite-state machine (i.e., a computer), the sequence will eventually repeat. These keystream generators are called periodic. Except for one-time pads, all keystream generators are periodic.

The keystream generator must have a long period, one longer than the number of bits generated. If the period is less than the plaintext, then parts of the plaintext repeat—a severe weakness. If a cryptanalyst knows a piece of the plaintext, he can recover a piece of the keystream and use that to recover more of the plaintext. If even the analyst only has the ciphertext, he can XOR the sections encrypted with the same keystream and the XOR of plaintext with plaintext. This is just the simple XOR algorithm with a very long period.

How long a period depends on the application. A keystream generator for a continuous T-1 link will encrypt 2 bits per day. The keystream generator's period is of magnitude larger than that, even if the key is changed daily. If the period is too long, you might only have to change the key very weekly or monthly.

Synchronous ciphers also protect against any insertions and deletions in the ciphertext, because these cause a loss of synchronization and will be immediately detected. They do not, however, fully protect against bit toggling. Like block ciphers in CFB mode, Mallory can toggle individual bits in the stream. If he knows the plaintext, he can make these bits decrypt to whatever he wants. Subsequent bits decrypt correctly, so in certain applications Mallory still do considerable damage.

## 9.8 Output-feedback Mode

### Insertion Attack

Synchronous stream ciphers are vulnerable to an insertion attack [93]. Mallory has recorded a ciphertext stream, but does not know the ciphertext or the keystream used to encrypt it.

```
Original plaintext:      p1 p2 p3
Original keystream:      k1 k2 k3
Original ciphertext:     c1 c2 c3
```

Mallory inserts a single known bit, into the plaintext, and then manages to get the modified plaintext encrypted with the same keystream. He records the updated ciphertext:

```
New plaintext:          p1 p' p3
New keystream:          k1 k2 k3
Updated ciphertext:     c1 c' c3
```

Assuming he knows the value of p', he can determine the entire keystream from the original and updated ciphertexts:

```
k1 = c1 ⊕ p1 (already known)
k2 = c' ⊕ p'
```

Mallory doesn't have to know the exact position in which the bit was inserted, he can just compare the original and updated ciphertexts to see where they begin to differ. To protect against this attack, never use the same keystream to encrypt two different messages.

## 9.8 OUTPUT-FEEDBACK MODE

Output-feedback (OFB) mode is a method of running a block cipher as a synchronous stream cipher. It is similar to CFB, except n bits of the previous output are moved into the right-most positions of the queue [See Figure 11]. Decryption is the reverse of this process. If n is the block size of the algorithm, n-bit OFB looks like (See Figure 12):

```
C_i = P_i ⊕ S_i, S_i = E_k(S_{i-1})
P_i = C_i ⊕ S_i, S_i = E_k(S_{i-1})
```

S_i is the state, which is independent of either the plaintext or the ciphertext. One nice feature of OFB mode is that most of the work can occur offline, before the plaintext exists. When the message arrives, it can be XORed with the output of the algorithm to produce the ciphertext.

## CHAPTER 9 Algorithm Types and Modes

![](img/e08b4270295105438dabfbd9a81857bf_226_0.png)

Figure 9.11 8-bit output-feedback mode.

## Initialization Vector

The OFB shift register must also be initially loaded with an IV. It should be unique but does not have be secret.

## Error Propagation

OFB mode has no error extension. A single-bit error in the ciphertext causes a single-bit error in the recovered plaintext. This can be useful in some digitized voice or video, where the occasional single-bit error can be tolerated without error extension.

On the other hand, a loss of synchronization is fatal. If the shift registers on the encryption end and the decryption end are not identical, then the recovered plaintext will be gibberish. Any system that uses OFB must have a mechanism for detecting a synchronization loss and a mechanism to fill both shift registers with new (or the same) IV to regain synchronization.

![](img/e08b4270295105438dabfbd9a81857bf_226_1.png)

Figure 9.12 n-bit OFB with an n-bit algorithm.
