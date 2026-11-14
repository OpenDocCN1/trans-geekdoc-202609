# 5.3.6.3 NWJ lower bound

The BA lower bound requires a tractable normalized distribution $q(\boldsymbol{x}|\boldsymbol{y})$ that we can evaluate pointwise. If we reparameterize this distribution in a clever way, we can generate a lower bound that does not require a normalized distribution. Let’s write:

$q(\boldsymbol{x}|\boldsymbol{y}) = \frac{p(\boldsymbol{x})e^{f(\boldsymbol{x}, \boldsymbol{y})}}{Z(\boldsymbol{y})}$ (5.145)

with $Z(\boldsymbol{y}) = \mathbb{E}_{p(\boldsymbol{x})}[e^{f(\boldsymbol{x}, \boldsymbol{y})}]$ the normalization constant or partition function. Plugging this into the BA lower bound above we obtain:

$\mathbb{E}_{p(\boldsymbol{x}, \boldsymbol{y})} \left[ \log \frac{p(\boldsymbol{x})e^{f(\boldsymbol{x}, \boldsymbol{y})}}{p(\boldsymbol{x})Z(\boldsymbol{y})} \right] = \mathbb{E}_{p(\boldsymbol{x}, \boldsymbol{y})} [f(\boldsymbol{x}, \boldsymbol{y})] - \mathbb{E}_{p(\boldsymbol{y})} [\log Z(\boldsymbol{y})]$ (5.146)
$= \mathbb{E}_{p(\boldsymbol{x}, \boldsymbol{y})} [f(\boldsymbol{x}, \boldsymbol{y})] - \mathbb{E}_{p(\boldsymbol{y})} \left[ \log \mathbb{E}_{p(\boldsymbol{x})} [e^{f(\boldsymbol{x}, \boldsymbol{y})}] \right]$ (5.147)
$\triangleq I_{DV}(X; Y).$ (5.148)

This is the **Donsker-Varadhan** lower bound [DV75].

We can construct a more tractable version of this by using the fact that the log function can be upper bounded by a straight line using

$\log x \le \frac{x}{a} + \log a - 1$ (5.149)

If we set $a = e$, we get

$\mathbb{I}(X; Y) \ge \mathbb{E}_{p(\boldsymbol{x}, \boldsymbol{y})}[f(\boldsymbol{x}, \boldsymbol{y})] - e^{-1} \mathbb{E}_{p(\boldsymbol{y})} Z(\boldsymbol{y}) \triangleq I_{NWJ}(X; Y)$ (5.150)

This is called the **NWJ lower bound** (after the authors of Nguyen, Wainwright, and Jordan [NWJ10a]), or the f-GAN KL [NCT16a], or the MINE-f score [Bel+18].

# 5.3.6.4 InfoNCE lower bound

If we instead explore a multi-sample extension to the DV bound above, we can generate the following lower bound (see [Poo+19b] for the derivation):

$\mathbb{I}_{\text{NCE}} = \mathbb{E} \left[ \frac{1}{K} \sum_{i=1}^K \log \frac{e^{f(\boldsymbol{x}_i, \boldsymbol{y}_i)}}{\frac{1}{K} \sum_{j=1}^K e^{f(\boldsymbol{x}_j, \boldsymbol{y}_i)}} \right]$ (5.151)
$= \log K - \mathbb{E} \left[ \frac{1}{K} \sum_{i=1}^K \log \left( 1 + \sum_{j \neq i} e^{f(\boldsymbol{x}_j, \boldsymbol{y}_i) - f(\boldsymbol{x}_i, \boldsymbol{y}_i)} \right) \right]$ (5.152)

where the expectation is over paired samples from the joint $p(X, Y)$. The quantity in Equation (5.152) is called the **InfoNCE** estimate, and was proposed in [OLV18a; Hen+19a]. (NCE stands for “noise contrastive estimation”, and is discussed in Section 24.4.)

The intuition here is that mutual information is a divergence between the joint $p(\boldsymbol{x}, \boldsymbol{y})$ and the product of the marginals, $p(\boldsymbol{x})p(\boldsymbol{y})$. In other words, mutual information is a measurement of how