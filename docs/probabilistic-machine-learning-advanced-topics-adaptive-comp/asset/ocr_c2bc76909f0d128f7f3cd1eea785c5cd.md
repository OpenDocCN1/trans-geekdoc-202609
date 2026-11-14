We can quantify the degree of transfer as follows, following [LPR17]. If \( R_{ij} \) is the performance on task \( j \) after it was trained on task \( i \), \( R_j^{\text{ind}} \) is the performance on task \( j \) when trained just on \( j \), and there are \( T \) tasks, then the amount of forwards transfer is

\(\text{FWT} = \frac{1}{T} \sum_{j=1}^T R_{j,j} - R_j^{\text{ind}}\) (19.41)

and the amount of backwards transfer is

\(\text{BWT} = \frac{1}{T} \sum_{j=1}^T R_{T,j} - R_{j,j}\) (19.42)

There are many methods that have been devised to overcome the problem of catastrophic forgetting, but we can group them into three main types. The first is **regularization methods**, which add a loss to preserve information that is relevant to old tasks. (For example, online Bayesian inference is of this type, since the posterior for the parameters is derived from the new data and the past prior; see e.g., the **elastic weight consolidation** method discussed in Section 17.5.1, or the **variational continual learning** method discussed in Supplementary Section 10.2). The second is **memory methods**, which rely on some kind of **experience replay** or **rehearsal** of past data (see e.g., [Hen+21]), or some kind of generative model of past data. The third is **architectural methods**, that add capacity to the network whenever a task boundary is encountered, such as a new class label (see e.g., [Rus+16]). Of course, these techniques can be combined. For example, we can create a semi-parametric model, in which we store some past data (exemplars) while also learning parameters online in a Bayesian (regularized) way (see e.g., [Kur+20]). The “right” method depends, as usual, on what inductive bias you want to use, and want your computational budget is in terms of time and memory.

# 19.7.5 Online learning

The problem of **online learning** is similar to continual learning, except the loss metric is different, and we usually assume that learning and evaluation occur at each step. More precisely, we assume the data generating distribution, \( p_t^*(\mathbf{x}, \mathbf{y}) = p(\mathbf{x}|\phi_t)p(\mathbf{y}|\mathbf{x}, w_t) \), evolves over time, as shown in Figure 19.22. At each step \( t \) nature generates a data sample, \( (\mathbf{x}_t, \mathbf{y}_t) \sim p_t^* \). The agent sees \( \mathbf{x}_t \) and is asked to predict \( \mathbf{y}_t \) by computing the posterior predictive distribution

\(\hat{p}_{t|t-1} = p(\mathbf{y}|\mathbf{x}_t, \mathcal{D}_{1:t-1})\) (19.43)

where \( \mathcal{D}_{1:t-1} = \{(\mathbf{x}_s, \mathbf{y}_s) : s = 1 : t-1 \} \) is all past data. It then incurs a loss of

\(\mathcal{L}_t = \ell(\hat{p}_{t|t-1}, \mathbf{y}_t)\) (19.44)

See Figure 19.22. This approach is called **prequential prediction** [DV99; GSR13], and also forms the basis of online conformal prediction [VGS22].

In contrast to the continual learning scenarios studied above, the loss incurred at each step is what matters, rather than loss on a fixed test set. That is, we want to minimize \( \mathcal{L} = \sum_{t=1}^T \mathcal{L}_t \). In the case of log-loss, this is equal to the (conditional) log marginal likelihood of the data, \( \log p(\mathcal{D}_{1:T}) = \)