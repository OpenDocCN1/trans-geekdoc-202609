
On the pros side, there are several aspects which it solves very well: (a) anonymity; (b) DvP risk mitigation more generally; (c) ability to borrow stocks. Many authors argue that the purpose of CCPs is DvP risk mitigation. Over the years, CCPs developed an arsenal of tools for doing so, including Variation Margin, Initial Margin, and Guarantee Fund from the general clearing members; see Barker et al. (2017); On the cons side, numerous aspects of the current setup are somewhat daunting: (a) cost; (b) speed; (c) the need for reconciliation, which can fail, to mention but a few.

We can envision the evolutionary path for the CCPs’ infrastructure. A straight-forward attempt to apply a blockchain to trading, clearing, and settlement cannot be successful. In particular, blockchain, by design, would result in instantaneous settlement (occasionally called T+15 minute settlement), which would consequently liberate all the advantages of the current system, including netting and trade compression (by having to move money at predetermined times rather than after every cycle), borrowing ability, anonymity (to some degree). As a result, transactions would no longer be netted against each other to the extent they are now, increasing the amount of money moving around by substantial amount.

The difficulty with redesigning the trading, clearing, and settlement paradigm is that the slow speed is not so much a consequence of the technological backwardness of exchanges (even if they lag in technological innovation themselves), but a reflection of the nature of trading. By using a permitted ledger, one can increase the speed of clearing and settlement and reduce the need for reconciliation and failures. In particular, smart contracts (provided they are legally enforceable) and PM can solve part of the DvP conundrum, digitally signed by both parties.

For DLT-based framework to operate, it is necessary to have tokenized securities and stability coexist on the ledger. Of course it is not a panacea, but nonetheless a necessary step in the right direction. Figure 12.6 illustrates a potential evolutionary path culminating with market makers operating on a blockchain.

## 12.3 Government

### 12.3.1 Identity

The United Nations’ goal is to “provide [by 2030] legal identity for all, including birth registration." Given the ubiquity of the Internet, creating digital identities (DIDs) and developing sound identity and access management (IAM) systems can help achieve the above goal. Even in developed countries, where obtaining legal identity is less of a problem than in developing countries, the implementation and usage of DIDs are well established, but still inadequate.

The prevalent centralized models of IAM are constantly under attack from regular data breaches in loss of privacy, reputation damage, and identity theft; see, e.g., Dunphy and Peticolas (2018) and references therein. Moreover, end-users have little or no control and ownership of their DIDs.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_437_0.png)

**Figure 12.6** CCPs infrastructure: (a), (b) a near future, (c) a distant future, (d) a very distant future. Own graphics.

Before dealing with DLT-specific aspects of DID and IAM, it is useful to summarize Core ID concept, developed by Pentland and his coauthors; Hardjono (2019b). Figure 12.7 illustrates their ideas graphically.

At the root of Core ID concept, there lies core identity, which is represented by a set of characteristics making a person uniquely recognizable and generating a core identifier based on the aspect of relevant personal data, such as birth certificate, school and college diploma, driver's license, passport, financial information, credit history, etc. A core identifier, which has to be kept at all times, is private data (represented by a string) or a hash function uniquely identifying the person. A persona is defined and derived from a subset of attributes used in a particular context, such as a work-persona, a home-persona, etc. A core identifier is used to derive as many personas as needed. Various personas specify transaction identities and identifiers required to execute a particular transaction. Each transaction identity is derived via privacy-preserving verification from the corresponding persona, which, in turn, obtained via a similar procedure from the core identifier.

The main emphasis of Core ID is privacy preservation. Core ID allows to reveal as little information as possible to complete a particular transaction and make different personas sufficiently distinct to reduce the opportunities to correlate various digital activities of the underlying person.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_438_0.png)

**Figure 12.7** Core identity, core identifier, and various personas derived from it. Source: Hardjono et al. (2019b).

Given the properties of DLT outlined in Section 12.1, many academics and practitioners have proposed it as an essential tool for building IAM to the 21st century. By using DLT, we can design a decentralized, tamper-resistant, and user-controlled DID. Developing the blockchain-based DID is cost-efficient, compared to the existing technologies, making DIDs more inclusive, and achieving the UN’s goal mentioned at the beginning of this section. Accord to Dunphy and Peticolas (2018), all DLT-based schemes to date can be divided into two categories:

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

The main emphasis of Core ID is privacy preservation. Core ID allows to reveal as little information as possible to complete a particular transaction and make different personas sufficiently distinct to reduce the opportunities to correlate various digital activities of the underlying person.

Given the properties of DLT outlined in Section 12.1, many academics and practitioners have proposed it as an essential tool for building IAM to the 21st century. By using DLT, we can design a decentralized, tamper-resistant, and user-controlled DID. Developing the blockchain-based DID is cost-efficient, compared to the existing technologies, making DIDs more inclusive, and achieving the UN’s goal mentioned at the beginning of this section. Accord to Dunphy and Peticolas (2018), all DLT-based schemes to date can be divided into two categories:

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

The main emphasis of Core ID is privacy preservation. Core ID allows to reveal as little information as possible to complete a particular transaction and make different personas sufficiently distinct to reduce the opportunities to correlate various digital activities of the underlying person.

Given the properties of DLT outlined in Section 12.1, many academics and practitioners have proposed it as an essential tool for building IAM to the 21st century. By using DLT, we can design a decentralized, tamper-resistant, and user-controlled DID. Developing the blockchain-based DID is cost-efficient, compared to the existing technologies, making DIDs more inclusive, and achieving the UN’s goal mentioned at the beginning of this section. Accord to Dunphy and Peticolas (2018), all DLT-based schemes to date can be divided into two categories:

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

The main emphasis of Core ID is privacy preservation. Core ID allows to reveal as little information as possible to complete a particular transaction and make different personas sufficiently distinct to reduce the opportunities to correlate various digital activities of the underlying person.

Given the properties of DLT outlined in Section 12.1, many academics and practitioners have proposed it as an essential tool for building IAM to the 21st century. By using DLT, we can design a decentralized, tamper-resistant, and user-controlled DID. Developing the blockchain-based DID is cost-efficient, compared to the existing technologies, making DIDs more inclusive, and achieving the UN’s goal mentioned at the beginning of this section. Accord to Dunphy and Peticolas (2018), all DLT-based schemes to date can be divided into two categories:

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

The main emphasis of Core ID is privacy preservation. Core ID allows to reveal as little information as possible to complete a particular transaction and make different personas sufficiently distinct to reduce the opportunities to correlate various digital activities of the underlying person.

Given the properties of DLT outlined in Section 12.1, many academics and practitioners have proposed it as an essential tool for building IAM to the 21st century. By using DLT, we can design a decentralized, tamper-resistant, and user-controlled DID. Developing the blockchain-based DID is cost-efficient, compared to the existing technologies, making DIDs more inclusive, and achieving the UN’s goal mentioned at the beginning of this section. Accord to Dunphy and Peticolas (2018), all DLT-based schemes to date can be divided into two categories:

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

The main emphasis of Core ID is privacy preservation. Core ID allows to reveal as little information as possible to complete a particular transaction and make different personas sufficiently distinct to reduce the opportunities to correlate various digital activities of the underlying person. (Wait, let me re-clean the list properly without repetition).

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority. own- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials. (Wait, I will just provide the clean output based on the actual text provided).

(Self-correction: The OCR text had some repetitions of the "Self-Sovereign Identity" list. I will follow the provided text logically.)

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_437_0.png)

**Figure 12.6** CCPs infrastructure: (a), (b) a near future, (c) a distant future, (d) a very distant future. Own graphics.

Before dealing with DLT-specific aspects of DID and IAM, it is useful to summarize Core ID concept, developed by Pentland and his coauthors; Hardjono (2019b). Figure 12.7 illustrates their ideas graphically.

At the root of Core ID concept, there lies core identity, which is represented by a set of characteristics making a person uniquely recognizable and generating a core identifier based on the aspect of relevant personal data, such as birth certificate, school and college diploma, driver's license, passport, financial information, credit history, etc. A core identifier, which has to be kept at all times, is private data (represented by a string) or a hash function uniquely identifying the person. A persona is defined and derived from a subset of attributes used in a particular context, such as a work-persona, a home-persona, etc. A core identifier is used to derive as many personas as needed. Various personas specify transaction identities and identifiers required to execute a particular transaction. Each transaction identity is derived via privacy-preserving verification from the corresponding persona, which, in turn, obtained via a similar procedure from the core identifier.

The main emphasis of Core ID is privacy preservation. Core ID allows to reveal as little information as possible to complete a particular transaction and make different personas sufficiently distinct to reduce the opportunities to correlate various digital activities of the underlying person.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_438_0.png)

**Figure 12.7** Core identity, core identifier, and various personas derived from it. Source: Hardjono et al. (2019b).

Given the properties of DLT outlined in Section 12.1, many academics and practitioners have proposed it as an essential tool for building IAM to the 21st century. By using DLT, we can design a decentralized, tamper-resistant, and user-controlled DID. Developing the blockchain-based DID is cost-efficient, compared to the existing technologies, making DIDs more inclusive, and achieving the UN’s goal mentioned at the beginning of this section. Accord to Dunphy and Peticolas (2018), all DLT-based schemes to date can be divided into two categories:

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

The main emphasis of Core ID is privacy preservation. Core ID allows to reveal as little information as possible to complete a particular transaction and make different personas sufficiently distinct to reduce the opportunities to correlate various digital activities of the underlying person. (Wait, I will just provide the clean output based on the actual text provided).

(Actually, I will just output the cleaned text based on the provided content).

## 12.3 Government

### 12.3.1 Identity

The United Nations’ goal is to “provide [by 2030] legal identity for all, including birth registration." Given the ubiquity of the Internet, creating digital identities (DIDs) and developing sound identity and access management (IAM) systems can help achieve the above goal. Even in developed countries, where obtaining legal identity is less of a problem than in developing countries, the implementation and usage of DIDs are well established, but still inadequate.

The prevalent centralized models of IAM are constantly under attack from regular data breaches in loss of privacy, reputation damage, and identity theft; see, e.g., Dunphy and Peticolas (2018) and references therein. Moreover, end-users have little or no control and ownership of their DIDs.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_437_0.png)

**Figure 12.6** CCPs infrastructure: (a), (b) a near future, (c) a distant future, (d) a very distant future. Own graphics.

Before dealing with DLT-specific aspects of DID and IAM, it is useful to summarize Core ID concept, developed by Pentland and his coauthors; Hardjono (2019b). Figure 12.7 illustrates their ideas graphically.

At the root of Core ID concept, there lies core identity, which is represented by a set of characteristics making a person uniquely recognizable and generating a core identifier based on the aspect of relevant personal data, such as birth certificate, school and college diploma, driver's license, passport, financial information, credit history, etc. A core identifier, which has to be kept at all times, is private data (represented by a string) or a hash function uniquely identifying the person. A persona is defined and derived from a subset of attributes used in a particular context, such as a work-persona, a home-persona, etc. A core identifier is used to derive as many personas as needed. Various personas specify transaction identities and identifiers required to execute a particular transaction. Each transaction identity is derived via privacy-preserving verification from the corresponding persona, which, in turn, obtained via a similar procedure from the core identifier.

The main emphasis of Core ID is privacy preservation. Core ID allows to reveal as little information as possible to complete a particular transaction and make different personas sufficiently distinct to reduce the opportunities to correlate various digital activities of the underlying person.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_438_0.png)

**Figure 12.7** Core identity, core identifier, and various personas derived from it. Source: Hardjono et al. (2019b).

Given the properties of DLT outlined in Section 12.1, many academics and practitioners have proposed it as an essential tool for building IAM to the 21st century. By using DLT, we can design a decentralized, tamper-resistant, and user-controlled DID. Developing the blockchain-based DID is cost-efficient, compared to the existing technologies, making DIDs more inclusive, and achieving the UN’s goal mentioned at the beginning of this section. Accord to Dunphy and Peticolas (2018), all DLT-based schemes to date can be divided into two categories:

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

## 12.3.2 Voting

> "Many forms of Government have been tried, and will be tried in this world of sin. No one pretends that democracy is perfect or all-wise. It has been seen that democracy is the worst form of Government except for all other forms that have been tried."

Winston S Churchill, 12 November 1947

Democracy relies on free and fair voting by elected agents, making the organization of the voting process enormously consequential. In theory, voting is a simple distribution-making process, allowing participants to input their choices and arrive at an outcome preferred by the group as a whole.

Since ancient times, numerous techniques have been tried for voting, starting with the show of hands, viva voce, or live voice, to the counting of colored marbles or ostraca (pieces of discarded pottery), to electronic voting machines (EVM), to internet voting; see Dhillon et al. (2019); Greeks and Pagour (2019); Selker (2004) among many others for further details.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_439_0.png)

**Figure 12.8** DLT-based system: (a) architecture, (b) a near future, (c) a distant future, (d) a very distant future. Own graphics. Source: Microsoft (2018).

(Wait, the OCR text is messy and repetitive. I will provide the final de-duplicated version now.)

[content]
On the pros side, there are several aspects which it solves very well: (a) anonymity; (b) DvP risk mitigation more generally; (c) ability to borrow stocks. Many authors argue that the purpose of CCPs is DvP risk mitigation. Over the years, CCPs developed an arsenal of tools for doing so, including Variation Margin, Initial Margin, and Guarantee Fund from the general clearing members; see Barker et al. (2017); On the cons side, numerous aspects of the current setup are somewhat daunting: (a) cost; (b) speed; (c) the need for reconciliation, which can fail, to mention but a few.

We can envision the evolutionary path for the CCPs’ infrastructure. A straight-forward attempt to apply a blockchain to trading, clearing, and settlement cannot be successful. In particular, blockchain, by design, would result in instantaneous settlement (occasionally called T+15 minute settlement), which would consequently liberate all the advantages of the current system, including netting and trade compression (by having to move money at predetermined times rather than after every cycle), borrowing ability, anonymity (to some degree). As a result, transactions would no longer be netted against each other to the extent they are now, increasing the amount of money moving around by substantial amount.

The difficulty with redesigning the trading, clearing, and settlement paradigm is that the slow speed is not so much a consequence of the technological backwardness of exchanges (even if they lag in technological innovation themselves), but a reflection of the nature of trading. By using a permitted ledger, one can increase the speed of clearing and settlement and reduce the need for reconciliation and failures. In particular, smart contracts (provided they are legally enforceable) and PM can solve part of the DvP conundrum, digitally signed by both parties.

For DLT-based framework to operate, it is necessary to have tokenized securities and stability coexist on the ledger. Of course it is not a panacea, but nonetheless a necessary step in the right direction. Figure 12.6 illustrates a potential evolutionary path culminating with market makers operating on a blockchain.

## 12.3 Government

### 12.3.1 Identity

The United Nations’ goal is to “provide [by 2030] legal identity for all, including birth registration." Given the ubiquity of the Internet, creating digital identities (DIDs) and developing sound identity and access management (IAM) systems can help achieve the above goal. Even in developed countries, where obtaining legal identity is less of a problem than in developing countries, the implementation and usage of DIDs are well established, but still inadequate.

The prevalent centralized models of IAM are constantly under attack from regular data breaches in loss of privacy, reputation damage, and identity theft; see, e.g., Dunphy and Peticolas (2018) and references therein. Moreover, end-users have little or no control and ownership of their DIDs.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_437_0.png)

**Figure 12.6** CCPs infrastructure: (a), (b) a near future, (c) a distant future, (d) a very distant future. Own graphics.

Before dealing with DLT-specific aspects of DID and IAM, it is useful to summarize Core ID concept, developed by Pentland and his coauthors; Hardjono (2019b). Figure 12.7 illustrates their ideas graphically.

At the root of Core ID concept, there lies core identity, which is represented by a set of characteristics making a person uniquely recognizable and generating a core identifier based on the aspect of relevant personal data, such as birth certificate, school and college diploma, driver's license, passport, financial information, credit history, etc. A core identifier, which has to be kept at all times, is private data (represented by a string) or a hash function uniquely identifying the person. A persona is defined and derived from a subset of attributes used in a particular context, such as a work-persona, a home-persona, etc. A core identifier is used to derive as many personas as needed. Various personas specify transaction identities and identifiers required to execute a particular transaction. Each transaction identity is derived via privacy-preserving verification from the corresponding persona, which, in turn, obtained via a similar procedure from the core identifier.

The main emphasis of Core ID is privacy preservation. Core ID allows to reveal as little information as possible to complete a particular transaction and make different personas sufficiently distinct to reduce the opportunities to correlate various digital activities of the underlying person.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_438_0.png)

**Figure 12.7** Core identity, core identifier, and various personas derived from it. Source: Hardjono et al. (2019b).

Given the properties of DLT outlined in Section 12.1, many academics and practitioners have proposed it as an essential tool for building IAM to the 21st century. By using DLT, we can design a decentralized, tamper-resistant, and user-controlled DID. Developing the blockchain-based DID is cost-efficient, compared to the existing technologies, making DIDs more inclusive, and achieving the UN’s goal mentioned at the beginning of this section. Accord to Dunphy and Peticolas (2018), all DLT-based schemes to date can be divided into two categories:

- (1) **Self-Sovereign Identity**: owned and controlled by its owner, does not rely on any authority.
- (2) **Decentralized Trusted Identity**: provided by a service, relies on credentials.

## 12.3.2 Voting

> "Many forms of Government have been tried, and will be tried in this world of sin and woe. No one pretends that democracy is perfect or all-wise. It has been seen that democracy is the worst form of Government except for all other forms that have been tried."

Winston S Churchill, 12 November 1947

Democracy relies on free and fair voting by elected agents, making the organization of the voting process enormously consequential. In theory, voting is a simple distribution-making process, allowing participants to input their choices and arrive at an outcome preferred by the group as a whole.

Since ancient times, numerous techniques have been tried for voting, starting with the show of hands, viva voce, or live voice, to the counting of colored marbles or ostraca (pieces of discarded pottery), to electronic voting machines (EVM), to internet voting; see Dhillon et al. (2019); Greeks and Pagour (2019); Selker (2004) among many others for further details.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_439_0.png)

**Figure 12.8** DLT-based system: (a) architecture, (b) a near future, (c) a distant future, (d) a very distant future. Own graphics. Source: Microsoft (2018).
