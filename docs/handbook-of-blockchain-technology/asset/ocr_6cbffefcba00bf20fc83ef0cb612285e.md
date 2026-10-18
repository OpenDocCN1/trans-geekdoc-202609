be a driver of mass adoption. Clear regulatory frameworks can facilitate the integration of blockchain technology into existing systems where regulatory sandbox programs can support innovation and increase adoption.

**Sourcing:** Another important factor in the adoption of blockchain technology is sourcing (Cunha et al., 2021). Employees with blockchain skills are required to support various areas of blockchain systems including designing, developing, deploying, managing, securing, and others. To achieve this, there is a need for education and training programs to develop a skilled workforce capable of supporting the growing demand for blockchain-based solutions.

**Public Acceptance:** We are still in the early days of blockchain adoption, especially as only a small percentage of the global population uses blockchain applications or cryptocurrencies. Specifically, it is estimated that only 3 percent to 5 percent of adults hold cryptocurrency wallets today. From a different point of view, this may also mean there is huge potential for the blockchain industry as most of the population is still ignoring its existence or prefers not to get involved with it at this time. Blockchain education and smarter regulation are expected to increase these low rates in the coming years (Themistocleous et al., 2020).

# 9.3    REVIEW OF CONSENSUS ALGORITHMS

Achieving consensus in distributed systems is at the heart of this technology, including blockchain. Since by nature such systems do not rely on a central authority for the validation process of transactions, the consensus mechanism plays a key role towards that goal. Such a system would confirm the legitimacy of each transaction by reaching an agreement between all the network participants. Consensus mechanisms existed long before the advent of blockchain. Starting from the “Byzantine Generals Problem”, this is a term derived from the definition of a situation in which two or more parties involved need to agree on a single strategy to avoid total failure, but where some of the parties involved are unethical and disseminate false information or are otherwise unreliable. In 1980, several system architectures were developed forming a distributed system, where Byzantine Fault Tolerance (BFT) consensus mechanisms were adopted. Such mechanisms include Draper’s FTMP, Honeywell’s MMFCS and SRI’s SIFT (Driscoll et al., 2003; Goldberg, 1981; Hopkins et al., 1978).

With the advent of blockchain, though, several CAs have been implemented, each aiming to have similar, but at the same time different, goals. A description of each of those algorithms is outlined in the next paragraphs, with their most common properties depicted in Figure 9.2.

Before examining the CA, we summarize some key parameters used by them:

+   - **Throughput:** The rate at which a network can process transactions. Throughput directly impacts its ability to cater to a high volume of users.
+   - **Scalability:** The capacity of a CA to handle an increasing number of participants. It also ensures the network’s growth without incurring significant performance bottlenecks.
+   - **Security:** It safeguards the network from malicious attacks and preserves the immutability of the blockchain.
+   - **Finality:** It assures that blockchain transactions are immutable.
+   - **Energy efficiency:** It minimizes the environmental impact and ensures the long-term viability of the system.