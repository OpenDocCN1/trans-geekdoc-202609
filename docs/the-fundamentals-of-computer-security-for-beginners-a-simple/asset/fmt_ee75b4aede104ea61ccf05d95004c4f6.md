
# Cloud Security

Cloud security depends on provider reliability. Cloud service contracts must contain guarantees regarding the protection of the provider's infrastructure, maximum time to troubleshoot technical issues, data privacy protection, access via secure connections, and the ability to recover lost or deleted data. Connectivity to the Internet becomes a single point of failure since if the connection is lost, no more data is accessed.

## Data Protection

The data must be protected at all stages: during storage, use (reading and editing), network transfer, and memory disposal. Encrypting the data becomes a necessary operation. Encrypting all data on the disk protects it in case of theft and if you lose the key the data is not recoverable (e.g. `BitLocker`). Encryption of individual files is optional in some software. Databases may have partial encryption systems and, since databases can contain a lot of data, these systems only allow you to encrypt some of it, such as credit card numbers and personal data.

Encryption for certain types of data is required by law. Data disposal is equally important. Paper documents and storage media must be thrown away so that the data can no longer be recovered. Paper documents must be passed through the shredder or incinerated and storage media must be physically destroyed. You can reset the memories with special software even if the physical destruction gives more guarantees. There is the possibility of drilling or degaussing, i.e. the application of a strong magnetic field that resets all data.

## Hardening of Mobile Devices

The hardening of mobile devices is similar to that of the PC. You have to disable unused services and connections, install antimalware, protect access (disable the screen after a period of inactivity, unlock via `PIN`), and impose conditions of use (e.g. do not install unsecure applications). Devices contain email, files, personal contacts, passwords and other sensitive information, so it is important to encrypt the memory. On iPhone there is an automatic hardware encryption system based on `AES` with 256-bit key. `GPS` tracking helps you find lost or stolen devices. When the lost or stolen device is located you can show a message on the screen to lock it with a code or make it sound and if you can't recover it you can erase the data remotely.

Other risks associated with using mobile devices are related to `Bluetooth`. `Bluejacking` causes you to receive spam messages via `Bluetooth` when the device is set as visible. `Bluesnarfing` is an unauthorized access to the mobile device's memory from a bug in the very first `Bluetooth` implementations, so remember to turn off `Bluetooth` when not needed. `NFC` (Near Field Communication) allows two devices to exchange data when in contact and, given the required proximity, no authentication is needed. `NFC` is a potential vector of attack because an attacker can approach his smartphone to our smartphone to pair them and then copy our data via `Bluetooth`.

The Bring Your Own Device trend is increasing (`BYOD`). Users' personal devices are neither controllable nor configurable by the company and therefore it is appropriate to require users to accept specific conditions if they want to use their devices at work (activate tracking systems using secure `VPN` and do not take photos in the company). `BYOD` should be considered when implementing the network.

## Encryption

### Cryptography History

Cryptography is the art of hiding information. It has very ancient origins, about 4000 years ago. Caesar used a rotation mechanism to encrypt messages (`rot` method), for example, the letters ABCDE correspond respectively to DEFGH, so the encrypted version of DAC is GDF.

### Encryption Process

The encryption process requires:

- **A)** Plain text to hide.
- **B)** The encryption algorithm
- **C)** The key
- **D)** The cipher text

### Types of Encryption

#### Physical Encryption

It can be done either by substitution (substitution of message characters as in Caesar's `rot`) or by transposition (subdivision of the message into blocks by changing the order, e.g. anagrams).

#### Mathematical Cryptography

It plans to alter the data with hashing.

#### Quantum Cryptography

It provides for the transmission change polarity when intercepted by hiding the original data.

### Hashing

Hashing is a mathematical function and is used to check whether what has been sent and received matches. The hash does not go back to the original value. When you download a file it happens that the manufacturer publishes the hash file in such a way that, once you download the file, you can calculate the hash that should match the one published by the manufacturer on the site otherwise the file may have been altered. The hash is used to ensure file integrity and protect your password during transmission or storage. Hash algorithms can lead to collisions (several input same output) and the longer the hashes the less collisions are generated. The hash ensures that a file is not modified, but not that the file is not opened or copied.

The hashing algorithms are:

- `MD5` (Message Digest 5) which generates 128-bit hashes
- `SHA` (Secure Hash Algorithm) which can generate up to 160-bit (`SHA-1`) and 256 or 512-bit (`SHA-2`)
- `RIPEMD` (RACE Integrity Primitives Evaluation Message Digest) which generates 128-bit hashes but is not very secure (the new version uses 160-bit)

### Symmetric and Asymmetric Encryption

Encryption can also be symmetrical or a mathematical procedure of polarized photons that asymmetrical. To make cracking the key even more difficult, some algorithms add a randomly generated and different number for each packet/message (`PRNG` - Pseudo Random Number Generator). The number that is generated in this way, called initialization vector (`IV`), or `nonce`, is then communicated in clear to the recipient.

Symmetric encryption uses the same key to encrypt and decrypt the message. Care must be taken when exchanging the key and a channel other than the communication channel must be used (better to exchange it in person). Underlying symmetric encryption is usually the `XOR` operation (between key and message). Modern algorithms use mechanisms that confuse the end result to preserve the confidentiality of the message (confusion).

Symmetric ciphers are distinguished between:

#### Flow Ciphers

The best known is the `RC4` (Rivest's Cipher) which uses keys between 40 and 2048-bit.

#### Block Ciphers

They cipher whole blocks of bits and are the most used algorithms. Among them we find:

- `DES` (Data Encryption Standard) which uses 56-bit keys (used in the 70s)
- `3DES` (Triple-DES) is an upgrade of `DES` and applies encryption 3 times
- `AES` (Advanced Encryption Standard) which is recognized as the best choice and uses variable keys of 128, 192 or 256 bits

### Block Cipher Modes

Block ciphers can be used in multiple modes:

#### ECB (Electronic Code Book)

The Electronic Code Book consists of applying the algorithm as it is: the message is divided into blocks that are encrypted one at a time.

#### CBC (Cipher-Block Chaining)

The Cipher-Block Chaining works like this: after the first block has been encrypted, it is `XOR`ed with the second block in clear and the result is then encrypted resulting in much more confusion.

#### CTR (Counter Mode)

The Counter Mode consists of using a series of values, encrypt those values with the algorithm and then `XOR` between the result and the plain text.

#### GCM (Galois Counter Mode)

Galois Counter Mode works like the previous one but adds the use of a hash on the encrypted text to verify that it is intact and that it comes from an authenticated sender.
