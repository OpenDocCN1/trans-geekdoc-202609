
The suggested method reduces latency by determining the closest node to each user using the CS algorithm and estimating the distance between nodes and users. The program successfully identified the occasion nodes for processing 4 user requests delivered to a base broker during an evaluation. The findings illustrate a substantial drop in latency when employing the CS method. This method was utilized to evaluate its effectiveness by comparing latency with and without the method. The table contrasts the delay in microseconds and the distance in kilometers while using and without the cuckoo algorithm.

| Latency (µs) with Cuckoo | Latency (µs) without Cuckoo | Distance (km) with Cuckoo | Distance (km) without Cuckoo |
| --- | --- | --- | --- |
| 0.0092 | 0.0284 | 7.0711 | 21.21324 |
| 0.0130 | 0.0748 | 5.02 | 28.0180 |
| 0.0064 | 0.0068 | 1.01 | 1.02 |
| 0.0213 | 0.1086 | 7.0712 | 35.3555 |

[Table 35.3 Final outcome](#ch35.xhtml#R_tab35_3)

## Conclusion

In summary, the CS algorithm has been developed as a highly efficient technique for the allocation of a resource in fog computing, especially in mitigating latency-related difficulties. This success can be attributed to its unique features: combining distance measurements between fog nodes and users into the fitness function and applying queue scheduling with 3 suggested lists in the basic broker, all of which are dependent on loaded criteria to decide whether or not a node is available. This precision in node selection significantly reduces randomness, enhancing the overall system performance. Latency, a pivotal metric in assessing resource allocation, encompasses various phases of request processing, from reception and proposal scheduling to response transmission. The suggested approach, which is founded on the CS algorithm, exhibits significant benefits in terms of cutting down on latency and increasing system efficacy. These results highlight the utmost significance of the CS algorithm and its potentially game-changing role in fog computing system optimization. Future research endeavors could delve deeper, focusing on further advancements and optimizations, especially in the realm of IoT applications where the CS method holds significant promise for resource allocation.

## References

*   Abd-Ali, R. S., Radhi, S. A., and Rasool, Z. I. (2020). A survey: The role of the internet of things in the development of education. Indonesian J. Elect. Engg. Comp. Sci. 19(1), 215–221. [https://doi.org/10.11591/ijeecs.v19.i1.pp215-221](https://doi.org/10.11591/ijeecs.v19.i1.pp215-221).

*   [Abd Elaziz, M., Abualigah, L., and Attiya, I.](#ch35.xhtml#R_ref35_2) (2021). Advanced optimization technique for scheduling IoT tasks in cloud-fog computing environments. Fut. Gen. Comp. Sys., 124, 142–154.

*   [Agarwal, M. and Srivastava, G. M. S.](#ch35.xhtml#R_ref35_3) (2018). A Cuckoo search algorithm-based task scheduling in cloud computing. Adv. Intel. Sys. Comput., 554, 293–299. [https://doi.org/10.1007/978-981-10-3773-3_29](https://doi.org/10.1007/978-981-10-3773-3_29).

*   [Alsadie, D.](#ch35.xhtml#R_ref35_4) (2022). Resource management strategies in fog computing environment-A comprehensive review. Int. J. Comp. Sci. Netw. Sec., 22(4), 310–328.

*   [Bhatia, H., Panda, S. N., and Nagpal, D.](#ch35.xhtml#R_ref35_5) (2020). Internet of things and its applications in healthcare-A survey. 2020 8th Int. Conf. Reliab. Infocom Technol. Optim. (ICRITO), 305–310. [https://doi.org/10.1109/ICRITO48877.2020.9197816](https://doi.org/10.1109/ICRITO48877.2020.9197816).

*   [Bittencourt, L. F., Diaz-Montes, J., Buyya, R., Rana, O. F., and Parashar, M.](#ch35.xhtml#R_ref35_6) (2017). Mobility-Aware application scheduling in fog computing. IEEE Cloud Comput., 4(2), 26–35. [https://doi.org/10.1109/MCC.2017.27](https://doi.org/10.1109/MCC.2017.27).

*   Ghobaei-Arani, M., Souri, A., and Rahmanian, A. A. (2020). Resource management approaches in fog computing: A comprehensive review. J. Grid Comput., 18(1), 1–42.

*   [Hao, Z., Ed Novak, Yi, S., and Li, Q.](#ch35.xhtml#R_ref35_8) (2017). Challenges and software architecture for fog computing. IEEE Int. Comput., 21(2), 44–53. [https://doi.org/10.1109/MIC.2017.26](https://doi.org/10.1109/MIC.2017.26).

*   [Hong, Cheol-ho, and Varghese, B.](#ch35.xhtml#R_ref35_9) (2018). Resource management in fog / edge computing: A survey. J. Supercomput. 75. [https://doi.org/10.1018/s13227-018-02763-2](https://doi.org/10.1018/s13227-018-02763-2).

*   [Islam, M. S. Ul, Kumar, A., and Hu, Y.-C.](#ch35.xhtml#R_ref35_10) (2021). Contextaware scheduling in fog computing: A survey, taxonomy, challenges, and future directions. J. Netw. Comp. Appl., 180, 103008.

*   [Iyapparaja, M., Naif Khalaf Alshammari, M. Sathish Kumar, S. Krishnan, and Chiranji Lal Chowdhary](#ch35.xhtml#R_ref35_11). (2022). Efficient Resource Allocation in Fog Computing Using QTCS Model. Computers, Materials & Continua. 70(2). DOI:[10.32604/cmc.2022.015707](http://dx.doi.org/10.32604/cmc.2022.015707), 1–15.

*   [Jamil, B., Ijaz, H., Shojafar, M., Munir, K., and Buyya, R.](#ch35.xhtml#R_ref35_12) (2022). Resource allocation and task scheduling in fog computing and internet of everything environments: A taxonomy, review, and future directions. ACM Comput. Sur., 54(11s). [https://doi.org/10.1145/3513002](https://doi.org/10.1145/3513002).

*   [Jamil, Bushra, Humaira Ijaz, Mohammad Shojafar, Kashif Munir, and Rajkumar Buyya](#ch35.xhtml#R_ref35_13). (2020). Resource allocation and task scheduling in fog computing and internet of everything environments: A taxonomy, review, and future directions. ACM Computing Surveys (CSUR). 54(11s): 1–38.

*   [Kaur, Mandeep, and Rajni Aron](#ch35.xhtml#R_ref35_14). (2021). A systematic study of load balancing approaches in the fog computing environment. The Journal of supercomputing. 77(8), 9202–9247.

*   [Khattar, N., Sidhu, J., and Singh, J.](#ch35.xhtml#R_ref35_15) (2019). Toward energyefficient cloud computing: A survey of dynamic power management and heuristics-based optimization techniques. J. Supercomput., 75. [https://doi.org/10.1007/s11227-019-02764-2](https://doi.org/10.1007/s11227-019-02764-2).

*   [Ma, K., Bagula, A., Nyirenda, C., and Ajayi, O.](#ch35.xhtml#R_ref35_16) (2019). An Iot-based fog computing model. Sensors (Switzerland), 19(12), 1–17. [https://doi.org/10.3390/s19122783](https://doi.org/10.3390/s19122783).

*   [Mahmud, Redowan, Kotagiri Ramamohanarao, and Rajkumar Buyya](#ch35.xhtml#R_ref35_17). (2020). Application management in fog computing environments: A taxonomy, review and future directions. ACM Computing Surveys (CSUR). 53(4). 1–43.

*   [Martinez, I., Hafid, A. S., and Jarray, A.](#ch35.xhtml#R_ref35_18) (2021). Design, resource management, and evaluation of fog computing systems: A survey. IEEE Int. Things J., 8(4), 2494–2516. [https://doi.org/10.1109/JIOT.2020.3022699](https://doi.org/10.1109/JIOT.2020.3022699).

*   [Member, Student, and Luo, J.](#ch35.xhtml#R_ref35_19) (2018). Tasks scheduling and resource allocation in fog computing based on containers for smart manufacturing. IEEE Trans. Indus. Informat., 14(10), 4712–4721. [https://doi.org/10.1109/TII.2018.2851241](https://doi.org/10.1109/TII.2018.2851241).
