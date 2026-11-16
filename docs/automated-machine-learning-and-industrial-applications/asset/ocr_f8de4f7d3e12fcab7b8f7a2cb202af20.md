```
\(\hat{x}^{[\alpha]} = \gamma_{(W^\prime, b^\prime)}\big(h_{(W, b)}\big(x^{[\alpha]}\big)\big) \equiv x^{[\alpha]}\) (8.9)
```

Other names for this include an encoder or a recognition technique. By optimizing the variational parameter \(\varphi\), Equation 8.10 is satisfied.

```
\(q_\varphi(\mathbf{z} \mid \mathbf{x}) \approx p_\theta(\mathbf{z} \mid \mathbf{x})\) (8.10)
```

The inference method is (almost) any directed graphical technique according to Equation 8.11:

```
\(q_\phi(\mathbf{z} \mid \mathbf{x}) = q_\phi(\mathbf{z}_1, ..., \mathbf{z}_M \mid \mathbf{x}) = \prod_{j=1}^M q_\phi(\mathbf{z}_j \mid Pa(\mathbf{z}_j), \mathbf{x})\) (8.11)
```

Every layer of a DBN is constructed as an RBM, so training its layers is identical to training an RBM. Classification is accomplished by initializing a network using DBN training using Equation 8.12.

```
\(\min_{\sigma_k} \frac{1}{|D|} \sum_{i=1}^{|D|} [-\log p\left(x_k^{(0)}; \theta_k\right)]_{\theta_k}\) (8.12)
```

Remember that layer-wise updating necessitates correcting all problems starting from the bottom hidden layer and working our way up to the top visible layer. We solve the optimization issue for the fine-tuning phase using Equation 8.13.

```
\(\min_\phi \frac{1}{D} \sum_{i=1}^{|D|} \left[\mathcal{L}\left(\phi; y^{(i)}, h\left(x^{(0)}\right)\right)\right]_{h(x^{(0)})} = h(x_i^{(i)})\) (8.13)
```

This method uses a two-phase training procedure simultaneously, but we still need to add one more hyperparameter to balance the relative weights of the two goals. The method (DBN + loss) is given as Equation 8.14:

```
\(\min_{\theta_{L,i}, \theta_{DNN}} \mathbb{E}_{\mathbf{x}}[\mathcal{L}(\theta_L;\mathbf{y}, h(\mathbf{x}))] + p \mathbb{E}_{\mathbf{x}}[-\log p(\mathbf{x}; \theta_{DAN})]\)
\(\min_{\theta_L, \theta_{DAN}} \frac{1}{D} \sum_{i=1}^{|D|} [\mathcal{L}(\theta_L; y^{(i)}, h(x^{(i)})) - \rho \log p(x^{(i)}; \theta_{DBN})]_{\theta_L}\) (8.14)
```