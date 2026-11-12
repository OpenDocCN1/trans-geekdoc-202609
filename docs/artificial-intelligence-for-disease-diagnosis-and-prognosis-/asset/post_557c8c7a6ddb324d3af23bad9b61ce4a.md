
![](img/bffdb4a72252285ac92f0fad78a7f104_186_0.png)

Figure 10.1 Samples of the BCSS dataset.

![](img/bffdb4a72252285ac92f0fad78a7f104_186_1.png)

Figure 10.2 Samples of the BreakHis dataset.

### 10.2.4 Breast Cancer Histopathological Database (BreakHis)

The Breast Cancer Histopathological Image Classification (BreakHis) is made up of 9109 microscopic images of breast tumor tissue collected from 82 people at various magnification levels (40×, 100×, 200×, and 400×) as shown in Figure 10.2. There are 2480 benign and 5429 malignant samples in this collection (700×460 pixels, 3-channel RGB, 8-bit depth in each channel, PNG format) [10].

![](img/bffdb4a72252285ac92f0fad78a7f104_187_0.png)

Figure 10.3 Samples of the PCam dataset.

### 10.2.5 PatchCamelyon (PCam) Dataset

PatchCamelyon is a dataset for picture categorization. It is made up of 327,680 color pictures (96 × 96 px) taken from lymph node histopathologic scans. Each image has a binary label that indicates the existence of metastatic tissue as shown in Figure 10.3. PCam is a new machine learning benchmark that is larger than CIFAR10, smaller than ImageNet, and trainable on a single GPU [11].

### 10.2.6 Kumar Dataset

The Kumar dataset contains 30 1000 × 1000 picture tiles taken at 40 magnifications from The Cancer Genome Atlas (TCGA) database for seven organs (6 breast, 6 livers, 6 kidneys, 6 prostates, 2 bladders, 2 colons, and 2 stomachs) as shown in Figure 10.4. Each nucleus's boundary is completely marked within each image [12].

## 10.3 RELATED WORK

Graham et al. [6] propose Dense Steerable Filter CNNs (DSF-CNNs), which use group convolutions in a densely connected framework with multiple rotatable copies of each filter. In comparison to traditional filters, each filter is specified as a linear combination of steerable basis filters, allowing precise rotation, and reducing the number of trainable parameters. W. Lafarge et al. [7] focused on histopathology image analysis applications where it is desirable that the machine learning models do not collect the arbitrary global orientation information of the observed tissues. Three separate histopathology image analysis tasks are used to test the proposed system. Zhou et al. [8] developed a new smooth truncated loss that modifies losses to minimize outlier disturbance. As a result, the network may concentrate on learning from reliable and informative data, which improves generalization capability intrinsically. Experiments on the MICCAI Multi-Organ-Nuclei-Segmentation challenge in 2018 confirmed the efficacy of our proposed technique. On numerous independent multi-tissue histology picture datasets, Graham et al. [9] exhibit state-of-the-art performance relative to previous approaches. We present a new dataset of Hematoxylin and Eosin-stained colorectal adenocarcinoma picture tiles, which contain 24,319 exhaustively annotated nuclei with associated class labels, as part of this effort. Weiler et al. [10] extend He's weight initialization approach to filters specified as a linear combination of atomic filters. Numerical experiments reveal that when the number of sampled filter orientations increases, the sample complexity increases significantly, indicating that the network generalizes learned patterns across orientations. S. Cohen et al. [11] propose Group-equivariant Convolutional Neural Networks (G-CNNs), a logical generalization of convolutional neural networks that exploits symmetries to reduce sample complexity. G-CNNs make use of G-convolutions, a novel form of layer with significantly more weight sharing than standard convolution layers. We describe a network and training technique that heavily depends on data augmentation to make better use of the given annotated samples. A contracting path is used to collect context, while a symmetrically expanding path is used to ensure exact localization.

## 10.4 CONCLUSION

Deep learning has made great progress in supervised learning and is continuing to improve radiologists’ workflow and decision-making. This chapter included an overview of breast cancer datasets and the efficacy of several deep learning architectures for breast cancer screening for several related works. Furthermore, the goal of this work

### TABLE 10.1 Breast Cancer Datasets and Specifications

| Year | Authors | Model | Tasks | Dataset | Results (%) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2020 | Graham et al. [5] | CIA-Net | Breast Tumour Classification Nuclear Segmentation Tumour Classification | PCam Kumar | F1-Score = 0.874 Dice = 0.891 |
| 2020 | W. Lafarge et al. [13] | Roto-Translation Equivariant Convolutional Networks | Breast Tumor Classification Data Augmentation Multi-tissue Nucleus Segmentation Translation | PCam Kumar | Dice = 0.811 |
| 2019 | Zhou et al. [14] | CIA-Net | Instance Segmentation Multi-Tissue Nucleus Semantic Segmentation | Kumar | Dice = 0.818 |
| 2018 | Graham et al. [15] | HoVer-Net | Classification Multi-Tissue Nucleus Nuclear Segmentation | CoNSeP | Dice = 0.826 |
| 2018 | Weiler et al. [16] | Steerable G-CNN | Breast Tumour Classification Segmentation Multi-Tissue Nucleus | PCam Kumar | Dice = 0.791 |
| 2016 | S. Cohen et al. [17] | G-CNN | Breast Tumour Classification Segmentation Multi-tissue Nucleus | PCam Kumar | Dice = 0.856 |
| 2015 | Ronneberger et al. | U-Net | Cell Segmentation Colorectal Microscopy Image Segmentation Lesion Segmentation Lung Nodule | CVC-ClinicDB Kumar | F1-Score = 0.7783 AUC = 0.9772 |

was to gain a clear grasp of current developments in deep learning for breast tumor identification.

## Bibliography

- 1. D. Houfani, S. Slatnia, O. Kazar, N. Zerhouni, A. Merizig, and H. Saouli, “Machine learning techniques for breast cancer diagnosis: Literature review,” Adv. Intell. Syst. Comput., vol. 1103 AISC, February, pp. 247–254, 2020, doi: 10.1007/978-3-030-36664-3_28.

- 2. F. Paquin, J. Rivnay, A. Salleo, N. Stingelin, and C. Silva, “Multi-phase semicrystalline microstructures drive exciton dissociation in neat plastic semiconductors,” J. Mater. Chem. C, vol. 3, January 2019, pp. 10715–10722, doi: 10.1039/b000000x.

- 3. M. A. Rahman and R. C. Muniyandi, “An enhancement in cancer classification accuracy using a two-step feature selection method based on artificial neural networks with 15 neurons,” Symmetry (Basel), vol. 12, no. 2, 2020, doi: 10.3390/sym12020271.

- 4. S. Dabeer, M. M. Khan, and S. Islam, “Cancer diagnosis in histopathological image: CNN-based approach,” Informatics Med. Unlocked, vol. 16, no. May, p. 100231, 2019, doi: 10.1016/j.imu.2019.100231.

- 5. S. Graham, D. Epstein, and N. Rajpoot, “Dense steerable filter CNNs for exploiting rotational symmetry in histology images,” IEEE Trans. Med. Imaging, vol. 39, no. 12, pp. 4124–4136, 2020, doi: 10.1109/TMI.2020.3013246.

- 6. S. Elmuogy, N. A. Hikall, and E. Hassan, “An efficient technique for CT scan images classification of COVID-19,” vol. 40, pp. 5225–5238, 2021, doi: 10.3233/JIFS-201985.

- 7. E. Hassan, M. Shams, N. A. Hikall, and S. Elmuogy, “Plant seedlings classification using transfer,” no. July, pp. 3–4, 2021.

- 8. “BRACS,” [Online]. Available: https://www.bracs.icar.cnr.it/.

- 9. BCSS, “No Title,” [Online]. Available: https://github.com/PathologyDataScience/BCSS.

- 10. “BreakHis,” [Online]. Available: https://web.inf.ufpr.br/vri/databases/breast-cancer-histopathological-database-breakhis/.

- 11. “PCam,” [Online]. Available: https://github.com/basveeling/pcam.

- 12. “Kumar,” [Online]. Available: https://monuseg.grand-challenge.org/Data/.

- 13. M. W. Lafarge, E. J. Bekkers, J. P. W. Pluim, R. Duits, and M. Veta, “Roto-translation equivariant convolutional networks: Application to histopathology image analysis,” Med. Image Anal., vol. 68, no. 2, 2021, doi: 10.1016/j.media.2020.101849.

- 14. C. I. Aggregation, Y. Zhou, O. F. Onder, Q. Dou, and E. Tsougenis, “CIA-Net: Robust nuclei instance segmentation,” vol. 1, pp. 1–12.

- 15. S. Graham, Q. D. Vu, S. E. A. Raza, A. Azam, and Y. W. Tsang, “HoVer-Net: Simultaneous segmentation and classification of nuclei in multi-tissue histology images,” pp. 1–18.

- 16. M. Weiler, F. A. Hamprecht, and M. Storath, “Learning steerable filters for rotation equivariant CNNs,” Proc. IEEE Comput. Soc. Conf. Comput. Vis. Pattern Recognit., pp. 849–858, 2018, doi: 10.1109/CVPR.2018.00095.

- 17. M. Welling and M. W. U. V. A. NI, “Group equivariant convolutional networks,” vol. 48, 2016.
