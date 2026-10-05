# Hacking Multifactor Authentication

+   - Every time the same input is hashed, it should result in the same hash output.
- No different inputs should result in the same hash output. This type of protection is called second preimage resistance.
- If the hash output, it should be nontrivial for anyone to derive the original content input. This type of protection is officially known as preimage resistance.

A good hash has all these attributes and, even under sustained attack, retains these protective capabilities. Collision resistance is related to and is similar to second-preimage resistance, but they are not the same. And being good at both does not guarantee preimage resistance because they are unrelated attributes. If a hash fails any of these tests, it is considered weak and should no longer be used.

Hash algorithms usually result in fixed-length hashes regardless of the input. Common hash lengths range from 128 to 256 bits. There are many different generally accepted standards over the years, including Message Digest 5 (MD5), Windows LANManager (LM), Windows NT (NT), and Secure Hash Algorithm-1 (SHA-1). All of these standards, for NT, are considered weak and broken. Today, the most popular hash algorithm is Secure Hash Algorithm-2 (SHA-2 or SHA2), although in 2015 NIST recommended that SHA-2's successor, Hash Algorithm-3 (SHA-3 or SHA3), be used because SHA-2 has been weakened over time for cryptographic attack improvements. So far, most people are still using SHA-2. SHA-2 has many different output sizes including 224, 256, and 512 bits. Hashing is often used as part of an authentication solution. Table 3.1 shows some hash outputs for the word "frog" using common examples

Table 3.1: Hash outputs for the word "frog"

| Hash algorithm | Hash result for "frog" |
|---|---|n| MD5 | 938C22CCD05F2B68C4287040CFC71 |
| SHA-1 | B3E0F6F2A1046CA6A85596C2831B6BD11345F36 |
| SHA-2 | 74FA5327C0F42947789D5E9984A16824986A59F170640CA90337BIDA1EE4 |
| SHA-3 (512) | 6EB693784D6128746291A3BBBFF799D28F77E18B1605C611E14AF2B39DEEE743D5F1721AC7436BE12CD62989063EE807F53EBE97D39DE2B5DS2B62 |

Hashes play a big part in authentication and many MFA solutions. Hashes are often used to digitally sign other messages that need to be verified on and to encode other secrets against easy eavesdropping.