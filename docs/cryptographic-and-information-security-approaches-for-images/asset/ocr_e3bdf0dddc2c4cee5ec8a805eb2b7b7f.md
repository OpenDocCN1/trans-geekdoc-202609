![](bbox=[0.11, 0.1, 0.88, 0.23])

Figure 25.6 Combinations of private key and public is used to generate a digital signature.

The main purpose is to create a secure digital identity reference using this component of blockchain technology. Identity is based on possession of a combination of private and public cryptographic keys.

As shown in Figure 25.6, by combining these private keys and public keys, an extremely useful and powerful digital signature can be created. And in turn, this digital signature is used to provide strong control of ownership of the data.

# Peer-to-peer network:

Cryptography does provide strong control of ownership but it is not enough to make the digital relationships secure. Authentication problem is solved using cryptographic keys, but we also need some kind of authorization. In blockchain it is done using distributed network.

The key benefit of a distributed network is that nodes witness every transaction that takes place on the network. It can be better understood using an example; suppose we have a very big hall with a hundred people in it and there are thousands of cameras installed to capture or record every move of the people. Now, if one person in the hall gives something to another one, it is going to be recorded in the cameras’ memory. Similarly, in blockchain, there are nodes on the network which act as validators, like the cameras in the example provided. These nodes reach a consensus state that they have witnessed a transaction at the same time on the blockchain. They use some mathematical verification for this purpose.

This explains one thing, that the size of the network matters and is important to make itself secure. More the number of nodes on the network, more secure the network will be. The process starts with person A taking its private key and making an announcement that he/she is sending some money and attach it to person B’s public key.

A block is then created using a time stamp, digital signature and other relevant information which is then broadcasted to every node on the