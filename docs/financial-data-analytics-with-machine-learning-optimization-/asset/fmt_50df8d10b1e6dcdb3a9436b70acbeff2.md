
Consider the simple case when both input `x` and output `y` are in `ℝ`, and the functional relation between `x` and `y` is `y = f(x)`, such as in [Figure 15.14](#c15.xhtml#c15-fig-0014)a, for example. We approximate this function by a step function (see [Figure 15.14](#c15.xhtml#c15-fig-0014)b), such that each “step” can be considered as a simple function of the form `𝟙[xᵢ, xᵢ₊₁]`, for some `xᵢ < xᵢ₊₁`. The linear combination of these simple functions clearly can approximate `f` arbitrarily well by reducing the mesh size of the underlying partition of the real line.

![FIGURE 15.14 Illustration of approximating a function by simple functions.](images/c15f014.png)

[**FIGURE 15.14**](#c15.xhtml#R_c15-fig-0014) Illustration of approximating a function by simple functions.

Consider two sigmoid functions `h₁` and `h₂` with very steep slopes such that for a small `δ > 0`, `h₁` stays at 0 for any `x ≤ −δ`, but reaches 1 linearly at `x = −δ / 2`, and it remains constant thereafter. Similarly, `h₂` stays at 0 for any `x ≤ δ / 2`, but reaches 1 at `x = δ` and remains constant thereafter, as seen in [Figures 15.15](#c15.xhtml#c15-fig-0015)a and [15.15](#c15.xhtml#c15-fig-0015)b. Then the function `h := h₁ − h₂` can approximately give us any one of the simple functions in [Figure 15.14](#c15.xhtml#c15-fig-0014)b as desired, as [Figure 15.15](#c15.xhtml#c15-fig-0015)c shows.

![FIGURE 15.15 Construction of a simple function.](images/c15f015.png)

[**FIGURE 15.15**](#c15.xhtml#R_c15-fig-0015) Construction of a simple function.

Hence, for an input `x` being passed into two sigmoid neurons with respective activation functions `h₁` and `h₂`, if we apply the weights `+1` and `−1` to them in the neuron in the next layer, we can obtain the desired approximation for one simple function. By combining several similar components, as in [Figure 15.16](#c15.xhtml#c15-fig-0016), we can approximate an arbitrary function `f`. Finally, note that by properly scaling the domain for the logistic or hyperbolic tangent function, either one can also well approximate `h₁` or `h₂`. Therefore, the claim of the theorem follows, and this in some sense justifies the effective `representational power of deep neural networks` in general.

![FIGURE 15.16 A component in an ANN used to construct a rectangular partition.](images/c15f016.png)

[**FIGURE 15.16**](#c15.xhtml#R_c15-fig-0016) A component in an ANN used to construct a rectangular partition.

## 15.9 LONG SHORT‐TERM MEMORY (LSTM)

`Long Short‐Term Memory` (LSTM) model is a kind of `recurrent neural network` (RNN). This DNN was designed to learn and store long‐term dependencies in temporal sequences. It was first introduced by Hochreiter and Schmidhuber [[10](#c15.xhtml#c15-bib-0010)]. Since then, LSTM has been widely used in various sequence‐to‐sequence tasks, such as natural language processing, speech recognition, and time series prediction; also see [[6](#c15.xhtml#c15-bib-0006), [11](#c15.xhtml#c15-bib-0011), [15](#c15.xhtml#c15-bib-0015), [22](#c15.xhtml#c15-bib-0022)].

The key ingredient in LSTM is the use of memory cells which enable the network to learn and remember long‐term dependencies. Each memory cell consists of three main components: an input gate, a forget gate, and an output gate; see [Figure 15.17](#c15.xhtml#c15-fig-0017) and more information in [[10](#c15.xhtml#c15-bib-0010)]. These gates control the flow of information within the cell, allowing the cell to selectively store, update, and retrieve information from its internal state. This gating mechanism helps to mitigate the `vanishing gradient problem`, which is a common issue in traditional RNNs [[2](#c15.xhtml#c15-bib-0002)]. The input gate determines the extent to which new input data is stored in the cell state. The forget gate decides which parts of the cell state should be forgotten or retained, allowing the network to learn when to discard irrelevant information. Finally, the output gate controls the output of the cell based on its current state; more discussions can be found in [[7](#c15.xhtml#c15-bib-0007), [10](#c15.xhtml#c15-bib-0010), [23](#c15.xhtml#c15-bib-0023)].

![FIGURE 15.17 A standard LSTM memory cell; also see [20].](images/c15f017.png)
