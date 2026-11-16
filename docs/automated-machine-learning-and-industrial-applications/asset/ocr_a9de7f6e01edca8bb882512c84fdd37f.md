$$\mathbb{E}[\| x^k - x(\lambda) \|^2] \leq \varepsilon \| x^0 - x(\lambda) \|^2 + \frac{2na\sigma^2}{\mu} (2.7)$$

The number of predicted communications and iterations needed to reach 10 are both decreased by the setting \(p^* = \frac{\lambda}{L+\lambda}\). Mainly, the desired iteration count and anticipated communication count are \(2 \frac{L+\lambda}{\mu} \log \frac{1}{\varepsilon}\) and \(\frac{2\lambda}{\lambda+L} \frac{L}{\mu} \log \frac{1}{\varepsilon}\) correspondingly. To make the output image almost equal to the original, we use relativistic average discriminator DRa. Objective processes by Equations 2.8–2.11 are as follows:

$$\mathcal{L}_{Ra\_D} = -\mathbb{E}_x [\log(D_{Ra}(x))] - \mathbb{E}_{x,v,<} [\log(1 - D_{Ra}(G(x,v,c)))] (2.8)$$

$$\mathcal{L}_{Ra\_G} = -\mathbb{E}_{x,D,} [\log(D_{Ra}(G(x,v,c)))] - \mathbb{E}_x [\log(1 - D_{Ra}(x))] (2.9)$$

$$D_{Ra}(x) = \text{sigmoid}(H(x) - \mathbb{E}_{x,v,c} [H(G(x,v,c))]) (2.10)$$

$$D_{Ra}(G(x,v,c)) = \text{sigmoid}(H(G(x,v,c)) - \mathbb{E}_x [H(x)]) (2.11)$$

The non-transformed layer's output is represented by the notation H(●). By reducing the loss of LR a G, the generated image tends to be more realistic than the original. We introduce a cycle consistency loss to the generator, as described in Equation 2.12:

$$\mathcal{L}_{cyc} = \mathbb{E}_{x,v,\epsilon} [\| x - G(G(x,v,c), v, 1 - c) \|_1] (2.12)$$