Example Encrypting the following 20-bit plaintext m under the 20-bit key k using OTP results in the ciphertext c below:

```
  11101111101111100011   (m)
⊕ 00011001110000111101   (k)
  11110110011111011110   (c = Enc(k, m))
```

Decrypting the following ciphertext c using the key k results in the plaintext m below:

```
  00001001011110010000   (c)
⊕ 10010011101011100010   (k)
  100110101010101110010  (m = Dec(k, c))
```

Note that Enc and Dec are essentially the same algorithm (return the xor of the two arguments). This results in some small level of convenience and symmetry when implementing one-time pad, but it is more of a coincidence than something truly fundamental about encryption (see Exercises 1.12 & 2.5). Later on you’ll see encryption schemes whose encryption & decryption algorithms look very different.

# Correctness

The first property of one-time pad that we should confirm is that the receiver does indeed recover the intended plaintext when decrypting the ciphertext. Without this property, the thought of using one-time pad for communication seems silly. Written mathematically:

Claim 1.2 For all k, m ∈ {0, 1}^λ, it is true that Dec(k, Enc(k, m)) = m.

Proof This follows by substituting the definitions of OTP Enc and Dec, then applying the properties of xor listed in Chapter 0.3. For all k, m ∈ {0, 1}^λ, we have:

```
Dec(k, Enc(k, m)) = Dec(k, k ⊕ m)
                  = k ⊕ (k ⊕ m)
                  = (k ⊕ k) ⊕ m
                  = 0^λ ⊕ m
                  = m.
```

Example Encrypting the following plaintext m under the key k results in ciphertext c, as follows:

```
  00110100110110001111   (m)
⊕ 11101010011010001101   (k)
  11011110101100000010   (c)
```

Decrypting c using the same key k results in the original m:

```
  11011110101100000010   (c)
⊕ 11101010011010001101   (k)
  00110100110110001111   (m)
```