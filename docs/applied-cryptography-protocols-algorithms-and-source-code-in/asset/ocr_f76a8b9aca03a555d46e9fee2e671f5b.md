# 19.2 Knapsack Algorithms

# Decryption

A legitimate recipient of the message knows the private key: the original super-increasing knapsack, as well as the values of $n$ and $m$ used to transform it into a normal-knapsack. To decrypt the message, the recipient must first determine $n^{-1}$ such that $nn^{-1} \equiv 1 \pmod m$. Multiply each of the ciphertext values by $n^{-1} \pmod m$, and then partition with the private key to get the plaintext values.

In our example, the superincreasing knapsack is $[2,3,13,27,52]$, $m$ is equal to 105, and $n$ is equal to 31. The ciphertext message is $174,280,333$. In this case $n^{-1}$ is equal to 61, so the ciphertext values were multiplied by 61.

+   - $174 \cdot 61 \pmod{105} = 9 = 3 + 6$, which corresponds to 011000
- $280 \cdot 61 \pmod{105} = 72 = 2 + 3 + 13$, which corresponds to 110101
- $333 \cdot 61 \pmod{105} = 48 = 2 + 6 + 13 + 27$, which corresponds to 101110

# Practical Implementations

With a knapsack of only six items, it's not hard to solve the problem even if it's superincreasing. Real knapsacks should contain at least 250 items. The value for each term in the superincreasing knapsack should be somewhere between 200 and 400 bits long, and the modulus should be somewhere between 100 to 200 bits. Real implementations of the algorithm use random-sequence generators to produce these values.

With knapsacks like these, it's futile to try to solve them by brute force. If a computer could try millions per second, trying all possible knapsack values would take over $10^{10}$ years. Even a million machines working in parallel would solve this problem before the sun went nova.

# Security of Knapsacks

It wasn't a machine that broke the knapsack cryptosystem, but a pair of cryptographers. First a single bit of plaintext was recovered [725]. Shamir showed that knapsacks can be broken in certain circumstances [1415,1416]. There were other results[1428,38,754,51,468]—but no one could break the Merkle-Hellman scheme. Finally Shamir and Jacobi [1418,1419,1421] found flaws in the transformation that allowed to reconstruct the superincreasing knapsack from the normal knapsack. The exact arguments are beyond the scope of this book, but a neat summary of them can be found in [1233,1244]. At the conference where the results were presented, the attack was demonstrated on stage using an Apple computer [492,494].

# Knapsack Variants

Since the original Merkle-Hellman scheme was broke, many other knapsack variants have been proposed: multiple iterated knapsacks, Graham-Shamir knapsacks, and others. These have all been analyzed and broken, generally using the same cryptographic techniques, and litter the cryptographic highway [260,253,269,921,1519,920,322,366,254,263,255]. Good reviews of these systems and their cryptanalyses can be found in [267,479,257,268].