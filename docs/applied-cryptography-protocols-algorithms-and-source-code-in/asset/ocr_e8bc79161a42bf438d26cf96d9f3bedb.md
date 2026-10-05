# 24.14 PUBLIC-KEY CRYPTOGRAPHY STANDARDS (PKCS)

The Public-Key Cryptography Standards (PKCS) are RSA Data Security, Inc.’s attempt to provide an industry standard interface for public-key cryptography. Traditionally, sort of thing would be handled by ANSI, but considering the current situation in cryptography politics, RSADI felt they had do it on their own. Working with a variety of companies, they developed a series of standards. Some are compatible with other standards and some are not.

These are not standards in the traditional sense of the word; no standards body convened and voted on PKCS. According to its own materials, RSADI “retain sole decision-making authority on what each standard is” and “publish revised standards when appropriate [803].

Even so, there is a lot of stuff here. If you’re not sure what kind of syntax and data structures to use when programming public-key cryptography, these standards are probably as good as anything you could come up with. And since they’re not really standards, you can tailor them to suit your needs.

Following is a short description of each PKCS (PKCS #2 and PKCS #4 have have been incorporated into PKCS #1!

PKCS #1 [1345] describes a method for RSA encryption and decryption, primarily for constructing digital signatures and digital envelopes described in PKCS #7. For digital signatures, the message is hashed and then the hash is encrypted with the private key of the signer. Both message and hash are represented as detailed in PKCS #7. For digital envelopes [encrypted messages], the message is first encrypted with a symmetric algorithm, and then the message is encrypted with the public key of the recipient. The encrypted message and key are represented together according to the syntax of PKCS #7. Both of these methods are compatible with PEM standards. PKCS #1 also describes a syntax, identical to the syntax in X.509 and PEM. For RSA public and private keys and three signature algorithms—MD2 and RSA, MD4 and MD5 and—for signing certificates and the like.

PKCS #3 [1346] describes a method for implementing Diffie-Hellman key exchange.

PKCS #5 [1347] describes a method for encrypting messages with a secret password. It uses either MD2 or MD5 to derive the key from the password, and encrypts with DES in CBC mode. The method is intended primarily to encrypt private keys when transferring them from one computer system to another, but can be used to encrypt messages.

PKCS #6 [1348] describes a standard for public keys. The syntax is a superset of X.509, so that X.509 can be extracted if necessary. Or and above the X.509 set, additional attributes extend the certification process beyond just the key. These include other information, such as electronic mail address.

PKCS #7 [1349] is a general syntax for data that may be encrypted or signed, as digital envelopes or digital signatures. The syntax is recursive, so that envelopes can be nested, or someone can sign previously encrypted data. The syntax also