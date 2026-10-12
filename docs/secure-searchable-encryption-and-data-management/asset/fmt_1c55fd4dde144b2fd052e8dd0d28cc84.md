
# DES (Data Encryption Standard)

DES was designed by Horst Feistel in early 1970 at IBM and named Lucifer. In 1976, the National Bureau of Standards (NBS) adopted a variant of Lucifer submitted by IBM as a federal standard and called it DES with a key length of 56 bits and a block length of 64 bits. In 1997, DES was broken by an exhaustive search where all the `2^(56)` combinations of keys were tried to find the challenge key. After DES was broken, the first thing that came to the mind of experts was to strengthen DES against an exhaustive key search attack by artificially expanding the key size. As a result, triple-DES (3DES) was invented. The idea was to iterate DES a couple of times. 3DES uses three independent keys, each of length 56 bits, which makes the key size equal to 168 bits (`56×3`), but it is three times slower than DES. Now, the question is, why not double DES? If 2DES is used, then there exists an attack called meet-in-the-middle which can try `2^(112)` in a minimal time approximately equal to the exhaustive search attack on DES. DES was a widely used and popular cipher in banking and commerce until the year 2000 when AES completely replaced DES.

# AES (Advanced Encryption Standard)

AES is a substitution-permutation network (SPN) and unlike the Feistel network where half of the bits remain unchanged from round to round, in SPN all the bits are changed in every single round. AES comes with three key options: 128 bits, 192 bits, and 256 bits, and the block size is fixed to 128 bits. The larger the key size the more secure is the resulting cipher; however, the number of rounds will increase with the increase in key size thus making the cipher slower. But it is still six times faster than the 3DES standard and hence completely replaced DES and is a widely used standard nowadays.

## 2.2.3 Based on the Type of Key

On the basis of the type of the keys used for encryption and decryption, ciphers are categorized into symmetric and asymmetric ciphers. In symmetric ciphers the same key is used for both encryption and decryption while in asymmetric ciphers different keys are used for encryption and decryption. Examples of symmetric ciphers are block and stream ciphers and all the classical ciphers; in the asymmetric category the most famous and foremost is the cipher developed by Rivest, Shamir and Adleman (RSA algorithm). We will discuss the famous asymmetric ciphers in the section where we discuss public-key encryption techniques.

## 2.3 Types of Cryptographic Techniques

In this section, we will discuss the symmetric and asymmetric or public-key cryptographic techniques. However, the main focus will be on public-key cryptographic techniques, as we later discuss the searchable encryption schemes based on public-key cryptographic primitives.

In a typical cryptosystem, there are three main components: the key-generation algorithm, the encryption algorithm and the decryption algorithm. The role of the key-generation algorithm mainly comes in public-key cryptosystems. In symmetric-key cryptosystems the sender and the receiver of the message must agree upon the common secret key used for both encryption and decryption. For this purpose, some key-exchange algorithm must exist and one such algorithm which gained a lot of popularity is the Diffie–Hellman key-exchange algorithm [[6]](#02chap_02.xhtml#ref2_6). To understand this algorithm, let us assume the famous Alice and Bob scenario where Alice wants to securely communicate with Bob. The key-exchange process between them is shown in [Figure 2.2](#02chap_02.xhtml#fig2_2). Alice and Bob select the public parameters (`p`, `α`) which are known to everyone.

![Figure 2.2 Diffie–Hellman key-exchange algorithm.](images/fig2_2.jpg)

*Figure 2.2* Diffie–Hellman key-exchange algorithm.

The public parameters which Alice and Bob decided are the order, `p`, of the cyclic group, `Z[p]`, and the generator, `α`, of the group. In the second step shown in [Figure 2.2](#02chap_02.xhtml#fig2_2), Alice and Bob are randomly choosing one element from the cyclic group and keep them as their secrets.

The Diffie–Hellman key-exchange algorithm suffers from man-in-the-middle attack, where a third person intercepts all the secret messages by computing a shared secret key of its own and sending that shared secret key to both Alice and Bob. The details of this attack are left for the reader as it is readily available in any standard cryptography book. The purpose of describing the Diffie–Hellman key-exchange algorithm is to demonstrate its significance in the development of public-key cryptosystems.

The symmetric-key cryptographic techniques are much faster than public-key cryptographic techniques. On the other hand, symmetric-key techniques require the process of sharing the secret key, and this process becomes quite complicated when a large number of users want to communicate together. Take the example of cloud storage where a large number of users participate and want to share their data among themselves; in this scenario, public-key cryptography is the better choice. The searchable encryption schemes that we will discuss in the subsequent chapters are developed for cloud storage and multi-user environments. Therefore, to better understand, we need to build a strong base in the public-key cryptographic techniques.

### 2.3.1 Public-key Cryptography

Public-key cryptography [[4]](#02chap_02.xhtml#ref2_4), also called asymmetric cryptography, contains a group of algorithms that use two different but related keys, one is used for encryption (which is called the public key) and the other is used for decryption (which is called the private key). Public-key cryptography contains the public-key encryption and signature scheme, but we will mainly focus only on the encryption schemes. In the encryption scheme, anyone who wants to communicate with someone can encrypt the message using the public key of the recipient and the recipient will use his/her corresponding private key to decrypt that message. Since the private key is only possessed by the recipient, no one else can decrypt that message. In the signature scheme, this process is inverted, to generate the signature the private key is used and to verify the signature the corresponding public key is used. The signature scheme is used to prove the authenticity and integrity of the message [[7]](#02chap_02.xhtml#ref2_7), [[8]](#02chap_02.xhtml#ref2_8), [[9]](#02chap_02.xhtml#ref2_9), and [[10]](#02chap_02.xhtml#ref2_10). The private key is used to generate the signature of the message, which guarantees that indeed the sender has sent the message. No one can change the contents because they do not possess the private key of the original sender and therefore cannot re-encrypt the modified content of the message without revealing it to the recipient.

The public-key encryption algorithm is composed of three algorithms: the key-generation algorithm, `KG`, the encryption algorithm, `E`, and the decryption algorithm, `D`. The key-generation algorithm takes the security parameter, `λ`, and generates the public and private key pair, (`pk`, `sk`). The encryption algorithm takes the message, `m ∈ M` (message space) and encrypts it using the public key, `pk`, to generate the ciphertext, `C`. The decryption algorithm takes the ciphertext and the private/secret key, `sk`, corresponding to the public key and outputs the message, `m`. The decryption algorithm is obviously deterministic while the key-generation and the encryption algorithms are non-deterministic. The correctness of these algorithms can be defined as:

```
∀ m ∈ M & ∀(pk, sk) ←$ KG(λ), D(sk, E(pk, m)) → m
```

#### 2.3.1.1 Security Models
