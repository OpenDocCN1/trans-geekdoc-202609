
24. Sun, K.; Xiao, B.; Liu, D.; Wang, J. Deep high-resolution representation learning for human pose estimation. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, Long Beach, CA, USA, 15–20 June 2019; pp. 5693–5703.

25. Sun, X.; Shang, J.; Liang, S.; Wei, Y. Compositional human pose regression. In Proceedings of the IEEE International Conference on Computer Vision, Venice, Italy, 22–29 October 2017; pp. 2602–2611.

26. Zhang, F.; Zhu, X.; Dai, H.; Ye, M.; Zhu, C. Distribution-aware coordinate representation for human pose estimation. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, Seattle, WA, USA, 13–19 June 2020; pp. 7093–7102.

27. Carreira, J.; Agrawal, P.; Fragkiadaki, K.; Malik, J. Human pose estimation with iterative error feedback. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, Las Vegas, NV, USA, 27–30 June 2016; pp. 4733–4742.

28. Li, J.; Bian, S.; Zeng, A.; Wang, C.; Pang, B.; Liu, W.; Lu, C. Human pose regression with residual log-likelihood estimation. In Proceedings of the IEEE/CVF International Conference on Computer Vision, Montreal, QC, Canada, 10–17 October 2021; pp. 11025–11034.

29. Røzeg, G.; Weinzappel, P.; Schmid, C. Lcr-net: Localization-classification-regression for human pose. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, Honolulu, HI, USA, 21–26 July 2017; pp. 3433–3441.

30. Pavllo, D.; Feichtenhofer, C.; Grangier, D.; Auli, M. 3D human pose estimation in video with temporal convolutions and semi-supervised training. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, Long Beach, CA, USA, 15–20 June 2019; pp. 7753–7762.

31. Wang, L.; Chen, Y.; Guo, Z.; Qian, K.; Lin, M.; Li, L.; Ren, J.S. Generalizing monocular 3D human pose estimation in the wild. In Proceedings of the IEEE/CVF International Conference on Computer Vision Workshops, Seoul, Republic of Korea, 27–28 October 2019; pp. 4024–4033.

32. Zeng, A.; Sun, X.; Huang, F.; Liu, M.; Xu, Q.; Lin, S. Snet: Improving generalization in 3D human pose estimation with a split-and-recombine approach. In Proceedings of the Computer Vision—ECCV 2020: 16th European Conference, Glasgow, UK, 23–28 August 2020; Proceedings, Part XIV 16; Springer: Berlin/Heidelberg, Germany, 2020; pp. 507–523.

33. Choi, H.; Moon, G.; Lee, K.M. Posemesh: Graph convolutional network for 3D human pose and mesh recovery from a 2D human pose. In Proceedings of the Computer Vision—ECCV 2020: 16th European Conference, Glasgow, UK, 23–28 August 2020; Proceedings, Part VII 16; Springer: Berlin/Heidelberg, Germany, 2020; pp. 769–787.

34. Fang, H.S.; Xu, Y.; Wang, W.; Liu, X.; Zhu, S.C. Learning pose grammar to encode human body configuration for 3D pose estimation. In Proceedings of the AAAI Conference on Artificial Intelligence, New Orleans, LA, USA, 2–7 February 2018; Volume 32.

35. Rezende, D.; Mohamed, S. Variational inference with normalization flows. In Proceedings of the International Conference on Machine Learning, Lille, France, 6–11 July 2015; PMLR; pp. 1530–1538.

36. Papandreou, G.; Zhu, T.; Chen, L.C.; Gidaris, S.; Templeton, J.; Murphy, K. Personlab: Person pose estimation and instance segmentation with a bottom-up, part-based, geometric embedding model. In Proceedings of the European Conference on Computer Vision (ECCV), Munich, Germany, 8–14 September 2018; pp. 269–286.

37. Kreiss, S.; Bertoni, L.; Alahi, A. Pfpa: Composite fields for human pose estimation. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, Long Beach, CA, USA, 15–20 June 2019; pp. 11977–11986.

38. Neff, C.; Sheth, A.; Furgarson, S.; Tabkhi, H. EfficientNet: Efficient scaling for lightweight high-resolution multi-person pose estimation. arXiv 2020. arXiv:2007.08090.

39. Tan, M.; Le, Q. EfficientNet: Rethinking model scaling for convolutional neural networks. In Proceedings of the International Conference on Machine Learning, Long Beach, CA, USA, 9–15 June 2019; PMLR; pp. 6105–6114.

40. Geng, Z.; Sun, X.; Xiao, B.; Zhang, Z.; Wang, J. Bottom-up human pose estimation via disentangled keypoint regression. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, Nashville, TN, USA, 20–25 June 2021; pp. 14676–14686.

**Disclaimer/Publisher’s Note:** The statements, opinions and data contained in all publications are solely those of the individual author(s) and contributor(s) and not of MDPI and/or the editor(s). MDPI and/or the editor(s) disclaim responsibility for any injury to people or property resulting from any ideas, methods, instructions or products referred to in the content.

## Detection of Small Lesions on Grape Leaves Based on Improved YOLOv7

Mingji Yang $^1$, Xinbo Tong $^1$ and Haisheng Chen $^{2,*}$

$^1$ Heilongjiang Province Key Laboratory of Laser Spectroscopy Technology and Application, Harbin University of Science and Technology, Harbin 150080, China; yangmingji@hrbust.edu.cn (M.Y.); 2120600050@stu.hrbust.edu.cn (X.T.)
$^2$ School of Undergraduate Education, Shenzhen Polytechnic University, Shenzhen 518055, China
*$^*$ Correspondence: hschen@szpt.edu.cn

**Abstract:** The precise detection of small lesions on grape leaves is beneficial for early detection of diseases. In response to the high missed detection rate of small target diseases on grape leaves, this paper adds a new prediction branch and combines an improved channel attention mechanism and an improved E-ELAN (Extended-Efficient Long-range Attention Network) to propose an improved algorithm for the YOLOv7 (You Only Look Once version 7) model. Firstly, to address the issue of low resolution for small targets, a new detection head is added to detect smaller targets. Secondly, in order to increase the feature extraction ability of E-ELAN components in YOLOv7 for small targets, asymmetric convolution is introduced into E-ELAN to replace the original $3 \times 3$ convolution in E-ELAN network to achieve multi-scale feature extraction. Then, to address the issue of insufficient extraction of information from small targets in YOLOv7, a channel attention mechanism was introduced and improved to enhance the network’s sensitivity to small-scale targets. Finally, the CIOU (Complete Intersection over Union) in the original YOLOv7 network model was replaced with SIoU (Structured Intersection over Union) to optimize the loss function and enhance the network’s localization ability. In order to verify the effectiveness of the improved YOLOv7 algorithm, three common grape leaf diseases were selected as detection objects to create a dataset for experiments. The results show that the average accuracy of the algorithm proposed in this paper is 2.7% higher than the original YOLOv7 algorithm, reaching 93.5%.

**Keywords:** YOLOv7; small target detection; E-ELAN network; attention mechanism

### 1. Introduction

The United States Department of Agriculture (USDA) released the “World Fresh apple, grape and pear market and Trade Report”, which shows that the 2022/2023 season global table grape production is expected to increase by 1.1 million tons to 27.3 million tons, achieving the fourth consecutive year of growth; China’s grape production will reach 12.6 million tons, the world’s largest grape producer [1]. At the same time, the output of the European Union and Turkey has increased significantly. However, Australia suffered heavy rains in the spring, and the attack of bacteria on grapes was extremely serious, affecting the yield of grapes. The wet conditions of South African grapes during the growing season have increased the pressure of fungal diseases, which have had a significant negative impact on the harvest, while the peak heat in December and January has brought sunburn to the grapes, and the lack of irrigation power during the high summer temperatures has resulted in crop losses [2].

When grapes grow, they are often eroded by diseases, which not only reduce the fruit and yield of grapes but even make the vineyard suffer a devastating blow in serious cases. Because grapes have important nutritional, medicinal and economic value, improving the efficiency of prevention and control of grape leaf diseases is the key to improving fruit
