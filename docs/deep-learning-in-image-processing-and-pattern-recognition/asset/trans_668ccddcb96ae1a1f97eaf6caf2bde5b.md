
分别提高了3.1%、7.9%和5.8%。值得注意的是，在比较同时代模型时，我们的模型与TBSRN之间最显著的改进体现在中等难度级别上，这突显了我们的技术在文本图像超分辨率中卓越的视觉质量。

## 表 3. 本文方法与其他方法在CRNN识别上的结果比较。

| 骨干网络 | 简单/% | 中等/% | 困难/% |
| :--- | :--- | :--- | :--- |
| BICUBIC | 36.4 | 21.1 | 21.1 |
| SRCNN | 38.7 | 21.6 | 20.9 |
| SRResNet | 39.7 | 27.6 | 22.7 |
| EDSR | 42.7 | 29.3 | 24.1 |
| RDN | 41.6 | 24.4 | 23.5 |
| ESRGAN | 50.2 | 33.0 | 28.9 |
| TSRN | 52.5 | 38.2 | 31.4 |
| TSRGAN | 56.2 | 42.5 | 32.8 |
| TBSRN | 59.6 | 47.1 | 35.3 |
| 我们的模型 | **62.7** | **55.0** | **41.1** |

表 4 和表 5 展示了所提出的方法与其他模型在 PSNR 和 SSIM 值方面的比较。值得注意的是，该方法在这些指标上的得分较低。然而，这种差异是可以解释的。必须强调，这种导致 PSNR 和 SSIM 分数降低的非传统方法，源于文本图像恢复中超分辨率的具体细微差别以及随后识别准确率的提升。

## 表 4. 本文方法与其他模型在 PSNR 值方面的比较。

| 骨干网络 | 简单 | 中等 | 困难 |
| :--- | :--- | :--- | :--- |
| EDSR | 24.26 | 18.63 | 19.14 |
| RDN | 22.27 | 18.95 | 19.70 |
| LapSRN | 24.58 | 18.85 | 19.77 |
| ESRGAN | 24.01 | 19.62 | 20.30 |
| TSRN | 25.07 | 18.86 | 19.74 |
| TSRGAN | 24.22 | 19.17 | 19.99 |
| TBSRN | 23.82 | 19.17 | 19.68 |
| 我们的模型 | 20.64 | 18.88 | 19.20 |

## 表 5. 本文方法与其他模型在 SSIM 值方面的比较。

| 骨干网络 | 简单 | 中等 | 困难 |
| :--- | :--- | :--- | :--- |
| EDSR | 0.8633 | 0.6440 | 0.7108 |
| RDN | 0.8249 | 0.6427 | 0.7113 |
| LapSRN | 0.8556 | 0.6480 | 0.7087 |
| ESRGAN | 0.8489 | 0.6569 | 0.7290 |
| TSRN | 0.8897 | 0.6676 | 0.7302 |
| TSRGAN | 0.8791 | 0.6770 | 0.7420 |
| TBSRN | 0.8660 | 0.6533 | 0.7490 |
| 我们的模型 | 0.8029 | 0.6292 | 0.6655 |

超越像素级指标：虽然 PSNR 和 SSIM 在各种图像处理任务中很有价值，但它们主要是在像素层面起作用的。在精细细节和特定内容（如文本）至关重要的任务中，这些指标可能无法全面反映真正的超分辨率结果。文本图像恢复需要极高的细节水平和可读性，这超出了像素级评估的范围。超分辨率对字符识别、文本清晰度和 OCR 准确率的影响，通过评估这些高层质量的指标更有效地被捕捉。

评估超分辨率结果：虽然 PSNR 和 SSIM 是超分辨率领域广泛认可的指标，但必须承认，它们并非图像质量的最终权威。在实践中，超分辨率结果通常通过主观评估进行评判。人类观察者的视觉评估仍然是对超分辨率结果图进行视觉重现效果排名的有价值方法。这强调了超分辨率质量不仅由数学指标决定，还由感知体验决定的认识。

强调识别率：在场景文本图像超分辨率的背景下，字符的可读性和 OCR 性能至关重要，识别率作为一个更具反射性和实用性的性能指标脱颖而出。这在采用相同的预训练 OCR 模型时尤为重要。识别率直观地反映了字符增强的影响，使其成为评估文本图像清晰度和可读性中超分辨率实际收益的必要度量。它还符合超分辨率的更广泛目标，即促进下游应用，其中文本识别通常是最终目标。

简而言之，该方法优先考虑文本图像可读性和字符识别的增强，符合超分辨率在文本图像恢复领域的实际应用。虽然 PSNR 和 SSIM 结果可能显得较低，但本文对识别准确率的强调凸显了该技术在实际应用中的 tangible（实质性的）和现实适用性。这反映了致力于优化文本清晰度和 OCR 性能的决心，这对于许多文本处理和分析任务至关重要。

为了更清晰地可视化不同模型的超分辨率结果比较，图 8 展示了各个模型增强后的超分辨率图像。为了提供更好的关于更细细节的清晰度，图 9 显示了模型的放大部分。结合图 8 和图 9 可以发现，对于标签“VARIETY”，TBSRN 错误地将字母“I”恢复为“V”。在标签“SWEEPING”的情况下，TBSRN 未能恢复字母“E”，而是将其解释为“C”。相比之下，所提出的超分辨率模型完美地重建了这些字符。观察标签“STORY”和“CONSTRUCTION”，虽然其他模型能够进行基本的轮廓恢复，但其结果充斥着伪影、拉长的拖尾失真以及次优的重建。另一方面，该方法提供了无伪影且精确的重建，紧密地模仿了原始内容。因此，与其他以文本为重点的超分辨率方法相比，该模型不仅表现出更少的伪影和失真，还保持了对原始内容的保真度。总之，所提出的基于像素级退化的文本图像超分辨率技术在文本图像超分辨率的实际应用中具有巨大的潜力。

在评估文本图像超分辨率模型的复杂度时，参数数量是一个关键指标。它代表了模型在保持效率的同时捕捉复杂特征和细节的能力。表 6 展示了本研究中使用的模型与其他模型参数数量的比较。拥有 520 万个参数，该模型有效地平衡了复杂性和实用性。令人惊叹的是，它在比较的模型中实现了最高的识别率，突显了其在光学字符识别（OCR）导向任务中的适用性。这种精炼的特征提取能力使该模型成为增强实际应用中文本图像可读性的诱人选择，巩固了该领域的突出地位。

![](img/e4200cc4308edaf8913e513b0f96dbb6_105_0.png)

图 8. 各模型超分辨率图像可视化后的比较。

![](img/e4200cc4308edaf8913e513b0f96dbb6_105_1.png)

图 9. 细节放大后的比较图像。

## 表 6. 本文方法与其他模型在参数数量方面的比较。

| 骨干网络 | SRCONN | EDSR | ESRGAN | TSRN | TBSRN | 我们的模型 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 参数 | 1.8 M | 43 M | 16 M | 2.6 M | 3.2 M | 5.2 M |

## 4.4. 局限性

尽管本文的方法可以有效地提高场景文本图像的识别率，但仍有一些领域需要进一步关注，特别是在处理高度模糊的图像方面。虽然识别率表现出显著改进，但传统指标如 PSNR 和 SSIM 仍可能表明存在优化的空间。

## 5. 结论

本文提出了一种文本图像超分辨率的新方法，该方法融合了像素级退化技术、迁移学习和传统退化方法。该方法在识别率方面产生了实质性改进，强调了其在增强文本图像清晰度和可读性方面的实际应用性，特别是在 OCR 和文本处理应用中。展望未来，迫切需要解决已识别的局限性，特别是在增强高度模糊图像的超分辨率效果以及优化各种背景下的性能方面，包括 PSNR 和 SSIM 等传统质量指标。此外，将该方法的适用范围扩展到多语言和多脚本场景具有巨大潜力。

作者贡献：概念化，X.Q., L.X. 和 S.Y.；方法论，L.X. 和 N.Y.；形式分析，X.Q.；验证，N.Y. 和 R.L.；撰写——初稿，X.Q. 和 L.X.；撰写——审稿和编辑，S.Y. 和 R.L.；监督，X.Q. 和 R.L.；资金支持获取，X.Q. 和 S.Y.。所有作者已阅读并同意发表版的手稿。

资金：本工作得到浙江省教育科研基金（项目编号 Y202352263）和国家自然科学基金（项目编号 61972357）的支持。

数据可用性声明：数据可向作者索取。我们的代码可在 https://github.com/syyang2022/PDTS 获取（访问日期：2023年11月1日）。

利益冲突：作者声明无利益冲突。

# 参考文献

1. Long, S.; He, Y.; Yao, C. Scene text detection and recognition: The deep learning era. Int. J. Comput. Vis. 2021, 129, 161–184. [CrossRef]
2. Naieemi, F.; Ghods, K.; Vaheshi, H. Scene text detection and recognition: A survey. Multimed. Tools Appl. 2022, 81, 20255–20290. [CrossRef]
3. Dong, C.; Zhu, X.; Deng, Y.; Loy, C.C.; Qiao, Y. Boosting optical character recognition: A super-resolution approach. arXiv 2015, arXiv:1506.02211.
4. Wang, W.; Xie, E.; Liu, X.; Wang, W.; Liang, D.; Shen, C.; Bai, X. Scene text image super-resolution in the wild. In Proceedings of the Computer Vision–ECCV 2020: 16th European Conference, Glasgow, UK, 23–28 August 2020; pp. 650–666, Part X 16.
5. Chen, J.; Li, B.; Xie, X. Scene text telescope: Text-focused scene image super-resolution. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, Nashville, TN, USA, 20–25 June 2021; pp. 12026–12035.
6. Fang, C.; Zhu, Y.; Liao, L.; Ling, X. TSRGAN: Real-world text image super-resolution based on adversarial learning and triplet attention. Neurocomputing 2021, 455, 88–96. [CrossRef]
7. Ma, J.; Liang, Z.; Zhang, L. A text attention network for spatial deformation robust scene text image super-resolution. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, New Orleans, LA, USA, 18–24 June 2022; pp. 5911–5920.
8. Wang, K.; Belongie, S. Word spotting in the wild. In Proceedings of the Computer Vision–ECCV 2010: 11th European Conference on Computer Vision, Heraklion, Crete, Greece, 5–11 September 2010; pp. 591–604, Part I 11.
9. Yuan, T.-T.; Zhu, J.; Xu, K.; Li, C.-J.; Mu, T.-J.; Hu, S.-M. A large chinese text dataset in the wild. J. Comput. Sci. Technol. 2019, 34, 509–521. [CrossRef]
10. Rishnumanan, A.; Shikavamura, P.; Chan, C.S.; Tan, C.L. A robust arbitrary text detection system for natural scene images. Expert Syst. Appl. 2014, 41, 8027–8048. [CrossRef]
11. Chen, H.; Gu, J.; Liu, Y.; Magid, S.A.; Dong, C.; Wang, Q.; Pfister, H.; Zhu, L. Masked Image Training for Generalizable Deep Image Denoising. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, Vancouver, BC, Canada, 18–22 June 2023; pp. 1692–1703.
12. Lan, R.; Sun, L.; Liu, L.; Lu, H.; Pang, C.; Luo, X. MADNet: A fast and lightweight network for single-image super resolution. IEEE Trans. Cybern. 2020, 51, 1443–1453. [CrossRef] [PubMed]
13. Ates, H.F.; Yildirim, S.; Gunturk, B.K. Deep learning-based blind image super-resolution with iterative kernel reconstruction and noise estimation. Comput. Vis. Image Underst. 2023, 233, 103718. [CrossRef]
14. Wang, X.; Xie, L.; Dong, C.; Shan, Y. Real-esrgan: Training real-world blind super-resolution with pure synthetic data. In Proceedings of the IEEE/CVF International Conference on Computer Vision, Montreal, BC, Canada, 11–17 October 2021; pp. 1905–1914.
15. Niu, A.; Zhu, Y.; Zhang, C.; Sun, J.; Wang, P.; Kweon, I.S.; Zhang, Y. Ms2net: Multi-scale and multi-stage feature fusion for blurred image super-resolution. IEEE Trans. Circuits Syst. Video Technol. 2022, 32, 5137–5150. [CrossRef]
16. Xuhong, L.; Grandvalet, Y.; Davonee, F. Explicit individual degree bias for transfer learning with convolutional networks. In Proceedings of the International Conference on Machine Learning, Stockholm, Sweden, 10–15 July 2018; pp. 2825–2834.
17. Chen, X.; Wang, X.; Zhou, Y.; Qiao, Y.; Dong, C. Activating more pixels in image super-resolution transformer. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, Vancouver, BC, Canada, 18–22 June 2023; pp. 22267–22377.

