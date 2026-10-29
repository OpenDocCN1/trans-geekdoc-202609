
## (d) CERTIFICATION AUTHORITIES (CA):

A Certificate authority or Certification authority (CA) is a trusted entity that issues digital certificates certifying the ownership of a public key by the named subject of the Certificate. This is an essential part of a PKI infrastructure. X.509 is a widespread standard to manage certification.

For example, in Hyperledger Fabric 1.1, the Certificate authority managing member identities issues X.509 certificates to its members.

## SUMMARISING BLOCKCHAIN’S FEATURES:

- Pseudonymity
- Decentralization
- Fault tolerance with no single point of failure
- Immutability (Tamper resistant)
- Transparency
- Trust through automation

## BLOCKCHAIN’S SECURITY TOOLS:

- One way Hash functions used in consensus implementation
- Data footprint representation and key generation
- Non-forgeable digital signature algorithms for transaction privacy
- Secrecy and non repudiation

In the traditional digital world, mutually untrusted partners communicate through a centralized system with the help of these digital certificates issued by centralized authorities to different websites and portals.

However, there have been increasing cases of Certification authorities being attacked.

There have been several cases of fake digital certificates for famous publishers like Google issued by reputed Certification authorities like Gogo (Inflight internet service) and Symantec, etc., while fake certificates used to target users of reputed banks to direct them to fake versions of their banks’ sites.

In the case of private Blockchains, the certification authorities and the administrators need to take utmost precaution in identifying genuine participants through issuance, identifying and revoking the certificates as the case may be appropriately. In the case of public Blockchains, in 2016, Sead Muftic proposed a Blockchain-based protocol that allows distribution and management of digital certificates (linking a subject with its public key) without the need of certificate authorities by offering BIX (Blockchain Information Exchange) certificates maintained in BCL (Bix certificate Ledger). These can replace the system of X.509 certificates offered by centralized authorities.

## VULNERABILITIES IN BLOCKCHAIN SECURITY

- **VULNERABILITIES TO MALWARES:** Malware attacks on users’ and nodes’ computer system to steal information and crypto-jacking (illegal mining using user’s resources). A Blockchain-based access control can help.
- **VULNERABILITY OF USERS’ INSTALLED PROGRAMS:** Third-party software compromised by hackers. Regular software patch updates is a must.

Properly managed identities and deployment of Byzantine fault tolerant consensus mechanisms ensures that the decentralized systems characterizing the Blockchain landscape are fault tolerant, attack resistant and collision resistant as they do not have the sensitive single central points of failure. It is also impossible for malicious participants to come together and act against the interests of the other genuine participants, unlike in centralized corporations with single points of failure and power concentration in a central authority.

However, there are certain limitations that are inherent to the Blockchain platforms that need to be looked at:

- a) The implementation of the consensus mechanism for arriving at the decision is contingent upon the opinion of the majority. Hence, it is possible for a majority to collude and manipulate decisions making a 51% attack feasible.
- b) Where there are a smaller number of participants in the Blockchain that generally happens in enterprise Blockchains closed groups or newly launched public platforms, the security is limited or missing at times.
- c) The private key management is vulnerable to thefts and hence exploitable. The trust in the Blockchain relies on the safekeeping of the private keys for a truly distributed identity management. Hence, the crypto currency and token investors in the case of public Blockchains and crypto asset-based platforms and the node administrators in the case of a private Blockchain should ensure adequate measures to record and store their private keys in a secure manner. Care should be taken that only authenticated users are able to transact on the respective platforms.
- d) Weakness in software implementation may compromise the entire system. There have been a number of cases where smart contracts and chain codes have been exploited to the detriment of the participants in the decentralized applications. In the case of the DAO, the first decentralized application launched on the Ethereum platform, about 50 million US dollars (3.6 million Ether) worth of tokens were syphoned off the organization through a bug that caused a recursive loop to remit the currency units to an attacker's account. (reference: https://en.wikipedia.org/wiki/The_DAO_(organization))
- e) Blockchain's cryptographic techniques may assure the immutability of the ledger but not that of the overall system. For example, there have been numerous attacks on the paraphernalia surrounding the Blockchain platforms like exchanges, wallets, etc.
- f) Blockchain aims at digitizing real-world assets to enable a safe and secure exchange through implementation of smart contracts. The physical world data can be manipulated before being digitized.

Let us take a look at the typical malware attacks and see how the Blockchains manage the same:

(1) SPOOFING: This involves use of a token or other credential information to pretend to be an authorized user of the platform. Many forms of attack like Sybil, Malware, Credential stuffing, Man in the middle (MITM) attacks involve the users being misled to fake sites or non-users gaining access to user’s credentials to transact on the system.

Hence, key management and identity tracking through the operation are an important part of the security offered by the Blockchain system. Protocols like the BIX protocol enable the correct identification of users and in enterprise applications, each user is provided a X.509 digital certificate that identifies and tracks his transactions. If any spurious transactions are detected that go against the interests of the participants, the identified participants are immediately rusticated from the system.

(2) DDOS (DISTRIBUTED DENIAL OF SERVICE ATTACKS) : DDOS attacks are executed by botnets that compromise the identity of connected systems and use the same to flood targeted websites with unmanageable traffic, thus forcing their shut down. Strong identity management and access controls provided at each node ensures that unauthorized participants cannot compromise and gain access to the connectivity of the compromised system, thus preventing the attack. Companies like Guardtime from Estonia are working on offering a Blockchain-enabled system that offers an additional bandwidth from connected peers, at times of increased load owing to such attacks, thus enabling them to share the burden without a shut down.

(3) RANSOMWARE ATTACKS: Ransomware attacks involve the blocking of access to an institution to one’s own data by the attackers. The distributed nature of the ledger in a Blockchain makes an attack improbable and ineffective as the attacker has to attack all the ledgers distributed across the system at the same time. Elimination of the single point of contact and the replication of data effectively disincentivizes the developers and perpetrators of Ransomware.

(4) TAMPERING AND REPUDIATION: The improbability of the ledger manipulation ensures that the contents of the ledger are neither tampered nor denied by a participant without leaving a trace of the credentials of those attempting the same. Hence, a Blockchain can be considered tamper evident, immutable platform, and the only way in which this can be done is by passing reversal/modification transactions through subsequent approved transactions.

(5) INFORMATION DISCLOSURE: In public Blockchains, the transactions are open for anyone to query, and the identity of the participants is protected using pseudonyms or other appropriate programs in case of Blockchains offering anonymous transactions. In case of private Blockchains, the transactions are protected cryptographically so that only authorized participants can view data relevant to them, using their private keys. Further, any entity or participant can only access the data that is programmatically approved by the access control mechanism approved by the administrators of the network. Any modification in access privileges must be authorized and approved by the authorities mentioned in the program.

Thus, in order to ensure integrity and safety of Blockchain-based systems, the implementers should ensure adequate control and employ best practices in the following:

- i. Key management
- ii. Software development and testing
- iii. Connectivity with external data sources and integration with front-end and backend systems
- iv. Using appropriate digital signature and validation mechanism for authorizing transactions
- v. Dynamic access control systems to ensure only the actual authorized participants are approved to transact by revoking the approval to those who cease to be members or are transferred to other positions in the organization.

It is a common practice for all Blockchain implementers to provision for a team that continuously scans the environment for evolving threats and also budget for and conduct hackathons to attack and compromise their
