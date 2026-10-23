detrimental. Therefore, data augmentations must not be overused, especially since it takes more resources to train (either storage or processing time), which does not always lead to a better result. Test Time Augmentations showed an additional performance gain compared to augmentations applied only during training.

We hope this study can be used as a guide for future research to optimize object detection in a limited set of radar imagery or as an inspiration for investigating alternative methods to augment radar images. The search for effective data augmentation methods can be expensive; thus, automated approaches can save time and computing resources. These approaches have not yet been studied in this article. Furthermore, generating new data through generative models or the use of simulations remain interesting avenues to explore.

Author Contributions: Conceptualization, S.W. and P.S.; methodology, S.W.; software, S.W. and A.G.; validation, S.W., P.S. and A.G.; formal analysis, S.W.; investigation, S.W.; resources, S.W.; data curation, S.W.; writing—original draft preparation, S.W.; writing—review and editing, S.W., P.S. and A.G.; visualization, S.W.; supervision, P.S. and A.G.; project administration, S.W. and P.S. All authors have read and agreed to the published version of the manuscript.

Funding: This research received no external funding.

Data Availability Statement: Not applicable.

Conflicts of Interest: The authors declare no conflict of interest.

# References

+   1. Kang, M.; Baek, J. Sar image change detection via multiple-window processing with structural similarity. Sensors 2021, 21, 6645. [CrossRef] [PubMed]
+   2. Jing, H.; Sun, X.; Wang, Z.; Chen, K.; Diao, W.; Fu, K. Fine Building Segmentation in High-Resolution SAR Images Via Selective Pyramid Dilated Network. IEEE J. Sel. Top. Appl. Earth Obs. Remote Sens. 2021, 14, 6608–6623. [CrossRef]
+   3. Shahzad, M.; Maurer, M.; Fraundorfer, F.; Wang, Y.; Zhu, X.X. Buildings detection in VHR SAR images using fully convolution neural networks. IEEE Trans. Geosci. Remote Sens. 2019, 57, 1100–1116. [CrossRef]
+   4. Sun, Y.; Hua, Y.; Mou, L.; Zhu, X.X. CG-Net: Conditional GIS-aware Network for Individual Building Segmentation in VHR SAR Images. IEEE Trans. Geosci. Remote Sens. 2022, 60, 1–15. [CrossRef]
+   5. Xia, J.; Yokoya, N.; Adriano, B.; Zhang, L.; Li, G.; Wang, Z. A Benchmark High-Resolution GaoFen-3 SAR Dataset for Building Semantic Segmentation. IEEE J. Sel. Top. Appl. Earth Obs. Remote Sens. 2021, 14, 5950–5963. [CrossRef]
+   6. Sun, C.; Shrivastava, A.; Singh, S.; Gupta, A. Revisiting Unreasonable Effectiveness of Data in Deep Learning Era. Proc. IEEE Int. Conf. Comput. Vis. 2017, 843–852. [CrossRef]
+   7. Maggiori, E.; Tarabalka, Y.; Charpiat, G.; Alliez, P. Can semantic labeling methods generalize to any city? The inria aerial image labeling benchmark. Int. Geosci. Remote Sens. Symp. 2017, 2017, 3226–3229. [CrossRef]
+   8. Van Etten, A.; Lindenbaum, D.; Bacastow, T.M. SpaceNet: A Remote Sensing Dataset and Challenge Series. arXiv 2018, arXiv:1807.01232.
+   9. Shermeyer, J.; Hogan, D.; Brown, J.; Van Etten, A.; Weir, N.; Pacifici, F.; Hansch, R.; Bastidas, A.; Soenen, S.; Bacastow, T.; et al. SpaceNet 6: Multi-sensor all weather mapping dataset. IEEE Comput. Soc. Conf. Comput. Vis. Pattern Recognit. Work. 2020, 2020, 768–777. [CrossRef]
+   10. Shorten, C.; Khoshgoftaar, T.M. A survey on Image Data Augmentation for Deep Learning. J. Big Data 2019, 6, 60. [CrossRef]
+   11. Ronneberger, O.; Fischer, P.; Brox, T. U-Net: Convolutional Networks for Biomedical Image Segmentation. In Proceedings of the International Conference on Medical Image Computing and Computer-Assisted Intervention, Munich, Germany, 5–9 October 2015.
+   12. Bisla, D.; Choromanska, A.; Berman, R.S.; Stein, J.A.; Polsky, D. Towards automated melanoma detection with deep learning: Data purification and augmentation. IEEE Comput. Soc. Conf. Comput. Vis. Pattern Recognit. Work. 2019, 2019, 2720–2728. [CrossRef]
+   13. Nalepa, J.; Myller, M.; Kawulok, M. Hyperspectral Data Augmentation. arXiv 2019, arXiv:1903.05580.
+   14. Illarionova, S.; Nesteruk, S.; Shadrin, D.; Ignatiev, V.; Pukalchik, M.; Oseledets, I. Object-Based Augmentation for Building Semantic Segmentation: Ventura and Santa Rosa Case Study. In Proceedings of the IEEE/CVF International Conference on Computer Vision, Montreal, BC, Canada, 11–17 October 2021; pp. 1659–1668. [CrossRef]
+   15. Yang, L.; Huang, R.; Huang, J.; Lin, T.; Wang, L.; Mijiti, R.; Wei, P.; Tang, C.; Shao, J.; Li, Q.; et al. Semantic Segmentation Based on Temporal Features: Learning of Temporal-Spatial Information From Time-Series SAR Images for Paddy Rice Mapping. IEEE Trans. Geosci. Remote Sens. 2021, 60, 1–16. [CrossRef]
+   16. Zhong, Z.; Zheng, L.; Kang, G.; Li, S.; Yang, Y. Random erasing data augmentation. In Proceedings of the AAAI Conference on Artificial Intelligence, New York, NY, USA, 7–15 February 2020; pp. 13001–13008. [CrossRef]