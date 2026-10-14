
## 2. Each general may have a different role to play to succeed in the plan. This may be agreed upon.

## 3. Consensus is reached without the need of a leader.

This has implications on the real world because in most matters when an agreement needs to be made, a central trusted authority is needed. So, the implications of this go beyond payments.

As an example, if we want to build a cab aggregator network, there will be riders, drivers, car owners, and the car itself. All four of them need to get into an agreement in the form of consensus rules written in the form of smart contract, where:

1. The driver will carry the rider to his specific location in the least time-consuming path,
2. The car will be maintained by the owner and gas will be filled whenever needed by the driver,
3. The rider will pay the car owner after reaching the destination, and
4. The driver will get his monthly salary from the car owner.

Even though there is a clear distinction between driver, rider, car owner, and car, once the rule of agreement is established, each one is equal in rank. The records of each transaction are kept in an immutable sequence of records, ensuring easy audit. No central authority is needed to lead the platform.

The following figure shows a car aggregator network:

![](images/Figure-2.4.jpg)

**Figure 2.4:** Decentralized car aggregator network

# Bitcoin as a solution to Byzantines general problem

In order to solve this problem, Bitcoin needs to:

* Maintain all transactions in an immutable sequence of records in the order of their occurrence.
* Make sure that transactions are easily verifiable in terms of immutability and order and any consensus rule or contract.
* Be able to resolve any race condition that may arise because two records are generated at the same time.
* Move messages quickly so that the race condition mentioned earlier does not make confirmation time longer.

This is the reason Bitcoin has the following characteristics:

* **Proof-of-work** makes transactions immutable by attaching cost on its creation.
* **Blockchain** is made up of blocks having transactions such that each block knows the previous block, and each block is arranged in time sequence.
* Bitcoin **proof-of-work algorithm** makes it **easy to verify** blocks but exceedingly difficult to create them. This ensures that Transactions are propagated fast enough so that race condition leading to the creation of blocks by two distant nodes simultaneously is solved by the time the block reaches a depth of six.
* Each transaction is linked to a previous transaction by **cryptography** and script enforcing order, consensus rules, and contract.
* **Validating nodes** or **Full nodes** are like observers watching matches played by the Bitcoin miners. They don't confirm a transaction by creating a block and adding the transaction to the block by the **proof-of-work algorithm**. Instead, they verify all the consensus rules, smart contract clauses, time sequence of blocks, sending of bitcoin from sender to receiver, and funding of bitcoin from the previous transaction.

# Bitcoin property as a digital asset

The Bitcoin network needs to collect fees so that it can fund the cost of mining as mining is the **proof-of-work** that secures the network. Satoshi devised an intelligent way to achieve this:

* When a miner solves the cryptographic puzzle needed to mine a block, he is paid in newly minted bitcoin. This reward reduces by half after every 210,000 blocks are mined, that is, around 4 years.
* Later, as the network becomes valuable, miners will charge fees to include the transaction in a block.

This ensures that bitcoin supply is perfectly inelastic, which means its supply is predetermined. Bitcoin supply is also reducing at an exponential rate, which means when it becomes popular, there won't be enough supply.

Block reward has reduced from 50 ![](images/Bitcoin.jpg) at the inception to 6.25 ![](images/Bitcoin.jpg) at the time of authoring this book, and network fees have gone up significantly from zero at the beginning. This has made Bitcoin less attractive for speculation.

Bitcoin is also highly divisible with **satoshi** as the lowest denomination, which has the following value:

![](images/53.jpg)

Bitcoin does not require intermediaries, which makes it the digital equivalent of physical cash.

Bitcoin is neither a privacy coin, nor does it disclose your identity. Characteristics of privacy in Bitcoin can be understood as follows:

* Bitcoin does not link a person to an identity; instead, bitcoins are attached to addresses.
* Bitcoin can be bought from exchanges, miners, or a person directly. This makes bitcoin difficult to track.
* Bitcoin can be bought from exchanges. Most exchanges follow **KYC** norms and so, link identity with the address. When we transfer our bitcoin from an exchange, it is aware of receiving addresses.
* All transactions in the Bitcoin blockchain are transparent, contain information such as the previous transaction, paid to address, and amount of funding address and receiving address. This way, each transaction has a history that can leave clues of the sender or receivers' identity.
* There are a few techniques that can make finding identity quite difficult.

Overall, Bitcoin privacy is a very personal thing. Consequently, when government regulates bitcoin and incentivizes its use, Bitcoin addresses become more transparent and easier to track, but when government penalizes its users, Bitcoin addresses become opaque and more difficult to track. This makes Bitcoin censorship-resistant.

Bitcoin is on the network, and wallets only hold its private keys. This makes bitcoin location-independent and so, easily transferable between people at opposite ends of the globe.

Bitcoin value is decided at exchanges. Since it is easy to transfer bitcoin anywhere in the world, its value in every currency is nearly the same. In some cases, when government imposes restrictions on cryptocurrency or when there is currency control on local currency, bitcoin value can be a bit higher than the international value.

Bitcoin is a number on the network associated with an address. If an address is linked with criminals or hackers, exchanges may block such addresses, and it can affect the value of that bitcoin in the next transaction. But in a later transaction, if it is mixed with other bitcoin, then it becomes indistinguishable from any other coin. Since bitcoin is almost never distinguishable, it makes them quite fungible.

All valid Bitcoin transactions are either in **mempool** (in memory of each full node on the Bitcoin network) or in blockchain. These are verified by nodes. Anyone can view a transaction by either having a node or by looking at one of the popular websites.

This gives bitcoin the following properties:

* Scarce
* Divisible
* Censorship-resistant
* Easily transferable
* Fungible
* Verifiable

Also, it makes Bitcoin:

* Less suitable for speculation
* More suitable for holding or saving

# Conclusion

In this chapter, we looked at the history of developments in cryptography that led to the development of Bitcoin. Then, we looked at the timeline since the time whitepaper was published till the authoring of this book.

After this, we defined Bitcoin and the game theory problem the Byzantine generals problem it solves. You learned how it solves the game theory problem and how the solution to the problem can change the fundamental structure of organizations. We then used this knowledge to list the fundamental characteristics of bitcoin.

In the next chapter, you will understand the structure of the Bitcoin network. We will relate each part of the network to the fundamentals of Bitcoin we learned in this chapter.

# Points to remember
