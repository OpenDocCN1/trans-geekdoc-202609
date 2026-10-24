
If there are 15 plaintext bytes and a single byte missing to fill a block, padding adds a single 01 byte. If the plaintext is already a multiple of 16 bytes, then add 16 bytes 0x10 (16 in decimal). The trick generalizes to any block length up to 255 bytes (for larger blocks, a byte is too small to encode values greater than 255).

Decryption of a padded message works like this:

- 1. Decrypt all the blocks as with unpadded CBC.
- 2. Make sure that the last bytes of the last block conform to the padding rule: that they finish with at least one 01 byte, at least two 02 bytes, or at least three 03 bytes, and so on. If the padding isn’t valid—for example, if the last bytes are 01 02 03—the message is rejected. Otherwise, decryption strips the padding bytes and returns the plaintext bytes left.

One downside of padding is that it makes ciphertext longer by at least 1 byte and at most a block.

## Ciphertext Stealing

Ciphertext stealing is another trick we use to encrypt a message whose length isn’t a multiple of the block size. Ciphertext stealing is more complex and less popular than padding, but it offers a few benefits:

- Plaintexts can be of any bit length, not just bytes. You can, for example, encrypt a message of 131 bits.
- Ciphertexts are exactly the same length as plaintexts.
- Ciphertext stealing is not vulnerable to padding oracle attacks, powerful attacks that sometimes work against CBC with padding (as you’ll see in “Padding Oracle Attacks” on page 83).

In CBC mode, ciphertext stealing extends the last incomplete plaintext block with bits from the previous ciphertext block and then encrypts the resulting block. The last, incomplete ciphertext block is made up of the first bits from the previous ciphertext block—that is, the bits that haven’t been appended to the last plaintext block.

In Figure 4-9, we have three blocks, where the last block, P₃, is incomplete (represented by a zero). If P₃ is 3 bytes, we XOR it with the last 12 bits from the previous ciphertext block E(K, P₂) and return the encrypted result as C₃. The last ciphertext block, C₃, then consists of the first 4 bytes of E(K, P₂). Decryption is simply the inverse of this operation.

![](img/ace4de942d037de8ea5835bc9fbe57cd_107_0.png)

*Figure 4-9: Ciphertext stealing for CBC-mode encryption*

There aren’t any major problems with ciphertext stealing, but it’s inelegant and hard to get right, especially when NIST’s standard specifies three different ways to implement it (see Special Publication 800-38A).

## Counter Mode

To avoid the troubles and retain the benefits of ciphertext stealing, use counter mode (CTR). CTR is hardly a block cipher mode: it turns a block cipher into a stream cipher that just takes bits in and spits bits out and doesn’t embarrass itself with the notion of blocks. (I’ll discuss stream ciphers in detail in Chapter 5.)

In CTR mode (see Figure 4-10), the block cipher algorithm won’t transform plaintext data. Instead, it encrypts blocks composed of a counter and a nonce. A *counter* is an integer that is incremented for each block. No two blocks should use the same counter within a message, but different messages can use the same sequence of counter values (1, 2, 3, . . .). A *nonce* is a number we use only once. It’s the same for all blocks in a single message, but no two messages should use the same nonce.

![](img/ace4de942d037de8ea5835bc9fbe57cd_107_1.png)

*Figure 4-10: CTR mode*

Figure 4-10 shows that in CTR mode, encryption XORs the plaintext and the stream taken from “encrypting” the nonce, N, and counter, Ctr. Decryption is the same, so you need only the encryption algorithm for both encryption and decryption. The Python script in Listing 4-6 gives you a hands-on example.

```
#!/usr/bin/env python

from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from os import urandom

BLOCK_SIZE = 16
KEY_SIZE = 16

# Pick a random key.
k = urandom(KEY_SIZE)
print(f"k   = {k.hex()}")

# And a random nonce
# (careful with random nonces, see discussion below).
n = urandom(BLOCK_SIZE)
print(f"nonce  = {n.hex()}")

# Create a 7-byte plaintext p.
p = bytes([0x00] * 7)

# Encrypt the plaintext p with AES-CTR.
aes_ctr_encryptor = Cipher(algorithms.AES(k), modes.CTR(n)).encryptor()

c = aes_ctr_encryptor.update(p) + aes_ctr_encryptor.finalize()
print(f"enc({p.hex()}) = {c.hex()}")

# Decrypt the ciphertext c.
aes_ctr_decryptor = Cipher(algorithms.AES(k), modes.CTR(n)).decryptor()
p = aes_ctr_decryptor.update(c) + aes_ctr_decryptor.finalize()
print(f"dec({c.hex()}) = {p.hex()}")

# Decrypt the ciphertext c using the encryption function.
aes_ctr_encryptor = Cipher(algorithms.AES(k), modes.CTR(n)).encryptor()
p = aes_ctr_encryptor.update(c) + aes_ctr_encryptor.finalize()
print(f"enc({c.hex()}) = {p.hex()}")
```

*Listing 4-6: Using AES in CTR mode*

The example execution encrypts a 4-byte plaintext and gets a 4-byte ciphertext. It then decrypts that ciphertext using the encryption function:

```
$ ./aes_ctr.py
k = 130a1aa77fa58335272156421cb2a3ea
enc(00010203) = b23d284e
enc(b23d284e) = 00010203
```

As with the initial value in CBC, the encrypter supplies CTR's nonce and sends it with the ciphertext in the clear. But unlike CBC's initial value, CTR's nonce doesn't need to be random; it simply needs to be unique. A nonce should be unique for the same reason that we shouldn't reuse a one-time pad: when calling the pseudorandom stream, S, if you encrypt P₁ to C₁ = P₁ ⊕ S and P₂ to C₂ = P₂ ⊕ S using the same nonce, then C₁ ⊕ C₂ reveals P₁ ⊕ P₂.

A random nonce will do the trick only if it’s long enough; for example, if the nonce is n bits, chances are that after 2^{n/2} encryptions and as many nonces, you’ll run into duplicates. Sixty-four bits are insufficient for a random nonce, since you can expect a repetition after approximately 2^{32} nonces, which is an unacceptably low number.

The counter is guaranteed unique if it’s incremented for every new plaintext, and if it’s long enough—for example, a 64-bit counter.

One particular benefit to CTR is that it can be faster than any other mode. Not only is it parallelizable, but you can also start encrypting even before knowing the message by picking a nonce and computing the stream that you’ll later XOR with the plaintext.

> NOTE
> Depending on the CTR version we implement, we may either concatenate the nonce the API uses as an argument to a counter (as in Figure 4-10) or directly consider a counter as wide as a block.

## How Things Can Go Wrong

There are two must-know attacks on block ciphers: meet-in-the-middle attacks, a technique discovered in the 1970s but still used in many cryptanalytic attacks (not to be confused with man-in-the-middle attacks), and padding oracle attacks, a class of attacks discovered in 2002 by academic cryptographers, then mostly ignored, and finally rediscovered a decade later along with several vulnerable applications.

## Meet-in-the-Middle Attacks

The 3DES block cipher is an upgraded version of the 1970s standard DES that takes a key of 56 × 3 = 168 bits (an improvement on DES’s 56-bit key). But the security level of 3DES is 112 bits instead of 168 bits because of the meet-in-the-middle (MitM) attack.

Figure 4-11 shows that 3DES encrypts a block using the DES encryption and decryption functions: first encryption with a key, K₁; then decryption with a key, K₂; and finally encryption with another key, K₃. If K₁ = K₂, the first two calls cancel themselves out, and 3DES boils down to a single DES with key K₃. 3DES does encrypt-decrypt-encrypt rather than encrypting thrice to allow systems to emulate DES when necessary using the new 3DES interface.

![](img/ace4de942d037de8ea5835bc9fbe57cd_109_0.png)

Why use triple DES and not just double DES—that is, why encrypt a plaintext P to E(K₂, E(K₁, P))? It turns out that the MitM attack makes double DES only as secure as single DES. Figure 4-12 shows the MitM attack in action.

![](img/ace4de942d037de8ea5835bc9fbe57cd_110_0.png)

Figure 4-12: The MitM attack

The MitM attack works as follows to attack double DES:

- 1. Say you have P and C = E(K₂, E(K₁, P)) with two unknown 56-bit keys, K₁ and K₂. (DES takes 56-bit keys, so double DES takes 112 key bits in total.) You build a key-value table with 2⁵⁶ entries of E(K₁, P), where E is the DES encryption function and K₁ is the value stored.
- 2. For all 2⁵⁶ values of K₂, compute D(K₂, C) and check whether the resulting value appears in the table as an index (thus as a middle value, represented by a question mark in Figure 4-12).
- 3. If you find a middle value as an index of the table, fetch the corresponding K₁ from the table and verify that the (K₁, K₂) found is the right one by using other pairs of P and C. Encrypt P using K₁ and K₂ and then check that the ciphertext obtained is the given C.

This method recovers K₁ and K₂ by performing about 2⁵⁷ instead of 2¹¹² operations: step 1 encrypts 2⁵⁶ blocks, and then step 2 decrypts at most 2⁵⁶ blocks, for 2⁵⁶ + 2⁵⁶ = 2⁵⁷ operations in total. You also need to store 2⁵⁶ elements of 15 bytes each, or about 1 exabyte. That's a lot, but there's a trick that allows you to run the same attack with only negligible memory (as you'll see in Chapter 6).

You can apply the MitM attack to 3DES in almost the same way you would to double DES, except that the third stage will go through all 2¹¹² values of K₂ and K₃. The whole attack thus succeeds after performing about 2¹¹² operations, meaning that 3DES gets only 112-bit security despite having 168 bits of key material.

## Padding Oracle Attacks

We conclude this chapter with one of the simplest and yet most devastating attacks of the 2000s: the padding oracle attack. Remember that padding fills the plaintext with extra bytes to fill a block. A plaintext of 111 bytes, for example, is a sequence of six 16-byte blocks followed by 15 bytes. In this case, forming a complete block padding adds a 01 byte. For a 110-byte plaintext, padding adds 2 02 bytes. For a 109-byte plaintext, it adds 3 03 bytes, and so on, up to the case where we add 16 10 bytes, where the hexadecimal value 10 is equal to 16.
