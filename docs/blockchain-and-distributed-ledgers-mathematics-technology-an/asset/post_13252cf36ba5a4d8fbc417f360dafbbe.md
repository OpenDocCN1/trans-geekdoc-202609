
## Chapter 12 Present and Future of DLT | 395

are unsealed, and the votes are tallied publicly in front of various competing parties' representatives. Of, by its very nature, the process is slow and error-prone. However, it leaves a paper trail, which is audited if needed, though the audit of election outcomes several problems, which are not dissimilar to those discussed in Section 12.2.1.

Many researchers and inventors have tried their hand at improving the voting process. For instance, Thomas Edison patented the first electric voting machine in 1868. Later machines were used in the US as early as 1992; mark-sense ballots debuted in 1964; direct-recording electronic (DRE) voting machines in 1976; and Internet voting in 2000; for further details, see Selker (2004).

Here, we focus on electronic voting systems and, specifically, whether one can improve these systems by using DLT. Such systems must satisfy several requirements, which we now articulate formulating Grontas and Pagourtzis (2019) and references therein. These requirements include:

- (1) availability and efficiency;
- (2) authentication and authorization;
- (3) privacy;
- (4) correctness;
- (5) end-to-end (E2E) verifiability;
- (6) several other, less critical properties.

Availability and efficiency mean that the system is readily available, easy to implement, and easy to use, not only those with varying levels of technical or language proficiency. This would also need to address hurdles that may prevent voters from being physically present at the polls. Finally, ensuring that these systems are easily accessible to individuals with disabilities is of paramount importance. Authentication and authorization refer to a system's ability to authenticate a voter's identity and eligibility. Privacy means that a voter's choice is not revealed to anyone. Correctness signifies that the voting system, when designed, produces the result that correctly reflects the actual votes cast, and can be checked by anyone. End-to-End (E2E) verifiability means that all the voting process stages — collection, accumulation, storage, and counting of votes — should be verifiable.

While easy to articulate, these requirements are also hard to satisfy. For many years, academics and practitioners have been finding the best ways of doing so. The celebrated CALTECH/MIT Voting Technology Project — a multi-disciplinary, collaborative project between two eminent academic institutions — is a case in point. Yet today, of their goals proved to be elusive, is not particularly surprising given the contradictory nature of the requirements. For instance, authentication and authorization can make privacy challenging to achieve.

In principle, one can use cryptographic primitives in Chapter 4 to build a cryptographic election system modeled after voting with a show of hands, with a snapshot maintained for tallying. That is to replace the paper trail with mathematical proofs based on such constructs as blind signatures constructed in Chapter 4, zero-knowledge proofs, covered in Chapter 12 below, and other similar tools; see Adida (2006). Specifically, the cryptographic voting paradigm is based on the Bulletin Board (BB) concept, defined as a broadcast channel with memory, which supports only the insertion of new data (append-only), does not allow any deletions or modifications, and retains data for verification.

Numerous attempts, there is no universally acceptable implementation of the BB. Since blockchains and BBs are databases operating in an append-only manner allowing participants to reach consensus on the validity of transactions, it is only natural to try blockchain-based voting. In the Bitcoin protocol, transactions represent the transfer of value, while in the elections protocol, transactions represent the record of preference.

All proposed DLT-based voting systems are conceptually similar. After choosing a particular blockchain protocol (both permitted and permissionless blockchains have been suggested), all eligible voters are represented by anonymous addresses, while candidates are represented by known addresses. Small amount of tokens is sent to voters in advance by the election. There is room for PM discussed in Section 12.2.3, which can be explicitly designed for voting, instead of pocketing or spending these crypto tokens on unrelated matters. A vote for a specific candidate is cast by sending the received amount of tokens to the address of the voter's choice. The corresponding transaction is recorded on the blockchain. When the election ends, accumulated by each candidate is checked, and the winner is declared; Nasser et al. (2018). This approach is the 21st-century version of the show of hands used in classical Greece with such pseudonymity.

Unfortunately, while superficially attractive, the proposed approach has many conceptual and logistical drawbacks. First, since only eligible voters should participate in the election, since such a mapping has to be between their real identities and the corresponding blockchain addresses by a registration authority, a third party is introduced to the voting system nolens volens. Blockchain-based voting does not provide proper voter secrecy (similar to its underlying blockchain protocol). Third, by its nature, DLT-based voting is conceptually complicated, making it potentially untrustworthy to the electorate. Hence it can disenfranchise many voters — a highly undesirable outcome.

One can run small scale elections, such as board elections, among tech-savvy voters known to each other on a smart-contract-supporting blockchain; e.g., Morrory et al. (2017). However, we share Dhillon et al. (2019); Grontas and Pagourzis (2019); Park et al. (2020) thinking that large-scale DLT voting is not for its prime time. Nevertheless, we feel that practical use of DLT for glamorous but vital tasks, such as running census, maintaining and updating lists of eligible voters, helping to tally results from different precincts, is a more promising short-term goal as we found a way to build a DLT framework for voting on a larger scale.

## 12.4 Healthcare

### 12.4.1 Electronic health records system

Not dissimilar to the financial system, the existing healthcare system also suffers from several drawbacks. This fact is not particularly surprising since its informational backbone — the electronic health records (EHRs) system — was not designed to be real-time. Instead, patient EHRs are kept by numerous medical care providers, retaining de facto (and often de jure) stewardship of the data; see Ekbal et al. (2016). As a result, patients cannot get a full picture of their health records, instead getting the information pieceal, if at all; the same is true as far as healthcare providers are concerned. It is natural to see if DLT can rectify the situation, e.g., Ekbal et al. (2016); Gordon and Catalini (2018); Hussein et al. (2019); Khezr et al. (2019); Kuo et al. (2017) among many others.

DLT-based system for handling EHRs achieves several key objectives, securing sensitive patient data, allowing access to real-time data to authorized parties, and facilitating collaboration of several authorized healthcare providers on the same medical records. Such a system has the following advantages compared to the existing one:

- (1) Increase of patients control over their EHR;
- (2) Improves data provenance and integrity;
- (3) Reduces the burden of data duplication and reconciliation;
- (4) Allows for seamless clinical care by different healthcare providers;
- (5) Enables effective management of emergency medical situations.

It also opens the possibility for patient-generated health data from wearables, sensors, smartphone applications, and Internet of Things (IoT) devices to be integrated with information obtained during interactions with healthcare providers. All of these data are permanently stored in designated databases and made available to patients and authorized providers as needed. We illustrate one potential implementation of DLT-based EHRs system in Figure 12.9.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_443_0.png)

Figure 12.9 A DLT-based system for maintaining EHRs. Own graphics.
