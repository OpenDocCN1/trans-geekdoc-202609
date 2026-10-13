

# 参考文献

Shin, J., Kim, S., Kang, S., Lee, S. W., Paik, J., Abidi, B., & Abidi, M. (2005). Optical flow-based real-time object tracking using non-prior training active feature model. *Real-Time Imaging*, 11(3), 204–218. doi:10.1016/j.rti.2005.03.006

Shiraga, K., Makihara, Y., Muramatsu, D., Echigo, T., & Yagi, Y. (2016). Geinet: View-invariant gait recognition using a convolutional neural network. *Proceedings International Conference on Biometrics (ICB)* (pp. 1-8). IEEE. doi:10.1109/ICB.2016.7550060

Sivapalan, S., Chen, D., Denman, S., Sridharan, S., & Fookes, C. (2013). Histogram of weighted local directions for gait recognition. *Proceedings IEEE Conference on Computer Vision and Pattern Recognition Workshops* (pp. 125-130). doi:10.1109/CVPRW.2013.26

Tan, D., Huang, K., Yu, S., & Tan, T. (2006). Efficient night gait recognition based on template matching. *Proceedings International Conference on Pattern Recognition* (Vol. 3, pp. 1000-1003).

Tao, D., Li, X., Wu, X., & Maybank, S. J. (2007). General tensor discriminant analysis and gabor features for gait recognition. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 29(10), 1700–1715. doi:10.1109/TPAMI.2007.1096

Viola, P., Jones, M. J., & Snow, D. (2005). Detecting pedestrians using patterns of motion and appearance. *International Journal of Computer Vision*, 63(2), 153–161. doi:10.1007/s11263-005-6644-8

Wang, L., Ning, H., Tan, T., & Hu, W. (2004). Fusion of static and dynamic body biometrics for gait recognition. *IEEE Transactions on Circuits and Systems for Video Technology*, 14(2), 149–158. doi:10.1109/TCSVT.2003.821972

Wang, L., Tan, T., Ning, H., & Hu, W. (2003). Silhouette analysis-based gait recognition for human identification. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 25(12), 1505–1518. doi:10.1109/TPAMI.2003.1251144

Xu, D., Huang, Y., Zeng, Z., & Xu, X. (2011). Human gait recognition using patch distribution feature and locality-constrained group sparse representation. *IEEE Transactions on Image Processing*, 21(1), 316–326. doi:10.1109/TIP.2011.2160956

Yan, C., Zhang, B., & Coenen, F. (2015). Multi-attributes gait identification by convolutional neural networks. *Proceedings International Congress on Image and Signal Processing* (pp. 642-647). IEEE. doi:10.1109/CISP.2015.7407957

Yu, S., Tan, D., & Tan, T. (2006). Modelling the effect of view angle variation on appearance-based gait recognition. *Proceedings Asian Conference on Computer Vision* (pp. 807-816). Berlin, Germany: Springer. doi:10.1007/11612032_81

Yu, S., Tan, D., & Tan, T. (2006). A framework for evaluating the effect of view angle, clothing and carrying condition on gait recognition. *Proceedings International Conference on Pattern Recognition* (Vol. 4, pp. 441-444).

Yu, S., Tan, T., Huang, K., Jia, K., & Wu, X. (2009). A study on gait-based gender classification. *IEEE Transactions on Image Processing*, 18(8), 1905–1910. doi:10.1109/TIP.2009.2020535

Zhao, N., Zhang, L., Du, B., Zhang, L., Tao, D., & You, J. (2016). Sparse tensor discriminative locality alignment for gait recognition. *Proceedings International Joint Conference on Neural Networks* (pp. 4489-4495). doi:10.1109/IJCNN.2016.7727787

Zheng, S., Zhang, J., Huang, K., He, R., & Tan, T. (2011). Robust view transformation model for gait recognition. *Proceedings IEEE International Conference on Image Processing* (pp. 2073-2076). doi:10.1109/ICIP.2011.6115889

# 第 12 章

**Avila Jayapalan**  
SASTRA University (Deemed), India

## 摘要

随着无线技术的飞速发展，正交频分复用（`OFDM`）近年来越来越受欢迎。`OFDM` 构成了当前许多无线传输标准的基本骨干。它是一种多载波调制方案，克服了因多径传播导致的 `ISI`（符号间干扰）而需要均衡器的问题。在本工作中，利用源编码、信道编码、`IFFT-FFT`、扰码器、循环前缀和信号映射器等各种模块开发了一个基于 `OFDM` 的收发器。为确保数据传输安全，哈达玛矩阵与数据进行 `XOR`（异或）运算。这为传输的图像提供了一定程度的低级保护。`LabVIEW` 已被用作处理工具来开发收发器，并利用通用软件无线电外设（`USRP`）测试了开发的原型。

## 绪论

无线系统的发展因其成本较低且易于使用，为全球连接敞开了大门。但是，即使存在这些优势，仍需应对一个称为多径衰落的严重问题，它会导致符号间干扰（`ISI`）或串扰。

正交频分复用（`OFDM`）（Gouda, Hussien, Ragab, Anwar, & Gouda, 2017）解决了上述问题。它是一种独特的 `FDM`（频分复用）类型，用户获得的一组子载波在频域中重叠（Bartalwar & Deepa, 2017）。然而，这些子载波经过专门设计，彼此正交，这使它们能够在没有任何干扰的情况下占用相同的带宽。这反过来又消除了对保护频带的需求。因此，子载波可以紧密排列以提高信道效率。

在 `OFDM` 中，大带宽的高速数据流被分割成并行的、较慢的、较低带宽的子流，称为子载波（Salwa & Eldin, 2017）。这些子载波以直流（`D.C`）两侧的载波频率为中心。随着带宽的增加，其中的子载波数量也随之增加。子载波的放置方式是：在一个子载波的峰值处，所有其他子载波均具有零分量。这样的子载波称为正交子载波。通过确保所有子载波具有相同的符号持续时间 `Ts` 且子载波间隔保持在 `f=1/Ts` 的等距，实现了正交性。

在时域中，这些子载波将表现为这些载波频率上的永恒正弦波。然而，为了在这些子载波上传输数据，它们被加载了调制符号，这些符号代表数字调制方案（如正交相移键控（`QPSK`）和 M 阵正交幅度调制（`QAM`））（Sklar & Ray, 2001）的星座点。

## 图像获取

本工作强调仅传输灰度图像（Saravanan, 2010）。灰度图像是一种图像类型，其中每个像素元素中的值仅代表光的量，即强度。灰度级由 `2^n` 给出，其中 `n` 是考虑的位数。由于重点是 8 位灰度图像，因此有 `2^8` 即 256 个级别，范围从 0 到 255。考虑的输入数据是一幅 `256*256` 的灰度图像。

## 安全性

加密是对数据进行编码的过程，使得只有拥有加密密钥的人才能访问数据（Balouch, Aslam, & Ahmed, 2017）。在发射端，阵列元素根据加密密钥进行打乱；而在接收端，接收到的数据根据相同的密钥进行重新排序，从而恢复原始传输的数据。为了确保通过 `OFDM` 收发器传输的图像具有一定程度的低级安全性，哈达玛序列被 `XOR`（异或）运算。

哈达玛矩阵是一个由 1 和 -1 两个值组成的方阵，其行彼此正交。这可以用两个基本术语来解释。从几何术语来看，每一对行都是相互垂直的向量；从组合术语来看，可以说每一对行恰好有一半的元素匹配。某些哈达玛矩阵被用作纠错码，如哈达玛码。哈达玛矩阵也用于低规模加密目的，因为将图像与同尺寸的哈达玛矩阵相乘会产生一幅打乱的图像（Lee, Shahab, Kader & Shin, 2016）。

## USRP

