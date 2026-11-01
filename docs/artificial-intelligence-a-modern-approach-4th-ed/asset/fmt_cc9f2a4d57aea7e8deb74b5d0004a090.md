
## 14.2 Prediction and Filtering

$\\begin{array}{l} \\left. \\mathbf{P}(R\_{1}\\text{|}\\,\\, u\_{1}\\,)\\,\\,\\, = \\,\\alpha\\,\\mathbf{P}\\text{(}u\_{1} \\middle| R\_{1}\\text{)}\\mathbf{P}\\text{(}R\_{1}\\text{)~=~}\\alpha\\,\\left\\langle \\text{0}\\text{.9,0}\\text{.2} \\right\\rangle\\,\\left\\langle \\text{0}\\text{.5,0}\\text{.5} \\right\\rangle\\text{.}\\, \\right. \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\,\\alpha\\,\\left\\langle \\text{0}\\text{.45,0}\\text{.1} \\right\\rangle\\ \\approx \\ \\left\\langle \\text{0}\\text{.818,0}\\text{.182} \\right\\rangle.\\ } \\\\ \\end{array}$

•On day 2, the umbrella appears, so `U2 = true`. The prediction from `t = 1` to `t = 2` is

$\\begin{array}{l} {\\mathbf{P}(R\_{2}\\text{|}\\,\\, u\_{1}\\,)\\,\\,\\, = \\,{\\sum\\limits\_{r\_{1}}\\left. \\mathbf{P}(R\_{2} \\middle| r\_{1})P(r\_{1} \\middle| u\_{1}) \\right.}\\,} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\,\\left\\langle \\text{0}\\text{.7,0}\\text{.3} \\right\\rangle\\, \\times \\text{0}\\text{.818}\\,\\text{+}\\,\\left\\langle \\text{0}\\text{.3,0}\\text{.7} \\right\\rangle\\, \\times \\text{0}\\text{.182~} \\approx \\ \\left\\langle \\text{0}\\text{.627,0}\\text{.373} \\right\\rangle,\\ } \\\\ \\end{array}$

and updating it with the evidence for `t = 2` gives

$\\begin{array}{l} \\left. \\mathbf{P}(R\_{2}\\text{|}\\,\\, u\_{1},u\_{2}\\,)\\,\\,\\, = \\alpha\\,\\mathbf{P}\\text{(}u\_{2} \\middle| R\_{2})\\mathbf{P}(R\_{2} \\middle| u\_{1}\\text{)~=~}\\alpha\\,\\left\\langle \\text{0}\\text{.9,0}\\text{.2} \\right\\rangle\\,\\left\\langle \\text{0}\\text{.627,0}\\text{.373} \\right\\rangle\\, \\right. \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\,\\alpha\\,\\left\\langle \\text{0}\\text{.565,0}\\text{.07}5 \\right\\rangle\\,\\, \\approx \\ \\left\\langle \\text{0}\\text{.883,0}\\text{.117} \\right\\rangle.\\ } \\\\ \\end{array}$

Intuitively, the probability of rain increases from day 1 to day 2 because rain persists. Exercise `14.CONV(a)` asks you to investigate this tendency further.

The task of prediction can be seen simply as filtering without the addition of new evidence. In fact, the filtering process already incorporates a one-step prediction, and it is easy to derive the following recursive computation for predicting the state at `t + k + 1` from a prediction for `t + k`:

$\\begin{matrix} {\\mathbf{P}(\\mathbf{X}\_{t + k + 1}\\,\\text{|}\\,\\mathbf{e}\_{\\text{1:}t}) = {\\sum\\limits\_{\\mathbf{x}\_{t + k}}\\underset{\\text{transition~model}}{\\underset{︸}{\\left. \\mathbf{P}(\\mathbf{X}\_{t + k + 1} \\middle| \\mathbf{x}\_{t + k}) \\right.}}}\\underset{\\text{recursion}}{\\underset{︸}{\\left. P(\\mathbf{x}\_{t + k} \\middle| \\mathbf{e}\_{1:t} \\right.}}.} & {\\,\\,\\,\\,\\,\\text{(14}\\text{.6)}} \\\\ \\end{matrix}$

Naturally, this computation involves only the transition model and not the sensor model.

It is interesting to consider what happens as we try to predict further and further into the future. As Exercise `14.CONV(b)` shows, the predicted distribution for rain converges to a fixed point 〈0.5,0.5〉, after which it remains constant for all time.[4](#Chapter14-07.xhtml#sup14-4) This is the stationary distribution of the Markov process defined by the transition model. (See also [page 462](#Chapter13-04.xhtml#page_462).) A great deal is known about the properties of such distributions and about the mixing time— roughly, the time taken to reach the fixed point. In practical terms, this dooms to failure any attempt to predict the actual state for a number of steps that is more than a small fraction of the mixing time, unless the stationary distribution itself is strongly peaked in a small area of the state space. The more uncertainty there is in the transition model, the shorter will be the mixing time and the more the future is obscured.

> Mixing time

In addition to filtering and prediction, we can use a forward recursion to compute the likelihood of the evidence sequence, `P(e1:t)`. This is a useful quantity if we want to compare different temporal models that might have produced the same evidence sequence (e.g., two different models for the persistence of rain). For this recursion, we use a likelihood message `ℓ1:t(Xt) = P(Xt,e1:t)`. It is easy to show (Exercise `14.LIKL`) that the message calculation is identical to that for filtering:

`ℓ[1 : t + 1] = FORWARD(ℓ[1 : t], e[t + 1])`.

Having computed `ℓ1:t`, we obtain the actual likelihood by summing out `Xt`:

$\\begin{matrix} {L\_{\\text{1:}t}\\text{~=~}P\\text{(}\\mathbf{e}\_{1:t}\\text{)} = {\\sum\\limits\_{\\mathbf{x}\_{t}}{\\mathcal{l}\_{1:t}(\\mathbf{X}\_{t}).}}} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(14}\\text{.7)}} \\\\ \\end{matrix}$

Notice that the likelihood message represents the probabilities of longer and longer evidence sequences as time goes by and so becomes numerically smaller and smaller, leading to underflow problems with floating-point arithmetic. This is an important problem in practice, but we shall not go into solutions here.

## 14.2.2 Smoothing

As we said earlier, smoothing is the process of computing the distribution over past states given evidence up to the present—that is, `P(Xk|e1:t)` for `0 ≤ k < t`. (See [Figure 14.3](#Chapter14-02.xhtml#fig14-3).) In anticipation of another recursive message-passing approach, we can split the computation into two parts—the evidence up to `k` and the evidence from `k + 1` to `t`,

$\\begin{array}{l} {\\text{P(}\\mathbf{X}\_{k}\\,\\text{|}\\,\\mathbf{e}\_{1:t}\\text{)}} \\\\ \\\\ \\\\ \\\\ \\end{array}\\,\\,\\,\\,\\begin{array}{l} \\left. = \\,\\mathbf{P}\\text{(}\\mathbf{X}\_{k} \\middle| \\mathbf{e}\_{1:k}\\text{,}\\mathbf{e}\_{k + 1:t}\\text{)} \\right. \\\\ \\left. = \\,\\alpha\\,\\mathbf{P}(\\mathbf{X}\_{k} \\middle| \\,\\mathbf{e}\_{1:k})\\mathbf{P}(\\mathbf{e}\_{k + 1:t} \\middle| \\mathbf{X}\_{k},\\mathbf{e}\_{1:k})\\,\\,\\,\\,\\,\\,\\text{(using~Bayes}'\\text{s}\\,\\text{rule,~given~}\\mathbf{e}\_{1:k}\\text{)} \\right. \\\\ \\left. = \\,\\alpha\\,\\mathbf{P}(\\mathbf{X}\_{k} \\middle| \\,\\mathbf{e}\_{1:k})\\mathbf{P}(\\mathbf{e}\_{k + 1:t} \\middle| \\mathbf{X}\_{k})\\,\\,\\,\\,\\,\\,\\text{(using~conditional~independence)} \\right. \\\\ {= \\,\\alpha\\,\\mathbf{f}\_{1:k} \\times \\mathbf{b}\_{k + 1:t}\\ \\text{.}} \\\\ \\end{array}\\,\\,\\,\\begin{array}{l} \\\\ \\\\ \\\\ {(14.8)} \\\\ \\end{array}$

where “×” represents pointwise multiplication of vectors. Here we have defined a “back-ward” message `bk+1:t = P(ek+1:t | Xk)`, analogous to the forward message `f1:k`. The forward message `f1:k` can be computed by filtering forward from 1 to `k`, as given by [Equation (14.5)](#Chapter14-02.xhtml#eq14-5). It turns out that the backward message `bk+1:t` can be computed by a recursive process that runs backward from `t`:
