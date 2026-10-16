# **_Encryption_** [14]:

Blockchain Technology uses Hashing. Hashing of the transaction uses mainly the SHA-256 algorithm to secure the data. The public key of the sender, the transaction information, and the receiver's address are encrypted by the SHA-256 algorithm to generate the fixed-length encrypted information. This process of verification done in the Blockchain is called Encryption. Each of the users in the Blockchain has a private and a public key. A private key is used to authenticate the user and to confirm the origin of the transaction is legitimate. The public key of the user is the key that is shared across the peer network for verification of the transaction.

# **_Verification of the sender_**

Once the Hash key or a message digest is generated, a digital signature is created, and along with the private key, a digitally signed document is created. The original message, digitally signed document and a public key are sent to the receiver. The receiver retrieves the hash value from the digitally signed document along with the shared public key of the sender compared with the hash value created at the receiver side by considering the original message.

# **_Proof of Work_**

Validation of the data is done by using a method called Mining [15]. The miners determine the nonce value, i.e., the random value combines it with the hash of the previous block, rehash the value, and compare this to the target hash. If the miners correctly determine the hash value and if it is less than the target value, the transaction is said to be validated by the user and the block is added to the Blockchain, and the transaction is processed. If one of the miners can determine the nonce value and decrypt the information. The other users can just validate the transaction so that the block is added to the Blockchain. The mathematical puzzle required to find the right nonce value such that the generated hash value meets the requirement, say it has to be less than the target value, requires an enormous amount of computation power as it has to be done using the Brute force method. And such an enormous amount of computation can be attempted only by standard users. As the nonce value is “Number only used Once”, Proof of Work is used to determine that the transaction done by the user is only once and is depicted in Fig. (7).

# **_Smart Contract_**

To have a more secure and automatic machine-to-machine transaction in IoT, a Smart contract is built over the Blockchain [16]. Smart Contract is an executable script that allows the automatic execution of multiple steps: the agreement to be met and the transaction to be carried over by all the peers in the network. It