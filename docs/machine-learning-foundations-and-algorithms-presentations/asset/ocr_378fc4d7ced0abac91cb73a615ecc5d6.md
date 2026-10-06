# # Log-Likelihood

We can now directly optimize the conditional Bernoulli log-likelihood

$$	ext{loglik}(	ilde{oldsymbol{w}}, D) = \sum_{i} \log p(c_i|oldsymbol{x}_i) = \sum_{i} \log p(c=1|oldsymbol{x}_i)^{c_i} p(c=0|oldsymbol{x}_i)^{1-c_i}$$
$= \sum_{i} c_i \log p(c=1|oldsymbol{x}_i) + (1-c_i) \log p(c=0|oldsymbol{x}_i)$$
$= \sum_{i} c_i \log \sigma(	ilde{oldsymbol{w}}^T	ilde{oldsymbol{x}}_i) + (1-c_i) \log (1-\sigma(	ilde{oldsymbol{w}}^T	ilde{oldsymbol{x}}_i))$$

+   - Negative likelihood is also often referred to as cross-entropy loss