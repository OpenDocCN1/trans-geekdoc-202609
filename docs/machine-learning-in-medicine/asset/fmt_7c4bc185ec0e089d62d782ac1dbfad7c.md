
We should point out that practically it might make more sense to keep `P` at a constant value (e.g. 0.5) and tune `N`, as opposed to keeping `N` constant and tuning `P`; this is because tuning `N` and keeping `P` constant effectively means varying the degree of polling on the sampled set of networks while expecting a fixed minimum classification probability agreement among the polled ones, whereas tuning `P` keeping `N` constant means freezing the polling space and varying the value of the minimum classification probability agreement in that frozen network space. In other words, it is `N` that allows us to choose how much of the sampled network distribution we will cover, and hence it is a better measure of practical uncertainty.

The takeaway from the findings is that the parameters `N` and `P` can be tuned to a desirable level and the higher the values of these parameters, the higher the confidence we will have in the predictions/classifications, in exchange for possibly lower coverage. For a domain like medical mammography image classification, it will be up to the mammography experts to determine what value of `N` and `P` is reasonable. After setting reasonable values for `N` and `P`, previously unseen images that will be classified by the Bayesian network (either as benign or malignant) are more likely to be correctly classified, whereas images that will be skipped and denied classification would need further investigation. The overall framework can be used as a confidence tuning tool for any computer-aided diagnosis problem.

## [9.5 Conclusion](#C16_chapter9.xhtml#rsecc009_5)

In this chapter, we highlight three practical issues that can arise while deploying an ML model for medical image segmentation or computer-aided diagnosis problems. We tackle the heavy dependence on large training datasets of deep learning models with transfer learning, where we show that utilizing transfer learning from natural images can significantly improve the performance of Alzheimer’s diagnosis. To address the issue of class imbalance, which is prevalent for medical image segmentation, we propose a novel FTL, which, combined with Attention U-Net, results in state-of-the-art lesion segmentation performance on a benchmark breast ultrasound dataset. Finally, we propose a confidence tuning tool utilizing a Bayesian neural network, where, through two simple hyperparameters (sampled number of networks and minimum probability), a neural network’s accuracy-coverage tradeoff can be tuned to the need of the domain expert.

Although the three sections showed promising results, more work needs to be done to ensure the robustness of the proposed methods before they can be deployed in a clinical setting. For transfer learning, we are investigating whether our solution can be generalized to solve computer-aided diagnosis problems in domains other than Alzheimer’s. For our proposed loss function, our next step is to investigate how the solution performs for different types of imbalanced classification problems, especially to investigate how the transfer learning approach can be combined with the proposed loss function. For confidence tuning, an end-to-end Bayesian learning approach on top of transfer learning to keep the computational requirement manageable is something we would be exploring in the future.

## [Notes](#C16_chapter9.xhtml#rsecc009_5a)

1.  [1](#C16_chapter9.xhtml#rfn9_1) Extended experimental results and analyses on this project was originally published in \[[3](#C16_chapter9.xhtml#ref9_3), [4](#C16_chapter9.xhtml#ref9_4)\].

2.  [2](#C16_chapter9.xhtml#rfn9_2) Extended experimental results and analyses on this project was originally published in \[[6](#C16_chapter9.xhtml#ref9_6)\].

3.  [3](#C16_chapter9.xhtml#rfn9_3) Code for this chapter can be found in: [https://github.com/nabsabraham/focal-tversky-unet](https://github.com)

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
