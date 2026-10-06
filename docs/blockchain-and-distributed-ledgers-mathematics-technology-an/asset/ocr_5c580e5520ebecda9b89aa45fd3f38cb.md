# Chapter 3 A Primer on Cryptocurrencies and Distributed Ledgers | 65

![](bbox=[0.088, 0.09, 0.912, 0.52])

**Figure 3.8** A block of transactions with additional data in its header to track the current difficulty and the proof-of-work. Own graphics.

rate. Eventually, block production may be so fast that the whole proof-of-work mechanism becomes useless. One concludes that mining cannot be a constant complexity problem: it must be adaptive to the amount of computing invested by miners such that for instance, the resolution remains constant on average.

# 3.6.6 Difficulty under competition

The difficulty target defines the hardness of the proof-of-work problem. Difficulty is endously defined and time-varying such that the expected block production rate is stable, or equivalently, that the time between each blocks is constant on average. The specific duration has no clear justification except that it is slow enough that two valid blocks should rarely be submitted at the same time by miners, and fast enough that waiting for a blockchain update is still tolerable; Bitcoin sets it at 10 minutes. This approach ensures that as the computational power of miners increases, the difficulty target rises; alternatively, as the computational power of miners decreases, the difficulty target drops. The outcome is a constant target of block production rate. Because of its importance, the difficulty level is included in a block's header, as demonstrated in Figure 3.8.