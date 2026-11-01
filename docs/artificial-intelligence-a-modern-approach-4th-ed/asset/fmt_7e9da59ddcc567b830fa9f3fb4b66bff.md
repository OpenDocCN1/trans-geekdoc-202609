
which simplifies to

$\\begin{matrix} {\\lambda = \\max\\limits\_{T > 0}\\frac{E\\left( \\sum\_{t\\, = \\, 0}^{T\\, - \\, 1}\\gamma^{t}R\_{t} \\right)}{E\\left( \\sum\_{t\\, = \\, 0}^{T\\, - \\, 1}\\gamma^{t} \\right)}.\\,\\,} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(16.15)} \\\\ \\end{matrix}$

This equation defines a kind of “value” for `M` in terms of its ability to deliver a stream of timely rewards; the numerator of the fraction represents a utility while the denominator can be thought of as a “discounted time,” so the value describes the maximum obtainable utility per unit of discounted time. (It’s important to remember that `T` in the equation is a stopping time, which is governed by a rule for stopping rather than being a simple integer; it reduces to a simple integer only when `M` is a deterministic reward sequence.) The value defined in [Equation (16.15)](#Chapter16-03.xhtml#eq16-15) is called the Gittins index of `M`.

<p class="sidebar">Gittins index</p>

The remarkable thing about the Gittins index is that it provides a very simple optimal policy for any bandit problem: pull the arm that has the highest Gittins index, then update the Gittins indices. Furthermore, because the index of arm `M[i]` depends only on the properties of that arm, an optimal decision on the first iteration can be calculated in `O(n)` time, where `n` is the number of arms. And because the Gittins indices of the arms that are not selected remain unchanged, each decision after the first one can be calculated in `O(1)` time.

## 16.3.1 Calculating the Gittins index

To get more of a feel for the index, let’s calculate the value of the numerator, denominator, and ratio in [Equation (16.15)](#Chapter16-03.xhtml#eq16-15) for different possible stopping times on the deterministic reward sequence 0,2,0,7.2,0,0,0,...:

| T || 1 || 2 || 3 || 4 || 5 || 6 |

| --- | --- | --- | --- | --- | --- | --- |

| Rt || 0 || 2 || 0 || 7.2 || 0 || 0 |

| ∑γtRt || 0.0 || 1.0 || 1.0 || 1.9 || 1.9 || 1.9 |

| ∑γt || 1.0 || 1.5 || 1.75 || 1.875 || 1.9375 || 1.9687 |

| ratio || 0.0 || 0.6667 || 0.5714 || 1.0133 || 0.9806 || 0.9651 |

Clearly, the ratio will decrease from here on, because the numerator remains constant while the denominator continues to increase. Thus, the Gittins index for this arm is 1.0133, the maximum value attained by the ratio. In combination with a fixed arm `Mλ` with 0 < `λ` ≤ 1.0133, the optimal policy collects the first four rewards from `M` and then switches to `Mλ`. For `λ` > 1.0133, the optimal policy always chooses `Mλ`.

To calculate the Gittins index for a general arm `M` with current state `s`, we simply make the following observation: at the tipping point where an optimal policy is indifferent between choosing arm `M` and choosing the fixed arm `Mλ`, the value of choosing `M` is the same as the value of choosing an infinite sequence of `λ`-rewards.

Suppose we augment `M` so that at each state in `M`, the agent has two choices: either continue with `M` as before, or quit and receive an infinite sequence of `λ`-rewards (see [Figure 16.13(a)](#Chapter16-03.xhtml#fig16-13)). This turns `M` into an `MDP`, whose optimal policy is just the optimal stopping rule for `M`. Hence the value of an optimal policy in this new `MDP` is equal to the value of an infinite sequence of `λ`–rewards, that is, `λ/(1 – γ)`. So we can just solve this `MDP` ... but, unfortunately, we don’t know the value of `γ` to put into the `MDP`, as this is precisely what we are trying to calculate. But we do know that, at the tipping point, an optimal policy is indifferent between `M` and `Mλ`, so we could replace the choice to get an infinite sequence of `λ`-rewards with the choice to go back and restart `M` from its initial state `s`. (More precisely, we add a new action in every state that has the same rewards and outcomes as the action available in `s`; see Exercise 16.KATV.) This new `MDP` `Ms`, called a restart `MDP`, is illustrated in [Figure 16.13(b)](#Chapter16-03.xhtml#fig16-13).

×![](images/Fig-234.jpg)

Figure 16.13(a) The reward sequence `M` \= 0,2,0,7.2,0,0,0,... augmented with a choice to switch permanently to a constant arm `Mλ` at each point. (b) An `MDP` whose optimal value is exactly equivalent to the optimal value for (a), at the point where the optimal policy is indifferent between `M` and `Mλ`.

<p class="sidebar">Restart MDP</p>

We have the general result that the Gittins index for an arm `M` in state `s` is equal to `1 – γ` times the value of an optimal policy for the restart `MDP` `Ms`. This `MDP` can be solved by any of the algorithms in [Section 16.2](#Chapter16-02.xhtml#sec16-2). Value iteration applied to `Ms` in [Figure 16.13(b)](#Chapter16-03.xhtml#fig16-13) gives a value of 2.0266 for the start state, so we have `λ` = 2.0266 (`1 – γ`) = 1.0133 as before.

## 16.3.2 The Bernoulli bandit

Perhaps the simplest and best-known instance of a bandit problem is the Bernoulli bandit, where each arm `Mi`, produces a reward of 0 or 1 with a fixed but unknown probability `μi`. The state of arm `M[i]`, is defined by `si`, and `fi`, the counts of successes (1s) and failures (0s) so far for that arm; the transition probability predicts the next outcome to be 1 with probability (`si`)/(`si` + `fi`,) and 0 with probability (`fi`)/(`si` + `fi`,). The counts are initialized to 1 so that the initial probabilities are 1/2 rather than 0/0.[4](#Chapter16-07.xhtml#sup16-4) The Markov reward process is shown in [Figure 16.14(a)](#Chapter16-03.xhtml#fig16-14).

<p class="sidebar">Bernoulli bandit</p>

×![](images/Fig-235.jpg)

Figure 16.14(a) States, rewards, and transition probabilities for the Bernoulli bandit. (b) Gittins indices for the states of the Bernoulli bandit process.

We cannot quite apply the transformation of the preceding section to calculate the Gittins index of the Bernoulli arm because it has infinitely many states. We can, however, obtain a very accurate approximation by solving the truncated `MDP` with states up to `si` + `fi` = 100 and `γ` = 0.9. The results are shown in [Figure 16.14(b)](#Chapter16-03.xhtml#fig16-14). The results are intuitively reasonable: we see that, generally speaking, arms with higher payoff probabilities are preferred, but there is also an exploration bonus associated with arms that have only been tried a few times. For example, the index for the state (3,2) is higher than the index for the state (7,4) (0.7057 vs. 0.6922), even though the estimated value at (3,2) is lower (0.6 vs. 0.6364).

<p class="sidebar">Exploration bonus</p>

## 16.3.3 Approximately optimal bandit policies

Calculating Gittins indices for more realistic problems is rarely easy. Fortunately, the general properties observed in the preceding section–namely, the desirability of some combination of estimated value and uncertainty–lend themselves to the creation of simple policies that turn out to be “nearly as good” as optimal policies.

The first class of methods uses the upper confidence bound or `UCB` heuristic, previously introduced for Monte Carlo tree search ([Figure 6.11](#Chapter06-04.xhtml#fig6-11) on [page 209](#Chapter06-04.xhtml#page_209)). The basic idea is to use the samples from each arm to establish a confidence interval for the value of the arm, that is, a range within which the value can be estimated to lie with high confidence; then choose the arm with the highest upper bound on its confidence interval. The upper bound is the current mean value estimate `μ̂[i]` plus some multiple of the standard deviation of the uncertainty in the value. The standard deviation is proportional to $\\sqrt{1/N\_{i}}$, where `Ni` is the number of times arm `Mi` has been sampled. So we have an approximate index value for arm `Mi` given by

<p class="sidebar">Upper confidence bound</p>

$UCB\\text{(}M\_{i}\\text{)~=}{\\overset{\\land}{\\mu}}\_{i}\\, + g(N)/\\sqrt{N\_{i}},$
