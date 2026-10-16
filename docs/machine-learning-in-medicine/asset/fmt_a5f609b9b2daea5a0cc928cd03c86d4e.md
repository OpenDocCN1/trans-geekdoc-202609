
27. [\[27\]](#C12_chapter5.xhtml#rref5_27) K. He, X. Zhang, S. Ren, and J. Sun, Deep residual learning for image recognition, `Presented at the 2016 IEEE Conference on Computer Vision and Pattern Recognition (CVPR)`, Las Vegas, NV, 2016.

28. [\[28\]](#C12_chapter5.xhtml#rref5_28) G. Huang, Z. Liu, L. Van Der Maaten, and K. Q. Weinberger, Densely connected convolutional networks, `CVPR`, vol. 1, no. 2, p. 3, 2017.

29. [\[29\]](#C12_chapter5.xhtml#rref5_29) B. Geraldo Junior, S. V. da Rocha, M. Gattass, A. C. Silva, and A. C. de Paiva, A mass classification using spatial diversity approaches in mammography images for false positive reduction, `Expert System with Applications`, vol. 40, no. 18, pp. 7534–7543, 2013.

30. [\[30\]](#C12_chapter5.xhtml#rref5_30) X. Jin, C. Xu, J. Feng, Y. Wei, J. Xiong, and S. Yan, Deep learning with S-shaped rectified linear activation units, `Presented at the Proceedings of the Thirtieth AAAI Conference on Artificial Intelligence`, Phoenix, AZ, 2016.

31. [\[31\]](#C12_chapter5.xhtml#rref5_31) A. Nicolae, PLU: the piecewise linear unit activation function, `ArXiv`, vol. abs/1809.09534, 2018.

32. [\[32\]](#C12_chapter5.xhtml#rref5_32) M. V. Boland and R. F. Murphy, A neural network classifier capable of recognizing the patterns of all major subcellular structures in fluorescence microscope images of HeLa cells, `BioInformatics`, vol. 17, no. 12, pp. 1213–223, 2001.

33. [\[33\]](#C12_chapter5.xhtml#rref5_33) N. Hamilton, R. Pantelic, K. Hanson, and R. D. Teasdale, Fast automated cell phenotype classification, `BMC Bioinformatics`, pp. 8–110, 2007.

34. [\[34\]](#C12_chapter5.xhtml#rref5_34) L. Shamir, N. V. Orlov, D. M. Eckley, and I. Goldberg, IICBU 2008: a proposed benchmark suite for biological image analysis, `Medical & Biological Engineering & Computing`, vol. 46, no. 9, pp. 943–947, 2008.

35. [\[35\]](#C12_chapter5.xhtml#rref5_35) J. N. Kather et al., Multi-class texture analysis in colorectal cancer histology, `Scientific Reports`, vol. 6, p. 27988, 2016.

36. [\[36\]](#C12_chapter5.xhtml#rref5_36) K. Dimitropoulos, P. Barmpoutis, C. Zioga, A. Kamas, K. Patsiaoura, and N. Grammalidis, Grading of invasive breast carcinoma through Grassmannian VLAD encoding, `PLoS One`, vol. 12, pp. 1–18, 2017.

37. [\[37\]](#C12_chapter5.xhtml#rref5_37) S. Moccia et al., Confident texture-based laryngeal tissue classification for early stage diagnosis support, `Journal of Medical Imaging (Bellingham)`, vol. 4, no. 3, p. 34502, 2017.

38. [\[38\]](#C12_chapter5.xhtml#rref5_38) J. Demšar, Statistical comparisons of classifiers over multiple data sets, `Journal of Machine Learning Research`, vol. 7, pp. 1–30, 2006.

# [CHAPTER 6](#C02a_toc.xhtml#rc6)

[Analysis of Structural MRI Data for Epilepsy Diagnosis Using Machine Learning Techniques](#C02a_toc.xhtml#rc6)

Seyedmohammad Shams  

and Esmaeil Davoodi-Bojd

Henry Ford Health System

Detroit, Michigan

Hamid Soltanian-Zadeh

Henry Ford Health System

Detroit, Michigan

University of Tehran

Tehran, Iran

## Contents

[6.1 Introduction](#C13_chapter6.xhtml#secc006_1)

[6.2 Lateralization Indices/Features Extracted from Structural MRI](#C13_chapter6.xhtml#secc006_2)

[6.2.1 Study Population](#C13_chapter6.xhtml#secc006_2_1)

[6.2.2 MRI Acquisition](#C13_chapter6.xhtml#secc006_2_2)

[6.2.3 Image Processing](#C13_chapter6.xhtml#secc006_2_3)

[6.2.4 Feature Analysis and Classification](#C13_chapter6.xhtml#secc006_2_4)

[6.2.5 Summary of Machine Learning for mTLE Lateralization](#C13_chapter6.xhtml#secc006_2_5)

[6.3 Results](#C13_chapter6.xhtml#secc006_3)

[6.3.1 Study I: Hippocampal Study – FLAIR Intensity, Texture Analysis, and Volumetry](#C13_chapter6.xhtml#secc006_3_1)

[6.3.2 Study II: Hippocampal and Amygdalar Study – FLAIR Intensity and Volumetry](#C13_chapter6.xhtml#secc006_3_2)

[6.3.3 Study III: DTI-Based Response-Driven Modeling](#C13_chapter6.xhtml#secc006_3_3)

[6.3.4 Study IV: Texture Features Extracted from Whole Brain MRI](#C13_chapter6.xhtml#secc006_3_4)

[6.3.5 Study V: Multi-Structural Vomuletric Features](#C13_chapter6.xhtml#secc006_3_5)

[6.4 Discussion](#C13_chapter6.xhtml#secc006_4)

[6.5 Conclusion](#C13_chapter6.xhtml#secc006_5)

[References](#C13_chapter6.xhtml#references-4)

## [6.1 Introduction](#C13_chapter6.xhtml#rsecc006_1)

Epilepsy, characterized by spontaneous and recurrent seizures, is one of the major neurological disorders affecting 0.5%–2% of the population, and based on the World Health organization’s report, more than three million Americans suffer from it `\[[1](#C13_chapter6.xhtml#ref6_1),[2](#C13_chapter6.xhtml#ref6_2)\]`. According to the new classification identified by the International League Against Epilepsy (ILAE), seizures can be categorized into generalized and focal epileptic seizures `\[[3](#C13_chapter6.xhtml#ref6_3)\]`. Of those, focal epilepsy is more common than generalized `\[[4](#C13_chapter6.xhtml#ref6_4)\]`. It has been shown that epilepsy with focal seizures in the temporal lobe, which is termed temporal lobe epilepsy (TLE), is the most probable one with local seizures, and about 60% of all adult and adolescent epileptic patients suffer from this type of focal epilepsy. The mesial temporal lobe epilepsy (mTLE) with hippocampal sclerosis, identified by ILAE due to its prevalence, is the most common and intractable TLE `\[[5](#C13_chapter6.xhtml#ref6_5),[6](#C13_chapter6.xhtml#ref6_6)\]` and more often refractory to medical treatment in adults.

A drug-resistant patient who fails more than two optimal trials of antiepileptics and has at least one seizure per month is considered a candidate for epilepsy surgery. In this case, a resection surgery can be an efficacious option and will be performed if an epileptic focus is localized with confidence `\[[7](#C13_chapter6.xhtml#ref6_7),[8](#C13_chapter 5.xhtml#rref5_27">K. He, X. Zhang, S. Ren, and J. Sun, Deep residual learning for image recognition, *Presented at the 2016 IEEE Conference on Computer Vision and Pattern Recognition (CVPR)*, Las Vegas, NV, 2016.

[3] [#C12_chapter5.xhtml#rref5_28] G. Huang, Z. Liu, L. Van Der Maaten, and K. Q. Weinberger, Densely connected convolutional networks, *CVPR*, vol. 1, no. 2, p. 3, 2017.

[3] [#C12_chapter5.xhtml#rref5_29] B. Geraldo Junior, S. V. da Rocha, M. Gattass, A. C. Silva, and A. C. de Paiva, A mass classification using spatial diversity approaches in mammography images for false positive reduction, *Expert System with Applications*, vol. 40, no. 18, pp. 7534–7543, 2013.

[3] [#C13_chapter6.xhtml#secc006_1] Epilepsy, characterized by spontaneous and recurrent seizures, is one of the major neurological disorders affecting 0.5%–2% of the population, and based on the World Health organization’s report, more than three million Americans suffer from it \[[1](#C13_chapter6.xhtml#ref6_1),[2](#C13_chapter6.xhtml#ref6_2)\]. According to the new classification identified by the International League Against Epilepsy (ILAE), seizures can be categorized into generalized and focal epileptic seizures \[[3](#C13_chapter6.xhtml#ref6_3)\]. Of those, focal epilepsy is more common than generalized \[[4](#C13_chapter6.xhtml#ref6_4)\]. It has been shown that epilepsy with focal seizures in the temporal lobe, which is termed temporal lobe epilepsy (TLE), is the most probable one with local seizures, and about 60% of all adult and adolescent epileptic patients suffer from this type of focal epilepsy. The mesial temporal lobe epilepsy (mTLE) with hippocampal sclerosis, identified by ILAE due to its prevalence, is the most common and intractable TLE \[[5](#C13_chapter6.xhtml#ref6_5),[6](#C13_chapter6.xhtml#ref6_6)\] and more often refractory to medical treatment in adults.

A drug-resistant patient who fails more than two optimal trials of antiepileptics and has at least one seizure per month is considered a candidate for epilepsy surgery. In this case, a resection surgery can be an efficacious option and will be performed if an epileptic focus is localized with confidence \[[7](#C13_chapter6.xhtml#ref6_7),[8](#C13_chapter6.xhtml#ref6_8)\]. Obviously, the success of surgical treatment in these cases is thoroughly dependent on the localization/lateralization accuracy provided by imaging, electrocortical, and neuropsychological testing. Congruent EEG, seizure semiology, and imaging studies in determining epileptogenic mesial temporal lobe can sufficiently satisfy the requirement of a successful epilepsy resective surgery, while in the presence of incongruent lateralization, patients may undergo intracranial electrode implantation, which has a major medical risk and financial cost \[[9](#C13_chapter6.xhtml#ref6_9)\].

Hence, the determination of the primary origin of a patient’s seizure by advanced structural imaging techniques is one of the active areas in epilepsy research, due to its noninvasive nature. Among abnormality syndromes, mesial temporal sclerosis (MTS) is the best predictor of mTLE \[[10](#C13_chapter6.xhtml#ref6_10), [11](#C13_chapter6.xhtml#ref6_11), [12](#C13_chapter6.xhtml#ref6_12)\]. Several structural imaging modalities have been utilized to diagnose MTS and reduce the error and uncertainty in the lateralization of mTLE, as the most operated form of epilepsy. In this direction, the following neuroimaging modalities have been widely used for determining structural features that are well-suited to distinguish patients with right and left mTLE as well as patients with unilateral and bilateral abnormality: anatomical magnetic resonance imaging (T1-weighted MRI), fluid-attenuated inversion recovery (FLAIR), and diffusion tensor imaging (DTI) \[[13](#C13_chapter6.xhtml#ref6_13)\].
