using base64 transformation. A Signed-Data message can only be accessed by a recipient with S/MIME capability. The steps required to prepare a Signed-Data are:

+   a. Select a message digest algorithm (SHA or MD5) and compute a message digest of the message contents.

+   b. Encrypt the message digest with the signer's private key, using the chosen signing algorithm.

+   c. Prepare a Signer-Info block that contains:

Signer-Info block:

| Signer's Public Key Certificate |
| Identifier of the Algorithm used to generate the Message Digest |
| Identifier of the Algorithm used to encrypt the Message Digest |
| Encrypted Message Digest |

+   d. Prepare the Signed-Data entity that consists of:

Signed-Data block:

| Message-Digest Algorithm Identifier |
| Message Contents |
| SignerInfo |

The Signed-Data entity may also include a set of public-key certificates, sufficient to constitute a chain for the recipient to verify a signature on the signer’s public-key certificate.

+   e. The Signed-Data entity is encoded using Base64 transformation and then sent to the intended recipients.

To recover the signed message the recipient will reverse the Base64 transformation, obtain the signer’s public key from the signer’s public certificate, use the signer’s public key to decrypt the message digest ($m_1$), and compute the message digest of the received message contents ($m_2$). If $m_1 = m_2$ then the signature is deemed to be verified.

# 3. Clear Signed Data: It is similar to Signed Data with transformed, that the message contents can be viewed by a recipient not having S/MIME capability. But such recipients will not be able to verify the digital signature.