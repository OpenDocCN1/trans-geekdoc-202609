
## 网络架构与训练

我们使用 Diffusers 库中的二维 U-Net$^{18,35}$ 从头开始训练评分网络和一致性网络，该网络包含四个下采样和上采样层。对于这四个层，我们使用了具有 128、128、256 和 256 个通道以及 3 $\times$ 3 卷积核的卷积、Sigmoid 线性单元（SiLU）激活函数、组归一化，并在架构瓶颈处使用了一个注意力层。该网络总共有大约 2700 万可训练参数。

我们使用 Adam 优化器$^{46}$ 对核心网络进行 200 个轮次的训练，批量大小为 1，学习率为 1 $\times$ 10$^{2}$，并对模型权重应用了衰减率为 0.999 的指数移动平均（补充信息）。

CM 模型使用 RAdam 优化器$^{47}$ 训练 150 个轮次$^{23}$，采用与评分网络相同的批量大小、学习率和指数移动平均调度（初始衰减率为 $\alpha_0=0.9$）。我们发现损失在训练过程中以稳定的方式下降（补充图 1）。在 NVIDIA G102 32 GB 图形处理单元上，CM 的 150 轮训练大约需要六天半，而 SDE 需要四天半。训练超参数的摘要见补充表 1。

## 尺度一致的下采样

正如其他工作$^{45,48}$所示，向图像（或流体动力学快照）添加具有选定方差的高斯噪声，结果是消除直至特定空间尺度的空间图案，该尺度与所加噪声量相关。经过训练的生成模型随后可以将噪声替换为从训练数据中学习到的、直至选定空间尺度的空间图案。

原则上，空间尺度可以根据给定的下采样任务进行选择，例如，与 ESM 分辨率或变量相关。因此，我们的方法在训练后提供了更大的灵活性，其中最优训练尺度可以根据任何给定的指标来定义。总体而言，ESM 场在小空间尺度上过于平滑，这是地球系统建模（总体而言）以及影响评估（特别是）的一个关键问题。更具体地说，当从空间功率谱密度（PSD）的角度比较空间降水场的频率分布时，可以看到 ESM 缺乏高频空间变异性，即空间间歇性，这是降水的一个关键特征$^{49}$。因此，保留在 ESM 场中的空间尺度的一个自然选择是来自 ESM 和真实 ERA5（参考文献 17）的 PSD 的交点（图 3），即 ESM 场变得过于平滑的尺度。

其中 $k$ 是当前训练步骤，$K$ 是从 PyTorch Lightning 库获得的估计总训练步骤数。初始离散化步骤设置为 $s_0 = 2$，最大步骤数设置为 $s_n = 150$（参考文献 23）。我们用 $\hat{\theta}$ 表示对模型参数 $\theta$ 的指数移动平均，其更新公式为 $\hat{\theta} = \text{stograd}[w(k)\hat{\theta} + (1-w(k)\theta)]$，衰减调度由下式给出：

```
w(k) = exp(s0 log($\alpha_0$) / N(k))
(9)
```

其中 $w_0 = 0.9$ 是初始衰减率$^{50}$。对于距离度量 $d(\cdot, \cdot)$，我们遵循另一项工作$^{35}$，使用学习到的感知图像块相似度$^{51}$和 $l^p$ 范数的组合：

```
$d(x, y) = \text{LPIPS}(x, y) + \|x-y\|_l$
(10)
```

因此，CMI 的训练是自监督的，并与表示学习$^{52}$密切相关，其中所谓的在线网络 $\hat{\text{f}}: \theta$ 被训练以预测与“目标网络” $\text{f}: \hat{\theta}$ 相同的图像表示（参考文献 44）。重要的是，因此 CMI 并非明确为下采样任务进行训练，这些任务纯粹在推理阶段执行。

对于高斯噪声，时间 $t$ 的方差可以通过$^{47}$与给定波数 $k$ 和网格大小 $N$ 的 PSD 相关联：

```
$\sigma^2(t) = N^{p}\text{PSD}(k)$
(11)
```

使用方程 (11)，我们选择 $k^* = 0.0667$（补充图 2），使其代表 ESM 和 ERA5 降水场 PSD 相交的波数或空间尺度。这对应于 CM 方差调度的 $t^* = 0.468$ 和 SDE 桥的 $t^* = 0.355$。

扩散桥$^{47}$从方程 (1) 中的前向 SDE 开始，初始化为来自 POEM ESM 的降水场。然后前向 SDE 被积分直至 $t = T$。然后，反向 SDE（方程 (2)）——在 $t = T$ 处初始化——再次对场去噪，从目标 ERA5 分布中添加结构。

对于 CM 方法，在推理时，我们应用“笔画引导”技术$^{48,53}$，其中我们首先采样一个噪声 ESM 场 $\mathbf{x}^{\text{ESM}} \in \mathbb{R}^{d}$，其方差对应于 $t^*$：

```
$\mathbf{x}^{\text{ESM}} \sim \mathcal{N}(\textbf{x}^{\text{ESM}}, \sigma^2(t^*)\mathbf{I})$
(12)
```

然后通过 CM 在单步内对其进行去噪：

```
$\mathbf{x} = f(\mathbf{x}^{\text{ESM}}, t^*, \theta)$
(13)
```

从而高效地生成现实样本 $\mathbf{x}$，这些样本保留了 ESM 直至尺度 $k^*$ 的无偏空间图案。

## 数据可用性

ERA5 再分析数据可在 Copernicus 气候变化服务（C3S）下载（https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=download）。POEM ESM 的模拟数据可通过 Zenodo 获取（https://doi.org/10.5281/zenodo.4685086）$^{30}$。

## 代码可用性

用于数据处理和分析的 PyTorch 代码，以及用于训练的 PyTorch$^{48}$ 代码$^{35}$，可通过 GitHub（https://github.com/p-los/consistency-climate-downscaling.git）和 Code Ocean（https://doi.org/10.24435/CO.2150269v1）$^{52}$ 获取。

## 参考文献

- 1. Kotz, M., Levernann, A. & Wenz, L. 降雨变化对经济生产的影响. Nature **601**, 223–227 (2022).
- 2. Schneider, T. et al. 气候目标与开启云层的未来. Nat. Clim. Change **7**, 3–5 (2017).
- 3. Dinh, L., Krueger, G. & Bengio, Y. NICE: 非线性独立成分估计. 预印本 http://arxiv.org/abs/1410.8516 (2015).
- 4. Goodfellow, I. et al. 生成对抗网络. In Advances in Neural Information Processing Systems (eds Ghahramani, Z. et al) 2672–2680 (MIT, 2014).
- 5. Groenke, B., Madau, L. & Monteleoni, C. ClimAlign: 通过归一化流对气候变量进行无监督统计降尺度. In Proc. 10th International Conference on Climate Informatics 60–66 (Association for Computing Machinery, 2020).
- 6. Pan, B. et al. 学习修正气候预测偏差. J. Adv. Model. Earth Syst. **13**, e2021MS002509 (2021).
- 7. Francois, B., Thaos, S. & Yrao, M. 使用循环一致性对抗网络调整气候模型输出的空间依赖性. Clim. Dyn. **57**, 3328–3353 (2021).
- 8. Harris, L., McRae, A. T. T., Chanhy, M., Dueben, P. D. & Palmer, T. N. 一种生成式深度学习方法来随机降尺度降水预报. J. Adv. Model. Earth Syst. **14**, e2022MS003120 (2022).
- 9. Hess, P., Dürke, M., Petri, A., Strandal, F. M. & Boers, N. 物理受限生成对抗网络用于改善地球系统模型的降水场. Nat. Mach. Intell. 4, 828–839 (2022).
- 10. Hess, P., Lange, S., Schötz, C. & Boers, N. 深度学习用于偏差校正 CMIP6 级地球系统模型. Earth’s Future 11, e2023EOF00402 (2023).
- 11. M. Arjovsky, L. & Bottou. 迈向训练生成对抗网络的原则性方法. In 5th International Conference on Learning Representations (OpenReview.net, 2017).
- 12. Dhariwal, P. & Nichol, A. 扩散模型在图像合成上击败 GAN. In Advances in Neural Information Processing Systems (eds Ranzato, M. et al.) 8780–8794 (Curran Associates, 2021).
- 13. Song, Y. et al. 通过随机微分方程进行基于评分的生成建模. In 9th International Conference on Learning Representations 8780–8794 (Curran Associates, 2021).
- 14. Clark, K. & Jaini, P. 文生图扩散模型是零样本分类器. In Advances in Neural Information Processing Systems (eds Oh, T. et al.) 58921–58937 (Curran Associates, 2023).
- 15. Sauer, A., Lorenz, D., Blattmann, A. & Rombach, R. 对抗扩散蒸馏. In Computer Vision—ECCV 2024 174–103 (Springer Nature, 2024).
- 16. Meng, G. et al. SDEdit: 使用随机微分方程进行指导图像合成和编辑. In 10th International Conference on Learning Representations (Curran Associates, 2022).
- 17. Bischoff, T. & Deck, K. 使用扩散桥对流体流动进行非配对降采样. Artif. Intell. Earth Syst. 3, e300039 (2024).
- 18. Wan, Z. Y. et al. 去偏差粗化，条件采样：统计降尺度模型优于 MIP 传输和概率扩散模型. In Advances in Neural Information Processing Systems (eds Oh, A. et al.) 47749–47763 (NeurIPS, 2023).
- 19. Karras, T., Aittala, M., Aila, T. & Laine, S. 阐明基于扩散的生成模型的设计空间. In Advances in Neural Information Processing Systems (eds Koyejo, S. et al.) 26565–26577 (NeurIPS, 2022).
- 20. Esser, P. et al. 为高分辨率图像合成扩展校正流 Transformer. In Proc. of the 41st International Conference on Machine Learning (eds Salakhutdinov, R. et al.) 12598–12633 (JMLR.org, 2024).
- 21. Luhman, E. & Luhman, T. 迭代生成模型中的知识蒸馏以提高采样速度. 预印本 http://arxiv.org/abs/2101.02388 (2021).
- 22. Zheng, H., Nie, W., Valdadt, A. & Anandkumar, A. 使用掩码 Transformer 快速训练扩散模型. In Transactions on Machine Learning Research (OpenReview.net, 2024).
- 23. Song, Y., Dhariwal, P., Chen, M. & Sutskever, I. 一致性模型. In Proc. 40th International Conference on Machine Learning (eds Krause, A. et al.) 32221–32252 (PMLR, 2023).
- 24. Harder, P. et al. 用于气候降尺度的硬约束深度学习. J. Mach. Learn. Res. 24, 1–40 (2023).
- 25. Ravuri, S. et al. 使用雷达的深度生成模型进行熟练的降水预报. Nature 597, 672–677 (2021).
- 26. Tian, B. & Dong, G. 基于年平均降水的 CMIP3、CMIP5 和 CMIP6 模型中的双 ITCZ 偏差. Geophys. Res. Lett. 47, e2019GL087232 (2020).
- 27. Cannon, A. J., Sobie, S. R. & Murdock, T. Q. 通过分位数映射对 GCM 降水进行偏差校正——这些方法在分位数和极值变化中的表现如何？J. Clim. 28, 6938–6959 (2015).
- 28. Hersbach, H. 集成预测系统中连续排序概率得分的分解. Weather Forecast. 15, 559–570 (2000).
- 29. Traxl, D., Boers, N., Rheinwalt, A. & Bookhagien, B. 气旋活动在热带温度-降雨尺度中的作用. Nat. Commun. 12, 6332 (2021).
- 30. Beucler, T. et al. 在模拟物理系统的神经网络中强制实施解析约束. Phys. Rev. Lett. 126, 98302 (2021).
- 31. Schwartz, R., Dodige, L., Smith, N. A. & Etzioni, O. Green AI. Commun. ACM 63, 54–63 (2020).
- 32. Price, I. et al. 使用机器学习的概率天气预报. Nature 637, 84–90 (2025).
- 33. Huang, X. et al. 扩散模型的蓝噪声. In ACM SIGGRAPH (eds Burbano, A. et al.) 1–11 (Association for Computing Machinery, 2024).
- 34. Hersbach, H. et al. ERA5 全球再分析. Q. J. R. Meteorol. Soc. 146, 1999–2049 (2020).
- 35. Dürke, M. et al. CM2mC-LPimL v1.0: 将基于过程的动态植被模型与管理土地耦合到一般循环模型中的生物物理耦合. Geosci. Model Dev. 14, 4117–4141 (2021).
- 36. Dunne, J. P. et al. GFDL 地球系统模型版本 4 (GFDL-ESM 4.1): 总体耦合模型描述和模拟特征. J. Adv. Model. Earth Syst. 12, e2019MS002015 (2020).
- 37. Klöwer, M. et al. SpeedyWeather.l: 重新发明大气一般循环模型以实现交互性和可扩展性. J. Open Source Softw. 9, 6323 (2024).
- 38. Song, Y. & Ermon, S. 通过估计数据分布的梯度进行生成建模. In Advances in Neural Information Processing Systems (eds Wallach, H. M. et al.) 11918–11930 (Curran Associates, 2019).
- 39. Song, J., Meng, C. & Ermon, S. 去噪扩散隐模型. In International Conference on Learning Representations 6323 (The Open Review, 2021).
- 40. Ho, J., Jain, A. & Abbeel, P. 去噪扩散概率模型. In Advances in Neural Information Processing Systems (eds Larochelle, M. et al.) 6840–6851 (NeurIPS, 2020).
- 41. Papamarkarios, G., Naishick, G., Rezende, D. J., Mohamed, S. & Lakshminarayanan, B. 用于概率建模和推理的归一化流. J. Mach. Learn. Res. 22, 2617–2680 (2021).
- 42. Zhang, R., Iosa, P., Eiros, A., Schmetzman, E. & Wang, O. 深度特征作为感知指标的不可思议的有效性. In Proc. IEEE Conference on Computer Vision and Pattern Recognition 586–595 (IEEE, 2018).
- 43. Lessig, C. et al. AtmoRep: 使用大规模表示学习的大气动力学随机模型. 预印本 http://arxiv.org/abs/2308.13280 (2023).
- 44. Grill, J. F. et al. 自举你的潜在变量——一种新的自监督学习方法. In Advances in Neural Information Processing Systems (eds Larochelle, M. et al.) 21271–21284 (Curran Associates, 2020).
- 45. Ronneberger, O., Fischer, P. & Brox, T. U-Net: 用于生物医学图像分割的卷积网络. In Medical Image Computing and Computer-Assisted Intervention—MICCAI 2015. Lecture Notes in Computer Science (eds Navab, N. et al.) 234–241 (Springer, 2015).
- 46. Kingma, D. P. & Ba, J. L. Adam: 一种随机优化方法. In 3rd International Conference on Learning Representations ICLR 2015—Conference Track Proc. 1–15 (ICLR, 2015).
- 47. Liu, L. et al. 关于自适应学习率的方差及更广阔的研究. In 8th International Conference on Learning Representations (OpenReview.net, 2020).

https://doi.org/10.1038/s42256-025-00980-5
