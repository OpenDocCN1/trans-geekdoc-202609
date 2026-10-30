a single file via an unprotected channel such as e-mail can be done securely with single-file encryption.

# Removable Media

Removable media, by its very nature, can be moved to another location, making the securing of the data stored on the device essential. Again, encryption becomes the tool of choice, and a wide range of encryption methods and applications support the protection of removable media. Microsoft BitLocker, built in to current editions of its Enterprise, Ultimate, and Pro OSs, offers the ability to protect data stored on removable media.

# Mobile Devices

Mobile device security, covered in detail in Chapter 18, is also essential when critical or sensitive data is transmitted to mobile devices. The protection of mobile devices goes beyond simple encryption of the data, as the device can act as an authorized endpoint for the system, opening up avenues of attack.

# Hardware-based Encryption Devices

Hardware-based encryption devices are designed to assist in the encryption/decryption actions via hardware rather than software on a system. Integration of encryption functionality via hardware offers both performance and security advantages for these solutions.

# TPM

The *Trusted Platform Module (TPM)* is a hardware solution on the motherboard, one that assists with key generation and storage as well as random number generation. When the encryption keys are stored in the TPM, they are not accessible via normal software channels and are physically separated from the hard drive or other encrypted data locations. This makes the TPM a more secure solution than storing the keys on the machine’s normal storage.

# HSM

A *hardware security module (HSM)* is a device used to manage or store encryption keys. It can also assist in cryptographic operations such as encryption, hashing, or the application of digital signatures. HSMs are typically peripheral devices, connected via USB or a network connection. HSMs have tamper protection mechanisms to prevent physical access to the secrets they protect. Because of their dedicated design, they can offer significant performance advantages over general-purpose computers when it comes to cryptographic operations. When an enterprise has significant levels of cryptographic operations, HSMs can provide throughput efficiencies.

![](bbox=[0.174, 0.856, 0.253, 0.904])

> **EXAM TIP**  Storing private keys anywhere on a networked system is a recipe for loss. HSMs are designed to allow the use of the key without exposing it to the wide range of host-based threats.