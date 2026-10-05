
## 10.4 Encrypting Data for Storage

### Table 10.4
Comparing Link-by-Link and End-to-End Encryption

| LINK-BY-LINK ENCRYPTION | END-TO-END ENCRYPTION |
| :--- | :--- |
| **Security within Hosts** | |
| Message exposed in sending host | Message exposed in intermediate nodes |
| Message encrypted in sending host | Message encrypted in intermediate nodes |
| **Role of User** | |
| Applied by sending host | Invisible to user |
| Host maintains encryption | One facility for all users |
| Can be done by | All or no messages encrypted |
| Applied by sending process | User applies encryption |
| User must find algorithm | User selects encryption |
| More easily done in software | User chooses to encrypt or not for each message |
| **Implementation Concerns** | |
| Requires one key per host pair | Requires one key per user pair |
| Requires encryption hardware or software at each host | Requires encryption hardware or software at each node |
| Provides node authentication | Provides user authentication |

- The speed of I/O devices demands fast encryption and decryption, and will probably require encryption hardware. In some applications, high-speed algorithms may be required.
- Safe, long-term storage for keys is required.
- Key management is much more complicated, since different people need access to different files, different portions of the file, and so forth.

If the encrypted files are not stored as records and fields, such as text files, retrieval is easier: The entire file is decrypted before use. If the encrypted files are database files, this solution is problematic. Decrypting the entire database to access a single record is inefficient, but encrypting records independently might be susceptible to a block-replay kind of attack.

In addition, you must make sure the unencrypted file is erased after encryption (see Section 10.9). For further details and insights, consult [425,569].

## Dereferencing Keys

When encrypting a large hard drive, you have two options. You can encrypt all the data using a single key. This gives a cryptanalyst a large amount of ciphertext to analyze and makes it impossible to allow multiple users to see only parts of the drive. Or, you can encrypt each file with a different key, forcing users to memorize a different key for each file.

The solution is to encrypt each file with a separate key, and to encrypt the keys with another key known by the users. Each user only has to remember that key. Different users can have subsets of the file-encryption keys encrypted by their key. And there can even be a master key under which every file-encryption key is encrypted. This is even more secure because the file-encryption keys are random and less susceptible to a dictionary attack.

## Driver-level vs. File-Level Encryption

There are two ways to encrypt a hard drive: at the file level and at the driver level. Encryption at the file level means that every file is encrypted separately. To use a file that's encrypted, you must first decrypt the file, then use it, and then encrypt it.

Driver-level encryption maintains a logical drive on the user's machine that has all good practices, when done does little worry on the part of the user. The driver must be considerably more complex than a simple file-encryption program, because it must deal with the issues of having an installed device driver, allocation of new sectors to files, recycling of old sectors from files, random-access read and update requests for data on the logical disk, and.

Typically, the driver prompts the user for a password before starting up. This is used to generate the master decryption key, which may then be used to decrypt actual keys used on different data.

## Providing Random Access to an Encrypted Drive

Most systems expect to be able to access individual disks randomly. This adds some complication for using many streams and block ciphers in any chaining mode. Several solutions are possible:

- Use the sector to generate a unique IV for each sector encrypted or decrypted. The drawback is that each sector will be encrypted with the same IV. Make sure this is not a problem.

- For the master key, generate a pseudo-random block as large as one sector. (You can do this by using an algorithm in OFB, for example.) To encrypt any sector, first XOR in this pseudo-random block, then encrypt normally with a block cipher in ECB mode. This is called ECB-OFB [see Section 15.4].

- Since CBC and CFB are error-recovering modes, you can use all the first block or two in the sector to generate the IV for that sector. For example, the IV for sector 3001 may be the hash of all the first 128 bits of the sector's data. After generating the IV, encrypt normally in CBC mode. To decrypt the sector, you use the 64-bit block of sector as an IV, and decrypt the remainder of the sector. Then, using the decrypted data, you regenerate the IV and decrypt the first 128 bits.

- You can use a block cipher with a large enough block size that it can encrypt the whole sector at once. Crab [see Section 14.6] is an example.

## 10.5 HARDWARE ENCRYPTION VERSUS SOFTWARE ENCRYPTION

### Hardware

Until very recently, all encryption products were in the form of specialized hardware. These encryption/decryption boxes plugged into a communications line and.

### Table 10.5 Comparing File-Level and Driver-Level Encryption

| FILE-LEVEL ENCRYPTION | DRIVER-LEVEL ENCRYPTION |
| :--- | :--- |
| **Benefits:** | |
| Ease of implementation and use. | Temporary works, files, and so forth can be kept on the secure drive. |
| Flexible. | |
| Relatively small performance penalty. | |
| Users can move files between different machines without problems. | It is harder to encrypt-something. |
| | Dedicated encryption boxes can be shielded. |
| Users can move files between different machines without problems. | |

### Security Issues:

- Potential leakage through security.
- Bad implementations may allow chosen-plaintext.
- Lots of things can go wrong.
- Bad implementations allow chosen-ciphertext.

### Usability Problems:

- User has to figure out.
- There may be different passwords.
- There will be performance penalty.
