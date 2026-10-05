byte of the plaintext. First, the entire key is XORed with a random constant and then rotated to the left 3 bits. The low-order 3 bits of the low-order byte frame are saved; they will control the rotation of the other 2 bytes. Then, the low-order byte of the working frame is XORed with the low-order byte of the key. Then, the concatenation of the 2 high-order bytes are rotated to the left number of bits (0 to 7). Finally, the working frame is shifted to the right 1 byte and the whole process repeats.

The point of the random constant is to turn the key into a pseudo-random sequence. The length of this constant must be equal to the length of the key and must be the same for everyone who wishes to communicate with one another. For a 64-bit key, Madryga examines the constant 00f1e2d3c4b5a697.

Decryption reverses this. Each iteration of the inner cycle starts the working frame from the third-to-last byte of the ciphertext and advances in the reverse direction directly through the second-to-last byte of the ciphertext. Both the key and the two ciphertext bytes are shifted to the right. And the XOR is done before rotations.

# Cryptanalysis of Madryga

Researchers at Queensland University of Technology [675] examined Madryga, along with several other block ciphers. They observed that the algorithm didnt exhibit the plaintext-ciphertext avalanche effect. Additionally, many ciphers had a higher percentage of ones zeros.

Although I know no formal analysis of the algorithm, it doesn't look terribly secure. A cursory review by Eli Bih led to the following observations [160]:

+   The algorithm consists only of linear operations (rotations and XOR), which are slightly modified depending on the data.
- There is nothing like the strength of DES S-boxes.
- The parity of all the bits of the plaintext and the ciphertext is a constant, depending only on the key. So, if you have one plaintext and its ciphertext, you can predict the parity of the ciphertext for any plaintext.

None of this is damaging in itself, but it doesn't leave me with a good feeling about the algorithm. I do not recommend Madryga.

# 13.3 NewDES

NewDES was designed in 1985 by Robert Scott as a possible DES replacement [145,364]. The algorithm is not a DES variant, as its name might imply. It operates on 64-bit blocks of plaintext, but it has a 120-bit key. NewDES is simpler than DES, with no initial or final permutations. All operations are on bytes. (Actually, NewDES isn't anything like a new version of DES; the name is unfortunate.)

The plaintext block is divided into eight 1-byte sub-blocks: $B_0, B_1, \dots, B_7$. Then the subblocks go through 17 rounds. Each round has seven steps. In each step, one of the sub-blocks is XORed with some key material (there is one exception).