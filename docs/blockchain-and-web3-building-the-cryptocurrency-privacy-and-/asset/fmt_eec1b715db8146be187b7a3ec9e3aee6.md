
## Blockchain and Metaverse: Marriage in Heaven?

Blockchain's encryption, immutability, and decentralization attributes make it a great choice for securing data. Blockchain-enabled data security methods help ensure confidentiality, integrity, and availability of information (see [Figure 8.1](#c08.xhtml#c08-fig-0001)).

### Confidentiality

The asymmetric encryption mechanism used in the public key provides pseudo anonymity of the user. Privacy coin leveraging zero knowledge, multipart secure computing, ring signature, coin join, and threshold signatures provides enhanced confidentiality of blockchain transactions. The layer two technology in Ethereum, the lightning network in Bitcoin, and channels in HyperLedger Fabric are also excellent mechanisms for confidentiality in addition to performance gains.

![Figure 8.1 The CIA of Blockchain](images/c08f001.png)

**[Figure 8.1](#c08.xhtml#R_c08-fig-0001) The CIA of Blockchain**

For example, Hyperledger Fabric can be defined as a logical entity that represents a grouping of two or more blockchain network members/participants for the purpose of conducting private and confidential transactions between themselves. Its `channels` are private and permissioned and meet the following requirements to enhance the confidentiality of the network:

*   Not anyone and everyone can join a channel.
*   Each peer joining a channel has its own identity.
*   This identity is given by a membership services provider (`MSP`).
*   Each peer in a channel must be authenticated and authorized to conduct transactions on that channel.

### Integrity

Blockchain data or transaction has to be signed, consensus agreed, and appended in the ledger. The ledger is globally distributed for and the integrity is ensured at global scale, not like a centralized database.

### Availability

Data on blockchain is hosted redundantly by many network nodes; the availability of data (if not considering the response time in data query) can be ensured because nodes are distributed and controlled with a good incentive mechanism by network participants. In addition, Smart contract, and protocol for data (in terms of ownership, pricing, and exchange) encourage and incentivize availability and sharing of data.

Although blockchain technology introduced new challenges to cybersecurity (we have to think about the cybersecurity of blockchain, too), the blockchain security features can be leveraged by metaverse applications for data confidentiality, data integrity, and data availability. It certainly seems like a marriage made in heaven if blockchain can be used properly in metaverse applications. However, as this chapter will discuss, the data security issues in the Web3 remain more complex than the marriage itself.

## Identity in Metaverse: Wild Wild West?

In the Metaverse, users' digital identity is where intruders strike first. The metaverse is expected to bring a shift from login IDs and usernames to enhanced digital avatars. Your metaverse profile may contain much more personal information than your current Google or Facebook account. If you are not careful, it may integrate your entire digital life and your personality — not only your unique online (and offline) identity, but also your bank account and other sensitive data. Protecting digital identities against theft will be a critical factor for metaverse applications; equally important, the community must ensure that metaverse users cannot fake their identities.

In history, fraudsters have claimed to be deposed princes with fortunes to share, or sweepstakes hosts desperately trying to reach you. When the internet developed, these schemes refranchised digitally by email, text messaging, and social network communication. Playing this forward, identify theft will be further upgraded in the metaverse. It won't be a fake email from your bank. It could be an avatar of a teller in a virtual bank lobby asking for your personal identification. It could be an impersonation of your social network friends inviting you to a multiplayer game in a malicious virtual room.

Therefore, solving for identity in the metaverse is a top concern. With a paradigm shift comes a great responsibility – but who will be the gatekeeper, and how can you ensure that your information is kept safe? The security of this new environment will lie on the shoulders of the companies involved with the metaverse as they will have to assume the role of identity verifiers. They will have to find a way to authenticate identity, protect the identity, and defend against misuse and fraudulent use of identity.

However, organizations need to know that adopting metaverse-enabled apps and experiences won't upend their identity and access control. There are many open questions about identity protection, and they are interesting challenges for the metaverse community as well as the cybersecurity providers. For example:

1.  **Will the metaverse make the identity crisis worse in industries like gaming, where attempts of hacking, tampering, cheating, and theft are already prominent?** For example, "deepfakes" is one challenge. Deepfake uses a deep-learning system to produce persuasive counterfeits by studying photographs and videos of a target person from multiple angles, and then mimicking its behavior and speech patterns. Once a preliminary fake has been produced, a method known as `GANs`, or generative adversarial networks, makes it more believable. The `GANs` process seeks to detect flaws in the forgery and then improve the fake by addressing the flaws. There are many deepfakes as service providers in the market that can simulate actual identity presentation via voice, image, and video data. When more and more personal data become exposed in 3D, immersive gaming (see related data privacy discussion in [Chapter 7](#c07.xhtml)), we may see explosive growth of deepfakes.

2.  **The ambiguity of ownership in the metaverse will create a lot of intellectual property disputes.** Who will truly own in-game contents or `NFT` items, the publishers, or users? Who drives the sales of the contents and who represents the users who generate content? The linkage between digital assets and individual identities is a huge topic for the metaverse.

3.  **The metaverse ecosystem will process enormous amounts of personal data.** This will be subject to increasingly stringent data regulations as the existing social networks face. This may be a heavy compliance burden for tech startups, especially for smaller companies keen to build up the metaverse. We must make identity manageable for enterprises in this new world.

Again, take "deepfakes" as an example. In January 2022, the Chinese regulator proposed draft rules to crack down on the spread of "deepfakes" at several platforms. As proposed by the draft rule, "Where a deep synthesis service provider provides significant editing functions for biometric information such as face and human voice, it shall prompt the (provider) to notify and obtain the individual consent of the subject whose personal information is being edited." Those first-time violators of this consent rule will be fined 10,000 yuan ($1,600) to 100,000 yuan ($16,000).

What's encouraging is that many researchers and standard organizations such as `W3C` and Decentralized Identity Foundation have been working hard to define the security requirements of decentralized identity. The newly formed organization named "Trust over IP" is also trying to provide a robust, common standard and complete architecture for internet-scale digital trust, which can be used by metaverse applications. Constructive steps also include making things like multifactor authentication (`MFA`) and passwordless authentication integral to platforms.
