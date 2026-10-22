
![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_257_0.png)

## EXHIBIT 7.21 Certificate Authorities and the Root Key

## 7.6 BEYOND RSA AND DES.

Cryptography research and development did not stop with the development of the RSA algorithms. Events in the last two decades of the twentieth century and the first decade of the twenty-first, and their implications, are discussed in this final section of the chapter, which concludes with some warnings on implementing encryption.

### 7.6.1 Elliptic Curve Cryptography.

In 1985, Neal Koblitz from the University of Washington and Victor Miller of IBM independently discovered the application of elliptic curve systems to cryptography. When applied to public key cryptography, elliptic curve arithmetic has been found to offer certain advantages over first-generation public key techniques such as Diffie-Hellman and RSA.

The security of elliptic curve algorithms is based on the same principle as the Diffie-Hellman algorithm, the discrete log problem, as described in Section 7.4.2. The advantages to elliptic curve algorithms lie in the key size needed to achieve certain levels of security. As one scales security upward over time to meet the evolving threat posed by eavesdroppers and hackers with access to greater computing resources, elliptic curves begin to offer dramatic savings over the old, first-generation techniques.58

Until 2010, public key systems used 1,024 bits or 2,048 bits for creating keys. NIST recommended that after 2010, these systems be upgraded to a system that can provide adequate security. One way of doing this would be to increase the key size that is used. However, systems that are in place today become increasingly cumbersome the larger the key size. The NSA is endorsing elliptic curve cryptography, stating on its Web site that it has implemented elliptic curve public key cryptography systems to protect both classified and unclassified information.59 Elliptic curve systems offer a way to increase key size moderately when more security is required. Exhibit 7.22 shows the NIST recommended key size that RSA or Diffie-Hellman should use to protect the transportation of symmetric keys of various sizes as well as the corresponding elliptic curve key size.

## Exhibit 7.22 NIST Recommended Key Sizes

| Symmetric Key Size (bits) | RSA and Diffie-Hellman Key Size (bits) | Elliptic Curve Key Size (bits) |
|---|---|---|
| 80 | 1024 | 160 |
| 112 | 2048 | 224 |
| 128 | 3072 | 256 |
| 192 | 8192 | 384 |
| 256 | 15360 | 521 |

Source: National Security Agency, "The Case for Elliptic Curve Cryptography," www.nsa.gov/business/programs/elliptic_curve.shtml.

Thus, in order to use RSA to protect a 256-bit AES key, one should use a key of 15,360 bits, which is an order of magnitude larger than the key sizes currently in use throughout the Internet. However, an elliptic curve key would need to be only 521 bits. Elliptic curve algorithms can use smaller keys, because the math involved makes the inverse, or decryption, operations harder as the key length increases.⁶⁰

Another feature that makes elliptic curves appealing is the fact that they are more efficient than the current implementations of public key cryptography, which tend to be relatively slow, causing them to be used more as key distribution methods than data encryption methods. Exhibit 7.23 shows the ratio of Diffie-Hellman computations versus elliptic curve computations for each of the key sizes listed in Exhibit 7.22.⁶¹

### 7.6.2 RSA Patent Expires.

On September 6, 2000, RSA Security released the RSA public key encryption algorithm into the public domain. This means that anyone can now create products that incorporate this algorithm (provided it is their own implementation and not one licensed from RSA). In effect, RSA Security waived its rights to enforce the patent for any development activities that include the RSA algorithm occurring after September 6, 2000. The U.S. patent for the RSA algorithm actually expired on September 20, 2000. The result has been an even broader use of public key encryption, at lower cost.

The RSA patent was always somewhat controversial, because it applied to a piece of mathematics, which is not what most people think of when they think of an invention. The owners of the patent were never able to expand protection beyond the United States. As a result, versions of public key encryption based on alternatives to the RSA algorithm were developed and marketed outside the country, by companies

## Exhibit 7.23 Relative Computation Costs of Diffie-Hellman and Elliptic Curves

| Security Level (bits) | Ratio of DH Cost : EC Cost |
|---|---|
| 80 | 3:1 |
| 112 | 6:1 |
| 128 | 10:1 |
| 192 | 32:1 |
| 256 | 64:1 |

Source: National Security Agency, "The Case for Elliptic Curve Cryptography," www.nsa.gov/business/programs/elliptic_curve.shtml.

like Ireland's Baltimore Technologies, Finland's F-Secure, and Israel's Algorithmic Research. Now encryption companies can dispense with the costly maintenance of multiple versions of their public key products (U.S. and non-U.S.). In addition, U.S. companies can develop and market RSA-based products. Large companies actually can "roll their own" public key encryption schemes for internal use, based on a proven, royalty-free algorithm.

### 7.6.3 DES Superseded.

RSA Security, the company that tried to make the RSA algorithm synonymous with public key encryption, played a leading role in the other watershed crypto event of 2000, the naming of a successor to DES, the Data Encryption Standard. As noted earlier, projects like the EFF DES Cracker showed that a computer built for less than $250,000 could decipher a DES-encrypted message in fewer than three days. In fact, this was part of the "DES Challenges" sponsored by RSA Security. DES Challenge I was won by Rocke Verser of Loveland, Colorado, who led a group of Internet users in a distributed brute force attack. The project, code-named DESCHALL, began on March 13, 1997, and was successfully completed some 90 days later. DES Challenge II consisted of two contests posted on January 13 and July 13, 1998. The first contest was cracked by a distributed computing effort coordinated by distributed.net, which met the challenge in 39 days. The second contest was the one solved by EFF's purpose-built DES Cracker.

The effect of these projects was to focus attention on the need for stronger encryption. Companies and government agencies wanting to archive sensitive data need it to remain secure for decades, not days. However, as predicted in the 1970s, advances in computer power rendered "obsolete" the DES, the widely used private key algorithm that forms the basis of the DES. Of course, the term "obsolete" is relative in this context. DES is not obsolete when applications need to encrypt bulk data to keep it confidential for a limited period of time, and a lot of data falls into this category. As Exhibit 7.24 shows, there is a direct relationship among time, technology, and the degree of protection that any ciphersystem provides.

In 1997, the U.S. Government began the process of establishing a more powerful standard than DES, known as Advanced Encryption Standard (AES). This is a Federal Information Processing Standard (FIPS) Publication. FIPS 197, specifying "a

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_259_0.png)

Over time, the relative cost of computing power declines, reducing protection afforded by given encryption scheme.

## Exhibit 7.24 Relationship among Time, Technology, and Protection

cryptographic algorithm for use by U.S. Government organizations to protect sensitive (unclassified) information." The government anticipated correctly that AES would be "widely used on a voluntary basis by organizations, institutions, and individuals outside of the U.S. Government—and outside of the United States—in some cases."

In essence, a competition was held to find the best possible algorithm for the job, and the winner, chosen in October 2000, was Rijndael (pronounced "Rhine Doll"). This algorithm was developed specifically for the AES by two cryptographers from Belgium, Dr. Joan Daemen and Dr. Vincent Rijmen. Rijndael is a block cipher with a variable block length and key length. So far, keys with a length of 128, 192, or 256 bits have been specified to encrypt blocks with a length of 128, 192, or 256 bits. (All nine combinations of key length and block length are possible.) However, both block length and key length can be extended very easily in multiples of 32 bits. Rijndael can be implemented very efficiently in hardware, even on smart cards.

### 7.6.4 Quantum Cryptography.

A new basis for computation will profoundly affect cryptographic strength in the coming decades. This section provides a brief and nontechnical summary of the science of quantum computation and quantum cryptography.

### 7.6.4.1 Historical Perspective.

The entirety of this chapter has focused on the status of cryptography as it currently exists. The classic computer has been sufficient to perform the computations and processes required of AES, RSA, and all of the cryptographic systems and algorithms that have been explored since the advent of cryptography. Although modern computers are fundamentally the same as they were in the 1950s, the machines we use today are significantly faster.62 Even though the speed has increased, the primary task of computers has remained the same: "to manipulate and interpret an encoding of binary bits into a useful computational result."63 To push the bounds of computer performance ever forward, computer scientists’ goal has "been the reduction of size in the transistors used in modern processors."64

Early computers were constructed of gates and storage "bits" made of many thousands of molecules. The components of today’s processors are moving in the direction of a few hundred molecules. The computing industry has always known that miniaturization would reach a barrier below which circuits could not be built, because their fundamental physical behavior would change.65

The components of modern computers are reaching this barrier; should transistors become much smaller, they will "eventually reach a point where individual elements would be no larger than a few atoms."66 Computer scientists are concerned about this continual shrinking, because at the atomic level, the laws of quantum mechanics will govern the properties and behavior of circuits, not the laws of classical mechanics.67

The science of quantum mechanics is not fully understood by scientists; it was initially thought to be a major limitation to the evolution of computer technology.68 It was not until 1982 that the scientific community saw any benefit from the unusual effects associated with quantum mechanics. That year, Richard Feynman theorized about a new type of computer that would harness the effects of quantum mechanics and use these effects to its advantage.69 In 1985, David Deutsch of the University of Oxford published a "ground breaking theoretical paper describing how any physical process could be modeled perfectly (in theory) using a quantum computing system."70 He further argued that a quantum system would be able to execute tasks that no modern computer could perform, such as true random number generation.71 "After
