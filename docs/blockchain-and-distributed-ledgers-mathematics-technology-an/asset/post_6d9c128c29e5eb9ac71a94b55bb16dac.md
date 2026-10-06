
# CHAPTER 4: 
## Essential Cryptographic Tools

> “One of the most singular characteristics of the art of deciphering is the strong conviction possessed by every person, even moderately acquainted with it, that he is able to construct a cipher that nobody else can decipher. I have also observed that the cleverer person, the more intimate is his conviction.”
Charles Babbage, *Passages from the Life of a Philosopher*

## 4.1 Introduction

In Greek, the word Cryptography (Κρυπτογογράφία) means hidden writing. Cryptography has been used since times immorial by various parties interested in hiding their messages from adversaries and preventing adversaries from forging a message purportedly coming from the original sender.

Until the middle of the 20th century, all cryptography relied on the symmetric paradigm. To encrypt and decrypt a message, both the sender and the receiver must possess the *same* key. In the 1970s, several groups of researchers achieved a remarkable breakthrough and discovered the asymmetric cryptography. Now, a sender can use the receiver's public key, readily available to all, to encrypt the message, while the receiver can use her (or private) key to decrypt it. Conversely, the sender can use her secret key to sign a message, which anyone can verify by applying her key.

As we shall see below, in the Bitcoin, Ethereum, and many other protocols, no information is encrypted per se. These protocols rely on the fact that asymmetric cryptography allows one to digitally sign messages, with a value signature being an irrefutable proof that the signer owns the secret key associated with her public key. This feature allows one to establish the ownership of the bitcoins associated with a particular address. The legitimate owner of the address can transfer this value to a different address if she wishes to.

One cryptographic construct is of paramount importance — a hash function. A useful hash function can map a message of an arbitrary length to a fixed-length message, say 256 bits. It is practically impossible to find another message with the same hash, even though, such messages do exist. Using hash functions, one can significantly reduce the computational burden associated with the requisite cryptographic operations, such as digitally signing a message, because it becomes possible to sign the hash of the message, rather than the message itself. In simple terms, one can think about a hash as a fingerprint of a person — it tells you who the owner is, but the owner can easily prove that the fingerprint is indeed hers.

Paradoxically, modern cryptography is simultaneously extraordinarily complex and relatively simple. On the one hand, the relevant cryptographic ideas are among the most complex achievements of humankind. On the other hand, at the end of the day, encryption or signing messages relies on the fact that there are so many permutations that their straightforward analysis, called the brute force attack, is not possible given the abilities of modern computers. Besides, the so-called cryptographic breaks operate faster than brute force attacks should not be possible either. One can think of the process of decrypting a message without knowing the key as searching for a needle in a stack of needles, not in a proverbial stack of them. Time will tell if billions of modern cryptography begin to crumble with the advent of quantum computing.

A mathematical aside is in order: the entire edifice of modern cryptography is probabilistic. A typical statement says “if p is a huge number, then a particular algorithm is secure.” However, if p is huge, as it should be in our day and age, and it’s not easy to check that it is prime, or probabilistically. Simultaneously, theorems in this field, such as the celebrated and extremely Hasse’s theorem, are discussed below, are of course, absolute. One has to appreciate that these theorems are based on the assumption that p is prime for their conclusions to be valid.

In this chapter, we provide a gentle introduction to cryptography. We cover both symmetric and asymmetric cryptography and hash functions, digital signatures, and a few other concepts. Modern cryptocurrencies rely on the so-called elliptic cryptography (ECC). Since a frontal attack on the requisite ideas is hard, we start with the Finite Ring Cryptography (FRC) due to Rivest-Shamir-Adleman (RSA), which is easier to understand. Then we touch upon the Finite Field Cryptography (FFC) before proceeding to more advanced topics related to the ECC.

The chapter proceeds as follows. In Section 4.2, we start with a brief discussion of symmetric cryptography to put things in perspective. In Section 4.3, we introduce all the important concept of asymmetric cryptography based on the public-secret key. Section 4.4 contains a concise exposition of number theory, which are used in subsequent sections to build the set of distributed ledger technology-related cryptographic tools. In Section 4.5, we put these tools to good use by developing the so-called FRC, also known as RSA cryptography. We emphasize that many cryptocurrencies rely on RSA digital signature directly; however, this framework is valable a starting point for more recent algorithms. In Section 4.6, we cover ECC including its most derivatives—the celebrated ElGamal and Schnorr digital signature algorithms. These algorithms are particularly interesting since they are usable in the ECC framework, which we discuss in Section 4.7. We compare three digital signature algorithms in 4.8 and conclude that at present, EC digital signature is best suited to DLT needs. However, in the long run, the EC-based version of the Schnorr algorithm will win. In Sections 4.9 and 4.10, we discuss the second cryptographic primitive needed for DLT—the so-called hash functions and search algorithms. In Section 4.11, we cover Merkle trees and hash pointers.

> Of course, one can never be sure that this is true, exhaustive adversarial analysis of any cryptographic algorithm is necessary before it is used.

In Section 4.12, we outline potential threats to DLT emanating from the nascent field of quantum computing. We summarize the chapter in Section 4.13.

It is worth mentioning that this chapter is relatively technical. The reader should consume the material at her own pace. Taking the main conclusions for granted should not prevent the reader from mastering the rest of the book.

## 4.2 Symmetric key cryptography

### 4.2.1 Introduction

To start with, we introduce some terminology. A plaintext message contains the information in its standard form. A ciphertext or cryptogram is the transformed message. The key (keys) is (are) the secret parameter(s) for the encryption, which are known only to the sender and intended recipients. The secret key(s) are used to perform the transformation from the plain text to the cryptogram (encryption) and from the cryptogram to the plain text (decryption). Ciphers are based on a general algorithm employing a secret key to perform encryption and decryption. Cryptanalysis represents a method for transforming a cryptogram back to the original plaintext without previous knowledge of the key.

The general setup is shown in Figure 4.1; Alice uses a secret key to encrypt a message and broadcast it to Bob, who uses the same secret key to decrypt the cryptogram. As usual, Charlie, the adversary, tries to eavesdrop on Alice’s communications using cryptanalysis. If succeeds, he can not only read the communications but, in principle, to forge messages.

According to Kerckhoffs principle, also known as Shannon’s maxim, a cryptographic scheme is secure when everything about it, except the key, is publicly known, and yet it cannot be broken. Shannon put it somewhat differently: “one ought to design systems under

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_127_0.png)

**Figure 4.1** Conceptual framework for symmetric key cryptography, which relies on a shared key that is used to both encrypt or decrypt text/ciphertext. Own graphics.
