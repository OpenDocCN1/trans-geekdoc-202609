
28. G. Huang, Z. Liu, L. Van Der Maaten, and K. Q. Weinberger, Densely connected convolutional networks, `CVPR`, vol. 1, no. 2, p. 3, 2017.

29. B. Geraldo Junior, S. V. da Rocha, M. Gattass, A. C. Silva, and A. C. de Paiva, A mass classification using spatial diversity approaches in mammography images for false positive reduction, `Expert System with Applications`, vol. 40, no. 18, pp. 7534–7543, 2013.

30. X. Jin, C. Xu, J. Feng, Y. Wei, J. Xiong, and S. Yan, Deep learning with S-shaped rectified linear activation units, `Presented at the Proceedings of the Thirtieth AAAI Conference on Artificial Intelligence`, Phoenix, AZ, 2016.

31. A. Nicolae, PLU: the piecewise linear unit activation function, `ArXiv`, vol. abs/1809.09534, 2018.

32. M. V. Boland and R. F. Murphy, A neural network classifier capable of recognizing the patterns of all major subcellular structures in fluorescence microscope images of HeLa cells, `BioInformatics`, vol. 17, no. 12, pp. 1213–223, 2001.

33. N. Hamilton, R. Pantelic, K. Hanson, and R. D. Teasdale, Fast automated cell phenotype classification, `BMC Bioinformatics`, pp. 8–110, 2007.

34. L. Shamir, N. V. Orlov, D. M. Eckley, and I. Goldberg, IICBU 2008: a proposed benchmark suite for biological image analysis, `Medical & Biological Engineering & Computing`, vol. 46, no. 9, pp. 943–947, 2008.

35. J. N. Kather et al., Multi-class texture analysis in colorectal cancer histology, `Scientific Reports`, vol. 6, p. 27988, 2016.

36. K. Dimitropoulos, P. Barmpoutis, C. Zioga, A. Kamas, K. Patsiaoura, and N. Grammalidis, Grading of invasive breast carcinoma through Grassmannian VLAD encoding, `PLoS One`, vol. 12, pp. 1–18, 2017.

37. S. Moccia et al., Confident texture-based laryngeal tissue classification for early stage diagnosis support, `Journal of Medical Imaging (Bellingham)`, vol. 4, no. 3, p. 34502, 2017.

38. J. Demšar, Statistical comparisons of classifiers over multiple data sets, `Journal of Machine Learning Research`, vol. 7, pp. 1–30, 2006.

# CHAPTER 6

## Analysis of Structural MRI Data for Epilepsy Diagnosis Using Machine Learning Techniques

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

### 6.1 Introduction

### 6.2 Lateralization Indices/Features Extracted from Structural MRI

#### 6.2.1 Study Population

#### 6.2.2 MRI Acquisition

#### 6.2.3 Image Processing

#### 6.2.4 Feature Analysis and Classification

#### 6.2.5 Summary of Machine Learning for mTLE Lateralization

### 6.3 Results

#### 6.3.1 Study I: Hippocampal Study – FLAIR Intensity, Texture Analysis, and Volumetry

#### 6.3.2 Study II: Hippocampal and Amygdalar Study – FLAIR Intensity and Volumetry

#### 6.3.3 Study III: DTI-Based Response-Driven Modeling

#### 6.3.4 Study IV: Texture Features Extracted from Whole Brain MRI

#### 6.3.5 Study V: Multi-Structural Vomuletric Features

### 6.4 Discussion

### 6.5 Conclusion

## References

## 6.1 Introduction

Epilepsy, characterized by spontaneous and recurrent seizures, is one of the major neurological disorders affecting 0.5%–2% of the population, and based on the World Health organization’s report, more than three million Americans suffer from it `\[1,2\]`. According to the new classification identified by the International League Against Epilepsy (ILAE), seizures can be categorized into generalized and focal epileptic seizures `\[3\]`. Of those, focal epilepsy is more common than generalized `\[4\]`. It has been shown that epilepsy with focal seizures in the temporal lobe, which is termed temporal lobe epilepsy (TLE), is the most probable one with local seizures, and about 60% of all adult and adolescent epileptic patients suffer from this type of focal epilepsy. The mesial temporal lobe epilepsy (mTLE) with hippocampal sclerosis, identified by ILAE due to its prevalence, is the most common and intractable TLE `\[5,6\]` and more often refractory to medical treatment in adults.

A drug-resistant patient who fails more than two optimal trials of antiepileptics and has at least one seizure per month is considered a candidate for epilepsy surgery. In this case, a resection surgery can be an efficacious option and will be performed if an epileptic focus is localized with confidence `\[7,8\]`. Obviously, the success of surgical treatment in these cases is thoroughly dependent on the localization/lateralization accuracy provided by imaging, electrocortical, and neuropsychological testing. Congruent EEG, seizure semiology, and imaging studies in determining epileptogenic mesial temporal lobe can sufficiently satisfy the requirement of a successful epilepsy resective surgery, while in the presence of incongruent lateralization, patients may undergo intracranial electrode implantation, which has a major medical risk and financial cost `\[9\]`.

Hence, the determination of the primary origin of a patient’s seizure by advanced structural imaging techniques is one of the active areas in epilepsy research, due to its noninvasive nature. Among abnormality syndromes, mesial temporal sclerosis (MTS) is the best predictor of mTLE `\[10, 11, 12\]`. Several structural imaging modalities have been utilized to diagnose MTS and reduce the error and uncertainty in the lateralization of mTLE, as the most operated form of epilepsy. In this direction, the following neuroimaging modalities have been widely used for determining structural features that are well-suited to distinguish patients with right and left mTLE as well as patients with unilateral and bilateral abnormality: anatomical magnetic resonance imaging (T1-weighted MRI), fluid-attenuated inversion recovery (FLAIR), and diffusion tensor imaging (DTI) `\[13\]`.

-   [海马硬化 (HS)](https://wiki.example.org/feynmans_learning_method) 是在难治性 `temporal lobe epilepsy (TLE)` 患者中最常见的病理改变，已被认可至少 190 `stras` `\[14,15\]`。海马硬化指的是海马不同亚区（如 `CA1`、`CA4`）出现严重的神经元丢失和胶质增生 `\[16\]`。在中颞叶 `TLE` (`mTLE`) 中，`HS` 的发生率报告为 56%，并被广泛用作判断受影响侧别（侧向化）的首要特征 `\[17, 18, 19\]`。`HS` 在 `MRI` 上可通过 `T1` 加权成像的体积减少、`T2` 加权成像的高信号以及 `FLAIR` 信号强度改变来表现。

-   虽然上述结构改变在高达 70% 的病例中被报道，但在部分病例中这些改变难以检测，或仅凭这些改变判断的侧别不足以确保手术成功 `\[20,21\]`。因此，研究者在定量分析中加入了相邻结构（如杏仁核）的改变，以增强分类。为了记录除海马和杏仁核外的 `mTLE` 相关结构改变，已开展多项研究，并报道了灰质和白质中多种异常 `\[20\]`。其中，内嗅回、前颞叶皮层、丘脑、背内侧束、体积束及胼胝体的异常是众所周知的。

-   普遍认为神经元丢失和胶质增生会导致组织中自由水增加。因此，`FLAIR`（弥散加权成像）作为测量组织自由水的技术，被视为研究神经元胶质及局灶性癫痫（尤其是中颞叶 `TLE` 患者）的标准手段。然而，许多研究表明 `FLAIR` 在 `mTLE` 患者的侧向化判断上灵敏度不足，需要结合其他影像特征才能获得满意结果。

-   由于部分研究报告指出，病理证实的海马硬化患者在 `T1` 加权和 `FLAIR MRI` 上并未表现出明显异常 `\[21\]`，因此有迫切需求采用其他影像技术。为此，已证明基于 `DTI`（弥散张量成像）的纤维追踪可以在解剖学 `MRI` 显示任何异常之前，检测到脑组织的微结构改变。`DTI` 在研究因癫痫灶导致的神经元丢失以及因广泛放电而影响的外侧脑结构异常方面具有特定作用。

-   在下面的章节中，我们将描述五项近期研究，这些研究利用上述 `MRI` 模态提供了一套有效的特征，可用于机器学习方法来诊断癫痫。

## 6.2 Lateralization Indices/Features Extracted from Structural MRI

-   侧向化研究的核心假设是：通过优化 `mTLE` 的侧向化，利用一套最佳影像特征和侧向化分类模型，可以在 `iEEG`（即阶段 II）阶段减少对颅内电生理检查的需求。为了侧向化 `mTLE`，`MRI` 已被广泛用于提取多种有效特征，以在 vivo 检测 `MTS` `\[22\]`。`MTS` 由海马组织中的神经元丢失、胶质/硬化、颗粒细胞分散以及 `mossy` 纤维萌芽等特征定义 `\[23\]`。基于 `T1` 加权图像的海马体积减少以及 `T2` 加权和 `FLAIR MRI` 中信号强度升高是目前用于量化 `MTS` 的主要特征 `\[17,24, 25, 26, 27, 28, 29\]`。这些特征能够在高达 70% 的病例中成功侧向化癫痫起源，但在 15%–30% 的确认单侧 `mTLE` 患者中，未见显著的海马不对称，即报告了细微或甚至没有不对称迹象 `\[8,17,30\]`。在这些情况下，可能需要额外的结构特征来提供足够的确定性来声明侧别。

-   第二类 `MRI` 特征是通过纹理分析评估的。纹理特征提供组织中信号强度模式的信息，也已用于阿尔茨海默病、多发性硬化和精神分裂症等心理疾病中 `\[31\]`。这些信号模式及其相对于海马和其他感兴趣区域的组织学改变的变化，已被用作检测海马硬化以及局灶性皮层发育不全的补充特征 `\[32, 33, 34\]`。在 `Ref. \[31\]` 中，从 `FLAIR` 图像中提取的海马体体积均值、标准差以及小波纹理特征被用于侧向化。作者训练了一种基于上述特征右左比值的线性分类器，以建立侧别。结果显示，75% 的病例中，`FLAIR` 强度的均值和标准差成功侧向化了癫痫发起部位。同时，纹理特征和海马体积特征的侧向化成功率分别为 64% 和 75%。
