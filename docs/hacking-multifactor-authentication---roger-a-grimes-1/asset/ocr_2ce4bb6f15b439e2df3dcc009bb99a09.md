# Hacking Multifactor Authentication

Issuing Authorities

The entity that confirms the subject's identity before issuing them an authenticated logon is called the issuing authority (or credential service provider [CSP] or identity provider). The person or subject who is attempting to prove their identity to the issuing authority by undergoing identity proofing is known as the applicant.

Any organization that accepts the authenticated logon identity is called the relying party. A relying party must trust the issuing authority to confirm the identity of the subject before the authentication logon identity. There is essentially always a three-way trust (see Figure 2.4) established between the user, issuing party, and relying parties.

![](bbox=[0.095, 0.323, 0.428, 0.433])

**Figure 2.4:** Basic three-way identity triad

The user must trust the issuing party to be a reliable issuer of authenticated identities (or anonymity), and secure enough that the user can trust that other people will not be easily to use their identity. The relying parties must trust the issuing authority to do their verifying of the user's identity, least according to the scope of registration, claims, and authentication. Both the user and the issuing authorities must trust that the relying parties will use the identities as the subjects they expect to be and in a secure way. If many authenticated logons have been issued in error to fraudulent subjects or the authenticated identities are too easy to hack, none of the parties will trust a relying party or use each other.

When a subject is attempting to authenticate to a relying party, they are known as the *claimant*. The claimant presents their proof of identity ownership as determined and controlled by the issuing authority. A relying party that verifies the claimant's identity is known as the *verifier* and may be the subject's ultimate relying party, but can also be separate entities. After a claimant is proven to an identity, they are no longer “claiming” to someone. They are an authenticated identity or a *subscriber* to the relying party or verifier.

> NOTE All the terms associated with various phases of the authentication life cycle can be confusing, for interest, but if you do not get hung up on the different terms you read documentation documents use other documents. There isn't an agreed-upon set of terms for the various phases of authentication, which is confusing, but there are only a few terms for each phase ... it's a pain, but not impossible to follow one document's description versus another. Realize that different documents use different terms to describe the same thing.