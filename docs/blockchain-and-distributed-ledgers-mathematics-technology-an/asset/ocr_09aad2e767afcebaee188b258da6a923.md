access to full collateral at any time and providing necessary KYC and AML checks. This approach suggests that digital currencies issued by NBs could become competitive with fiat currencies for everyday use. Such alternative currencies have a long history of for smoothing bumps in the economic environment. If backed by an NB, they could avoid the bankruptcy problems that have traditionally plagued alternative currencies.

# 8.3.3 Technical considerations

One can think about CBDC in various ways. One possibility is to follow Nakamoto's idea and use it on a blockchain. However, due to various limitations inherent in the blockchain itself, it is not suitable for the large scale heavy-duty applications. The old Chaum's blind signature discovery, described in Section 4.5.6, might be more useful and come to the rescue. Rather than using proof-of-work (PoW) or other mechanisms for achieving consensus, one can avoid double spending by using a single-unique number per unit of currency issued by the central bank itself. Recall that paper banknotes have unique numbers already; in a decentralized fashion by a set of validators (or notaries), each knowing only the overall number. In this way, validators can secure multi-party computations to check the numbers' database and address the double spend problem in a Byzantine fault-tolerant way.

Major technical specifications for CBDC have to amalgamate the original Nakamoto and Ohta ideas and some additional considerations articulated by the Bank of England; see Okamoto and Ohta (1991); Bank of England (2020). We summarize these requirements in Table 8.1.

# Table 8.1 Key technical specifications for CBDC.

| Requirement | Summary |
| --- | --- |
| Anonymous or pseudonym | Transactable without revealing parties' identities |
| Secure | Secure against cyber and physical attacks |
| Divisible | Subdivisible as needed |
| Future-proof | Capable of upgrading without impacting operations |
| High-throughput capable | Capable of 20,000 transactions per second |
| Innovation-ready | Capable of handling innovative features and services |
| Instantaneous and final | Near-instantaneous, real-time, with settlement finality |
| Interoperable | Interoperable with traditional payment systems and other CBDCs |
| Non-reproducible | Cannot be copied and reused |
| Usable online | Securely usable online |
| Usable offline | Securely usable offline |
| Resilient | 99.9999% operational availability 24/7/365 |
| Transferrable | Transferrable to others |