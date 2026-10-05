
从上述调度指标可以观察到，所有类型的算法都将响应时间、延迟、完跨时间（makespan）等作为其基本的调度目标。

## 4.1 任务调度中传统、元启发式和基于机器学习的解决方案比较

与传统的任务调度方法相比，基于元启发式的方法和基于机器学习的方法运行时间更高。元启发式算法在给出最优解决方案之前会产生大量的运行时间，因为这些算法必须收敛。它们尝试种群中所有可能的解决方案以免陷入局部最优，从而给出全局最优。基于机器学习的解决方案运行时间较长，因为它们需要先对数据集进行训练，而传统方法没有这些要求。但是，元启发式方法和基于机器学习的方法在响应时间、能耗、完跨时间等方面表现出更好的性能。一些作者使用了这些方法的组合来权衡运行时间与其他参数。与传统方法相比，元启发式和基于机器学习的解决方案能够生成更优的上下文，从而在此基础上进行任务分类、调度和分配。

## 5 结论

作者部署了多种方法通过云和物联网设备使雾计算层智能化。作者考虑了各种依赖任务和非依赖任务、工作流分析，并提出了不同的解决方案。若干算法在云端和雾端均结合了不同的元启发式和机器学习算法，以获得最优解决方案。然而，这种不同流的组合可以提高性能。我们根据任务的性质、调度目标和解决方案属性，在不同的表格（表3、4、5）中对云环境或雾环境中的任务放置进行了对比分析。分析表明，如果说传统调度方法在运行时间和资源分配方面收益最大，那么基于机器学习和元启发式的任务调度和资源分配方法能够为任务关键型应用开发出更优的解决方案的上下文。因此，许多作者使用了这些方法的组合来弥补每种方法独立使用时的缺陷。本文对各类算法进行了广泛研究，为了解现有解决方案提供了见解，也为研究人员未来开展此类调查以开发更好的解决方案提供了参考。

## 参考文献

- [1] Ahmed, E., Yaqoob, I., Gani A., Imran M., and Guizani M., “Internet-of-Things-based Smart Environments: State of the Art, Taxonomy, and Open Research Challenges,” IEEE Wireless Communication., vol. 23, no. 5, pp. 10–16, Oct. 2016.
- [2] Shafiq K., Khawaja B. A., Sabir F., Qazi S. and Mustaqu M., “Internet of Things (IoT) for Next-Generation Smart Systems: A Review of Current Challenges, Future Trends and Prospects for Emerging5G-IoT Scenarios,” in IEEE Access, vol. 8, pp. 23022–23040, 2020, doi: 10.1109/
- [33] Co-Operating With the Working Group RFID of the EPTP EPOS, Internet of Things in 2020, Roadmap for the Future, Version 1.1, INFSO D.4 Networked RFID INFSO G.2 Microsanosystems, May 2008.
- [34] Gedon, J. Jenschchel, L. Wang and M. Mühäuser "Invited Paper: Edge and Fog Computing: Vision and Future Challenges." (2018).
- [35] Dustavar, S. Avancali C. and Murturi I., "Invited Paper: Edge and Fog Computing: Vision and Research Challenges," 2019 IEEE International Conference on Service-Oriented System Engineering (SOSE), San Jose, CA, USA, 2019, pp. 96–9609, doi:10.1109/SOSE.2019.00023.
- [36] Carvalho L. L., da Silva D. M. and Sofia R. C., "Leveraging Context-Awareness to Support the IoT Cloud Edge Computing," IEEE Conference on Mobile Edge Computing (FEMC), Paris, France, 2020, pp. 356–359, doi:10.1109/FEMEC49853.2020.9144760.
- [37] Narayana, P., Paravatani P. and Keerti K. A., "Research on Scheduling Strategies in Fog Computing Environment," 2020 International Conference on Emerging Trends in Information Technology and Engineering (IT-ITE), Vellore, India, 2020, pp. 1–6, doi:10.1109/ITE4970.2020.203.
- [38] Xin Yang, Nasir Zamani R. and Rahman M., "Task Scheduling Mechanisms in Fog Computing: Reviews, Trends, and Perspectives," Vol. 50, No. 1, pp. 22–38, 2020, doi:10.1108/ITK-2019-1086-6.
- [39] Redwan, Mohammad Karim and Rahman M., "Application Management in Fog Computing Environments: A Survey, Review and Future Directions," ACM Computing Surveys, Vol. 53, No. 4, July 2020, doi:10.1149/3410395.
- [40] Thanh Le Duc, Rafael Garcia Lucia, Paolo Casari, Per-Olav Öberg, "Machine Learning Methods for Resource Provision in Edge Computing: A Survey," ACM Computing Surveys, Vol. 52, No. 6, Article 95.
- [41] Essam H., Ahmed G., Yaser P. Nunnothari Sugathan, "Task Scheduling in Cloud Computing on Metaheuristics: Review, Taxonomy, Open Challenges and Futures," Swarm and Evolutionary Computation, Volume 62, 2021, 10841, doi:10.1109/2210-452.
- [42] Ria A., Alrasi Saif T., "Task Scheduling in Cloud Computing on Metaheuristics: A Review," EAI Embedded Transactions on Cloud Systems, January 2020, doi:10.4201/10618-13.6789.
- [43] Khaled Mahatrou, Ahmed, "Scheduling in Fog Computing: A Survey," International Journal of Distributed and Networking Computing, Vol. 9(1), pp. 59–74, 2021. DOI:10.2901/jndnc.2111.
- [44] Tahini Alyabadi, "Hotloading Tasks in Fog Computing based on Importance," Computer Science, Volume 169, 2023, pp. 560–569, doi:10.1116/j.procs.2023.12.388.
- [45] Lin, L. P., Xiong and Lin, M., "Distributed and Application-Aware Task Scheduling," 14th International Conference on Mobile Adhoc and Sensor Networks (MSN), 2018, pp. 165–170, doi:10.1109/MSN.2018.1.
- [46] Minh-Quang Tran, Duy Nguyen, Tran Vu, "Task Placement on Fog Computing Made for IoT Communications and Mobile Computing," 2019, Article ID 62154, 17 pages, doi:10.1155/6254.
- [47] Chandhari, Tejas, "Prioritized Task Scheduling in Fog Computing," (2018). Master's Projects.581, doi:10.1399/etd.pqc, http://scholars.asu.edu/etd_projects/581.
- [48] Feller, A., Elter, K., Naif and Chung, "A Multi-Agent Based Model for Task Scheduling in Fog-Cloud Platform," 2020 IEEE International Conference on Informatics, IoT and Enabling Technologies (IoT), Doha, Qatar, 2020, pp. 377–382, doi:10.1109/IOT4869.2020.90286.
- Lin, Yu J. and Luo H., "Tasks and Resource Allocation on Containers," IEEE Transactions on Informatics, vol. 14, no. 10, pp. 4712–4721, Oct. 2018, doi:10.1109/TI.2018.285124.
- [49] Elarbi Badini, "QoS-Aware Placement of Tasks on a Fog Cluster in Edge Computing Environment," Journal of Ubiquitous Systems & Predictive Networks, Vol 13, No. 1 (2020) pp. 11–19, doi:10.5389/JUSP.13.01.102.
- Brebach, M., Schäfer D., Einger J and Becker C., "Context-Aware Data and Task Placement in Edge Computing Environments," 2019 International Conference on Pervasive Computing and Communications (PerCom), Kyoto, Japan, 2019, pp. 1–10, doi: 10.1109/PERCOM.2019.876378.
- [23] Shudang Wang, Yanqi Li, Shunchen Pang, Qianhua Hu, Shuyu Wang, Jianli Zhao, “A Task Scheduling Strategy in Edge-Cloud Collaborative Scenario Based on Dataset,” Scientific Programming, 2020, Article ID 3967847, 9 pages. doi: https://doi.org/10.1155/2020/3967847
- [24] Haaisen K. M. and K. Musa, “Efficient Task Offloading for IoT-Based Applications in Cloud Computing Using Analytics,” in IEEE Access, vol. 8, pp. 37191–37200, 2020, doi: 10.1109/ACCESS.2020.2975471.
- [25] Qayyum T. Tabbrez, Malik A. W. and Hayat K., “Multi-Level Resource Sharing Framework Using Collaborative Filtering for Smart Cities,” IEEE Access, vol. 9, pp. 21859–21869, 2020, doi: 10.1109/ACCESS.2020.30153.
- [26] Goudar U., Mu J. Ravi M., “Intelligent and Agile Control of Edge Resources for Latency-Sensitive IoT Services,” IEEE Transactions on Mobile Computing, vol. 20, no. 4, pp. 12791–12802, 2021, doi: 10.1109/TMC.2020.305167.
- [27] Bakdar A., Shreen H. Talaat M., “Cost-Aware Task Scheduling in Fog Environment,” 2020 IEEE International Conference on Signal Processing (ICCPS), pp. 1–8, doi:10.1109/ICCPS.2020.914010.
- [28] Sahni S., Chao J. Lang Y., “A High-Efficient ‘Cloud-Edge’ Aware Strategy for Task Deployment and Load Balancing,” IEEE Internet of Things Journal, vol. 6, pp. 3512–3524, 2019, doi:10.1109/IOT.2018.286857.
- [29] Abbasi M., Mohammad J. Pand E., “Quantized Approach of Loading Scheduling in Fog Environment Using Genetic Algorithm,” Journal of Green Computing, vol. 5, no. 3.
