
![](img/6e4271af21d9a195003ab8711aa79d27_284_0.png)

Figure 13.1 Proposed ME-AES method.

questions. The smart assistant receives the inquiries in encrypted form. IBE requires both the user's email address and the serial number of the device to which it is tied for it to function effectively. AES and Twofish are used to encrypt sensitive data, whereas AES is used to secure common data. This layered design provides substantially more efficient and rapid data security.

## 13.3.1 Uploading voice

Objects and keywords can be split as two independent components of a data structure throughout the voice uploading process. An “object” is the data from the user that will be transferred to the server. Class and attribute names can be used to identify an item. Each pair is represented on the server by a unique copy of the data set (objects and keywords) that it represents. The items are specifically encrypted and stored on the server. In contrast, the keywords are now recorded on the server as hidden attributes. Items and keywords may have many-to-many relationship. As a result, a keyword may be associated with many objects, or multiple items may be related to a keyword. For example, “apple, fruit” has two distinct meanings: “apple” refers to an item, while “fruit” refers to the class to which the object belongs. If the phrase “Apple, Red” is repeated, the server will append the latest crucial phrase “Red” to an item already identified as “Apple.” During upload, the keyword is extracted using an obfuscation method using the Mel Frequency Cepstral Coefficient (MFCC). These two events happen at the same time. As a result, before sending the ciphertext to the server, this function encrypts the data to protect the privacy of users’ sensitive data.

## 13.3.2 Retrieving voice

A user initiates the voice retrieval process by sending a query command to a server, which is followed by the ensuing activities. Home IoT Voice System (HIVOS) is initially given the keyword and query instructions. After HIVOS and masking have extracted features, the server receives them in an obscured state. The response is arranged in increasing order depending on the distance between these features within the encrypted response. After completion, HIVOS receives the response with the least encrypted distance. The user will receive the original, unencrypted content once HIVOS decrypts the encrypted version using AES. As a result, the user will hear the response.

## 13.3.3 Multi-layer feature characterizations

Smart home IoT devices are capable of a wide range of processing, storage, and communication functions. Bridges support IoT wireless protocols and TCP/IP and can connect to battery-powered devices like motion and water leak sensors. Smart TVs and Amazon Echoes use electricity and connect to the internet wirelessly or wired via household routers.

IoT Argos investigates a range of multi-layer properties derived from wireless packets gathered by sniffers and TCP/IP-based network flow records recorded by the SoftFlowd. Because most Internet of Things apps and services used in smart homes encrypt data transfers, IoT Argos focuses on behavioral elements such as data volumes, length, protocols, and remote end systems.

## 13.3.4 Identity-based encryption

The sender can encrypt communication using the recipient’s identification in identity-based encryption systems. These benefits were initially emphasized. As a result, there is no longer a need for a centralized system to control the generation and distribution of public keys. An IBE scheme requires a trustworthy central authority. This is critical for us to achieve our goal.

Because the central authority of the IBE scheme has access to every private key, it is obvious that this type of scheme cannot guarantee non-repudiation. Remember that private keys must be securely held on the client or user's end or handed to them. This could be accomplished in the IoT by affixing a secret code put in the gadget during manufacturing or configuration.

The MasterKeyGen algorithm, the UserKeyGen method, the encryption strategy, and the decryption algorithm are used in IBE systems. UserKeyGen generates the ID, user private key, and master secret key, whereas MasterKeyGen generates the authority's key pair. Only the decryption and encryption algorithms must be run on the user's device; all other operations may take place in the secure environment supplied by the regulating body. It is possible to establish security proofs for a wide range of difficult situations using IBE systems. These issues include Ring Learning with Errors (RLWE) and the Bilinear Diffie-Hellman assumption [35, 36].

To implement the IBE approach and to evaluate its suitability for application to embedded Internet of Things devices. We present an overview of the necessary technical background here; the original work should be read for a more detailed explanation of the technical aspects and security proof. The master key must be generated by the central authority using the MasterKeyGen technique, which is detailed below (Algorithm 1). The entire cryptographic setup of the IBE system is determined by this way.

### ALGORITHM 1: Master Key Generation

```
1. MasterKeyGen()
2. do
3. k, l ← D_{σ_E} ▷ σ_E = 1.17√(q / 2n)
4. while max(‖(l, -k)‖, ‖( qk/(f×f + g ḡ), q l̄/(f×f + g ḡ) )‖) > 1.17√q
5. Use extended Euclidean algorithm to compute ρ_k, ρ_l ∈ R and R_k, R_l ∈ Z such
6. ρ_k·k = R_k mod x^n + 1 and
7. ρ_l·l = R_l mod x^n + 1
8. If (GCD(R_k, R_l) ≠ 1 or GCD(R_k, q)≠1) Restart
9. Use extended Euclidean algorithm to compute u, v ∈ Z such that u·R_k + v·R_l = 1
10. K ← q v ρ_l
11. L ← q u ρ_k
12. o ← [ (K × k̄ + l × l̄) / (k × k̄ + l l̄) ] ∈ R
13. K ← K - o × k
14. L ← L - o × l
15. h←l×k⁻¹ mod q
16. B ← ( A(l) - A(k) 
    A(L) - A(K) )
17. Return (s0, p0) = (B, h)
18. End
```

In order to produce a unique secret key for each user or device, the governing body will employ the UserKeyGen technique represented in Algorithm 2. This method is normally performed only once per embedded device during a secure system configuration phase.

### ALGORITHM 2: User Key Generation

```
1. UserKeyGeneration
2. t ← H(ID) ∈ Z_q^n ▷ H() is a hash function.
3. s1, s2 ← (t,0) - GaussianSampler(B,σ,(t,0))
4. Return s0_ID = s2
5. end
```

We will ignore the MasterKeyGen and UserKeyGen computations for field-installed embedded devices to pay attention to the following encryption and decryption methodologies for our implementation. As a result, we can disregard these computations (Algorithms 3 and 4, respectively). Encryption and decryption necessitate the use of three procedures: polynomial sampling, polynomial multiplication, and threshold encoding. An n-bit message can be transformed to a [0, 1] polynomial using the threshold encoding procedure. The polynomial has been encoded after being multiplied by q12 many times. The error-prone message polynomial [q/4, 3q/4] is obtained at completion of the decryption process. In this case, unlike in prior cases, the ciphertext bit will be set to 1.

## 13.3.5 BLAKE2 hash algorithm

The improved version of SHA-3, BLAKE2, decreases program performance. These techniques are used in cloud storage, versioning, detection, and intrusion detection. BLAKE2b and BLAKE2s are available for 64-bit platforms and smaller architectures, respectively. BLAKE2 consumes 32% less RAM than BLAKE thanks to its efficient MAC node and tree-hashing mode.

BLAKE2 carries out the following tasks: MasterKeyGen and UserKeyGen will not be used in our solution because they will not be implemented on field-deployed embedded devices. Instead, we will concentrate on encryption

and decryption (Algorithms 3 and 4). Encipherment and decipherment will be discussed (Algorithms 3 and 4, respectively). Data encryption and decryption use threshold encoding, polynomial multiplication, and equally distributed ternary polynomials. A threshold encoding converts an n-bit message into a [0, 1] polynomial with n coefficients. The polynomial is encoded using the q12 technique. Use of polynomial decryption errors are then added to this polynomial, and each coefficient must match [q/4, 3q/4]. Otherwise, if the answer is no, set the ciphertext bit to 0.

- 1. Initialization: A 16-word state initialized so that different inputs result in different initial states.
- 2. Iteration of the Round Function: The round function will iterate 14 or 16 times (BLAKE-256) (BLAKE-512).
- 3. BLAKE only employs one basic function, the G function. The G function is repeated 128 times in BLAKE 512, compared to 112 times in BLAKE 256 (a 32-bit word) (64 bit word). Each column must be subjected to the G function. Apply the G function to each diagonal member in parallel.
- 4. Conclusion: The information supplied can be used to calculate a new chain value.

## 13.3.6 Advanced Encryption Standard (AES)

The Data Encryption Standard (DES), developed by the National Institute of Standards and Technology, was recommended for adoption. In 2001, the National Institute of Standards and Technology (NIST) replaced DES with the Advanced Encryption Standard (AES). Any database collection could benefit from AES. Prior to creating the encoded message, AES supports data lengths of up to 128 bits, with each bit split into at least four active basic blocks. Following processing as a single line of bytes, these elements are concatenated to generate the state, which is a 4 × 4 matrix. The initial phase in both encoding and decoding a cypher is the “Add round key stage.” To get to the final round, the output must first go through the first nine fundamental rounds, where it experiences the four transformations listed below: The four subsequent actions are as follows: (1) adding a round key, (2) shifting rows, (3) mixing columns, and (4) sub-bytes. It is unable to use the mix column transformation in the ninth and final round. The full procedure is depicted in great detail in Figure 13.2. The inverse of encryption, decryption performs the opposite procedures:

### 1. Sub-byte

The AES key is a data block of 128 bits. Each record in the database is made up of 16 bytes. The Rijndael S-box is an 8-bit substitution box used to change the sub-byte. Using this box, each data byte is transformed into a separate component during this transformation.
