
In this minimization problem, constraint (7.5) is just a linear equality constraint, but constraint (7.6) is a non-linear and non-convex constraint when $\sigma^{(l)}$ is a nonlinear function such as ReLU. Therefore, it is theoretically difficult to solve this optimization problem exactly. The idea in sound but incomplete verification aims to relax constraint (7.6) to make the problem tractable while being able to compute a lower bound of the solution. We will discuss how to achieve a lower bound and the exact solution of this problem in the next two chapters, corresponding to algorithms for incomplete and complete verifications.

Before delving into the actual verification algorithms, we will first discuss the generalized form of (7.3). In fact, neural network verification can be used to verify many other properties in addition to adversarial robustness. Given a neural network $f : \mathbb{R}^d \rightarrow \mathbb{R}^K$ that maps input to output neurons, verification aims to find a lower bound or exact solution of an affine function within an input region $S$:

$$\min \langle c, f(\boldsymbol{x}) \rangle \text{ s.t. } \boldsymbol{x} \in S, \tag{7.8}$$

where $c$ is called a linear specification, which corresponds to the property we want to verify. In the setting of binary classification, as in formulation (7.3), $f(\boldsymbol{x})$ is just a single value and we can set $c = 1$ for verification. For multi-class classification problem, by setting $c$ as a vector with $1$ on the positive class and $-1$ on the opposite class (e.g., class $t$), the sign of the solution of (7.8) indicates whether there exists any adversarial example predicted as class $t$. If we verify there exists no adversarial example for each class $t$, then the robustness can be certified. In addition to robustness verification, this framework is also used to guarantee safety in many real-time control systems, such as aircraft controls (Julian et al., 2019; Katz et al., 2017).

## 7.3 Applications of neural network verification

As mentioned before, neural network verification can verify not only robustness, but also other safety specifications as long as the specification can be written as an affine function locally. Here we introduce some important applications for neural network verification.

### Safety-critical control systems

Verification has been used in many control systems. Among them, the safety verification problem of next-generation airborne collision avoidance system for unmanned aircraft (ACAS Xu) has been used as the benchmark for this field (Katz et al., 2017; Julian et al., 2019), and several other practical systems are also considered in the previous verification work such as a LiDAR object detection system (Sun et al., 2019a), a perception network for automated driving (Cheng, 2019), and a fuel injecting system (Wong et al., 2020b). Taking the ACAS Xu system as an example, it contains 45 neural networks with hundreds of neurons, and the goal is to verify whether these networks satisfy some predefined safety specifications for collision avoidance.

### Natural language processing

The robustness of natural language models have become an important problem in natural language processing. It has been shown that semantic preserved perturbations (e.g., replacing a word by its synonym) can alter the model's prediction in many NLP tasks. Certified defense methods have been applied in (Jia et al., 2019; Huang et al., 2019) by using neural network verification methods and extending to the discrete perturbation setting.

### Machine learning interpretability

Neural network verification is also an important tool for understanding the model's behavior. For instance, many feature-based explanations (Hsieh et al., 2020) are based on the sensitivity of models – how much perturbation to a feature can change the model's prediction – which can be easily answered by verification tools. Also, verification methods can be used to find an important set of features as well as identifying unimportant features that are provably having no effect on the model.

## 7.4 Extended reading

- A survey on neural network verification in (Liu et al., 2019a) gives an overview on both incomplete and complete verifications.
- The International Verification of Neural Network Competition (VNN-Comp) that takes place each year has been a place for teams demonstrating state-of-the-art tools on neural network verification on various problems.

This page intentionally left blank

## CHAPTER 8

### Incomplete neural network verification

As mentioned in the previous section, solving the complete neural network verification problem is challenging and time-consuming, and earlier works that focused on complete verification usually do not scale to problems beyond a hundred neurons. Further, it has been shown that complete verification for ReLU networks is NP-complete (Katz et al., 2017). Motivated by the fundamental limit and practical difficulties, incomplete verification algorithms have arisen since 2018, where they aim to provide sound verification for large neural networks, with the trade-off that they can only certify some but not all instances. These verifiers are often efficient and can be easily parallelized with GPU. Interestingly, these incomplete verifiers later become powerful tools even for complete verification, as will be shown in the next section.

### 8.1 A convex relaxation framework

We first introduce the convex relaxation framework, which covers most of the existing incomplete neural network verification methods. As mentioned in the last chapter, neural network verification can be formulated as an optimization problem. For simplicity, let us assume that \( f(\boldsymbol{x}) \) is an \( L \)-layer feedforward network:

$$f(\boldsymbol{x}) := \boldsymbol{z}^{(L)} = W^{(L)}\boldsymbol{x}^{(L)} + \boldsymbol{b}^{(L)}, \quad \boldsymbol{x}^{(l)} = \sigma^{(l)}(W^{(l)}\boldsymbol{x}^{(l)} + \boldsymbol{b}^{(l)}), \quad l \in [L], \quad (8.1)$$

where \( \boldsymbol{x}^{(0)} = \boldsymbol{x} \) is the input, \( W^{(l)} \) and \( \boldsymbol{b}^{(l)} \) are the weight matrix and bias vector of the \( l \)th layer, and \( \sigma^{(l)} \) is a (nonlinear) activation function. Instead of passing a single \( \boldsymbol{x} \) to the network, neural network verification aims to propagate an input region \( S \) and verify some properties of output neurons. This can be written as the following optimization problem:

$$\begin{aligned} \min_{\boldsymbol{x}^{(0)} \in S} \quad & \boldsymbol{c}^T \boldsymbol{x}^{(L)} \text{ s.t. } \boldsymbol{z}^{(l)} = W^{(l)}\boldsymbol{x}^{(l)} + \boldsymbol{b}^{(l)}, \\ & \boldsymbol{x}^{(l+1)} = \sigma^{(l)}(\boldsymbol{z}^{(l)}), \\ & l \in [L], \end{aligned} \quad (\mathcal{O})$$

where **c** corresponds to the specification as defined in (7.8). Unfortunately, solving (O) is intractable due to the nonconvex constraints; it is thus natural to conduct convex relaxation on the feasible set. Specifically, we relax each \(x^{(l+1)} = \sigma^{(l)}(z^{(l)})\) by convex inequality constraints, leading to the following convex relaxation:

$$\begin{aligned} \min \quad & c^T x^{(L)} \text{ s.t. } z^{(l)} = W^{(l)}x^{(l)} + b^{(l)}, \\ & \underline{\sigma}^{(l)}(z^{(l)}) \le x^{(l+1)} \le \bar{\sigma}^{(l)}(z^{(l)}), \\ & \underline{z}^{(l)} \le x^{(l)} \le \bar{z}^{(l)}, \\ & l \in [L], \end{aligned} \quad (C)$$

where \(\underline{\sigma}^{(l)}(z)\) (\(\bar{\sigma}^{(l)}(z)\)) is convex (concave) and satisfies \(\underline{\sigma}^{(l)}(z) \le \sigma^{(l)}(z) \le \bar{\sigma}^{(l)}(z)\) for \(\underline{z}^{(l)} \le z \le \bar{z}^{(l)}\). The preactivation upper and lower bounds \(\bar{z}^{(l)}\) and \(\underline{z}^{(l)}\) correspond to some precomputed upper and lower bounds for each **z**. In general, we can set \(\underline{z}^{(l)} = -\infty\) and \(\bar{z}^{(l)} = \infty\) for all *l*, but tighter ranges of \(\underline{z}^{(l)}\) and \(\bar{z}^{(l)}\) can achieve tighter solutions. A typical approach is to solve (C) recursively to obtain the tightest \(\underline{z}^{(l)}\) and \(\bar{z}^{(l)}\).

In the following, we will introduce a family of linear relaxation-based methods, which can be viewed as particular cases of (C) when the nonlinear activation functions are bounded by linear upper and lower bounds.

### 8.2 Linear bound propagation methods

Linear bound propagation is a simple yet effective method for sound but incomplete verification. Note that there were several papers proposing different versions of linear bound propagation methods, such as (Wong and Kolter, 2017; Weng et al., 2018a; Zhang et al., 2018; Singh et al., 2018a, 2019b) (see Fig. 8.1). However, since they lead to similar algorithms with slightly different choices of upper/lower bounds, we will mainly focus on introducing the CROWN algorithm (Zhang et al., 2018) in this section and then talk about the relationship between CROWN and other algorithms.

The key idea is to use linear functions to bound the values of each particular neuron in any intermediate and final layer. The main difficulty for obtaining a linear bound is the nonlinear activations. If there are no nonlinear activations, then clearly any \(z^{(l)}\) can be written as a linear function to the input. Then for any output neuron \(f(\mathbf{x})\), we can write it as \(f(x) = a^T x\), where \(a\) is the slope, and in this case, verification is equivalent to
