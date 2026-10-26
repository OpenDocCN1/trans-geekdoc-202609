# Sigmoid Belief Networks:
Learning and Inference

![](bbox=[0.02, 0.04, 0.08, 0.17])

+   - Neal proposed Monte Carlo methods for learning and inference (Neal, 1992):
+   - Approximated with Gibbs sampling
+   - Conditional distributions:
+     $P(S_i = x \mid S_j = s_j : j \neq i)$
+     $\propto \sigma\left(x^* \sum_{j<i} s_j w_{ij}\right) \prod_{j>i} \sigma\left(s_j^*\left(x w_{ji} + \sum_{k<j, k\neq i} s_k w_{jk}\right)\right)$
+   - No negative phase as in RBM!
+   - Convergence is very slow, especially for large belief nets, due to the intricate “explain-away” effects...

Equations from Neal, 1992

$\frac{\partial L}{\partial w_{ij}} = \sum_{\tilde{v}\in T} \frac{1}{P(\tilde{V}=\tilde{v})} \frac{\partial P(\tilde{V}=\tilde{v})}{\partial w_{ij}}$ 
$= \sum_{\tilde{v}\in T} \frac{1}{P(\tilde{V}=\tilde{v})} \sum_{\tilde{h}} \frac{\partial P(\tilde{S}=\langle\tilde{h},\tilde{v}\rangle)}{\partial w_{ij}}$ 
$= \sum_{\tilde{v}\in T} \sum_{\tilde{h}} P(\tilde{S}=\langle\tilde{h},\tilde{v}\rangle \mid \tilde{V}=\tilde{v}) \cdot \frac{1}{P(\tilde{S}=\langle\tilde{h},\tilde{v}\rangle)} \frac{\partial P(\tilde{S}=\langle\tilde{h},\tilde{v}\rangle)}{\partial w_{ij}}$ 
$= \sum_{\tilde{v}\in T} \sum_{\tilde{s}} P(\tilde{S}=\tilde{s} \mid \tilde{V}=\tilde{v}) \frac{1}{P(\tilde{S}=\tilde{s})} \frac{\partial P(\tilde{S}=\tilde{s})}{\partial w_{ij}}$ 
$= \sum_{\tilde{v}\in T} \sum_{\tilde{s}} P(\tilde{S}=\tilde{s} \mid \tilde{V}=\tilde{v}) \frac{1}{\sigma\left(s_i^* \sum_{k<i} s_k w_{ik}\right)} \frac{\partial \sigma\left(s_i^* \sum_{k<i} s_k w_{ik}\right)}{\partial w_{ij}}$ 
$= \sum_{\tilde{v}\in T} \sum_{\tilde{s}} P(\tilde{S}=\tilde{s} \mid \tilde{V}=\tilde{v}) s_i^* s_j \sigma\left(-s_i^* \sum_{k<i} s_k w_{ik}\right).$

log derivative

prob. of the visibles via marginalization

Bayes rule + rearrange sums

Plug-in the actual sigmoid form of the conditional prob.