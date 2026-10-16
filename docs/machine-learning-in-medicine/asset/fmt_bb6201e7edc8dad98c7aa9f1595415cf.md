
54. [54.](#C13_chapter6.xhtml#rref6_54) D. Böhning, “Multinomial logistic regression algorithm,” *Ann. Inst. Stat. Math.*, vol. 44, no. 1, pp. 197–200, 1992.

55. [55.](#C13_chapter6.xhtml#rref6_55) H. Soltanian-Zadeh, D. J. Peck, J. P. Windham, and T. Mikkelsen, “Brain tumor segmentation and characterization by pattern analysis of multispectral NMR images,” *NMR Biomed.*, vol. 11, no. 4–5, pp. 201–208, 1998.

56. [56.](#C13_chapter6.xhtml#rref6_56) J. Ashburner and K. J. Friston, “Unified segmentation,” *Neuroimage*, vol. 26, no. 3, pp. 839–851, 2005.

57. [57.](#C13_chapter6.xhtml#rref6_57) B. Patenaude, S. M. Smith, D. N. Kennedy, and M. Jenkinson, “A Bayesian model of shape and appearance for subcortical brain segmentation,” *Neuroimage*, vol. 56, no. 3, pp. 907–922, Jun. 2011.

58. [58.](#C13_chapter6.xhtml#rref6_58) G. Sahebzamani, M. Saffar, and H. Soltanian-Zadeh, “Machine learning based analysis of structural MRI for epilepsy diagnosis,” in *2019 4th International Conference on Pattern Recognition and Image Analysis (IPRIA)*, 2019, pp. 58–63.

59. [59.](#C13_chapter6.xhtml#rref6_59) E. Ben Othmen, M. Sayadi, and F. Fniaech, “3D gray level co-occurrence matrices for volumetric texture classification,” in *3rd International Conference on Systems and Control*, 2013, pp. 833–837.

60. [60.](#C13_chapter6.xhtml#rref6_60) I. Kononenko, “Estimating attributes: Analysis and extensions of RELIEF,” *Lect. Notes Comput. Sci. (including Subser. Lect. Notes Artif. Intell. Lect. Notes Bioinformatics)*, vol. 784 LNCS, pp. 171–182, 1994.

61. [61.](#C13_chapter6.xhtml#rref6_61) F. Mahmoudi, et al., “Data mining MR image features of select structures for lateralization of mesial temporal lobe epilepsy,” *PLoS One*, vol. 13, no. 8, pp. 1–19, 2018.

62. [62.](#C13_chapter6.xhtml#rref6_62) R. Kohavi and G. H. John, “Wrappers for feature subset selection,” *Artif. Intell.*, vol. 97, no. 1–2, pp. 273–324, Dec. 1997.

63. [63.](#C13_chapter6.xhtml#rref6_63) S. Shalev-Shwartz, Y. Singer, N. Srebro, and A. Cotter, “Pegasos: Primal estimated sub-gradient solver for SVM,” *Math. Program.*, vol. 127, no. 1, pp. 3–30, 2011.

64. [64.](#C13_chapter6.xhtml#rref6_64) H. G. Wieser, “Mesial temporal lobe epilepsy versus amygdalar epilepsy: Late seizure recurrence after initially amygdalotomy and regained seizure control following hippocampectomy,” *Epileptic Disord.*, vol. 2, no. 3, pp. 141–152, Oct. 2000.

# [CHAPTER 7](#C02a_toc.xhtml#rc7)

[Artificial Intelligence-Powered Ultrasound for Diagnosis and Improving Clinical Workflow](#C02a_toc.xhtml#rc7)

Zeynettin Akkus

Mayo Clinic

Rochester, Minnesota

## Contents

[7.1 Introduction](#C14_chapter7.xhtml#secc007_1)

[7.1.1 Ultrasound Imaging](#C14_chapter7.xhtml#secc007_1_1)

[7.1.2 Deep Learning](#C14_chapter7.xhtml#secc007_1_2)

[7.1.3 AI-Powered US in Radiology](#C14_chapter7.xhtml#secc007_1_3)

[7.1.4 AI-Powered US in Cardiology](#C14_chapter7.xhtml#secc007_1_4)

[7.2 Discussion and Outlook](#C14_chapter7.xhtml#secc007_2)

[References](#C14_chapter7.xhtml#references-5)

## [7.1 Introduction](#C14_chapter7.xhtml#rsecc007_1)

Artificial intelligence (AI) could be considered as a system that has the ability to observe its environment and takes actions to maximize the success of achieving its goals. Some examples of such a system that has the ability of sensing, reasoning, engaging, and learning are computer vision for understanding digital images, natural language processing for interaction between human and computer languages, voice recognition for recognition and translation of spoken languages, robotics and motion, planning and organization, and knowledge capture. Machine learning (ML) is a subsection of AI that covers the ability of a system to learn about data using supervised or unsupervised statistical and ML methods such as regression, support vector machines, decision trees, and neural networks. Deep learning (DL), which is a subclass of ML, learns a sequential chain of pivotal features from images that maximizes the success of learning process with its self-learning ability. This is different from statistical ML algorithms that require handcrafted feature selection \[[1](#C14_chapter7.xhtml#ref7_1)\] ([Figure 7.1](#C14_chapter7.xhtml#f7_1)). In this chapter, we will start with a brief background on ultrasound imaging and DL and will continue with a summary of the advances in ultrasound (US) powered with AI. These advances could potentially allow evaluating US data objectively, improving clinical workflow, and cutting healthcare costs. Subsequently, we present currently available AI-powered US applications in radiology and cardiology, go into challenges of current AI applications, and present our view on future trends in US powered with AI.

![FIGURE 7.1 The context of artificial intelligence, machine learning, and deep learning.](images/fig7_1.jpg)

FIGURE 7.1 The context of artificial intelligence, machine learning, and deep learning.

### [7.1.1 Ultrasound Imaging](#C14_chapter7.xhtml#rsecc007_1_1)

US imaging has been commonly used in routine clinical practice for diagnosis and visualization of internal organs (e.g. liver, kidney, and heart) and superficial structures (e.g. thyroid, breast, carotid artery, and muscles). An US transducer uses a piezoelectric material that converts electrical energy to mechanical movement, which transmits and receives sound waves with frequencies higher than human hearing. It generates US waves and transmits into the tissue and listens to receive the reflected sound wave (echo). The reflected echo signal is recorded in order to construct an image of the interrogated region. The sound waves travel through a soft tissue medium with approximately 1,540 m/s. The time of flight between the transmitted and received sound waves is used to locate objects and construct an image of the probed area. US has several advantages compared to magnetic resonance (MR), computed tomography (CT), and positron emission tomography (PET) imaging modalities. US is unharmful as it does not use destructive ionizing radiations like X-ray, CT, and PET. It is considerably lower in cost, handy for point-of-care (POCUS) applications, and provides actual real-time imaging. Since it is handy, it can be carried to a patient’s bedside for examining patients and monitoring changes over time. The disadvantages of US include operator dependability and being incapable of examining body areas that contain gas and bones.

Diverse image types are formed by using US ([Figure 7.2](#C14_chapter7.xhtml#f7_2)). The most common types used in clinics are:

![FIGURE 7.2 Sample US images showing different US modes. (a) A B-mode image of a heart: An apical four chamber view. (b) A color Doppler image of a thyroid nodule. (c) A Shear Wave Elastography map of a liver. (d) A CEUS image of a carotid artery.](images/fig7_2.jpg)

FIGURE 7.2 Sample US images showing different US modes. (a) A B-mode image of a heart: An apical four chamber view. (b) A color Doppler image of a thyroid nodule. (c) A Shear Wave Elastography map of a liver. (d) A CEUS image of a carotid artery.

*   **B-mode ultrasound:** It is also called as brightness mode (B-mode) and is the most well-known US image. An US beam is scanned across a tissue to construct a 2D cross-section image of the tissue.

*   **M-mode ultrasound:** Motion mode (M-mode) is used to examine motion over time. For example, it provides a single scan line of the heart and all of the reflectors along this line are shown along the time axis to measure the temporal resolution of the cardiac structures.
