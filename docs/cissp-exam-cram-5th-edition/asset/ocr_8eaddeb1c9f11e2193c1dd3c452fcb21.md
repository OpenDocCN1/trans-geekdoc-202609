ISO 11889-1:2009 addresses TPM chips, which can also be used with other forms of data and system protection to provide a layered approach referred to as defense in depth. For example, a TPM chip can help protect a system, and another set of encryption keys can be stored on a user's common access card or smart card to decrypt and access the data set.

Another potential option that builds on this technology is self-encrypting hard drives (SEDs). SEDs are hardware that offers many advantages over non-encrypted drives, including the following:

+   **Compliance**: SEDs have the ability to offer built-in encryption, which can help with compliance laws that many organizations must adhere to.

+   **Strong security**: SEDs make use of strong encryption. The contents of an SED are always encrypted, and the encryption keys are themselves encrypted and protected in hardware.

+   **Ease of use**: Users only have to authenticate to the drive when the device boots up or when they change passwords/credentials. The encryption is not visible to the user.

+   **Performance**: As SEDs are not visible to the user and are integrated into hardware, the system operates at full performance and has no impact on user productivity.

Software encryption is another protection mechanism for data at rest. There are many options available, such as BitLocker and PGP. Software encryption can be used on specific files, databases, or even entire RAID arrays that store sensitive data. With any potential software option, the encrypted data must remain secure and inaccessible when access controls, such as usernames and passwords, are incorrect; in addition, the encryption keys must be protected, and they should therefore be updated on a regular basis.

**Caution**

Encryption keys should be stored separately from the data.