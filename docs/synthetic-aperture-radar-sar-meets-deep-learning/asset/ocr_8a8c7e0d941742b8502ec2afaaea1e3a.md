SAR images. The GTP module can eliminate the effects of natural images, time series images and the performance of GAN. Secondly, the EUNet is designed to improve the features extraction and fusion capabilities of the U-Net. Compared with U-Net, we introduce BN-RRDC blocks, convolutional layers with s = 2, improved skip connections and SSAM. Although the EUNet has more parameters and more complex structure, the training difficulty will not increase. The reason is that there is the residual structures in the BN-RRDC block. Thirdly, a self-supervised training loss function is designed to address the difference of target pixel values between neighbors on the original noisy image. The loss function includes a reconstruction loss (MSE) and a regularization loss. Finally, visual and quantitative experiments on simulated and real-world SAR images show that the proposed SSEUNet notably reduces speckle noise with better preserving features, which exceed several state-of-the-art despeckling methods.

However, the inference speed of proposed SSEUNet needs to be improved. The proposed SSEUNet uses complex feature extraction block and sub-space attention modules, which leads to a longer time for evaluating an image. At the same time, the despeckling results of different data augmentation methods also need to be verified on the SAR images. In the future, we plan to explore two works. Firstly, we will explore a lightweight network to replace EUNet for improving inference speed. Secondly, the despeckling effects of different data augmentation methods will be verified.

Author Contributions: Conceptualization, G.Z.; Data curation, G.Z. and S.L.; Formal analysis, G.Z.; Investigation, G.Z. and X.L.; Methodology, G.Z. and X.L.; Resources, Z.L.; Software, G.Z.; Supervision, Z.L.; Validation, G.Z. and X.L.; Visualization, G.Z.; Writing—original draft, G.Z. and X.L. All authors have read and agreed to the published version of the manuscript.

Funding: This research was supported by the National Science Foundation for Distinguished Young Scholars, Grant Numbers 61906213.

Institutional Review Board Statement: Not applicable.

Informed Consent Statement: Not applicable.

Data Availability Statement: UC Merced land-use dataset is available are http://vision.ucmerced.edu/datasets, accessed on 27 October 2021. ICEYE SAR dataset is available at https://www.iceye.com/sar-data, accessed on 27 October 2021.

Conflicts of Interest: The authors declare no conflict of interest.

# References

+   1. Moreira, A.; Prats-Iraola, P.; Younis, M.; Krieger, G.; Hajnsek, I.; Papathanassiou, K.P. A tutorial on synthetic aperture radar. IEEE Geosci. Remote Sens. Mag. 2013, 1, 6–43. [CrossRef]
+   2. Yang, Z.; Wei, J.; Deng, J.; Gao, Y.; Zhao, S.; He, Z. Mapping Outburst Floods Using a Collaborative Learning Method Based on Temporally Dense Optical and SAR Data: A Case Study with the Baige Landslide Dam on the Jinsha River, Tibet. Remote Sens. 2021, 13, 2205. [CrossRef]
+   3. Qin, Y.; Xiao, X.; Wang, J.; Dong, J.; Ewing, K.; Hoagland, B.; Hough, D.J.; Fagin, T.D.; Zou, Z.; Geissler, G.L.; et al. Mapping Annual Forest Cover in Sub-Humid and Semi-Arid Regions through Analysis of Landsat and PALSAR Imagery. Remote Sens. 2016, 8, 933. [CrossRef]
+   4. Zhang, T.; Zhang, X.; Ke, X.; Zhan, X.; Shi, J.; Wei, S.; Pan, D.; Li, J.; Su, H.; Zhou, Y.; et al. LS-SSDD-v1.0: A Deep Learning Dataset Dedicated to Small Ship Detection from Large-Scale Sentinel-1 SAR Images. Remote Sens. 2020, 12, 2997. [CrossRef]
+   5. Zhang, T.; Zhang, X.; Ke, X.; Liu, C.; Xu, X.; Zhan, X.; Wang, C.; Ahmad, I.; Zhou, Y.; Pan, D.; et al. HOG-ShipCLSNet: A Novel Deep Learning Network with HOG Feature Fusion for SAR Ship Classification. IEEE Trans. Geosci. Remote Sens. 2021. [CrossRef]
+   6. Herzfeld, U.C.; Williams, S.; Heinrichs, J.; Maslanik, J.; Such, S. Geostatistical and Statistical Classification of Sea-Ice Properties and Provinces from SAR Data. Remote Sens. 2016, 8, 616. [CrossRef]
+   7. Singh, P.; Diwakar, M.; Shankar, A.; Shree, R.; Kumar, M. A Review on SAR Image and its Despeckling. Arch. Comput. Methods Eng. 2021. [CrossRef]
+   8. Argenti, F.; Lapini, A.; Bianchi, T.; Alparone, L. A Tutorial on Speckle Reduction in Synthetic Aperture Radar Images. IEEE Geosci. Remote Sens. Mag. 2013, 1, 6–35. [CrossRef]
+   9. Zhang, T.; Zhang, X.; Shi, J.; Wei, S.; Wang, J.; Li, J.; Su, H.; Zhou, Y. Balance Scene Learning Mechanism for Offshore and Inshore Ship Detection in SAR Images. IEEE Geosci. Remote Sens. Lett. 2020, 1–5. [CrossRef]