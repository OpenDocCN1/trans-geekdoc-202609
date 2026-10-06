# Appendix: Derivation of the Bias-Variance Trade-off 2/2

$R(\hat{f}_{D_n}) = \mathbb{E}_{x,y,D_n}\left[(\hat{f}_{D_n}(\boldsymbol{x}) - \mathbb{E}_{D_n}[\hat{f}_{D_n}(\boldsymbol{x})]^2\right]_{\text{variance}} + \mathbb{E}_{x,y,D_n}\left[\left(\mathbb{E}_{D_n}[\hat{f}_{D_n}(\boldsymbol{x})] - y\right)^2\right]$

$2^{\{nd}}$ term:

$\mathbb{E}_{x,y,D_n}\left[\left(\mathbb{E}_{D_n}[\hat{f}_{D_n}(\boldsymbol{x})] - y\right)^2\right] = \mathbb{E}_{x,y}\left[\left(\mathbb{E}_{D_n}[\hat{f}_{D_n}(\boldsymbol{x})] - f(\boldsymbol{x}) - \epsilon\right)^2\right]$\n= \mathbb{E}_{x,y}\left[\left(\mathbb{E}_{D_n}[\hat{f}_{D_n}(\boldsymbol{x})] - f(\boldsymbol{x})\right)^2\right]_{\text{bias}^2} + \mathbb{E}_{x,y}\left[\epsilon^2\right]_{\text{noise}} - 2\mathbb{E}_{x,y}\left[\epsilon(\hat{f}_{D_n}(\boldsymbol{x}) - f(\boldsymbol{x}))\right]_{\text{0 due to zero mean i.i.d noise}}$