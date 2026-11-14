It is also possible to compose individual proposals by chaining them together to get

$q(\mathbf{x}'|\mathbf{x}) = \sum_{\mathbf{x}_1} \cdots \sum_{\mathbf{x}_{K-1}} q_1(\mathbf{x}_1|\mathbf{x})q_2(\mathbf{x}_2|\mathbf{x}_1) \cdots q_K(\mathbf{x}|\mathbf{x}_{K-1})$ (12.17)

A common example is where each base proposal only updates a subset of the variables (see e.g., Section 12.3).

# 12.2.3.4 Data-driven MCMC

In the case where the target distribution is a posterior, \(p^*(\mathbf{x}) = p(\mathbf{x}|\mathcal{D})\), it is helpful to condition the proposal not just on the previous hidden state, but also the visible data, i.e., to use \(q(\mathbf{x}'|\mathbf{x}, \mathcal{D})\). This is called **data-driven MCMC** (see e.g., [TZ02; Jih+12]).

One way to create such a proposal is to train a recognition network to propose states using \(q(\mathbf{x}'|\mathbf{x}, \mathcal{D}) = f(\mathbf{x})\). If the state space is high-dimensional, it might be hard to predict all the hidden components, so we can alternatively train individual “experts” to predict specific pieces of the hidden state. For example, in the context of estimating the 3d pose of a person from an image, we might combine a face detector with a limb detector. We can then use a mixture proposal of the form

\(q(\mathbf{x}'|\mathbf{x}, \mathcal{D}) = \pi_0 q_0(\mathbf{x}'|\mathbf{x}) + \sum_k \pi_k q_k(\mathbf{x}'_k|f_k(\mathcal{D}))\) (12.18)

where \(q_0\) is a standard data-independent proposal (e.g., random walk), and \(q_k\) updates the \(k\)’th component of the state space.

The overall procedure is a form of **generate and test**: the discriminative proposals \(q(\mathbf{x}'|\mathbf{x}, \mathcal{D})\) generate new hypotheses, which are then “tested” by computing the posterior ratio \(\frac{p(\mathbf{x}'|\mathcal{D})}{p(\mathbf{x}|\mathcal{D})}\), to see if the new hypothesis is better or worse. (See also Section 13.3, where we discuss learning proposal distributions for particle filters.)

# 12.2.3.5 Adaptive MCMC

One can change the parameters of the proposal as the algorithm is running to increase efficiency. This is called **adaptive MCMC**. This allows one to start with a broad covariance (say), allowing large moves through the space until a mode is found, followed by a narrowing of the covariance to ensure careful exploration of the region around the mode.

However, one must be careful not to violate the Markov property; thus the parameters of the proposal should not depend on the entire history of the chain. It turns out that a sufficient condition to ensure this is that the adaption is “faded out” gradually over time. See e.g., [AT08] for details.

# 12.2.4 Initialization

It is necessary to start MCMC in an initial state that has non-zero probability. A natural approach is to first use an optimizer to find a local mode. However, at such points the gradients of the log joint are zero, which can cause problems for some gradient-based MCMC methods, such as HMC (Section 12.5), so it can be better to start “close” to a MAP estimate (see e.g., [HFM17, Sec 7.]).