
Indeed, the standard objective has the form

```
$\mathcal{L}_{\text{VI}}(\boldsymbol{w}^0, \boldsymbol{\phi}) = \frac{1}{J} \sum_{j=1}^J \left( \sum_{(\boldsymbol{x}, \boldsymbol{y}) \in \mathcal{D}_{all}^j} \left[ \frac{1}{S} \sum_{s=1}^S \log p(\tilde{\boldsymbol{y}}^j | \tilde{\boldsymbol{x}}^j, \boldsymbol{w}_s^j) - D_{KL} \left( q_\phi(\boldsymbol{w}^j | \mathcal{D}_{all}^j, \boldsymbol{w}^0) \| p(\boldsymbol{w}^j | \boldsymbol{w}^0) \right) \right] \right)$
(19.33)
```

where \(\boldsymbol{w}_s^j \sim q_\phi(\boldsymbol{w}^j | \mathcal{D}_{all}^j)\). We see that the standard formulation takes the average of a log, but the meta-learning formulation takes the log of an average. The latter can give provably better predictive accuracy, as pointed out in [MAD20]. Another difference is that the meta-learning formulation optimizes the forward KL, not reverse KL. Finally, in the meta-learning formulation, we do not have the KL penalty term on the parameter posterior.
Below we show how this framework includes several common approaches to meta-learning.

### 19.6.4.2 Neural processes

In the special case that the task-specific inference network computes a point estimate, \(q(\boldsymbol{w}^j | \mathcal{D}^j, \boldsymbol{w}^0) = \delta(\boldsymbol{w}^j - \mathcal{A}_\phi(\mathcal{D}^j, \boldsymbol{w}^0))\), the posterior predictive distribution becomes

```
$q(\tilde{\boldsymbol{y}}^j | \tilde{\boldsymbol{x}}^j, \mathcal{D}^j, \boldsymbol{w}^0) = \int p(\tilde{\boldsymbol{y}}^j | \tilde{\boldsymbol{x}}^j, \boldsymbol{w}^j) q(\boldsymbol{w}^j | \mathcal{D}^j, \boldsymbol{w}^0) d\boldsymbol{w}^j = p(\tilde{\boldsymbol{y}}^j | \tilde{\boldsymbol{x}}^j, \mathcal{A}_\phi(\mathcal{D}^j, \boldsymbol{w}^0), \boldsymbol{w}^0)$
(19.34)
```

where \(\mathcal{A}_\phi(\mathcal{D}^j, \boldsymbol{w}^0)\) is a function that takes in a set, and returns some parameters. We can evaluate this predictive distribution empirically, and directly optimize it (wrt \(\boldsymbol{\phi}\) and \(\boldsymbol{w}^0\)) using standard supervised maximum likelihood methods. This approach is called a **neural process** [Gar+18e; Gar+18d; Dub20; Jha+22].

### 19.6.4.3 Gradient-based meta-learning (MAML)

In gradient-based meta-learning, we define the task specific inference procedure as follows:

```
$\hat{\boldsymbol{w}}^j = \mathcal{A}(\mathcal{D}^j, \boldsymbol{w}^0) = \boldsymbol{w}^0 + \eta \nabla_\boldsymbol{w} \log \sum_{n=1}^{N^j} p(\boldsymbol{y}_n^j | \boldsymbol{x}_n^j, \boldsymbol{w})|_{_\boldsymbol{w}^0}$
(19.35)
```

That is, we set the task specific parameters to be shared parameters \(\boldsymbol{w}^0\), modified by one step along the gradient of the log conditional likelihood. This approach is called **model-agnostic meta-learning** or **MAML** [FAL17]. It is also possible to take multiple gradient steps, by feeding the gradient into an RNN [RL17].

### 19.6.4.4 Metric-based few-shot learning (prototypical networks)

Now suppose \(\boldsymbol{w}^0\) correspond to the parameters of a shared neural feature extractor, \(h_{\boldsymbol{w}^0}(\boldsymbol{x})\), and the task specific parameters are the weights and biases of the last linear layer of a classifier, \(\boldsymbol{w}^j = \{\boldsymbol{w}_c^j, b_c^j\}_{c=1}^C\). Let us compute the average of the feature vectors for each class in each task's training set:

```
$\boldsymbol{\mu}_c^j = \frac{1}{|\mathcal{D}_c^j|} \sum_{\boldsymbol{x}_n^i \in \mathcal{D}_c^j} h_{\boldsymbol{w}^0}(\boldsymbol{x}_n^c)$
(19.36)
```

Now define the task specific inference procedure as follows. We first compute the vector containing the centroid and norm for each class:

\(\hat{\mathbf{w}}^j = \mathcal{A}(\mathcal{D}^j, \mathbf{w}^0) = [\boldsymbol{\mu}_c^j, -\frac{1}{2}||\boldsymbol{\mu}_c^j||^2]_{c=1}^C\)

The predictive distribution becomes

\(q(\tilde{y}^j = c | \tilde{\mathbf{x}}^j, \mathcal{D}^j, \mathbf{w}^0) \propto \exp\left(-d(h_{\mathbf{w}^0}(\tilde{\mathbf{x}}), \boldsymbol{\mu}_c^j)\right) = \exp\left( h_{\mathbf{w}^0}(\tilde{\mathbf{x}})^\mathsf{T} \boldsymbol{\mu}_c^j - \frac{1}{2}||\boldsymbol{\mu}_c^j||^2 \right)\)

where \(d(\boldsymbol{\unknown}, \mathbf{v})\) is the Euclidean distance. This is equivalent to the technique known as **prototypical networks** [SSZ17].

## 19.7 Continual learning

In this section, we discuss **continual learning** (see e.g., [Had+20; Del+21; Qu+21; LCR21; Mai+22; Wan+23]), also called **life-long learning** (see e.g., [Thr98; CL18]), in which the system learns from a sequence of different distributions, \(p_1, p_2, \dots\). In particular, at each time step \(t\), the model receives a batch of labeled data,

\(\mathcal{D}_t = \{(\mathbf{x}_n, \mathbf{y}_n) \sim p_t(\mathbf{x}, \mathbf{y}) : n = 1 : N_t\}\)

where \(p_t(\mathbf{x}, \mathbf{y})\) is the unknown data distribution, which we represent as \(p_t(\mathbf{x}, \mathbf{y}) = p_t(\mathbf{x})p(\mathbf{y}|f_t(\mathbf{x}))\), where \(f_t : \mathcal{X}_t \rightarrow \mathcal{Y}_t\) is the unknown prediction function. Each distribution defines a different **task**. The learner is then expected to update its belief state about the underlying distribution, and to use its beliefs to make predictions on an independent test set,

\(\mathcal{D}_t^{\text{test}} = \{(\mathbf{x}_n, \mathbf{y}_n) \sim p_t^{\text{test}}(\mathbf{x}, \mathbf{y}) : n = 1 : N_t^{\text{test}}\}\)

Depending on how we assume \(p_t(\boldsymbol{x}, \boldsymbol{y})\) evolve over time, and how the test set is defined, we can create a variety of different CL scenarios. In particular, if the test distribution at time \(t\) contains samples from all the tasks up to (and including) time \(t\), then we require that the model not “forget” past data, which can be tricky for many methods, as discussed in Section 19.7.4. By contrast, if the test distribution at time \(t\) is same as the current distribution, as in online learning (Section 19.7.5), then we just require that the learner adapt to changes, but it need not remember the past. (Note that we focus on supervised problems, but non-stationarity also arises in reinforcement learning; in particular, the input distribution changes due to the agent’s changing policy, and the desired prediction function changes due to the value function for that policy being updated.)

### 19.7.1 Domain drift

The problem of **domain drift** refers to the setting in which \(p_t(\boldsymbol{x})\) changes over time (i.e., covariate shift), but the functional mapping \(f_t : \mathcal{X} \rightarrow \mathcal{Y}\) is constant. For example, the vision system of a self driving car may have to classify cars vs pedestrians under shifting lighting conditions (see e.g., [Sun+22]).

To evaluate such a model, we assume \(f_t^{\text{test}} = f_t\) and define \(p_t^{\text{test}}(\boldsymbol{x})\) to be the current input distribution \(p_t\) (e.g., if it is currently night time, we want the detector to work well on dark images).

![](img/ca72c1626f4850f058a9edc138c1ac73_782_0.png)

Figure 19.16: An illustration of domain drift.

![](img/ca72c1626f4850f058a9edc138c1ac73_782_1.png)

Figure 19.17: An illustration of concept drift.

Alternatively we can define \( p_t^{\text{test}}(\boldsymbol{x}) \) to be the union of all the input distributions seen so far, \( p_t^{\text{test}} = \cup_{s=1}^T p_s \) (e.g., we want the detector to work well on dark and light images). This latter assumption is illustrated in Figure 19.16.

### 19.7.2 Concept drift

The problem of **concept drift** refers to the setting where the functional mapping \( f_t : \mathcal{X} \rightarrow \mathcal{Y} \) changes over time, but the input distribution \( p_t(\boldsymbol{x}) \) is constant [WK96]. For example, we can imagine a setting in which people engage in certain behaviors, and at step \( t \) some of these are classified as illegal, and at step \( t' > t \), the definition of what is legal changes, and hence the decision boundary changes. This is illustrated in Figure 19.17.

As another example, we might initially be faced with a sort-by-color task, where red objects go on the left and blue objects on the right, and then a sort-by-shape task, where square objects go on the
