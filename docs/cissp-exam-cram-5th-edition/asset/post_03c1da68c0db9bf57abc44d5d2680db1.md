
> **ExamAlert** Expect to see CISSP exam questions that deal with the workings of PKI. It’s important to understand that the RA cannot issue certificates.

## Certificate Revocation Lists

Just like driver’s licenses, digital certificates might not always remain valid.
(I had a great aunt who drove with an expired license for years. In her case,
she was afraid that at 95 years old, she might not pass the eye exam.) In
corporate life, certificates might become invalid because someone leaves the
company, information might change, or a private key might become
compromised. For these reasons, the CRL must be maintained.

The CRL is maintained by the CA, which signs the list to maintain its
accuracy. Whenever problems with digital certificates are reported, those
certificates are considered invalid, and the CA has the serial number added to
the CRL. Anyone requesting a digital certificate can check the CRL to verify
the certificate’s integrity. The replacement for CRLs is the Online Certificate
Status Protocol (OCSP); it has a client/server design that scales better than a
CRL. When a user requests access to a server, OCSP sends a request for
certificate status information. The server sends back a response of current,
expired, or unknown. Regardless of which method is used, problems with
certificates are nothing new; to read about the problem Dell had in 2015, see
www.infoworld.com/article/3008422/security/what-you-need-to-know-about-dells-root-certificate-security-debacle.html.

## Digital Certificates

Digital certificates are at the heart of a PKI system. A digital certificate
serves two roles:

- It ensures the integrity of the public key and makes sure the key
  remains unchanged and in a valid state.
- It validates that the public key is tied to the stated owner and that all
  associated information is true and correct.

The information needed to accomplish these goals is added to the digital certificate. Digital certificates are formatted to the X.509 standard, whose most current version is Version 3. One of the key developments in Version 3 is the addition of extensions. Version 3 includes the flexibility to support other topologies. It can operate as a web of trust, much like PGP. An X.509 certificate includes the following elements, and examples showing some of these elements are provided in Figure 4.21:

- Version
- Serial number
- Algorithm ID
- Issuer
- Validity
  - Not before (a specified date)
  - Not after (a specified date)
- Subject
- Subject public key information
  - Public key algorithm
  - Subject public key
- Issuer—unique identifier (optional)
- Subject—unique identifier (optional)
- Extensions (optional)

Digital certificates play a vital role in the chain of trust. Public key encryption works well when you are dealing with people you know because it’s easy for you to send each other a public key. But what about communicating with people you don’t know?

Digital certificates are used to prove your identity when performing electronic transactions.

![](img/cd307d33c10f35ada49ea76811ef60ad_299_0.png)

FIGURE 4.21 X.509 Certificate

Although you might want to use an external certificate authority, doing so is not mandatory. You could decide to have your own organization act as a certificate authority. Regardless of whether you have a third party handle certificate duties or you perform them yourself, digital certificates typically contain the following critical pieces of information:

- Identification information including username, serial number, and validity dates of the certificates
- The public key of the certificate holder
- The digital signature of the signature authority, which piece is critical because it certifies and validates the integrity of the entire package

## The Client's Role in PKI

It might seem that up to this point, all the work has fallen on the shoulders of the CAs; this is not entirely true, however. Clients are responsible for requesting digital certificates and for maintaining the security of their private keys. Loss or compromise of a private key would be devastating; it would mean that communications were no longer secure. If you are dealing with credit card numbers or other pieces of user identity, this type of loss of security could lead to identity theft.

Protecting a private key is an important issue because it’s easier for an attacker to target the key than to try to crack the certificate service. Organizations should concern themselves with seven key management issues:

- Generation
- Distribution
- Installation
- Storage
- Key change
- Key control
- Key disposal

Key recovery and control is an important issue that must be addressed. One basic recovery and control method is the M of N control method of access. This method is designed to ensure that no one person can have total control; it is closely related to dual control. Therefore, if N number of administrators have the ability to perform a process, M number of those administrators must authenticate for access to occur. M of N control should require physical presence for access. Here is an example: Suppose that a typical M of N control method requires that four people have access to the archive server and at least two of them must be present to accomplish access. In this situation, M = 2 and N = 4. This would ensure that no one person could compromise the security system or gain access.

Note

Many organizations use hardware security modules (HSMs) to securely store and securely retrieve these escrowed keys. HSM systems protect keys and can detect and prevent tampering by destroying the key material if unauthorized access is detected.

## Integrity and Authentication

One of the things cryptography offers to its users is the capability to verify integrity and authentication. Integrity assures a recipient that the information remained unchanged and is in its true original form. Authentication provides the capability to ensure that messages are sent from who you believed sent them and that messages are received by the intended recipient. To help ensure your success on the CISSP exam, review the integrity methods listed in Table 4.10.

## TABLE 4.10 Integrity Verification

| Method | Description |
| :--- | :--- |
| Parity | Simple error detection code for networking |
| Hashing | Integrity |
| Digital signature | Integrity, authentication, and nonrepudiation |
| Hashed MAC | Integrity and data origin authentication |
| CBC MAC | Integrity and data origin authentication |
| Checksum | Redundancy check, weak integrity |

## Hashing and Message Digests

Hashing algorithms function by taking a variable amount of data and compressing it into a fixed-length value referred to as a *hash value*. Hashing provides a fingerprint or message digest of the data. Strong hashing algorithms are hard to break and will not produce the same hash value for two or more messages. Hashing can be used to meet the goals of integrity and/or nonrepudiation, depending on how the algorithms are used. Hashes can help verify that information has remained unchanged. Figure 4.22 provides an overview of the hashing process.

Hashing algorithms are not intended to be reversed to reproduce the data. The purpose of the message digest is to verify the integrity of data and messages. In a well-designed message digest, if there is even a slight change in an input string, the output hash value should change drastically. This is known as the avalanche effect. For example, the version of SolarWinds that is vulnerable to Sunburst has the MD5 hash value b91ce2fa41029f6955bff20079468448. This means if you were to match this hash to the version of SolarWinds, the version you are running would leave you exposed to the Sunburst malware. Another value would indicate that the version you have may not be vulnerable.

![](img/cd307d33c10f35ada49ea76811ef60ad_302_0.png)
