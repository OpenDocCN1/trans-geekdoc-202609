# # HAVAL

HAVAL is another one-way hashing algorithm that is similar to MD5. Unlike MD5, HAVAL is not tied to a fixed message-digest value. HAVAL-3-128 makes three passes and produces a 128-bit fingerprint; HAVAL-4-256 makes four passes and produces a 256-bit fingerprint.

# # Message Authentication Code (MAC)

A MAC is like a poor man’s version of a digital signature and is somewhat similar to a digital signature except that it uses symmetric encryption. MACs are created and verified with the same secret (symmetric) key. Four types of MACs exist: unconditionally secure, hash function based, stream cipher based, and block cipher based.

# # HMAC

Hashed-Based Message Authentication Code (HMAC) was designed to be immune to multi-collision attacks. This immunity was added by including a shared secret key. In simple terms, HMAC functions by using a hashing algorithm such as MD5 or SHA-1 and altering the initial state of the file to be processed by adding a password. Even if someone can intercept and modify the data, it’s of little use if that person does not possess the secret key. There is no easy way for the person to re-create the hashed value without it. For HMAC to be used successfully, the recipient would have to have acquired a copy of the symmetric key through some secure out-of-band mechanism.

# # CBC-MAC

A cipher block chaining MAC uses the CBC mode of a symmetric algorithm such as DES to create a MAC. CBC-MAC differs from HMAC in that CBC-MAC uses one algorithm, whereas HMAC uses two (a hashing algorithm and a symmetric block cipher). The last block of the message is used as the MAC authentication portion and is appended to the actual message.

# # CMAC

Cipher-Based Message Authentication (CMAC) addresses some of the