
It is also important to keep in mind that it was the bits on each end that were duplicated. This will be a key item later in the round function. Perhaps this example will help you understand what is occurring at this point. Let us assume 32 bits, as shown here:

`11110011010111111111000101011001`

Now divide this into 8 sections of 4 bits each, as shown here:

`1111 0011 0101 1111 1111 0001 0101 1001`

Now each of these has its end bits duplicated, as you see here:

`1111` becomes `111111`

`0011` becomes `000111`

`0101` becomes `001011`

`1111` becomes `111111`

`1111` becomes `111111`

`0001` becomes `000011`

`0101` becomes `001011`

`1001` becomes `110011`

The resulting 48-bit string is now XORed with the 48-bit round key. Now you are done with the round key. Its only purpose was to XOR with the 32-bit half. It is now discarded, and on the next round another 48-bit round key will be derived from the two 28-bit halves of the 56-bit cipher key, using the key schedule we previously described.

Now we have the 48-bit output of the XOR operation. But this still does not seem to work. Don’t we need 32 bits rather than 48? That 48 bits is now split into 8 sections of 6 bits each. Each of those 6-bit sections is going to be input into an s-box (substitution box), and only 4 bits will be output.

The 6-bit section is used as the input to an *s-box*, which is a table that takes input and produces an output based on that input. In other words, it is a substitution box that substitutes new values for the input. There are eight different s-boxes for DES, but below you can see one of them:

|   ||   || Middle 4 Bits of Input |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

|   ||   || **0000** || **0001** || **0010** || **0011** || **0100** || **0101** || **0110** || **0111** || **1000** || **1001** || **1010** || **1011** || **1100** || **1101** || **1110** || **1111** |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| **Outer Bits** || **00** || 0010 || 1100 || 0100 || 0001 || 0111 || 1010 || 1011 || 0110 || 1000 || 0101 || 0011 || 1111 || 1101 || 0000 || 1110 || 1001 |

| **01** || 1110 || 1011 || 0010 || 1100 || 0100 || 0111 || 1101 || 0001 || 0101 || 0000 || 1111 || 1010 || 0011 || 1001 || 1000 || 0110 |

| **10** || 0100 || 0010 || 0001 || 1011 || 1010 || 1101 || 0111 || 1000 || 1111 || 1001 || 1100 || 0101 || 0110 || 0011 || 0000 || 1110 |

| **11** || 1011 || 1000 || 1100 || 0111 || 0001 || 1110 || 0010 || 1101 || 0110 || 1111 || 0000 || 1001 || 1010 || 0100 || 0101 || 0011 |

An s-box is really just a hard-coded lookup table. The 2 bits on either end are shown in the left column, and the 4 bits in the middle are shown in the top row. They are matched, and the resulting value is the output of the s-box. For example, with the previous demonstration numbers we were using, our first block would be 111111. So you find 1xxxx1 on the left and x1111x on the top. The resulting value is 3 in decimal, or 0011 in binary.

Recall that during the expansion phase we simply duplicated the outermost bits, so when we come to the s-box phase and drop the outermost bits, no data is lost.

Since each s-box outputs 4 bits and there are 8 s-boxes, the result is 32 bits. That 32 bits is now exclusively ORed with the other half of the original block. Recall that we did nothing with that half originally. Now the two halves are swapped.

If you are new to cryptography, all of this might seem a bit confusing, even with the explanations provided. Many readers will need to reread this section a few times for it to become totally clear.

##### 3DES

*Triple DES* (*3DES*) was created as a replacement for DES. At the time, the cryptography community was searching for a viable alternative. While that was still being worked on, 3DES was created as a stop-gap measure. It essentially applies DES three times with three different keys, thus the name 3DES.

There were variations of 3DES that used only two keys. The text was first encrypted with key A. The cipher text from that operation was then encrypted with key B. Then the cipher text from that operation was encrypted, this time reusing key A. The reason for this reuse is that creating good cryptographic keys is computationally intensive.

##### AES

*Advanced Encryption Standard* (*[AES](#glossary.xhtml#gloss3)*) was the algorithm eventually chosen to replace DES. It is a block cipher that works on 128-bit blocks. It can have one of three key sizes: 128, 192, or 256 bits. The U.S. government selected AES to be the replacement for DES, and it is now the most widely used symmetric key algorithm.

AES, also known as *Rijndael block cipher,* was officially designated as a replacement for DES in 2001 after a 5-year process involving 15 competing algorithms. AES is designated as FIPS 197. Other algorithms that did not win that competition include such well-known algorithms as Twofish. The importance of AES cannot be overstated. It is widely used around the world and is perhaps the most widely used symmetric cipher. Of all the algorithms in this chapter, AES is the one you should give the most attention to.

As mentioned earlier, AES can have three different key sizes: 128, 192, and 256 bits. The three different implementations of AES are referred to as AES 128, AES 192, and AES 256. The block size can also be 128, 192, or 256 bit. It should be noted that the original Rijndael cipher allowed for variable block and key sizes in 32-bit increments. However, the U.S. government uses these three key sizes with a 128-bit block as the standard for AES.

This algorithm was developed by two Belgian cryptographers, John Daemen and Vincent Rijmen. John Daeman is a Belgian cryptographer who has worked extensively on the cryptanalysis of block ciphers, stream ciphers, and cryptographic hash functions. For those new to security, the brief description given so far is sufficient. However, we will explore the AES algorithm in more detail. Just as with the details of DES, this may be a bit confusing to some readers at first glance and may require a few rereads.

Rijndael uses a substitution-permutation matrix rather than a Feistel network. The Rijndael cipher works by first putting the 128-bit block of plain text into a 4-byte-by-4-byte matrix, termed the *state*, that changes as the algorithm proceeds through its steps. The first step is to convert the plain text block into binary and then put it into a matrix, as shown in [Figure 8.3](#ch08.xhtml#ch08fig03).

![Figure 8.3 The Rijndael matrix.](Images/08fig03.jpg)

**Figure 8.3** The Rijndael matrix.

Once you have the original plain text in binary, placed in the 4-byte-by-4-byte matrix, the algorithm consists of a few relatively simple processes that are used during various rounds. The processes are described here:

*   **AddRoundKey:** In this process, each byte of the state is exclusively ORed with the round key. Just as with DES, there is a key schedule algorithm that slightly changes the key each round.

*   **SubBytes:** This involves substitutions of the input bytes (which are the output from the AddRoundKey phase). This is where the contents of the matrix are put through the s-boxes. Each of the s-boxes is 8 bits.

*   **ShiftRows:** This is a transposition step where each row of the state is shifted cyclically a certain number of steps. In this process, the first row is left unchanged. Every byte in the second row is shifted 1 byte to the left (and the far left wraps around). Every byte of the third row is shifted 2 to the left, and every byte of the fourth row is shifted 3 to the left (again with the far left wrapping around). This is shown in [Figure 8.4](#ch08.xhtml#ch08fig04). Notice that in this figure that the bytes are simply labeled by their row and then a letter, such as 1a, 1b, 1c, 1d.
