26! = 403291461126605635584000000 ≈ 2^88

Here, the exclamation point (!) is the factorial symbol, defined as follows:

n! = n × (n − 1) × (n − 2) × … × 3 × 2

(To see why we end up with this number, count the permutations as lists of reordered letters: there are 26 choices for the first possible letter, then 25 possibilities for the second, 24 for the third, and so on.) This number is huge: it’s of the same order of magnitude as the number of atoms in the human body. But classical ciphers can use only a small fraction of those permutations—namely, those that require simple operations (such as shifts) and have a short description (like a short algorithm or a small lookup table). The problem is that a secure permutation can’t accommodate both of these limitations.

You can get secure permutations using simple operations by picking a random permutation, representing it as a table of 25 letters (enough to represent a permutation of 26 letters, with the 26th one missing), and applying it by looking up letters in this table. But then you wouldn’t have a short description. For example, it would take 250 letters to describe 10 different permutations, rather than just the 10 letters used in the Vigenère cipher.

You can also produce secure permutations with a short description. Instead of just shifting the alphabet, you could use more complex operations such as addition and multiplication. This is how modern ciphers work: given a key of typically 128 or 256 bits, they perform hundreds of bit operations to encrypt a single letter. This process is fast on a computer that can do billions of bit operations per second, but it would take hours to do by hand and would still be vulnerable to frequency analysis.

# The Perfect Cipher: The One-Time Pad

Essentially, a classical cipher can’t be secure unless it comes with a huge key, but encrypting with a huge key is impractical. However, the one-time pad is such a cipher, and it is the most secure cipher. In fact, it guarantees perfect secrecy: even if an attacker has unlimited computing power, it’s impossible to learn anything about the plaintext except for its length.

In the next sections, I’ll show you how a one-time pad works and then offer a sketch of its security proof.

# Encryption and Decryption

The one-time pad takes a plaintext, P, and a random key, K, that’s the same length as P and produces a ciphertext, C, defined as

C = P ⊕ K

where C, P, and K are bit strings of the same length and ⊕ is the bitwise exclusive OR operation (XOR), defined as 0 ⊕ 0 = 0, 0 ⊕ 1 = 1, 1 ⊕ 0 = 1, 1 ⊕ 1 = 0.