202 | Blockchain Distributed Ledgers: Mathematics, Technology, Economics

superseded by more robust and less wasteful technology in the distant future. In this regard, an analogy with vinyl discs jumps to mind. Although remain ardent aficionados of vinyl discs, the community has shrunk dramatically since their prime days.

# 5.8 Summary

After the publication of the seminal paper by Nakamoto (2008), Bitcoin took the world by storm. The fact that it had survived for more than a decade, and continues to thrive at present, speaks volumes. The Bitcoin protocol is a marvel of engineering, built in a a very innovative way on top of excellent (if not the most modern) cryptographic primitives. Bitcoin cleverly combines cryptographic might with economics and game theory insights to make the protocol robust and mostly impervious to malicious interference.

However, the future of Bitcoin is uncertain. As shown in the chapter, it is not digital gold. The original promises, it is highly centralized in its implementation, mining and trading. Moreover, BTC ownership is exceedingly concentrated and, therefore, is profoundly undermines, or at least no democratic than the real world it wishes to improve. Besides, Bitcoin is not genuinely but rather pseudonym. Despite the above, we feel that Bitcoin has a future (if highly volatile) stock of value and can find other exciting applications. For further discussion of BTC prices and related topics, see Chapter 10.

We hope that this book will help the reader make her mind about Bitcoin’s merits and weaknesses. In our mind, it is a great success at present, but more likely than not, it will be eclipsed by other protocols in the future.

# 5.9 Exercises

+   1. Explain how one can use a good hash function to perform a proof-of-work (PoW) calculation?
2. Explain why two nonces are needed to find a block.
3. Derive the distribution of time it takes to mine a block successfully. Calculate mean and standard deviation for the time it takes a miner whose share of hashing power is p to find a block. Assuming that a miner holds a proportion p of the total mining capacity, what is the probability that she may find to n blocks in a row? What are the implications in censorship resistance and adverse chain reorganization?
4. Consider a secret miner owning more than 50% of the mining capacity and building an unpublished, parallel chain. Explain the potential threats.
5. Explain why miners may find it to join forces with other miners — so-called mining pools. How does it impact the distribution of mining rewards?
6. Design an algorithm to estimate the number of bitcoins actually spent per block.