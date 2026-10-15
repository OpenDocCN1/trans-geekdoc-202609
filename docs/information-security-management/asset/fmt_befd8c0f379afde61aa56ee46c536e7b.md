
As a consequence of cipher compromises, modern ciphers have increased the complexity of the ciphering algorithms. For example, 3DES carried the DES concept forward by taking the DES 64-bit keys and tripling the rounds to create an overall key length of 192 bits. (Note that 3DES can be executed in several different ways, or modes, which are beyond the scope of our text, but for a more precise and thorough explanation, see Kaufman.[²](#9781284211658_CH10_08.xhtml#c10-bib0002)) Recall, though, that DES requires bits for integrity checking, and that means some number of bits is siphoned off and the rest is left over for the key. The 3DES breaks the key into three subkeys, padding the keys if necessary so they are each 64 bits long, then the remainder of the encryption process uses the DES algorithm but with 48 rather than 56 bits (for reasons we have explained relative to integrity checking). As described conceptually then in this example, substitution, transposition and permutation are fairly straightforward in this approach, but the actual computations are much more complex.

Aside from 3DES, we have also seen the popularization of IDEA (International Data Encryption Algorithm). With the IDEA algorithm, there are three substitution operations performed on data: (1) a bitwise XOR, (2) addition modulo 2[^(16)](#9781284211658_CH10_08.xhtml#c10-bib0016), and (3) multiplication modulo 2[^(16)](#9781284211658_CH10_08.xhtml#c10-bib0016) + 1, where an all zero block is treated as 2[^(16)](#9781284211658_CH10_08.xhtml#c10-bib0016). IDEA combines 16-bit chunks of keys and data using various substitution functions with a final permutation at the end of each round. The final output transformation consists of repeating the initial substitutions utilizing the same 16-bit key chunks. By these examples, which we have simplified, you can still see how difficult it can be to decipher even relatively simple modern ciphers, at least for humans—computers have an easier time of it.

The Advanced Encryption Standard, or AES (FIPS PUB 197), is like 3DES in that it is a symmetric cipher that operates on blocks of data rather than a continuous stream. However, the cipher itself is very different from 3DES. The block size for AES is 128 bits, with the key size being 128, 192, or 256 bits. For clarity, it is recommended that the key size be specified when talking about the algorithm (AES-128, AES-192, AES-256) (FIPS PUB 197). AES differs from 3DES in how it handles data blocks. Instead of dividing data blocks in halves, then performing the round function and swapping the halves, the Rijndael (named for inventers Vincent Rijmen and Joan Daemen) algorithm on which AES is based creates parallel substitution and permutation stages, where every permutation has three substitution stages.[^(15)](#9781284211658_CH10_08.xhtml#c10-bib0015) The basic algorithm for AES is as follows:

1.  Take the given key (128, 192, 256 bit) and, using the specified key expansion algorithm, generate enough 32-bit chunks (known as words) to cover one more than the number of rounds. A 128-bit key will have 10 rounds, a 192-bit key will have 12 rounds, and a 256 bit key will have 14 rounds.

2.  Break the 128-bit block to be encrypted into 8-bit bytes.

3.  XOR 128-bit round key with the 128-bit block of data.

4.  For all but the last round:

    1.  Substitute bytes in the current block according to the substitution table (called an S-box, which is a matrix of values from which to select). This is the first substitution.

    2.  Shift the rows in the block cyclically according to the row number. This is the permutation.

    3.  Mix the column in the block according to the specified algorithm (for details, see FIPS PUB 197). This is the second substitution.

    4.  Add a round key with XOR. This is the third substitution.

5.  For all but the last round:

    1.  Substitute bytes in the block according to the substitution table (S-box).

    2.  Shift the rows in the block according to their row number.

    3.  Add the final round key with XOR.

As seen by this simplified description of AES, and more specifically, the Rijndael algorithm, it does not perform a symmetrical substitution (Feistel) as does DES. Instead, using S-boxes (a matrix of values that can be algorithmically vectored and selected), the selections are a multiplicative inverse transformation function for each input value.[²](#9781284211658_CH10_08.xhtml#c10-bib0002) This is a complicated way of saying simply that the values chosen are not just subdivided, substituted, and swapped in the permutation round. Rather, the algorithm has nonlinearity properties, making it extremely difficult for a cryptanalyst (a code breaker) to calculate a next iteration result, given a known previous iteration result, which is otherwise the case with DES.[^(16)](#9781284211658_CH10_08.xhtml#c10-bib0016)

### 10.2.4 Key Issues with Symmetric Cryptography

As you now know, private key cryptography uses the same key to encrypt and decrypt a message, and the key must be kept secret. This form of cryptography is quite efficient in terms of encryption and decryption of messages. By simply reversing the process, an encrypted message can be reconstructed because the XOR function reverses the bits back to their original form. To highlight with a simple explanation, if we encode a message segment 1001 with a subkey 1111, the XOR produces 0110. If we XOR 0110 with the subkey 1111, we get 1001. However, relying on one key poses some problems in terms of distributing the keys and keeping them secure.

One of the practical problems faced in wide-scale, secret key cryptography is how to exchange keys with many others electronically. Whitfield Diffie and Martin Hellman devised a method of using modulo functions with prime numbers to encode the key. While the Diffie–Hellman technique is not technically cryptography, it uses cryptographic techniques to encode keys exchanged by parties. Thus, the Diffie–Hellman key exchange protocol allows two users to independently generate a shared secret key utilizing information passed over an insecure communication channel. The key exchange is based on the difficulty of computing discrete logarithms, but for our purposes, it’s sufficient to understand how the numbers needed to compute the shared secret are chosen. The exchange depends on choosing a prime number, p, and a primitive root of the prime number mod p.

A primitive root of a prime number p is one whose powers mod p up to p – 1 generates all the integers from 1 to p – 1 creating a matrix of primes from which the cryptographic system can choose (for a thorough explanation, see Stallings, p. 294).[^(17)](#9781284211658_CH10_08.xhtml#c10-bib0017) As an example, given the prime number 5, the primitive roots are 2 and 3 because each satisfies the requirements:

1.  2¹ mod 5 = 2; 2² mod 5 = 4; 2³ mod 5 = 3; 2⁴ mod 5 = 1

2.  3¹ mod 5 = 3; 3² mod 5 = 4; 3³ mod 5 = 2; 3⁴ mod 5 = 1
