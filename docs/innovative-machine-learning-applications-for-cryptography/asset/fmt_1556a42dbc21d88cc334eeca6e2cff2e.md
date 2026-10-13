
Since then, HE has been a fast-developing field of research. Researchers have produced ever more effective and practical schemes. These technical breakthroughs have been brought about by the increasing importance of data privacy and security in areas from cloud computing to finance, healthcare, etc. Collaboration between cryptographers, mathematicians and computer scientists has characterized the development of HE.

Homomorphic Encryption now leads the way in search for secure data processing. In the age of big data and cloud computing, where privacy matters more than ever, this is seen as an essential technology ([A. Singla, N. Sharma 2022](#979-8-3693-1642-9.ch010.xhtml#r17)). Later in the sections dealing with HE, we will see how this technology is not just a concept but can actually be something that people could use to radically change our handling and processing of information.

## 2. HOMOMORPHIC ENCRYPTION TECHNIQUES

The initial idea behind cryptography was to create a system that could guarantee safe communication between various entities. One side encrypts a message and sends it to the other, who can decode it ([A. Singla, N. Sharma 2022](#979-8-3693-1642-9.ch010.xhtml#r17)). The idea of doing calculations on encrypted data was first proposed as a “privacy transformation” in 1978 by Rivest, Adleman, and Dertouzos. What is currently known as homomorphic encryption developed out of this idea over time. Homomorphic encryption, in a wide sense, allows us to compute on encrypted data. If a scheme has the following characteristics, we say that it is additively (or multiplicatively) homomorphic:

```
[x] ⊕ [y] = [x + y] and [x] ⊗ [y] = [x · y]
```

In this context, the letter `[⊗]` stands for the plaintext value's encryption, while the characters `⊗` and `·` denote the homomorphic operations of addition and multiplication carried out in the ciphertext space. If an encryption system is additively homomorphic, then encrypting data before adding it is equivalent to adding the data before encryption, to put it more simply. Figure 1 shows this idea in action.

### Partially Homomorphic Encryption (PHE)

Partially Homomorphic Encryption schemes are specialized to allow specific types of operations on encrypted data. These schemes can perform either addition or multiplication, but not both ([G. Karatas, O. Demir and O. K. Sahingoz, 2019](#979-8-3693-1642-9.ch010.xhtml#r6)). A prominent example is the `RSA` encryption, which exhibits multiplicative homomorphic properties. In PHE, if you encrypt two numbers and multiply their ciphertexts, the result, when decrypted, will be the product of the original numbers. PHE is relatively more efficient than its more advanced counterparts and forms the basis of many early applications of homomorphic encryption.

| Figure 1. Concept of Homomorphic Encryption |
| --- |
| ![Figure979-8-3693-1642-9.ch010.f01](i/ch010.f01.png) |

### Somewhat Homomorphic Encryption (SWHE)

Somewhat Homomorphic Encryption is an extension of PHE. SWHE schemes can perform a limited number of both addition and multiplication operations on ciphertexts. The limitation arises from the fact that every homomorphic operation introduces a small amount of noise into the ciphertext, and this noise accumulates with each operation (A. Sharma, K. S and M. R. Arun, 2022). Once the noise reaches a certain threshold, the ciphertext becomes too corrupted to be reliably decrypted. SWHE is a critical stepping stone towards fully homomorphic encryption, offering more flexibility than PHE while still being constrained by the noise buildup.

Supporting Single Instruction Multiple Data (`SIMD`) operations, Smart and Vercauteren presented a Secure Homomorphic Encryption (`SHE`) technique in an independent research. By using a method known as ciphertext packing, this feature enables Fully Homomorphic Encryption (`FHE`) to achieve parallelization. The encoding of several plaintext values into a single the ciphertext vector is an example of how `SIMD` instructions improve computing performance. One of the main uses of ciphertext packing is in batch calculation, which is a common feature of many `FHE` algorithms. In addition, it permits the reordering of plain slots within a packed ciphertext, which may result in enhanced evaluation speed. Figure 2 is a graphical representation of these ideas ([M. N. Reza, and M. Islam, 2021](#979-8-3693-1642-9.ch010.xhtml#r14)); it shows a vector with several values within it, which may be processed with a single command and their slots may be rearranged for different uses.

| Figure 2. Secure Homomorphic Encryption (SHE) |
| --- |
| ![Figure979-8-3693-1642-9.ch010.f02](i/ch010.f02.png) |

At its most sophisticated, Fully Homomorphic Encryption (`FHE`) protects data from prying eyes. The amount of additions and multiplications that may be performed on encrypted data is limitless. The breakthrough achievement of `FHE` is its ability to manage and control the noise accumulation that plagues `SWHE` schemes (Kumar, Pullela SVVSR, & Chaturvedi, Abhay, 2023). This is accomplished by a method called `bootstrapping`, which serves to lower the noise level and permits continuous computation. Since its start, `FHE` has been a major area of research. Constant work is being done to make it more practical in terms of efficiency and computational resources.

### Mathematical Foundations of Homomorphic Encryption

HE's mathematical basis lies in number theory and algebra (Kumar, R & B. Ashreetha, 2023). In fact, the essence of HE utilizes complex mathematical concepts including lattice-based cryptography; ring theory and polynomial arithmetic. These mathematical foundations allow the operations on encrypted data to be carried out in a secure and stable manner.

| Figure 3. Simplified Overview of Single-Scheme FHE Protocol |
| --- |
| ![Figure979-8-3693-1642-9.ch010.f03](i/ch010.f03.png) |
