
## 1.2.3 SERVICE-LAYER BASED THREATS

Upon sensing and transmission, the data procured requires operation while utilizing and integrating services of hardware and software platforms. The service layer hence aptly touted to be the middleware technology is designed according to the application requirements, application programming interface and service protocols to the standards of service providers, vendors and organizations. This layer is responsible for integration, analysis, security, management of UI and event-processing services [9] To render these services, the following steps are taken:

- a) Service detection: Locating the optimum infrastructure necessary to conduct services efficiently;
- b) Service combination and integration: To further broaden the scope of interaction among services and draw out more reliable ones is achieved by interaction by scheduling or recreating;
- c) Authentication Management: Focus is laid upon verification of trusted devices through other services;
- d) Service APIs: These help to improve interconnections between services.

To tackle the numerous challenges and threats, developers and corporations have contributed relentlessly to offer solutions to augment and improve services within the connected network. The ambitious SOCRADES integration architecture aims to ameliorate the interactions between application and service layers efficiently [11]. The “things” in the interconnection of devices are often limited to delivering services while exploiting these devices for discovery of networks, exchange of metadata and asynchronous publish and subscribe events [12]. In Peris-Lopez et al. (2006) [13], to increase the interoperability of loosely coupled devices and distributed applications, representational state transfer is set up. In Hernandez-Castro et al. (2013) [14], a service-provisioning process is introduced in the service layer that could strengthen ties and buttress cooperation between applications and services.

In light of the above-mentioned challenges and solutions offered to counter them, it is imperative to understand that certain security precautions, requirements and protocols, if undertaken, could shield against attacks in the service layer. A few of them are:

- a) Dedicated authorization methods for service verification, authentication of groups, protection of privacy and integrity for the upkeep and storage of keys;
- b) Protection against privacy leakage and location tracking;
- c) Tracking services involving unauthorized use and unsubscribed services;
- d) Prevention of potential threats like DoS attacks, node identification masquerade, replay attacks, service information manipulation and communication and services repudiation.

The solutions offered in this section broadly cover the solutions from major potential security threats.

In spite of the solutions offered, there remain a few open challenges that need to be addressed when creating an IoT application or services:

- a) Securing data transference between layers;
- b) Securing service management.

## 1.2.4 APPLICATION INTERFACE LAYER

This interface is the most visible and interactive layer of the IoT network and encompasses a myriad of utility-based implementations ranging from radio frequency identification based tracking to intelligent home management that are enabled via standardized protocols and other technologies [15]. Application maintenance requires certain security preconditions such as:

- a) Safety-based isolation.
- b) Secure methodologies for acquisition of software and updates.
- c) Patches for augmenting security.
- d) Verification means for the administrators.
- e) Integrated platform for enhancement of security.

Different layers of IoT architecture require the following in order to sustain security in communication between the layers:

- a) Maintaining the three tenets of security (privacy, confidentiality and integrity) for inter-layer communication.
- b) Verification and approval of administrators cross layer.
- c) Isolation of critical data.

The following regulations could prove to be helpful in designing security solutions:

- a) The safety of these nodes should be attended carefully as most of the nodes in question are unsupervised.
- b) Energy efficiency of nodes is of utmost importance while designing security solutions considering their large numbers.

## 1.2.5 CROSS-LAYER CHALLENGES

Across all layers of IoT architecture through which the data is shared, certain standards are to be maintained to ensure that the network remains secure and fully interoperable. With the growing number of things in the network, it is the prerogative of the users to ascertain that their data is guaranteed protection against challenges among layers of the architecture.

The security needs across layers are virtually the amalgamation of the challenges faced across the IoT network:

- a) Security protection in terms of design and execution time;
- b) Ensuring high privacy standards to protect personal data through enhancement technologies;
- c) Reinstating trust in IoT architecture

## 1.3 CHALLENGE TO IMPLEMENTATION OF BLOCKCHAIN IN IOT

### 1.3.1 ABSENCE OF IOT-CENTRIC CONSENSUS PROTOCOL

A consensus protocol is a technique or a set of rules and regulations that make all the full nodes finalize on an arrangement over the sequence of transactions. There are various categories of consensus protocols being currently utilized in a variety of blockchain applications, for example, PoS, Proof of Work (PoW), Practical Byzantine Fault Tolerance (PBFT), etc. A few of the commonly used consensus protocols are deliberated upon in the following paragraphs of this chapter. Makhdoom [16] shows the contrariety of a few of the widely known and used blockchain consensus protocols in a thorough and exhaustive manner. The established consensus protocols such as Proof of Stake (PoS), Proof of Work (PoW), IOTA, Proof of Elapsed Time (PoET) are fabricated for permissionless blockchains, with an emphasis on financial transactions, whereas PoS and PoET have the potential to be used in permissioned blockchains.

The universal problem with these consensus protocols is the probabilistic nature of the consensus process and that it fails to terminate in a durable committed block. This further explains their vulnerability to blockchain forks [17]. One of the major contributors to deferred transaction verification is an absolute absence of consensus finality that is not at all sustainable for the various real / near-real-time IoT systems that demand instantaneous transaction verification and completion. Furthermore, examining the various consensus protocols, we find that a certain type of hardware is required by PoET in which the region allocating wait time necessitates being a trusted entity.

A number of ambiguities are yet to be resolved when it comes to IOTA since it is still in the open beta testing phase particularly regarding its performance efficacy and security. A number of questions pertaining to whether IOTA would be an effective micro-payment method or its compatibility with contracts as in HFB (Hyperledger-Fabric blockchains) and Ethereum and its capability of providing data confidentiality are still unanswered.

Meanwhile, a number of other consensus protocols like the Delegated Byzantine Fault Tolerance (DBFT), Practical Byzantine Fault Tolerance (PBFT), HoneyBadger et al. are based on the Byzantine Fault Tolerance (BFT) protocol which is a group of state machine reduplication protocols. By replicating the services on a multitude of nodes it provides security against arbitrary faults. Despite BFT being the preferred protocol for permissioned-type blockchains, it has several shortcomings. BFT-based protocols have a high vulnerability toward DoS attacks owing to their lax timing assumptions with the exception of HoneyBadger BFT [18]. Not only does the feeble synchrony negatively alters the system’s productivity, but the liveliness characteristic of lax synchronous protocols is also unsuccessful as the feeble timing assumptions get contravened when malicious networks launch DoS attacks.
