
我们应指出，实际上保持 `P` 为常数值（例如 0.5）并调节 `N` 可能更合理，而不是保持 `N` 不变而调节 `P`；这是因为调节 `N` 并保持 `P` 不变意味着在样本网络集合上改变采样程度，同时期望在被采样的网络中保持固定的最小分类概率一致性，而调节 `P` 并保持 `N` 不变则意味着冻结采样空间并改变在该冻结网络空间中的最小分类概率一致性的值。换句话说，`N` 使我们能够选择覆盖样本网络分布的多少，因此它是实用不确定性的更好度量。

从发现中得出的要点是，参数 `N` 和 `P` 可以调节到理想水平，这些参数的值越高，我们对预测/分类的置信度就越高，代价是可能出现较低的覆盖率。对于医学乳腺 X 光图像分类这一领域，将由乳腺 X 光专家决定 `N` 和 `P` 的合理取值。设定合理的 `N` 和 `P` 后，以前未见的图像在由贝叶斯网络分类（无论是良性还是恶性）时，更有可能被正确分类；而被跳过并拒绝分类的图像则需要进一步调查。整体框架可作为任何计算机辅助诊断问题的置信度调节工具。

## [9.5 Conclusion](#C16_chapter9.xhtml#rsecc009_5)

在本章中，我们突出了在部署用于医学图像分割或计算机辅助诊断问题的机器学习模型时可能出现的三个实际问题。我们通过转移学习来解决深度学习模型对大规模训练数据集的高度依赖问题，展示了从自然图像进行转移学习可以显著提升阿尔茨海默病诊断的性能。为解决医学图像分割中普遍存在的类别失衡问题，我们提出了一种新型的 FTL，结合 Attention U-Net，在基准乳腺超声数据集上实现了最先进的病灶分割性能。最后，我们提出了一种利用贝叶斯神经网络的置信度调节工具，通过两个简单的超参数（样本网络数量和最小概率），可以在域专家的需求下调节神经网络的准确率-覆盖率权衡。

尽管前三节展示了有希望的结果，但在将这些方法部署到临床环境之前，仍需进一步工作以确保所提方法的鲁棒性。对于转移学习，我们正在探讨我们的方案是否能够推广到阿尔茨海默病以外的其他计算机辅助诊断领域。对于我们提出的损失函数，下一步是研究其在不同类型的不平衡分类问题中的表现，特别是研究如何将转移学习方法与所提损失函数相结合。对于置信度调节，我们计划在未来探索一种端到端的贝叶斯学习方法，在转移学习基础上进行，以保持计算需求可管理。

## [Notes](#C16_chapter9.xhtml#rsecc009_5a)

1.  [1](#C16_chapter9.xhtml#rfn9_1) 本项目的扩展实验结果和分析最初发表在 \[[3](#C16_chapter9.xhtml#ref9_3), [4](#C16_chapter9.xhtml#ref9_4)\]。

2.  [2](#C16_chapter9.xhtml#rfn9_2) 本项目的扩展实验结果和分析最初发表在 \[[6](#C16_chapter9.xhtml#ref9_6)\]。

3.  [3](#C16_chapter9.xhtml#rfn9_3) 本章代码可在：[https://github.com/nabsabraham/focal-tversky-unet](https://github.com)

## [References](#C16_chapter9.xhtml#rreferences-7)

1.  [1.](#C16_chapter9.xhtml#rref9_1) T.-Y. Lin, P. Goyal, R. Girshick, K. He, and P. Dollár, “Focal loss for dense object detection,” *IEEE Transactions on Pattern Analysis and Machine Intelligence*, vol. 42, no. 2, pp 318–327, 2018.

2.  [2.](#C16_chapter9.xhtml#rref9_2) B. M. Geller, A. Bogart, P. A. Carney, J. G. Elmore, B. S. Monsees, and D. L. Miglioretti, “Is confidence of mammographic assessment a good predictor of accuracy?” *American Journal of Roentgenology*, vol. 199, no. 1, pp. W134–W141, 2012.

3.  [3.](#C16_chapter9.xhtml#rref9_3) N. M. Khan, N. Abraham, and M. Hon, “Transfer learning with intelligent training data selection for prediction of Alzheimer’s disease,” *IEEE Access*, vol. 7, pp. 72726–72735, 2019.

4.  [4.](#C16_chapter9.xhtml#rref9_4) M. Hon and N. M. Khan, “Towards Alzheimer’s disease classification through transfer learning,” in *IEEE International Conference on Bioinformatics and Biomedicine*, 2017.

5.  [5.](#C16_chapter9.xhtml#rref9_5) C. R. Jack et al., “The Alzheimer’s disease neuroimaging initiative (ADNI): MRI methods,” *Journal of* *Magnetic Resonance Imaging*, vol. 27, no. 4, pp. 685–691, 2008.

6.  [6.](#C16_chapter9.xhtml#rref9_6) N. Abraham and N. M. Khan, “A novel focal Tversky loss function with improved attention U-net for segmentation,” in *IEEE Symposium on Biomedical Imaging*, 2019.

7.  [7.](#C16_chapter9.xhtml#rref9_7) S. R. Hashemi et al., “Tversky as a loss function for highly unbalanced image segmentation using 3D fully convolutional deep networks,” *CoRR*, vol. abs/1803.11078, 2018.

8.  [8.](#C16_chapter9.xhtml#rref9_8) S. Klöppel et al., “Accuracy of dementia diagnosis – A direct comparison between radiologists and a computerized method,” *Brain*, vol. 131, no. 11, pp. 2969–2974, 2008.

9.  [9.](#C16_chapter9.xhtml#rref9_9) C. Plant et al., “Automated detection of brain atrophy patterns based on MRI for the prediction of Alzheimer’s disease,” *Neuroimage*, vol. 50, no. 1, pp. 162–174, 2010.

10.  [10.](#C16_chapter9.xhtml#rref9_10) N. Tajbakhsh et al., “Convolutional neural networks for medical image analysis: Full training or fine tuning?” *IEEE Transactions on Medical Imaging*, vol. 35, no. 5, pp. 1299–1312, 2016.

11.  [11.](#C16_chapter9.xhtml#rref9_11) J. Yosinski, J. Clune, Y. Bengio, and H. Lipson, “How transferable are features in deep neural networks?” in *Advances in Neural Information Processing Systems*, 2014.

12.  [12.](#C16_chapter9.xhtml#rref9_12) O. Russakovsky et al., “Imagenet large scale visual recognition challenge,” *International Journal of Computer Vision*, vol. 115, no. 3, pp. 211–252, 2015.

13.  [13.](#C16_chapter9.xhtml#rref9_13) K. Simonyan and A. Zisserman, “Very deep convolutional networks for large-scale image recognition,” *arXiv preprint arXiv:1409.*1556, 2014.

14.  [14.](#C16_chapter9.xhtml#rref9_14) C. Studholme, D. L. Hill, and D. J. Hawkes, “An overlap invariant entropy measure of 3D medical image alignment,” *Pattern* *Recognition*, vol. 32, no. 1, pp. 71–86, 1999.

15.  [15.](#C16_chapter9.xhtml#rref9_15) A. Gupta, M. Ayhan, and A. Maida, “Natural image bases to represent neuroimaging data,” in *International Conference on Machine Learning*, 2013.

16.  [16.](#C16_chapter9.xhtml#rref9_16) Hosseini-Asl et al., “Alzheimer’s disease diagnostics by adaptation of 3D convolutional network,” in *IEEE International Conference Image Processing*, 2016.

17.  [17.](#C16_chapter9.xhtml#rref9_17) S. Sarraf et al., “Deepad: Alzheimer’s disease classification via deep convolutional neural networks using MRI and fMRI,” *bioRxiv*, p. 070441, 2016.

18.  [18.](#C16_chapter9.xhtml#rref9_18) C. H. Sudre et al., “Generalised dice overlap as a deep learning loss function for highly unbalanced segmentations,” in *Deep Learning in Medical Image Analysis for Clinical Decision Support*. Springer, 2017, pp. 240–248. [https://link.springer.com/chapter/10.1007/978-3-319-67558-9\_28](https://link.springer.com)

