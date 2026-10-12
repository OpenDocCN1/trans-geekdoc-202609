
Such ML-based systems collect, aggregate, and analyse massive amounts of data on a single server, making them vulnerable to catastrophic data breaches caused by a single point of failure. It is challenging to provide meaningful analysis of ML algorithms due to the black box-like nature of their execution and decision-making [[34](#ch5.xhtml#ref5_34)]. As a result, the standards of GDPR’s transparency, impartiality, and automated decision-making are challenging for most ML-based systems to meet.

In addition, ML-based systems don’t always realistically meet the constraints of purpose limiting and data reduction. Most machine learning algorithms are extremely dependent on the quality and amount of the data they are given, thus researchers generally aim to collect as much of it as possible [[35](#ch5.xhtml#ref5_35)]. So, before running such ML algorithms, it is difficult to (1) ascertain the motivations for data collection and (2) ascertain whether data is appropriate, constrained, and relevant exclusively to the declared aims. These limitations put artificial limits on the potential of machine learning (ML) services and applications.

Finally, machine learning algorithms are mostly created to maximise efficiency, while privacy protection methods continue to be limited to basic caveats. To fulfill the stringent necessities of the GDPR, machine learning algorithms will need to undergo a fundamental redesign at the algorithm level. To achieve such a radical change would require enormous, maybe unachievable, technological accuracy and financial backing. It appears that many service providers are weighing the costs and benefits of prioritising efficiency above privacy-guarantee, with the realisation that doing so may render them unable to continue providing their current services.

## 3. Federated Learning: An Approach to Distributed Collaborative Learning

Due to the difficulties in adhering to stringent data protection requirements on the massive gathering and processing of personal data, the old cloudcentric ML techniques are no longer suitable in many situations. Enduser devices (such as smartphones, tablets, and wearables) have growing computational power and Internet access, and so create the vast majority of personal data [[36](#ch5.xhtml#ref5_36)]. Decentralized AI has arisen to move intelligence from the cloud to the edge using mobile edge computing and artificial intelligence/machine learning methods in reaction to the proliferation of such personal gadgets and the associated increase in privacy issues.

Since federated learning enables users to maintain their original personal data on their devices throughout collaborative training of an ML model, it may help mitigate some of the hazards associated with cloudbased ML. It is an interdisciplinary approach to training a centralized ML model using decentralized data, with applications in machine learning, distributed computing, data privacy, and security. When combining and updating models, only training parameters are traded. When it comes to training data, traditionally distributed learning assumes that each compute node’s local training datasets are IID and are around the same size. This is not the case with FL. Since FL can accommodate non-IID data sets whose sizes could vary by several orders of magnitude, it is an advance in distributed learning. These unrelated data sets are scattered over a wide variety of mobile devices with varying degrees of network availability and data transmission rates.

### 3.1 Model Training in Federated Learning

With a model constructed as the minimization of specific objective functions over a training dataset, FL is mainly effective for parameter estimation in ML models. One such statement of the purpose of minimization is:

(2)

```
\min\limits_{w \in {\mathbb{R}}^{d}}f(w) = \frac{1}{n}\sum\limits_{i = 1}^{m}f_{i}(w)
```

whereas the input-output pairs (`xi`, `yi`) used for training are of the type `x[i]` ∈ R`^d` and `y[i]` ∈ R, ∀`i` ∈ {1, 2*, ., n*}. Dataset sample size (`n`), parameter vector `w` ∈ R`^d` and loss function (`fi (w)`) are denoted in Equation 2. This idea applies to a broad variety of ANN-related tasks, including linear and logistic regressions, support vector machines, and more. It even extends to sophisticated non-convex challenges in ANN, such as Deep Learning. Minimizing the sum of the losses as a function of the model parameters may be easily computed using the gradient descent technique using backpropagation as an optimization strategy.

These kinds of processes do a high number of quick iterations on a huge dataset that has been uniformly partitioned in data servers, as is done in conventional ML methods. Such algorithms necessitate extremely fast and low-latency links to the training data. The conventional ML approaches to solving this optimisation problem do not apply in FL settings since these conditions are not met. FL training data, in contrast to the balanced and IID data utilised by conventional methods, is dispersed over millions of separate mobile devices connected by substantially higher-latency, lowerthroughput networks. As an added caveat, data from individual devices and access to computers are only made available on an as-needed basis throughout the training process. Optimisation algorithms will need to be successfully adapted to and implemented in federated environments before FL can be put into practise.

### 3.2 Federated Optimization

Optimization algorithms that work well in federated environments where training data is substantially and unevenly dispersed among local nodes are a cornerstone of FL. The following formula describes the dispersed parameters for the federated optimization. Let `K` indicates the total number of nodes in the cluster, `P[k]` denote the collection of data points held by node `k` ∈ {1, 2*, .*, K}, and `n[k]` = |`P[k]`| denote the total no of data points held by node `k`. Given that each local node stores its own unique set of personal information, we may deduce that, ℙ[`k`] ∩ ℙ[`l`] = ⌀ if `k` ≠ `l` and *Σ*[`k` = 1]^(`K`)`n`[`k`] = `n`.  For minimization, the following defines the distributed problem formulation:

(3)

```
\min\limits_{w \in {\mathbb{R}}^{d}}f(w) = \frac{n_{k}}{n}\sum\limits_{k = 1}^{K}F_{k}(w)
```

(4)

```
F_{k}(w) = \frac{1}{n_{k}}\text{Σ}_{i \in {\mathbb{P}}_{k}}f_{i}(w)
```

Due to the limited communication capabilities of the local nodes in this federated system, it is essential to decrease the number of iterations utilised by optimization techniques. The SVRG and DAN algorithms for distributed optimization were combined by the authors [[25](#ch5.xhtml#ref5_25)] to create a unique distributed gradient descent (Federated SVRG). The FSVRG updates the parameters at each node after each cycle by computing gradients from `P k` data at each local node `k`, and then averaging those weighted values across all `k` local nodes. The next step is to evaluate the system’s ability to forecast whether a post will garner comments on Google+ public postings using a sample of around 10,000 individuals as local nodes. The optimal solution is reached by the FSVRG in 30 fewer iterations than by the original gradient descent approach.
