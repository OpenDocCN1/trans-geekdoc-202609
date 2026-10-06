
# Chapter 7 Ripple — A Simple Solution to a Complex Problem? | 239

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_285_0.png)

**Figure 7.4** (a, b) If validators are split into cliques, consensus becomes impossible. (c) When the connectivity of validating nodes is sufficiently robust, consensus can always be reached. Own graphics. Source: Ripple.

the amount of money one wishes to move across the system. As such, Ripple payments are not payments in the conventional sense of the word. After Alice sends her money to Bob, there is a chain of reverse transactions, which need to be closed at some point — the same issue that afflicts Hawala protocol; see Section 2.5.3.

In general, having multiple payment routes is an advantage. However, even with a plethora of roads, some are better to avoid. The reader will do to recall the conversation between Napoleon and the Russian general Balashov from *War and Peace* by Leo Tolstoy: “Napoleon ...” naively asked Balashov what towns at the dinner the direct road from there to Moscow passed. Balashov, was on the alert all through the dinner, that replied that ‘all roads lead to Rome, so all roads lead to Moscow; there were many roads, and ‘them the road through Poltava, see Charles XII chose’ ¹

Under normal circumstances, credit extended by one bank is not an issue. In the case of default, we who think this is just a hypothetical possibility, have two words — the Herstatt risk; see Galati (2002). This is essentially a cross-currency settlement risk by asynchronous money flowing in and out of the system. For instance, a bank can receive money as part of the transaction and default before honoring its money transfer. This situation happened on June 26, 1974, when the troubled German bank Herstatt received Marks from several counterparties and was supposed to initiate USD-denominated reciprocal payments. However, Herstatt ceased its operations before sending payments to time zone differences between Cologne and New York. As a result, the counterpart banks did not get their dollars. Although this type of risk is

> ¹The general was alluding to the decisive victory of Peter the Great over Charles XII of Sweden in the battle of Poltava on July 8, 1709. According to Tolstoy, the irony of this answer escaped Napoleon.

# Table 7.1 Similarities and differences between Bitcoin and Ripple protocols.

| Objective | Bitcoin | Ripple |
| :--- | :--- | :--- |
| Native unit | An alternative currency BTC — a currency | Cross-currency messaging technology XRP — a currency real-time gross settlement system |
| Storage on | Wallet | Wallet |
| Traded on | Exchanges and peer-to-peer | Exchanges and peer-to-peer |
| Transaction style | UTXO-based | Account-based |
| Transaction purpose | Moving Bitcoin | Moving XRP or sending message |
| Implementation | Public blockchain | Public blockchain |
| Elliptic curve | sec256k1 | sec256k1 and ed25519 |
| Addresses | Secret-controlled | Secret-controlled |
| Ownership proof | ECDSA | ECDSA and EdDSA |
| Consensus algorithm | Proof-of-Work | Low-latency Byzantine agreement protocol |
| Hash function | SHA256 | N/A |
| Consensus keepers | Miners | Validators |
| Transaction fees | Voluntary | Mandatory and voluntary |
| Block size | 2,000 TX | N/A |
| Ledger update time | approx. 10 min | approx. 3–5 sec |
| Supply mechanism | Mining | Pre-mined supply and mining |
| Mining reward | 6.25 BTC | N/A |
| Supply cap | 21 million in total | 100 billion in total deflationary in theory, inflationary in practice |

significantly reduced due to the Continuous Linked Settlement's prevalence for fiat transactions, the Ripple system functions outside of it and is still vulnerable.
The way value moves in the Ripple ecosystem is shown in Figure 7.5.
It is worth noting if the chain of banks willing to deal with each cannot be found, or, more likely, is economical. Alice can choose a different route. She can convert her dollars into XRP on an exchange (exposing herself to the credit risk of the exchange), send Bob XRPs, and let him deal with his exchange to convert them into Euros (the credit again).
The Ripple way of moving value should be compared and contrasted with the conventional correspondent banking framework discussed in Section 2.5.1; see especially

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_287_0.png)

**Figure 7.5** Value can be moved across the Ripple network from Alice to Bob in two ways. (a) Several chains of mutually trusting banks can be used, such as $B_A \rightarrow B_1 \rightarrow B_4 \rightarrow B_5 \rightarrow B_B, B_A \rightarrow B_2 \rightarrow B_7 \rightarrow B_B$, and (b) $B_A \rightarrow B_3 \rightarrow B_6 \rightarrow B_B$. If such chains cannot be found, or are too expensive to use, the first currency is converted to XRP on $E_1$, XPR is moved across the network to $E_2$, which is converted into the second fiat currency. Own graphics.

Figures 2.15 and 2.16. The sheer costs of establishing payment rails prevent many participants. Ripple, if it were able to reduce the Herstatt risk, would be a welcome addition to the existing network. It is likely to stay this way for a long time, because the nature of such payments are limited. We observed several segments of Ripple, to attract global, and payment service providers, in the market.

# Chapter 7 Ripple — A Simple Solution to a Complex Problem? | 242 | Blockchain Distributed Ledgers: Mathematics, Economics

# 7.4 Summary

Ripple lacks the revolutionary spirit of Bitcoin and Ethereum. Still, it might gain some traction since the existing network. We leave it to the reader to decide whether it is good enough for the long run. We finished this book by the end of 2020. At that time, Ripple was doing well, commanded the third-highest market cap among all currencies, behind Bitcoin and Ethereum. There are several reasons for that:

- Firstly, as mentioned earlier, the Ripple protocol is limited in scope, allowing more advanced protocols with more comprehensive capabilities, such as Bitcoin and Cardano, to overtake it. Ripple does not support smart contracts. own- Secondly

# 7.5 Exercises

1. Recently, Ripple published a paper, https://ripple.com/wp-content/uploads/2021/01/cbdc-whitepaper.pdf, proposing to use XRP as a “neutral bridge currency” facilitating exchanges between digitized fiat currencies. Describe the pros and cons of their proposal.

# CHAPTER Central Bank Digitalrencies and Stablecoins

# 8.1 Introduction

In many countries Similarly, Yves Mersch, Member of the Executive Board of the European Central Bank (ECB), in a speech given on February 14, 2018, noted: "... printed euro banknotes retain their place and their role in society as legal tender for a very long time. There is no viable alternative to euro cash. There is good reason to believe that banknotes do not take the form of printed paper, cotton, or polymer. However, printed banknotes will remain our core business. And if there is public demand for digital central bank money, this should only be a technical variant of cash" (ECB, 2018).

Hence, building a digital analog of cash addresses well-defined societal needs. The often-repeated statement that credit cards and digital forms of payment already play the role of cash is misguided since the nature of such payments

On the one hand, we observed a heated race between central banks researching, building digital central bank currencies (CBDCs). On the other hand, numerous enterprises, from huge conglomerates to small private companies, develop their stablecoins, which are variations on the same. In this chapter, we discuss some of these efforts and put them in a proper context.

One can envision two types of CBDCs: (a) wholesale CBDCs designed to circulate only among selected financial institutions; (b) retail CBDCs intended for everyday use by the whole population, like physical cash at present. Wholesale CBDCs are very technical—they can dramatically change the better to domestic and cross-border payments discussed in Sections 2.4 and 2.5, but are not going to affect the way ordinary people live their lives.

The reason behind CBDCs and stablecoins' importance is easy to discern—they might be the only way of bringing advantages of distributed ledger technology (DLT) to the real
