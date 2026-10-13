
Figure 19.16 Generic scheme for pretext tasks: The upper branch feeds the encoder, `f[θ](⋅)`, and the projector/predictor, `g[ϕ](⋅)`, generates predictions to predict the targets/pseudo labels. The latter are generated in the lower branch. Dotted boxes are optional. During training, via backpropagation, the involved parameters are adjusted to minimize the cost function that quantifies deviation between the targets, `𝒯`, and their corresponding predictions, `T̂`. When `g[ξ]'(⋅)` is employed, the updating of the corresponding parameters may need special attention. In some cases, `g[ϕ](⋅)` and `g[ξ]'(⋅)` may be implemented as a serial connection of two sub-networks.

1.  

2. **2.** Generate a corresponding set of target values (pseudo labels), `𝒯`, from the set `𝒳`, via a transformation process, `P`, i.e.,

```
𝒯 = P(𝒳).
```

1. For example, `𝒯` could comprise the one-hot vector representations of the masked tokens in BERT. In the case of GPT, `𝒯` would consist of the one-hot vector representations of the next word to be predicted at each time instant. Let us assume that, in general, `𝒯` comprises `m` vectors/targets, i.e., `𝒯 = {t[1], t[2], …, t[m]}`. Needless to say that `m = 1` is a special case that is commonly encountered in practice. The action of `P` on the input data, `𝒳`, is schematically shown by the lower branch in [Fig. 19.16](#Chp019_997-1102_B9780443292385000251.xhtml#f0085), and it corresponds to the box “Transform #2.” Note that in the figure a second (nonlinear) network, denoted by `g[ξ]'(⋅)`, parameterized in terms of another set of parameters, `ξ`, may be optionally used (for reasons that we see later on) to provide the final targets, `𝒯`.

2. **3.** A decoder, often referred to as the predictor, the predictor head, or the projector is selected (e.g., a feed-forward neural network) that maps the `N` encoded outputs of the encoder, `ℋ`, into `m` target estimates, `T̂ = {t̂_1, t̂_2, …, t̂_m}`, i.e.,

```
T̂ = g_ϕ(ℋ),
```

1. where `ϕ` is the set of parameters that define the projector/predictor network. For example, in the case of GPT and BERT, the predictor comprises the extra networks on top of the last transformer block, which converts the outputs to probability vectors.
