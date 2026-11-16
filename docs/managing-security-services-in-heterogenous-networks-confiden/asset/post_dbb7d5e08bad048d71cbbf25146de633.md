

- 25. Bara’a, A. Attea, “Energy-Aware Evolutionary Routing Protocol for Dynamic Clustering of Wireless Sensor Networks.” Swarm and Evolutionary Computation, vol. 1, no. 4, pp. 195–203, 2011.

- 26. Villas, L. Á., A. Boukerche, H. S. Ramos, H. A. B. F. de Oliveira, R. B. de Araujo; A. A. F. Loureiro, “DRINA: A Lightweight and Reliable Routing Approach for In-Network Aggregation in Wireless Sensor Networks.” IEEE Trans. Computers, vol. 62, no. 4, pp. 676–689, 2013.

- 27. Nakamura, E. F., H. A. B. F. de Oliveira, L. F. Pontello, and A. A. F. Loureiro, “On Demand Role Assignment for Event Detection in Sensor Networks.” 11th Symp., Computers and Comm. (ISCC ’06), Sardinia, Italy, pp. 941–947, 2006.

- 28. Heinzelman, Wendi Rabiner, Anantha Chandrakasan, and Hari Balakrishnan. “Energy-Efficient Communication Protocol for Wireless Microsensor Networks.” Annual Hawaii International Conference, System Sciences, pp. 10, 2010.

- 29. Younis, O., and S. Fahmy, “HEED: A Hybrid, Energy-efficient, Distributed Clustering Approach for Ad Hoc Sensor Networks.” IEEE Trans. Mobile Computing, vol. 3, no. 4, pp. 366–379, 2004.

- 30. Wang, Chu-Fu, Suh-Chien Hang, “Efficient Algorithm for Prolonging Network Lifetime of Wireless Sensor Network.” In 2008 Eighth International Conference on Intelligent Systems Design and Applications, vol. 2, pp. 196–201, 2008.

- 31. Mathapati, Basavaraj S., Siddarama R. Patil, V. D. Mytri, “A Cluster Based Energy Efficient Reliable Routing Protocol for Wireless Sensor Networks.” Proc. 1st International Conference, ET2ECN, pp. 1–6, 2012.

- 32. Kuila, Pratyay, Prasanta K. Jana, “Energy Efficient Clustering And Routing Algorithms For Wireless Sensor Networks: Particle Swarm Optimization Approach.” Engineering Applications of Artificial Intelligence, vol. 33, pp. 127–140, 2014.

## ENSURING SECURITY THROUGH TRUST IN MOBILE AD-HOC NETWORKS USING SOFT COMPUTING METHODS

NAGESWARARAO SIRISALA AND C. SHOBA BINDU

Associate Professor, CSE Dept, Vardhaman College of Engg., Hyderabad, India

Professor, CSE Dept, JNTUACE, Anantapur, India

## Contents

- 3.1 Introduction 40
- 3.2 Trust in Mobile Ad-hoc Networks 41
- 3.2.1 Trust Definitions 41
- 3.2.2 Trust Properties in MANETs 41
- 3.2.3 Trust Propagation 43
- 3.2.4 Trust Aggregation 43
- 3.2.5 Trust Prediction 43
- 3.2.6 Trust Computation 43
- 3.2.6.1 Direct Trust Computation 43
- 3.2.6.2 Recommendation-Based Trust 44
- 3.2.6.3 Hybrid Method 45
- 3.3 Trust Distortion Attacks: A Taxonomy 45
- 3.3.1 Trust Attacks in MANETs 45
- 3.3.1.1 Badmouthing Attacks 45
- 3.3.1.2 Double-Face Attacks 46
- 3.3.2 Trust-Distortion Resistant Trust Management Frameworks 47
- 3.3.2.1 TMFs Resistant to Double-Face Attacks 47
- 3.3.2.2 TMFs Resistant to BadMouthing Attacks 47
- 3.4 Trust Management Using Soft Computing Methods in MANETs
- 3.4.1 Trust Computation Using Fuzzy Logic
- 3.4.1.1 Computation of QoS Parameters
- 3.4.1.2 Fuzzy Inference System to Evaluate Node Trust Values
- 3.4.2 Trust Routing Using Fuzzy Petri-Nets in MANETs
- 3.4.2.1 Weighted Rules of DFPN
- 3.4.2.2 MANET Routing Using DFPN
- 3.4.3 Dempster-Shafer Theory
- 3.4.3.1 Dempster's Rule for Combinations
- 3.4.3.2 DST Example
- 3.4.4 Trust Matrix Operations
- 3.5 Conclusion
- References

## 3.1 Introduction

In mobile ad-hoc networks (MANETs), a node has to interact with unknown nodes in establishing the network. The applications are run successfully, if all the nodes are cooperative. Hence, the trust computation of each node is certainly an advantage in running applications effectively by eliminating untrustworthy nodes. Due to the severe resource constraints (like energy, computational power, bandwidth, and time) and dynamics (like topological changes, mobility, and channel conditions) of the network, creation of a secure environment by implementing complex encryption algorithms (hard security) is not a trivial task [8]. Alternatively, researchers have concentrated on soft security (trust) methods to separate malicious nodes by monitoring their activities.

In MANET, usually a node switches to selfish mode when it is short of resources, and it may not cooperate in running neighbor applications. Due to malicious behavior, a node can weaken the network performance by dropping or tampering with packets. In this regard, authors [1,2] suggest taking into account a node’s ability (in terms of resources) and attitude in its trust estimation. Through the node trust computation, the quality of service (QoS) of the applications in the network can be improved [10,12].

In this chapter in Section 2, trust definitions, properties, prediction, aggregation, propagation, and computation methods are discussed in the MANET context. Different trust attacks in MANETs and their countermeasures are discussed in Section 3. In Section 4, soft computing methods in trust estimation are discussed like fuzzy logic, fuzzy Petri nets, Bayesian conditional probability, Dempster-Shafer Theory (DST), and trust matrix operations.

## 3.2 Trust in Mobile Ad-hoc Networks

Trust is platform independent, and the principles of trust are even applicable to the communication network. In current research, trust is being considered as one of the design considerations in a networking protocol stack [4]. In the distributed environment of MANETs, maintenance of trust relations with other nodes can increase the network performance like scalability, dependability, and reliability. In this section, these concepts are discussed in the MANET context.

### 3.2.1 Trust Definitions

The term “trust” is defined in multiple ways, but the widely accepted two definitions are discussed here.

In [14], the trust of a particular node is a subjective assessment by an agent/other peer node on the reliability and accuracy of information received from or traversing through that node in a given context.

In [13], trust reflects the belief or confidence or expectations in terms of the honesty, integrity, ability, availability, and quality of service of a target node’s future activity/behavior. It also reflects the mutual relationships where a given node behaves in a trustworthy manner and maintains reliable communications only with nodes that are highly trusted by the given node.

### 3.2.2 Trust Properties in MANETs

In Figure 3.1, the trust properties are described from a MANET perspective, where the trust is shown as the combination of properties like asymmetry, subjectivity, context dependency, dynamicity, and transitivity.

![](img/058011bdc8fc3d3d77199bfcbf721be0_48_0.png)

Figure 3.1 Trust Properties in MANETs.

- **Trust is dynamic:** In MANETs, node behavior is not static; it changes based on conditions over time. Hence, the node’s trust is a variable factor. In [15], Adams et al. recommended a random variable to capture the trust changes instead of a discrete variable.

- **Trust is subjective:** In a network, a node can have different opinions on other nodes at different time intervals, where these trust changes are influenced by the network topology conditions.

- **Trust is asymmetric:** Usually ad-hoc networks are formed with the heterogeneous nodes, where nodes have different capabilities like computational power, memory, battery power, etc. Hence, the trust relation between two nodes is not symmetric. Generally, a node with good resources has good trust with its neighbors.

- **Trust is transitive:** A node can assess the trustworthiness of a target node through intermediate nodes using a trust transitivity rule. Let us consider three nodes (n<sub>i</sub>, n<sub>j</sub>, n<sub>k</sub>), where n<sub>j</sub> is the neighbor of both n<sub>i</sub> and n<sub>k</sub>, but n<sub>i</sub> and n<sub>k</sub> are not neighbors. Node n<sub>i</sub> takes the trust recommendation of n<sub>j</sub> to estimate the trustworthiness of n<sub>k</sub>.

- **Trust is context dependent:** In ad-hoc networks, trust is context dependent, i.e. a node has different trust opinions of the same node in different contexts. A node can trust another node in an energy context but cannot trust in a bandwidth context, for example.

