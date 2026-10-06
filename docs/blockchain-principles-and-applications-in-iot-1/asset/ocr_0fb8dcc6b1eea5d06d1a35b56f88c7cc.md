# Lightweight Cryptography and Protocols

# 279

# 15.3 Motivation of Work

Today, our world is rapidly advancing towards the transformation of a smart and fast generation. In this smart world, a huge number of smart devices are connected to communicate between human to machine or human to human for faster transferring of data with security. But the constraints of a smart environment have reinforced another, the idea of lightweight cryptography. The National Institute of Standards and Technology (NIST) and International Organization for Standardization/International Electromechanical Commission (ISO/IEC) standardized a number of methods for lightweight cryptography in an IoT domain. To maintain security with all constraints in mind, various lightweight primitives and protocols have originated.

Under lightweight cryptography, the ISO/IEC 29192-5:2016 standardized PHOTON and SPONGENT as standard hashing methods, ISO/IEC 29192-2:2012 represent PRESENT and CLEFIA as standard block cipher method. The stream Trivium was also selected by the ISO/IEC 29192-3:2012. In this paper, these standard methods have been discussed. The others are selected for their wide acceptance in the industry. The three lightweight protocol selections are based on the strength of instant data transfer or variability of their industry usage or the popularity of multicast support.

# 15.4 Lightweight Block Cipher

One of the important lightweight cryptographic primitives is lightweight block cipher. Lightweight block ciphers belong to the symmetric key encryption category, which is operated on fixed length of bits. This primitive includes straightforward operations. Two types of networks are used to implement these types of ciphers. One is substitution and permutation networks (SPN) and the second one is the Feistel network. SPN uses substitution boxes (S-boxes) and permutation boxes (P-boxes) in each round for network implementation. Some mathematical operations with the key can convert a block of plaintext to a block of cipher text. The advantage of a Feistel cipher lies in its symmetric structure. Here, the encryption and decryption functions are almost the same except for the key scheduling method. Here, to achieve low latency, the implementation code can be reduced by 50%. Some of the popular lightweight block ciphers are discussed below.

# 15.4.1 PRESENT

An ultra-lightweight block cipher, PRESENT [9] is based on a substitution permutation network (SPN) structure. It has 31 iteration rounds including block size of 64 bits. PRESENT supports 80-bit and 128-bit key variants. This cipher has three different layers in each round. Figure 15.2 displays the block diagram (including layers) of PRESENT cipher.

Substitution layer: this first layer comprises 16 S-boxes where an individual S box has 4 bits of inputs and 4 bits of outputs; 16 parallel applications using 4-bit S-boxes have been done here.