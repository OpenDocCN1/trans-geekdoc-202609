
![image](Images/image00484.jpeg)  *Community clouds* are a midway point between private and public. These are systems wherein several organizations share a cloud for specific community needs. For example, several computer companies might join to create a cloud devoted to common security issues.

Regardless of the type of cloud, the structure is the same: geographically dispersed, replicated data. And the issues of securing that data are the same.

# Cryptography Options for the Cloud

You might think that cryptography in the cloud is no different from encrypting any file or hard drive, but that would be a mistake. Certainly you can use traditional algorithms such as `Blowfish` or `AES` to encrypt files or folders that are stored in the cloud. The issue arises when cloud customers want to have data that is encrypted in such a way that the cloud vendor cannot access it.

One of the options for cryptography in the cloud is *homomorphic cryptography*, which we will explore later in this chapter. For now, just keep in mind that homomorphic encryption is important to cloud computing because it allows the cloud vendor to perform some limited mathematical operations on the cipher text without first decrypting it or even having the key.

Proof of storage (PoS) is another option for the cloud. Proof of storage is a mechanism whereby the user can get proof that the vendor has not tampered with the data. There are a number of ways of doing this, many of which involve the use of hashing algorithms (see [Chapter 9](#part0018.xhtml#ch09)). However, proof of storage has evolved beyond simply maintaining a hash of your data to become an interactive protocol that allows a client to verify that the server possesses the original data without retrieving it.

Other related concepts include provable data possession (PDP) or proof of retrievability (POR). With both terms, the idea is the same: The data owner does not have a copy of all the data in the cloud; however, the owner wants to make sure their data is still available in the cloud. One simple solution is to sign data digitally and to check the signature when needed.

According to the Microsoft Research web site,

              Using a proof of storage (also known as a proof of data possession or a proof of retrievability) a client can verify whether the cloud operator has tampered with its data. In particular, this can be done without the client storing a local copy of the data and without it having to retrieve any of the data. In fact, the work for the client is negligible no matter how large the data is.^([1](#part0030.xhtml#ch19note1a))

Of course, there is a simpler option. Each customer keeps its own cryptographic keys in its own network and is responsible for key management. The problem with this approach, however, is that it leads to a wide range of different levels of security within the same cloud, because customers may be adept or not so adept at key management. Invariably, some end user may lose his or her key and expect the cloud vendor to be able to recover it. But if each customer is responsible for its own key management, there is nothing the vendor can do. Also, the vendor is unable to perform any operations with the encrypted data (see the next section, “Homomorphic Cryptography”).

## Homomorphic Cryptography

Homomorphic encryption is a fascinating branch of cryptography that enables someone to carry out computations on cipher text without first decrypting the message. In other words, you can perform math on the encrypted data without actually decrypting the data. It must be stressed, however, that the entity performing the operation on the encrypted data has no idea what the actual data is. The entity cannot see the plain text, since it doesn’t have access to the encryption key. This is particularly interesting in cloud environments because it allows the cloud vendor to perform some operations on the encrypted data without having access to the encryption key.

In *Wired* magazine, Andy Greenberg described homomorphic encryption, as well as its uses, as follows:

              A homomorphically encrypted search engine, for instance, could take in encrypted search terms and compare them with an encrypted index of the web. Or a homomorphically encrypted financial database stored in the cloud would allow users to ask how much money an employee earned in the second quarter of 2013. But it would accept an encrypted employee name and output an encrypted answer, avoiding the privacy problems that usually plague online services that deal with such sensitive data.^([2](#part0030.xhtml#ch19note2a))

Craig Gentry described the first plausible homomorphic encryption process, which supported both addition and multiplication on cipher text, without first decrypting the cipher text. Several algorithms are either partially homomorphic (that is, they allow one operation to be done homomorphically) or fully homomorphic (they allow addition and multiplication).

**Note**

Craig Gentry is an American computer scientist who won a MacArthur Fellowship in 2014. He also invented the first plausible construction for a fully homomorphic encryption scheme. The MacArthur Fellowship, often referred to as the “Genius Grant,” is awarded each year to several individuals who show exceptionally creative work. The prize is currently $625,000 awarded over five years in quarterly installments. An anonymous group nominates potential MacArthur Fellows; there are no applications.

Although homomorphic encryption has uses beyond the cloud, it has been specifically lauded as a solution to cloud issues. In a 2011 *MIT Technology Review* article, author Erica Neone specifically described Gentry’s innovations as follows: “Craig Gentry is creating an encryption system that could solve the problem keeping many organizations from using cloud computing to analyze and mine data: it’s too much of a security risk to give a public cloud provider such as Amazon or Google access to unencrypted data.”^([3](#part0030.xhtml#ch19note3a))

**Note**

When the first papers on homomorphic encryption were published, it was an impractical, theoretical technology. However, in the past several years it has moved from the theoretical to the practical and applied. For example, as early as 2011, researchers at Microsoft developed a practical, applicable homomorphic approach.^([4](#part0030.xhtml#ch19note4a)) In 2011, Gentry and Shai Halevi published a methodology for implementing Gentry’s original homomorphic process.^([5](#part0030.xhtml#ch19note5a))

## RSA

RSA in textbook format (that is, not modified) can be used homomorphically. Here’s an example. Assume that the public key is modulus `m` and exponent `e`. You encrypt any message by `x^e mod m`. You can certainly perform some mathematical operations on the encrypted data by simply encrypting that data and applying the operation to the two encrypted texts. For example, let’s use `E` to represent the encryption operation of RSA: `E(x[1]) * e(x[2]) = x[1]^e x[2]^e mod m`, which is, in turn, equal to `E(x[1] * x[2])`. Basically multiplying two cipher texts together is the same as multiplying two plain texts and then encrypting them. Not all ciphers lend themselves to this sort of operation, but RSA does. ElGamal can also be used in a homomorphic manner.

## Goldwasser–Micali

Goldwasser–Micali is an asymmetric cipher developed by Shafi Goldwasser and Silvio Micali in 1982. It was the first probabilistic public key algorithm that is provably secure. This algorithm has not gained wide use because the cipher texts are far larger than the initial plain text—as much as several hundred times larger. However, this algorithm supports homomorphic properties.

**Note**
