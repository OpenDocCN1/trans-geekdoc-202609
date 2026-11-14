where $\mathcal{B}_{b,c}$ is the $b$'th bin for class $c$, and $w_c \in [0, 1]$ denotes the importance of class $c$. (We can set $w_c = 1/C$ if all classes are equally important.) In [Nix+19], they call this metric **static calibration error**; they show that certain methods that have good ECE may have poor MCE. Other multi-class calibration metrics are discussed in [WLZ19].

# 14.2.2.2 Improving calibration

In principle, training a classifier so it optimizes a proper scoring rule (such as NLL) should automatically result in a well-calibrated classifier. In practice, however, unbalanced datasets can result in poorly calibrated predictions. Below we discuss various ways for improving the calibration of probabilistic classifiers, following [Guo+17].

# 14.2.2.3 Platt scaling

Let $z$ be the log-odds, or logit, and $p = \sigma(z)$, produced by a probabilistic binary classifier. We wish to convert this to a more calibrated value $q$. The simplest way to do this is known as **Platt scaling**, and was proposed in [Pla00]. The idea is to compute $q = \sigma(az+b)$, where $a$ and $b$ are estimated via maximum likelihood on a validation set.

In the multiclass case, we can extend Platt scaling by using matrix scaling: $\mathbf{q} = \text{softmax}(\mathbf{W}z + \mathbf{b})$, where we estimate $\mathbf{W}$ and $\mathbf{b}$ via maximum likelihood on a validation set. Since $\mathbf{W}$ has $K \times K$ parameters, where $K$ is the number of classes, this method can easily overfit, so in practice we restrict $\mathbf{W}$ to be diagonal.

# 14.2.2.4 Nonparametric (histogram) methods

Platt scaling makes a strong assumption about how the shape of the calibration curve. A more flexible, nonparametric, method is to partion the predicted probabilities into bins, $p_m$, and to estimate an empirical probability $q_m$ for each such bin; we then replace $p_m$ with $q_m$; this is known as **histogram binning** [ZE01a]. We can regularize this method by requiring that $q = f(p)$ be a piecewise constant, monotonically non-decreasing function; this is known as **isotonic regression** [ZE01a]. An alternative approach, known as the **scaling-binning calibrator**, is to apply a scaling method (such as Platt scaling), and then to apply histogram binning to that. This has the advantage of using the average of the scaled probabilities in each bin instead of the average of the observed binary labels (see Figure 14.2). In [KLM19], they prove that this results in better calibration, due to the lower variance of the estimator.

In the multiclass case, $\mathbf{z}$ is the vector of logits, and $\mathbf{p} = \text{softmax}(\mathbf{z})$ is the vector of probabilities. We wish to convert this to a better calibrated version, $\mathbf{q}$. [ZE01b] propose to extend histogram binning and isotonic regression to this case by applying the above binary method to each of the $K$ one-vs-rest problems, where $K$ is the number of classes. However, this requires $K$ separate calibration models, and results in an unnormalized probability distribution.

# 14.2.2.5 Temperature scaling

In [Guo+17], they noticed empirically that the diagonal version of Platt scaling, when applied to a variety of DNNs, often ended learning a vector of the form $\mathbf{w} = (c, c, \dots, c)$, for some constant $c$. This suggests a simpler form of scaling, which they call **temperature scaling**: $\mathbf{q} = \text{softmax}(\mathbf{z}/T)$,