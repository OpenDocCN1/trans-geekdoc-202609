
This may change in the future as we become better at controlling these environmental factors. However, we don’t know when or if quantum computers will ever be a threat to asymmetric cryptography.

If we can build significantly reliable quantum computers with several thousand qubits sufficient to crack 256-bit `ECDSA` used for Bitcoin, then it would only affect bitcoins, which is held in addresses with known public keys. As you learned in the previous chapters, it is advisable not to reuse addresses. If we don’t reuse addresses, hackers cannot use quantum computing to steal bitcoin.

If quantum computers can crack Bitcoin public keys, then Bitcoin can move to quantum-resistant algorithms such as Lamport signatures.

On the other hand, `Grover’s algorithm` can only accelerate nonce search and give an advantage to the miner using quantum computers. However, like other mining devices, it will be competing against other quantum computers doing the mining. The scenario will be like the situation when `ASIC` miners introduced mining advantage. This does not affect the network; instead, over time, it improves the security of the network.

# [Hidden bugs, bug exploit, and reorg](#toc.xhtml#s187a)

It is always possible that there exists an unidentified bug in the Bitcoin core software, consensus rules, etc. which may get exploited by an attacker. This could be an inflation bug that would allow an attacker to pay themselves extra bitcoin and would lead to an increase in bitcoin supply. It could lock unspent transactions indefinitely. It can affect the miner or user.

If a bug is exploited, then it needs to be identified immediately or within a few blocks. Once identified bug needs to be fixed, it may be required for the Bitcoin community to plan Bitcoin blockchain reorg. Blockchain reorg means convincing Miners to upgrade Bitcoin software, invalidating the blocks from the exploited blocks, and restart mining.

When a block is mined, the miner cannot immediately move the newly minted bitcoin. The miner needs to wait for 100 blocks before they can move it. This allows developers to fix the bug and convince miners to reorg before 100 blocks get mined, which is roughly 16 hours and 40 minutes. The transactions that were confirmed during this time will need to wait to get confirmed again. It is also possible that the transaction that was confirmed earlier may not get confirmed again before getting dropped by the mempool of most nodes. This will negatively affect the Bitcoin network’s credibility.

# [Frauds and robbery](#toc.xhtml#s188a)

Bitcoin is very valuable, so it attracts criminals. Like gold, bitcoin is sometimes robbed at gunpoint.

Bitcoin can also be stolen by fraudsters through social engineering like using rewards, urgency, and fear or through fake services. The frauds could be like banking frauds where one gains access to crypto exchange through `OTP`. A fraudster can ask you to fill in details and can take your `PIN` or wallet seeds. A fraudster can also ask you to transfer coins to your wallet in return for service.

# [Conclusion](#toc.xhtml#s189a)

In this chapter, you learned about the limitations of Bitcoin design, why those limitations are necessary, and what developments are happening to address those limitations. You also learned about the different ways bitcoin holders and networks could be attacked, the different ways by which merchants, miners, and holders of Bitcoin can mitigate most of those risks, and why some of the risks are not really a risk because those are either too difficult or are financially unviable for an attacker.

We discussed how Bitcoin centralization is both bad for network security and good for getting enhancement accepted by the Bitcoin mining community. We also saw how Bitcoin energy usage is good for the environment.

In the next chapter, you will learn about the Bitcoin address format and understand how to generate the private key, public key, and addresses. You will also learn about how you can create your bitcoin wallet and how you can protect the wallet from hackers.

# [Points to remember](#toc.xhtml#s190a)

*   Blockchain verification time is the most important reason due to which Bitcoin block size is limited to 1MB to 4 MB.
*   By replacing multiple signatures and complex scripts with a single public key and signature using `Taproot`, signature aggregation, and `Schnorr signatures`, we can accommodate more transactions in a block and have better privacy.
*   `Lightning Network` is a layer two payment protocol.
*   `Lightning Network` provides privacy as individual transactions are not recorded on the Bitcoin blockchain.
*   `Lightning Network` provides scaling as an unlimited number of transactions can happen between peers.
*   Bitcoin mining helps lower carbon footprint by encouraging the use of off-grid renewable energy sources and utilizing waste energy.
*   Bitcoin mining difficulty is adjusted at every 2016 block.
*   Mining pools being centralized are prone to natural disasters, power failures, government crackdowns, or `DDoS` attacks, which leads to drop in network hash rate.
*   A sudden drop-in hash rate causes block time to increase and network fees to spike.
*   Lack of legal protection encourages fraud and illegal activities in bitcoin.
*   Most central banks discourage the use of bitcoin and other cryptocurrencies to protect their currencies against capital flight.
*   High entropy random number generators help generate private keys that are safe from brute force attacks.
*   `SHA256` is collision-resistant.
*   `Salt` protects against rainbow table attacks.
*   Low-round `PBKDF2-HMAC-SHA512` algorithms are prone to brute force attacks.
*   `Hierarchical Deterministic Wallets`, along with 12- to 24-word mnemonic code, eases securing of private keys.
*   A `trojan` is a malware that disguises itself as legitimate software.
*   `Spyware` is malicious software that gets installed without the victim’s knowledge and steals information and sends it to attackers.
*   `Social Engineering` is the use of psychological manipulations in order to collect private information.
*   Transaction malleability bug affects the non-`SegWit` transactions.
*   `BIP62` solves most of the transaction malleability issues.
*   Bitcoin nodes, by default, enforce a minimum transaction fee on all the received transactions in order to accept and forward them. This fee is called the `relay fee`.
*   `Relay fee` protects addresses from dusting attacks.
*   To protect against dusting attacks, a wallet should not accept very small value transactions.
*   In mempool flood attack, an attacker publishes a large number of small value transactions, which increases network fees.
*   Mempool flood attacks have become unviable because even `relay fee` is not cheap.
*   In `selfish mining`, a malicious mining pool takes greater control over the network hash rate by inflicting cost to the competing mining pools.
*   `Selfish mining` is easy to identify as it causes a greater occurrence of competing chains.
*   `FIBRE` stands for Fast Internet Bitcoin Relay Engine.
*   `FIBRE` is a protocol design that can achieve propagation delay nearly close to the physical limit with the help of a well-managed network.
*   `FIBRE` reduces propagation delay to less than a second, which gives little room for a malicious mining pool to attack networks using `selfish mining`.
*   Mining pools being centralized are also prone to network partitioning and delay attacks using `BGP hijacking`.
*   Unconfirmed transactions, even if those are `SegWit`, are prone to double-spend attacks.
*   Always run a full node to connect using `Tor` routing.
*   Miners add fingerprints in the `coinbase transaction` of a newly mined block, which helps the network know the mining hash rate of each miner.
*   A miner can hide its real hash rate and can mine over 51% hash rate if it does not add its fingerprints.
