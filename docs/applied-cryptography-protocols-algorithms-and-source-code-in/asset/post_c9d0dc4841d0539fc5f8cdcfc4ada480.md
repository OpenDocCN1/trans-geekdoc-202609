
# Public-Key Digital Signature Algorithms

## 20.1 DIGITAL SIGNATURE ALGORITHM (DSA)

In August 1991, The National Institute of Standards and Technology [NIST] proposed the Digital Signature Algorithm [DSA] for use in their Digital Signature Standard [DSS]. According to the Federal Register [538]:

> A Federal Information Processing Standard (FIPS) for Digital Signature Standard (DSS) is being proposed. This proposed standard specifies a public-key digital signature algorithm [DSA] appropriate for Federal digital signature applications. The proposed DSS uses a public key to verify the integrity of the data and identity of the sender of the data. The DSS can also be used by a third party to ascertain the authenticity of a signature and the data associated with it.

This proposed standard adopts a public-key signature scheme that uses a pair of transformations to generate and verify a digital value called a signature.

And:

This proposed FIPS is the result of evaluating a number of alternative digital signature techniques. In selecting, NIST has followed the mandate contained in section 2 of the Computer Security Act of 1987 that NIST develop standards to ensure the cost-effective security and privacy of Federal information and, among technologies offering comparable protection, selecting the option with the most desirable operating and use characteristics.

Among the factors that were considered during this process were the level of security provided, the ease of implementation in both hardware and software, the case of export from the U.S., the applicability of patents, on national security and law enforcement and the level of efficiency in both the signing and verification functions. A number of techniques were deemed to provide appropriate protection for Federal systems. The technique selected has the following desirable characteristics:

NIST expects it to be available on a royalty-free basis. Broader use of this technique resulting from public availability should be an economic benefit to the government and the public.

The technique is selected for efficient implementation of the signature operations in smart applications. In these applications the signature operations are performed in the computationally modest environment of the smart card while the verification process is implemented in a more computationally rich environment such as a personal computer, a hardware cryptographic module, or a mainframe computer.

Before it gets confusing, let me review the nomenclature: DSA is the algorithm; DSS is the standard. The standard employs the algorithm. The algorithm is part of the standard.

## Reaction to the Announcement

NIST's announcement created a maelstrom of criticisms and accusations. Unfortunately, it was more political than academic. RSA Data Security, Inc., vendors of the RSA algorithm, led the criticism against DSS. They wanted RSA, and not another, used as the standard. RSADSI made a lot of money licensing the RSA algorithm, and a royalty-free digital signature standard would directly affect their bottom line. [Note: DSA is not necessarily free of patent infringements; I'll disclose that.]

Before the algorithm was announced, RSADSI campaigned against a “common modulus,” which might have given the government the ability to forge signatures. When the algorithm was announced without this modulus, they attacked on other grounds [154], both in letters to NIST and statements to the press. [Four letters to NIST appeared in [136]. When reading them, keep in mind that at least two of the authors, Rivest and Hellman, had financial interest in DSS's not approved.]

Many large software companies that already licensed the RSA algorithm came out against the DSS. In 1982, the government had solicited public-key algorithms for a standard [537]. After that, there wasn't a peace for NIST years. Companies such as IBM, Apple, Novell, Northern Telecom, Microsoft, DEC, and Sun had already spent amounts of money implementing the RSA algorithm. They were not interested in losing their investment.

In all, NIST received 109 comments by the end of the first comment period February 28, 1992.

Let's look at the criticisms against DSA, one by one.

- 1. DSA cannot be used for encryption or key distribution.

True, but not the point of the standard. This is a signature standard. NIST is committing a standard for public-key encryption. NIST should have a standard for public-key encryption. A grave injustice to the American people by not implementing a public-key encryption standard. It is suspicious that this proposed digital signature standard cannot be used for encryption. As it turns out, though, it can—see Section 23.3.] That does not mean that a signature standard is useless.

- 2. DSA was developed by the NSA, and there may be a trapdoor in the algorithm.

Much of the initial comments were just paranoia: "NIST's denial of information with no apparent justification does not inspire confidence in DSS, but intensifies concern that there is a hidden agenda, such as laying the groundwork for a national public-key cryptosystem that is in fact vulnerable to being broken by NIST and/or NSA" [154]. One serious question about the security of DSA was raised by Arjen Lenstra and Stuart Haber at Bellcore. This will be discussed later.

- 3. DSA is slower than RSA [800].

True, or less. Signature generation speeds are slower, but signature verification can be 10 to 40 times slower than DSA. Key generation, however, is irrelevant, a user rarely does it. On the other hand, signature verification is the most common operation.
The problem with this criticism is that there are many ways to play with the test parameters, depending on the results you want. Precomputations can speed up DSA signature generation, but don't always apply. Proponents of RSA use optimized numbers to make their calculations easier; proponents of DSA use their own.

- 4. RSA is a de facto standard.

Here are two examples of this. From Robert Follett, the program director of standards at IBM [570]: "IBM is concerned that NIST proposed a standard rather than adopting ISO 9796. This is not a sufficient justification for RSA."

- 5. The DSA selection process was not public; sufficient time for analysis has not been provided.

First NIST claimed that they designed the DSA, then they admitted that NSA helped them. Finally, they confirmed that NSA designed the algorithm. This worries many people; the NSA does not inspire trust. Even so, the algorithm is public and available for analysis, and NIST extended the time for comment.

- 6. DSA may infringe on other patents.

This may be discussed in the section on patent issues.

- 7. The key size is too small.

This was the only valid criticism of DSS. The original implementation the modulus at 512 bits [1149]. Since the algorithm gets its security from the difficulty of computing discrete logs in a finite field, 512 bits is de-short. According to Brian LaMacchia and Andrew Odlyzko, "...512-bit primes appear to offer marginal security..." [934]. In response to this criticism, NIST made the key size variable, from 512 bits to 1024 bits. Not great, better.

On May 19, 1994, the standard was finally issued [1154]. The issuing statement said [542]:

"This is applicable to all Federal departments and agencies for the protection of unclassified information... This standard shall be used in designing and implementing public-key signature schemes which Federal departments and agencies operate or are operated for under contract. Adoption and use of this standard is available to private and commercial organizations."

## Description of DSA

DSA is a variant of the Schnorr and ElGamal algorithms, and is fully described in [1154]. The algorithm uses the following parameters:

p = a prime number L bits long, when L ranges from 512 to 1024 and is a multiple of 64.
