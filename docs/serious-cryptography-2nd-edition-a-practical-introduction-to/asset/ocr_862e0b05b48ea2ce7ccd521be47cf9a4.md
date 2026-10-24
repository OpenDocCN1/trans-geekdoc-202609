Listing 6-4 shows SHA-1’s compression function, `SHA1-compress()`:

```
SHA1-compress(H, M) {
    (a0, b0, c0, d0, e0) = H   // Parsing H as five 32-bit big-endian words
    (a, b, c, d, e) = SHA1-blockcipher(a0, b0, c0, d0, e0, M)
    return (a + a0, b + b0, c + c0, d + d0, e + e0)
}
```

*Listing 6-4: SHA-1’s compression function*

SHA-1’s block cipher `SHA1-blockcipher()`, shown in bold, takes a 512-bit message block, *M*, as a key and transforms the five 32-bit words (a, b, c, d, and e) by iterating 80 steps of a short sequence of operations to replace the word a with a combination of all five words. It then shifts the other words in the array, as in a shift register. Listing 6-5 describes these operations in pseudocode, where K[i] is a round-dependent constant.

```
SHA1-blockcipher(a, b, c, d, e, M) {
    W = expand(M)
    for i = 0 to 79 {
        new = (a <<< 5) + f(i, b, c, d) + e + K[i] + W[i]
        (a, b, c, d, e) = (new, a, b >>> 2, c, d)
    }
    return (a, b, c, d, e)
}
```

*Listing 6-5: SHA-1’s block cipher*

The `expand()` function in Listing 6-5 creates an array of 80 32-bit words, W, from the 16-word message block by setting W’s first 16 words to M and the subsequent ones to an XOR combination of previous words, rotated 1 bit to the left. Listing 6-6 shows the corresponding pseudocode.

```
expand(M) {
    // The 512-bit M is seen as an array of sixteen 32-bit words.
    W = empty array of eighty 32-bit words
    for i = 0 to 79 {
        if i < 16 then W[i] = M[i]
        else
            W[i] = (W[i − 3] ⊕ W[i − 8] ⊕ W[i − 14] ⊕ W[i − 16]) <<< 1
    }
    return W
}
```

*Listing 6-6: SHA-1’s `expand()` function*

The <<< 1 operation in Listing 6-6 is the only difference between the SHA-1 and the SHA-0 functions.

Finally, Listing 6-7 shows the f() function in SHA1-blockcipher(), a sequence of eight bitwise logical operations (a Boolean function) that depends on the round number.