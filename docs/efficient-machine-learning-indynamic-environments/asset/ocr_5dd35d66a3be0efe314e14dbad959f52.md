where $f_t$ are functions in class $\mathcal{F}$. Suppose data $D$ contains $N$ i.i.d. samples from distribution $\mathcal{D}$ and that the function $g$ has $\epsilon$ margin on data $D$ with probability $\mu$, i.e., $\mathbb{P}_{x \sim \mathcal{D}} [|g(x)| < \epsilon] < \mu$. Further, suppose that the class $\mathcal{C}_T$ has VC dimension $d$. Then, for $T \ge 4G_\infty^2 \ln 2N/\epsilon^2$, with probability at least $1 - \delta$ over the samples, the output $F_T$ of Algorithm 1 satisfies:

$\text{err}(F_T) \le \widehat{\text{err}}(g) + \mathcal{O} \left( \sqrt{\frac{d \ln(N/d) + \ln(1/\delta)}{N}} \right) + \mu.$

Note that the above theorem can easily be adapted to the case of margins and VC dimension of the class $\mathcal{C}_T$ being replaced with the corresponding fat-shattering dimensions. Furthermore, in the setting of stochastic minimax optimization, one can get population bounds directly by thinking of sample losses and gradients as stochastic gradients to the population objective. This is for example the view taken by [118]. We separate the population and sample bounds to simplify the presentation and the proofs, found in Appendix A.2.

# 2.4 Empirical Evaluation

We now evaluate B-DISTIL on both real-world and simulated datasets and over a variety of architecture types. We consider six real-world datasets across three domains—vision, speech, and sensor data—as well as two simulated datasets. This allows us to evaluate our method on five architecture types: fully connected, convolutional, residual, densely connected networks, and recurrent networks.

# 2.4.1 Dataset Information

For experiments with simulated data, we construct two datasets. The first dataset, referred to as $ellipsoid$, is a binary classification dataset. Here the classification labels for each data point $x \in \mathbb{R}^{32}$ are determined by the value of $x^T A x$ for a random positive semidefinite matrix $A$. The second simulated dataset, $cube$, is for multiclass classification with 4 classes. Here labels are determined by distance to the vertices from $\{-1, 1\}^{32}$ in $\mathbb{R}^{32}$, partitioned into 4 classes.

We also use six real-world datasets for our experiments. Our image classification experiments use the $CIFAR$-$10$, $CIFAR$-$100$, $TinyImageNet$, and $ImageNet$ datasets. For time-series classification tasks, we use the $Google$-$13$ speech commands dataset. Here the task is keyword detection: given a one-second buffer of audio, we need to identify if any of 13 predefined keywords have been uttered in this. Finally, we use the daily sports activities ($DSA$) dataset for experiments with sensor data. Here the