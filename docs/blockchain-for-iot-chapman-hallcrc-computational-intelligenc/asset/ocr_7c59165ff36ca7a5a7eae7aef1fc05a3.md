Private Key Confidentiality – Private keys essentially ensure undisclosed among whole entities apart from the data owner and allow utilization of the key during its lifecycle.

Ensure Security of Shared Keys –Public keys are known to everyone, and any sender can use those receivers’ public key to encrypt the data to be communicated securely without sharing the private keys. This encryption using receiver’s public key is based on discrete logarithmic problem, as it is difficult to find the private key of the sender. Moreover, it also is not guaranteed that the accompanying public keys will be accurate. As a result, public key management [14] must place a greater emphasis on ensuring that public keys are used for their intended purpose.

PKI ensures the security of shared keys. It allows for the identification and distribution of public keys. The following components make up the PKI composition.

+   - The term “digital certificate” refers to a public key certificate.
+   - Tokens for private keys.
+   - Certification Authority (CA).
+   - Registration Authority (RA) – The authority in charge of registration.
+   - System for managing certificates.

# (i) Digital Certificate

A certificate can be compared to identification card of a person, such as a driver’s license, voter ID, or a permit, in terms of proving one’s identity. Digital certificates are given not only to individuals but also to computers, software packages, and everything else that requires proof of its distinctiveness in a massive environment.X.509 is a digital certificate based on the International Telecommunication Union (ITU) X.509standard. It specifies a regular format of a certificate to be issued for public key infrastructure, authentication, and authorization of certificates.

The certification authority (CA) or expert holds the global public keys pertaining to the user account in digital certificates, including further related information of the client and its usability. The whole information is digitally signed by CA, and the certificate contains a digital signature. Anyone who requires confirmation about a client’s