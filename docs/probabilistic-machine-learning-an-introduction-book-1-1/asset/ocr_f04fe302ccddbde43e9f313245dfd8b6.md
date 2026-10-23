# 4.6 Online (recursive) estimation

If the entire dataset $\mathcal{D}$ is available before training starts, we say that we are doing **batch learning**. However, in some cases, the data set arrives sequentially, so $\mathcal{D} = \{\mathbf{y}_1,\mathbf{y}_2,\dots\}$ in an unbounded stream. In this case, we want to perform **online learning**.

Let $\hat{\boldsymbol{\theta}}_{t-1}$ be our estimate (e.g., MLE) given $\mathcal{D}_{1:t-1}$. To ensure our learning algorithm takes constant time per update, we need to find a learning rule of the form

$$\boldsymbol{\theta}_t = f(\hat{\boldsymbol{\theta}}_{t-1},\mathbf{y}_t)\tag{4.100}$$

This is called a **recursive update**. Below we give some examples of such online learning methods.

# 4.6.1 Example: recursive MLE for the mean of a Gaussian

Let us reconsider the example from Sec. 4.2.5 where we computed the MLE for a univariate Gaussian. We know that the batch estimate for the mean is given by

$$\hat{\boldsymbol{\mu}}_t = \frac{1}{t}\sum_{n=1}^{t}\mathbf{y}_n\tag{4.101}$$

This is just a **running sum** of the data, so we can easily convert this into a recursive estimate as follows:

$$\hat{\boldsymbol{\mu}}_t = \frac{1}{t}\sum_{n=1}^{t}\mathbf{y}_n = \frac{1}{t}\big((t-1)\hat{\boldsymbol{\mu}}_{t-1} + \mathbf{y}_t\big)\tag{4.102}$$\n$$= \hat{\boldsymbol{\mu}}_{t-1} + \frac{1}{t}(\mathbf{y}_t - \hat{\boldsymbol{\mu}}_{t-1})\tag{4.103}$$

This is known as a **moving average**.

We see from Eq. (4.103) that the new estimate is the old estimate plus a correction term. The size of the correction diminishes over time (i.e., as we get more samples). However, if the distribution is changing, we want to give more weight to more recent data examples. We discuss how to do this in Sec. 4.6.2.

# 4.6.2 Exponentially-weighted moving average (EMA)