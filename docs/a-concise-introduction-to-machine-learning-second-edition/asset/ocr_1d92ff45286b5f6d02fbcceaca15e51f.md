We illustrate with an example generating samples of a target distribution which is normal with mean and variance

$$\mu = \left( \frac{2}{3} \right), \quad \Sigma = \left( \begin{array}{cc} 1 & 3/2 \ 3/2 & 3 \end{array} \right).$

Listing 3.3 implements Metropolis algorithm for this example. The question is

Also the start of the Markov chain needs to be chosen carefully to ensure the state space is explored in relatively few steps. The technique known as *burn-in* discards the first elements of a Markov chain and restarts the chain from the state it reached. Strictly speaking, this is not necessary. The elements of a Markov chain will be a good set of samples as much as the chain is long enough. Listing 3.3 sets the first element $x_1$ to the mean $\mu$ of the target distribution. Of course, these choices for $\sigma$ and $x_1$ are only possible if this is known about the target. In any case, good estimates for these are necessary.

These considerations are illustrated in Figure 3.6 which depicts the generated random walks with the candidates that were rejected (+) for different choices of $x_1$ and $\sigma$ and the 95% *confidence ellipse* of the target distribution. The confidence ellipse gives the area where 95% of the samples of the target distribution are expected to lie.

Figure 3.6a used $x_1 = \mu$ and $\sigma = \sigma_{min}$. The state space is well explored. About two thirds of candidates are accepted. This means that one out of three samples coincide with another sample. In Figure 3.6 the acceptance ratio is about the same as before, but the state space is less explored. Figure 3.6b shows the starting position was moved to $(0,0)^T$. The algorithm needs to run for longer.

Figure 3.6 used $\sigma = \sigma_{min}/2$. About 87% of candidates are accepted, but the algorithm moves slowly through the state space. Again it needs to run longer to explore the state space. In Figure 3.6d the standard deviation of the proposal distribution was doubled as compared to Figure 3.6a. The acceptance rate dropped to 43%. This means that more than half of samples share their location. This does not matter, if the expectation is expected to be calculated and the appropriate weighting is applied. If the aim is however to explore the state space, a higher acceptance rate is more desirable.