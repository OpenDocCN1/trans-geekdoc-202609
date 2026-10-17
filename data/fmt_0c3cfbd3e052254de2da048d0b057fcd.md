
| 预训练数据集 | 微调数据集 | 准确率 |
|:---:|:---:|:---:|
| `ShapeNN(OBJ_BG)` | `ShapeNN(OBJ_BG)` | 87.1 |
| `ShapeNN(OBJ_BG)` | `ShapeNet` | 90.0 |
| `ShapeNN(OBJ_ONLY)` | `None` | 80.6 |
| `ShapeNN(OBJ_ONLY)` | `ShapeNN(OBJ_BG)` | 87.3 |
| `ShapeNN(OBJ_ONLY)` | `ShapeNet` | 88.3 |
| `ShapeNN(PB-T0-RS)` | `None` | 77.2 |
| `ShapeNN(PB-T0-RS)` | `ShapeNN(OBJ_BG)` | 81.2 |
| `ShapeNN(PB-T0-RS)` | `ShapeNet` | 85.2 |

## 4.4. 讨论

我们尝试分析 `Point-MAE` 优于同样采用掩码重建框架的 `Point-BERT` 的原因。首先，在预训练期间，我们的重建目标来自输入（即坐标），这是无噪声的；而 `Point-BERT` 重建高层表示，如果 `VAE` 没有被良好学习，重建目标可能会有噪声。其次，`Point-BERT` 从输入处理掩码标记。这导致了位置信息的泄漏，对于学习潜在特征是有害的。我们通过移位掩码标记解决了这个问题。第三，我们认为点云在信息密度上与图像相似。实验上，我们采用了 60–80% 比例的随机掩码，这与 `Point-BERT` 的 25–45% 大不相同。

### 5 结论与未来工作

在本章中，我们提出了一种用于点云自监督学习的新型掩码自动编码器方案，称为 `Point-MAE`。我们的 `Point-MAE` 基于点云的属性进行了极小的修改。我们方法的有效性和高泛化能力在物体分类、少量学习和部分分割等多种任务上得到了验证。具体来说，`Point-MAE` 优于所有其他自监督方法。此外，我们的工作启发了从语言和图像到点云的统一架构的可性。

对于未来的工作，我们预计可以探索以下方面。首先，正如我们在消融实验中提到的，尽管我们的方法无论预训练数据集如何都能带来性能提升，但尚不清楚噪声数据如何影响模型性能。从应用角度来看，从现实世界收集的点云带有噪声。其次，由于我们使用了标准 `transformer` 架构，我们希望点云能够加入多模态学习框架，通过语言或图像或其他模态辅助学习。第三，我们的方法迈出了第一步，并在小型数据集上得到了验证。未来的工作还可以关注为大型数据集开发我们的方法，以完成更复杂的下游任务，例如自动驾驶任务的检测和分割。

## 致谢

本章基于论文“Masked autoencoders for point cloud self-supervised learning”，最初发表于 `Computer Vision-ECCV 2022: 17th European Conference, Tel Aviv, Israel, October 23-27, 2022, Proceedings, Part II`。我们增加了更多的实验结果。还添加了实验细节以及更多显示下游任务的网络。此外，我们讨论了这项工作的未来方向。

## 参考文献

1. C. R. Qi, H. Su, K. Mo, and L. J. Guibas. `PointNet`: Deep learning on point sets for 3D classification and segmentation. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 652–660 (2017).

2. J. Devlin, M-W. Chang, K. Lee, and K. Toutanova. `BERT`: Pretraining of bidirectional transformers for language understanding, arXiv preprint arXiv:1810.04805 (2018).

3. T. Brown, B. Mann, N. Ryder, M. Subbiah, J. D. Kaplan, D. Dhariwal, A. Neelantan, P. Shyam, S. Gastry, A. Askell, et al. Language models are few-shot learners. In Advances of Neural Information Processing Systems, Vol. 33, pp. 1877–1901 (2020).

4. A. Radford, J. Wu, R. Chang, D. Lu, A. Amodei, I. Sutskever, et al. Language models are unsupervised multitask learners, OpenAI Blog 1(8), 9 (2019).

5. C. Raffel, N. Shazeer, A. Roberts, K. Lee, S. Narang, M. Matena, Y. Zhou, W. Li, and P. J. Liu. Exploring the limits of transfer learning with a unified text-to-text transformer. arXiv preprint:1910.10683 (2019).

6. D. Pathak, P. Krakenbruch, J. Donahue, T. Darrell, and A. A. Efros. Context encoders: feature learning by inpainting. In Proceedings of IEEE 计算机视觉与模式识别会议，第 2536-2544 页 (2016)。

7. H. Bao, L. Dong, F. Wei. `BEIT`: 图像 `Transformer` 的 `BERT` 预训练。arXiv 预印本 arXiv:2106.08254 (2021)。

8. T. Chen, S. Kornblit, M. Noruzi, G. Hinton. 视觉表示对比学习的简单框架。在国际机器学习会议上，1597–1607 页 (2020)。

9. K. He, H. Fan, Y. Wu, S. Xie, R. Girshick. 用于无监督视觉表示学习的动量对比。在 IEEE/CVF 计算机视觉与模式识别会议论文集中，第9729–9738 页 (2020)。

10. M. Chen, A. Radford, R. Child, J. Wu, H. Jun, D. Duan, I. Sutskever. 来自像素的生成式预训练。在国际机器学习会议上，1691–1730 页 (2020)。

11. A. Baevski, W.-N. Hsu, Q. Xu, A. Babu, J. Gu, M. Auli. `Data2vec`: 用于语音、视觉和语言自监督学习的通用框架，第 1–27 页 (2022)。https://ai.facebook.com/research/data2vecca-general-framework-for-self-supervised-learning-in-speech-vision-and-language/

12. K. He, X. Chen, S. Xie, Y. Li, P. Dollár, R. Girshick. 掩码自动编码器是可扩展的视觉学习者。arXiv 预印本 arXiv:2111.06377 (2021)。

13. Z. Xie, Z. Zhang, Y. Cao, Y. Lin, J. Bao, Z. Yao, Q. Dai, H. Hu. `SimMIM`: 掩码图像建模的简单框架。arXiv 预印本 arXiv:2111.09886 (2021)。

14. A. Vaswani, N. Shaazeer, I. Polosukhin. 注意力即你所需。A. N. Gomez, L. Kaiser，在神经信息处理系统进展中，第 30 (2017)。

15. X. Yu, L. Tang, Y. Rao, T. Huang, J. Zhou, J. Lu. `Point-BERT`: 通过掩码点建模预训练 3D 点云 `Transformer`。arXiv 预印本 arXiv preprint:2111.14819 (2021)。

16. Y. Wang, Y. Sun, Z. Liu, S. E. Sarma, M. M. Bronstein, J. M. Solomon. 用于点云学习的动态图 `CNN`，ACM 图形学 (TOG) 38(5)，1–12 页 (2019)。

17. J. T. Rolfe. 离散变分自动编码器。arXiv 预印本 arXiv:1609.02230 (2016)。

18. A. Dosovitskiy, L. Beyer, A. Kolesnikov, D. Weissenborn, X. Chai, T. Unterthiner, M. Dehghani, M. Minderer, G. Heigold, S. Gelly, 等。图像的宽度为 16 × 16：用于大规模图像识别的 `Transformer`。arXiv 预印本 arXiv:2010.11929 (2020)。

19. X. Liu, F. Zhang, Z. Hou, L. Lian, Z. Wang, J. Zhang, J. Tang. 自监督学习：生成还是对比？IEEE 知识与数据工程 35(1)，857–876 页 (2023)。doi:10.1109/TKDE.2021.309086。

20. Z. Wu, Y. Wu, Y. Xiong, S. Xu, D. Lin. 通过非参数判别进行无监督特征学习。在 IEEE 计算机视觉会议论文集中，3733–3742 页 (2018)。

21. J.-B. Grill, F. Strub, F. Altches, R. Richemond, E. Buchacker, C. Doersch, B. Pires, Z. Guo, 等。一种自监督学习的新方法。在神经信息处理进展中，第 33，2127–2184 页 (2020)。

22. X. Chen, H. Fan, R. Girshick, K. He. 动量对比学习改进的基准。arXiv 预印本 arXiv:2003.04297 (2020)。

23. C. Wei, H. Fan, S. Xie, C.-Y. Yu, C. Fechtenhofer. 用于自监督预训练的掩码预测。arXiv 预印本 arXiv:2112.09133 (2021)。

24. H. Wang, Q. Liu, X. Yue, M. Kusner. 无监督完成。在 IEEE/CVF 国际计算机视觉论文集中，9782–9792 页 (2021)。

25. Z. Zhang, R. Girdhar, A. Youlin, I. Misra. 3D 特征自监督预训练。在 IEEE/CVF 国际计算机视觉论文集中，10252–10263 页 (2021)。

26. S. Xie, J. Gu, C. R. Qi, L. Guibas, O. Litany. 3D 点云理解的无监督预训练。在欧洲视觉会议上，574–591 页 (2020)。

27. J. Sauder, B. Sievers. 通过重构空间的点云自监督深度学习。在神经信息处理进展中，第 32 (2019)。

28. P. Achlioptas, O. Diamanti, I. Mitchellakis, L. Guibas. 3D 点云的表示和生成模型。在国际机器学习会议上，40–49 页 (2018)。

29. J. Li, B. M. Chen, G. H. `So-Net`. 用于点云分析的自组织网络。在 IEEE 计算机视觉会议论文集中，9397–9406 页 (2018)。

30. Y. Yang, C. Feng, Y. Shen, D. Tian. `FoldingNet`: 通过深度形变的点云自动编码器。在 IEEE 计算机视觉会议上，206–215 页 (2018)。Y. Pang 等。

31. Y. Rao, J. Lu, J. Zhou. 3D 点云无监督表示学习的全局-局部双向推理。在 IEEE/CVF 计算机视觉会议论文集中，5376–5385 页 (2020)。

32. B. Eckart, W. Yuan, C. Liu, J. Kaut. 通过学习离散生成模型进行 3D 点云自监督学习。在 IEEE/CVF 计算机视觉会议论文集中，8248–8257 页 (2021)。

33. S. Yan, Z. Yang, H. Li, L. Guan, H. Kang, G. Hua, Q. Huang. 用于点云自监督表示学习的隐式自动编码器。arXiv 预印本 arXiv:2211.00785 (2022)。

34. Y. Liu, M. Ott, N. Goyal, J. Du, M. Joshi, D. Chen, O. Levy, M. Lewis, L. Zettlemoyer, S. Stoyanov. 一种鲁棒的 `BERT` 预训练方法。arXiv 预印本 arXiv:1907.11692 (2019)。

35. L. Yuan, Y. Chen, T. Wang, W. Wu, Y. Yu, Z.-H. Liang, J. Feng, S. San. Token 到 Token: 从头训练视觉 `Transformer`。在 IEEE/CVF 国际计算机视觉论文集中，558–567 页 (2021)。

36. Z. Liu, Y. Lin, Y. Cao, H. Hu, Y. Wei, Z. Zhang, S. Lin, B. Guo. `Swin transformer`: 使用移动窗口的分层视觉 `Transformer`。在 IEEE/CVF 国际计算机视觉论文集中，10012–10022 页 (2021)。

37. L. Yuan, Q. Hou, Z. Jiang, J. Feng, S. Yan. `VOLO`: 视觉识别的展望。arXiv 预印本 arXiv:2106.13112 (2021)。

38. W. Wang, L. Yao, L. Chen, D. Liu, X. He, W. Liu. `Crossformer`: 一种通尺度无关 `Transformer`。arXiv 预印本 arXiv:2108.051 (2021)。

39. W. Wang, E. Xie, D. Chen, S. Shao. 无监督预训练。在 IEEE/CVF 国际计算机视觉论文集中，568–578 页 (2021)。

40. H. Li, J. Chen, P. Wang, X. Liu. 自监督预训练。在 IEEE/CVF 国际计算机视觉论文集中，16259–16268 页 (2021)。

41. Z. Zhang, M. Chen, D. Duan, H. Li. 解耦权重正则化。arXiv 预印本 arXiv:1711.05101 (2017)。

42. X. Chen, W. Wu, Y. Yu, S. Xie. 掩码自动编码器。arXiv 预印本 arXiv:2112.09387 (2021)。

43. J. Li, B. Lee, R. Kim, Y. Lee. 从点集学习。在国际机器学习会议上，3744–3753 页 (2018)。

55. S. Qiu, S. Anwar, and N. Barnes. 用于点云分类的几何反投影网络，IEEE Transactions on Multimedia (2021)。

56. S. Cheng, X. Chen, X. He, Z. Liu, and X. Bai. `PRA-Net`: 用于 3D 点云分析的点关系感知网络，IEEE Transactions on Image Processing 30, 4436–4448 (2021)。

57. A. X. Chang, T. Funkhouser, L. Guibas, P. Hanrahan, Q. Huang, Z. Li, S. Savarese, M. Savva, S. Song, H. 等. `ShapeNet`: 一种信息丰富的 3D 模型表示。arXiv预印版 arXiv:1512.06012 (2015)。

58. H. Thomas, C. R. Qi, J.-E. Deschaud, B. Marcotegu, F. Goulette, and L. J. Guibas: 用于点云的灵活可变形卷积。收录于 IEEE/CVF 国际计算机视觉会议，pp. 6411–6420 (2019)。

59. Y. Liu, B. Fan, S. Xiang, and C. Pan. 用于点云分析的关系-形状卷积神经网络。收录于 IEEE/CVF 计算机视觉与模式识别会议，pp. 8895–8904 (2021)。

60. C. Zhang, H. Wan, S. Liu, X. Chen, and Z. Wu. `PVT`: 用于 3D 深度学习的点-像素 `Transformer`。arXiv预印版 arXiv:2108.06076 (2021)。

61. S. Huang, Y. Xie, S.-C. Zhu, and Y. Zhu: 用于 3D 点云的时空自监督表示学习。收录于 IEEE/CVF 国际计算机视觉会议，pp. 6535–6545 (2021)。

62. Z. Wu, S. Song, A. Khosla, F. Yu, L. Zhang, X. Zhang, X. Tang, and J. Xiao. `ShapeNets`: 用于体素形状的深度表示。收录于 IEEE 计算机视觉与模式识别会议，pp. 1912–1920 (2015)。

63. C. Sharma and M. Kaul. 点云上的自监督少样本学习。收录于神经信息处理系统进展，第 33 卷，pp. 7212–7221 (2020)。
