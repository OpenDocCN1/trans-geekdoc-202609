The standard notation for representation of a certificate is C<<A>>, which implies a certificate issued to user “A” and signed by certification agency “C”.

The users act as CAs for each other. For example, User “A” issues Certificate A<<B>> to User “B” and User “B” issues Certificate C<<A>> to User “A”. User “D” has been issued Certificate B<<D>> by user “B”. User D will have access to the Public Key of User “B” so that “D” can verify “B’s signature on its certificate.

# 10.4 CREATION OF CERTIFICATES’ CHAIN FOR CA’s SIGNATURE VERIFICATION

Suppose “D” has to communicate with User “F”. Then User “D” will obtain F’s Public Key Certificate C<<F>>. Now will “D” verify C’s signature on this certificate, since “D” does not have access to “C’s Public Key? For this, “D” will obtain the following additional certificates and create a certificate:

B<<A>> A<<C>> C<<F>>

Now, “D” will obtain user C’s Public Key from certificate A<<C>> and use that Public Key to verify user “C’s signature on certificate C<<F>>. Then “D” will obtain user A’s Public Key from certificate B<<A>> and use that to verify user “A’s signature on certificate A<<D>>. Regarding verification of user B’s signature on certificate B<<A>>, the user “D” has direct access to B’s Public Key. Thus, by creating a chain, user “D” is able to verify the digital signature on certificate C<<F>>.

Similarly, “F” will obtain certificate B<<D>> and verify user “B’s digital signature on that certificate by creating the following chain:

C<<A>> A<<B>> B<<D>>

Now, both “D” and user “F” have successfully verified the digital signatures on the certificates required for their communication. Thus, they can communicate with each other using each other’s Public Key.

# 10.5 REVOCATION OF X.509 CERTIFICATES

An X.509 Certificate can be revoked by the Issuer Certification Agency (CA) by listing the X.509 Certificate in a “Certificate Revocation List” (CRL), which is periodically issued by the CA. The CRL is signed by the concerned CA.