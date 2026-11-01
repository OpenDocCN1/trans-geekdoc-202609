
Figure 13.19 Performance of rejection sampling and likelihood weighting on the insurance network. The x-axis shows the number of samples generated and the y-axis shows the maximum absolute error in any of the probability values for a query on `PropertyCost`.

## 13.4.2 Inference by Markov chain simulation

Markov chain Monte Carlo (`MCMC`) algorithms work differently from rejection sampling and likelihood weighting. Instead of generating each sample from scratch, `MCMC` algorithms generate a sample by making a random change to the preceding sample. Think of an `MCMC` algorithm as being in a particular current state that specifies a value for every variable and generating a next state by making random changes to the current state.

Markov chain Monte Carlo

The term Markov chain refers to a random process that generates a sequence of states. (Markov chains also figure prominently in [Chapters 14](#Chapter14-00.xhtml) and [16](#Chapter16-00.xhtml); the simulated annealing algorithm in [Chapter 4](#Chapter04-00.xhtml) and the WALK SAT algorithm in [Chapter 7](#Chapter07-00.xhtml) are also members of the `MCMC` family.) We begin by describing a particular form of `MCMC` called Gibbs sampling, which is especially well suited for Bayes nets. We then describe the more general Metropolis–Hastings algorithm, which allows much greater flexibility in generating samples.

Markov chain Gibbs sampling Metropolis–Hastings

## Gibbs sampling in Bayesian networks

The Gibbs sampling algorithm for Bayesian networks starts with an arbitrary state (with the evidence variables fixed at their observed values) and generates a next state by randomly sampling a value for one of the nonevidence variables `Xi`. Recall from [page 437](#Chapter13-02.xhtml#page_437) that `Xi` is independent of all other variables given its Markov blanket (its parents, children, and children’s other parents); therefore, Gibbs sampling for `Xi` means sampling conditioned on the current values of the variables in its Markov blanket. The algorithm wanders randomly around the state space—the space of possible complete assignments—flipping one variable at a time, but keeping the evidence variables fixed. The complete algorithm is shown in [Figure 13.20](#Chapter13-04.xhtml#fig13-20).

![](images/Fig-187.jpg)

Figure 13.20 The Gibbs sampling algorithm for approximate inference in Bayes nets; this version chooses variables at random, but cycling through the variables but also works.

Consider the query `P(Rain | Sprinkler = true, WetGrass = true)` for the network in [Figure 13.15(a)](#Chapter13-03.xhtml#fig13-15). The evidence variables `Sprinkler` and `WetGrass` are fixed to their observed values (both true), and the nonevidence variables `Cloudy` and `Rain` are initialized randomly to, say, true and false respectively. Thus, the initial state is [true, true, false, true], where we have marked the fixed evidence values in bold. Now the nonevidence variables `Zi` are sampled repeatedly in some random order according to a probability distribution `ρ(i)` for choosing variables. For example:
1. `Cloudy` is chosen and then sampled, given the current values of its Markov blanket: in this case, we sample from `P(Cloudy | Sprinkler = true, Rain = false)`. Suppose the result is `Cloudy = false`. Then the new current state is [false, true, false, true].
2. `Rain` is chosen and then sampled, given the current values of its Markov blanket: in this case, we sample from `P(Rain | Cloudy = false, Sprinkler = true, WetGrass = true)`. Suppose this yields `Rain = true`. The new current state is [false, true, true, true].

The one remaining detail concerns the method of calculating the Markov blanket distribution `P(Xi | mb(Xi))`, where `mb(Xi)` denotes the values of the variables in `Xi`’s Markov blanket, `MB(Xi)`. Fortunately, this does not involve any complex inference. As shown in Exercise 13.MARB, the distribution is given by
$\\begin{matrix} \\left. P\\text{(}x\_{i} \\middle| mb\\text{(}X\_{i}\\text{))~=}\\alpha\\ P\\text{(}x\_{i} \\middle| parents\\text{(}X\_{i}\\text{))}{\\prod\\limits\_{Y\_{j} \\in Children(X\_{i})}\\left. P\\text{(}y\_{j} \\middle| parents\\text{(}Y\_{j}\\text{))~}\\text{.} \\right.} \\right. & {\\text{(13}\\text{.10)}} \\\\ \\end{matrix}$

In other words, for each value `x_i`, the probability is given by multiplying probabilities from the CPTs of `Xi` and its children. For example, in the first sampling step shown above, we sampled from `P(Cloudy | Sprinkler = true, Rain = false)`. By [Equation (13.10)](#Chapter13-04.xhtml#eq13-10), and abbreviating the variable names, we have
$\\begin{matrix} \\left. P(c \\middle| s,\\neg r)\\ = \\alpha\\ P(c)P(s \\middle| c)P(\\neg r \\middle| c)\\ = \\alpha\\ 0.5\\ \\text{·}\\ 0.1\\ \\text{·}\\ 0.2 \\right. \\\\ \\left. P(\\neg c \\middle| s,\\neg r)\\ = \\ P(\\neg c)P(s \\middle| \\neg c)P(\\neg r \\middle| \\neg c)\\ = \\alpha\\ 0.5\\ \\text{·}\\ 0.5\\ \\text{·}\\ 0.8, \\right. \\\\ \\end{matrix}$
so the sampling distribution is α〈0.001,0.020〉 ≈ 〈0.048,0.952〉.

[Figure 13.21(a)](#Chapter13-04.xhtml#fig13-21) shows the complete Markov chain for the case where variables are chosen uniformly, i.e., `ρ(Cloudy) = ρ(Rain) = 0.5`. The algorithm is simply wandering around in this graph, following links with the stated probabilities. Each state visited during this process is a sample that contributes to the estimate for the query variable `Rain`. If the process visits 20 states where `Rain` is true and 60 states where `Rain` is false, then the answer to the query is `NORMALIZE(〈20, 60〉) = 〈0.25,0.75〉`.

Description
In both parts, the different states are depicted by four rectangular blocks. The blocks are labeled `c r`, `c not r`, `not c r`, and `not c not r`. Part (“a”): A loop labeled 0.6296 from `c r` points back to it. An arrow labeled 0.0926 from `c r` points to `c not r`. An arrow labeled 0.4074 from `c not r` points back to `c r`. A loop labeled 0.1164 from `c not r` points back to it. An arrow labeled 0.2778 from `c r` points to `not c r`. An arrow labeled 0.2222 from `not c r` points back to `c r`. A loop labeled 0.3856 from `not c r` points back to itself. An arrow labeled 0.3922 from `not c r` points to `not c not r`. An arrow labeled 0.1078 from `not c not r` points back to `not c r`. A loop labeled 0.8683 from `not c not r` points back to it. An arrow labeled 0.0238 from `not c not r` points to `c not r`. An arrow labeled 0.4762 from `c not r` points back to `not c not r`. Part (b): A loop labeled 1.0000 from `c r` points back to it. An arrow labeled 0.0000 from `c r` points to `c not r`. An arrow labeled 0.5000 from `c not r` points back to `c r`. A loop labeled 0.0000 from `c not r` points back to it. An arrow labeled 0.0000 from `c r` points to `not c r`. An arrow labeled 0.5000 from `not c r` points back to `c r`. A loop labeled 0.0000 from `not c r` points back to itself. An arrow labeled 0.5000 from `not c r` points to `not c not r`. An arrow labeled 0.0000 from `not c not r` points back to `not c r`. A loop labeled 1.0000 from `not c not r` points back to it. An arrow labeled 0.0000 from `not c not r` points to `c not r`. An arrow labeled 0.5000 from `c not r` points back to `not c not r`.

![](images/Fig-188.jpg)

Figure 13.21(a) The states and transition probabilities of the Markov chain for the query `P(Rain | Sprinkler = true, WetGrass = true)`. Note the self-loops: the state stays the same when either variable is chosen and then resamples the same value it already has. (b) The transition probabilities when the CPT for `Rain` constrains it to have the same value as `Cloudy`.

## Analysis of Markov chains

We have said that Gibbs sampling works by wandering randomly around the state space to generate samples. To explain why Gibbs sampling works correctly—that is, why its estimates converge to correct values in the limit—we will need some careful analysis. (This section is somewhat mathematical and can be skipped on first reading.)
