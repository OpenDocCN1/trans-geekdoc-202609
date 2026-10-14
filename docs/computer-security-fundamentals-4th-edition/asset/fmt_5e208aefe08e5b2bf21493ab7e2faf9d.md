
φ (3233) = (61 − 1)(53 − 1) = 3120

Choose any number 1 < `e` < 3120 that is co-prime to 3120. Choosing a prime number for `e` leaves us only to check that `e` is not a divisor of 3120. Let `e` = 17. Compute `d`, the modular multiplicative inverse of yielding `d` = 2753.

The public key is (`n` = 3233, `e` = 17). For a padded plain text message *m*, the encryption function is:

`m`^(17) (mod 3233)

The private key is:

(`n` = 3233, `d` = 2753)

For an encrypted cipher text, *c*, the decryption function is:

`c`^(2753) (mod 3233)

For those readers new to RSA or new to cryptography in general, it might be helpful to see one more example, with even smaller numbers:

Select primes: `p` = 17 & `q` = 11.

Compute `n` = `pq` = 17 × 11 = 187.

Compute φ(`n`) = (`p` − 1)(`q` − 1) = 16 × 10 = 160.

Select `e`: gcd(`e`,160) = 1; choose `e` = 7.

Determine `d`: `de` = 1 mod 160 and `d` < 160. Value is `d` = 23 since 23 × 7 = 161 = 10 × 160 + 1.

Publish public key: (7 and 187).

Keep secret private key: 23.

##### Diffie-Hellman

Diffie-Hellman was the first publicly described asymmetric algorithm. This cryptographic protocol allows two parties to establish a shared key over an usecured channel. In other words, Diffie-Hellman is often used to allow parties to exchange a symmetric key through some unsecured medium, such as the Internet. It was developed by Whitfield Diffie and Martin Hellman in 1976.

One problem with working in cryptology is that much of the work is classified. You could labor away and create something wonderful…that you cannot tell anyone about. Then to make matters worse, years later someone else might develop something similar, release it, and get all the credit. This is exactly the situation with Diffie-Hellman. It turns out that a similar method had been developed a few years earlier by Malcolm J. Williamson of the British Intelligence Service, but it was classified.

There have been several modifications and improvements to Diffie-Hellman. Among the most well known are Elgamal and MQV. Elgamal is named after its inventor, Taher Elgamal. MQV was first proposed in 1995 and is named after its inventors Alfred Menezes, Minghua Qu, and Scott Vanstone. MQV is incorporated in the public key standard IEEE P1363 and NIST’s SP800-56A standard.

##### Elliptic Curve Cryptography

The elliptic curve algorithm was first described in 1985 by Victor Miller and Neal Koblitz. Elliptic curve cryptography (ECC) is based on the fact that finding the discrete logarithm of a random elliptic curve element with respect to a publicly known base point is difficult to the point of being impractical. The mathematics behind this algorithm are a bit much for an introductory book on security. However, if you are interested, you should read the great tutorial at [http://arstechnica.com/security/2013/10/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography/](http://arstechnica.com/security/2013/10/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography/).

There are a number of variations, such as ECC-DH (ECC Diffie-Hellman) and ECC-DSA (ECC Digital Signature Algorithm). The real strength of ECC crypto systems is that you can get just as much security with a smaller key as with other systems, like RSA. For example, a 384-bit ECC key is as strong as 2048-bit RSA.

### PGP

*PGP*, a public key system, stands for *Pretty Good Privacy*. It is a widely used system that is considered very secure by most experts. There are several software implementations available as freeware for most desktop operating systems. There are PGP plug-ins for MSN Messenger and many other popular communications software packages. A simple Yahoo! or Google search for *PGP* will help you find many of these software products.

FYI: “Old” Encryption

PGP is quite old, and you might wonder whether it is therefore outdated. Cryptography is unlike other technological endeavors in this regard: Older is better. It is usually unwise to use the “latest thing” in encryption for the simple reason that it is unproven. An older encryption method, provided it has not yet been broken, is usually a strong choice because it has been subjected to years of examination by experts and to cracking attempts by both experts and less honorably motivated individuals. This is sometimes hard for computer professionals to understand since the newest technology is often preferred in the computer business.

PGP was invented by Phil Zimmermann. Before creating PGP, Zimmermann had been a software engineer for 20 years and had experience with existing forms of cryptography. A great deal of controversy surrounded the birth of PGP because it was created without an easy means for government intrusion, and its encryption was considered too strong for export. This led to Zimmermann being the target of a 3-year government investigation. However, those legal matters have since been resolved, and PGP is one of the most widely used encryption methods available.

The important things to know about PGP are that it is:

*   A public key encryption

*   Considered quite secure

*   Available free of charge

These facts make it well worth your time to investigate PGP as a possible solution for your organization’s encryption needs.

### Legitimate Versus Fraudulent Encryption Methods

The encryption methods discussed earlier in this chapter are just a few of the most widely used modern encryption methods. Dozens of other methods are released to the public for free or are patented and sold for profit every year. However, it is important to realize that this particular area of the computer industry is replete with frauds and charlatans. One need only scan a search engine for *encryption* to find a plethora of advertisements for the latest and greatest “unbreakable” encryption. If you are not knowledgeable about encryption, how do you separate legitimate encryption methods from frauds?

There are many fraudulent cryptographic claims out there. You do not have to be a cryptography expert to be able to avoid many of those fraudulent claims. Here are some warning signs:

*   **Unbreakable:** Anyone with experience in cryptography knows that there is no such thing as an unbreakable code. There are codes that have not yet been broken. There are codes that are very hard to break. But when someone claims that a method is “completely unbreakable,” you should be suspicious.

*   **Certified:** Guess what? There is no recognized certification process for encryption methods. Therefore, any “certification” a company claims is totally worthless.

*   **Inexperienced people:** A company is marketing a new encryption method. What experience do the people working with it have? Does the cryptographer have a background in math, encryption, or algorithms? If not, has he submitted his method to experts in peer-reviewed journals? Or, is he at least willing to disclose how his method works so that it can be fairly judged? Recall that PGP’s inventor had decades of software engineering and encryption experience.

Auguste Kerckhoffs first articulated what has come to be called Kerckhoffs’s principle in the 1800s. He stated that the security of a cipher depends only on the secrecy of the key, not on the secrecy of the algorithm. Claude Shannon rephrased, this stating that, “One ought to design systems under the assumption that the enemy will ultimately gain full familiarity with them.” This idea, referred to as Shannon’s maxim, states essentially the same idea as Kerckhoffs’s principle.

I would add to Kerckhoffs’s principle/Shannon’s maxim something I will humbly call Easttom’s corollary: “You should be very wary of any cryptographic algorithm that has not been published and thoroughly reviewed. Only after extensive peer review should you consider the use of any cryptographic algorithm.” I first proposed this corollary in my book *Modern Cryptography: Applied Mathematics for Encryption and Information Security*.

### Digital Signatures
