
7. [7.](#C09_chapter2.xhtml#rref2_7) 牛皮藻统计数据。在：National Psoriasis Foundation [Internet]。可用：[`https://www.psoriasis.org/content/statistics`](https://www.psoriasis.org/content/statistics)

8. [8.](#C09_chapter2.xhtml#rref2_8) 黑色素瘤临床诊断。*Am Fam Physician*。2008;78: 1205.

9. [9.](#C09_chapter2.xhtml#rref2_9) Esteva A, Kuprel B, Novoa RA, Ko J, Swetter SM, Blau HM, et al. 使用深度神经网络对皮肤癌进行医师级别分类。*Nature*。2017;542: 115–118。doi:[`10.1038/nature21056`](https://doi.org/10.1038/nature21056)

10. [10.](#C09_chapter2.xhtml#rref2_10) Haenssle HA, Fink C, Schneiderbauer R, Toberer F, Buhl T, Blum A, et al. 人对机器：深度学习卷积神经网络在与58名皮肤科医生比较时的黑色素瘤镜下识别诊断性能。*Ann Oncol Off J Eur Soc Med Oncol*。2018;29: 1836–1842。doi:[`10.1093/annonc/mdy166`](https://doi.org/10.1093/annonc/mdy166)

11. [11.](#C09_chapter2.xhtml#rref2_11) Aggarwal SLP. 利用机器学习进行皮肤病图像识别的数据增强。*Skin Res Technol Off J Int Soc Bioeng Skin ISBS Int Soc Digit Imaging Skin ISDIS Int Soc Skin Imaging ISSI*。2019;25: 815–820。doi:[`10.1111/srt.12726`](https://doi.org/10.1111/srt.12726)

12. [12.](#C09_chapter2.xhtml#rref2_12) Bobrova M, Taranik M, Kopanitsa G. 使用神经网络进行皮肤科诊断。*Stud Health Technol Inform*。2019;261: 211–216。

13. [13.](#C09_chapter2.xhtml#rref2_13) Han SS, Park GH, Lim W, Kim MS, Na JI, Park I, et al. 深度神经网络在隐形眼镜真菌感染诊断中的表现与皮肤科医生相当，甚至更优；通过区域卷积深度神经网络自动构建隐形眼镜真菌感染数据集。*PloS One*。2018;13: e0191493。doi:[`10.1371/journal.pone.0191493`](https://doi.org/10.1371/journal.pone.0191493)

14. [14.](#C09_chapter2.xhtml#rref2_14) Kawahara J, BenTaieb A, Hamarneh G. 使用深度特征对皮肤病变进行分类。2016 IEEE 13th International Symposium on Biomedical Imaging (ISBI)。2016。pp. 1397–1400。doi:[`10.1109/ISBI.2016.7493528`](https://doi.org/10.1109/ISBI.2016.7493528)

15. [15.](#C09_chapter2.xhtml#rref2_15) Eapen BR. “神经网络”算法预测表皮松解性水疱病严重程度。*Indian J Dermatol Venereol Leprol.* 2005;71: 106–108。doi:[`10.4103/0378-6323.13995`](https://doi.org/10.4103/0378-6323.13995)

16. [16.](#C09_chapter2.xhtml#rref2_16) Gniadecka M, Philipsen PA, Wessel S, Gniadecki R, Wulf HC, Sigurdsson S, et al. 利用拉曼光谱和神经网络进行黑色素瘤诊断：完整癌组织中蛋白质和脂质结构的改变。*J Invest Dermatol*。2004;122: 443–449。doi:[`10.1046/j.0022-202X.2004.22208.x`](https://doi.org/10.1046/j.0022-202X.2004.22208.x)

17. [17.](#C09_chapter2.xhtml#rref2_17) Perez F, Vasconcelos C, Avila S, Valle E. 皮肤病变分析的数据增强。*ISIC Skin Image Anal Workshop*。2018。可用：[`https://arxiv.org/pdf/1809.01442.pdf`](https://arxiv.org/pdf/1809.01442.pdf)

# [CHAPTER 3](#C02a_toc.xhtml#rc3)

[Vision and AI](#C02a_toc.xhtml#rc3)

Mohini Bindal

Baylor College of Medicine

Houston, Texas

Pushkar Aggarwal

University of Cincinnati College of Medicine

Cincinnati, Ohio

## Contents

[3.1 Introduction](#C10_chapter3.xhtml#secc003_1)

[3.2 Diabetic Retinopathy](#C10_chapter3.xhtml#secc003_2)

[3.3 Age-Related Macular Degeneration](#C10_chapter3.xhtml#secc003_3)

[3.4 Glaucoma](#C10_chapter3.xhtml#secc003_4)

[3.5 Multi-Classifier and Improving Performance](#C10_chapter3.xhtml#secc003_5)

[3.6 Machine Learning for Predicting Survival/Prognosis](#C10_chapter3.xhtml#secc003_6)

[3.7 Conclusion](#C10_chapter3.xhtml#secc003_7)

[References](#C10_chapter3.xhtml#references-2)

## [3.1 Introduction](#C10_chapter3.xhtml#rsecc003_1)

The current world population is 7.7 billion, of which at least 2.2 billion (28.6%) has visual impairment \[[1](#C10_chapter3.xhtml#ref3_1)\]. In 2015, it was estimated that 36 million people were blind \[[2](#C10_chapter3.xhtml#ref3_2)\]. Early diagnosis and treatment of ophthalmological diseases are crucial in order to decrease this prevalence and to improve the quality of life of those affected. In the last few years, machine learning has made significant strides in various aspects of healthcare, including ophthalmology. In ophthalmology, a majority of research on the integration of machine learning has focused on the diagnosis of diabetic retinopathy and age-related macular degeneration (AMD). In the last few years, researchers have been investigating the application of machine learning to other diseases, such as glaucoma.

## [3.2 Diabetic Retinopathy](#C10_chapter3.xhtml#rsecc003_2)

In 2010, it was estimated that 126.6 million people have diabetic retinopathy, of which 37.3 million have vision-threatening diabetic retinopathy. It was also predicted that by 2030, these numbers would increase to 191.0 million and 56.3 million, respectively \[[3](#C10_chapter3.xhtml#ref3_3)\]. Globally, diabetic retinopathy is the leading cause of vision loss in those between 20 and 74 st age. However, only 33% of those with diabetes mellitus have characteristic symptoms \[[4](#C10_chapter3.xhtml#ref3_4)\]. Machine learning presents an opportunity by which early detection and correct diagnosis of diabetic retinopathy can be performed.

Gulshan et al. at Google trained a convolutional neural network (CNN) on over 120,000 retinal images \[[5](#C10_chapter3.xhtml#ref3_5)\]. These retinal images were first graded by ophthalmologists for image quality and for the presence of diabetic retinopathy or diabetic macular edema. In addition to labeling the images, ophthalmologists assessed the severity of the images identified as diabetic retinopathy on the scale of none, mild, moderate, severe, or proliferative. Next, the images were presented to the CNN for training. Two sets of testing were performed and the CNN achieved an area under the curve (AUC) of 0.991 (95% confidence interval (CI), 0.988–0.993) on the first testing data set and 0.990 (95% CI, 0.986–0.995) on the second testing data set. Given that the highest AUC possible is 1.0, the above model performed exceptionally well.

One of the limitations of machine learning in healthcare is that most often the images that the CNN is trained and validated on are images of one or only a few ethnicities. The model is never exposed to the inter-ethnicity differences and as such its performance would be expected to drop significantly if it was to be used for a different population. Ting et al. tried to account for this variability \[[6](#C10_chapter3.xhtml#ref3_6)\]. Their CNN was trained primarily on retinal images from people of Chinese, Malay, and Indian ethnicity. However, during validation, the CNN was provided images from people of the following races/ethnicities: Chinese, Malay, Indian, African American, White, and Hispanic. For detection of diabetic retinopathy, 76,370 images were used during training, and 112,648 images were used during testing. The model had an AUC of 0.936 (95% CI, 0.925–0.943), a sensitivity of 90.5% (95% CI, 87.3%–93.0%), and a specificity of 91.6% (95% CI, 91.0%–92.2%). The inclusion of multiple ethnicities is expected to lower the accuracy of the model but achieving an AUC higher than 0.93 indicates that machine learning has the potential to tease out inter-ethnicity differences when analyzing retinal images.

