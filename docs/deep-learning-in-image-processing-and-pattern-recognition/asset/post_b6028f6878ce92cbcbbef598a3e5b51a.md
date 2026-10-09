
the proposed algorithm remain above 0.97. In other runs, the data packet reception rate of the algorithm proposed in this article is higher than that of the other three algorithms, as shown in Figure 6.

![](img/e4200cc4308edaf8913e513b0f96dbb6_358_0.png)

**Figure 6.** Packet reception rate (energy consumption parameters: $5E_{fuse}$, $5E_{clec}$, $5E_{amp}$).

In the case of low energy consumption parameters, the data packet accuracy of all four methods remains at 1 when the network runs 1000 to 1400 times. When the network runs 1400–2000 times, the data packet accuracy of all four methods has decreased, but the data acceptance rate of the proposed algorithm is always the highest, being maintained above 0.99. When the network runs 1400–1700 times, there is not much difference between the proposed algorithm and Method 3 in this article; however, it is still higher than Method 1 and Method 2. When the network runs 1800–2000 times, the data packet accuracy of the proposed algorithm is significantly higher than that of Method 3 and there is a significant difference between the two. From the simulation results, it can be seen that the data packet accuracy of all four methods remains above 0.97, as shown in Figure 7.

![](img/e4200cc4308edaf8913e513b0f96dbb6_358_1.png)

**Figure 7.** Data accuracy (energy consumption parameters: $E_{fuse}$, $E_{clec}$, $E_{amp}$).

Increasing the energy consumption parameter by five times is different from the simulation results of the data packet acceptance rate, and the difference in data packet accuracy among different algorithms is not significant. Due to the use of an EC encoding fault-tolerant mechanism, the data accuracy of the proposed algorithm is the highest and the decrease is relatively smooth, with an accuracy rate consistently maintained above 0.985. For Method 3, the addition of FEC encoding has achieved a certain fault tolerance rate, but the fault tolerance rate is lower than that of the proposed algorithm. Therefore, the data packet accuracy of Method 3 is lower than that of the proposed algorithm but significantly higher than Methods 1 and 2. As shown in Figure 8.

![](img/e4200cc4308edaf8913e513b0f96dbb6_359_0.png)

**Figure 8.** Data accuracy (energy consumption parameters: $5E_{fuse}$, $5E_{elec}$, $5E_{amp}$).

The energy efficiency of the path is calculated by analyzing the energy value required by the destination node to receive data and the energy value of the original node to send data. Method 2 has the lowest energy efficiency. The difference between the proposed algorithm and Method 3 in this paper is not significant when the number of runs on the network is 1000–1700 times. When the network runs 1700 times, the proposed algorithm in this article is slightly lower than Method 3. After running the network 1700–2000 times, it can be seen that the proposed algorithm has the highest energy efficiency. It is kept above 350, as shown in Figure 9.

![](img/e4200cc4308edaf8913e513b0f96dbb6_359_1.png)

**Figure 9.** Energy efficiency analysis.

From the above simulation results, it can be seen that the proposed algorithm is significantly superior to Method 1 and Method 2 in terms of data packet reception rate, accuracy, and energy efficiency. Compared with the three-phase method, the algorithm proposed in this paper does not have significant advantages in packet reception rate and energy efficiency. However, with the addition of an EC encoding fault-tolerant mechanism, the proposed method significantly outperforms Method 3 in terms of data packet accuracy. Overall, the proposed algorithm is the best of the four algorithms and is a highly reliable and low-energy-consuming routing algorithm.

## 5. Conclusions

By analyzing the reliability of data transmission in wireless sensor networks, the performance of wireless sensor networks can be measured. This paper proposes the E-RelnForMIF algorithm, which improves the multipath routing algorithm by combining the EC fault-tolerant machine and node residual energy sorting selection. The encoded data is transmitted through the calculated path. During transmission, the energy consumption and residual energy of the nodes in the transmission path are always considered and a certain amount of data packet loss is provided to ensure the accuracy of data transmission. After transmitting to the destination node, the destination node decodes the encoded data. In the whole transmission process, the method of node residual energy ranking is used to quantitatively evaluate the energy consumption of nodes, so that the whole algorithm can improve the efficiency of data transmission, reduce energy consumption, and improve the reliability of data transmission. This article compares and analyzes the improved algorithm with traditional methods. From the simulation results, it can be seen that the algorithm proposed in this article has higher data packet reception and accuracy rates than the other three methods and also has higher energy efficiency than the other three methods. Therefore, the E-RelnForMIF algorithm in this article is better. Due to its excellent reliability advantage, it can be applied to the detection of all toxic gas parameters in public places such as schools and factories. Detection of temperature and pressure in pipelines such as water supply, heating, and oil supply is essential to prevent the occurrence of disasters. In the future, with the deepening of research on wireless sensor networks, they can also be applied to the healthcare industry. Remote detection of patients' conditions will enable them to receive timely treatment even at a distance from the hospital, achieving remote medical control.

**Author Contributions:** Conceptualization, Q.W.; methodology, Q.W.; software, H.H.; validation, J.Q., Q.W. and J.G.; writing—original draft preparation, X.L. and C.Y.; writing—review and editing, C.Y.; project administration, Q.W.; funding acquisition, X.L. and Q.W. All authors have read and agreed to the published version of the manuscript.

**Funding:** This research was funded by Heilongjiang Postdoctoral Foundation (Grant number LBH-Z222200) and Heilongjiang Provincial Natural Science Foundation of China (Grant number YQ2022FP014).

**Acknowledgments:** The authors acknowledge Heilongjiang Postdoctoral Foundation (Grant number LBH-Z222200) and Heilongjiang Provincial Natural Science Foundation of China (grant number YQ2022FP014).

**Conflicts of Interest:** The authors declare no conflict of interest.

# References

1. Ahmed, S.; Ahmed, W.; Alaid, O.; Ahmed, M.K. Compressive sensing based secure data aggregation scheme for IoT based WSN applications. *PLoS ONE* **2021**, *16*, 10160–10187.
2. Nouf, A.; Tahani, G. A Novel Security Architecture for WSN-Based Applications in Smart Grid. *Smart Cities* **2022**, *5*, 633–649.
3. Lavanya, S.; Prashant, S.; Jayachitra, S.; Shenbagarajan, M. A Tuned classification approach for efficient heterogeneous fault diagnosis in IOT-enabled WSN applications. *Measurement* **2021**, *183*, 109771–109787. [CrossRef]
4. Mustafa, A.S.; Ismail, B.; Abdelhadi, A.; Pascal, L. Enhanced efficient outlier detection and classification approach for WSNs. *Simul. Model. Pract. Theory* **2022**, *120*, 102618–102635.
5. He, C.B.; Qin, K.; Li, M.Z. Variable Factor Based Non Uniform Clustering Routing Protocol for WSNs. Inf. Comput. 2022, 34, 11–13.
6. Zhao, F.; Wei, K.; Chen, H.B. A data aggregation node selection algorithm based on average residual energy in sensor networks. Comput. Appl. Res. 2012, 29, 3096–3098.
7. Elsway, A.A.; Khedr, A.M.; Oruba, A.; Walid, O. Energy-aware disjoint dominating sets-based whale optimization algorithm for data collection in WSNs. J. Supercomput. 2022, 79, 10227–10249. [CrossRef]
8. Xu, J.Q.; Ding, Y.G.; Zhao, H.; Zhang, X.Y.; Bi, F.W. Energy Balanced Reliable Routing Metrics in Wireless Sensor Networks. Comput. Eng. 2009, 35, 87–89.
9. Zhuang, Y.; Shen, J. ReInForm-CS routing algorithm for CS based wireless sensor networks. Comput. Syst. Appl. 2012, 21, 140–144.
10. Wang, D.D.; Chai, Q.L.; Cai, X.J. Research and Simulation of ReInFormM Routing Algorithm Based on Energy Selection. Comput. Simul. 2011, 28, 174–177.
11. Zhang, K.L. Research and Implementation of Error Tolerant Mechanism for Erasure Codes in Distributed Systems. Comput. Mod. 2012, 8, 47–50.
12. Zhang, Y.H.; Yan, L.J. Low energy routing protocol based on the remaining energy of all nodes. Microcomput. Appl. 2021, 37, 20–23.
13. Pristupa, P.V.; Suschenko, S.P.; Mikheev, P.A.; Moiseev, A.N. Efficiency Analysis of the Forward Error Correction at the Transport Protocol Level. Autom. Remote Control 2022, 83, 1059–1077. [CrossRef]
14. Suellen, L.; Ricardo, M.; Carlos, M.; Francisco, V. Combining Network Coding and Retransmission Techniques to Improve the Communication Reliability of Wireless Sensor Network. Information 2021, 12, 184. [CrossRef]
15. Sun, C.L.; Wang, Z.Z.; Lu, D.W.; Cao, L.; Yue, Y.G.; Ding, H.H.; Hu, Z.Y. An Energy Efficient and Reliable Multipath Transmission Strategy for Mobile Wireless Sensor Networks. Comput. Intell. Neurosci. 2022, 80, 3804–3819. [CrossRef] [PubMed]
16. Zhu, B.T.; Ebrahim, B.; Nguyen, H.H.; Robert, B.; Jerome, H. Improved Soft-k-Means Clustering Algorithm for Balancing Energy Consumption in Wireless Sensor Networks. IEEE Internet Things J. 2021, 8, 4868–4881. [CrossRef]
17. Jiang, Y.; Wu, M. Research on Reliability of Data Transmission Based on Network Coding in WSN. Comput. Technol. Dev. 2013, 23, 148–151.

**Disclaimer/Publisher’s Note:** The statements, opinions and data contained in all publications are solely those of the individual author(s) and contributor(s) and not of MDPI and/or the editor(s). MDPI and/or the editor(s) disclaim responsibility for any injury to people or property resulting from any ideas, methods, instructions or products referred to in the content.
