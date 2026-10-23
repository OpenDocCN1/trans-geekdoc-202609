sampled (section 16.3). Ancestral sampling defines an efficient, single-pass method of obtaining a sample.

In an EBM, we can avoid this chicken-and-egg problem by sampling using a Markov chain. The core idea of a Markov chain is to have a state $\boldsymbol{x}$ that begins as an arbitrary value. Over time, we randomly update $\boldsymbol{x}$ repeatedly. Eventually $\boldsymbol{x}$ becomes (very nearly) a fair sample from $p(\boldsymbol{x})$. Formally, a Markov chain is defined by a random state $\boldsymbol{x}$ and a transition distribution $T(\boldsymbol{x}' \mid \boldsymbol{x})$ specifying the probability that a random update will go to state $\boldsymbol{x}'$ if it starts in state $\boldsymbol{x}$. Running the Markov chain means repeatedly updating the state $\boldsymbol{x}$ to a value $\boldsymbol{x}'$ sampled from $T(\boldsymbol{x}' \mid \boldsymbol{x})$.

To gain some theoretical understanding of how MCMC methods work, it is useful to reparametrize the problem. First, we restrict our attention to the case where the random variable $\mathbf{x}$ has countably many states. We can then represent the state as just a positive integer $x$. Different integer values of $x$ map back to different states $\boldsymbol{x}$ in the original problem.

Consider what happens when we run infinitely many Markov chains in parallel. All the states of the different Markov chains are drawn from some distribution $q^{(t)}(x)$, where $t$ indicates the number of time steps that have elapsed. At the beginning, $q^{(0)}$ is some distribution that we used to arbitrarily initialize $x$ for each Markov chain. Later, $q^{(t)}$ is influenced by all the Markov chain steps that have run so far. Our goal is for $q^{(t)}(x)$ to converge to $p(x)$.

Because we have reparametrized the problem in terms of a positive integer $x$, we can describe the probability distribution $q$ using a vector $\boldsymbol{v}$ with

$$q(\mathrm{x}=i)=v_i.\tag{17.17}$$

Consider what happens when we update a single Markov chain's state $x$ to a new state $x'$. The probability of a single state landing in state $x'$ is given by

$$q^{(t+1)}(x')=\sum_{x} q^{(t)}(x)T(x' \mid x).\tag{17.18}$$

Using our integer parametrization, we can represent the effect of the transition operator $T$ using a matrix $\boldsymbol{A}$. We define $\boldsymbol{A}$ so that

$$A_{i,j}=T(\mathbf{x}'=i \mid \mathbf{x}=j).\tag{17.19}$$

Using this definition, we can now rewrite equation 17.18. Rather than writing it in terms of $q$ and $T$ to understand how a single state is updated, we may now use $\boldsymbol{v}$