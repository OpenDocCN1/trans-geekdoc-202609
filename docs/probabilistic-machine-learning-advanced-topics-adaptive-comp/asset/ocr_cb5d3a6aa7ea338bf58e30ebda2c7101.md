are occasional “streaks”, in which 6s seem to show up more often than other values. We would like to estimate the underlying state, namely whether the die is fair or loaded, so that we make predictions about the future.

To formalize this, let \( z_t \in \{1, 2\} \) represent the unknown hidden state (fair or loaded) at time \( t \), and let \( y_t \in \{1, \dots, 6\} \) represent the observed outcome (die roll). Let \( A_{jk} = p(z_t = k | z_{t-1} = j) \) be the state transition matrix. Most of the time the casino uses a fair die, \( z = 1 \), but occasionally it switches to a loaded die, \( z = 2 \), for a short period, as shown in the state transition diagram in Figure 9.2.

Let \( B_{kl} = p(y_t = l | z_t = k) \) be the observation matrix corresponding to a categorical distribution over values of the die face. If \( z = 1 \) the observation distribution is a uniform categorical distribution over the symbols \(\{1, \dots, 6\}\). If \( z = 2 \), the observation distribution is skewed towards face 6. That is,

\( p(y_t | z_t = 1) = \text{Cat}(y_t | [1/6, \dots, 1/6]) \) (9.2) 
\( p(y_t | z_t = 2) = \text{Cat}(y_t | [1/10, 1/10, 1/10, 1/10, 1/10, 5/10]) \) (9.3)

If we sample from this model, we may generate data such as the following:

```
hid: 111111111222211111111111111111111111112222222222212222111111111111111111
obs: 13555345265533663163515515526232112113462221263264265422344645323242361
```

Here obs refers to the observation and hid refers to the hidden state (1 is fair and 2 is loaded). In the full sequence of length 300, we find the empirical fraction of times that we observe a 6 in hidden state 1 to be 0.149, and in state 2 to be 0.472, which are very close to the expected fractions. (See casino_hmm.ipynb for the code.)

# 9.2.1.2 Posterior inference

Our goal is to infer the hidden states by computing the posterior over all the hidden nodes in the model, \( p(z_t | y_{1:T}) \). This is called the **smoothing distribution**. By the Markov property, we can break this into two terms:

\( p(\boldsymbol{z}_t = j | \boldsymbol{y}_{1:t+1:T}, \boldsymbol{y}_{1:t}) \propto p(\boldsymbol{z}_t = j, \boldsymbol{y}_{t+1:T} | \boldsymbol{y}_{1:t}) p(\boldsymbol{z}_t = j | \boldsymbol{y}_{1:t}) p(\boldsymbol{y}_{t+1:T} | \boldsymbol{z}_t = j, \boldsymbol{y}_{1:t}) \) (9.4)

We will first compute the **filtering distribution** \( p(\boldsymbol{z}_t = j | \boldsymbol{y}_{1:t}) \) by working forwards in time. We then compute the \( p(\boldsymbol{y}_{t+1:T} | \boldsymbol{z}_t = j) \) terms by working backwards in time, and then we finally combine both terms. Both passes take \( (TK^2) \) time, where \( K \) is the number of discrete hidden states. We give the details below.

# 9.2.2 The forwards algorithm

As we discuss in Section 8.1.2, the **Bayes filter** is an algorithm for recursively computing the **belief state** \( p(\boldsymbol{z}_t | \boldsymbol{y}_{1:t}) \) given the prior belief from the previous step, \( p(\boldsymbol{z}_{t-1} | \boldsymbol{y}_{1:t-1}) \), the new observation \( \boldsymbol{y}_t \), and the model. In the HMM literature, this is known as the **forwards algorithm**.

In an HMM, the latent states \( \boldsymbol{z}_t \) are discrete, so we can define the belief state as a vector, \( \alpha_t(j) \triangleq p(z_t = j | \boldsymbol{y}_{1:t}) \), the local evidence as another vector, \( \lambda_t(j) \triangleq p(\boldsymbol{y}_t | z_t = j) \), and the transition matrix as \( A_{i,j} = p(z_t = j | z_{t-1} = i) \). Then the predict step becomes

\( \alpha_{t|t-1}(j) \triangleq p(z_t = j | \boldsymbol{y}_{1:t-1}) = \sum_i p(z_t = j | z_{t-1} = i) p(z_{t-1} = i | \boldsymbol{y}_{1:t-1}) = \sum_i A_{i,j} \alpha_{t-1}(i) \) (9.5)