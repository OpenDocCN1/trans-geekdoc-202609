# 8.8 Backup Keys

An example of this system is IPS [881]. Users can either enter the 64-bit key or enter the key as a longer string. The system then generates a 64-bit key from the character string using a key-crunching technique.

Another solution is to store the key in a magnetic stripe card, plastic card with an embedded ROM chip (called a ROM key), or smart card [556,557,455]. A user could then enter his key by inserting the physical token into his encryption box or attached to his computer terminal. While the user can use the key, he does not know it and cannot compromise it. He can use it only in the way and for the purposes indicated by the control vector.

A ROM key is a very clever idea. People understand physical keys, what they signify and how to protect them. Putting a cryptographic key in the same physical format makes storing and protecting that key more intuitive.

This technique is made by splitting the key into two halves, one half in the terminal and the other half in the ROM key. The U.S. government's STU-III secure telephone works this. Losing the ROM key does not compromise the cryptographic key—change that and everything is back to normal. The same is true with the loss of the terminal. This way, compromising the ROM key or the system does not compromise the cryptographic key—an adversary has both parts.

Hard-remember keys can be stored in encrypted form, for example, an RSA key could be encrypted with a DES key and stored on disk. To recover the RSA key, the user has to type in the DES key to a decryption

If the keys are generated deterministically [with a cryptographically secure pseudorandom generator], it might be easier to regenerate the keys from an easy-to-remember password every time they are required.

Ideally, a key should never appear unencrypted outside the encryption device. This isn't always possible, but it is a worthy goal.

# 8.8 BACKUP KEYS

Alice is the chief financial officer at Sec., Ltd.—We don't tell you motto.” Like any good corporate officer, she follows the company's security guidelines and encrypts all her data. Unfortunately, she ignores the company's street-crossing guidelines and gets hit by a truck. What does the company's president, Bob, do?

Unless Alice left a copy of the key, she's in deep trouble. The whole point of encryption is to make files irrecoverable without the key. Unless Alice was a moron and used lousy encryption software, her files are gone forever.

Bob can avoid this is sometimes called key escrow [see Section 4.1]: He requires all employees to write their keys on paper and give the company's security officer, who will lock them in a safe somewhere [or encrypt them all with a master key]. Now, when Alice is bowled over the Interstate, Bob can ask his security officer for her key. Bob should make sure to have the combination to the safe somewhere; otherwise, if the security officer is run over by another truck, Bob will be out of luck again.