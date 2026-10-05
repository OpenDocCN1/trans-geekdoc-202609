# CHAPTER 18 One-Way Hash Functions

# 18.7 SECURE HASH ALGORITHM (SHA)

NIST, along with the NSA, designed the Secure Hash Algorithm (SHA) for use with the Digital Signature Standard [see Section 20.2] [1154]. (The standard is the Secure Hash Standard (SHS), SHA is the algorithm used in standard.) According to the Federal Register [539].

A Federal Information Processing Standard (FIPS) for Secure Hash Standard [SHS] is being proposed. This proposed standard specifies a Secure Hash Algorithm [SHA] for use with the proposed Digital Signature . . Additionally, for applications not requiring a digital signature, the SHA is to be used whenever a secure hash is required for Federal applications.

And

This standard specifies a Secure Hash Algorithm (SHA), which is necessary to ensure the security of the Digital Signature Algorithm (DSA). When a message of any length < 2^64 bits is input, the SHA produces a 160-bit output called a message digest. The message digest is input to the DSA, which computes the signature for the message. Signing the message digest rather than the message often improves the efficiency of the process, because the message digest is usually much smaller than the message. The same message digest should be obtained by the verifier of the signature when the received version of the message is used as input to SHA. The SHA is secure because it is designed to be computationally infeasible to recover a message corresponding to a given digest, or to find two different messages that produce the same message digest. Any change to a message in transit will, with a very high probability, result in a different message digest, and the signature will fail to verify. The SHA is based on principles similar to those used by Professor Ronald L. Rivest of MIT designing the MD4 message digest algorithm [1319], and is closely modeled after that.

SHA produces a 160-bit hash, longer than MD5.

# Description of SHA

First, the message is padded to make it a multiple of 512 bits long. Padding is exactly the same as in MD5: First append one, then as many zeros as necessary to make it 64 bits short of a multiple of 512, and finally a 64-bit representation of the length of the message before padding.

Five-32 bit variables (MD5 has four variables, but this algorithm needs to produce a 160-bit hash) are initialized as follows:

```
A = 0x67452301
B = 0xefcdab39
C = 0x98badcfe
D = 0x10325476
E = 0xc3d2e1f0
```