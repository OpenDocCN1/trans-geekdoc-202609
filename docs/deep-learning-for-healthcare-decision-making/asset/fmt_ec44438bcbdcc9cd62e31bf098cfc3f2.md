
## Discussion and Future Work

The feature exaggeration offered by DenseNets is also subject to erroneous extraction due to the use of dense skip connection. The model cannot potentially utilize all the parameters that could be amended by using the features on other convoluted network architecture. An architecture can be designed to integrate these components or even design a novel approach based on previous architectures.

Another potential problem with the use of these models is that these products are utilized by clinicians who are unskilled with respect to the use of advanced deep learning tools. An interface that can allow them to conveniently access and store files and perform various operations on them is a necessity to actively involve neural networking at the clinical level. Easy-to-use platforms that have networks trained to segment and classify images at the back end have to be designed for increased usage capability.

Our architecture was trained using MRI images as they are one of the most widely used imaging techniques for gliomas. But MRI images are known to produce images with non-uniform intensity which can manifest as varying changes in the pixel values of the images produced. Therefore, the architecture can be modified to accommodate image files produced by other high end imaging tools such as PET and CT. The DenseNet architecture implemented in this project can also be trained to segment other tumors by training them on the particular tumor image set. This can diversify the role of the neural net in different aspects of the diagnostic process.

There can still be modifications made to further classify particular sections of the gliomas beyond the basic high grade and low grade division. It is also necessary to integrate neural network structures that can process glioma images obtained from other imaging tools apart from MRI devices to offer a state-of-the-art resource for medical professions to work on with minimal skill specialization required.

## References

1. Omuro A., DeAngelis L.M. ‘Glioblastoma and Other Malignant Gliomas: A Clinical Review.’ *Jama.*; 310(17) \[2013\] 1842–1850. doi:`10.1001/jama.2013.280319`
2. Louis D.N., Holland E.C., Cairncross J.G. ‘Glioma classification: a molecular reappraisal.’ *The American journal of pathology* vol. 159,3 \[2001\]: 779–786. doi:`10.1016/S0002-9440(10)61750-6`
3. Ohgaki H., Kleihues P. ‘Epidemiology and etiology of gliomas.’ *Acta Neuropathol* \[2005\] 109, 93–108 `https://doi.org/10.1007/s00401-005-0991-y`
4. Li Sun, Songtao Zhang, Hang Chen and Lin Luo. ‘Brain Tumor Segmentation and Survival Prediction Using Multimodal MRI Scans With Deep Learning.’ \[2015\]
5. Yue Cao, Pia C. Sundgren, Christina I. Tsien, Thomas T. Chenevert, Larry Junck. ‘Physiologic and Metabolic Magnetic Resonance Imaging in Gliomas’ *Journal of Clinical Oncology* \[2006\] 24:8, 1228–1235
6. Villanueva-Meyer J.E., Mabray M.C., Cha S. ‘Current Clinical Brain Tumor Imaging’, *Neurosurgery*, 81, \[2017\], 397–415
7. El-Sayed A. El-Dahshan, Heba M. Mohsen, Kenneth Revett, Abdel-Badeeh M. Salem. ‘Computer-aided diagnosis of human brain tumor through MRI: A survey and a new algorithm’ *Expert Systems with Application* \[2014\], 5525–5545
8. Riccardo Miotto, Fei Wang, Shuang Wang, Xiaoqian Jiang, Joel T. Dudley. ‘Deep learning for healthcare: review, opportunities and challenges’ *Briefings in Bioinformatics*, Volume 19, Issue 6, \[2018\] Pages 1236–1246 `https://doi.org/10.1093/bib/bbx044`
9. Lele Chen, Yue Wu Adora, M. DSouza, Anas Z. Abidin, Axel Wismüller, Chenliang Xu. ‘MRI Tumor Segmentation with Densely Connected 3D CNN’, University of Rochester, New York \[2017\]
10. Shi Z., He L., Suzuki K., Nakamura T., Itoh H. ‘Survey on Neural Networks Used for Medical Image Processing.’ *International journal of computational science* vol. 3,1 \[2009\] 86–100.
11. Zaharchuk G., Gong E., Wintermark M., Rubin D., Langlotz C.P. ‘Deep Learning in Neuroradiology’ *American Journal of Neuroradiology*, \[2018\]
12. Jégou1 S., Drozdzal M., Vazquez D., Romero A., Bengio Y. ‘The One Hundred Layers Tiramisu: Fully Convolutional DenseNets for Semantic Segmentation’ Computer Vision Center, Barcelona. \[2017\]
13. Sérgio Pereira, Adriano Pinto, Victor Alves, and Carlos A. Silva. ‘Brain Tumor segmentation using convolutional neural networks for MRI images’ *Ieee Transactions On Medical Imaging*, VOL. 35, NO. 5, \[2016\]
14. Zhao X., Wu Y., Song G., Li Z., Fan Y., Zhang Y. ‘Brain tumor segmentation using a fully convolutional neural network with conditional random fields’ MICCAI, Athens, Greece, October 17, 2016, 75-87 \[2016\].
15. Kamnitsas, K., Ledig, C., Newcombe, V. F. J., Simpson, J. P., Kane, A. D., Menon, D. K., Rueckert, D., Glocker, B. ‘Efficient multi-scale 3d CNN with fully connected CRF for accurate brain lesion segmentation’ *Medical Image Analysis* 36, 61–78 \[2017\].
16. Trevethan, Robert. “Sensitivity, Specificity, and Predictive Values: Foundations, Pliabilities, and Pitfalls in Research and Practice.” *Frontiers in public health* vol. 5 307. 20 Nov. 2017, doi:`10.3389/fpubh.2017.00307`
17. Miller A.S., Blott B.H., Hames T.K. ‘Review of neural network applications in medical imaging and signal processing’. *Med Biol Eng Comput.* \[1992\] Sep; 30(5):449–464.
18. Gao Huang, Zhaung Liu, Killian Q. Weinberger, Laurens van der Maaten. “Densely connected convolutional networks”, *Ieee Explore* – \[2018\]
19. Jean Stawiaski1. “A pre-trained Dense-net encoder for brain tumor segmentation.”, 19 Nov 2018
20. Ashia C. Wilson, Rebecca Roelofs, Mitchell Stern, Nathan Srebroy, Benjamin Recht. “The Marginal Value of Adaptive Gradient Methods in Machine Learning.”, University of California Berkeley \[2016\]
21. Hao Dong, Guang Yang, Fangde Liu, Yuanhan Mo, Yike Guo. “Automatic Brain Tumor Detection and Segmentation Using U-Net Based Fully Convolutional Networks”, *Data Science Journal of London*\-2017.
22. B. Menze et al. “The multimodal brain tumor image segmentation benchmark (BRATS),” *IEEE Trans. Med. Imag.*, vol. 34, no. 10, \[2015\] pp. 1993–2024.
23. Martin Kolarˇík, Radim Burget, Václav Uher, Kamil R. íha, Malay Kishore Dut. “Optimized high resolution 3D Dense-U-NET network for brain and spine segmentation”, *MDPI applied sciences* January 2019.

# 5 Automatic Liver Tumor Segmentation from Computed Tomography Images Based on 2D and 3D Deep Neural Networks

William Tustumi, Guilherme P. Telles and Helio Pedrini

Institute of Computing, University of Campinas, Campinas-SP 13083-852, Brazil

## Abstract
