
## Software and Firmware Uncertainty

With the different applications of IoT devices, there come different types of software and different types of firmware to run them [[58](#C_006_c1.xhtml#r1_58)]. But for the lack of standardization and proper review, it becomes hard to create secure code. Moreover, failure to regular security updates to the devices increases vulnerability. The attacker can also hamper the synchronization process of IoT devices with other devices manipulating clock time. Eventually, it becomes easier for the intruder to exploit the backend code and change the code for pre-allocated memory [[59](#C_006_c1.xhtml#r1_59)].

## XMPPilot Attack

In order to eavesdrop on the communication channel between the sender and receiver, the attacker uses XMPPilot. He writes code to hamper XMPP connection and confines the encryption process at receiver side communication [[60](#C_006_c1.xhtml#r1_60)].

## Credibility Issues

Lack of authentication standards or authorized party to maintain security ease the attack for the intruders [[61](#C_006_c1.xhtml#r1_61)]. They can use the update file to inject their own manipulated script. Again, it is necessary to authenticate end-to-end encryption in communication.

### 1.4.5 Security Issues of Business Layer

The business layer is the latest addition to the IoT structure that enables the system to be more productive and easier to use. Not many threats to this layer are still found but attackers can manipulate the previous layer attacks. Some possible security issues in this layer are as follows:

## Zero-Day Attack

A Zero-Day attack is an attack pointing to certain security weaknesses of a software or application that is discovered by the developer but not yet mitigated. It can occur the same day the developer found the weakness. Usually, this type of attack exploits security holes without the vendor having any kind of knowledge of it [[62](#C_006_c1.xhtml#r1_62)].

## Logic Attack

The business layer uses a lot of logic to compute the data and generate necessary graphs or decisions. Mistakes in the logic while programming initiates certain threats while computing these outcomes [[63](#C_006_c1.xhtml#r1_63)]. Again, shortcomings in the algorithm of password recovery or authentication, encryption, input validation, etc. can poise some security threats on the business layer too.

There are other approaches to discover the security gaps of IoT and classification for possible threats. But the five-layered architecture holds almost all the crucial attacks that are common in all the IoT ecosystems.

## 1.5 Blockchain-Based Solution

Blockchain can offer improved solutions in different domains of IoT. IoT devices need to deal with a lot of private data. Permissioned blockchain can be an excellent solution to avoid exposing user data [[64](#C_006_c1.xhtml#r1_64)]. Direct communication eliminating the use of central authority can handle the increasing traffic of exponentially growing IoT devices. It can also decrease the load on a cloud server for storing data. Strengthening the infrastructure, blockchain can further contribute to the prevention of data manipulation and numerous cyberattacks.

Several approaches have been taken in the previous years to solve the issues of IoT. The researchers propose different architectures and system designs. [Table 1.1](#C_006_c1.xhtml#t1_1) represents some recent works on blockchain solutions aiming to solve issues in security as well as IoT architecture and data management.

**TABLE 1.1** State-of-the-Art IoT Security Solutions with Blockchain

| Attack Name | Effect | Blockchain Solutions | References |
| --- | --- | --- | --- |
| Eavesdropping | Transmitted data loses privacy | * Divides blockchain into two parts: off-blockchain and on-blockchain to process data in three steps each. | [[65](#C_006_c1.xhtml#r1_65)] |
| Timing attack | Subject to side-channel attack exposing the cryptosystem | * Combines blockchain with a domestic commercial cryptographic algorithm.<br>* A probabilistic model is applied in blockchain framework for data collection. | [[66](#C_006_c1.xhtml#r1_66), [67](#C_006_c1.xhtml#r1_67)] |
| Node Hijack | Hampers data collection or transfers to attacker | * Proposes a signature scheme of permissioned blockchain.<br>* Introduces a blockchain-based framework in the unmanned aerial vehicles network. | [[68](#C_006_c1.xhtml#r1_68), [69](#C_006_c1.xhtml#r1_69)] |
| Replay attack | Destroys private data security | * Blockchain-based logistics system with special monitoring sensors.<br>* Two-way authentication in a blockchain scheme.<br>* BSS (blockchain enabled security system) scheme with the batch system. | [[70](#C_006_c1.xhtml#r1_70), [71](#C_006_c1.xhtml#r1_71), [72](#C_006_c1.xhtml#r1_72)] |
| Malicious and fake node | Consumes energy | * RSA (Rivest–Shamir–Adleman) signature-based authentication in a blockchain network.<br>* Manage identity authentication with lightweight blockchain.<br>* Hyperledger Fabric private blockchain-based framework. | [[73](#C_006_c1.xhtml#r1_73), [74](#C_006_c1.xhtml#r1_74), [75](#C_006_c1.xhtml#r1_75)] |
| Sybil attack | Corrupts data acquisition | * SSDT (Blockchain-Based Sybil-Secure Data Transmission) framework based on blockchain.<br>* Blockchain-based detection mechanism for UWSN | [[76](#C_006_c1.xhtml#r1_76), [77](#C_006_c1.xhtml#r1_77)] |
| Black hole and gray hole attack | Network latency | * Coded blockchain-based energy-efficient mechanism<br>* Efficient lightweight integrated blockchain (ELIB) model for public blockchain | [[78](#C_006_c1.xhtml#r1_78), [79](#C_006_c1.xhtml#r1_79)] |
| Exploitation | Contaminates network/IP address | * Hybrid blockchain based on DPoA (Delegated Proof of Authority) | [[80](#C_006_c1.xhtml#r1_80)] |
| Man in the middle attack | Network security, key management | * Seed-based blockchain scheme for key generation and management<br>* Blockchain-based architecture for CAV (connected and autonomous vehicles) | [[81](#C_006_c1.xhtml#r1_81), [82](#C_006_c1.xhtml#r1_82)] |
| DoS/DDoS | Network unavailability, system crash | * Hybrid blockchain for IIoT.<br>* Private blockchain using Ethereum platform.<br>* Blockchain framework using smart contract and LSTM (long short-term memory) for access control | [[83](#C_006_c1.xhtml#r1_83), [84](#C_006_c1.xhtml#r1_84), [85](#C_006_c1.xhtml#r1_85)] |
| Virus attack | Data/System disruption | * Proposed consortium blockchain-based recovery service.<br>* Detection mechanism using blockchain in distributed database. | [[86](#C_006_c1.xhtml#r1_86), [87](#C_006_c1.xhtml#r1_87)] |
| Exhaustion | Decay memory/resources | * Proposed a blockchain-based data edge verification system.<br>* Lightweight blockchain for IIoT.<br>* Hybrid model of public and local blockchain for authentication. | [[88](#C_006_c1.xhtml#r1_88), [89](#C_006_c1.xhtml#r1_89), [90](#C_006_c1.xhtml#r1_90)] |
| Phishing attack | Credentials’ security | * Blockchain and Zero Trust-based framework. | [[91](#C_006_c1.xhtml#r1_91)] |
| Logic attack | Runtime error | * Hyperledger Fabric for verification and access control | [[92](#C_006_c1.xhtml#r1_92)] |
| Zero-day attack | Network security, zero knowledge | * Detection mechanism with deep blockchain framework.<br>* Blockchain-based authentication mechanism | [[93](#C_006_c1.xhtml#r1_93), [94](#C_006_c1.xhtml#r1_94)] |
| Sniffing attack | Unauthorized access | * Blockchain-based event log security mechanism.<br>* GADV in blockchain encryption scheme. | [[95](#C_006_c1.xhtml#r1_95), [96](#C_006_c1.xhtml#r1_96)] |
| Routing attack | Deteriorates network efficiency, DoS | * Blockchain-based framework using smart contract to identify tampered sensor nodes. | |
