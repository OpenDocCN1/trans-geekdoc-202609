
Upon receiving the message, the recipient can then decrypt it using their private key to read the original message. By following these steps, public key cryptography can provide secure communication while ensuring that only the intended recipient can read the message.

## Public key cryptosystem applications

Public key cryptography is considered highly crucial in the fields of secure communication methods and identity verification mechanisms across digital platforms. It has various applications and some of the prominent ones among them are as follows:

*   **Decryption/encryption**: If the objective of an application is to encode and decode the message, then the sender must encode the message using the intended recipient’s public key, and the recipient can decode the message using their own private key.
*   **Authentication**: It can certify that the message or user is legal or not. Authentication represents that users are who they request to be. Availability describes that resources are accessible by authorized parties such as denial of service attacks, which are the sensitive matter of national information, are attacks against availability.
*   **Digital signature**: When the primary goal of an application is to confirm the authenticity of the sender, a digital signature can be used. This involves encrypting or signing the message using the private key of the sender. Since only the sender has access to their private key, it assures all parties involved that the message is indeed sent by that particular individual.
*   **Key generation**: Each user generates two keys including public key and private key. The private key is maintained at user side and public key is freely accessible in the network.
*   **Verification**: The signed signature is verified by the public key of concerned user.

## RSA

RSA is named after its creators, Rivest, Shamir, and Adleman. It is an asymmetric cryptographic algorithm that facilitates the generation of public and private keys. RSA enables key exchange, where each party involved in a transaction is assigned their own set of public and private keys. Subsequently, a symmetric key is generated and securely communicated using the public/private key pairs. Asymmetric encryption, although typically slower than symmetric encryption and less scalable, is commonly employed for securely exchanging symmetric keys.

RSA uses an asymmetric cryptographic algorithm which works on a block cipher concept that converts plain text into ciphertext and vice versa at the receiver side. If the public key of User A is used for encryption, we have to use the private key of the same user for decryption.

To implement the RSA encryption algorithm, the following steps are taken:

1.  First, two prime numbers `X` and `Y` are selected. These prime numbers must be large to ensure security.
2.  The product of the two primes, denoted as `N = X*Y`, is calculated. This product forms the basis of the encryption algorithm.
3.  Next, a public key `E` is chosen. It must not be a factor of `(X-1)` and `(Y-1)`.
4.  A private key `D` is selected such that the equation `(D * E) mod (X-1) * (Y-1) = 1` holds true.
5.  For encryption, the ciphertext `CT` is calculated as `CT = (plaintext)^E mod N`. The resulting `CT` is then sent to the receiver.
6.  Finally, for decryption, the plaintext `PT` is calculated as `PT = (ciphertext)^D mod N`.

These steps form the basis of the RSA encryption algorithm, which is widely used in secure communication systems due to its effectiveness in ensuring confidentiality and authenticity.

> **Note**: In the RSA algorithm, selecting and generating a public key and the private key is a critical task.

## El Gamal cryptography algorithm

It is a public key cryptography algorithm. This cryptosystem is based on the difficulty of finding discrete logarithm in a cyclic group; that is, even if we know `ga` and `gk`, it is extremely difficult to compute `gak`.

*   Start by selecting two large prime numbers, `P` and `Q`, with `P` being the public key and `Q` being the private key.
*   Choose the second encryption key as `E1`.
*   Compute the third encryption key, `E2`, such that `E2 = E^Q mod P`, for El Gamal key encryption.
*   Select a random number, `R`.
*   Calculate the ciphertext as `CT = E1^R mod P`.
*   Calculate the second ciphertext as `CT2 = (PT * E2^R) mod P`, for El Gamal key decryption. Finally, compute the plaintext as `PT = (CT2 * (CT^Q)^-1) mod P`.

## Elliptic Curve Cryptography

Elliptic Curve Cryptography (ECC) is a contemporary family of public-key cryptographic systems, utilizing the algebraic structures of elliptic curves over finite fields and the Elliptic Curve Discrete Logarithm Problem (ECDLP) complexity. ECC provides all fundamental capabilities of asymmetric cryptosystems, including encryption, digital signatures, and key exchange. It is regarded as a natural successor to the RSA cryptosystem, thanks to its use of smaller keys and signatures that offer the same level of security as RSA but with faster key generation, key agreement, and signature processing speeds. Refer to Figure 1.8 which deciphers how ECC functions.

![](images/Figure_1.8.png)

Elliptic curves are utilized to create encryption schemes. They are defined over a special field and are discontinuous curves, meaning that they consist of a finite set of points. Elliptic curve cryptography forms the foundation of decentralized trust when transmitting and receiving transactions. In fact, it is employed to generate transaction signatures which, akin to physical signatures, can demonstrate a user’s authority to participate in a transaction. In a decentralized system where there is no central authority to authenticate transactions, each transaction broadcasted to the network must possess a valid signature. These signatures must be capable of verifying that the transaction was initiated by a specific user. This is accomplished through asymmetric encryption where a user possesses one or multiple public/private key pairs. Signature schemes comprise a problem that can only be computed if the user has access to both the public and private key, but can be validated as a genuine signature by any other user with access to the public key.

One example of this is elliptic curve-based signature schemes, which enable a user to prove that they own the funds they are declaring in a transaction. This allows for the sending and receiving of transactions without the need for a central authority. Elliptic curves are chosen over other signature schemes such as RSA due to the smaller key sizes, which helps to reduce the amount of information held on the network.

## Hash functions

A hash function is a mathematical algorithm that takes a variable number of characters, referred to as a message and converts it into a string with a fixed number of characters known as a hash value or hash. Hashing algorithms are one-way functions, meaning they are easy to perform in one direction but impossible to reverse. Hashing is valuable for ensuring the integrity of data and detecting any tampering, as even a slight change in the message will produce a completely different hash. Hash functions are fundamental tools in modern cryptography, used in information security to verify transactions, messages, and digital signatures. They have various applications in blockchain and distributed ledger technologies, including linking blocks and creating compressed data structures. Figure 1.9 illustrates the sequential stages involved in the functioning of a hash.

![](images/Figure_1.9.png)

In a decentralized environment, where there is no central authority to control and verify the validity of transactions, the use of a hashing function ensures the integrity and traceability of each block in a blockchain. This creates an immutable record of events and allows for the tracking of assets from one block to the next.
