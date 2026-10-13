

设 $\mathcal{X}$ 为观测变量集合，$\mathcal{X}^{(l)}$ 为与图结构节点相关的隐随机变量集合；在图模型术语中，我们可以分别将它们称为证据节点和隐节点。定义

$$
\mathcal{F}(Q) = \sum_{x \in \mathcal{X}^{l}}Q(\mathcal{X}^{l})\ln\frac{P(\mathcal{X},\mathcal{X}^{l})}{Q(\mathcal{X}^{l})},
$$

其中 $Q$ 为任意概率函数。然后，由式 (16.15) 可直接得到

$$
\mathcal{F}(Q) = \ln P(\mathcal{X}) + \sum_{x \in \mathcal{X}^{l}}Q(\mathcal{X}^{l})\ln\frac{P(\mathcal{X}^{l}|\mathcal{X})}{Q(\mathcal{X}^{l})},
$$

或

$$
\ln P(\mathcal{X}) = \mathcal{F}(Q) + \sum_{x \in \mathcal{X}^{l}}Q(\mathcal{X}^{l})\ln\frac{Q(\mathcal{X}^{l})}{P(\mathcal{X}^{l}|\mathcal{X})}.
$$

注意式 (16.16) 中的第二项是 $P(\mathcal{X}^{(l)}|\mathcal{X})$ 与 $Q(\mathcal{X}^{(l)})$ 之间的 Kullback-Leibler (KL) 散度。因为 KL 散度总是非负的（问题 12.7），我们可以写成

$$
\ln P(\mathcal{X}) \geq \mathcal{F}(Q),
$$

若我们最小化 KL 散度，则下界取得最大值。

