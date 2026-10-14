authentication. The source normally is a **certificate authority (CA)**,²⁴ which is an independent and trusted source of information about the public keys of true parties. Unfortunately, few countries regulate CAs, so the verifier must only accept digital certificates from certificate authorities it trusts by reputation.

Some well-known certificate authorities include but are not limited to IdenTrust (48 percent market share), Sectigo (24 percent), DigiCert (15 percent), and GoDaddy (7 percent).²⁵ In fact, corporations can issue their own digital certificates for internal use. Microsoft Windows Server® 2019 comes with the ability to issue and manage digital certificates.

By the way, a common misconception is that certificate authorities vouch for the honesty of the party named in the certificate. They do not! They merely vouch for the named party’s public key. Although customers who misbehave may have their certificates revoked, CAs rarely give strong warranties about the trustworthiness of their certificate holders. That is not their job. Their job is to associate a public key with a name.

> > When a CA gives a digital certificate to a person or organization, this does not mean that the CA vouches for the honesty of the party named in the certificate.
> > It merely asserts that a certain party has a certain public key.

**DIGITAL CERTIFICATE** The CA will send the verifier a digital certificate. Digital certificates follow the X.509 syntax. A **digital certificate** contains a number of fields, which are shown in Figure 3-18. Most importantly, the digital certificate contains the *name of the true party* (in the Subject field) and the *true party’s public key* (in the Public Key field as

| Field | Description |
|---|---|
| Version Number | Version number of the X.509 standard. Most certificates follow Version 3. Different versions have different fields. This figure reflects the Version 3 standard. |
| Serial Number | Unique serial number for the certificate, set by the CA. |
| Signature Algorithm ID | The digital signature algorithm the CA uses to sign its certificates. |
| Issuer Name | Name of the certificate authority (CA). |
| Validity Period | The period before which and after which the certificate should not be used. Note: Certificate may be revoked before the end of this period. |
| Subject Name | The name of the person, organization, computer, or program to which the certificate has been issued. This is the true party. |
| Public Key Algorithm | The algorithm the subject uses to sign messages with digital signatures. |
| Subject Public Key | The public key of the subject (the true party). |
| Other Optional Fields | . . . |
| Certificate Signature Algorithm | Algorithm used in the generation of the signature (e.g. SHA-256) |
| Certificate Signature | The digital signature of the certificate, signed by the CA with the CA's own private key. For testing certificate authentication and integrity. User must know the CA's public key independently. |

**Figure 3-18 X.509 Digital Certificate Fields**

²⁴ PGP (Pretty Good Privacy) uses a different method to get public keys. This method is called circles of trust. If I trust people, I place my list of trusted people and their public keys on a list and make this list available to others. This avoids the need to have a certificate authority. However, if one person is duped into placing an impostor on the list, this misplaced trust may spread quickly to other people.

²⁵ W3Techs, “Usage of SSL Certificate Authorities for Websites,” W3Techs.com, August 3, 2019. https://w3techs.com/technologies/overview/ssl_certificate/all.