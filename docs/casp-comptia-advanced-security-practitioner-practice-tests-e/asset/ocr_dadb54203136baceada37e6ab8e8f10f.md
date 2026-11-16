185. C. Key-stretching techniques are used to make a possibly weak key or password more secure against a brute-force attack by increasing the work factor it takes to test each possible key. This works by inserting a random set of characters into the key to increase the size of the password hash, making things harder for the attacker.

186. B. Password-Based Key Derivation Function 2 (PBKDF2) is a simple cryptographic key derivation function that is resistant to dictionary attacks and rainbow table attacks. It is based on iteratively deriving HMAC many times with some padding. The components of a key built with PBKDF2 are key = pbkdf2(password, salt, iterations-count, hash-function, derived-key-len). Today PBKDF2 is considered less secure than modern KDF functions, so it is recommended that you use bcrypt or Argon2 instead.

187. D. Bcrypt is a hash function that has built-in salt functionality. The MD5 function is now considered very insecure: it is easy to reverse with current processing power. SHA1, SHA256, and SHA512 functions are no longer considered secure. PBKDF2 is considered acceptable. The most secure current hash function listed here is bcrypt.

188. C. GNU Privacy Guard (GPG) is a free asymmetric encryption system in which the end users have to manage the keys and have to verify public key identities.

189. B. The Encrypting File System (EFS) is a Microsoft file encryption technology that enables a user to encrypt individual files.

190. A. GNU Privacy Guard (GPG) is a free software package that can run on Linux and that supports the encryption of data and communication using both symmetric and asymmetric encryption.

191. D. The Encrypting File System (EFS) is a component of the New Technology File System (NTFS). Other filesystems do not support EFS.

192. A. Although these are all good questions, the next question for mitigation should be “Can the attackers actually use what was stolen?” Attackers steal data all the time, but most of the time it is/isn’t unusable due to strong encryption. If the data stolen is in cleartext or with weak encryption, it changes the trajectory of your disaster recovery process.

193. A. HTTPS (Hypertext Transfer Protocol Secure) appears in the URL when a website is secured by a certificate. The details of the certificate, including the issuing authority and the corporate name of the website owner, can be viewed by clicking the lock symbol on the browser bar. In 2015, you could get an SSL/TLS certificate good for five years. In 2018, that was reduced to two years. In September 2020, it was announced that SSL/TLS certificates would no longer be issued for longer than 13 months or 397 days. An expired certificate is usually a management issue. The administrator of the website has not tracked and updated the digital certificate. An expired certificate will be treated as untrusted certificate.

194. A. By creating a unique session key for transactions instead of relying on an encrypted session, attackers cannot gain access to data for more than one single communication between a server and a user. The benefit is increased security for both the user and the server.