
# Broadcast vs. SPDZ vs. MYSTIKO

Broadcast’s performance and scalability far outstrip those of the standard ring protocol because each node transmits independently of the others. Since with SPDZ, each participant’s gradient vectors are partitioned into secret shares before being broadcast to the other participants, SPDZ is less efficient and scalable than broadcast. With MYSTIKO, the dual broadcast is unnecessary because data is encrypted using Paillier theory and then decrypted centrally using aggregated gradients. The effects of switching to alternative protocols on two different types of performance are shown in [Table 1](#ch4.xhtml#tab4_1).

## Table 1. MYSTIKO: Decreased performance of broadcast, ring, and SPDZ compared to all-reduction

### Communication time

| # Parties | All-reduce | Broadcast | Ring | SPDZ |
| :--- | :--- | :--- | :--- | :--- |
| 20 | 1 | 64–7.2× | 382–39.9× | 131–14.2× |
| 40 | 1 | 79–8.6× | 705–80.8× | 138–14.7× |

### Total synchronization time

| # Parties | All-reduce | Broadcast | Ring | SPDZ |
| :--- | :--- | :--- | :--- | :--- |
| 20 | 1 | 12–51% | 27–100% | 22–6.1× |
| 40 | 1 | 6–25% | 15–59% | 13–2.6× |

While All-Reduce promises “enormous” speedups, when the entire synchronization time is included, those speedups disappear. There has been no change in the general tendencies of the four scalability protocols; the reductions in overall synchronization time are still sizable (with two examples shown in [Table 4.1](#ch4.xhtml#tab4_1)). In comparison to the benefits made available by enhanced communication, however, the improvements are rather modest. This illustrates that the time spent changing gradients before sharing them is the primary cost of private gradient descent compared to non-private gradient descent in MYSTIKO and SPDZ. [Figure 7](#ch4.xhtml#fig4_7) and [Table 1](#ch4.xhtml#tab4_1) illustrate how communication time becomes increasingly crucial for less complex models (5-Layer CNN and Resnet18). However, large models benefit more from gradient modification (like Resnet-50 and VGG-16).

When comparing private and non-private gradient descent, authors find that synchronization time for the former is significantly longer when epoch time is used as a proxy for training time. One reason for this is that while gradient modification is performed on CPUs, training is done on V100 GPUs (which have hundreds of cores). Researchers are unaware of a GPU-accelerated version of the Paillier technique, despite the fact that totally homomorphic encryption does exist (with poorer performance than Paillier on CPUs).

# 5.2 Trusted Execution Environments: AMD SEV

The minimal overheads are the primary benefit when compared to MYSTIKO and SPDZ. Using TEEs causes more work because the EVMs must conduct aggregation. Two to four percent of extra end-to-end latency was incurred for each federated synchronization round. The convergence rate and accuracy were both identical.

# 6. Conclusion

Options for private parameter aggregation in federated learning have been explored in this chapter. It is evident that every approach has its benefits and drawbacks, and the hunt for the optimal answer remains an ongoing field of study. Although differential privacy shows promise for preventing data leaks, it does so at the cost of model accuracy and necessitates non-trivial hyperparameter tuning (learning rate schedule, batch size) for optimal results (or even near optimal results). Given that hyperparameter tweaking relies on the availability of all participants over extended periods and because doing many trials increases total delay, it may not be practical in federated situations. Neither the accuracy nor the convergence rate needs to be tuned for when utilizing homomorphic encryption or a secure multiparty computation scheme. However, they have significant overhead in terms of runtime; as shown by MYSTIKO, additive homomorphic encryption can greatly reduce this overhead if the aggregation protocol is well-designed. Finally, if anyone is willing to invest in some specialized hardware, TEEs can reduce aggregation overhead to almost nothing, with no negative effects on accuracy or convergence.

## References

1.  [Abdel-Basset, M., Hawash, H. and Moustafa, N.](#ch4.xhtml#R_ref4_1) 2022. Toward privacy preserving Federated Learning in internet of vehicular things: Challenges and future directions. IEEE Consum. Electron. Mag., 11(6): 56–66. doi: [10.1109/MCE.2021.3117232.](http://dx.doi.org/10.1109/MCE.2021.3117232)

2.  [Ibitoye, O., Shafiq, M.O. and Matrawy, A.](#ch4.xhtml#R_ref4_2) 2022. Differentially private self-normalizing neural networks for adversarial robustness in Federated Learning. Comput. Secur., 116. doi: [10.1016/j.cose.2022.102631.](http://dx.doi.org/10.1016/j.cose.2022.102631)

3.  [Moudoud, H. and Cherkaoui, S.](#ch4.xhtml#R_ref4_3) 2022. Toward Secure and private Federated Learning for IoT using blockchain. In 2022 IEEE Global Communications Conference, GLOBECOM 2022—Proceedings, pp. 4316–4321. doi: [10.1109/GLOBECOM48099.2022.10000623.](http://dx.doi.org/10.1109/GLOBECOM48099.2022.10000623)

4.  [Guo, K., Chen, Z., Yang, H.H. and Quek, T.Q.S.](#ch4.xhtml#R_ref4_4) 2022. Dynamic scheduling for heterogeneous Federated Learning in private 5G edge networks. IEEE J. Sel. Top. Signal Process, 16(1): 26–40. doi: [10.1109/JSTSP.2021.3126174.](http://dx.doi.org/10.1109/JSTSP.2021.3126174)

5.  [Cholakoska, A., Pfitzner, B., Gjoreski, H., Rakovic, V., Arnrich, B. and Kalendar, M.](#ch4.xhtml#R_ref4_5) 2021. Differentially private federated learningfor anomaly detection in eHealth networks. In UbiComp/ISWC 2021 - Adjunct Proceedings of the 2021 ACM International Joint Conference on Pervasive and Ubiquitous Computing and Proceedings of the 2021 ACM International Symposium on Wearable Computers, pp. 514–518. doi: [10.1145/3460418.3479365.](http://dx.doi.org/10.1145/3460418.3479365)

6.  [Ziller, A. et al.](#ch4.xhtml#R_ref4_6) 2021. PySyft: A library for easy Federated Learning. Studies in Computational Intelligence, 965: 111–139. doi: [10.1007/978-3-030-70604-3_5.](http://dx.doi.org/10.1007/978-3-030-70604-3_5)

7.  [Augustine, C., Anand, J., Kaleeswaran, D., Muneeswari, G. and Santhoshkumar, S.P.](#ch4.xhtml#R_ref4_7) 2022. 6G-based mobile IPTV using adaptive hybrid transmission. In Handbook of Research on Design, Deployment, Automation, and Testing Strategies for 6G Mobile Core Network, IGI Global, pp. 72–91.

8.  [Liang, Y., Guo, Y., Gong, Y., Luo, C., Zhan, J. and Huang, Y.](#ch4.xhtml#R_ref4_8) 2021. FLBench: A benchmark suite for Federated Learning. Communications in Computer and Information Science, 1385 CCIS. pp. 166–176. doi: [10.1007/978-981-16-1160-5_14.](http://dx.doi.org/10.1007/978-981-16-1160-5_14)

9.  [Kong, L., Tao, H., Wang, J., Huang, Z. and Xiao, J.](#ch4.xhtml#R_ref4_9) 2020. Network coding for Federated Learning Systems. Lecture Notes in Computer Science (including subseries Lecture Notes in Artificial Intelligence and Lecture Notes in Bioinformatics), 12533 LNCS. pp. 546–557. doi: [10.1007/978-3-030-63833-7_46.](http://dx.doi.org/10.1007/978-3-030-63833-7_46)

10.  [Dhanalakshmi, R., Anand, J., Sivaraman, A.K. and Rani, S.](#ch4.xhtml#R_ref4_10) 2022. IoT-based water quality monitoring system using cloud for agriculture use. In Cloud and Fog Computing Platforms for Internet of Things, Chapman and Hall/CRC, pp. 183–196.

11.  [Wang, H., Li, A., Shen, B., Sun, Y. and Wang, H.](#ch4.xhtml#R_ref4_11) 2020. Federated multi-view spectral clustering. IEEE Access, 8: 202249–202259. doi: [10.1109/ACCESS.2020.3036747.](http://dx.doi.org/10.1109/ACCESS.2020.3036747)

12.  [Yang, Z., Zhou, M., Yu, H., Sinnott, R.O. and Liu, H.](#ch4.xhtml#R_ref4_12) 2023. Efficient and secure Federated Learning with verifiable weighted average aggregation. IEEE Trans. Netw. Sci. Eng., 10(1): 205–222. doi: [10.1109/TNSE.2022.3206243.](http://dx.doi.org/10.1109/TNSE.2022.3206243)
