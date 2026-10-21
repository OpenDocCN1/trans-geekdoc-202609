
通过适当的更新调整目标外观，以最大化前景-背景可分性。与AGAME相比，专注于判别能力而非整个分布，有望带来更轻量、更快速的算法。

这在判别式VOS方法FRTM（Robinson等人，2020）中得到了证实，该方法还用时空一致性取代了AGAME中使用的掩码传播。

与ATOM跟踪器相似的目标模型

$$\mathbf{s} = D(\mathbf{x}; \mathbf{w}) = \mathbf{w}_2 * (\mathbf{w}_1 * \mathbf{x}) \tag{9.68}$$

使用加权MOSSE准则在线训练

$$\mathcal{L}_D(\mathbf{w}) = \sum_k \gamma_k \|\mathbf{v}_k \circ (\mathbf{y}_k - U(D(\mathbf{x}_k)))\|^2 + \sum_j \lambda_j \|\mathbf{w}_j\|^2, \tag{9.69}$$

其中$\mathbf{v}_k$是用于增加小目标对象重要性的平衡权重，$U$执行双线性上采样，$\gamma_k$是用于控制数据集中不同样本影响的权重。

与跟踪方法类似，在线训练使用时间窗口。来自该窗口的数据存储在内存$M$中。

目标模型学习的伪代码如下：

1. 初始化内存$M$，训练判别式目标模型$D$
2. 从下一帧提取特征$x$
3. 应用目标模型并生成粗分数图$s$
4. 使用细化网络将$s$增强为目标掩码$y$
5. 用新样本$(x, y, \gamma)$更新$M$
6. 每八帧使用$M$重新优化判别式目标模型
7. 返回步骤2。

步骤4中使用的细化模型在VOS训练阶段进行离线训练。粗分数图$s$和细化掩码$y$的作用类似于AGAME，但AGAME使用粗预测进行模型更新，而FRTM使用细化预测进行训练，并采用双线性上采样。FRTM通过这些改变变得非常高效，并实现了实时VOS算法。

与从ATOM到DiMP的转变类似（其中损失被泛化），VOS目标模型也可以针对粗分割预测之外的表示进行优化。假设目标模型（9.68）产生的是某种特征图而不是粗分割图，并且细化分割是通过解码器而不是上采样模块获得的。在这种情况下，目标模型的损失可以在特征图域中计算，方法是对分割掩码进行编码，并计算编码后的分割与目标模型输出之间的加权$L_2$误差（Bhat等人，2020）。

这种“学习如何学习”的方法将VOS学习与度量学习联系起来。其他有趣的问题包括泛化到无监督VOS、多实例VOS以及VIS。

## 9.6 结论

本章描述的从简单模板匹配到视频分割的发展，是计算机视觉中许多应用的基石之一：视频分析、视觉监控、遥感、增强现实（AR）、视觉机器人控制和自动驾驶汽车只是所开发方法的一些主要应用领域。这些应用中的大多数都需要实时处理、鲁棒的模型和准确的预测。

例如，AR需要低延迟的视频实时处理，以减少AR晕动症。AR的无标记方法在很大程度上依赖于视觉跟踪（Chandaria等人，2007）。相机姿态与虚拟姿态的对齐也可用于控制无人机。例如，可以使用DCF跟踪器对来自无人机的RGB视频实现虚拟牵引（Häger等人，2016）。

本章讨论的输入数据大多局限于RGB序列，但类似的方法也可以应用于其他光谱范围或深度数据。例如，基于热红外相机的列车安全系统可以减轻与大型动物、人和轨道上障碍物碰撞的后果（Berg等人，2015）。在这项工作中，轨道上的异常检测使用基于MOSSE的滤波器进行。此外，例如使用红外相机（Källhammer等人，2007）和RGB相机检测行人的汽车安全系统，也受益于RGB和热跟踪相结合（Kristan等人，2019b）的进展。

DCF的方法不仅适用于跟踪和异常检测，而且可以按照尺度空间跟踪的精神进一步推广。例如，沿海地区船舶的视觉导航可以实现GPS级精度（Grelsson等人，2020）。这里，利用傅里叶变换DCF实现的效率，将（一段）地平线与从数字高程模型采样的大量模型地平线进行实时匹配。

随着VOS和VIS方法转向实时处理，出现了新的应用领域和现有应用领域中的新功能。例如，AR系统可以利用分割对象的对齐来进一步提高精度和延迟。自动驾驶汽车和高级驾驶辅助系统已经频繁使用逐帧语义分割，但强大的VIS算法可能会进一步提高性能。船舶导航不再需要依赖单独的地平线提取，而是可以将地平线分析集成到匹配中。

显然，潜在的滥用和伦理上有问题的应用也受益于技术发展：当局或公司对人们进行大规模监控已经是实际存在的案例。同样，VOS方法可用于伪造视频或制作深度伪造。最后，可以想到许多军事应用——特别是使用红外图像。研究的开放性和开源实现的可获得性是科学进步的关键，但不幸的是，也是滥用和虚假应用的关键。

## 致谢

本章的大部分内容描述了过去七年在林雪平计算机视觉实验室与Fahad Khan以及多名博士生和硕士生合作开发的方法和结果，主要要提到Martin Danelljan、Gustav Häger、Andreas Robinson、Joakim Johnander、Felix Järemo-Lawin、Goutam Bhat、Amanda Berg和Susanna Gladh。

本章涵盖的研究工作部分得到了KAW通过Wallenberg人工智能、自主系统和软件项目WASP的资助，瑞典研究委员会通过EMC2、NCNN和ELLIIT项目的资助，SSF通过CUAS和SymbiCloud项目的资助，以及LiU通过CENIIT的资助。

## 参考文献

- Baker, S., Matthews, I., 2004. Lucas-Kanade 20 years on: a unifying framework. International Journal of Computer Vision 56 (3), 221–255.
- Berg, A., Öfjäll, K., Ahlberg, J., Felsberg, M., 2015. Detecting rails and obstacles using a train-mounted thermal camera. In: Lecture Notes in Computer Science (Including Subseries Lecture Notes in Artificial Intelligence and Lecture Notes in Bioinformatics), LNCS, vol. 9127, pp. 492–503.
- Berg, A., Johnander, J., Durand De Gevigney, F., Ahlberg, J., Felsberg, M., 2019. Semi-automatic annotation of objects in visual-thermal video. In: Proceedings – 2019 International Conference on Computer Vision Workshop, ICCVW 2019, pp. 2242–2251.
- Bhat, G., Johnander, J., Danelljan, M., Khan, F.S., Felsberg, M., 2018. Unveiling the power of deep tracking. In: Lecture Notes in Computer Science (Including Subseries Lecture Notes in Artificial Intelligence and Lecture Notes in Bioinformatics), LNCS, vol. 11206, pp. 493–509.
- Bhat, G., Danelljan, M., Van Gool, L., Timofte, R., 2019. Learning discriminative model prediction for tracking. In: Proceedings of the IEEE International Conference on Computer Vision, vol. 2019-October, pp. 6181–6190.
- Bhat, G., Lawin, F.J., Danelljan, M., Robinson, A., Felsberg, M., Van Gool, L., Timofte, R., 2020. Learning what to learn for visual object segmentation. In: Vedaldi, A., Bischof, H., Brox, T., Frahm, J.-M. (Eds.), Computer Vision – ECCV 2020. Springer International Publishing, Cham, pp. 777–794.
- Bolme, D.S., Beveridge, J.R., Draper, B.A., Lui, Y.M., 2010. Visual object tracking using adaptive correlation filters. In: Proceedings of the IEEE Computer Society Conference on Computer Vision and Pattern Recognition, pp. 2544–2550.
- Bracewell, R.N., 1995. Two-Dimensional Imaging. Prentice Hall Signal Processing Series. Prentice Hall, Englewood Cliffs.
- Chandaria, J., Thomas, G., Bartczak, B., Koeser, K., Koch, R., Becker, M., Bleser, G., Stricker, D., Wohlleber, C., Felsberg, M., Gustafsson, F., Hol, J.D., Schön, T.B., Skoglund, J., Slycke, P.J., Smeitz, S., 2007. Realtime camera tracking in the MATRIS project. SMPTE Motion Imaging Journal 116 (7–8), 266–271.
- Chatfield, K., Simonyan, K., Vedaldi, A., Zisserman, A., 2014. Return of the devil in the details: delving deep into convolutional nets. In: British Machine Vision Conference.
- Chen, Q.-S., Defrise, M., Deconinck, F., 1994. Symmetric phase-only matched filtering of Fourier-Mellin transforms for image registration and recognition. IEEE Transactions on Pattern Analysis and Machine Intelligence 16, 1156–1168.
- Chéron, G., Laptev, I., Schmid, C., 2015. P-CNN: pose-based CNN features for action recognition. In: 2015 IEEE International Conference on Computer Vision (ICCV), pp. 3218–3226.
- Dalal, N., Triggs, B., 2005. Histograms of oriented gradients for human detection. In: 2005 IEEE Computer Society Conference on Computer Vision and Pattern Recognition (CVPR 2005), vol. 1, pp. 886–893.
- Danelljan, M., Häger, G., Khan, F.S., Felsberg, M., 2014a. Accurate scale estimation for robust visual tracking. In: BMVC 2014 – Proceedings of the British Machine Vision Conference 2014.
- Danelljan, M., Khan, F.S., Felsberg, M., Van De Weijer, J., 2014b. Adaptive color attributes for real-time visual tracking. In: Proceedings of the IEEE Computer Society Conference on Computer Vision and Pattern Recognition, pp. 1090–1097.
- Danelljan, M., Häger, G., Khan, F.S., Felsberg, M., 2015. Learning spatially regularized correlation filters for visual tracking. In: Proceedings of the IEEE International Conference on Computer Vision, vol. 2015-December, pp. 4310–4318.
- Danelljan, M., Häger, G., Khan, F.S., Felsberg, M., 2016a. Adaptive decontamination of the training set: a unified formulation for discriminative visual tracking. In: Proceedings of the IEEE Computer Society Conference on Computer Vision and Pattern Recognition, 2016-December, pp. 1430–1438.
- Danelljan, M., Häger, G., Khan, F.S., Felsberg, M., 2016b. Convolutional features for correlation filter based visual tracking. In: Proceedings of the IEEE International Conference on Computer Vision, vol. 2016-February, pp. 621–629.
- Danelljan, M., Robinson, A., Khan, F.S., Felsberg, M., 2016. Beyond correlation filters: Learning continuous convolution operators for visual tracking. LNCS, vol. 9909.
