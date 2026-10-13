
# Verifier

A verifier is an entity that verifies if the credential shared by a holder is valid (i.e., if the credential comes from a trusted issuer, not revoked by the issuer). For example: An access management system installed at a facility like airport that allows / denies access based on whether the holder has completed Covid-19 vaccination. Verification could be a combination business logic like “is the credential issued in the last 14 days” and “is it issued by an issuer that is recognized.”

![Figure 8.2 Self-Sovereign Identity (SSI) ¶ Source: Affinidi](images/c08f002.png)

**Figure 8.2 Self-Sovereign Identity (SSI)** ¶ Source: Affinidi

## What Is a Verifiable Credential (VC)?

The term `credential` can imply any (tamper-resistant) set of information that some authority claims to be true about you, and that enables you to convince others (who trust that authority) of these truths. For example, a diploma issued by a university proves you have an educational degree. A passport issued by a government of a country proves you are a citizen.

Every credential contains a set of claims about the subject of the credential – that is, about the holder. These claims are made by an issuer. To qualify as a credential, the claims must be verifiable in some way. This means a verifier must be able to determine the following:

*   Who issued the credential
*   That the credential has not been tampered with since it was issued
*   That it has not expired or been revoked

With physical credentials, this is accomplished through some proof of authenticity embedded directly in the credential itself like a chip or hologram. It can also be done by checking directly with the issuer that the credential is valid, accurate, and current. But this manual verification process can be difficult and time-consuming – a major reason why there is a worldwide black market in falsified credentials.

This brings us to one of the fundamental advantages of verifiable credentials: using cryptography and the blockchain, they can be digitally verified in seconds. This verification process can answer the following three questions:

*   Is the credential in a standard format, and does it contain the data the verifier needs?
*   Is the credential still valid – that is, not expired or revoked?
*   If applicable, does the credential (or its signature) provide cryptographic proof that the holder of the credential is the subject of the credential.

SSI will allow users or holders in **Figure 8.2** to maintain and have the ownership of its own digital identity across multiple platforms while selecting the information they wish to share on each. This mode of interaction would drastically transform the current digital marketplace that has turned personal data into a commodity. Identity is going to be returned, through blockchain, back to the individual so that the individual will own their data and then be able to marshal it out based on what's best for them, as opposed to how Facebook or LinkedIn or other people may want to exploit it.

With SSI, the security focus can be changed from centralized platform to wallet security, SSI security, and Access Control using smart contracts for data access. One such example is `OpenZeppelin`, which provides smart contracts for secure data access. The basic building block of SSI is public key cryptography. The owners of an SSI use a digital wallet with a private key to hold their digital identity, and they use this identity in conducting data ownership verification, data related transactions, and metaverse data exchanges. Users can encrypt the data and store the data in an `IPFS` file storage or `NFT` storage space, and the ownership of the data can be verified using the user's private key to digitally sign the data. The data can be encrypted by using the public key, so only the user can decrypt the data using the corresponding private key.

In practice, an encrypt key can be derived from the private key. This encrypt key can then be used as a symmetric key to both encrypt and decrypt the data for higher performance in data encryption, since encryption using public key cryptography usually is still very slow, especially with a large amount of data. SSI is a European Union standard. The European Union is creating an eIDAS compatible European Self-Sovereign Identity Framework (`ESSIF`). The `ESSIF` makes use of decentralized identifiers (`DIDs`) and the European Blockchain Services Infrastructure (`EBSI`), and (`eIDAS` stands for electronic Identification, Authentication and Trust Services defined by the EU).

The World Wide Web Consortium (`W3C`)'s Credentials Community Group (`CCG`), in collaboration with Decentralized Identity Foundation (`DIF`), is actively working on building a suite of `DID`) standards that cover core `DID` attributes, `DID` authentication and discovery, verifiable claims, `DID` secure communication, secure data storage, and wallet security. These suites of standards will clarify how identity and data ownership are defined in the metaverse platform. Of course, its most basic component is still the private and public key pairs used in public key cryptography. The protection of private keys will become a very important defense measure for metaverse data security.

## Data Leak Cases in NFT Projects

If a hacker steals your private key or the mnemonics used for the private key, you will lose your data and assets associated with this key. Worse, if you are a metaverse company that hosts users' funds, and a hacker is able to hack the server with the private key, then the financial loss can be huge.

This was what happened to a $140 million hack from a Polygon gaming platform named `Vulcan Forged` (NFT Marketplace) in December 2021. According to company CEO Jamie Thomson, the hacker was able to attack the semi-custodial wallets that `Vulcan Forged` helped manage for its customers. The problem wasn't with its wallet solution provider, `Venly`, but a vulnerability with `Vulcan Forged`. “What's happened is someone's exploited our servers, got the `Venly` credentials, and used it to extract the private keys of the `MyForge` users,” Thomson said in a video shared on the company's social media accounts after the attack. (`MyForge` is an asset management tool that displays users' crypto and NFT holdings.) “Going forward, of course, we're going to be using nothing but decentralized wallets so we never have to encounter this problem again.”

Another example was the hack of a Hong Kong–based NFT project in December 2021. In that case, the hacker stole an administrator account of the project's group chat on `Discord`, a popular online instant messaging service. Launched on November 27, 2021, `Monkey Kingdom`, which is comprised of 2,222 digital portraits of the mythical hero Monkey King dressed in different styles, has quickly become one of the most talked-about NFT projects in Asia, with endorsements from celebrities including Steve Aoki, JJ Lin, and Ian Chan of the Hong Kong–based boy band `Mirror`.

The hacker posted a “phishing” link in the group chat, just as the project kicked off a new sale in earnest. Buyers lost more than 7,000 `solana`, a popular cryptocurrency, to the scam, which amounted to nearly US$1.3 million. Phishing is a common form of online fraud used to steal user data, including login credentials and credit card numbers. It occurs when an attacker, masquerading as a trusted entity, dupes a victim into opening an email, instant message, or text message. It is now being used to breach access to users' cryptocurrency wallets. This example demonstrates that if a hacker gets the administrator account of a Web2.0 application, he can “fish” the users to send him the funds even if the user has full control of their private key.
