
## 6. DeFi Index Funds, Insurance Products, and Supply Chain Finance

At present, DeFi is not mature enough to support sophisticated application in these areas, but innovation is rapidly emerging, especially in the insurance market.

It should be noted that from the second to the sixth level, the assistance of blockchain oracles (oracles connect blockchains to external systems) is required to provide authentic data. When different levels are combined, pay close attention to associated security issues. Following is a list of most widely exploited security vulnerabilities in the DeFi systems.

### Incorrect Liquidity Pool Calculations

When the value of tokens within the DeFi pool is priced, one of the most exploited forms of attack in DeFi smart contracts is the manipulation of price by hackers.

DeFi participants gain a stake of tokens when they invest in a pool, allowing them to extract value in the future. Rather than using an external oracle, some poorly designed DeFi protocol frequently computes the value of the tokens they hold depending on the present composition of the pool. Flash loan assaults take advantage of this by dramatically unbalancing a pool for the period of a transaction. This uneven pool causes the token's value to be calculated incorrectly, allowing the attacker to drain value from the pool. (Belt Finance, Rari Capital, and BurgerSwap are examples of protocols that have been exploited in this fashion.)

### Stolen and Leaked Private Keys

To manage the access to and control over blockchain accounts, blockchain technologies employ public key cryptography. The address of a blockchain account is derived from a public key that is connected to a private key. Any transaction conducted on that account's behalf must be digitally signed with the correct private key. As a result, private keys are the focus of numerous blockchain attacks. Keys can be stolen or compromised in a variety of ways, including:

*   **Compromised cryptocurrency wallets (like `MetaMask`).** `MetaMask` is commonly used to interact with and perform transactions on the Ethereum blockchain. Several DeFi users and projects – including the CEO of Nexus Mutual and the EasyFi project – have lost cryptocurrency when they used malicious versions of `MetaMask` installed on their machines.
*   **Leaked/stolen mnemonic phrase.** Mnemonic phrases are a common way to make private keys easier to remember or enter when recovering or setting up a new wallet. Some DeFi-related hacks have involved the theft or accidental exposure of these keys.
*   **Poor key generation.** Private keys should be generated using a secure random number generator. If these keys are generated improperly with a poor source of randomness, then an attacker may be able to guess them and gain control over a blockchain account.
*   **Phishing attacks on the private key.** Hackers usually target developers or top executives from prominent DeFi protocols to phish for private key. For example, in November 2021, the private key of BZX protocol's developer was stolen and $55 million lost. This attack granted the hacker access to the content of the bZx developer's wallet and the private keys to the BSC and Polygon deployment of bZx Protocol. For this kind of attack, it can be easily avoided by separating the development duties from operation duties. The operation team should hold multiple signature keys and deploy protocol contracts using a safe workstation.

### Poor Access Control of Privileged Functionalities

Privileged functionalities are common in every DeFi smart contract. These functions are only to be called by the contract's owner, and access control must be in place to ensure that. Access is usually controlled by specifying that calls to a function must be made by one or more addresses from a list of addresses. These access controls are sometimes omitted or built in a way that allows an attacker to circumvent them. If this happens, the attacker gains privileged access to the contract, allowing them to extract value from it.

The Poly Network and Punk Protocol hacks are two recent examples of such a vulnerability, in which the attacker claimed ownership over the projects' contracts and utilized that access to drain value from them.

### Frontrunning Attacks

Blockchains do not immediately add transactions to the distributed ledger. Transactions are broadcasted to the blockchain network as soon as they are created, but they are stored in mempools on each blockchain node until they are added to the ledger as part of a block.

The gap between the creation of a transaction and its inclusion in the ledger creates the opportunity for frontrunning attacks. The attackers, commonly an autonomous program (bot), will look for transactions that they can exploit. If they see one, they create their own version of the transaction with a higher transaction fee and transmit it to the network. Since blockchain miners commonly order transactions in blocks based on their transaction fee, the attacker's transaction comes before the original one, netting them a profit.

Frontrunning impacts DeFi security in different ways. Many bots will use frontrunning to make a profit based on foreknowledge of users' transactions. In some cases, this is malicious, while in others (such as the DODO DEX and Punk Protocol hacks), a bot front-runs an attempted exploit and then returns the stolen tokens to the exploited protocol.

### Rug Pulls

Many attacks on DeFi protocols come from external threats, but this is not always true. Rug pulls are attacks committed by the owners and developers of the DeFi protocols themselves. In a rug pull scheme, someone inside the company with privileged access to its contracts uses this access to drain value from the protocol. Typically, the project and the team behind it then disappear, leaving the victims with little recourse to address the issue.

One of the Chainalysis blog post noted that rug pulls have emerged as the go-to scam of the DeFi ecosystem, accounting for 37 percent of all cryptocurrency scam revenue in 2021, versus just 1 percent in 2020. The Chainalysis blog post also provides examples of some of the biggest rug pulls of 2021. (See **[Box: AnubisDAO and Up1 Rug Pull](#c04.xhtml#head-2-27)**.) It is important for DeFi user to click on approve or other messages prompted by a dialog from a web3 app using their own wallets such as `Metamask`, `Enjin`, or `Agent wallet` as the hacker's contract may be able to gain access to all your tokens and then withdraw them from the affected wallet address.

### DeFi Cross-Chain Bridge Attack

In August 2021, Poly Network, an important cross-chain protocol for swapping tokens across multiple blockchains, suffered an attack. As a result, more than $600 million was stolen, which was the largest DeFi hack. The day after the attack, the hacker posted a series of Q&As via memos in Ethereum transactions. He said the attack was “for fun :),” and because “cross-chain hacking is hot.” This incident truly highlighted the importance of securing cross-chain protocols.

In a way, the high frequency and large monetary impact of these cross-chain attacks is a consequence of the growing enthusiasm for cross-chain protocols. The emergence of cross-chain DEXs has made it simple and fast for DeFi users to trade assets across different chains. In a traditional centralized exchange (CEX), cross-chain transactions take tens of minutes or even several days to process and can involve large fees. Thus, a cross-chain DEX (which only takes two to three steps and a few seconds to complete a cross-chain transaction) can offer improved user experiences. However, the recent and frequent security incidents surrounding cross-chain protocols indicates that, without strong security guarantees, better speed, efficacy, and rates might not be enough.

Following is a brief overview of the potential risks of cross-chain DeFi transactions, with specific examples of past attacks.
