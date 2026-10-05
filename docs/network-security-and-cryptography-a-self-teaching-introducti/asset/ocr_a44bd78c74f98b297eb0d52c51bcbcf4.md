overall package is called Enveloped Data. The steps required to prepare
an Enveloped Data are:

+   a. Generate Pseudo random session key for the chosen symmetric
encryption algorithm (3DES or RC2/40).

+   b. For each recipient, encrypt the session key with the recipient's
Public Key using the chosen public encryption algorithm.

+   c. For each recipient, prepare a Recipient-Info block that contains:

Recipient-Info block:

| Identifier of Recipient's Public Key Certificate |
| Identifier of the Algorithm used to encrypt the session key |
| Encrypted Session Key |

+   d. Encrypt the message contents with the session key, using the cho-
symmetric Encryption algorithm.

+   e. The Recipient-Info block, followed by the encrypted message con-
tents, constitute the Enveloped Data as follows:

Enveloped Data:

| Recipient-Info block (1) |
| Recipient-Info block (2) |
| - |
| Recipient info block (n) |
| Encrypted Message Contents |

![](bbox=[0.518, 0.563, 0.693, 0.715])

+   f. The Enveloped-Data block is encoded using base 64 (R64)
encoding.

2. Signed-Data: The Signed-Data block caters for multiple signatures. A
Digital Signature is formed by taking a message digest of the message
contents using the chosen message digest algorithm and then signing
t digest with the signer's private key using the chosen signa-
ture algorithm. The message contents plus signature are then encoded