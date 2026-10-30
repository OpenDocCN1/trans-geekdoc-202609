There were variations of 3DES that used only two keys. The text was first encrypted with key A. The ciphertext from that operation was then encrypted with key B. Then the ciphertext from that operation was encrypted, this time reusing key A. The reason for this is that creating good cryptographic keys is computationally intensive. This is one approach. There were other variations.

# AES

Advanced Encryption Standard (AES) was the algorithm eventually chosen to replace DES. It is a block cipher that works on 128-bit blocks. It can have one of three key sizes of 128, 192, or 256 bits. This was selected by the U.S. government to be the replacement for DES and is now the most widely used symmetric key algorithm.

AES is also known as Rijndael block cipher. It was officially designated as a replacement for DES in 2001 after a 5-year process involving 15 competing algorithms. AES is designated as FIPS 197. Other algorithms that did not win that competition include such well-known algorithms as Twofish. The importance of AES cannot be overstated. It is widely used around the world and is perhaps the most widely used symmetric cipher. Of all the algorithms in this chapter, AES is the one you should give the most attention to.

AES can have three different key sizes: 128, 192, and 256 bits. The three different implementations of AES are referred to as AES 128, AES 192, and AES 256. The block size can also be 128, 192, or 256 bit. It should be noted that the original Rijndael cipher allowed for variable block and key sizes in 32-bit increments. However, the U.S. government uses these three key sizes with a 128-bit block as the standard for AES.

This algorithm was developed by two Belgian cryptographers, Joan Daemen and Vincent Rijmen. Joan Daemen is a Belgian cryptographer who has worked extensively on the cryptanalysis of block ciphers, stream ciphers, and cryptographic hash functions. For those new to security, this brief description given so far is sufficient; however, we will explore the AES algorithm in more detail. Just as with the details of DES, this may be a bit confusing to some readers at first glance and may require a few rereads.

Rijndael uses a substitution-permutation matrix rather than a Feistel network. The Rijndael cipher works by first putting the 128-bit block of plaintext into a 4-byte by 4-byte matrix. This matrix is termed the state and will change as the algorithm proceeds through its steps. So the first step is to convert the plaintext block into binary and then put it into a matrix.

Once you have the original plaintext in binary, placed in the 4-byte by 4-byte matrix, the algorithm consists of a few relatively simple steps that are used during various rounds. The steps are described here:

+   - **AddRoundKey:** In this step, each byte of the state is exclusively ORd with the round key. Just like DES, there is a key schedule algorithm that slightly changes the key each round.
+   - **SubBytes:** This involves substitution of the input bytes (which are the output from the AddRoundKey phase). This is where the contents of the matrix are put through the s-boxes. Each of the s-boxes is 8 bits.