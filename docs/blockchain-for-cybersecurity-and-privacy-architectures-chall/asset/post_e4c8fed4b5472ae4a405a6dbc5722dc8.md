
## A Taxonomy of Blockchain Threats and Vulnerabilities

targets for this attack. The adversary withdraws from an exchange and republishes the same transaction with TXID, and one of them will show on the network. Because of delays, it is highly probable the altered transaction will win rather than the original withdrawal. The currency exchange will not locate the original transaction on the network and will think that the transaction has failed if the exchange relies on TXIDs only. Thus, the adversary can continuously withdraw in the Mt. Gox attack; the attackers performed a transaction malleability attack to steal coins from the exchange, which forced the exchange to freeze users' account and halt withdrawals [19].

Table 1.1 shows that hacking fraud trips, with hack vectors comprising and blocked computer system, compromising cloud service, compromising email account, compromising private key, compromising third party, compromising server, compromising website, compromising cold and hot wallet, compromising platform, phishing attack, social engineering, masquerade attack, malicious insider, and Subscriber Identity Module (SIM) swapping attack. Coinbase successfully detected and blocked what would have been on a bank account on June 20. The hackers are believed to exploit a Firefox zero-day bug, targeting employees by spear-phishing [20]. There are different types of flaws in blockchain users' software, such as runtime, concurrency, security, performance, configuration, Graphical User Interface (GUI), compatibility, and hard fork flaws. Flaws in the blockchain users software, which is used in the blockchain network, may lead to the exposure of users' private keys. In 2014, Blockchain info, which is a hybrid wallet provider, a mistake during their software update in when their users generated a new key on their local computer using the affected software, the Elliptic Curve Digital Signature Algorithm (ECDSA), inputs were not adequately random, which caused an adversary to operate the software to compromise the users' private keys by only viewing the public address. There are 0.0002% of users affected, and the issue was detected and resolved within two and a half hours, although some Bitcoins were stolen. Software flaws may lead to a leak of users' private keys [21]. The number of blockchain incidents due to scam is 10. The secrecy of identity property provided by the blockchain has enabled itself to become the platform of choice for scams. The table shows that the second-highest loss is due to scams as the Ponzi scheme and Pyramid scheme, causing a loss of 1 billion dollars. Scam includes all the incidents from which the target owner disappeared with the funds.

Table 1.2 shows that the victims of blockchain incidents range from individuals to BTC, banks, BTC service providers such as Wallet service, currency trading platform, and exchange. Cryptocurrency exchanges are the prime targets of attack.

### TABLE 1.1
Blockchain Incident Classification

| Type | No. of Incident | Total Amount Loss ($ million) |
| --- | --- | --- |
| Hack | 48 | 1621 |
| Scam | 10 | 1126 |
| Smart contract flaws | 7 | 289 |

### TABLE 1.2 Blockchain Fraud Victim Classification

| Victim Type | No. of Incident | Amount Loss ($) |
|---|---|---|
| Bitcoin bank | 1 | 502,029 |
| Bitcoin payment service provider | 1 | 1,800,000 |
| Bitcoin stock market | 2 | 6,741,039 |
| Blockchain network | 1 | 7,700,000 |
| Cryptocurrency project | 1 | 40,000 |
| Blockchain project | 1 | 500,000 |
| Cloud services provider | 1 | 228,845 |
| Darknet market | 1 | 100,000,000 |
| Digital currency trading platform | 1 | 4,100,000 |
| Distributed autonomous organization | 1 | 74,124,000 |
| Exchange | 36 | 1,568,184,876 |
| Individual | 4 | 6,646,944 |
| Margin trading service | 2 | 441,760 |
| Mining marketplace | 1 | 64,931,534 |
| Online poker room | 1 | 15,543 |
| Ponzi scheme | 4 | 1,014,500,000 |
| Pyramid scheme | 2 | 2,300,000 |
| Smart contract coding company | 1 | 10,000 |
| Bitcoin stock market | 2 | 2,200,000 |

There are 36 incidents, with a total of $1.56 billion loss. The transaction marketplace vulnerability in BT was the cause of the Mt. Gox incident in 2014. There are incidents where hackers make use of cryptjacking to install the malware in the target machine or mobile device to utilize their computational power to mine a block, which consumes a large amount of electricity and might compromise the target's system functionality. In February 2018 researchers launched a cryptojacking campaign, affected more than 4000 devices, including the UK and US governments; the other campaign targeted millions of Android devices. In addition, Radiflow, a critical infrastructure security company, found cryptocurrency mining malware on the European water utility operational network, which had a huge impact on the systems [22].

## 1.4 CATEGORIZATION OF BLOCKCHAIN THREATS AND VULNERABILITIES

Figure 1.5 shows a taxonomy of blockchain threats and vulnerabilities that we have identified so far. This taxonomy is built upon the findings from 65 real-world cybersecurity incidents occurred between 2011 and the first half of year 2019 and produces a classification scheme according to the threat vectors and vulnerabilities of BT.

## A Taxonomy of Blockchain Threats and Vulnerabilities

![](img/816c34830872ca25a809f80557c16d27_39_0.png)

**1.5** Classification of blockchain threats and vulnerabilities.

We classify BT threats and vulnerabilities into the following five categories:

- Clients vulnerabilities
- Consensus mechanism vulnerabilities
- Mining pool vulnerabilities
- Network vulnerabilities
- Smart contract vulnerabilities

Each of the threat and vulnerability type is discussed in the following sections.

### 1.4.1 Clients’ VULNERABILITIES

All BTC’s asymmetric cryptography is based on elliptic curve cryptography (ECC). The addresses in BTC are derived from public keys of ECC, and the authentication of the transaction uses digital signatures, which are generated by the ECDSA. The use of ECC is inadequate because it does not have the randomness, which might compromise the user's keys. For example, in blockchain, 158 unique keys were found, which used the same value (nonce) for each transaction, which made it possible to compromise the users' private keys [23].

### 1.4.2 Hash Function Vulnerability

The operation in some blockchain networks relies on cryptographic primitives to ensure the correctness and accuracy. With the rapid development in computational power, these primitives have become breakable [24]. One of these primitives is the hash function. For example, SHA256 is the hash function used in blockchain, which is vulnerable to different cybersecurity threats, such as preimage and collision attacks. A preimage attack is when the attacker finds an input Y with hashing; however, finding two inputs providing the same hash is considered a collision attack. The collision attack might be possible if the adversary has quantum computing or dominates a mining pool [24].

### 1.4.1.3 Mining Malware

Cryptojacking is when the adversary installs the malware on the target machine or mobile device to utilize its capacity to mine a bitcoin, which consumes a large amount of electricity and might compromise the target's functionality. In February 2018, researchers launched a cryptojacking campaign, which affected more than 4000 websites, including the UK and US government. Venkatraman et al. [27,28] proposed a deep-learning-based analysis for malware detection. In the ledger, a critical infrastructure security company found cryptocurrency malware on the European water utility operational network, which had a huge impact on the systems [22].

### 1.4.1.4 Software's Flaws

There are different types of flaws in blockchain users' software, such as runtime, concurrency, and hard fork flaws [29]. In the blockchain users' software, which is used in the blockchain network, may lead to the exposure of users' private keys. In 2014, Blockchain.info, which is a hybrid wallet provider, made a mistake during their software update in when their users generated a new key pair on their local computer by the affected software, the ECDSA index were not adequately random, which means an adversary could operate the software to compromise the users' private keys by only viewing the public address [21].

### 1.4.1.5 Users' Addresses Vulnerability

Addresses in BTC are vulnerable to identity theft threat because these addresses are not certified. For instance, a man-in-the-middle attack might be performed by an adversary to change the target BTC address to the adversary address. The adversary might vandalize the target website to obtain payments destined for the target. The impact of the attack is disastrous, in the BTC blockchain, it is impossible to return the payment if the nodes in the network accept and register it in the ledger [30].
