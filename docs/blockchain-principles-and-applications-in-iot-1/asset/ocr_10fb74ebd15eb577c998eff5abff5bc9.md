# Cryptographic Foundations

# 237

+   - require less energy
- require less power
- have some latency
- provide better throughput
- side-channel resistance

Lightweight cryptography focuses on resource-constrained devices and tries to provide solutions that are tailored for them. There are ISO/IEC standards for lightweight crypto-graphic algorithms. Moreover, currently NIST is organizing a Lightweight Cryptography Competition to standardize one or more algorithms.

In symmetric cryptography, the keys used for encryption and decryption are the same or closely related. These encryption algorithms are mainly categorized as stream ciphers or block ciphers. Almost permissionless blockchains do not encrypt the blocks data is available for everyone. On the other hand, permitted blockchains may prefer encryption of the blocks. However, this means that additional measures must be taken in order to generate, distribute, and protect the secret key or keys.

Advanced Encryption Standard (AES) stands against cryptanalytic attacks after more than 20 years of investigation. Moreover, modern CPUs with hardware level AES instruction sets (e.g., Intel's AES-NI). Therefore, AES is arguably the first choice for the encryption of blocks in a blockchain. However, if the blockchain is going to be stored also in constrained devices, then using a lightweight cipher might be a better solution. There are three ISO/IEC standards for lightweight block ciphers: PRESENT, CLEFIA, and LEA. PRESENT was designed in 2009 by Bogdanov et. [36]. It is a hardware-oriented design focusing on a low hardware frontend. PRESENT is an SPN design. Its block size is 64 bits and supports 128 and 80-bit keys. PRESENT's two rounds are provided in Figure 13.3 and it consists of 31 rounds.

CLEFIA was designed by Shirai et. [37] and it is a software oriented algorithm. CLEFIA is a Feistel network. Its block size is 128 bits. It supports keys of size 128, 192, and 256 bits. The number of rounds for these key lengths are 18, 22, and 26, respectively. Details of CLEFIA are provided in Figure 13.4.

![](bbox=[0.104, 0.672, 0.896, 0.853])

FIGURE 13.3
Two rounds of PRESENT cipher. is drawn by Jeremy Jean and it is publicly available [15] under Creative Commons license CC0.