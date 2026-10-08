
# Enhancing Multicriteria Decision-Making

The proposed algorithm follows asymmetric key cryptography, which further enhances the security of the system. The authors also present a comparative analysis of the proposed algorithm with the traditional RSA algorithm, highlighting the improvements in security achieved by the enhanced version.

Meenakshi et al. [11] explored the use of effective domination and fuzzy vertex coloring in the context of cryptography and improved the security and effectiveness of cryptographic protocols, and Henry Rowland [12] performed integer factorization and primality testing to establish the use of RSA systems for data security. They determined that continuous study into integer factorization methods like Shor's algorithm and technological advancements, particularly quantum computing, could pose a significant danger to the security of the RSA cryptocurrency.

Ivy et al. presented a novel method that speeds up the operations of key generation and decryption by using three primes and the Chinese remainder theorem (CRT) for the RSA cryptocurrency, and the third integer RSA more sophisticated and secure. The algorithm includes message encryption, message decryption, and key generation, and Ivy et al. [13] proposed a modified RSA system based on $n$ primes to provide maximum security for data over the network. By using three primes rather than two, the suggested technique seeks to minimize the time required for key generation and raise the complexity of $n$ analysis [14–16].

Meenakshi et al. [17] presented a new combinatorial technique to encrypt and decrypt numbers using labeled graphs and domination theory. The technique involves splitting the secret number into partitions and assigning them to dominating vertices and edges in a graph. Tan et al. [18] sought strategies for improving the synergy between multicriteria decision making (MCDM) and building information modelling (BIM) in the architecture, engineering, and construction industry. Combining MCDM with BIM, they identified the major domains as sustainability, retrofit, supplier selection, and constructability. Tan et al. also discuss five strategies for improving the synergy between MCDM and BIM.

Aliams et al. [19] proposed a new RSA cryptystem based on fuzzy set numbers for encryption and decryption and showed that fuzzy theory is suitable for securing other systems and provides difficulty for attackers in communication. Kamardan et al. [20] proposed a modified multiple RSA system consisting of three phases: key generation, encryption, and decryption. The decryption phase utilized the CRT to expedite computation and found that decryption using multiple RSA was nearly four times faster than the standard RSA. Additionally, using multiple primes and additional secret keys increases the difficulty of breaking the security of the algorithm.

It is an intriguing idea to combine conventional RSA encryption with fuzzy logic, particularly, with trapezoidal fuzzy numbers (TFNs). The CRT allows for efficient computation by breaking down the RSA problem into smaller equations, reducing computational complexity, and enabling faster encryption and decryption. Furthermore, incorporating TFNS enables a more comprehensive representation of uncertainty in the encryption process, enhancing security attacks that exploit vulnerabilities in standard RSA methods [12,21,22].

In this chapter, we presented a detailed theoretical framework that integrates the CRT and TFNS into the RSA encryption algorithm. The main aim of this study is to maintain secure encryption while adding fuzziness or unpredictability to key generation considering uncertainties in prime number selection or exponent choices. Through mathematical formulations and algorithmic procedures, integrating these methodologies improved the computational efficiency and security in encrypting sensitive data.

# Multi-Criteria Decision-Making with Machine Learning

## 17.2 KEY GENERATION

- 1. Choose two distinct prime numbers. Select two large prime numbers, denoted as $p$ and $q$. These numbers should be randomly chosen and keep secret. Their multiplication will be part of the RSA algorithm.
- 2. Calculate the modulus. Compute modulus $n$ by multiplying the two primes: $n = p \times q$. The modulus is a part of both the public and the private keys.
- 3. Compute Euler's totient function. Calculate Euler's totient function $\phi(n)$, which is the number of positive integers less than $n$ that are coprime with $n$. For two distinct primes $p$ and $q$, $\phi(n) = (p-1) \times (q-1)$.
- 4. Choose an exponent. Select an integer $e$ that is relatively prime to $\phi(n)$. This will be part of the public key.
- 5. Calculate the private exponent. Compute private $d$ as the modular multiplicative inverse of $\phi(n)$. In other words, find a value $d$ such that $(d \times e) \mod \phi(n) = 1$. The value of $d$ is a part of the private key.
- 6. Create the public key. The public key consists of the modulus $(n)$ and the exponent $(e)$. This is the key that will be distributed to others for encryption.
- 7. Create the private key. The private key consists of the modulus $(n)$ and the private exponent $(d)$. This key must keep secret and not be shared.
- 8. Transform the message into cipher text. To enable encryption, the message must be transformed into a numerical representation. This is commonly referred to as “padding” and entails numeric value conversion from the plaintext message.

## 17.2.1 ENCRYPTION

The sender uses the public key to encrypt the message:

- a. Acquire the public key.
- b. Using the public key, represent the message as $m$.
- c. Use exponentiation to determine the cipher text $c^* = m^e \pmod{n}$.

## 17.2.2 DECRYPTION

The recipient uses the private key to decrypt the message:

- a. Acquire the private key.
- b. Using the private key, represent the cipher text $c$.
- c. Calculate $m = c^d \pmod{n}$.

## 17.3 ILLUSTRATION

- Choose six distinct prime numbers, say $p=17, q=19, r=23, s=29, t=31, u=37$.
