
distance from the operating table, creating a logistic barrier for surgeons interested in viewing slides with the pathologists. Moreover, the process for creating high-quality pathology slides is time- and labor-intensive. Consequently, pathologists will call into an OR with a diagnosis 30–45 min after a specimen is collected. The inefficiency of this process isolates surgeons from histologic data and limits the way it can be used to inform surgical decision-making.

Given the challenges in the modern neuropathology workflow, AI holds great promise in a number of regards: (1) verifying that lesional tissue has been collected, (2) assisting in tissue diagnosis, (3) helping to define surgical endpoints in tumors without gross boundaries, and (4) in the future, predicting actionable and diagnostic molecular markers. In fixed tissue, AI has been applied to classification of epithelial versus stromal regions in breast and colon cancer [57], differentiating necrotic and nonnecrotic regions [58], and differentiating high- and low-grade gliomas [59]. That said, the application of AI for assisting in diagnosis only addresses the challenges associated with establishing diagnosis in neuropathology. With conventional histologic workflows, many of the barriers related to tissue transport and processing remain. To fully leverage the opportunity created by rapid advances in AI-assisted pathologic diagnosis, marriage with a technique for rapid histology is essential.

## Approaches to rapid histology interpretations

To this end, several methods for slide-free histology have been proposed and validated to varying degrees. MUSE, stimulated Raman histology (SRH), and light-sheet microscopy are among the most promising tools for imaging unprocessed or minimally processed biological specimens (Fig. 7.6).

While numerous techniques for slide-free histology have been proposed, only SRH has been incorporated into an AI-based diagnostic pipeline validated for brain tumor diagnosis in a clinical setting. Hollon et al. adapted the Inception-V2 CNN to diagnose the 10 most common brain tumors using SRH images and deployed their software on a bedside SRH imager. In a head-to-head clinical trial of 278 patients, Hollon et al. demonstrated that an autonomous diagnostic pathway utilizing SRH and a CNN could predict diagnosis with performance that was noninferior to board-certified neuropathologists interpreting conventional histologic slides in the same patients [61]. The accuracy of both arms was approximately 94% and interestingly the errors in both arms were entirely nonoverlapping (Fig. 7.7). The authors of this study therefore conclude that the SRH + CNN pathway can be used as a standalone method for brain tumor diagnosis when pathology resources are unavailable and as a method to improve diagnostic accuracy in neuropathology, even in well-staffed centers. Although the authors limited trial inclusion to common types of brain tumors, they also offered a means of differentiating common and unusual histologic classes in an effort to make their system universal to application in all central nervous system neoplasms. The algorithm was also used to develop a semantic segmentation tool capable of depicting the areas of a histologic image most likely to contain lesional tissue (Fig. 7.8). The authors also conclude that given the features that their CNN used to classify brain tumors, similar algorithms could be developed for tumors of other organs in the future.

It is interesting to speculate whether AI-based image enhancement prior to the classification learning step would have improved the performance of the latter.

## FIGURE 7.6

### (A) Microscopy with ultraviolet surface excitation
![](img/ec668102bd6cbe5645156f246a7c2e8b_148_0.png)

### (B) Light-sheet microscopy
![](img/ec668102bd6cbe5645156f246a7c2e8b_148_1.png)

### (C) Stimulated Raman histology
![](img/ec668102bd6cbe5645156f246a7c2e8b_148_2.png)

Methods for slide-free histology including (A) microscopy with ultraviolet surface excitation, (B) light sheet microscopy, and (C) stimulated Raman histology (SRH), all of which can be performed on minimally processed or unprocessed tissue to generate diagnostic histologic images without the need for the resources of a conventional pathology lab. Each technique relies on optical, rather than physical sectioning of imaged tissue, simplifying the workflow required to generate a diagnostic histologic image. SRH has unique value as a modality for bedside histology as no staining, clearing, or handling of the tissue is required to generate a histological image. In SRH, fresh specimens can be placed into an imager at bedside which rapidly creates a virtual H&E microscopic image through relatively simple spectral band combination and recoloring. To this end, academic-industrial partnership has resulted in the first FDA-registered imager, now employed in several operating rooms across the United States.

> Adapted with permission from Orringer DA, Camelo-Piragua S, Fast and slide-free imaging. Nature Biomedical Engineering, 2017;1(12):926–928. https://doi.org/10.1038/s41551-017-0172-z.

![](img/ec668102bd6cbe5645156f246a7c2e8b_149_0.png)

## FIGURE 7.7

Prospective clinical trial of SRH plus CNN versus conventional H&E histology. (A) The prediction probabilities for the ground truth classes are plotted in descending order by medical center with indication of correct (green) or incorrect (red) classification. (B) Multiclass confusion matrices for both the control arm and experimental arm. Mistakes in the control arm, traditional H&E histology with pathologist were mostly misclassification of malignant gliomas (10/17). The glial tumors had the highest error rate in the SRH plus CNN arm (9/14). Common tumors, including ependymoma, medulloblastoma, and pilocytic astrocytomas were also misclassified, likely due to insufficient number of cases for model training, resulting in lower mean class accuracy compared with the control arm. These errors are likely to improve with additional SRH training data. SRH, stimulated Raman histology; CNN, convolutional neural networks (CNN).

*Adapted with permission from Hollon TC, et al., Near real-time intraoperative brain tumor diagnosis using stimulated Raman histology and deep neural networks.* Nature Medicine, 2020;26(1):52–58. https://doi.org/10.1038/s41591-019-0715-9.

![](img/ec668102bd6cbe5645156f246a7c2e8b_150_0.png)

## FIGURE 7.8

Semantic segmentation. (A) An SRH mosaic image of a specimen from a glioblastoma patient contains areas of (B) dense tumor infiltration, tumor-brain interface as well as the gliotic peritumoral regions. Tiles from the mosaic are fed into a semantic segmentation algorithm (C) that are classified by a convolutional neural network (CNN) which then assigns a numerical value, depicted by color (red green or blue) corresponding to the likelihood that a given region contains tumor, nondiagnostic tissue, or nonlesional tissue. The classifier provides the likelihood of class membership among 10 categories of the most common brain tumors (D). The entire mosaic can be predicted as a heatmap for each of the 10 categories, 3 of which are shown here (E). SRH, stimulated Raman histology; CNN, convolutional neural networks (CNN).

*Adapted with permission from Hollon TC, et al., Near real-time intraoperative brain tumor diagnosis using stimulated Raman histology and deep neural networks. Nature Medicine, 2020;26(1):52–58. https://doi.org/10.1038/s41591-019-0715-9.*

- [25] Perez L, Wang J. The effectiveness of data augmentation in image classification using deep learning. ArXiv:171204621 Cs. Dec. 2017.
- [26] Ciompi F, et al. The importance of stain normalization in colorectal tissue classification with convolutional networks. In: 2017 IEEE 14th international symposium on biomedical imaging (ISBI 2017); 2017. p. 160–3. https://doi.org/10.1109/ISBI.2017.7950492.
- [27] Janowczyk A, Basavanhally A, Madabhushi A. Stain normalization using sparse AutoEncoders (StaNoSA): application to digital pathology. Computerized Medical Imaging and Graphics 2017;57:50–61. https://doi.org/10.1016/j.compmedimag.2016.05.003.
- [28] Ruifrok AC, Johnston DA. Quantification of histochemical staining by color deconvolution. Analytical and Quantitative Cytology and Histology 2001;23(4):291–9.
- [29] Azevedo Tosta TA, de Faria PR, Neves LA, do Nascimento MZ. Computational normalization of H&E-stained histological images: progress, challenges and future potential. Artificial Intelligence in Medicine 2019;95:118–32. https://doi.org/10.1016/j.artmed.2018.10.004.
- [30] Roy S, kumar Jain A, Lal S, Kini J. A study about color normalization methods for histopathology images. Micron 2018;114:42–61. https://doi.org/10.1016/j.micron.2018.07.005.
- [31] Bug D, et al. Context-based normalization of histological stains using deep convolutional features. In: Deep learning in medical image analysis and multimodal learning for clinical decision support, Cham; 2017. p. 135–42. https://doi.org/10.1007/978-3-319-67558-9_16.
- [32] F. G. Zanjani, S. Zinger, and B. E. Bejnordi, “Histopathology stain-color normalization using generative neural networks,” p. 16.
- [33] Chen X, Duan Y, Houthooft R, Schulman J, Sutskever I, Abbeel P. InfoGAN: interpretable representation learning by information maximizing generative adversarial nets. In: Lee DD, Sugiyama M, Luxburg UV, Guyon I, Garnett R, editors. Advances in neural information processing systems 29. Curran Associates, Inc.; 2016. p. 2172–80.
- [34] Kingma DP, Welling M. Auto-encoding variational bayes. ArXiv:13126114 Cs Stat. May 2014.
- [35] Tellez D, et al. Quantifying the effects of data augmentation and stain color normalization in convolutional neural networks for computational pathology. Medical Image Analysis 2019;58:101544. https://doi.org/10.1016/j.media.2019.101544.
- [36] Rivenson Y, Liu T, Wei Z, Zhang Y, de Haan K, Ozcan A. PhaseStain: the digital staining of label-free quantitative phase microscopy images using deep learning. Light: Science & Applications 2019;8(1):1–11. https://doi.org/10.1038/s41377-019-0129-y.
- [37] Combalia M, Perez-Anker J, Garcia-Herrera A. Digitally stained confocal microscopy through deep learning. In: Proceedings of the 2nd international conference on medical imaging with deep learning (PMLR), 102; 2019. p. 121–9.
- [38] Borhani N, Bower AJ, Boppart SA, Psaltis D. Digital staining through the application of deep neural networks to multi-modal multi-photon microscopy. Biomedical Optics Express 2019;10(3):1339–50. https://doi.org/10.1364/BOE.10.001339.
- [39] Nygate YN et al. HoloStain: holographic virtual staining of individual biological cells. p. 20.
- [40] Christiansen EM, et al. In silico labeling: predicting fluorescent labels in unlabeled images. Cell 2018;173(3):792–803. https://doi.org/10.1016/j.cell.2018.03.040. e19.
- [41] Rana A, Yauney G, Lowe A, Shah P. Computational histological staining and destaining of prostate core biopsy RGB images with generative adversarial neural networks.
