
- 39. Zhang, J.; Li, W.; Li, Y. SAR Image Despeckling Using Multiconnection Network Incorporating Wavelet Features. IEEE Geosci. Remote Sens. Lett. 2020, 17, 1363–1367. [CrossRef]
- 40. Vitale, S.; Ferraioli, G.; Pascazio, V. Multi-Objective CNN-Based Algorithm for SAR Despeckling. IEEE Geosci. Remote Sens. 2020. [CrossRef]
- 41. Martino, G.D.; Poderico, M.; Poggi, G.; Riccio, D.; Verdoliva, L. Benchmarking framework for SAR despeckling. IEEE Trans. Geosci. Remote Sens. 2014, 52, 1596–1615. [CrossRef]
- 42. Laine, S.; Karras, T.; Lehtinen, J.; Aila, T. High-quality self-supervised deep image denoising. In Proceedings of the 33rd Conference on Neural Information Processing Systems (NeurIPS 2019), 8–14 December 2019; pp. 6968–6978.
- 43. Heinrich, M.; Stille, M.; Buzug, T. Residual U-Net Convolutional Neural Network Architecture for Low-Dose CT Denoising. Curr. Dir. Biomed. Eng. 2018, 4, 297–300. [CrossRef]
- 44. Guo, Y.; Chen, J.; Wang, J.; Chen, Q.; Cao, J.; Deng, Z.; Xu, Y.; Tan, M. Closed-Loop Matters: Dual Regression Networks for Single Image Super-Resolution. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, Virtual, 14–19 June 2020; pp. 5406–5415.
- 45. Zhou, Z.; Rahman Siddiquee, M.M.; Tajbakhsh, N.; Liang, J. UNet++: A Nested U-Net Architecture for Medical Image Segmentation. In Deep Learning in Medical Image Analysis and Multimodal Learning for Clinical Decision Support; Springer: Cham, Switzerland, 2018; pp. 3–11.
- 46. Li, X.; Chen, H.; Qi, X.; Dou, Q.; Fu, C.W.; Heng, P.A. H-DenseUNet: Hybrid Densely Connected UNet for Liver and Tumor Segmentation From CT Volumes. IEEE Trans. Med Imaging 2018, 37, 2663–2674. [CrossRef]
- 47. Li, W.; Chakraborty, M.; Fenner, D.; Faber, J.; Zhou, K.; Ruempker, G.; Stoecker, H.; Srivastava, N. EPick: Multi-Class Attention-based U-shaped Neural Network for Earthquake Detection and Seismic Phase Picking. arXiv 2021, arXiv:2109.02567.
- 48. Cheng, S.; Wang, Y.; Huang, H.; Liu, D.; Fan, H.; Liu, S. NBNet: Noise Basis Learning for Image Denoising with Subspace Projection. arXiv 2020, arXiv:2012.15028.
- 49. Wang, X.; Yu, K.; Wu, S.; Gu, J.; Liu, Y.; Dong, C.; Loy, C.C.; Qiao, Y.; Tang, X. ESRGAN: Enhanced Super-Resolution Generative Adversarial Networks. Eur. Conf. Comput. Vis. 2018, 11133, 63–79.
- 50. He, K.; Zhang, X.; Ren, S.; Sun, J. Delving deep into rectifiers: Surpassing-human level performance on imagenet classification. In Proceedings of the IEEE International Conference on Computer Vision, Santiago, Chile, 11–18 December 2015; pp. 1026–1034.
- 51. Diederik, P.K.; Jimmy, L.B. Adam: A method for stochastic optimization. arXiv 2014, arXiv:1412.6980.
- 52. Yi, Y.; Shawn, N. Bag-Of-Visual-Words and Spatial Extensions for Land-Use Classification. In Proceedings of the 18th SIGSPATIAL International Conference on Advances in Geographic Information Systems, San Jose, CA, USA, 2–5 November 2010; pp. 270–279.
- 53. Liu, C.; Tupin, F.; Gousseau, Y. Training CNNs on speckled optical dataset for edge detection in SAR images. ISPRS J. Photogramm. Remote Sens. 2020, 170, 88–102. [CrossRef]
- 54. Stringham, C.; Farquharson, G.; Castelletti, D.; Quist, E.; Riggi, L.; Eddy, D.; Soenen, S. The Capella X-band SAR Constellation for Rapid Imaging. In Proceedings of the IEEE International Geoscience and Remote Sensing Symposium, Yokohama, Japan, 28 July–2 August 2019; pp. 9248–9251.
- 55. Lattari, F.; Gonzalez Leon, B.; Asaro, F.; Rucci, A.; Prati, C.; Matteucci, M. Deep Learning for SAR Image Despeckling. Remote Sens. 2019, 11, 1532. [CrossRef]
- 56. Wang, Z.; Bovik, A.C.; Sheikh, H.R.; Simoncelli, E.P. Image quality assessment: From error visibility to structural similarity. IEEE Trans. Image Process. 2004, 13, 600–612. [CrossRef]
- 57. Lee, J.S.; Pottier, E. Polarimetric Radar Imaging: From Basics to Applications; CRC Press: Boca Raton, FL, USA, 2009.
- 58. Feng, H.; Hou, B.; Gong, M. SAR image despeckling based on local homogeneous-region segmentation by using pixel-relativity measurement. IEEE Trans. Geosci. Remote Sens. 2011, 49, 2724–2737. [CrossRef]
- 59. Deledalle, C.A.; Denis, L.; Tabti, S.; Tupin, F. MuLoG, or How to apply Gaussian denoisers to multi-channel SAR speckle reduction. IEEE Trans. Image Process. 2017, 26, 4389–4403. [CrossRef]
- 60. Anfinsen, S.N.; Doulgeris, A.P.; Eltoft, T. Estimation of the equivalent number of looks in polarimetric synthetic aperture radar imagery. IEEE Trans. Geosci. Remote Sens. 2009, 47, 3795–3809. [CrossRef]

Article

## A Novel Guided Anchor Siamese Network for Arbitrary Target-of-Interest Tracking in Video-SAR

Jinyu Bao, Xiaoling Zhang *, Tianwen Zhang, Jun Shi and Shunjun Wei

School of Information and Communication Engineering, University of Electronic Science and Technology of China, Chengdu 611731, China; 201811011909@std.uestc.edu.cn (J.B.); twzhang@std.uestc.edu.cn (T.Z.); shijun@uestc.edu.cn (J.S.); weishunjun@uestc.edu.cn (S.W.)
* Correspondence: xlzhang@uestc.edu.cn

**Abstract:** Video synthetic aperture radar (Video-SAR) allows continuous and intuitive observation and is widely used for radar moving target tracking. The shadow of a moving target has the characteristics of stable scattering and no location shift, making moving target tracking using shadows a hot topic. However, the existing techniques mainly rely on the appearance of targets, which is impractical and costly, especially for tracking targets of interest (TOIs) with high diversity and arbitrariness. Therefore, to solve this problem, we propose a novel guided anchor Siamese network (GASN) dedicated to arbitrary TOI tracking in Video-SAR. First, GASN searches for matching areas in the subsequent frames with the initial area of the TOI in the first frame are conducted, returning the most similar area using a matching function, which is learned from general training without TOI-related data. With the learned matching function, GASN can be used to track arbitrary TOIs. Moreover, we also constructed a guided anchor subnet, referred to as GA-SubNet, which employs the prior information of the first frame and generates sparse anchors of the same shape as the TOIs. The number of unnecessary anchors is therefore reduced to suppress false alarms. Our method was evaluated on simulated and real Video-SAR data. The experimental results demonstrated that GASN outperforms state-of-the-art methods, including two types of traditional tracking methods (MOSSE and KCF) and two types of modern deep learning techniques (Siamese-FC and Siamese-RPN). We also conducted an ablation experiment to demonstrate the effectiveness of GA-SubNet.

**Keywords:** video synthetic aperture radar (Video-SAR); moving target tracking; guided anchor Siamese network (GASN)

**Citation:** Bao, J.; Zhang, X.; Zhang, T.; Shi, J.; Wei, S. A Novel Guided Anchor Siamese Network for Arbitrary Target-of-Interest Tracking in Video-SAR. *Remote Sens.* **2021**, *13*, 4504. https://doi.org/10.3390/rs13224504

Academic Editor: Fabio Rocca

Received: 27 August 2021
Accepted: 1 November 2021
Published: 9 November 2021

**Publisher's Note:** MDPI stays neutral with regard to jurisdictional claims in published maps and institutional affiliations.

![](img/828a5d28a36454f7b3332df93f35492f_117_0.png)

**Copyright:** © 2021 by the authors. Licensee MDPI, Basel, Switzerland. This article is an open access article distributed under the terms and conditions of the Creative Commons Attribution (CC BY) license (https://creativecommons.org/licenses/by/4.0/).

### 1. Introduction

Video synthetic aperture radar (Video-SAR) provides high-resolution SAR images at a faster frame rate, which is conducive to the continuous and intuitive observation of ground moving targets. Due to this advantage, Video-SAR brings about important applications in SAR moving target tracking [1]. Since the Sandia National Laboratory (SNL) of the United States first obtained high-resolution SAR images in 2003 [2], many scholars have investigated the problem of moving target tracking in Video-SAR [3–7]. However, due to different angles of illumination, the scattering characteristics of moving targets change with the movement of the platform. Worse still, it is difficult to track a moving target directly because the imaging results of the moving target usually shift from their true position.

Fortunately, shadow is caused by the ground being blocked by the moving target. Due to the absence of energy reflection, shadows appear at the real position of the moving target in the SAR image, with the advantage of a constant grayscale [8]. Therefore, shadow-aided moving target tracking has become a hot topic in Video-SAR. In recent years, many scholars have worked on shadow-aided moving target tracking in Video-SAR [9–11]. Wang et al. [9] fully considered the constant grayscale of shadows and used data multiplexing to achieve moving target tracking. Zhao et al. [10] applied the saliency-based detection mechanism and used spatial–temporal information to achieve moving target
