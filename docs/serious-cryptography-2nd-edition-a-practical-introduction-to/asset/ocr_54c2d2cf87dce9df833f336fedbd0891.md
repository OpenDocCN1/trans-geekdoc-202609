Once this algorithm completes, array S still contains all the byte values from 0 to 255 but now in a random-looking order. For example, with the all-zero 128-bit key, the state S (from S[0] to S[255]) becomes:

0, 35, 3, 43, 9, 11, 65, 229, (…), 233, 169, 117, 184, 31, 39

However, if I flip the first key bit and run the KSA again, I get a totally different, apparently random state:

32, 116, 131, 134, 138, 143, 149, (…), 152, 235, 111, 48, 80, 12

Given the initial state S, RC4 generates a keystream, KS, of the same length as the plaintext, P, to compute a ciphertext: C = P ⊕ KS. The bytes of the keystream KS are computed from S according to the Python code in Listing 5-2, if P is m bytes long.

```
i = 0
j = 0
for b in range(m):
    i = (i + 1) % 256
    j = (j + S[i]) % 256
    S[i], S[j] = S[j], S[i]
    KS[b] = S[(S[i] + S[j]) % 256]
```

Listing 5-2: The keystream generation of RC4, where S is the state initialized in Listing 5-1

In Listing 5-2, each iteration of the for loop modifies up to 2 bytes of RC4's internal state S: the S[i] and S[j] whose values are swapped. That is, if i = 0 and j = 4 and if S[0] = 56 and S[4] = 78, then the swap operation sets S[0] to 78 and S[4] to 56. If j equals i, then S[i] isn't modified.

This looks too simple to be secure, yet it took 20 years for cryptanalysts to find exploitable flaws. Before the flaws were revealed, we knew RC4's weaknesses only in specific implementations, as in the first Wi-Fi encryption standard, WEP.

# RC4 in WEP

WEP, the first-generation Wi-Fi security protocol, is now completely broken due to weaknesses in the protocol's design and in RC4.

In its WEP implementation, RC4 encrypts payload data of 802.11 frames, the datagrams (or packets) that transport data over the wireless network. All payloads delivered in the same session use the same secret key of 40 or 104 bits but have what is a supposedly unique 3-byte nonce encoded in the frame header (the part of the frame that encodes metadata and comes before the actual payload).