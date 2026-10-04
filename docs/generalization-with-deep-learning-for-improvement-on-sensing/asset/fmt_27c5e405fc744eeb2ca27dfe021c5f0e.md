
Notable recent works on action recognition that have improved the state-of-the-art results are: (i) `ST-ResNet` [[26](#chap2.xhtml#fsr26)] method, which uses a very deep architecture combined with cross-stream residual connections; and (ii) `TSN` method [[25](#chap2.xhtml#fsr25)], which uses a very deep architecture combined with a consensus function at the final layer of the network. From [Table 6](#chap2.xhtml#tab6), we see that with the same two input modalities, `HACNN` outperforms `ST-ResNet` [[26](#chap2.xhtml#fsr26)] by 1.2% on `UCF-101` and 5.5% on `HMDB51`. Similarly, comparing with `TSN` method [[25](#chap2.xhtml#fsr25)], we improve by 0.6% on `UCF-101` and 3.4% on `HMDB51`. In order to confirm that the performance gain is mainly due to `HACNN` and not due to the additional frames used in our model, we tested the `TSN` with 32 frames and found no performance improvement. As explained before, we used the standard dense testing procedure to generate 10 samples for each input frame. We believe that the effect of number of frames reduces beyond a certain number.

Other interesting comparisons are with the (1) two-stream `LSTM` [[49](#chap2.xhtml#fsr49)], which attaches an `LSTM` to a two-stream `Inception` and (2) `LRCN` method [[28](#chap2.xhtml#fsr28)], which combines `CNN` with an `LSTM` to model long-term temporal dynamics. Again, we observe that our method outperforms the former by a significant 6.0% on `UCF-101` and the latter by 2.9% on `UCF-101` and 7.1% on `HMDB51`. (3) Our method achieves much better results than more complicated aggregation approaches, such as `ActionVlad` [[50](#chap2.xhtml#fsr50)].

This clearly demonstrates the effectiveness of the hierarchical aggregation strategy adopted in `HACNN`. Actions in `HMDB` dataset consist of complex wide ranging motions that are difficult to capture without explicit temporal modeling. The larger improvement on the `HMDB` dataset again strengthens our claim that `HACNN` is effective in modeling long-range dynamics. Note that we do not combine `iDT` features as done by several earlier methods [[26](#chap2.xhtml#fsr26), [46](#chap2.xhtml#fsr46)].

### 5.Conclusion

In this chapter, we presented a novel hierarchically aggregated deep ConvNets model to better capture long-term dynamics present in action videos. The proposed hierarchical model consists of special aggregation functions acting upon the output feature maps of a subConvNet at each level. The aggregation function has the effect of pooling most discriminative information from the neighboring segments. When repeated over multiple levels, this captures complex dynamics present in the video. We performed detailed experiments to investigate various aspects of the model such as the choice of different aggregation functions and their usage at various levels of the hierarchy. We observed that aggregation functions are useful at each level and that a spatial layout preserving function plays an important role in achieving superior performance. We also showed that the whole system is end-to-end trainable and achieves state-of-the-art performance on two challenging action recognition datasets.

### References

[1](#chap2.xhtml#fs1).Z. Chen, Q. Zhu, Y. C. Soh, and L. Zhang, “Robust human activity recognition using smartphone sensors via ct-pca and online SVM,” *IEEE Trans. Indust. Inform*, vol. 13, no. 6, pp. 3070–3080, 2017.

2.Z. Chen, L. Zhang, Z. Cao, and J. Guo, “Distilling the knowledge from handcrafted features for human activity recognition,” *IEEE Trans. Indust. Informa*., vol. 14, no. 10, pp. 4334–4342, 2018.

3.Z. Chen, L. Zhang, C. Jiang, Z. Cao, and W. Cui, “Wifi CSI based passive human activity recognition using attention based BLSTM,” *IEEE Trans. Mobile Comput*., vol. 18, no. 11, pp. 2714–2724, 2018.

[4](#chap2.xhtml#fs4).Z. Chen, C. Jiang, S. Xiang, J. Ding, M. Wu, and X. Li, “Smartphone sensor based human activity recognition using feature fusion and maximum full a posteriori,” *IEEE Trans. Instrum. Measure*., vol. 69\. no. 7, pp. 3992–4001, 2019.

[5](#chap2.xhtml#fs5).M. Brand and V. Kettnaker, “Discovery and segmentation of activities in video”. *IEEE Trans. Pattern Analy. Mach. Intell*., vol. 22, Aug. 2000.

[6](#chap2.xhtml#fs6).Z. Cai, L. Wang, X. Peng, and Y. Qiao, “Multi-view super vector for action recognition,” *IEEE Conf. Computer Vision and Pattern Recognition*, pp. 596–603, 2014.vol. 69, no. 7, pp. 3992–4001.

[7](#chap2.xhtml#fs7).A. A. Efros, A. C. Berg, G. Mori, and J. Malik, “Recognizing action at a distance,” *IEEE Int. Conf. Computer Vision*, Nice, France, October 2003, October 2003.

8.A. F. Bobick and J. W. Davis, “The recognition of human movement using temporal templates,” *IEEE Trans. Pattern Analy. Mach. Intell*., vol. 23, no. 3, pp. 257–267, 2001.

9.I. Laptev and T Lindeberg, “Space-time interest points,” *Int. J. Comput. Vis*., vol. 64, no. (2–3), 107–123, Sept. 2005.

[10](#chap2.xhtml#fs10).H. Wang, A. Klaser, C. Schmid, and C.-L. Liu, “Action Recognition by Dense Trajectories,” in *CVPR*, 2011.

[11](#chap2.xhtml#fs11).M. Bruni, T. Uricchio, L. Seidenari, and A. Del Bimbo, “Do textual descriptions help action recognition?” *Proc. 2016 ACM on Multimedia Conference*, ACM, pp. 645–649, 2016.

[12](#chap2.xhtml#fs12).J. C. Niebles, H. Wang, and L. Fei-Fei, “Unsupervised learning of human action categories using spatial-temporal words,” *Int. J. Comput. Vis*., vol. 79, no. 3, pp.299–318, 2008.

13.M. Brand, N. Oliver, and A. Pentland, “Coupled hidden markov models for complex action recognition,” *IEEE Conf. Computer Vision and Pattern Recognition*, 1997.

14.P. Turaga, R. Chellappa, V. S. Subrahmanian, and O. Udrea, “Machine recognition of human activities: A survey,” *IEEE Transactions on Circuits and Systems for Video Technology*, 2008.

[15](#chap2.xhtml#fs15).Y. Tian, Q. Ruan, G. An, and Y. Fu, “Action recognition using local consistent group sparse coding with spatio-temporal structure,” *Proc. 2016 ACM on Multimedia Conference*, ACM, pp. 317–321, 2016.

[16](#chap2.xhtml#fs16).K. Soomro, A. R. Zamir, and M. Shah, “Ucf101: A dataset of 101 human actions classes from videos in the wild.” Crcv-tr-12-01, UCF, 2012.

[17](#chap2.xhtml#fs17).E. G. T. P. H. Kuehne, H. Jhuang, and T. Serre, “HMDB: A large video database for human motion recognition,” *ICCV*, 2011.

[18](#chap2.xhtml#fs18).I. S. A. Krizhevsky and G. E. Hinton, “Imagenet classification with deep convolutional neural networks,” *NIPS*, 2012.

19.C. Szegedy, W. Liu, Y. Jia, P. Sermanet, S. Reed, D. Anguelov, D. Erhan, V. Vanhoucke, and A. Rabinovich, “Going deeper with convolutions,” *CVPR*, 2015.

[20](#chap2.xhtml#fs20).K. Simonyan and A. Zisserman, “Very deep convolutional networks for large-scale image recognition,” *ICLR*, 2014.

[21](#chap2.xhtml#fs21).K. He, X. Zhang, S. Ren, and J. Sun, “Deep residual learning for image recognition,” 2015, arXivpreprint arXiv: 1512.03385.

[22](#chap2.xhtml#fs22).J. Long, E. Shelhamer, and T. Darrell, “Fully convolutional networks for semantic segmentation,” *IEEE Conf. Computer Vision and Pattern Recognition*, pp.3431–3440, 2015.

[23](#chap2.xhtml#fs23).A. J. Y. L. J. Tompson, R. Goroshin and C. Bregler, “Efficient object localization using convolutional networks,” *CVPR*, 2015.

[24](#chap2.xhtml#fs24).D. K. F. Schroff and J. Philbin, “Facenet: A uni-fied embedding for face recognition and clustering,” *CVPR*, 2015.

[25](#chap2.xhtml#fs25).L. Wang, Y. Xiong, Z. Wang, Y. Qiao, D. Lin, X. Tang, and L. Van Gool, “Temporal segment networks: Towards good practices for deep action recognition,” *European Conf. Comput. Vision*, pp. 20–36. Springer, 2016.

[26](#chap2.xhtml#fs26).C. Feichtenhofer, A. Pinz, and R. P. Wildes, “Spatiotemporal residual networks for video action recognition,” *NIPS*, 2016.

[27](#chap2.xhtml#fs27).S. Ioffe and C. Szegedy, “Batch Normalization: Accelerating deep network training by reducing internal covariate shift,” 2015, arXiv preprint arXiv.1502.03167.
