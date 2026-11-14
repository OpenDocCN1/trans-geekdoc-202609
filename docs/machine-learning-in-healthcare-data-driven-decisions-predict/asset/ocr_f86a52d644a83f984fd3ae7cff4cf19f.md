structures, weak support for cross-institutional regulatory compliance, and the lack of dynamic identity verification.

Although federated learning and blockchain offer a revolutionary potential for intelligent healthcare, current solutions lack the ability to properly merge efficiency, privacy, and trust into one architecture. The majority ignore the full set of criteria, such as identity sovereignty, compliance automation, and distributed system interoperability, to concentrate on one or two – e.g., privacy or auditability. These restrictions strongly highlight the importance of having a top-down model that combines blockchain, FL, and decentralized identity management like SSI to provide secure, open, and legally compliant exchange of healthcare data at scale.

# 3 System Methodology

The proposed algorithm integrates FL with permissioned blockchain technology to facilitate secure, private, multi-institution collaborative healthcare data analysis. The approach reduces privacy concerns and direct data sharing by allowing each institution to train models locally on their sensitive patient information. While blockchain ensures transparent, unbreachable coordination using consensus and access control via smart contracts, homomorphic encryption and differential privacy methods secure model updates as they are in transit. This dual-mode approach is best suited to today's healthcare environments because it addresses the significant concerns of data confidentiality, integrity, and regulatory alignment. Figure 1 shows the proposed framework.

# 3.1 Federated Learning Framework

# 3.1.1 Problem Formulation

Given healthcare institutions \(H_1, H_2, \dots, H_N\), each holding a private dataset:

\(D_i = \{ (x_{ij}, y_{ij}) \}_{j=1}^{m_i}\) (1)

where \(x_{ij} \in R^d\) are patient features and \(y_{ij}\) are labels, the goal is to learn a global predictive model parameterized by \(\theta \in R^p\) that minimizes the empirical risk without sharing raw data:

\(\min_\theta L(\theta) = \sum_{i=1}^N \frac{m_i}{M} L_i(\theta)\) (2)