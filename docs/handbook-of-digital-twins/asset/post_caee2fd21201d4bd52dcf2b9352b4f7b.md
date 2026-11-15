
Alternative techniques, such as learning from demonstration [43] and active learning [44], should be considered to augment the approach with. Once reinforcement agents become experienced enough with different instances and flavors of the same class of Digital Twins, new agents can be trained by experienced agents. Such settings would allow removing the human from the loop and replacing the manually assembled default policies with the ones the agents themselves inferred from previous cases.

### 8.4.3.2 Policy Reuse in Congruent Problems

One of the main benefits of building inference methods specifically for DEVS is that the wide range of problems that can be mapped onto DEVS can effectively leverage the approach presented in this book chapter. This facilitates the much sought-after reuse of simulators and simulator components [7,8]. Reusing the policy of the agent is different from simulator reuse. When a policy is reused, previously learned patterns of simulator inference are used to solve slightly different simulator inference problems.

Policy reuse is typically achieved by transfer learning [45], in which the output layer of the neural network encoding the policy is removed, and the rest of the network is retrained on the new problem. This, in effect, associates the previously learned solution patterns with the tokens of the problem at hand. The effectiveness of transfer learning in simulator inference is determined by the similarity of the original problem and the new one.

### 8.4.3.3 Ensembles of Inverse Learning Methods

The approach presented in this book chapter uses a generic reward function based on behavioral traces. However, some problems might necessitate more specialized reward functions. As discussed in Section 4.4, appropriately capturing the reward function becomes challenging as the complexity of the underlying system increases. Similarly, we used a set of generic DEVS model engineering operations, but domain-specific approaches might prefer to leverage a more refined set of actions. For example, the exact value by which the time advance is increased or decreased in Section 4.3.4 was an arbitrary choice at our end.

To approach the estimation of these parameters in a sound way, inverse reinforcement learning methods [46] can be employed. Inverse reinforcement learning aims to learn the reward function under a fixed policy. Similarly, the action space can be inferred under a fixed policy and reward function. We foresee advanced learning settings in which the reward function, value function, and actions are inferred in an iterative fashion by an ensemble of inverse reinforcement learning algorithms. This will enable simulator inference processes that are better tailored to the problem at hand.

### 8.4.3.4 Co-design of Digital and Physical Capabilities

The feasibility of using machine learning methods is heavily influenced by the amount and quality of data that can be used to train the machine learning agent. The same holds for the services provided by Digital Twins. In the context of the approach presented in this book chapter, data quality and quantity can be improved by considering data concerns in the early design phases of Digital Twins. We anticipate research directions focusing on the co-design of Digital Twin services and the instrumentation of the physical asset (such as the sensor and actuator architecture, data management infrastructure, and appropriate network configuration). Such integrated approaches will enable more efficient harvesting of data on the physical asset, give rise to more sophisticated real-time data processing capabilities [47], and improve the costs associated with the engineering of Digital Twins.

### 8.4.3.5 The Need for Unified Digital Twin Frameworks

The lack of unified Digital Twin frameworks adversely affects the engineering of their simulators [48], even if automated as discussed in this chapter. Limitations of reports on Digital Twin have been recently identified as a factor that hinders understanding and development of Digital Twin tools and techniques [49]. Experience reports often omit important characteristics of Digital Twin, such as the scope of system-under-study, the time-scale of processing, and life-cycle stages. Standards such as the Reference Architectural Model Industry 4.0 (RAMI 4.0) [50] and various academic frameworks [51,52] are the first steps toward alleviating this issue, although they only address select aspects of Digital Twins.

The benefits of ontology-based semantic knowledge management have been demonstrated in the design of complex heterogeneous systems [53]. The success of ontology-based techniques in the realm of cyber-physical systems [54] sets promising future directions in their application in the design of Digital Twins.

## 8.5 Conclusion

As the complexity of services provided by Digital Twins keeps increasing, the importance of advanced simulation capabilities to support those services grows as well. Therefore, proper automation is paramount in enabling the construction of simulators.

This chapter outlined how machine learning can be used to automate the construction of simulators in Digital Twins. We illustrated the concepts of such an approach based on DEVS and reinforcement learning. Depending on the problem at hand, other simulation formalisms and other machine learning approaches might be appropriate choices as well. However, DEVS projects to be an appropriate choice for a wide range of problems as it is commonly considered the assembly language of simulation formalisms [18]. Reinforcement learning is a natural fit for problems in which previously labeled data are not available, but model operations can be exhaustively listed. The formal foundations of DEVS provide a good starting point for the latter, allowing reinforcement learning to be leveraged for inferring DEVS models.

The approach discussed in this chapter is of particular utility in the context of systems that are challenging to model due to their complexity, such as Digital Twins. We anticipate numerous lines of research on this topic unfolding in the upcoming years.

## Bibliography

- [1] Adil Rasheed, Omer San, and Trond Kvamsdal. Digital twin: Values, challenges and enablers from a modeling perspective. IEEE Access, 8:21980–22012, 2020.
- [2] Benoit Combemale et al. A hitchhiker’s guide to model-driven engineering for data-centric systems. IEEE Software, 2020, 38(4): 71-84.
- [3] Sheldon M Ross. Simulation (Statistical Modeling and Decision Science) (5th ed.). Academic Press, 2012. ISBN 978-0-12-415825-2.
- [4] Francis Bordeleau, Benoit Combemale, Romina Eramo, Mark van den Brand, and Manuel Wimmer. Towards model-driven digital twin engineering: Current opportunities and future challenges. In Systems Modelling and Management: First International Conference, ICSMM 2020, Bergen, Norway, June 25–26, 2020, Proceedings 1. Springer International Publishing, 2020: 43–54.
- [5] Michael Spiegel, Paul F Reynolds Jr., and David C Brogan. A case study of model context for simulation composability and reusability. In Proceedings of the Winter Simulation Conference, 2005. IEEE, 2005: 8 pp.
- [6] Thijs Defraeye, Chandima Shrivastava, Tarl Berry, Pieter Verboven, Daniel Onwude, Seraína Schugl, Andreas Buhlmann, Paul Cronje, and Rene M Rossi. Digital twins are coming: Will we need them in supply chains of fresh horticultural produce? Trends in Food Science & Technology, 109:245–258, 2021. DOI: 10.1016/j.tifs.2021.01.025.
- [7] Ernest H Page and Jeffrey M Opper. Observations on the complexity of composable simulation. In Proceedings of the 31st conference on Winter simulation: Simulation--a bridge to the future-Volume 1. 1999: 553–560.
- [8] Richard J Malak and Chris J Paredis. Foundations of validating reusable behavioral models in engineering design problems. In Proceedings of the 2004 Winter Simulation Conference, 2004. IEEE, 2004: 1.
- [9] Robert G Bartholet, David C Brogan, Paul F Reynolds, and Joseph C Carnahan. In search of the philosopher’s stone: Simulation composability versus component-based software design. In Proceedings of the Fall Simulation Interoperability Workshop. 2004.
