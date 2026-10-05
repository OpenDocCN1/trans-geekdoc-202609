If Alice and Bob do not trust each other's algorithms, they can use a cascade. If these are stream algorithms, the order doesn't matter. If they are block algorithms, Alice can first use Algorithm A and then use Algorithm B. Bob, who trusts Algorithm B more, can use Algorithm B followed by Algorithm A. They might even add a good stream cipher between the two; it can't hurt and could well increase security.

Remember that the keys for each algorithm in the cascade must be independent. If Algorithm A has a 64-bit key and Algorithm B has a 128-bit key, then the cascade must have a 192-bit key. If you don't use independent keys, then the pessimists are much more likely to be right.

# 15.8 COMBINING MULTIPLE BLOCK ALGORITHMS

Here's another way to combine multiple block algorithms, one that is guaranteed to be at least as secure as both algorithms. With two algorithms (and two independent keys):

+   (1) Generate a random-bit string, $R$, the same size as the message $M$.
(2) Encrypt $R$ with the first algorithm.
(3) Encrypt $M \oplus R$ with the second algorithm.
(4) The ciphertext message is the results of steps [2] and [3].

Assuming the random-bit string is indeed random, this method encrypts $M$ with a one-time pad and then encrypts both the pad and the encrypted message with each of the two algorithms. Since both are required to reconstruct $M$, a cryptanalyst must break both algorithms. The drawback is that the ciphertext is twice the size of the plaintext.

This method can be extended to multiple algorithms, but the ciphertext expands with each additional algorithm. It's a good idea, but I don't think it's very practical.