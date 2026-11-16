
![](img/c73db5a1f734ebb7c0655f19e5bc9daa_183_0.png)

Figure 31.17: Signature of X causing Y. Left: If we try to predict Y from X, the residual error (noise term, shown by vertical arrows) is independent of X. Right: If we try to predict X from Y, the residual error is not constant. From Figure 8.8 of [Var21]. Used with kind permission of Kush Varshney.

In the case of two variables, we have Y = f(X) + U. If X and U are both Gaussian, and f is linear, the system defines a jointly Gaussian distribution p(X, Y), as we discussed in ??. This is symmetric, and prevents us distinguishing X → Y from Y → X. However, if we let f be nonlinear, and/or let X or U be non-Gaussian, we can distinguish X → Y from Y → X, as we discuss below.

### 31.4.1.3 Nonlinear additive noise models

Suppose p_{Y|X} is an additive noise model (possibly Gaussian noise) where f is a nonlinear function. In this case, we will not, in general, be able to create an ANM for p_{X|Y}. Thus we can determine whether X → Y or vice versa as follows: we fit a (nonlinear) regression model for X → Y, and then check if the residual error Y - \(\hat{f}_Y(X)\) is independent of X; we then repeat the procedure swapping the roles of X and Y. The theory [PJS17] says that the independence test will only pass for the causal direction. See Figure 31.17 for an illustration.

### 31.4.1.4 Linear models with non-Gaussian noise

If the function mapping from X to Y is linear, we cannot tell if X → Y or Y → X if we assume Gaussian noise. This is apparent from the symmetry of Figure 31.17 in the linear case. However, by combining linear models with non-Gaussian noise, we can recover identifiability.

For example, consider the ICA model from **??**. This is a simple linear model of the form y = Ax, where p(x) has a non-Gaussian distribution, and p(y|x) is a degenerate distribution, since we assume the observation model is deterministic (noise-free). In the ICA case, we can uniquely identify the parameters A and the corresponding latent source x. This lets us distinguish the X → Y model from the Y → X model. (The intuition behind this method is that linear combinations of random variables tend towards a Gaussian distribution (by the central limit theorem), so if X → Y, then p(Y) will “look more Gaussian” than p(X).)

Another setting in which we can distinguish the direction of the arrow is when we have non-Gaussian observation noise, i.e., y = Ax + U_Y, where U_Y is non-Gaussian. This is an example of a “linear non-Gaussian acyclic model” (LiNGAM) [Shi+06]. The non-Gaussian additive noise results in the induced distributions p(X, Y) being different depending on whether X → Y or Y → X.

### 31.4.1.5 Information-geometric causal inference

An alternative approach, known as information-geometric causal inference, or IGCI, was proposed in [Dan+10; Jan+12]. In this method, we assume f is a deterministic strictly monotonic function on [0, 1], with f(0) = 0 and f(1) = 1, and there is no observation noise, so Y = f(X). If X has the distribution p(X), then the shape of the induced distribution p(Y) will depend on the form of the function f, as illustrated in Figure 31.18. Intuitively, the peaks of p(Y) will occur in regions where f has small slope, and thus f^{-1} has

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_184_0.png)

Figure 31.18: Illustration of information-geometric causal inference for \( Y = f(X) \). The density of the effect \( p(Y) \) tends to be high in regions where \( f \) is flat (and hence \( f^{-1} \) is steep). From Figure 4 of [Jan+12].

large slope. Thus \( p_Y(Y) \) and \( f^{-1}(Y) \) will depend on each other, whereas \( p_X(X) \) and \( f(X) \) do not (since we assume the distribution of causes is independent of the causal mechanism).

More precisely, let the functions \( \log f' \) (the log of the derivative function) and \( p_X \) be viewed as random variables on the probability space \( [0, 1] \) with a uniform distribution. We say \( p_{X,Y} \) satisfies an IGCI model if \( f \) is a mapping as above, and the following independence criterion holds: \( \text{Cov} [\log f', p_X] = 0 \), where

\[
\text{Cov} [\log f', p_X] = \int_0^1 \log f'(x) p_X(x) dx - \int_0^1 \log f'(x) dx \int_0^1 p_X(x) dx \quad (31.55)
\]

where \( \int_0^1 p_X(x) dx = 1 \). One can show that the inverse function \( f^{-1} \) satisfies \( \text{Cov} \left[ \log f^{-1'}, p_Y \right] \ge 0 \), with equality iff \( f \) is linear.

This can be turned into an empirical test as follows. Define

\[
C_{X \to Y} = \int_0^1 \log f'(x) p(x) dx \approx \frac{1}{N-1} \sum_{j=1}^{N-1} \log \frac{|y_{j+1} - y_j|}{|x_{j+1} - x_j|} \quad (31.56)
\]

where \( x_1 < x_2 \cdots x_N \) are the observed \( x \)-values in increasing order. The quantity \( C_{Y \to X} \) is defined analogously. We then choose \( X \to Y \) as the model whenever \( \hat{C}_{X \to Y} < \hat{C}_{Y \to X} \). This is called the **slope based approach** to IGCI.

One can also show that an IGCI model satisfies the property that \( H(X) \le H(Y) \), where \( H() \) is the differential entropy. Intuitively, the reason is that applying a nonlinear function \( f \) to \( p_X \) can introduce additional irregularities, thus making \( p_Y \) less uniform than \( p_X \). This is illustrated in Figure 31.18. We can then choose between \( X \to Y \) and \( X \leftarrow Y \) based on the difference in estimated entropies.

An empirical comparison of the slope-based and entropy-based approaches to IGCI can be found in [Moo+16].

## 31.4.2 Learning causal DAGs from interventional data

In Section 31.2, we discuss how to learn a DAG structure from observational data, using either likelihood-based (Bayesian) methods of model selection, or constraint-based (frequentist) methods. (See [Tu+19] for a recent empirical comparison of such methods applied to a medical simulator.) However, such approaches cannot distinguish between models that are Markov equivalent, and thus the output may not be sufficient to answer all causal queries of interest.

To distinguish DAGs within the same Markov equivalence class, we can use **interventional data**, where certain variables have been set, and the consequences have been measured. In particular, we can modify the standard likelihood-based DAG learning method discussed in Section 31.2 to take into account the fact that

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_185_0.png)

Figure 31.19: (a) A design matrix consisting of 5400 data points (rows) measuring the status (using flow cytometry) of 11 proteins (columns) under different experimental conditions. The data has been discretized into 3 states: low (black), medium (grey) and high (white). Some proteins were explicitly controlled using activating or inhibiting chemicals. (b) A directed graphical model representing dependencies between various proteins (blue circles) and various experimental interventions (pink ovals), which was inferred from this data. We plot all edges for which p(G_st = 1|D) > 0.5. Dotted edges are believed to exist in nature but were not discovered by the algorithm (1 false negative). Solid edges are true positives. The light colored edges represent the effects of intervention. From Figure 6d of [EM07].

the data generating mechanism has been changed. For example, if \(\theta_{ijk} = p(X_i = j|X_{pa(i)} = k)\) is a CPT for node \(i\), then when we compute the sufficient statistics \(N_{ijk} = \sum_n \mathbb{I}(X_{ni} = j, X_{n,pa(i)} = k)\), we exclude cases \(n\) where \(X_i\) was set externally by intervention, rather than sampled from \(\theta_{ijk}\). This technique was first proposed in [CY99], and corresponds to Bayesian parameter inference from a set of mutilated models with shared parameters.

The preceding method assumes that we use **perfect interventions**, where we deterministically set a variable to a chosen value. In reality, experimenters can rarely control the state of individual variables. Instead, they can perform actions which may affect many variables at the same time. (This is sometimes called a “fat hand intervention”, by analogy to an experiment where someone tries to change a single component of some system (e.g., electronic circuit), but accidentally touching multiple components and thereby causing various side effects.) We can model this by adding the intervention nodes to the DAG (**??**), and then learning a larger augmented DAG structure, with the constraint that there are no edges between the intervention nodes, and no edges from the “regular” nodes back to the intervention nodes.

For example, suppose we perturb various proteins in a cellular signalling pathway, and measure the resulting phosphorylation status using a technique such as flow cytometry, as in [Sac+05]. An example of such a dataset is shown in Figure 31.19(a). Figure 31.19(b) shows the augmented DAG that was learned from the interventional flow cytometry data depicted in Figure 31.19(a). In particular, we plot the median graph, which includes all edges for which \(p(G_{ij} = 1|\mathcal{D}) > 0.5\). These were computed using the exact algorithm of [Koi06]. See [EM07] for details.

Since interventional data can help to uniquely identify the DAG, it is natural to try to choose the optimal set of interventions so as to discover the graph structure with as little data as possible. This is a form of active learning or experiment design, and is similar to what scientists do. See e.g., [Mur01; HG09; KB14; HB14; Mue+17] for some approaches to this problem.

## 31.4.3 Learning from low-level inputs

In many problems, the available data is quite “low level”, such as pixels in an image, and is believed to be generated by some “higher level” latent causal factors, such as objects interacting in a scene. Learning causal models of this type is known as **causal representation learning**, and combines the causal discovery methods discussed in this section with techniques from latent variable modeling (e.g., VAEs, **??**) and representation
