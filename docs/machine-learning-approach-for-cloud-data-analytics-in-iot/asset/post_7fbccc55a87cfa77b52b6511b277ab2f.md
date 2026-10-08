
## 7.4 Classical Cryptography for Cloud Computing

In this section, the detailed study of existing classical cryptography mechanisms such as RSA, AES, DES, and Blowfish have been studied.

### 7.4.1 RSA

RSA is asymmetric key cryptography where the public key is being used for the encryption process and the private key is used for the decryption process. There are three different stages known as Key Generation Phase, Encryption Phase, and Decryption Phase [35].

Key Generation

- 1. Select two prime numbers P and Q
- 2. Find $N = P \times Q$
- 3. Calculate $\varphi\left(N\right) = (P - 1) \times (Q - 1)$
- 4. Select e such that $gcd(\varphi\left(N\right), e) = 1$
- 5. Calculate $d = e^{-1}\, mod\, \varphi\left(N\right)$
- 6. Choose e as public key and d as the private key

Encryption process
Let M be the plain text that is to be stored and C as the calculated ciphertext. Then, C can be calculated as follows:

- 1. $C = M^{e}\, mod\, N$

Decryption process
The plain text M can be retrieved back from the ciphertext C as follows:

- 1. $M = C^{d}\, mod\, N$

### 7.4.2 AES

AES works on a block of 128 bits data with three different key sizes such as 128, 192, and 256 bits [32, 33]. It has four different stages as follows:

- Substitution Byte: Each bit of the plain text is being replaced with the substitution bit from the 8-bit S BOX.
- Shift Row: It is being operated on a row basis. Elements of each row are shuffled by a certain offset. The first row will be remaining unchanged, elements of the second row will be shifted 1 bit left, the element of the third row will be shifted 2 bits left, and similarly, the elements of the fourth row will be shifted 3 bits left.
- Mix Column: In this stage, each column will be mapped with a linear function to reform a new input matrix.
- Add Rounded Key: In this step, the subkey is XORed with the input matrix to obtain the ciphertext.

In the case of the encryption, the above-said processes are executed serially, but in the case of decryption, the above-said process is executed in the reverse order.

### 7.4.3 DES

It utilizes 16 rounds of Feistel cipher structure with the input plain text size as 64 bits. It divides the whole plain text into two equal blocks each of 32 bits. For the encryption process, it makes the uses of a rounded key generator which takes a 48 bits sub-key out of 56 bits of the available key. With one block the sub-key is being combined and the other one will be kept as same for getting the next block of text. The sub-block size is 32 and the subkey size is 48 bits, so the DES uses a P-BOX which expands the block size from 32 bits to 48 bits. After the operation, the expanded block is again compressed into 32 bits with the help of S-Box. This process is repeated 16 times to obtain the ciphertext.

### 7.4.4 Blowfish

Blowfish is an alternative for the DES algorithm. In this protocol, variable key size starting from 32 bits to 448 bits is taken for each cycle to obtain the ciphertext. The input block size for the Blowfish technique is 64 bits. This is getting popularity because it is unpatented and freely available for all-purpose.

## 7.5 Homomorphic Cryptosystem

In this section, two homomorphic encryption techniques such as Pailler and RSA have been studied. Both strategies are partial homomorphic. RSA supports multiplicative homomorphic property, whereas Paillier supports the additive homomorphic property.

### 7.5.1 Paillier Cryptosystem

It was invented by Paillier in 1999. It is public-key cryptography which supports the additive homomorphic property. It has three phases known as key generation, encryption, and decryption phase [34].

Key Generation

- 1. Select two prime integers P and Q
- 2. Calculate N = P × Q
- 3. Calculate $\lambda = \text{lcm}(P - 1, Q - 1)$
- 4. Find g as $gcd(L(g^{\lambda} \bmod n^2), n) = 1$

L can be defined as $\frac{x-1}{n}$, x is the plain text.

- 5. Calculate $\mu = L(g^{\lambda} \bmod n^2)^{-1} \bmod n$
- 6. Public key = (n, g) and private key = ($\lambda, \mu$)

Encryption

- 1. M is the plain text
- 2. Choose r as a random integer such as $0 < r < n$
- 3. $C = g^M r^n \bmod n^2$

Decryption

- 1. $M = L(C^{\lambda} \bmod n^2) \cdot \mu \bmod n$

#### 7.5.1.1 Additive Homomorphic Property

Let E is encryption function and M1 and M2 are two plain texts available for encryption then

$E(M1 + M2) = E(M1) + E(M2)$

C1 and C2 are two ciphertexts for M1 and M2, respectively, with two random variable r1 and r2, then

$C1, C2 = g^{(M1 + M2)} (r1 \cdot r2)^n \bmod n^2$

### 7.5.2 RSA Homomorphic Cryptosystem

Key Generation [35]

- 1. Select two prime numbers P and Q
- 2. Find $N = P \times Q$
- 3. Calculate $\phi(N) = (P-1) \times (Q-1)$
- 4. Select e such that $gcd(\phi(N), e) = 1$
- 5. Calculate $d = e^{-1} \bmod \phi(N)$
- 6. Choose e as public key and d as the private key

Encryption process
Let M be the plain text that is to be stored and C as the calculated ciphertext. Then, C can be calculated as follows:

- 1. $C = M^{e} \bmod N$

Decryption process
The plain text M can be retrieved back from the ciphertext C as follows:

- 1. $M = C^{d} \bmod N$

#### 7.5.2.1 Multiplicative Homomorphic Property

Let E be the encryption function and M1 and M2 are two plain texts available for encryption, then

$E(M1, M2) = E(M1) \cdot E(M2)$

C1 and C2 are two ciphertexts for M1 and M2, respectively, then

$C1, C2 = (M1 \cdot M2)^{e} \bmod n$

## 7.6 Implementation

In this research article, the authors have tried to implement classical RSA, Paillier homomorphic, and RSA homomorphic mechanism in the java environment. The time taken to compute some update operation on the stored data is being calculated and shown that the run time of the homomorphic encryption technique is much faster than classical cryptography. The memory analyzer is being used to measure the memory used by this above-said algorithm while in operation. The above-said algorithms have been implemented in java with a system having 8-GB RAM, Windows 10 OS, and 1-TB HDD, and the ECLIPSE JVM memory analyzer has been used to track the memory used by the algorithms. Security, IO, and UTIL packages of java need to be imported to execute algorithms successfully. Figures 7.2 and 7.3 shows the runtime and memory utilization comparison of classical RSA, Paillier homomorphic encryption and homomorphic RSA algorithms respectively.

![](img/cbc35e0d02425baa6028b87d56263a7f_182_0.png)

**Figure 7.2** Runtime for CRSA, Pallier HE, and RSA HE.

![](img/cbc35e0d02425baa6028b87d56263a7f_182_1.png)

**Figure 7.3** Memory analyzer for CRSA, HE RSA, and HE PAILLIER.

## 7.7 Conclusion and Future Scope

This research work has been carried out to investigate the characteristics of classical cryptography and homomorphic cryptosystem. While doing some operation on the stored data in classical cryptography, the time taken to compute is more as compared to the HE cryptosystem. Since in the case of classical cryptography, the cipher text has to be decrypted first and then only the operation is possible, therefore the time of computation is high. Unlike classical cryptography, the HE cryptosystem allows the user to operate on the ciphertext itself which helps to reduce the computational time. In this work, the author has implemented classical RSA along with HE RSA and HE Paillier for doing multiplication or addition after encryption. The result shows that the time for classical RSA is higher as compared to the other two. In this work, we have also discussed the importance of cryptography in cloud computing along with the disadvantage faced in classical cryptography which is being removed by applying the homomorphic cryptography.

The computation time of RSA and Pallier HE cryptosystem depends upon the key size. If the key size is more, the computation time and cost will also increase severely. The future scope of this work is to reduce the time complexity of the HE cryptosystem while applied to a cloud computing environment.

## References

- 1. Wang, G. and Ng, T.E., The impact of virtualization on network performance of amazon ec2 data center, in: 2010 Proceedings IEEE INFOCOM, 2010, March, IEEE, pp. 1–9.
- 2. Wilder, B., Cloud architecture patterns: using microsoft azure, O’Reilly Media, Inc., North Sebastopol, CA, 2012.
- 3. Serrano, N., Gallardo, G., Hernantes, J., Infrastructure as a service and cloud technologies. IEEE Software, 32, 2, 30–36, 2015.
- 4. Zhou, T., Shen, J., Li, X., Wang, C., Shen, J., Quantum cryptography for the future internet and the security analysis, in: Security and Communication Networks, 2018.
