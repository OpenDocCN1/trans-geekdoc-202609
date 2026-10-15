
**Keywords:** Binomial probability distribution, Ballot stuff, Bad mouth, Collusion, Direct reputation, Euclidean Distance, Hosts, Indirect reputation, Mobile agents, P2P, Single-linkage clustering.

## 6.1. INTRODUCTION

P2P networks consist of some important properties that attracted many researchers to talk about trust and reputation issues. These issues help agents to find the trustworthiness of peers (hosts) before the actual transaction. Since each peer plays the role of both server and client, P2P networks do not require any central control [1]. Peers are also called hosts, where the actual execution of the agent takes place. Reputation-based systems collect facts about the properties of hosts, analyze them, aggregate facts about them, and finally disseminate these aggregated facts to all other hosts in the network [2]. Our earlier paper discussed how these systems could be used in mobile agent technology to secure mobile agents [3]. To ensure security, trust, and reputation-based systems are built where mobile agent finds the trustworthiness of the host’s behavior before performing an actual transaction with them. In the earlier paper, the MRep model is proposed to determine the trustworthiness of the host with which mobile agent wants to pursue transaction [4]. Since all hosts are autonomous in nature, they can check each other’s trustworthiness using social mechanisms of reputation. A reputation-based system collects facts about the properties of the host. It analyzes and aggregates the facts about it and finally disseminates these aggregated facts to all other hosts in the network [5]. In an e-commerce scenario, an agent is dispatched by the user in the network for selling or buying (transactional purpose) products. For this purpose, it performs possible negotiations with sellers (hosts). Since an agent has no past behavioral information, it carries a lot of suspicion and mistrust on hosts. An entity that trusts are called a trustor and an entity on which the trustor trusts is called the trustee. Our proposed MRep model consists of a trustor (agent) that collects feedback from recommending hosts (recommenders) to derive the reputation of the DH. The model considers recommendations from only those hosts that possess past transaction history with the DH. Recommendation reputation (rating) helps the mobile agent to predict the trustworthiness of the DH. Unfortunately, the recommendations given by recommenders or raters collaborate to give false ratings to make DH's reputation low or high in the market. These recommenders collude to act as if they are one single unit. Such recommenders are called colluders. These colluders keep the information about each host’s transaction and recommendation history. Ballot stuff collusion occurs when recommenders collude to give a fake positive recommendation for non-reputable DH while bad-mouth collusion occurs when recommenders give fake negative recommendations for reputable DH [6]. Bad-mouth colluders not only give

determine the increase and decrease in the probability of reputation error with a varying number of colluders and estimate the error in the final reputation value of DH under ballot stuff and bad mouth attacks. Later, similarity filtering (SF) is compared with other filterings under varying percentages of collusion. MRep calculates FR of DH. MRep calculates the dynamic reputation of DH before pursuing the transaction. DR of DH is obtained from past transaction experience of SH and indirect reputation(IDR) is obtained from recommenders divided into different recommender groups according to their distance from SH. Our earlier papers discuss in detail the methodology to calculate FR via direct and indirect reputation [11]

## 6.3. RELATED WORKS

Reputation systems that lack mechanisms to provide data authentication and integrity are vulnerable to collusion attacks because we are not able to differentiate between fabricated and legitimate feedback. Several researchers have addressed this problem. Liu et al [12] reported that the FR is always misled by inserting unfair ratings in regular ratings. [13] propose a scheme to detect collaborative unfair raters (recommending hosts) based on the similarity in their rating behavior schemes. These schemes identify time intervals in which unfair ratings are highly suspected. Selcuk et al [14] suggest keeping records of recommender’s trustworthiness which is later updated only in case transactions with such host becomes successful. Rahman and Hailes [15] propose to calculate the semantic distance between the recommender’s recommendation and the trustor’s (agent’s) own perception towards the recommender for the outcome of its transaction. Huynh et al [16] suggest calculating credibility ratings of each recommender’s recommendation after a transaction is performed between agent and host. These credibility ratings assign weight to recommenders before obtaining future recommendations from them. Dillon et al [17] estimated the recommender’s reputation strength by finding the difference between its given recommendation and the trustor’s evaluation of the transaction with the trustee (host). Dellarocas [18] calculated feedback reputation based on the number of consistent ratings that the trustor gave for the trustee. Allahbakhsh et al [19] propose a model that uses a mining technique to detect the collusion groups and sub-groups. Ashri et al [20] advise incorporating more detailed relationships between hosts and proposed some identification mechanisms for characterization of these relationships. Such relationships change dynamically in e-marketplaces.

## 6.4. MREP MODEL

A reputation system for securing mobile agents helps the agent to compute the reputation of a destination host. The destination host (DH) is the host with which the agent wishes to pursue a transaction in the future. In MRep, the agent combines direct trust (DT) obtained from the pre-trusted host (assumed) called source host. The fixed hierarchical network of MRep is shown in Fig. (6.1).

![](img/be45bf301a3c0ebefb162571e2625fab_147_0.png)

Fig. (6.1). MRep hierarchical view.

The source host(SH) is the host with which the agent had already performed the transaction and declared it pre-trusted. Indirect trust(IT) is obtained from directly or indirectly connected hosts with SH. These hosts are responsible for giving indirect trust (IDT) and are called recommenders. The model divides recommenders into four recommender communities or groups depending on their distance from SH. These four recommender groups are
- Relatives (R): hosts possessing past transactional history with DH and are at one hop distance from SH.
- Friends(F): Host possessing past transactional history with DH and is at a two-hop distance from SH.
- Neighbors(N): hosts possessing past transactional history with DH and is at three-hop distance from SH.
- Strangers (S): Host possessing past transactional history with DH and is at four or above hop distance from SH.
The fixed hierarchical network of MRep is shown in Fig. (6.1).

MRep assists MA to do the prior computation of DH reputation. DR score (DRscore) is used to determine the transactional behavior of the host on each date. Transaction Score (Tscore) is the ratio of the number of successful to the total number of transactions given by Equation 6.1. Transaction Evaluation (TE) is the product of T-score on each date with recency in the time given by Equation 6.2. TE is weighted by a time decay function represented as e^{-dt}, where dt is the difference between the current date and previous date of transaction by DH. Time decay function (e ^-dt) establishes the principle that states the more recent the transaction higher the value of DRscore. The formula to calculate DRscore is given in equation 6. Agent calculates confidence by estimating divergence (Div) in total TE and DRscore values. Div is given by equation 6.4. Confidence achieved by the agent is given in equation 6.5. Finally, the DR of DH is the product of confidence with the total DRscore value given by equation 6.6.

```
Tscore = s/n  (6.1)
TE = e^-dt * Tscore  (6.2)
DRscore = TE / Σ e^-dt  (6.3)
Div = | Σ TE - Σ DRscore |  (6.4)
Conf = k1 * k2 * (1-Div)  (6.5)
```

k1 = 1 if (t_c - t0) * ψ < N, else k1 = N / ((t_c - t0) * ψ)

k2 = 1 if (t_c - t0) * φ < S, else k2 = S / ((t_c - t0) * φ)

t_c: current date of transaction with DH

t_p: previous dates of transaction with DH.

N: Total number of transaction, S: Total number of successful transaction

t0: date of first transaction

ψ: Threshold for number of transactions per day

φ: Threshold for successful transactions per day

Thresholds ψ, φ can be set as per the requirements of the user.

```
DR = Conf * Σ DRscore  (6.6)
```

Fig. (6.2) shows the logical community-level view of MRep where α, β, γ and δ signifies weight to R, F, N and S groups respectively.
