# Simple Hash Functions

A hash operates on an input of any length (there are some limitations, but the message sizes are huge) and generates a fixed-length output. The simplest hash merely divides the input message into fixed-size blocks and then XORs every block. The hash would therefore be the same size as a block.

```
Hash = block 1 block 2 block 3 ... end of message
```

# MD5 Message Digest Algorithm

MD5 was developed by Ron Rivest at MIT in 1992. It is the most widely used hashing algorithm and is described in RFC 1321.148 MD5 generates a 128-bit digest from a message of any length. It processes the message in 512-bit blocks and does four rounds of processing. Each round contains 16 steps. The likelihood of finding any two messages with the same hash code is estimated to be 264, and the difficulty of finding a message with a given digest is estimated to be 2128. One common use of MD5 is to verify the integrity of digital evidence used in forensic investigations and ensure that the original media has not been altered since seizure. In the past two years, there have been several attacks developed against MD5 where it is now possible to find collisions through analysis. This is leading to many professionals recommending the abandonment of MD5 for use in secure communications, such as digital signatures. MD4 was developed in 1990 and revised in 1992. It only does three rounds of processing and fewer mathematical operations per round. It is not considered strong enough for most applications today. It also generated a 128-bit output. It is a predecessor to MD5.

# Secure Hash Algorithm (SHA) and SHA-1

The original SHA was developed by NIST in the United States in 1993 and issued as Federal Information Processing Standard (FIPS) 180. A revised version (FIPS 180-1) was issued in 1995 as SHA-1 (RFC 3174).149 SHA was based on the MD4 algorithm, whereas SHA-1 follows the logic of MD5. SHA-1 operates on 512-bit blocks and can handle any message up to 264 bits in length. The output hash is 160 bits in length. The processing includes four rounds of operations of 20 steps each. Recently, there have been several attacks described against the SHA-1 algorithm despite it being considerably stronger than MD5. NIST has issued FIPS 180-4, which recognizes SHA-1, SHA-224, SHA-256, SHA-384, SHA-512, SHA-512/224, and SHA 512/256 as a part of the Secure Hash Standard. The output lengths of the digests of these vary from 160 to 512 bits.150

# SHA-3

In November 2007, NIST issued an invitation for candidate algorithms for new hash