
如前所述，没有常用的单一 Copula 能实现这一目标。因此，本节旨在通过合理混合若干单一 Copula 来提出该问题的解决方案。

如表 38.2 所示，候选 Copula 包括四种流行的 Copula，即高斯 Copula、t Copula、Gumbel Copula 和 Clayton Copula。这些 Copula 各有优缺点，分别用符号“√”和“×”表示。Frank Copula 被排除在外，因为它相对于另外四种 Copula 没有任何优势。混合 Copula 嵌套了其组成 Copula 的依赖结构。在这种情况下，Copula 的混合是其特征捕捉能力的组合。例如，如果一个 Copula 在某项特征上为“×”，另一个 Copula 在该特征上为“√”，则它们的混合在该特征上也将为“√”。因此，通过仔细选择组成 Copula，可以构造出全部为“√”的混合 Copula。

### (1) t-Gumbel Copula

在这些候选 Copula 中，我们首先选择 t Copula，因为它可以捕捉大多数类型的特征。表 38.2 中唯一的“×”显示了其唯一的弱点，即尾部不对称。因此，能够捕捉尾部不对称的 Copula 将成为一个很好的搭档。如表 38.2 所示，Clayton Copula 和 Gumbel Copula 分别对下尾和上尾相关性具有高度敏感性，在尾部不对称行中被标记为“√”。当银行风险处于极端大值时，通常会观察到显著更强的依赖性，因此最终选择了 Gumbel Copula。t Copula 与 Gumbel Copula 的混合预计能够捕捉银行风险依赖性的所有典型特征。它被称为 t-Gumbel Copula，定义为式 (38.2)。

$$C_{\mathrm{t\text{-}Gumbel}}(u_1, u_2, \ldots, u_n \mid w_t, w_{Gu}, \nu, R, \alpha) = w_t C_t(u_1, u_2, \ldots, u_n \mid \nu, R) + w_{Gu} C_{\mathrm{Gumbel}}(u_1, u_2, \ldots, u_n \mid \alpha), \tag{38.2}$$

其中 \(w_t, w_{Gu} \in [0,1]\) 且 \(w_t + w_{Gu} = 1\)。参数 \((\nu, R, \alpha)\) 是反映依赖程度的关联参数，而 \((w_t, w_{Gu})\) 是反映依赖结构的权重参数。

根据 Nelsen (1999)，就 Copula \(C\) 而言，上尾和下尾相关系数 \(\lambda^U\) 和 \(\lambda^L\) 为：

\[
\lambda^U = \lim_{u\to 1} \frac{1 - 2u + C(u,u,\ldots,u)}{1-u}, \tag{38.3}
\]

\[
\lambda^L = \lim_{u\to 0} \frac{C(u,u,\ldots,u)}{u}. \tag{38.4}
\]

**表 38.2：构建的混合 Copula 及其捕捉风险依赖特征的能力。**

| 风险依赖的主要特征 | 候选个体 Copula：高斯 | 候选个体 Copula：t | 候选个体 Copula：Gumbel | 候选个体 Copula：Clayton | 混合 Copula：t-Gumbel | 混合 Copula：Gaussian-Gumbel | 混合 Copula：Gaussian-Gumbel-Clayton |
|---|---|---|---|---|---|---|---|
| 非线性依赖 正 | √ | √ | √ | √ | √ | √ | √ |
| 非线性依赖 负 | √ | √ | × | × | √ | √ | √ |
| 尾部行为 尾部相关 上 | × | √ | √ | × | √ | √ | √ |
| 尾部行为 尾部相关 下 | × | √ | × | √ | √ | × | √ |
| 尾部行为 尾部不对称 | × | × | √ | √ | √ | √ | √ |
| 结构不对称 | √ | √ | × | × | √ | √ | √ |

注：符号“√”表示该方法可以捕捉相应特征，符号“×”表示该方法无法捕捉相应特征。

因此，t-Gumbel Copula 的上尾和下尾相关系数 \(\lambda_{t-\text{Gumbel}}^U\) 和 \(\lambda_{t-\text{Gumbel}}^L\) 可推导如下。

\[
\begin{aligned}
\lambda_{t-\text{Gumbel}}^U
&= \lim_{u\to1} \frac{1 - 2u + C_{t-\text{Gumbel}}(u,u,\ldots,u)}{1 - u}, \tag{38.5}\\
&= \lim_{u\to1} \frac{1 - 2u + w_t C_t(u,u,\ldots,u) + w_{Gu} C_{\text{Gumbel}}(u,u,\ldots,u)}{1 - u}, \tag{38.6}\\
&= w_t \lim_{u\to1} \frac{1 - 2u + C_t(u,u,\ldots,u)}{1 - u} + w_{Gu} \lim_{u\to1} \frac{1 - 2u + C_{\text{Gumbel}}(u,u,\ldots,u)}{1 - u}, \tag{38.7}\\
&= w_t \lambda_t^U + w_{Gu} \lambda_{Gu}^U, \tag{38.8}\\
&= w_t \lambda_t^U + w_{Gu} \cdot \left(2 - 2^{1/\alpha}\right), \tag{38.9}
\end{aligned}
\]

\[
\begin{aligned}
\lambda_{t-\text{Gumbel}}^L
&= \lim_{u\to0} \frac{C_{t-\text{Gumbel}}(u,u,\ldots,u)}{u}, \tag{38.10}\\
&= \lim_{u\to0} \frac{w_t C_t(u,u,\ldots,u) + w_{Gu} C_{\text{Gumbel}}(u,u,\ldots,u)}{u}, \tag{38.11}\\
&= w_t \lim_{u\to0} \frac{C_t(u,u,\ldots,u)}{u} + w_{Gu} \lim_{u\to0} \frac{C_{\text{Gumbel}}(u,u,\ldots,u)}{u}, \tag{38.12}\\
&= w_t \lambda_t^L + w_{Gu} \lambda_{Gu}^L, \tag{38.13}\\
&= w_t \cdot \lambda_t^L, \tag{38.14}
\end{aligned}
\]

其中 \(\lambda_t^U\) 和 \(\lambda_t^L\) 分别是 t Copula 的上尾和下尾相关系数，而 \(\lambda_{Gu}^U\) 和 \(\lambda_{Gu}^L\) 分别是 Gumbel Copula 的上尾和下尾相关系数。\(\lambda_t^U\) 和 \(\lambda_t^L\) 的复杂表达式可参见 Nikoloulopoulos et al. (2009)。如式 (38.9) 和 (38.14) 所示，t-Gumbel Copula 既可捕捉上尾也可捕捉下尾相关性，且上尾相关性强于下尾相关性。

### (2) Gaussian–Gumbel copula

高斯 Copula 已被充分理解，并在多种应用中得到检验，直到其无法描述尾部行为的局限性被完全认识到。为了考虑可能的上尾相关性，选择 Gumbel Copula 来改进单一高斯依赖结构。然而，对于该混合，在下尾相关性行中仍存在“×”符号，因为两个组成 Copula 都无法建模该特征。高斯 Copula 与 Gumbel Copula 的混合被称为 Gaussian–Gumbel Copula，定义为式 (38.15)。

$$C_{\mathrm{Gaussian\text{-}Gumbel}}(u_1, \ldots, u_n \mid w_{Ga}, w_{Gu}, R, \alpha) = w_{Ga} C_{\mathrm{Gaussian}}(u_1, \ldots, u_n \mid R) + w_{Gu} C_{\mathrm{Gumbel}}(u_1, \ldots, u_n \mid \alpha), \tag{38.15}$$

其中 \(w_{Ga}, w_{Gu} \in [0,1]\) 且 \(w_{Ga} + w_{Gu} = 1\)。参数 \((R, \alpha)\) 是关联参数，而 \((w_{Ga}, w_{Gu})\) 是权重参数。

类似地，Gaussian–Gumbel Copula 的上尾和下尾相关系数分别如式 (38.16) 和 (38.17) 所示。它只能捕捉上尾相关性。

\[
\lambda^U_{\mathrm{Gaussian\text{-}Gumbel}} = w_{Ga} \lambda^U_{Ga} + w_{Gu} \lambda^U_{Gu} = w_{Gu} \cdot \left(2 - 2^{1/\alpha}\right), \tag{38.16}
\]

\[
\lambda^L_{\mathrm{Gaussian\text{-}Gumbel}} = w_{Ga} \lambda^L_{Ga} + w_{Gu} \lambda^L_{Gu} = 0. \tag{38.17}
\]

### (3) Gaussian–Gumbel–Clayton copula

三个或三个以上的 Copula 可以混合以体现更大的灵活性。一般而言，组成 Copula 越多，其混合越灵活。例如，为了进一步覆盖可能的下尾相关性，可以将 Clayton Copula 添加到高斯和 Gumbel Copula 的混合中。与 Gaussian–Gumbel Copula 相比，该三 Copula 混合实际上嵌套了更强的捕捉敏感下尾相关性的能力，并在表 38.2 中全部为“√”。高斯 Copula、Gumbel Copula 和 Clayton Copula 的混合被称为 Gaussian–Gumbel–Clayton Copula，定义为式 (38.18)。

$$C_{\mathrm{Gaussian\text{-}Gumbel\text{-}Clayton}}(u_1, \ldots, u_n \mid w_{Ga}, w_{Gu}, w_C, R, \alpha, \beta) = w_{Ga} C_{\mathrm{Gaussian}}(u_1, \ldots, u_n \mid R) + w_{Gu} C_{\mathrm{Gumbel}}(u_1, \ldots, u_n \mid \alpha) + w_C C_{\mathrm{Clayton}}(u_1, \ldots, u_n \mid \beta), \tag{38.18}$$

其中 \(w_{Ga}, w_{Gu}, w_C \in [0,1]\) 且 \(w_{Ga} + w_{Gu} + w_C = 1\)。参数 \((R, \alpha, \beta)\) 是关联参数，而 \((w_{Ga}, w_{Gu}, w_C)\) 是权重参数。

此外，类似地，Gaussian–Gumbel–Clayton Copula 的上尾和下尾相关系数如式 (38.19) 和 (38.20) 所示。它可以捕捉上尾和下尾相关性，但这两种尾部相关性是不对称的。

\[
\lambda^U_{\mathrm{Gaussian\text{-}Gumbel\text{-}Clayton}} = w_{Ga} \lambda^U_{Ga} + w_{Gu} \lambda^U_{Gu} + w_C \lambda^U_C = w_{Gu} \cdot \left(2 - 2^{1/\alpha}\right), \tag{38.19}
\]

\[
\lambda^L_{\mathrm{Gaussian\text{-}Gumbel\text{-}Clayton}} = w_{Ga} \lambda^L_{Ga} + w_{Gu} \lambda^L_{Gu} + w_C \lambda^L_C = w_C \cdot 2^{-1/\beta}. \tag{38.20}
\]

本节共构建了三种混合 Copula，其中 t-Gumbel Copula 能够以最少的 Copula 组成全面捕捉风险依赖的典型特征，被认为最适合建模银行风险依赖。为比较，次优的 Gaussian–Gumbel Copula 和 Gaussian–Gumbel–Clayton Copula 也被构建。与单一 Copula 相比，混合 Copula 更灵活，具有更强的特征捕捉能力；然而值得注意的是，增加更多的组成 Copula 也会增加模型的复杂性并引入额外参数，导致模型估计和应用的计算成本和工作量增加。

## 38.3.3 Mixture copula-based risk integration

由于混合 Copula 也是 Copula，它们可以耦合边缘分布以恢复联合分布。具体而言，类似于 Copula 方法，混合 Copula 也可以将不同类型的银行风险整合为总风险。如图 38.1 所示，使用混合 Copula

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1582_0.png)

图 38.1：基于混合 Copula 的风险整合框架。
