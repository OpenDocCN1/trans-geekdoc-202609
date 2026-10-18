
*   Open the store at 8am.

*   Experience random demand from customers according to demand probabilities stated above (number of bicycles sold for the day will be the minimum of demand on the day and inventory at store opening on the day).

*   Close the store at 6pm and observe the state (this state is `S[t + 1]`).

If we let this process run for a while, in steady-state, we ensure that `α + β ≤ C`. So to model this process as a Finite Markov Process, we shall only consider the steady-state (finite) set of states

$$
\begin{array}{r} {\mathcal{S} = \left\{ (\alpha,\beta)|\alpha \in {\mathbb{Z}}_{\geq 0},\beta \in {\mathbb{Z}}_{\geq 0},0 \leq \alpha + \beta \leq C \right\}} \\ \end{array}
$$  

So restricting ourselves to this finite set of states, our order quantity equals `C − (α + β)` when the state is `(α, β)`.

If the current state `S[t]` is `(α, β)`, there are only `α + β + 1` possible next states `S[t + 1]` as follows:

$$
\begin{array}{r} {(\alpha + \beta - i,C - (\alpha + \beta))\text{~for~}i = 0,1,\ldots,\alpha + \beta} \\ \end{array}
$$  

with transition probabilities governed by the Poisson probabilities of demand as follows:

$$
\begin{array}{r} {\mathcal{P}((\alpha,\beta),(\alpha + \beta - i,C - (\alpha + \beta))) = f(i)\text{~for~}0 \leq i \leq \alpha + \beta - 1} \\ \end{array}
$$  

$$
\begin{array}{r} {\mathcal{P}((\alpha,\beta),(0,C - (\alpha + \beta))) = {\sum\limits_{j = \alpha + \beta}^{\infty}f}(j) = 1 - F(\alpha + \beta - 1)} \\ \end{array}
$$  

Note that the next state's (`S[t + 1]`) On-Hand can be zero resulting from any of infinite possible demand outcomes greater than or equal to `α + β`.

So we are now ready to write code for this simple inventory example as a Markov Process. All we have to do is to create a derived class inherited from `FiniteMarkovProcess` and write a method to construct the `transition_map: Transition`. Note that the generic state type `S` is replaced here with the `@dataclass InventoryState` consisting of the pair of On-Hand and On-Order inventory quantities comprising the state of this Finite Markov Process.

![](images/comp03_15.jpg)

Let us utilize the `__repr__` method written previously to view the transition probabilities for the simple case of `C = 2` and `λ = 1.0` (this code is in the file `rl/chapter2/simple_inventory_mp.py`)

![](images/comp03_16.jpg)

The output we get is nicely displayed as:

![](images/comp03_17.jpg)

For a graphical view of this Markov Process, see [Figure 3.6](#chapter3.xhtml#fig3_6). The nodes are the states, labeled with their corresponding `α` and `β` values. The directed edges are the probabilistic state transitions from 6pm on a day to 6pm on the next day, with the transition probabilities labeled on them.

![Figure 3.6 Simple Inventory Markov Process](images/fig3_6.jpg)

[Figure 3.6](#chapter3.xhtml#b3fig3_6) Simple Inventory Markov Process

We can perform a number of interesting experiments and calculations with this simple Markov Process, and we encourage you to play with this code (specifically varying the capacity `C` and Poisson mean `λ`) to run simulations and probabilistic calculations of natural curiosity for a store owner.

There is a rich and interesting theory for Markov Processes. However, we won't go into this theory as our coverage of Markov Processes so far is a sufficient building block to take us to the incremental topics of Markov Reward Processes and Markov Decision Processes. However, before we move on, we'd like to show just a glimpse of the rich theory with the calculation of `Stationary Probabilities` and apply it to the case of the above simple inventory Markov Process.

## 3.7 STATIONARY DISTRIBUTION OF A MARKOV PROCESS

The intuitive view of the stationary distribution `π` is that (under specific conditions we are not listing here) if we let the Markov Process run forever, then in the long run, the states occur at specific time steps with relative frequencies (probabilities) given by a distribution `π` that is independent of the time step. The probability of occurrence of a specific state `s` at a time step (asymptotically far out in the future) should be equal to the sum-product of probabilities of occurrence of all the states at the previous time step and the transition probabilities from those states to `s`. But since the states' occurrence probabilities are invariant in time, the `π` distribution for the previous time step is the same as the `π` distribution for the time step we considered. This argument holds for all states `s`, and that is exactly the statement of the definition of `Stationary Distribution` formalized above.

If we specialize this definition of `Stationary Distribution` to Finite-States, Discrete-Time, Time-Homogeneous Markov Processes with state space `𝒮 = {s[1],s[2],…,s[n]} = 𝒩`, then we can express the Stationary Distribution `π` as follows:

$$
\begin{array}{r} {\pi(s_{j}) = {\sum\limits_{i = 1}^{n}\pi}(s_{i}) \cdot \mathcal{P}(s_{i},s_{j})\text{~for~all~}j = 1,2,\ldots n} \\ \end{array}
$$  

Below we use bold-face notation to represent functions as vectors and matrices (since we assume finite states). So, `π` is a column vector of length `n` and `𝒫` is the `n × n` transition probability matrix (rows are source states, columns are destination states with each row summing to 1). Then, the statement of the above definition can be succinctly expressed as:

$$
\begin{array}{r} {\mathbf{\pi}^{T} = \mathbf{\pi}^{T} \cdot \mathcal{P}} \\ \end{array}
$$  

which can be re-written as:

$$
\begin{array}{r} {\mathcal{P}^{T} \cdot \mathbf{\pi} = \mathbf{\pi}} \\ \end{array}
$$  

But this is simply saying that `π` is an eigenvector of `𝒫^(T)` with eigenvalue of 1. So then, it should be easy to obtain the stationary distribution `π` from an eigenvectors and eigenvalues calculation of `𝒫^(T)`.

Let us write code to compute the stationary distribution. We shall add two methods in the `FiniteMarkovProcess` class, one for setting up the transition probability matrix `𝒫` (`get_transition_matrix` method) and another to calculate the stationary distribution `π` (`get_stationary_distribution`) from this transition probability matrix. Note that `𝒫` is restricted to `𝒩×𝒩→[0,1]` (rather than `𝒩×𝒮→[0,1]`) because these probability transitions suffice for all the calculations we will be performing for Finite Markov Processes. Here's the code for the two methods (the full code for `FiniteMarkovProcess` is in the file `rl/markov_process.py`):

![](images/comp03_18.jpg)

We skip the theory that tells us about the conditions under which a stationary distribution is well-defined, or the conditions under which there is a unique stationary distribution. Instead, we just go ahead with this calculation here assuming this Markov Process satisfies those conditions (it does!). So, we simply seek the index of the `eig_vals` vector with eigenvalue equal to 1 (accounting for floating-point error). Next, we pull out the column of the `eig_vecs` matrix at the `eig_vals` index calculated above and convert it into a real-valued vector (eigenvectors/eigenvalues calculations are, in general, complex numbers calculations—see the reference for the `np.linalg.eig` function). So this gives us the real-valued eigenvector with eigenvalue equal to 1. Finally, we have to normalize the eigenvector, so its values add up to 1 (since we want probabilities) and return the probabilities as a Categorical distribution).

Running this code for the simple case of capacity `C = 2` and Poisson mean `λ = 1.0` (instance of `SimpleInventoryMPFinite`) produces the following output for the stationary distribution `π`:

![](images/comp03_19.jpg)

This tells us that On-Hand of 0 and On-Order of 1 is the state occurring most frequently (28% of the time) when the system is played out indefinitely.
