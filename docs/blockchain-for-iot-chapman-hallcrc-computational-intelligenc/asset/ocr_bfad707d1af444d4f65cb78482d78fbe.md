public key and related information performs signature validation using the public key of CA. Validation ensures that the certificate’s public key belongs to the individual whose information is included in the certificate.

# (ii) Tokens

If a client’s public key is stockpiled within digital certificates, hidden private key accompanying it may be saved in the client’s device. Storing keys is not common practice. An intruder who gains access to the machine can easy open and use the private key. As a result, the private key is held on an encrypted removable storage token that requires a password to access. When it comes to storing keys, various vendors use a variety of formats, some of which are licensed.

# (iii) Certificate Authority (CA)

The CA disputes a certificate for each customer as well as helps other clients validate it. The CA is responsible for properly identifying the client requesting a certificate, as well as ensuring that the details provided within the certificate are appropriate and signing is done. The following are the main functions of a CA:

+   Creating a Pair of Keys – CA can create a key pair on its own and/ or in collaboration with the user.

+   Creating and Delivering Digital Certificates – CA can be compared to a passport agency in terms of PKI. After the client presents the credentials to validate its distinctiveness, CA then issues a certificate, which is then signed by the CA to keep it from being altered.

+   Certificate Dissemination – When the client or user is being located, CA publishes the client’s certificate. This can be accomplished either by disseminating the certificate in publicly available directory or by providing it only to a particular client.

+   Certificate Authentication – CA allows its public key accessible to aid in the sign verification in the authentication process of clients’ certificate.

+   Cancellation of Certificate – CA can remove a certificate issued for a variety of reasons, including the user’s compromise of the private key or a lack of confidence in the client. After removal, the CA keeps a registry of all revoked certificates that are still valid.