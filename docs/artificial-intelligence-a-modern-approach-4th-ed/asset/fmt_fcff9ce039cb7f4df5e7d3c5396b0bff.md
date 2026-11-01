
```
$\\begin{array}{l} {\\mathbf{m}\_{1:t + 1}\\text{~=~}\\underset{\\mathbf{x}\_{1:t}}{\\text{max}\\ }\\mathbf{P}\\text{(}\\mathbf{x}\_{1:t},\\,\\mathbf{X}\_{t + 1}\\text{,}\\,\\mathbf{e}\_{1:t + 1}\\text{)~=}\\,\\underset{\\mathbf{x}\_{1:t}}{\\text{max}\\ }\\mathbf{P}\\text{(}\\mathbf{x}\_{1:t},\\,\\mathbf{X}\_{t + 1}\\text{,}\\,\\mathbf{e}\_{1:t}\\text{,}\\, e\_{t + 1}\\text{)}} \\\\ \\left. \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\,\\,\\underset{\\mathbf{x}\_{1:t}}{\\text{max}\\ }\\mathbf{P}\\text{(}\\mathbf{e}\_{t + \\, 1} \\middle| \\,\\mathbf{x}\_{1:t}\\text{,}\\,\\mathbf{X}\_{t + 1}\\text{,}\\,\\mathbf{e}\_{1:t}\\text{)}\\mathbf{P}\\text{(}\\mathbf{x}\_{1:t},\\,\\mathbf{X}\_{t + 1}\\text{,}\\,\\mathbf{e}\_{1:t}\\text{)}\\, \\right. \\\\ \\left. \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\,\\mathbf{P}\\text{(}e\_{t + 1} \\middle| \\mathbf{X}\_{t + 1})\\underset{\\mathbf{x}\_{1:t}}{\\max\\ }\\mathbf{P}(\\mathbf{X}\_{t + 1}, \\middle| \\,\\mathbf{x}\_{t})P(\\mathbf{x}\_{1:t},\\mathbf{e}\_{1:t}) \\right. \\\\ \\left. \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\,\\mathbf{P}\\text{(}e\_{t + 1} \\middle| \\mathbf{X}\_{t + 1})\\underset{\\mathbf{x}\_{t}}{\\max\\ }\\mathbf{P}(\\mathbf{X}\_{t + 1}, \\middle| \\,\\mathbf{x}\_{t})\\max\\limits\_{\\mathbf{x}\_{1:t..1}}P(\\mathbf{x}\_{1:t - 1},\\mathbf{x}\_{t},\\mathbf{e}\_{1:t})\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(14.11) \\right. \\\\ \\end{array}\\,\\,$
```

where the final term `max[x1:t−1] P(x[1:t−1], x[t], e[1:t])` is exactly the entry for the particular state `xt` in the message vector `m1:t`. [Equation (14.11)](#Chapter14-02.xhtml#eq14-11) is essentially identical to the filtering [equation (14.5)](#Chapter14-02.xhtml#eq14-5) except that the summation over `xt` in [Equation (14.5)](#Chapter14-02.xhtml#eq14-5) is replaced by the maximization over `xt` in [Equation (14.11)](#Chapter14-02.xhtml#eq14-11), and there is no normalization constant `a` in [Equation (14.11)](#Chapter14-02.xhtml#eq14-11). Thus, the algorithm for computing the most likely sequence is similar to filtering: it starts at time 0 with the prior `m1:0 = P(X0)` and then runs forward along the sequence, computing the `m` message at each time step using [Equation (14.11)](#Chapter14-02.xhtml#eq14-11). The progress of this computation is shown in [Figure 14.5(b)](#Chapter14-02.xhtml#fig14-5).

At the end of the observation sequence, `m1:t` will contain the probability for the most likely sequence reaching each of the final states. One can thus easily select the final state of the most likely sequence overall (the state outlined in bold at step 5). In order to identify the actual sequence, as opposed to just computing its probability, the algorithm will also need to record, for each state, the best state that leads to it; these are indicated by the bold arrows in [Figure 14.5(b)](#Chapter14-02.xhtml#fig14-5). The optimal sequence is identified by following these bold arrows backwards from the best final state.

The algorithm we have just described is called the `Viterbi algorithm`, after its inventor, Andrew Viterbi. Like the filtering algorithm, its time complexity is linear in `t`, the length of the sequence. Unlike filtering, which uses constant space, its space requirement is also linear in `t`. This is because the `Viterbi algorithm` needs to keep the pointers that identify the best sequence leading to each state.

> Viterbi algorithm

One final practical point: numerical underflow is a significant issue for the `Viterbi algorithm`. In [Figure 14.5(b)](#Chapter14-02.xhtml#fig14-5), the probabilities are getting smaller and smaller—and this is just a toy example. Real applications in DNA analysis or message decoding may have thousands or millions of steps. One possible solution is simply to normalize `m` at each step; this rescaling does not affect correctness because `max(cx, cy) = c ⋅ max(x,y)`. A second solution is to use log probabilities everywhere and replace multiplication by addition. Again, correctness is unaffected because the `log` function is monotonic, so `max(log x, log y) = log max(x, y)`.

## 14.3 Hidden Markov Models

The preceding section developed algorithms for temporal probabilistic reasoning using a general framework that was independent of the specific form of the transition and sensor models and independent of the nature of the state and evidence variables. In this and the next two sections, we discuss more concrete models and applications that illustrate the power of the basic algorithms and in some cases allow further improvements.

We begin with the hidden Markov model, or `HMM`. An `HMM` is a temporal probabilistic model in which the state of the process is described by a single, discrete random variable. The possible values of the variable are the possible states of the world. The umbrella example described in the preceding section is therefore an `HMM`, since it has just one state variable: `Raint`. What happens if you have a model with two or more state variables? You can still fit it into the `HMM` framework by combining the variables into a single “megavariable” whose values are all possible tuples of values of the individual state variables. We will see that the restricted structure of `HMMs` allows for a simple and elegant matrix implementation of all the basic algorithms.[6](#Chapter14-07.xhtml#sup14-6)

> Hidden Markov model

Although `HMMs` require the state to be a single, discrete variable, there is no corresponding restriction on the evidence variables. This is because the evidence variables are always observed, which means that there is no need to keep track of any distribution over their values. (If a variable is not observed, it can simply be dropped from the model for that time step.) There can be many evidence variables, both discrete and continuous.

### 14.3.1 Simplified matrix algorithms

With a single, discrete state variable `Xt`, we can give concrete form to the representations of the transition model, the sensor model, and the forward and backward messages. Let the state variable `Xt` have values denoted by integers `1,...,S`, where `S` is the number of possible states. The transition model `P(X[t] | X[t−1])` becomes an `S × S` matrix `T`, where

`T[i j]` = `P(X[t] = j | X[t−1] = i)`.

That is, `Tij` is the probability of a transition from state `i` to state `j`. For example, if we number the states `Rain = true` and `Rain = false` as `1` and `2`, respectively, then the transition matrix for the umbrella world defined in [Figure 14.2](#Chapter14-01.xhtml#fig14-2) is

```
$\\mathbf{T}\\,\\text{=~}\\mathbf{P}\\text{(}X\_{t}\\,\\text{|}\\, X\_{t - 1})\\, = \\,\\left( \\begin{matrix} 0.7 \\\\ 0.3 \\\\ \\end{matrix}\\,\\,\\begin{matrix} 0.3 \\\\ 0.7 \\\\ \\end{matrix} \\right)$
```

We also put the sensor model in matrix form. In this case, because the value of the evidence variable `Et` is known at time `t` (call it `et`), we need only specify, for each state, how likely it is that the state causes `et` to appear: we need `P(et | Xt = i)` for each state `i`. For mathematical convenience we place these values into an `S × S` diagonal observation matrix, `Ot`, one for each time step. The `i` th diagonal entry of `Ot` is `P(et | Xt = i)` and the other entries are `0`. For example, on day 1 in the umbrella world of [Figure 14.5](#Chapter14-02.xhtml#fig14-5), `U1 = true`, and on day 3, `U3 = false`, so we have

> Observation matrix

```
$\\text{O}\_{1} = \\left( \\begin{array}{l} 0.9 \\\\ {\\,\\,\\, 0} \\\\ \\end{array}\\,\\,\\begin{array}{l} {\\,\\, 0} \\\\ 0.2 \\\\ \\end{array} \\right);\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{O}\_{3} = \\left( \\begin{array}{l} 0.1 \\\\ {\\,\\, 0} \\\\ \\end{array}\\,\\,\\begin{array}{l} {\\,\\, 0} \\\\ 0.8 \\\\ \\end{array} \\right).$
```

Now, if we use column vectors to represent the forward and backward messages, all the computations become simple matrix-vector operations. The forward [equation (14.5)](#Chapter14-02.xhtml#eq14-5) becomes
