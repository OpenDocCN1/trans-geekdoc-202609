
![image](Images/image00483.jpeg)`SSL/TLS basics`

The preceding 12 chapters have covered the algorithms used in cryptography, including symmetric key cryptography, asymmetric key cryptography, cryptographic hashes, and generating random numbers. In this chapter, as well as the next two chapters, we will be focusing on practical applications of cryptography. [Chapter 14](#part0025.xhtml#ch14) will discuss virtual private networks, and [Chapter 15](#part0026.xhtml#ch15) will cover military applications of cryptography. In this chapter, the primary focus is on Secure Sockets Layer and Transport Layer Security (SSL/TLS) Protocols. However, in order to cover this topic adequately, I will first cover digital signatures, digital certificates, and the Public Key Infrastructure (PKI), all of which are needed for SSL/TLS.

The importance of applied cryptography cannot be overstated. Without modern protocols such as SSL/TLS, modern e-commerce, online banking, and similar technologies would not exist. Although it is certainly important that you understand the mathematics behind cryptography and the actual algorithms being implemented, it is also important that you understand how all of this is used for secure communications.

#### Digital Signatures

I briefly touched on digital signatures when I discussed asymmetric cryptography in [Chapter 10](#part0020.xhtml#ch10). The concept involves simply reversing some asymmetric algorithm process. A piece of data is encrypted with the sender’s public key. Anyone can access the sender’s public key and decrypt/verify that message.

There are primarily two types of digital signatures: direct and arbitrated. Each has its own strengths and weaknesses and is thus used in different situations. The question is not which type of signature is best, but rather which is better for a specific situation.

##### Direct Signature

A direct signature involves only two parties (the sender/signer and the receiver). The signature is usually done in one of two ways: either the entire message is encrypted with the sender’s private key, or a cryptographic hash, message authentication code, or HMAC is created that is then encrypted with the sender’s private key. In either case, the recipient will obtain the sender’s public key to decrypt/verify the message.

With a direct signature, there is no third-party verification of the sender’s identity. This type of signature is often used in e-mail communications. Verification is assumed based on the sender’s e-mail address and the fact that the recipient used the alleged sender’s public key to verify the message and it worked. If the e-mail was spoofed (that is, it was not really the purported sender, but rather someone else faking the sender’s e-mail address), then the message signature was actually done with some key other than the purported sender’s key, and thus verification would fail. The basic process is shown in [Figure 13-1](#part0024.xhtml#ch13fig01).

![Images](Images/image00703.jpeg)

* * *

**FIGURE 13-1**`Direct digital signature process`

A typical direct signature process involves the following steps:

**1.**`Write the message.`

**2.**`Create a hash of the message.`

**3.**`Sign the hash with the sender’s private key.`

**4.**`Encrypt the message with the recipient’s public key.`

**5.**`Send the message.`

This multi-step process ensures message integrity with the hash, verifies the identity of the sender with the digital signature, and provides message confidentiality with the encryption. This is diagrammed in [Figure 13-2](#part0024.xhtml#ch13fig02). Note that, in the diagram, H(M) means the cryptographic hash function of the message M: H is the hashing function and M is the input, or message. The S(H(M)) has similar meaning, with S denoting the digital signature of the hash of the message M.

![Images](Images/image00704.jpeg)

* * *

**FIGURE 13-2**`Typical signature process`

##### Arbitrated Digital Signature

An arbitrated digital signature works similarly to a direct signature, but the entity signing the message is not the sender and is instead a third party that is trusted by both sender and receiver. The rest of the process is the same. This sort of digital signature is often used to provide even more assurance that the sender is indeed who they claim to be. A common implementation of this process is shown in [Figure 13-3](#part0024.xhtml#ch13fig03).

![Images](Images/image00705.jpeg)

* * *

**FIGURE 13-3**`Arbitrated digital signature`

###### Blind Signatures

The blind signature adds a nuance to the process of arbitrated digital signatures. The signer simply signs a message verifying that the sender did indeed send it, but the signer has no idea what the content of the message is. This allows the signer to verify the origin of the message but not the content.

Think about it like this: Assume you observe a person writing a note, putting it in an envelope, and then sealing the envelope. You then sign the envelope, verifying that the person did indeed write it and place it in the envelope. You can attest to the identity of the sender, but you have no idea what the contents are.

A blind signature is a great option when the privacy of the data being sent is of paramount importance, such as in voting situations or when using private digital currency. Blind signatures provide the enhanced validation of the sender via arbitrated digital signatures, but they protect the privacy of the data.

#### Digital Certificates

In [Chapters 10](#part0020.xhtml#ch10) and [11](#part0021.xhtml#ch11) I discussed asymmetric key cryptography, also known as public-key cryptography. The strength of asymmetric cryptography is that there is no issue with key exchange. It is perfectly acceptable for anyone, and indeed everyone, to have access to the public keys of both the sender and receiver. However, this does not answer the question of how such public keys are disseminated. The first step in that process is a *digital certificate*, a digital document that contains some information about the certificate holder and the certificate holder’s public key. There are two major types of digital certificates: X.509 and PGP.

##### X.509

X.509 is an international standard for the format and information contained in a digital certificate. X.509 is the most common type of digital certificate in the world. It is a digital document that contains a public key signed by a trusted third party known as a certificate authority (CA). The X.509 standard was released in 1988. It has been revised since then, with the most recent version being X.509 version 3, specified in RFC 5280.^([1](#part0024.xhtml#ch13note1a)) This system supports not only obtaining information about the certificate holder, but also verifying that information with a trusted third party. This is key to secure protocols such as SSL and TLS, as you will see later in this chapter.

The content of an X.509 certificate is listed here:

![image](Images/image00484.jpeg)`Version``The version of X.509 being used (as of this writing, version 3).`

![image](Images/image00484.jpeg)`Certificate holder’s public key``The public key of the certificate holder—this is how public keys are disseminated.`

![image](Images/image00484.jpeg)`Serial number``A unique identifier that identifies this certificate.`

![image](Images/image00484.jpeg)`Certificate holder’s distinguished name``A distinguished, or unique, name for the certificate holder; usually a URL for a web site or an e-mail address.`

![image](Images/image00484.jpeg)`Certificate’s validity period``Most certificates are issued for one year, but the exact validity period is reflected in this field.`

![image](Images/image00484.jpeg)`Unique name of certificate issuer``Identifies the trusted third party that issued the certificate. Public CAs include Thawte, VeriSign, GoDaddy, and others.`
