# 344 CHAPTER 14 Still Other Block Ciphers. On the other hand,

(4) $m = 0$
(5) For $j = 0$ to 1

```
For $i = 256$ to 1 step-1
m = (K_{256-i} + K_{257-j}) \mod i$
$K_{357-i} = K_{257-j} \lll 3$
Swap $P_i$ and $P_{i-1}$
```

The S-array of 2048 32-bit words could be generated in a similar manner, either from the same 80-bit key or another key. The authors claim that these details should "viewed as motivational, there may well be alternative schemes which are both more efficient and offer improved security" [810].
 Crab proposed as a test of new ideas and not as a working algorithm. It uses many of the same techniques as MD5. Biham argued that a very large block size makes an algorithm easier to cryptanalyze [160]. Crab might make efficient use of a very large key. In such a case, "easier to cryptanalyze" might not mean much.

# 14.7 SXAL8/MBAL

This is a 64-bit block algorithm from Japan [769]. SXAL8 is the basic algorithm, MBAL is an expanded version with a block length. Since MBAL does some clever things, the authors claim that they can get adequate security with only a few rounds. With a block length of 1024 bytes, MBAL is about 70 times faster than DES. Unfortunately, [1174] shows that MBAL is susceptible to differential cryptanalysis, and [865] shows that it is susceptible to linear analysis.

# 14.8 RC5

RC5 is a block cipher with a variety of parameters: block size, key size, and number of rounds. It was invented by Ron Rivest and analyzed by RSA Laboratories [1324.1325].\There are three operations: XOR, addition, and rotations. Rotations are constantime on processors and variable rotations are a nonlinear function. These rotations, which depend on both the key and the data, are the interesting operation.

RC5 has a variable-length block, but this example will focus on a 64-bit data block. Encryption uses $2r+2$ key-dependent 32-bit words—$S_0, S_1, S_2, \dots, S_{2r+1}$—where $r$ is the number of rounds words later. To encrypt, first the plaintext block into two 32-bit words: $A$ and $B$. [RC5 assumes a littleendian convention for packing bytes into register $A$, etc.) Then:

```
$A = A + S_0$
$B = B + S_1$
```