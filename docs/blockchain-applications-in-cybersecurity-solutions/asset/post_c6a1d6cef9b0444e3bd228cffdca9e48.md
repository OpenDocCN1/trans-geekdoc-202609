
## Restrictions on New Nodes:

By increasing the cost or difficulty of construction of new nodes inside a network, the blockchain architect can raise the standard for malicious actors to saturate the network with malicious nodes. This strategy frequently entails restricting the number of nodes that can connect to a single IP address or device. This precautionary measure can be evaded by an attacker building a botnet comprised of devices with unique IP addresses.

## Countermeasures against Long-Range Attacks on Proof of Stake Networks

A Long-Range attack is one in which the adversary returns to the genesis block and splits the network. The new branch is filled with people with a distinct history from the main chain. The attack is successful when the adversary's branch grows longer than the main chain and overtakes it. Longest chain rule, Moving Checkpoints, Key-evolving cryptography, context-aware transactions and plenitude rule are countermeasures against long-range attacks [10].

## Defence Mechanism against User Wallet Attacks

### Countermeasures against Phishing

To resist phishing attacks, Imperva offers a combination of login management and online application security solutions: Imperva Login Safeguard provides two-factor authentication to protect URL addresses on your website or online application. This includes URL parameterized addresses and AJAX pages, which are typically a greater challenge to safeguard with 2FA. The solution can be implemented in a matter of seconds with just a few mouse clicks. It requires no additional hardware or software and allows you to modify user roles and rights directly from the Imperva dashboard [11]. The Imperva Web Application Firewall (WAF), which runs in the cloud, prevents malicious requests at the network edge. This involves preventing attempts by insiders to inject malware which have been infiltrated, as well as duplicating XSS attacks caused by phishing campaigns.

### Countermeasures against Dictionary Attacks

A dictionary attack is a brute-force assault in which attackers try to guess passwords by running them through a dictionary of popular words and phrases. To prevent offline Dictionary attacks, Canetti et al. [12] proposed using many human-only solvable puzzles (HOSPs) generated and saved on disk without their answers. The password provided by the user is then used to choose a small number of puzzles from the database. The key is extracted from the password and the puzzle solutions once a legitimate user completes these puzzles to acquire. Encrypted, this part is vulnerable to dictionary-based attacks, in which an attacker attempts to decrypt a huge number of popular passwords until he discovers one that works [15]. Cold wallets are offline wallets for storing bitcoins. Two issues are related to cold wallets.

- 1. The presence of private keys in at least one cold device;
- 2. The exposure of all private keys to a single trusted cold wallet administrator.

To address these challenges, Ebrahimi et al. [16] create a novel system for handling cold wallet assets that makes use of native multi-signature schemes. For both wallet creation and signature generation, the proposed cold wallet system includes at least two different devices and their respective administrators. The strategy makes certain that no final private key is stored on any device. To that objective, no single authority may spend from exchange assets.

## Mechanism against Smart Contract Attacks

In the proposed solution, Alkhalifah et al. [17] calculate the difference between the contract balance and the sum of the balance of all participants in the smart contract balance (noted as a1 before the transaction and a1 ' after the transaction). The result is computed by calculating the difference between a1 and b1 before and a1 ' and b1 ' after each procedure in a smart contract transaction. The transaction is recorded as T1 and the pre-trade difference as x1, while the post-trade difference is recorded as x1 '. If the difference is equal to (x1 = x1 '), then the operation is genuine; otherwise, the operation is malignant. This operation is blocked, and the transaction is considered a malignant operation.

## Defense Mechanism against Transaction Verification Mechanism Attacks

### Countermeasures against Finney Attacks

Finney's attack targets the merchant who does not wait for transaction confirmation. To counteract this assault, the Vendor must obtain several confirmations before transferring items or offering a service to the client. While waiting for several confirmations does not eliminate the possibility of a double-spending attack, it does reduce the risk and makes it more difficult for the attacker to spend the same coins twice.

### Countermeasures against Race Attacks

Race Attack occurs when a vendor or recipient accepts unconfirmed transactions as payment. In a Race attack, the target is the Vendor (V) that accepts transactions without completely confirming the authenticity of blocks. The three detecting methods are as follows:

- **Listening period:** In this method, each received transaction is associated with a listening period, during which the Vendor monitors all receiving transactions. Only if the Vendor observes no attempt at double-spending throughout the listening period, will he deliver the product or provide the service.
- **Inserting observer nodes:** In this case, the Vendor inserts observer nodes into the network. The main task of the observer node is to transmit all transactions received to Vendor. This enables the Vendor or its observers to notice a double-spending attempt within seconds. To detect this attack, the Vendor must deploy a large number of observer nodes capable of connecting numerous nodes. The Vendor will incur costs as a result of implementing this countermeasure.
- **Sending out Warning or Alert Messages:** To counteract double-spending on rapid Bitcoin transfers, an efficient defense strategy has been developed. Peers on the Bitcoin network send out alarm messages when they receive two additional transactions with similar inputs but distinct outputs.

### Countermeasures against Vector76

Vector76 attack is an attack in which attackers aim to fraudulently withdraw or steal the coins from the target using an invalid transaction. Using the mechanism that does not accept transactions with a single confirmation, the user node in the network should avoid having inbound connections, which prevents the attacker from injecting false information into the network; outgoing node connections should be monitored as well, and only well-known nodes should be permitted to join, and notifying the merchant about the ongoing double-spend could be preventive actions.

### Countermeasures against Alternative History Attacks

In the case of repeated confirmations, an alternate-history attack is still conceivable, but it necessitates a high hash rate and the danger of largely lost electricity to the attacking miner. Incoming connections are not permitted; implementation of explicit outbound connections to well-known nodes, placing observer nodes in the network, and notifying the merchant about the ongoing double-spend are all feasible safeguards [11].

### Countermeasures for 51% Or Majority Attacks

Several countermeasures are recommended to mitigate 51 percent of attacks or the Majority of attacks. Miller et al. [18] recommended adjustments to Bitcoin's PoW puzzle in order to minimise coalitions of mining pools for majority attacks. In

PirlGuard was created to protect against 51 percent exploitation. It works in a similar fashion as compared to the Penalty System and dPoW. As a result, attackers face a penalty. Master nodes are involved in notarization. As a centralised technique, the master nodes amplify it. This security method is solely dependent on only the Ethash algorithm. PirlGuard mitigates the 51% attack to approximately 0.03%. As a result, the penalty mechanism and the master node feature are both low risks.

ChainLocks is a Dash-specific security solution that tries to protect users from a 51 percent assault. Dash, with only 4100 master nodes, is an ideal target for a 51 percent assault because of its limited hashing power [23]. The 51 percent attack against low hashing currencies is highly likely to be carried out by simply renting the necessary hashing power [24]. As a result, ChainLocks' security mechanisms are insufficient to prevent the double-spending attack. The double-spending attack can be carried out by attackers with less than 51 percent hashing power because just one confirmation is required to publish a block which makes the Dash blockchain more susceptible. As a result, the level of risk is considered to be high.

Merged mining is a technology that allows several coins to be mined concurrently [25]. Merged mining is not a safe method of mining, but it can help to mitigate the 51 percent attack when used. This strategy combines the hashing power of two crypto-coins, increasing the cost of the attack. This method has the potential to greatly boost low-quality coins. The main constraint of this method is that the combined crypto-coins must be on the same consensus. Another problem is that if two crypto-coins with low hashing power collide, they can still be attacked if the attacker has enough hashing power. As a result, merged mining is simply a method of increasing the attacking cost by combining hashing power. As a result, it does not give a practical solution, and the risk level is judged to be significant.

## Defense Mechanism Mining Pool Attacks

### Countermeasures against Selfish Mining

Researchers have carried out research beforehand and proposed numerous viable solutions to tackle the problem of selfish mining [26 - 29]. Solat and Potop-Butucaru [30] support block 'lives,' which prohibits greedy miners from retaining blocks. The network will refuse the estimated lifespan of a block (measured by honest miners). Heilman [27] is hindering the profitability of greedy miners by adopting a “Freshness Preferred” defense strategy. Heilman [27] adds unforgeable timestamps to blocks, and in comparison to older blocks, it prefers more recent timestamps in blocks, in addition to the prior works by Eyal and Sirer [29]. The author shows through his research that miners who store their blocks for a long time have lower motivation than opportunistic miners.
