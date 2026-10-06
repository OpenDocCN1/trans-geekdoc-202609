
## 22 Blockchain and Distributed Ledgers: Mathematics, Technology, Economics

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_68_0.png)

(a) Ten DM note.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_68_1.png)

Figure 2.3 (a) a Ten DM note; (b) a hundred DM note. What is the story behind their alphanumeric codes? Sources: Wikipedia.

Consider typical ten and hundred Deutsche Mark notes shown in Figures 2.3 (a), (b). To start with, the 11-characters alphanumeric code of the ten DM banknote, GG6414493L3, is transformed into the 11-digit number according to the following mapping rule:

A, D, G, K, L, N, S, U, Y, Z \Rightarrow 0, 1, 2, 3, 4, 5, 6, 7, 8, 9.

As a result, the note gets its 11-digit number, namely, 22641449433. Numbers 0...9 are mapped into 0...9 according to the following permutation rule:

0, 1, 2, 3, 4, 5, 6, 7, 8, 9 \Rightarrow 1, 5, 7, 6, 2, 8, 3, 0, 9, 4.

Thus, $\pi(0) = \pi(1) = 5$, etc. A group operation $\cdot$ is defined for $n, m, 0 \leq m \leq 9$ in Table 2.1.

> *It is well telling that Germany was born out its most outstanding scientists and artists' on banknotes. The ten Mark note depicts Karl Friedrich Gauss (1777–1855) and his most significant discovery—the ubiquitous curve, also known as the Gaussian distribution. Despite its ubiquity, in Chapter 10, we show that the Gaussian distribution is not useful for describing Bitcoin and other cryptocurrencies returns. The hundred Mark note depicts Clara Schumann (1819–1896) — one of the most distinguished pianists of the Romantic era.*

## Chapter 2 The Global Financial System and its Pain Points

Table 2.1 The multiplication table.

| | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
| 1 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 5 |
| 2 | 2 | 3 | 4 | 0 | 1 | 7 | 8 | 9 | 5 | 6 |
| 3 | 3 | 4 | 0 | 1 | 2 | 8 | 9 | 5 | 6 | 7 |
| 4 | 4 | 4 | 0 | 1 | 2 | 3 | 9 | 5 | 6 | 7 | 8 |
| 5 | 5 | 9 | 8 | 7 | 6 | 0 | 4 | 3 | 2 | 1 |
| 6 | 6 | 5 | 9 | 8 | 7 | 1 | 0 | 4 | 3 | 2 |
| 7 | 7 | 6 | 5 | 9 | 8 | 2 | 1 | 0 | 4 | 3 |
| 8 | 8 | 7 | 6 | 5 | 9 | 3 | 2 | 1 | 0 | 4 |
| 9 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |

Thus, we have $3 \cdot 6 = 9, 6 \cdot 3 = 8$, etc. Checksum rule reads

$$\pi(a_1) \cdot \pi^2(a_2) \cdot \ldots \cdot \pi^{10}(a_{10}) \cdot \pi^0(a_{11}) = 0,$$

where $\pi^0(a) = a$, the 11th digit is used to check that the first 10 digits form proper number. Symbolically, we can write the sum as follows

$$\sum_{n=1}^{11} \pi^{n \pmod{11}}(a_n) = 0.$$

We can easily check that this is case for the banknote in question, and well as for the hundred DM note; see Table 2.2.

Table 2.2 Checking the validity of banknotes. Here $n' = n \pmod{11}$.

| $n$ | Code | $a_n$ | $\pi^{n'}(a_n)$ | Sum | Code | $a_n$ | $\pi^{n'}(a_n)$ | Sum |
|---|---|---|---|---|---|---|---|---|
| 1 | G | 2 | 7 | 7 | A | 0 | 1 | 1 |
| 2 | G | 2 | 0 | 7 | D | 1 | 8 | 9 |
| 3 | G | 6 | 3 | 9 | S | 5 | 4 | 5 |
| 4 | A | 4 | 1 | 8 | B | 2 | 5 | 0 |
| 5 | I | 1 | 2 | 6 | O | 0 | 4 | 4 |
| 6 | A | 4 | 8 | 3 | B | 3 | 3 | 2 |
| 7 | A | 4 | 4 | 7 | A | 4 | 9 | 6 |
| 8 | A | 9 | 9 | 3 | I | 1 | 1 | 5 |
| 9 | | 3 | 6 | 9 | G | 6 | 3 | 7 |
| 10 | L | 4 | 7 | 2 | U | 7 | 1 | 6 |
| 11 | M | 3 | 3 | 0 | 6 | 6 | 6 | 0 |

### 2.2.5 Money as records

Since the late Medieval times, money has gradually assumed the form of records in various ledgers. This aspect of money is all-important in the modern world, especially in the context of DLT. At present, the vast majority of money in circulation is nothing more than a sequence of transactions, organized in ledgers. Private banks maintain their ledgers, while central banks provide the money (central bank cash) and tokens (different money transfer systems), which are used to reconcile these ledgers.

Different mechanisms for representing money as records are shown in Figure 2.4. This figure illustrates the progression from clay tablets to modern bank balance sheets. In Figure 2.4 we show:

- (a) A Sumerian cuneiform tablet. Akkadians and Sumerians have been true pioneers in numerous domains, including writing and money; see, e.g., Goetzmann (2017). They came up with an idea of debt and developed to record the corresponding transactions using inexpensive and extremely durable.
- (b) Egyptian papyrus.
- (c) Tally sticks.
- (d) Stone money.
- (e) British ledger.
- (f) Electronic bank balance sheet.
