
它们是眼表健康的关键因素，因为它们分泌油脂形成泪膜的极性油层，防止水分蒸发。`MGs`负责产生眼部所需的油层，确保眼部正常功能。眼表干燥症（`DED`）的主要原因之一是`MGD`，因此理解`DED`的文献用法至关重要。`MGD`是一种普遍的眼部疾病，但许多人并不知情地患有它。当眼睑中数十个微小腺体中的少数腺体发生故障时，就会出现`MGD`。`MGD`在图74.3中有所展示。

![Figure 74.3 MG 功能障碍](img/fig74_3_B.jpg)

Figure 74.3 MG 功能障碍

`MG`的异常油脂分泌（称为`meibum`）可能导致泪膜不稳定、蒸发增加，进而引发睑缘腺功能障碍（`MGD`）。为保护眼部免受`DED`侵害，定期监测睑缘腺非常重要。随着技术用品的增多，`MGD`的患病率近年来迅速上升，严重影响人们的正常生活。新冠疫情对我们生活的重大影响也是导致此上升的原因（Mahajan and Kaushal, 2020）。

医疗行业可能因深度学习的快速进步而发生根本性转变。眼科领域的大多数疾病诊断依赖于对大量图像的识别，这正是深度学习（`DL`）的常见应用场景。因此，`DL`在诊断眼部疾病方面表现出色。许多作者已在机器学习和深度学习技术上开展工作，用于计算和评估`MG`的`meibography`（睑缘摄影）Ramesh等人, 2022。`DL`方法近年来被提出，用于分析`meibography`图像中的`MG`形态，部分技术的准确性已超过经验丰富的人类观察者。因此，与单个腺体形态的评估不同，这些方法只能评估整体睑缘腺形态。因此，目前许多医生正在使用深度学习算法对`meibography`图像进行分割，以区分特定`MG`区域、量化腺体特性并识别“鬼腺”。文献中已有多种分割技术来解决这些问题（Setu等人, 2021; Wang等人, 2021）。图像分割是一种识别图像中边界或物体的技术，通过不同特征将前景与背景像素分离。

Setu等人 (2021)描述了`MGD`相关`DED`诊断的关键条件是准确的`MG`自动分割。然而，由于图像伪影，利用红外`meibography`自动分割睑缘腺仍是一项困难的步骤。提出了一种基于`DL`的`MG`分割方法，该方法直接从训练数据集的图像中学习`MG`特征，无需进行任何图像预处理。该模型使用了728张经匿名化的临床`meibography`图像进行测试和训练。该方法还建议评估腺体数量、长度、宽度、弯曲程度以及自动计算的`MG`形态学特征。这是首次使用经过验证的深度学习技术对上下眼睑的`MG`分割与评估进行操作。本研究将通过本研究提供关于`MGD`诊断最新进展的综述。本文章节包括——讨论`meibography`及其使用的技术，随后是文献综述、讨论与展望，最后以结论结束。

## Meibography 与技术

`Meibography`定义为对`MG`的成像，在`MGD`检测中发挥重要作用。为了研究和分析眼睑，一种非接触式光学成像方法——红外（`IR`）`meibography`利用红外照射可视化`MG`形态。临床上，在干眼检查时通常建议对`MG`进行成像和量化（Modi等人, 2021; Setu等人, 2021）。`Meibography`是一种简单且无创的方法，用于获取眼部`MG`的详细形态学信息。其优势包括能够测量疾病进展、监测疾病以及评估治疗效果和潜在性。

红外`meibography`利用红外光创建`MG`的详细图像，供医疗提供者用于诊断和治疗影响腺体及泪膜的疾病。红外光之所以用于红外`meibography`，是因为它能穿透眼睑及其他组织，使医疗提供者在不进行侵入性操作的情况下观察`MG`。红外光的波长长于可见光，因此不易被眼部组织散射或吸收，从而能够提供更清晰、更详细的`MG`图像。此外，红外光对眼部安全，不会产生任何有害影响。

## Meibography 技术

目前有三种`meibography`技术：接触式、非接触式以及油层厚度测量测试，具体如下：

### 接触式 meibography

*它是一种在1970年代末期创建的传统程序，直接将光探针应用于皮肤，照亮眼睑并使其翻转，然后使用专用相机对结果进行成像。该系统多年来取得了显著成功，但也存在一些缺点。*

* 主要缺点是需要一位熟练的操作员才能高效使用设备并获得高质量图像。
* Eyelids have distinct features that are rarely susceptible to manipulate with the light probe. A typical and time-consuming problem is partial lid eversion that requires numerous photos to be captured and fused for generating a wide image of the eyelid.
* The probe’s heat, pressure, brightness, and sharpness could make patients feel uncomfortable.
* A recently developed “oblique T-shaped probe” that helps to enhance image quality and lid manipulation while decreasing patient pain was made public in year 2007 in order to avoid these issues. The growth of non-contact meibography has considerably dominated contact meibography, despite well-intentioned advancements like the oblique T-shaped probe (Wise et al., 2012).

### Non-contact meibography

The newest meibographic approach, non-contact meibography was presented by Arita et al. (2008). A digitally everted eyelid is imaged using video camera that uses an `IR` charge-coupled device and a slit-lamp biomicroscope with an `IR` filter. Non-contact meibography differs from the contact method in that a light probe is not required. This method solves the problems of lid manipulation and discomfort of patient that are frequently experienced with contact meibography by doing away with the necessity for a light probe. In contrast of this, non-contact meibography asserts to be patient-centered, rapid and user-friendly than contact approaches. Non-contact meibography also has the benefit of viewing a larger portion of the everted eyelid, which requires fewer photos and take lesser time to combine into a wide view of the lid for analysis. The progress in techniques of meibography was described who invented the mobile pen-shaped meibography system.

This system is an example of non-contact meibography that makes use of an infrared LED that is linked to a pen-shaped camera that can be held in the hand and that is proficient in taking high-quality pictures or videos of the meibomian glands. Consequently, the slit-lamp biomicroscope that is traditionally used in non-contact meibography is effectively unnecessary with the mobile penshaped meibography device (Wise et al., 2012).

### Lipid layer thickness measurement

Lipid layer thickness measurement is a diagnostic technique that is used to evaluate the thickness of the lipid (or oily) layer of the tear film on the surface of eye. This layer is formed by the `MGs` in the eyelid and it helps to keep the surface of the eye moist and healthy. A thin or insufficient lipid layer can cause dry eye symptoms and other problems with the tear film. `LLT` measurement is typically performed using specialized equipment such as an interferometer or an optical coherence tomographer, which can measure the thickness of the lipid layer with high accuracy. This information can be used by a healthcare provider to detect and treat conditions that affect the meibomian glands and the tear film (Özcura et al., 2007).

## Literature review and major findings

`MGD` is a widespread eye disorder. In literature, several researchers have published a number of techniques for diagnosing Meibomian gland dysfunction in the literature as can be seen in Table 74.2.

Table 74.2 Different techniques for diagnosis of Meibomian gland dysfunction

| S. No. | Authors | Dataset used | Techniques used | Outputs |
| --- | --- | --- | --- | --- |
| 1 | Yu et al., 2022 | 1878 meibography images | Mask R-CNN | * 21 times faster method than clinicians<br>* Grade the MGs more accurately<br>* Efficiency increased but various structural anomalies and structural defects remains to be further re-fined |
| 2 | Zhang et al., 2022 | 1620 upper eyelids and 2386 lower eyelids images | Mask R-CNN | * Sensitivity - 88%<br>* Specificity - 81% |
| 3 | Dai et al., 2021 | 120 meibography images in a prospective trial | A CNN with enhanced mini U-Net MGs extraction approach | * Although precision of MGD diagnosis increases but data set is very small<br>* Reduce analysis time to help ophthalmologists with minimal clinical experience |
| 4 | Khan et al., 2021 | 706 meibography images | Pearson correlation, grading, Meiboscoring and Bland-Altman analysis | * Improves the quantification of IR irregularities<br>* Locating and analyzing the MGD dropout area.<br>* MGD score based quantitative evaluation is required |
| 5 | Wang et al., 2021 | 1443 meibography images | Support vector machine classifier (SVM) | * Mean intersection over union – 63%<br>* Sensitivity – 84.4%<br>* Specificity – 71.7% |
| 6 | Setu et al., 2021 | 728 meibography images | U-net | * Average precision – 83%<br>* Recall – 81%<br>* F1 score – 84%, respectively |
| 7 | Prabhu et al., 2020 | 400 prototype images and 400 oculus images | CNN | * Length – 47.88<br>* Number of glands – 14.40<br>* Gland-drop – 0.56<br>* Tortuosity – 1.31<br>* Width – 4.20 |
| 8 | Xiao et al., 2021 | 15 meibography images | Image contrast enhancement and ROI segmentation | * Similarity index = 0.94±0.02<br>* False-negative rate = 6.43±1.98%<br>* False-positive rate = 6.02±2.41%<br>* Technique is applicable to upper lid MGs only |
| 9 | Celik et al., 2013 | 131 meibography images | Support vector machine classifier (SVM) | * Accuracy of MGD – 88%<br>* Focus on classification only<br>* MGD score based quantitative evaluation is required |

A detailed literature study regarding the diagnosis of Meibomian gland dysfunction and `DED` in `IR` images has resulted in the following findings which are yet to be addressed:
