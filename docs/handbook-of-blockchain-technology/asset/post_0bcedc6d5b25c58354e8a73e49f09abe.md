
Apart from the above two main categories we observe a third one called hybrid. Hybrid CAs seek to combine the advantages of both proof-based and voting-based approaches. Delegated Proof of Stake (DPoS) combines PoS features with a voting mechanism, allowing stakeholders to select a set number of individuals in charge of validating transactions (Snider et al., 2018). This technique improves transaction throughput and energy efficiency while maintaining decentralization. However, it may still be vulnerable to collusion and centralization among delegates. Another hybrid example is DPBFT, which combines pBFT and a dynamic validator set defined by a PoS-based approach (Hao et al., 2018b). However, the implementation complexity of such hybrid systems may limit their general use.

An initial analysis of the abovementioned algorithms reveals the following findings:

- **Real-world Applications:** Distinct blockchain platforms, like Bitcoin and Ethereum, provide practical case studies of PoW and PoS in action. Their operational characteristics, benefits, and challenges offer insights that can guide future CA developments and adoption.
- **Regulatory and Legal Implications:** The continued expansion of blockchain makes its junction with regulatory systems critical. Some CAs, particularly those with centralization tendencies, may face rigorous evaluation. For example, the DPoS algorithm, with its limited validator set, may be considered a centralization facilitator, requiring regulatory attention.
- **Stability and Adoption:** Legacy algorithms, such as PoW, have demonstrated endurance, supporting cryptocurrencies like Bitcoin. In contrast, despite their potential benefits, emergent algorithms face adoption hurdles. The stability of an algorithm is frequently linked to its network size, with larger, more scattered networks generally being safer.
- **Security Implications:** Most consensus algorithms prioritize security, yet flaws still exist. For example, PoW is vulnerable to at least 51% attacks, particularly in computationally weaker networks. PoS variations may face the “nothing at stake” challenge, in which validators lack disincentives to validate multiple blockchain splits.
- **User Participation and Inclusivity:** Blockchain’s underlying idea promotes decentralization and inclusion. Algorithms like PoW, with their high processing needs, may unintentionally exclude participants who do not have an advanced mining infrastructure. On the other hand, PoS and its derivatives foster a more inclusive environment in which users validate transactions based on their network stake.
- **Future Potential and Directions:** Many CAs are still in the early stages of development. As the blockchain technology becomes more mature, we can expect these algorithms to be iteratively refined, making them more proficient and versatile to meet a wider range of purposes.
- **Consensus Algorithms Evaluation:** An evaluation framework is required to further investigate the key characteristics and analyze blockchain CAs. Such a framework will allow us to collect and analyze relevant data and share the results with the community. To address this need we propose a suitable framework as it is shown in Table 9.2. For the development of the framework, we heavily rely on the discussion carried out in the previous sections as well as in the normative literature. Our goal is to assess the proposed CAs framework by analyzing empirical data from blockchain experts who participate on the above CAs. At this stage we are identifying potential experts and in the next few months we are going to run a survey and report the results.

## Table 9.2 Proposed framework for the evaluation of consensus algorithms

| Criteria | Description |
|---|---|
| Decentralization | The extent to which decision-making authority is distributed among nodes in the network. |
| Scalability | The ability of the algorithm to handle increasing workloads effectively as the network grows. |
| Security | The algorithm’s resilience against potential attacks, vulnerabilities, and failure scenarios. |
| Energy Efficiency | The algorithm’s resource requirements, in regard to energy consumption. |
| Fairness | The equal opportunity for all nodes in the network to contribute to the consensus process. |

## 9.5 CONCLUSIONS

This chapter began by focusing on blockchain evolutionary phases and reporting their attributes and influence across numerous industry sectors. In doing so, we refined the existing classifications by separating the last evolutionary phase into two; the new Blockchain 5.0 phase, which is based on Web 3.0 technologies and concentrates on decentralization, and Blockchain 6.0 that focuses on CBDCs.

Significant parameters associated with blockchain evolution phases include scalability, performance, and decentralization. The analysis of these parameters directs our attention to the review of blockchain CAs. Currently, there is confusion around this area, with many issues remaining unclear regarding the quality of CAs, their performance, evaluation and more. This chapter sheds light on the most used CAs and proposes a framework for the evaluation of their main parameters (e.g., decentralization, scalability, security, fairness, and energy efficiency).

Our future steps include the testing of the proposed framework in the practical arena, and our plan is to conduct a survey with key stakeholders in this area in order to examine the proposed framework.

## REFERENCES

Anderson, S., Felici, M. and Littlewood, B. (Eds). (2003). Computer Safety, Reliability, and Security: 22nd International Conference… – Google Books, available at: https://books.google.com.cy/books?id=SaJqCQAAQBAJ&pg=PA243&lpg=PA243&dq=Honeywell+MMFCS&source=bl&ots=HwBGsdulutT&sig=ACfFU3U2hVwo_-3BArBVMOanu7WsLInvA8JQ&hl=en&sa=X&ved=2ahUKEwiZj_q35abqAhXSGewKHfb_D0EQ6AEwAHoECAkQAQ#v=onepage&q=Honeywell+MMFCS&f=false (accessed 29 June 2020).

Angrish, A., Craver, B., Hasan, M. and Starly, B. (2018). “A Case Study for Blockchain in Manufacturing: ‘FabRec’: A Prototype for Peer-to-Peer Network of Manufacturing Nodes.” *Procedia Manufacturing*, 26, pp. 1180–1192.

Baliga, A. (2017). Understanding Blockchain Consensus Models, Whitepaper, pp. 1–14.

Bentov, I., Lee, C., Mizrahi, A. and Rosenfeld, M. (2014). “Proof of Activity: Extending Bitcoin’s Proof of Work via Proof of Stake.” *ACM SIGMETRICS Performance Evaluation Review*, 42(3), 34–37.

Borge, M., Kokoris-Kogias, E., Jovanovic, P., Gasser, L., Gailly, N. and Ford, B. (2017). “Proof-of-Personhood: Redemocratizing Permissionless Cryptocurrencies”, *2017 IEEE European Symposium on Security and Privacy Workshops* (EuroS&PW), pp. 23–26.

Buterin, V. (2014). “A Next-Generation Smart Contract and Decentralized Application Platform.” *White Paper*, 3(37), pp. 2–1.

Chen, S. and Liu, C.C. (2017). “From Demand Response to Transactive Energy: State of the Art”, *Journal of Modern Power Systems and Clean Energy*, 5(1), 10–19. doi: 10.1007/s40565-016-0256-x.

Christodoulou, K., Iosif, E., Inglezakis, A. and Themistocleous, M. (2020). “Consensus Crash Testing: Exploring Ripple’s Decentralization Degree in Adversarial Environments”, *Future Internet*, MDPI AG, 12(3), 53. doi: 10.3390/fi12030053.

Compare, P. (2018). “What Is Proof of Weight? | CoinCodex.” Available at: https://coincodex.com/article/2617/what-is-proof-of-weight/ (accessed 30 September 2020).

Cunha, P. R., Soja, P. and Themistocleous, M. (2021). “Blockchain for Development: A Guiding Framework.” *Information Technology for Development*, 27(3), 417–438. https://www.tandfonline.com/doi/full/10.1080/02681102.2021.1935453

Cunha, P., Soja, P. and Themistocleous, M. (2020). “Blockchain for Development: Preliminary Insights from a Literature Review”, *In Proceedings of the twenty-sixth Americas Conference on Information Systems (AMCIS 2020)*, Virtual Conference, August 10–14, 2020. https://core.ac.uk/download/pdf/326836039.pdf

Deloitte. (2019). *Deloitte’s 2019 Global Blockchain Survey*.

Driscoll, K., Hall, B., Sivencrona, H. and Zumsteg, P. (2003). “Byzantine Fault Tolerance, from Theory to Reality.” In S. Anderson, M. Felici, and B. Littlewood (Eds), *Computer Safety, Reliability, and Security*. SAFECOMP 2003. Lecture Notes in Computer Science, vol 2788. Springer, Berlin, Heidelberg. DOI: 10.1007/978-3-540-39878-3_19.

Dziembowski, S. (2015). “Introduction to Cryptocurrencies”, *Proceedings of the 22nd ACM SIGSAC Conference on Computer and Communications Security*, Association for Computing Machinery, New York, NY, USA, pp. 1700–1701. doi: 10.1145/2810103.2812704.

Egorova, M. A. and Kozhevina, O. V. (2020). “Legal Issues of Using Blockchain Technology in the Issue and Circulation of Cryptocurrency.” In *Advances in Social Science, Education and Humanities Research*, volume 498, Proceedings of the XIV European-Asian Law Congress “The Value of Law” (EAC-LAW 2020).

Fu, X., Wang, H., Shi, P. and Mi, H. (2018). “PoPF: A Consensus Algorithm for JCLedger.” In *Proceedings – 12th IEEE International Symposium on Service-Oriented System Engineering, SOSE 2018 and 9th International Workshop on Joint Cloud Computing*, JCC 2018, Institute of Electrical and Electronics Engineers Inc., pp. 204–209, doi: 10.1109/SOSE.2018.00034.

Gilad, Y., Hemo, R., Micali, S., Vlachos, G. and Zeldovich, N. (2016). “Algorand”, Association for Computing Machinery (ACM), 51–68. doi: 10.1145/2932734.2932757.

Reis, G.A., Chang, J., Vachharajani, N., Rangan, R. and August, D.I., 2005, March. SWIFT: Software implemented fault tolerance. In *International Symposium on Code Generation and Optimization* (pp. 243–254). IEEE.

Hao, X., Yu, L., Zhiqiang, L., Zhen, L. and Dawu, G. (2018a). “Dynamic Practical Byzantine Fault Tolerance”, *2018 IEEE Conference on Communications and Network Security* (CNS), pp. 1–8.

Hao, X., Yu, L., Zhiqiang, L., Zhen, L. and Dawu, G. (2018b). “Dynamic Practical Byzantine Fault Tolerance”, *2018 IEEE Conference on Communications and Network Security*, CNS 2018, Institute of Electrical and Electronics Engineers Inc., doi: 10.1109/CNS.2018.8433150.

Harðarson, A. (2018). *Can Ripple Disrupt the Global Payments Market?* skemman.is.

Iredale, G. (2018). “Top 10 Blockchain Adoption Challenges | 101 Blockchains.” Available at: https://101blockchains.com/blockchain-adoption-challenges/#prettyPhoto (accessed 29 June 2020).

Hopkins, A.L., Smith, T.B. and Lala, J.H. (1978). “FTMP: A Highly Reliable Fault-tolerant Multiprocessor for Aircraft.” *Proceedings of the IEEE*, 66(10), 1221–1239.

Huang, D., Ma, X. and Zhang, S. (2018). “Performance Analysis of the Raft Consensus Algorithm for Private Blockchains”, *ArXiv*, 50(1), 172–181.
