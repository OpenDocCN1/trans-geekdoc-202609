# Hacking Multifactor Authentication

nothing the attacker cannot. They have the keys to the kingdom. The entire authentication system was essentially set up to prevent that occurrence, and once it has happened, the authentication system can no longer be trusted as a way to verify who is or isnt associated with a particular identity (label).

# Cryptography

Most authentication solutions (although not all) use cryptography to protect themselves and their secrets. Most authentication systems use "industry-accepted" cryptographic algorithms and key sizes. Many hacks try to compromise the cryptography itself (by finding an inherent weakness) or by finding a flaw in the implementation. The latter is many, times easier and more common. The world is full of hundreds of vulnerabilities found because MFA developers did not correctly and securely implement the secure cryptography. Attacks like these are often described as "leaving the keys of the kingdom under the doormat"

All industry-accepted cryptographic standards become weaker over time. Cryptographic attacks only get better over time, either because of increasing computational resources or because the attacks find increasingly ways to take advantage of an inherent cryptographic flaw in the cipher. The nature of cryptographic use is that vendors must always be aware that existing cryptography is constantly weakened over time and that an MFA solution relying on cryptography must be prepared to move to newer, stronger cryptographic standards. If it is relatively easy for the MFA vendor to move their solution to other, newer cryptographic standards, if their solution is "crypto-agile." Unfortunately, many MFA solutions are "hard-coded" as to what cryptographic algorithms and key sizes they can use, and they cannot be upgraded without a complete replacement of the hardware and software.

On a related note, as of 2020 quantum computers are becoming powerful enough that they may break most public key cryptography (RSA, Diffie-Hellman, Elliptic Curve, etc.) and weaken in half most traditional symmetric algorithms (e.g., AES), hashes (e.g., SHA-2), and random number generators (RNG). See my previous book, Cryptography Apocalypse (Wiley, 2019), if you want to learn about the quantum crypto break in more detail and how you can start preparing now.

No matter what, an MFA solution should always be aware that any involved cryptography can become compromised at any time and make their solutions crypto-agile in anticipation.

# Technology

Like cryptography, any of the technology used by the MFA solution can be compromised. For example, many physical MFA device rely on the Universal Serial Bus (USB) standard. USB is a software, API, and hardware specification, and each of those components can come under attack at any time.