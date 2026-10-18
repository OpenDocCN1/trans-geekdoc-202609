

Empirical evidence in [\[12\]](#c15.xhtml#c15-bib-0012) argues that the performance is the best when both `β₁` and `β₂` are close enough to 1. To tackle the possibility that `mᵢ(t)` and `vᵢ(t)` are biased towards 0 due to zero values initially set, the update in ([15.5](#c15.xhtml#c15-disp-0012)) can be replaced by

(15.6)`wᵢ(t+1) Baseline = wᵢ(t) Baseline − η / (√v̂ᵢ(t) Baseline + ε) m̂ᵢ(t) Baseline`

where

`m̂ᵢ(t) = mᵢ(t) / (1 − β₁)` and `v̂ᵢ(t) = vᵢ(t) / (1 − β₂)`

## 15.6 TRAINING NEURAL NETWORKS VIA BACKPROPAGATION

As seen in [Section 15.3](#c15.xhtml#c15-sec-0004), training a neural network is equivalent to finding the appropriate weight parameter `w` such that the loss function `E = 1/2 (y − o′)² (y − o′)` is minimized, and this is achieved by using a backpropagation algorithm. Let us illustrate this approach by a simple 2‐2‐1 ANN with a linear output; also see [Figure 15.8](#c15.xhtml#c15-fig-0008) for an illustration.

Suppose the four sample input vectors, the target vector of the labels and the initial weights are as follows:

