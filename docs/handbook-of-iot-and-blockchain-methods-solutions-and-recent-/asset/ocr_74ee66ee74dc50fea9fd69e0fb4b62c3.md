ever created. The hash of each block is available. If you click on one of these, you will see the number of transactions in each block which contains the amount of bitcoins transferred, the sender’s address and the receiver’s address¹⁴. For each address, you can also view the history of all transactions made by that address along with dates.

Each block also identifies the username of the miner (the one who successfully solved the mathematical problem before everyone else) as well. This miner would have received a reward for doing this as well. This keeps miners motivated and therefore the system has an in-built reward within it. Each block is about 1.2 Mb. The block height or the number of the block is in the 6,00,000 series. All these transactions would roughly add up to 72 Gb of data. Since all the transactions on each block are hashed, the entire chain, without the record of the transactions would occupy less than 1 Mb of space. This allows the system to be scalable.

Everything about bitcoin transactions is public. The identities of the sender and the receiver are encrypted. Each wallet (of sender and receiver) has multiple unique hashed identities. This ensures that no one can trace previous transactions to one person.

The same is true for all crypto currencies. The famous ones with higher volumes have their ledger accessible from multiple websites.

# ## 4.7.3 ETHEREUM BLOCKCHAIN

Ethereum has been a successful blockchain in terms of diversifying beyond a currency. At time of writing it is considered to be the default platform for coding DAPPS (stands for Distributed Applications). Solidity is the platform where smart contracts can be coded on to the Ethereum blockchain. Learning Solidity has been made easy by CrytoZombies.io. This platform offers a gamified system of learning how to code for Ethereum. The course is free and has levels that one progresses through in the journey of dealing with zombies.

# ## 4.7.4 GENERATE A HASH

There are a number of hashing algorithms. They have varied complexity. Some have a private key that can be changed for each transaction.

If you are familiar with the statistics software called R, then you can try out digest package to generate hashes. You can use the following code to generate the hash for any content hmac (“PrivateKey”, “Content”, algo = “sha256”).

You can change the Private Key to anything you want. The content can be whatever you want. The algorithm can be specified to any out of sha1, sha256, sha512, crc32, mda5. These would all generate a different hash of the same content but would be internally consistent.

Alternatively, you can visitwww.sha1-online.com/ to hash anything you type.

You can hash images as well. Right click any image file and click on Open With... and click Notepad or any text editor. You will see the textual representation of the image. It is this text that would be hashed. Try editing this image in Paint or any other picture editing software. You could add a small dot, that might even be imperceptible