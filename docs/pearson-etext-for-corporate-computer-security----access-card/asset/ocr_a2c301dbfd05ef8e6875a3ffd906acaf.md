# Figure 8-27 Cryptographic Protection for E-mail

![](bbox=[0.11, 0.09, 0.7, 0.33])

also use transmission encryption when they send and receive e-mail, and unless the recipient also communicates securely with its mail server, there will not be end-to-end encryption.

# MESSAGE ENCRYPTION

For end-to-end security, the sender must encrypt the message, including the header, body, and attachments. Two popular standards for this end-to-end encryption are S/MIME and PGP (together with OpenPGP).

S/MIME and PGP encryption both use digital signatures, which require the receiver to know the sender’s public key. S/MIME (Secure/Multipurpose Internet Mail Extensions) requires a traditional public key infrastructure (PKI) with a central certificate authority and digital certificates. Figure 8-28 shows e-mail security settings in Microsoft Outlook using S/MIME.

Instead of a PKI, PGP (Pretty Good Privacy) uses circles of trust. If you trust Pat, and if Pat trusts Leo, then you may trust Leo. This is dangerous because if misplaced trust is present anywhere in the system, bogus public key /name pairs may circulate widely. PGP has had most success in person-to-person communication without corporate control.

# Figure 8-28 Microsoft Outlook Hashing and Encryption Options

![](bbox=[0.23, 0.69, 0.59, 0.95])