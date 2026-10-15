
SAC ([刘等，2021b](#Ch003_29-58_S0169716123000019.xhtml#bb0250))是一种通用的防御方法，可在不重新训练目标检测器的情况下，增强任何目标检测器对补丁攻击的鲁棒性。SAC采用“检测并删除”策略：它检测出对抗性补丁并从输入图像中删除相关区域，然后将掩码图像输入目标检测器。这一策略基于以下观察：虽然对抗性补丁是局部化的，但它们不仅会影响局部区域，还会影响图像中较远的目标，因为目标检测算法利用空间上下文进行推理（[Saha等，2020](#Ch003_29-58_S0169716123000019.xhtml#bb0325)）。这种效应在深度学习模型中尤其显著，因为小范围的对抗性补丁会因神经元的大受体场而对大范围的特征图产生显著干扰。通过从图像中移除检测到的补丁，SAC将对抗性补丁在局部和全局层面的负面影响最小化。

SAC的核心是可靠地检测对抗性补丁。SAC首先训练一个补丁分割器，用于从输入中分割出对抗性补丁并生成初始补丁掩码。它采用自对抗训练算法增强补丁分割器的鲁棒性，该算法高效且与目标检测器无关。由于攻击者可能在自适应攻击下对分割器进行攻击并扰乱其输出，SAC进一步利用一种鲁棒的形状完成算法，该算法利用补丁形状先验，确保对抗性补丁的可靠检测。形状完成算法接收初始补丁掩码，生成“完成补丁掩码”，只要初始掩码在一定的汉明距离范围内，该完成掩码即可**保证**覆盖整个对抗性补丁。

SAC的整体流程如[Fig. 6](#Ch003_29-58_S0169716123000019.xhtml#f0035)所示。

![Fig. 6 Pipeline of the SAC approach. SAC detects and removes adversarial patches on pixel level through patch segmentation and shape completion, and feeds the masked images into the base object detector for prediction.](images/S0169716123000019/f03-06-9780443184307.jpg)

[Fig. 6](#Ch003_29-58_S0169716123000019.xhtml#B-f0035) Pipeline of the SAC approach. SAC detects and removes adversarial patches on pixel level through patch segmentation and shape completion, and feeds the masked images into the base object detector for prediction.

SAC在适应性攻击下的防御性能如[Table 5](#Ch003_29-58_S0169716123000019.xhtml#t0035)所示。SAC在不同补丁尺寸上对两个数据集均表现出极强的鲁棒性，且其mAP高于所有基线方法。此外，SAC在未防御模式下也保持了较高的清洁性能。[Figs. 7](#Ch003_29-58_S0169716123000019.xhtml#f0040)和[8](#Ch003_29-58_S0169716123000019.xhtml#f0045)分别展示了防御前后的目标检测结果示例。对抗性补丁会产生伪检测并隐藏真实目标，而SAC通过掩蔽对抗性补丁恢复了模型的预测。

[Table 5](#Ch003_29-58_S0169716123000019.xhtml#B-t0035)

mAP (%) under adaptive attack with different patch sizes.

| Dataset || Method || Clean || 75 × 75 || 100 × 100 || 125 × 125 |

| --- | --- | --- | --- | --- | --- |

| COCO || Undefended || **49.0** || 19.8±1.0 || 14.4±0.6 || 9.9±0.5 |

| --- | --- | --- | --- | --- | --- |

|  || AT ([Madry et al., 2017](#Ch003_29-58_S0169716123000019.xhtml#bb0255)) || 40.2 || 23.5±0.7 || 18.6±0.8 || 13.9±0.3 |

|  || JPEG ([Dziugaite et al., 2016](#Ch003_29-58_S0169716123000019.xhtml#bb0095)) || 45.6 || 22.8±0.9 || 18.0±0.8 || 13.4±0.7 |

|  || Spatial smoothing ([Xu et al., 2017](#Ch003_29-58_S0169716123000019.xhtml#bb0460)) || 46.0 || 23.2±0.7 || 17.5±1.0 || 13.5±0.6 |

|  || LGS ([Naseer et al., 2019](#Ch003_29-58_S0169716123000019.xhtml#bb0275)) || 42.7 || 20.8±0.7 || 15.9±0.5 || 12.2±0.9 |

|  || APM ([Chiang et al., 2021](#Ch003_29-58_S0169716123000019.xhtml#bb0075)) || 47.6 || 19.4±0.4 || 14.7±0.4 || 10.8±0.4 |

|  || SAC (**Ours**) || **49.0** || **43.6** ±**0.9** || **44.0** ±**0.3** || **39.2** ±**0.7** |

| Dataset || Method || Clean || 50×50 || 75×75 || 100×100 |

| xView || Undefended || **27.2** || 8.4±1.6 || 7.1±0.4 || 5.3± 1.1 |

|  || AT ([Madry et al., 2017](#Ch003_29-58_S0169716123000019.xhtml#bb0255)) || 22.2 || 12.1±0.4 || 8.6±0.1 || 7.2±0.7 |

|  || JPEG ([Dziugaite et al., 2016](#Ch003_29-58_S0169716123000019.xhtml#bb0095)) || 23.3 || 11.2±0.3 || 9.5±1.0 || 8.3±0.3 |

|  || Spatial smoothing ([Xu et al., 2017](#Ch003_29-58_S0169716123000019.xhtml#bb0460)) || 21.8 || 11.0±0.7 || 7.9±0.6 || 6.5±0.2 |

|  || LGS ([Naseer et al., 2019](#Ch003_29-58_S0169716123000019.xhtml#bb0275)) || 19.1 || 8.2±0.8 || 6.5±0.4 || 5.4±0.5 |

|  || APM ([Chiang et al., 2021](#Ch003_29-58_S0169716123000019.xhtml#bb0075)) || 27.1 || 20.5±0.3 || 20.2±1.4 || 18.9±0.9 |

|  || SAC (**Ours**) || **27.2** || **25.3** ±**0.3** || **23.6** ±**1.2** || **23.2** ±**0.3** |

表格中每列的最佳性能以**粗体**标出。

![Fig. 7 Visualization of object detection results from COCO dataset. Adversarial patches create spurious detections, and make the detector ignore the ground-truth objects. SAC masks out the patch and restores model predictions. (A) Ground-truth on clean image. (B) Predictions on clean image. (C) Predictions on adversarial images with a 100 × 100 patch. (D) Predictions on SAC masked images.](images/S0169716123000019/f03-07-9780443184307.jpg)

[Fig. 7](#Ch003_29-58_S0169716123000019.xhtml#B-f0040) Visualization of object detection results from COCO dataset. Adversarial patches create spurious detections, and make the detector ignore the ground-truth objects. SAC masks out the patch and restores model predictions. (A) Ground-truth on clean image. (B) Predictions on clean image. (C) Predictions on adversarial images with a 100 × 100 patch. (D) Predictions on SAC masked images.

![Fig. 8 Visualization of object detection results from xView dataset. Adversarial patches create spurious detections, and make the detector ignore the ground-truth objects. SAC masks out the patch and restores model predictions. (A) Ground-truth on clean image. (B) Predictions on clean image. (C) Predictions on adversarial images with a 100 × 100 patch. (D) Predictions on SAC masked images.](images/S0169716123000019/f03-08-9780443184307.jpg)

[Fig. 8](#Ch003_29-58_S0169716123000019.xhtml#B-f0045) Visualization of object detection results from xView dataset. Adversarial patches create spurious detections, and make the detector ignore the ground-truth objects. SAC masks out the patch and restores model predictions. (A) Ground-truth on clean image. (B) Predictions on clean image. (C) Predictions on adversarial images with a 100 × 100 patch. (D) Predictions on SAC masked images.

##  6: Reverse engineering of deceptions via residual learning

几乎所有前文所述的防御方法都通过对抗训练或通过判断示例是否为对抗性（对抗性检测）来防御深度学习模型免受对抗攻击。然而，我们希望不仅能检测对抗性示例，还能识别产生这些示例的对抗算法。这对于任何安全关键系统都极为有用，因为它可以根据对手使用的对抗算法选择最有效的防御措施。

