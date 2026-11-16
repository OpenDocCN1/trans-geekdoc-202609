components of this framework include the following:

+   - The certificate authority (CA)
+   - The registration authority (RA)
+   - The certificate revocation list (CRL)
+   - Digital certificates
+   - A certificate distribution system

# Certificate Authorities

A good analogy for a CA is the Department of Motor Vehicles (DMV), a state entity that is responsible for issuing driver’s licenses, which are the known standard for physical identification. If you cash a check, go to a night club, or catch a plane, your driver’s license is one document that is widely accepted at these locations to prove your identity. CAs are like DMVs: They vouch for your identity in a digital world. VeriSign, Thawte, and Entrust are some of the companies that perform public CA services.

A CA doesn’t have to be an external third party; many companies decide to tackle these responsibilities by themselves. Regardless of who performs them, the following steps are necessary:

+   1. The CA verifies the request for certificate with the help of the RA.
+   2. The individual’s identification is validated.
+   3. A certificate is created by the CA, which certifies that the person matches the public key that is being offered.

# Registration Authorities

The RA is like a messenger: It’s positioned between the client and the CA. Although the RA cannot generate a certificate, it can accept requests, verify a person’s identity, and pass along the information to the CA for certificate generation.

RAs play a key role when certificate services expand to cover large geographic areas. One central CA can delegate its responsibilities to regional RAs around the world.