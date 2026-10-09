# Table 5: The throughput of Plume with 1000 nodes.

| Block Size(Byte) | Interval(s) | Average parent blocks | Tps |
|---|---|---|---|
| 10K | 1 | 1.45 | 40 |
| 10K | 0.8 | 2.23 | 50 |
| 10K | 0.5 | 2.89 | 80 |
| 10K | 0.2 | 6.35 | 200 |
| 100K | 1 | 7.86 | 408 |

# Table 6: When the block size is 10K bytes, the confirmation time of Plume.

| Amount of Nodes | Time Interval(s) | Confirmation Time(s) |
|---|---|---|
| 600 | 1 | 64 |
| 600 | 0.8 | 55 |
| 600 | 0.5 | 33 |
| 1000 | 1 | 118 |

# Table 7: The structure of a fast block.

| Item | Size(byte) | Description |
|---|---|---|
| round | 8 | Round of the block |
| slot | 2 | Slot of the block |
| vrf | 32 | Result of vrf |
| parent | 32*amount of parent blocks | List of parent blocks |
| txs | 250*amount of Transactions | Transactions |

is higher throughput and narrower DAG. We find that the width DAG in the case that block size is 10K bytes and time interval is 1 second is closed to the case that block size is 100K bytes and time interval is 1 second. While throughput of the later is over twice the former. Therefore, in practical condition, how to balance the time interval and the block size to achieve higher throughput and narrower DAG should be consider seriously.

Secondly, table 6 shows that with the rising of generation rate of blocks, the confirmation time of a certain block also reduces constantly. And in the case that the network scale is 600 nodes and time interval is 0.5 second, the confirmation time is about half a minute which is much less than Bitcoin and Ethereum. Comparing the row 1 and row 4 in table 6, the confirmation time with 1000 nodes is almost twice as the confirmation time with 600 nodes. This is because that, with a certain time interval, larger a network scale means more pending blocks. Therefore, the blocks in larger network need more time to wait for enough descendant blocks to finalize it which stretches the confirmation time.

# 7 CONCLUSION

Plume utilises single-chain to generate a randomness seed, and uses hash inequally to map the randomness seed to a group of participants as committee members. Blocks are created by committee members by computing $VRF_{s_k}(slot|||r_t)$ and construct DAG according to reference rules. As a consequence of our analysis, we have following conclusion: (1) In the case of a small number of malicious nodes, it is secure to generate commit according to the randomness from single chain. Although the randomness seed from the single chain is biased, its entropy is enough to make sure that the malicious nodes can not control the election of committee, and the security of Plume will not be affected. (2) If the randomness from single chain is secure, Plume can resist the double spending attack. Due to Plume adopts the mechanism of density comparison, when honest nodes are in the majority, malicious nodes can not form a double spending attack. (3) In Plume, the confirmation of blocks is probabilistic, and user can decide when a certain block is confirmed. When the interval between block is set appropriately, the confirming time can be controlled in seconds. (4) As a DAG class consensus protocol, Plume also can provide a high throughput without sacrificing decentralization and security. Nevertheless, in Plume there may be several participants pack transactions at the same time, a certain transaction may be packed more than one time which increase the redundancy of system. We will reduce the redundancy in the future.

randomness from single chain. Although the randomness seed from the single chain is biased, its entropy is enough to make sure that the malicious nodes can not control the election of committee, and the security of Plume will not be affected. (2) If the randomness from single chain is secure, Plume can resist the double spending attack. Due to Plume adopts the mechanism of density comparison, when honest nodes are in the majority, malicious nodes can not form a double spending attack. (3) In Plume, the confirmation of blocks is probabilistic, and user can decide when a certain block is confirmed. When the interval between block is set appropriately, the confirming time can be controlled in seconds. (4) As a DAG class consensus protocol, Plume also can provide a high throughput without sacrificing decentralization and security. Nevertheless, in Plume there may be several participants pack transactions at the same time, a certain transaction may be packed more than one time which increase the redundancy of system. We will reduce the redundancy in the future.

# REFERENCES

+   1. 2020. *Blockchain.com*. https://www.blockchain.com/charts/transactions-per-second
2. 2020. *Etherscan*. https://cn.etherscan.com
3. Iddo Bentov, Ariel Gazit, and David Zuckerman. 2016. Bitcoin Beacon. (2016).
4. Joseph Bonneau, Jeremy Clark, and Steven Goldberg. 2015. On Bitcoin as a public randomness source. *Cryptology ePrint Archive, Report 2015/1015*.
5. Juan Garay, Aggelos Kiayias, and Nikos Leonardos. 2015. The Bitcoin Backbone Protocol: Analysis and Applications. (2015).
6. Seyoung Hu, Sangre K Cho, and Sooyoung Kim. 2017. Mining IoT devices using blockchain platform. In *2017 19th 199th international conference on advanced communication technology* (ICACT). IEEE, 644--647.
7. Elithérios Kokoris-Kogias, Philipp Jovanovic, Linus Gasser, Nicolas Gailly, Ewa Syta, and Bryan Ford. 2018. Omniledger: A secure, scale-out, decentralized ledger via sharding. In *2018 IEEE Symposium on Security and Privacy (SP)*. IEEE, 583--598.
8. Yoel Lewenberg, Yonatan Sompolinsky, and Aviv Zohar. 2015. Inclusive block chain protocols. In *International Conference on Financial Cryptography and Data Security*. Springer, 528--547.
9. Chenxing Li, Peilin Li, Dong Zhou, Wei Xu, Fan Long, and Andrew Yao. 2018. Scaling blockchain consensus to thousands of transactions per second. *arXiv preprint arXiv:1805.03870* (2018).
10. Xiaoqiu Li, Peng Jiang, Ting Chen, Xuan Luo, and Qiaoyan Wen. 2020. A survey on the security of blockchain systems. *Future Generation Computer Systems 107* (2020), 841--853.
11. Silvio Micali, Michael Rabin, and Salil Vadhan. 1999. Verifiable random functions. In *40th annual ACM conference on foundations of computer science*. (cat. no. 99CHR7039). IEEE, 120--130.
12. Satoshi Nakamoto. 2019. *Bitcoin: A peer-to-peer electronic cash system*. Technical report, Manubot.
13. Rafael Pass, Lior Seeman, and Abhi Shelat. 2017. *Analysis of the blockchain protocol in asynchronous networks*. In *Annual International Conference on the Theory and Applications of Cryptographic Technology*. Springer, 643--673.
14. Rafael Pass and Elie Sirh. 2018. Thunderchain: Blockchains with Optimistic Instant Confirmation. In *Annual International Conference on the Theory and Applications of Cryptographic Techniques*.
15. Sara Saber, Makhfah Kouhiadizadeh, Sarskias, and Lela Chiyan. 2019. Blockchain technology and its relationships to sustainable supply chain management. *International Journal of Production Research 57, 7* (2019), 2117--2135.
16. Yonatan Sompolinsky, Yoad Perlmutter, and Aviv Zohar. 2016. Secure: Serialization of proof-of-work events: Confirming transactions via recursive elections.
17. Yonatan Sompolinsky and Aviv Zohar. 2015. Secure high-rate transaction processing in bitcoin. In *International Conference on Financial Cryptography and Data Security*. Springer, 507--527.
18. TUC 2019. *The Libra Blockchain*. (https://developers.libra.org/assets/papers/the-libra-blockchain/2020-09-26.pdf)
19. Gavin Wood et al. 2014. Ethereum: A secure decentralised generalised transaction ledger. *Ethereum project yellow paper 151* (2014), 1--32.
20. Mahdi Zamani, Mahvash Movahedi, and Mariana Ryzova. 2018. Rapidchain: Scaling blockchain via full sharding. In *Proceedings of the 2018 ACM SIGSAC Conference on Computer and Communications Security*. 931--948.