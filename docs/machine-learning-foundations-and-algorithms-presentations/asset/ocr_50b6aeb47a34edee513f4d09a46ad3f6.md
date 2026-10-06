# # Variational Inference for Bayesian Learning

## Reformulated as maximization problem:

$$\text{argmin}_q KL(q(	heta)||p(	heta|\mathcal{D})) = 	ext{argmax}_q \int_{	heta} q(	heta) \log p(\mathcal{D}|	heta) d	heta - KL(q(	heta)||p(	heta))$$

+   - We need to find distribution q with samples that have high likelihood...

+   - ... and q should be close to prior