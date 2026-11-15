that incorporates the push-sum consensus protocol, which is outlined as follows for each node \( i \) in the set \( \mathcal{V} \):

![](bbox=[0.35, 0.17, 0.55, 0.29])

where \( C_t \) satisfies Assumption 6.1 and \( v_t^i \) is an auxiliary variable. The aforementioned algorithm has been validated as fitting for dynamic directed networks. Distinguishing itself from the push-sum based approach in [40], the authors of [29] devised a fresh approach from a distinct angle, demonstrating its efficacy in mitigating the imbalance inherent in time-varying directed networks. Nevertheless, this innovative strategy is not integrated within the realm of decentralized dual averaging algorithms. Furthermore, neither of the algorithms discussed in [40] and [29] take into account the vital aspect of node privacy protection within the network, which is paramount, particularly in scenarios where data is continuously exchanged. With this in mind, we proceed to present our proposed decentralized algorithm, termed Zeroth-Order Dual Averaging (ZO-DDA).

# 6.3.2 The proposed decentralized algorithm (ZO-DDA)

Given the unavailability of gradient information in the bandit framework, we embark on designing a zeroth-order algorithm. To advance the development of our proposed ZO-DDA, we can define a smoothed approximation of the local loss function \( f_t^i(x) \) for each node \( i \) belonging to the set \( \mathcal{V} \), as outlined below:

![](bbox=[0.28, 0.635, 0.78, 0.655])

where the parameter \( \beta \) is randomly and uniformly sampled within a unit sphere, while \( \delta \in (0, d\bar{\xi}] \) is an exploration parameter, and \( \bar{\xi} \in (0, 1) \) serves as a contraction coefficient. Contrasting with the Gaussian distribution [32], which possesses the potential to yield unbounded values for \( \beta \), the uniform distribution is employed to derive \( \beta \) in Eq. (6.6). Given that perturbations may displace points outside the feasible set \( \Omega \), the function \( \hat{f} \) is defined on the contracted set \( (1 - \bar{\xi})\Omega \). The validity of these perturbations is assured (as per Observation 2 in [52]), ensuring that for any \( x \) within \( (1 - \bar{\xi})\Omega \), the perturbed point \( x + \delta \beta_t^i \) remains within \( \Omega \).

Within the framework of ZO-DDA, we refrain from directly computing the sub-gradient of the function and instead leverage a local zeroth-order oracle, which is inspired by the two-point sampling gradient estimator approach outlined in [34]:

![](bbox=[0.27, 0.885, 0.78, 0.915])