
## 4.5 SUCCESS STORIES

### 4.5.1 LaVis Wine

Counterfeit is a major problem for the wine industry. People want to be assured of what they are drinking especially when they are paying so much for each bottle. Ernst and Young (EY) has been the blockchain implementation partner for LaVis. LaVis is claimed to be one of the first to sell blockchain-certificate wine using EY Ops Chain9. The blockchain contains all details related to the story of the wine starting from the type and quality of the grapes, to the date of bottling and the quality of the sulfates. Each time the bottle changes hands between the producer to the wholesaler to the retailer, the status is updated.

### 4.5.2 TReDS Bill Discounting

TReDS or Trade Receivables Discounting System which is an RBI10 approved platform for discounting bills for MSMEs, has started using blockchain11. This allows them to broadcast information across a shared network where not only is all information in the public domain, it is also sensitive as it deals with financials.

Blockchain allows them to operate while protecting privacy.

### 4.5.3 Travel Insurance

Axa has partnered with Fizzy to provide travel insurance on blockchain. As mentioned above, blockchain is at the back end and the insured have little or no visibility on that. The process of getting flight insurance or to get any insurance for that matter has always been easy. The problem is at the time of claims. Blockchain is solving that component. Insurance pays off in the event of that condition being met. The insured is supposed to file a claim and then that claim is processed internally by the insurer and payment is released. In case of flight insurance, the insured and the insurer check as to whether the flight was delayed by two hours or more, or cancelled altogether. The advantage in this case is that as soon as a flight is delayed by two hours, the information is relayed at the same time to the insured and the insurer. And since it is coded on Ethereum smart contracts, that information triggers payment of the sum insured without any human intervention. Even if the insurer wants, they cannot edit the contract once it is on the system. The contract address is: 0xdc3d8fc2c41781b0259175bdc19516f7da11cba7 which can be accessed on etherscan.io and other such options for Ethereum Blockchain. Anyone can view the contract and the code.

The link to the website is https://fizzy.axa-en-gb/

Other good insurance use cases can be found at https://builtin.com/blockchain/blockchaininsurance-companies

### 4.5.4 SWEDEN LAND RECORDS

Since land record titles are susceptible to minor forgeries and clerical errors, the Swedish government has decided to experiment12 with the use of blockchain. It is called Lantmäteriet. Instead of signing papers, people could use digital signatures. Since these can be validated online, a transaction can be concluded. The system operates on a private blockchain and includes land registry and other parties that hold land records such as banks. However, even this system does not act like cryptocurrency where high-value transactions are easy. Nevertheless, just by removing paperwork and preventing forgery, Sweden would save more than $100 million.

## 4.6 CHALLENGES

### 4.6.1 DIGITIZATION

Driving licenses can be put online in a cryptic form only to check validity and if there have been any challans in the past due to traffic violation. This would allow insurers to decide premium based on the driving history of the person. The problem with this solution is that all the driver’s license data is not available in one online database that is accessible and compatible with other databases.

Firstly all data would have to be digitized with a collaborative architecture. This is an exercise that has been undertaken in many developed economies and efforts for this are under way in India as well.

### 4.6.2 PROPERTY RECORDS COMPLETE

Property records on blockchain would ensure that there is no amendment to land ownership without consent (and in some cases, corresponding payment to the seller). The problem with this approach is that it is only prospective. In order to be retrospective, the land records have to be clean in the first place. In the absence of this, the legacy data cannot be digitized on to blockchain. While this may seem very simple it is not so. Even some of the best States in Government of India’s Ease of Doing Business Ranking do not have even two years’ worth of property records and transactions digitized13. Property is fraught with disputes, some in civil courts and others in criminal courts. It is mortgaged, pledged and rented. There are cases subject to Wills, Gift Deeds and Sale Deeds. This leads to too many ownership disputes. If this is not free of errors and disputes, it cannot be put on the blockchain as they would then be immutable.

### 4.6.3 NEED FOR SCALE

The benefits will only arise once the entire platform is on the system. We need everyone to use it. Imagine using emails only to find out that you need to take a print of each communication, respond in writing and each response will then be digitized. It would not add any value, right? Similarly blockchain will add value if all processes are present on it. Therefore the need for scale is high to unlock value.

### 4.6.4 CODERS

The main platforms at the moment are

- 1. Hyperledger: by IBM
- 2. Corda R3: industry collaboration initiative with leading organizations as partners
- 3. Solidity: Ethereum blockchain
- 4. Others such as MultiChain, SmartChain and other chains: platforms to create your own blockchain

While Hyperledger and Corda require mostly Java knowledge, Solidity and other platforms require more sophisticated knowledge. There is a dearth of people who understand blockchain architecture and can implement it. Coders are in short supply for the entire industry but more so for blockchain.

### 4.6.5 SMART CONTRACTS

**Oracles:** smart contracts require Oracles. These Oracles are assumed to be sources of truth for a contract to get executed. For smart contracts to be a reality, we would need many more Oracles. We would also need more reliable and consistent Oracles. For example, flight.com is a reliable source for flight data. However, it can get hacked. There might be an internal maintenance issue. The server might be down or it could have bugs. Since it is owned privately, one cannot rule out any interference. These issues hamper trust.

**Non-repudiability** of smart contracts is a welcome feature in many cases. However, in certain cases it can prove to be problematic. If someone were inebriated or under duress while they were writing a smart contract, it could have difficult consequences. The best software from the biggest companies also suffers from bugs. It is inconceivable that no smart contracts would have bugs. Further, both parties may agree to dissolve the contract, or there could be a *force majeure*. In these cases we would need an escape chute from the non-repudiable smart contract which is not possible currently.

## 4.7 DO IT YOURSELF

### 4.7.1 HYPERLEDGER

Click and Build platforms such as Hyperledger by IBM are available free of cost for enthusiasts. The online program is free for all and leads to a decent working knowledge of the platform. The course helps you develop a small blockchain for trading cars. It does not require any coding experience. In order to build something useful for an organization, it has a Java component that needs to be understood and coded. However, this is a good place to start if you want to understand and see it in action.

Coursera and a number of other learning platforms provide free learning content hosted at www.coursera.org/lecture/blockchain-platforms/hyperledgerpart-1-87Qz4.

### 4.7.2 BITCOIN

Although Bitcoin and trading in any form of crypto is not recommended in India, it is possible to look at the blocks. Since it is open, you can look at all the blocks ever created. The hash of each block is available. If you click on one of these, you will see the number of transactions in each block which contains the amount of bitcoins transferred, the sender’s address and the receiver’s address14. For each address, you can also view the history of all transactions made by that address along with dates.

Each block also identifies the username of the miner (the one who successfully solved the mathematical problem before everyone else) as well. This miner would have received a reward for doing this as well. This keeps miners motivated and therefore the system has an in-built reward within it. Each block is about 1.2 Mb. The block height or the number of the block is in the 6,00,000 series. All these transactions would roughly add up to 72 Gb of data. Since all the transactions on each block are hashed, the entire chain, without the record of the transactions would occupy less than 1 Mb of space. This allows the system to be scalable.

Everything about bitcoin transactions is public. The identities of the sender and the receiver are encrypted. Each wallet (of sender and receiver) has multiple unique hashed identities. This ensures that no one can trace previous transactions to one person.

The same is true for all crypto currencies. The famous ones with higher volumes have their ledger accessible from multiple websites.

### 4.7.3 ETHEREUM BLOCKCHAIN

Ethereum has been a successful blockchain in terms of diversifying beyond a currency. At time of writing it is considered to be the default platform for coding DAPPS (stands for Distributed Applications). Solidity is the platform where smart contracts can be coded on to the Ethereum blockchain. Learning Solidity has been made easy by CryptoZombies.io. This platform offers a gamified system of learning how to code for Ethereum. The course is free and has levels that one progresses through in the journey of dealing with zombies.

### 4.7.4 GENERATE A HASH

There are a number of hashing algorithms. They have varied complexity. Some have a private key that can be changed for each transaction.

If you are familiar with the statistics software called R, then you can try out digest package to generate hashes. You can use the following code to generate the hash for any content hmac ("PrivateKey", "Content", algo = "sha256").

You can change the Private Key to anything you want. The content can be whatever you want. The algorithm can be specified to any out of sha1, sha256, sha512, crc32, md5. These would all generate a different hash of the same content but would be internally consistent.

Alternatively, you can visit www.sha1-online.com/ to hash anything you type.

You can hash images as well. Right click any image file and click on Open With... and click Notepad or any text editor. You will see the textual representation of the image. It is this text that would be hashed. Try editing this image in Paint or any other picture editing software. You could add a small dot, that might even be imperceptible
