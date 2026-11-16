

| 参数 | 值 |
| :--- | :--- |
| 判别器：优化器 | Adam |
| 判别器：Adam：beta1 | 0.9 |
| 判别器：Adam：beta2 | 0.999 |
| 判别器：Adam：epsilon | 1e-8 |
| 判别器：学习率 | 0.0001 |
| 判别器：最大梯度范数 | 1 |
| 判别器编码器权重 $\mu_{enc}$ | 0.3 |
| 判别器解码器权重 $\mu_{dec}$ | 0.001 |
| $\gamma$ | 500 |
| $\Delta C$ | 4e-5 |

## B.3.2 DAVA不同构建模块的个体贡献

人们可能会好奇，DAVA的哪些构建模块对性能贡献最大。开发期间的结果显示，仅DAVA的对抗损失就能与\(\beta\)-TCVAE和FactorVAE取得可比性能，且同样存在正则化强度依赖于数据集的问题。有趣的是，对于AnnealedVAE，不同数据集的最优\(C\)与DAVA在图4.10中显示的值高度吻合。这也反映了在没有对抗损失的情况下，人们可以期望从DAVA获得的性能。

## B.3.3 DAVA与现有方法的组合

DAVA的主要贡献在于其能够根据判别器评估的模型当前状态，自适应调整隐式容量瓶颈。在这方面，可以使用不同于DAVA提出的判别器。其中一种选择是FactorVAE中使用的判别器，它可以以类似于DAVA中判别器的方式引导隐式容量瓶颈。这仍然允许针对特定数据集的退火方案，而无需针对特定数据集的超参数。

```
Algorithm 2.18 Training DAVA
\(\theta_{enc},\theta_{dec},\theta_{dis} \leftarrow initialize parameters\)
while Not Converged do
  \(x \leftarrow sample random mini-batch from \tilde{D}\)
  \(\hat{z} \leftarrow Enc(x)\)
  \(\hat{x} \leftarrow Dec(\hat{z})\)
  \(\mathcal{L}_{vae} \leftarrow logp(\hat{x}|\hat{z}) - \gamma(KL(q(\hat{z})||p(\hat{z})) - C)^4\)
  \(\theta_{enc} \xleftarrow{\dagger} -\nabla_{\theta_{enc}}\mathcal{L}_{vae}\)
  \(\theta_{dec} \xleftarrow{\dagger} -\nabla_{\theta_{dec}}\mathcal{L}_{vae}\) \(\triangleright\) Update VAE
  \(\hat{z} \leftarrow Enc(x)\)
  \(\hat{x} \leftarrow Dec(\hat{z})\) \(\triangleright\) Recreate \(\hat{z}\) and \(\hat{x}\) after update
  \(\tilde{x} \leftarrow Dec(PermuteDims(\hat{z}))\)
  \(acc \leftarrow accuracy(Dis, \hat{x}, \tilde{x})\)
  \(\theta_{dis} \xleftarrow{\dagger} \nabla_{\theta_{dis}} log(Dis(\hat{x})) + log(1 - Dis(\tilde{x}))\) \(\triangleright\) Update Discriminator
  \(C \xleftarrow{\dagger} update_C(acc)\)
  \(\mu_{base} \leftarrow max((acc - 0.5) \cdot 100, 0)\) \(\triangleright\) Weight grows linearly with higher accuracy
  \(\theta_{enc} \xleftarrow{\dagger} -\nabla_{\theta_{enc}}\mu_{base} \cdot \mu_{enc} \cdot log(Dis(\hat{x}))\)
  \(\theta_{dec} \xleftarrow{\dagger} -\nabla_{\theta_{dec}}\mu_{base} \cdot \mu_{dec} \cdot log(1 - Dis(\tilde{x}))\) \(\triangleright\) Update VAE with adversarial loss
end while
```

```
Algorithm 2.19 update_C
Input: accuracy acc
if acc \(\le\) 0.5 then
  \(U \leftarrow \Delta C\) \(\triangleright\) Only increase C if discriminator is clueless
else if acc \(\le\) 0.51 then
  \(U \leftarrow 0\) \(\triangleright\) Grace period
else
  \(U \leftarrow -\Delta C\) \(\triangleright\) Decrease C if discriminator gets better
end if
Output: update U
```

## B.4 所有评估数据集的完定量结果

我们展示了大量数据集的结果。我们还在每个表格的上半部分包含了每种基线方法在监督超参数选择后的最佳正则化强度的结果。这作为在最佳场景下对完全无监督方法可能预期结果的一个额外参考。我们还包括Chen等人[45]的递归解耦网络（RecurD）的结果。这些结果应谨慎解读，因为我们未能自行复现，而是不得不从他们的论文中获取数值。这意味着首先，只评估了有限的一组数据集和指标。其次，模型架构、超参数选择、超参数调整范围、通用训练循环以及可能更多方面都会存在差异。请注意，关于AnnealedVAE的强性能，有两点需要考虑。首先，所选取的超参数范围尤其强，因为我们包含了DAVA发现的超参数。其次，如前文对DAVA的解释，我们使用$(\cdot)^4$而不是差的绝对值来控制KL偏差。还需注意，FactorVAE在NoisyDSprites上异常高的PIPE指标得分，是由于FactorVAE模型的解码器无论潜在空间如何始终产生相同的输出。这是PIPE的设计决策，如小节B.2.3中所述。也许令人惊讶的是，这些模型似乎仍然在潜在空间中传递少量信息，如监督指标所反映的。同样的情况也发生在FactorVAE在Mpi3d Toy上，有趣的是，这在Mpi3d Real上没有发生。

### 表 B.4.20: Shapes3D结果

| 架构 | MIG | DCI | FVAE | PIPE | Rec |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 最佳 \(\beta\)-TCVAE (\(\beta = 32\)) | 0.39±0.09 | 0.65±0.03 | 0.76±0.06 | 0.36±0.03 | 0.0041±0.0008 |
| 最佳 FactorVAE (\(\gamma = 30\)) | 0.39±0.16 | 0.54±0.12 | 0.79±0.05 | 0.30±0.08 | 0.0032±0.0005 |
| 最佳 AnnealedVAE (\(C = 1\)) | 0.63±0.04 | 0.78±0.05 | 0.94±0.04 | 0.49±0.05 | 0.0027±0.0002 |
| 最佳 ControlVAE (\(C = 18\)) | 0.08±0.03 | 0.20±0.06 | 0.68±0.12 | 0.02±0.00 | 0.0019±0.0004 |
| 最佳 RecurD [45] | (0.31) | (0.58) | - | - | (0.0083) |
| 平均 \(\beta\)-TCVAE | 0.26±0.06 | 0.50±0.03 | 0.76±0.03 | 0.11±0.03 | 0.0023±0.0004 |
| 平均 FactorVAE | 0.20±0.10 | 0.41±0.07 | 0.78±0.04 | 0.22±0.04 | 0.0027±0.0005 |
| 平均 AnnealedVAE | 0.52±0.02 | 0.70±0.02 | 0.92±0.01 | 0.26±0.03 | 0.0020±0.0001 |
| 平均 ControlVAE | 0.07±0.03 | 0.17±0.04 | 0.68±0.07 | 0.02±0.00 | 0.0019±0.0004 |
| 本文方法 | 0.62±0.05 | 0.78±0.03 | 0.82±0.03 | 0.61±0.04 | 0.0029±0.0004 |

### 表 B.4.21: AbstractDSprites结果

| 架构 | MIG | DCI | FVAE | PIPE | Rec |
|---|---|---|---|---|---|
| 最佳 \(\beta\)-TCVAE (\(\beta = 4\)) | 0.17±0.04 | 0.22±0.03 | 0.55±0.03 | 0.11±0.02 | 0.0017±0.0001 |
| 最佳 FactorVAE (\(\gamma = 50\)) | 0.18±0.07 | 0.26±0.04 | 0.65±0.05 | 0.23±0.04 | 0.0019±0.0001 |
| 最佳 AnnealedVAE (\(C = 2\)) | 0.23±0.04 | 0.26±0.04 | 0.65±0.05 | 0.13±0.02 | 0.0018±0.0001 |
| 最佳 ControlVAE (\(C = 18\)) | 0.06±0.01 | 0.11±0.03 | 0.50±0.05 | 0.07±0.01 | 0.0016±0.0000 |
| 平均 \(\beta\)-TCVAE | 0.12±0.01 | 0.18±0.01 | 0.45±0.02 | 0.19±0.01 | 0.0027±0.0000 |
| 平均 FactorVAE | 0.12±0.02 | 0.19±0.02 | 0.55±0.03 | 0.20±0.03 | 0.0018±0.0000 |
| 平均 AnnealedVAE | 0.15±0.01 | 0.21±0.01 | 0.54±0.02 | 0.18±0.01 | 0.0022±0.0000 |
| 平均 ControlVAE | 0.04±0.02 | 0.07±0.01 | 0.42±0.02 | 0.06±0.01 | **0.0016±0.0000** |
| 本文方法 | **0.23±0.04** | **0.27±0.05** | **0.67±0.05** | **0.35±0.03** | 0.0020±0.0002 |

### 表 B.4.22: Mpi3d Toy结果

| 架构 | MIG | DCI | FVAE | PIPE | Rec |
|---|---|---|---|---|---|
| 最佳 \(\beta\)-TCVAE (\(\beta = 2\)) | 0.23±0.04 | 0.33±0.01 | 0.42±0.06 | 0.07±0.01 | 0.0005±0.0000 |
| 最佳 FactorVAE (\(\gamma = 5\)) | 0.10±0.05 | 0.20±0.02 | 0.46±0.03 | 0.36±0.16 | 0.0021±0.0003 |
| 最佳 AnnealedVAE (\(C = \frac{1}{2}\)) | 0.21±0.07 | 0.31±0.02 | 0.41±0.05 | 0.12±0.01 | 0.0005±0.0000 |
| 最佳 ControlVAE (\(C=16\)) | 0.04±0.01 | 0.18±0.02 | 0.44±0.04 | 0.02±0.01 | 0.0003±0.0000 |
| 平均 \(\beta\)-TCVAE | 0.11±0.02 | 0.23±0.01 | 0.39±0.02 | 0.09±0.01 | 0.0006±0.0000 |
| 平均 FactorVAE | 0.02±0.01 | 0.13±0.00 | 0.38±0.02 | 0.99±0.10 | 0.0041±0.0000 |
| 平均 AnnealedVAE | 0.07±0.03 | 0.23±0.02 | **0.50±0.02** | 0.02±0.01 | **0.0003±0.0000** |
| 平均 ControlVAE | 0.04±0.01 | 0.17±0.02 | 0.43±0.04 | 0.03±0.01 | **0.0003±0.0000** |
| 本文方法 | **0.12±0.09** | **0.30±0.03** | 0.41±0.04 | **0.21±0.03** | 0.0006±0.0000 |

### 表 B.4.23: DSprites结果

| 架构 | MIG | DCI | FVAE | PIPE | Rec |
|---|---|---|---|---|---|
| 最佳 \(\beta\)-TCVAE (\(\beta = 32\)) | 0.34±0.02 | 0.50±0.03 | 0.60±0.00 | 0.76±0.14 | 0.0081±0.0000 |
| 最佳 FactorVAE (\(\gamma = 50\)) | 0.10±0.04 | 0.22±0.02 | 0.73±0.04 | 0.41±0.05 | 0.0098±0.0007 |
| 最佳 AnnealedVAE (\(C = \frac{1}{2}\)) | 0.36±0.01 | 0.51±0.01 | 0.76±0.03 | 0.42±0.03 | 0.0060±0.0006 |
| 最佳 ControlVAE (\(C = 18\)) | 0.06±0.02 | 0.13±0.03 | 0.67±0.11 | 0.24±0.03 | 0.0008±0.0000 |
| 最佳 RecurD [45] | (0.27) | (0.38) | - | - | (0.047) |
| 平均 \(\beta\)-TCVAE | **0.27±0.05** | **0.45±0.06** | **0.84±0.03** | 0.44±0.08 | 0.0024±0.0001 |
| 平均 FactorVAE | 0.14±0.06 | 0.22±0.05 | 0.72±0.07 | 0.31±0.03 | 0.0052±0.0002 |
| 平均 AnnealedVAE | 0.18±0.06 | 0.28±0.05 | 0.77±0.04 | 0.32±0.05 | 0.0013±0.0001 |
| 平均 ControlVAE | 0.05±0.02 | 0.13±0.01 | 0.69±0.06 | 0.20±0.08 | **0.0008±0.0000** |
| 本文方法 | 0.24±0.09 | 0.42±0.14 | 0.74±0.11 | **0.51±0.09** | 0.0025±0.0005 |

