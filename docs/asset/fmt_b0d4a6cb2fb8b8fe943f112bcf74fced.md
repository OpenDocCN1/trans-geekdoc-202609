
*Note:* 比较了空间流、时间流及其融合的结果。

## 4.7. 正则化的有效性

如 Section 3.4 中所述，我们对层次结构中每一层的特征图进行正则化以进一步增强其判别能力。`Inception4`、`Inception5`和最后一个 1 × 1 卷积层的正则化参数分别设置为 `5e^(-5)`、`1e^(-6)` 和 `5e^(-5)`。使用 `UCF-101` 的第一个划分，我们比较了有无中心损失正则化项的模型性能，结果呈现在 Table 5 中。显然，我们看到正则化带来了更好的结果，尽管改进很小。

`Table 5:`在 `UCF-101` 的第一个划分上比较 `HACNN` 方法有无中心损失正则化的性能。

![figure](img/p48-1.jpg)

`Table 6:`在 `UCF-101` 和 `HMDB51` 数据集上将我们的方法与其他最先进方法进行比较。

![figure](img/p48-2.jpg)

## 4.8. 与最先进方法的比较

在两个数据集上探索层次化聚合方法并建立了该方法有效性后，我们总结了我们方法获得的结果并将其与几种最先进方法进行比较。`Table 6` 详细分析了各种方法，包括依赖于手工特征的传统方法，如 `iDT` [10] 和超向量 [6, 48]。我们还与几种基于深度学习的方法进行比较，如双流架构 [31, 33]、循环神经网络 [28]、3D 卷积 [35]、轨迹池化深度卷积描述符（`TDD`）[33] 以及最近提出的时段网络（`TSN`）[32] 和时空 Resnets（`ST-ResNet`）[26]。正如我们从 `Table 6` 中看到的，在大多数情况下，深度学习特征优于手工特征。

在动作识别方面取得最新进展并提升了最先进结果的著名工作有：(i) `ST-ResNet` [26] 方法，其使用非常深的架构结合跨流残差连接；以及 (ii) `TSN` 方法 [25]，其使用非常深的架构结合网络最后一层的共识函数。从 `Table 6` 可以看出，在相同的两种输入模态下，`HACNN` 在 `UCF-101` 上比 `ST-ResNet` [26] 高出 1.2%，在 `HMDB51` 上高出 5.5%。同样，与 `TSN` 方法 [25] 相比，我们在 `UCF-101` 上提高了 0.6%，在 `HMDB51` 上提高了 3.4%。为了确认性能提升主要归因于 `HACNN` 而非模型中使用的额外帧，我们测试了使用 32 帧的 `TSN`，并未发现性能提升。如前所述，我们使用标准的密集测试程序为每个输入帧生成 10 个样本。我们认为帧数的影响在超过某一数量后会减小。

其他有趣的比较包括 (1) 双流 `LSTM` [49]，其将 `LSTM` 附加到双流 `Inception` 上，以及 (2) `LRCN` 方法 [28]，其将 `CNN` 与 `LSTM` 结合以建模长期时序动态。同样，我们观察到我们的方法比前者高出显著的 6.0%（在 `UCF-101` 上），比后者在 `UCF-101` 上高出 2.9%，在 `HMDB51` 上高出 7.1%。(3) 我们的方法比更复杂的聚合方法，如 `ActionVlad` [50]，取得了更好的结果。

这清楚地证明了 `HACNN` 中采用的分层聚合策略的有效性。`HMDB` 数据集中的动作由难以在没有显式时序建模的情况下捕捉的复杂广泛运动组成。`HMDB` 数据集上更大的提升再次加强了我们关于 `HACNN` 在建模长程动态方面有效的论断。注意，我们没有像若干早期方法 [26, 46] 那样结合 `iDT` 特征。

## 5.结论

在本章中，我们提出了一种新颖的分层聚合深度 ConvNets 模型，以更好地捕捉动作视频中存在的长期动态。所提出的分层模型由作用于每一层子 ConvNet 输出特征图的特殊聚合函数组成。聚合函数的作用是从邻近片段中汇聚最具判别性的信息。当在多层上重复时，这可以捕捉视频中存在的复杂动态。我们进行了详细的实验来研究模型的各个方面，例如不同聚合函数的选择及其在层次结构各层中的使用。我们观察到聚合函数在每一层都有用，并且保留空间布局的函数在实现优越性能中起着重要作用。我们还证明了整个系统是端到端可训练的，并在两个具有挑战性的动作识别数据集上实现了最先进的性能。

## References

1.Z. Chen, Q. Zhu, Y. C. Soh, and L. Zhang, “Robust human activity recognition using smartphone sensors via ct-pca and online SVM,” *IEEE Trans. Indust. Inform*, vol. 13, no. 6, pp. 3070–3080, 2017.

2.Z. Chen, L. Zhang, Z. Cao, and J. Guo, “Distilling the knowledge from handcrafted features for human activity recognition,” *IEEE Trans. Indust. Informa*., vol. 14, no. 10, pp. 4334–4342, 2018.

3.Z. Chen, L. Zhang, C. Jiang, Z. Cao, and W. Cui, “Wifi CSI based passive human activity recognition using attention based BLSTM,” *IEEE Trans. Mobile Comput*., vol. 18, no. 11, pp. 2714–2724, 2018.

4.Z. Chen, C. Jiang, S. Xiang, J. Ding, M. Wu, and X. Li, “Smartphone sensor based human activity recognition using feature fusion and maximum full a posteriori,” *IEEE Trans. Instrum. Measure*., vol. 69\. no. 7, pp. 3992–4001, 2019.

5.M. Brand and V. Kettnaker, “Discovery and segmentation of activities in video”. *IEEE Trans. Pattern Analy. Mach. Intell*., vol. 22, Aug. 2000.

6.Z. Cai, L. Wang, X. Peng, and Y. Qiao, “Multi-view super vector for action recognition,” *IEEE Conf. Computer Vision and Pattern Recognition*, pp. 596–603, 2014.vol. 69, no. 7, pp. 3992–4001.

7.A. A. Efros, A. C. Berg, G. Mori, and J. Malik, “Recognizing action at a distance,” *IEEE Int. Conf. Computer Vision*, Nice, France, October 2003, October 2003.

8.A. F. Bobick and J. W. Davis, “The recognition of human movement using temporal templates,” *IEEE Trans. Pattern Analy. Mach. Intell*., vol. 23, no. 3, pp. 257–267, 2001.

9.I. Laptev and T Lindeberg, “Space-time interest points,” *Int. J. Comput. Vis*., vol. 64, no. (2–3), 107–123, Sept. 2005.

10.H. Wang, A. Klaser, C. Schmid, and C.-L. Liu, “Action Recognition by Dense Trajectories,” in *CVPR*, 2011.

11.M. Bruni, T. Uricchio, L. Seidenari, and A. Del Bimbo, “Do textual descriptions help action recognition?” *Proc. 2016 ACM on Multimedia Conference*, ACM, pp. 645–649, 2016.

12.J. C. Niebles, H. Wang, and L. Fei-Fei, “Unsupervised learning of human action categories using spatial-temporal words,” *Int. J. Comput. Vis*., vol. 79, no. 3, pp.299–318, 2008.

13.M. Brand, N. Oliver, and A. Pentland, “Coupled hidden markov models for complex action recognition,” *IEEE Conf. Computer Vision and Pattern Recognition*, 1997.

14.P. Turaga, R. Chellappa, V. S. Subrahmanian, and O. Udrea, “Machine recognition of human activities: A survey,” *IEEE Transactions on Circuits and Systems for Video Technology*, 2008.

15.Y. Tian, Q. Ruan, G. An, and Y. Fu, “Action recognition using local consistent group sparse coding with spatio-temporal structure,” *Proc. 2016 ACM on Multimedia Conference*, ACM, pp. 317–321, 2016.

16.K. Soomro, A. R. Zamir, and M. Shah, “Ucf101: A dataset of 101 human actions classes from videos in the wild.” Crcv-tr-12-01, UCF, 2012.

17.E. G. T. P. H. Kuehne, H. Jhuang, and T. Serre, “HMDB: A large video database for human motion recognition,” *ICCV*, 2011.

18.I. S. A. Krizhevsky and G. E. Hinton, “Imagenet classification with deep convolutional neural networks,” *NIPS*, 2012.

19.C. Szegedy, W. Liu, Y. Jia, P. Sermanet, S. Reed, D. Anguelov, D. Erhan, V. Vanhoucke, and A. Rabinovich, “Going deeper with convolutions,” *CVPR*, 2015.

20.K. Simonyan and A. Zisserman, “Very deep convolutional networks for large-scale image recognition,” *ICLR*, 2014.

21.K. He, X. Zhang, S. Ren, and J. Sun, “Deep residual learning for image recognition,” 2015, arXivpreprint arXiv: 1512.03385.

22.J. Long, E. Shelhamer, and T. Darrell, “Fully convolutional networks for semantic segmentation,” *IEEE Conf. Computer Vision and Pattern Recognition*, pp.3431–3440, 2015.

23.A. J. Y. L. J. Tompson, R. Goroshin and C. Bregler, “Efficient object localization using convolutional networks,” *CVPR*, 2015.

24.D. K. F. Schroff and J. Philbin, “Facenet: A uni-fied embedding for face recognition and clustering,” *CVPR*, 2015.

25.L. Wang, Y. Xiong, Z. Wang, Y. Qiao, D. Lin, X. Tang, and L. Van Gool, “Temporal segment networks: Towards good practices for deep action recognition,” *European Conf. Comput. Vision*, pp. 20–36. Springer, 2016.

26.C. Feichtenhofer, A. Pinz, and R. P. Wildes, “Spatiotemporal residual networks for video action recognition,” *NIPS*, 2016.

27.S. Ioffe and C. Szegedy, “Batch Normalization: Accelerating deep network training by reducing internal covariate shift,” 2015, arXiv preprint arXiv.1502.03167.

28.J. Donahue, L. A. Hendricks, S. Guadarrama, M. Rohrbach, S. Venugopalan, K. Saenko, and T. Darrell, “Long-term recurrent convolutional networks for visual recognition and description,” `CVPR`, 2015.

29.S. Ji, W. Xu, M. Yang, and K. Yu, “3D convolutional neural networks for human action recognition,” `IEEE Trans. Pattern Anal. Mach. Intell`., vol. 35, no. 1, pp. 221–231, 2013.

30.A. Karpathy, G. Toderici, S. Shetty, T. Leung, R. Sukthankar, and L. Fei- Fei, “Large-scale video classification with convolutional neural networks,” `CVPR`, 2014.

31.K. Simonyan and A. Zisserman, “Two-stream convolutional networks for action recognition in videos,” `NIPS`, 2014.

32.Y. Wang, J. Song, L. Wang, L. Van Gool, and O. Hilliges, “Two-stream SR-CNNs for action recognition in videos,” `BMVC`, 2016.

33.L. Wang, Y. Qiao, and X. Tang, “Action recognition with trajectory-pooled deep-convolutional descriptors,” `CVPR`, pp. 4305–4314, 2015.

34.B. Zhang, L. Wang, Z. Wang, Y. Qiao, and H. Wang, “Real-time action recognition with enhanced motion vector cnns,” `CVPR`, pp. 2718–2726, 2016.

35.D. Tran, L. Bourdev, R. Fergus, L. Torresani, and M. Paluri, “Learning spatiotemporal features with 3D convolutional networks,” `ICCV`, 2015.

36.G. Varol, I. Laptev, and C. Schmid, “Long-term temporal convolutions for action recognition,” 2016, arXiv: 1604.04494.

37.B. Fernando, P Anderson, M. Hutter, and S. Gould, “Discriminative hierarchical rank pooling for activity recognition,” `CVPR`, pp. 1924–1932, 2016.

38.X. Peng, L. Wang, X. Wang, and Y. Qiao, “Bag of visual words and fusion methods for action recognition: Comprehensive study and good practice,” `Computer Vis. Image Understand`, vol. 150, pp. 109–125, 2016.
