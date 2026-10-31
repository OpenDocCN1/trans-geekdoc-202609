
8. Vinceslas, L., Dogan, S., Sundareshwar, S., & Kondoz, A. M. (2023). Abstracting data in distributed ledger systems for higher level analytics and visualizations. *Future Internet* 15(1), 33.
9. Selvarajan, S., Srivastava, G., Khadidos, A. O., Khadidos, A. O., Baza, M., Alsheri, A., Lin, J. C.-W. (2023). An artificial intelligence lightweight blockchain security model for security and privacy in IIoT systems. *Journal of Cloud Computing* 12, 38. https://doi.org/10.1186/s13677-023-00412-y
10. Diwan, P., Khandelwal, B., Dewangan, B. K., & Shriwas, P. (2023). A bibliometric analysis of network security on blockchain. In 2022 OPJU International Technology Conference on Emerging Technologies for Sustainable Development (*OTCON*), pp. 1–6. IEEE, Raigarh, Chhattisgarh, India.
11. Selvarajan, S., Manoharan, H., Iwendi, C., Al-Shehari, T., Al-Razgan, M., & Alfakih, T. (2023). SCBC: smart city monitoring with blockchain using Internet of Things for and neuro fuzzy procedures. *Mathematical Biosciences and Engineering* 20(12), 20828–20851. doi: 10.3934/mbe.2023922.
12. Natarajan, K., Karthikeyan, R., & Rajalingam, S. (2023). Importance of drone technology in agriculture. In Mohanty, S. N., Ravindra, J. V. R., Surya Narayana, G., Pattnaik, C. R., & Mohamed Sirajudeen, Y. (eds.), *Drone Technology*. Wiley, Hoboken, NJ, pp. 351–374. https://doi.org/10.1002/9781394168002.ch14.
13. Karthikeyan, R., Sundaravadivazhagan, B., Cyriac, R., Balachandran, P. K., & Shitharth, S. (2023). Preserving resource handiness and exigency-based migration algorithm (PRH-EM) for energy efficient federated cloud management systems. *Mobile Information Systems* 11. https://doi.org/10.1155/2023/7754765.
14. Srinivasarao, U., Karthikeyan, R., Sarangi, P. K., & Panigrahi, B. S. (2022). Enhanced movie recommendation and sentiment analysis model achieved by similarity method through Cosine and Jaccard similarity algorithms. 2022 International Conference on Computing, Communication, and Intelligent Systems (*ICCCIS*), Greater Noida, India, pp. 214–218. doi: 10.1109/ICCCIS56430.2022.10037722.
15. Hussain, S. F. M., Karthikeyan, R., Ramamoorthi, S., Arafat, I. S., & Gani, S. S. M. (2023). Enhanced protection for information and network using intrusion detection system. 2023 2nd International Conference on Edge Computing and Applications (*ICECAA*), Namakkal, India, pp. 280–286. doi: 10.1109/ICECAA58104.2023.10212144.
16. Saleem Raja, A., Balasubaramaniam, S., Ganesan, P., Rajasekaran, J., & Karthikeyan, R. (2023). Weighted ensemble classifier for malicious link detection using natural language processing. *International Journal of Pervasive Computing and Communications*. https://doi.org/10.1108/IJPCC-09-2022-0312.

## HSMAO

Efficient resource allocation in cloud-fog Internet of Things (IoT) networks using metaheuristic scheduling algorithm

Santhosh Kumar Medishetti, VNLN Murthy, Ruqqaiya Begum, and Ganesh Reddy Karri

## 11.1 INTRODUCTION

Cloud-Fog Computing (CFC) has revolutionized the landscape of distributed computing by offering a flexible and scalable infrastructure for hosting diverse applications and services [1]. This paradigm leverages both centralized cloud data centers and distributed fog nodes located closer to end-users to efficiently process and manage computing tasks. Task Scheduling (TS) plays a pivotal role in optimizing resource utilization, minimizing latency, and enhancing overall system performance in CFC environments.

Traditional TS approaches often face challenges in dynamically allocating resources to meet the varying demands of applications and users. The inherent complexity, heterogeneity, and dynamic nature of CFC environments require innovative optimization techniques to achieve efficient TS [2]. In recent years, metaheuristic optimization algorithms have garnered significant attention due to their ability to efficiently search large solution spaces and adapt to changing environmental conditions.

In this context, this research focuses on proposing a novel approach for TS in CFC environments utilizing the Harmony Search Mexican Axolotl Optimization (HSMAO) algorithm. Inspired by the harmonious behavior of Mexican axolotls in their natural habitat, HSMAO aims to strike a balance between exploration and exploitation to effectively optimize TS in dynamic and heterogeneous computing environments [3].

The unique characteristics of HSMAO make it well-suited for addressing the challenges associated with TS in CFC [4]. By dynamically adapting to changing workload conditions and resource availability, HSMAO seeks to optimize resource allocation, minimize response time, and reduce energy consumption in CFC environments [5].

In this chapter, we present a comprehensive investigation of the proposed HSMAO algorithm for TS in CFC environments. We evaluate its performance against state-of-the-art scheduling algorithms using various performance metrics and workload scenarios. The results obtained demonstrate the effectiveness and robustness of HSMAO in optimizing TS, thereby contributing to the advancement of resource allocation strategies in CFC. The contribution of this study is as follows:

- A novel optimization approach HSMAO introduces a unique blend of harmony search (HS) and Mexican axolotl-inspired principles for CFC TS, addressing resource allocation challenges in dynamic environments.
- HSMAO optimizes resource allocation, minimizing response time and energy consumption in CFC systems by dynamically adapting to workload changes.
- This study evaluates HSMAO against state-of-the-art algorithms, showcasing its effectiveness and providing insights for designing efficient resource allocation in dynamic computing environments.

The outline of chapter will begin with an introduction, providing an overview of TS in CFC and introducing the HSMAO algorithm. Section 11.2, Related Work, will follow, reviewing existing research on TS in CFC environments. Section 11.3, Research Methods, will detail the design and implementation of HSMAO. Section 11.4, Results, will then be presented, showcasing the performance of HSMAO compared to existing algorithms. Finally, Section 11.5, Conclusion, will summarize the findings, discuss implications, and outline future research directions.

## 11.2 RELATED WORK

Table 11.1 literature survey conducted for TS in CFC using the HSMAO algorithm provides a comprehensive overview of existing research in this domain. The survey encompasses various studies that investigate different aspects of TS techniques, optimization algorithms, and their applications in CFC environments. By synthesizing findings from the reviewed literature, this survey aims to identify gaps, trends, and challenges in current research and pave the way for the introduction and evaluation of the HSMAO algorithm. Through a systematic examination of prior work, this survey lays the groundwork for understanding the state-of-the-art in CFC in TS and highlights the need for novel optimization approaches like HSMAO to address the evolving demands of dynamic and heterogeneous computing environments.

### Table 11.1 Analysis of scheduling parameters and techniques used in a hybrid cloud-fog scenario

| Ref no. | Technique used | Parameters addressed | Limitations |
|---|---|---|---|
| [6] | Priority-based ant colony optimization (PBACO) | Makespan, cost, deadline violation rate, and resource utilization | In this proposed technique will not give the accurate result for multiple parameters while in execution process |
| [7] | Multi-component path-covering problem (MCPCPP) | Execution cost | Author unable to address the execution time, data transfer time for a huge data workflow in multi-clouds |
| [8] | Least total response area (LTRA) | Energy consumption and task reduction time | In this study author considered only limited number of parameters |
| [9] | Deep reinforcement learning (DRL) | Response time, success rate, and cost | Author not concentrated on real-world problems |
| [10] | Modified particle swarm optimization or multi-objective particle swarm optimization (M-PSO) | Monetary cost | Meta heuristic optimization methods for multi-cloud environment is not considered |
| [11] | Improved Jumping Frog Algorithm (IJFA) | Makespan time, execution costs, and resource utilization | Author unable to address the multi-objective model lowering the integrated fog-cloud architecture's response time and energy consumption |
| [12] | Hybrid Genetic Algorithm (HGA) | Cost and execution time | In this work, huge data center space is not considered |
| [13] | Opposition-Based Chaotic Whale Optimization Algorithm (OppoCWOA) | Energy consumption and QoS parameters | In this study future research on data privacy with the help of the blockchain-based FogBus platform was not done |
| [14] | An enhanced version of the Hunter algorithm (possibly in the context of AI or optimization, though the specific meaning might vary) (HunterPlus) | Energy consumption and job completion rate | It simply records one snapshot of the system's performance at any given moment |
| [15] | Hybrid Metaheuristic Algorithm (HMA) | Task completion rate and power consumption | Unable to resolve the issue with intelligent manufacturing lines' task flow scheduling |
