
4.  [\[4\]](#C08_chapter1.xhtml#rref1_4) Pambianco DJ, Vargo JJ, Pruitt RE, Hardi R, Martin JF. 计算机辅助个性化镇静术用于上消化道镜检和结肠镜检：多中心随机对照研究。*胃肠镜学杂志* 2011;73: 765–772. doi:`[10.1016/j.gie.2010.10.031](https://doi.org/10.1016/j.gie.2010.10.031)`

5.  [\[5\]](#C08_chapter1.xhtml#rref1_5) Boggs S. 计算机辅助个性化镇静术——麻醉提供者的开始还是终结？在：Anesthesia Business Consultants \[Internet\]. \[cited 19 Dec 2019\]. 可用: [`https://www.anesthesiallc.com/publications/blog/entry/computer-assisted-personalized-sedation-the-beginning-or-the-end-of-the-anesthesia-provider`](https://www.anesthesiallc.com/publications/blog/entry/computer-assisted-personalized-sedation-the-beginning-or-the-end-of-the-anesthesia-provider)

6.  [\[6\]](#C08_chapter1.xhtml#rref1_6) Hatib F, Jian Z, Buddi S, Lee C, Settels J, Sibert K, 等. 基于高保真动脉压波形分析的机器学习算法预测低血压。*麻醉学杂志* 2018;129: 663–674. doi:`[10.1097/ALN.0000000000002300](https://doi.org/10.1097/ALN.0000000000002300)`

7.  [\[7\]](#C08_chapter1.xhtml#rref1_7) Kendale S, Kulkarni P, Rosenberg AD, Wang J. 监督机器学习预测分析在术后低血压预测中的应用。*麻醉学杂志美国麻醉医师学会* 2018;129: 675–688. doi:`[10.1097/ALN.0000000000002374](https://doi.org/10.1097/ALN.0000000000002374)`

8.  [\[8\]](#C08_chapter1.xhtml#rref1_8) Lundberg SM, Nair B, Vavilala MS, Horibe M, Eisses MJ, Adams T, 等. 可解释机器学习预测术中低氧血症的预防。*自然生物医学工程* 2018;2: 749–760. doi:`[10.1038/s41551-018-0304-0](https://doi.org/10.1038/s41551-018-0304-0)`

9.  [\[9\]](#C08_chapter1.xhtml#rref1_9) Saadeh W, Khan FH, Altaf MAB. 基于机器学习的EEG处理器设计及实现，用于准确估计麻醉深度。*IEEE 传感器与生物医学电路系统杂志* 2019;13: 658–669. doi:`[10.1109/TBCAS.2019.2921875](https://doi.org/10.1109/TBCAS.2019.2921875)`

10.  [\[10\]](#C08_chapter1.xhtml#rref1_10) Lee CK, Hofer I, Gabel E, Baldi P, Cannesson M. 发展并验证一个深度神经网络模型，用于预测术后住院死亡率。*麻醉学杂志* 2018;129: 649–662. doi:`[10.1097/ALN.0000000000002186](https://doi.org/10.1097/ALN.0000000000002186)`

11.  [\[11\]](#C08_chapter1.xhtml#rref1_11) Novak R. 机器人麻醉。在：The anesthesia consultant \[Internet\]. 2012年11月27日 \[cited 19 Dec 2019\]. 可用: [`https://theanesthesiaconsultant.com/2012/11/27/robot-anesthesia/`](https://theanesthesiaconsultant.com/2012/11/27/robot-anesthesia/)

# [CHAPTER 2](#C02a_toc.xhtml#rc2)

[Dermatological Machine Learning Clinical Decision Support System](#C02a_toc.xhtml#rc2)

Pushkar Aggarwal

University of Cincinnati College of Medicine

Cincinnati, Ohio

## Contents

[2.1 Background](#C09_chapter2.xhtml#secc002_1)

[2.2 Melanoma](#C09_chapter2.xhtml#secc002_2)

[2.3 Non-Melanoma Machine Learning](#C09_chapter2.xhtml#secc002_3)

[2.4 Non-Skin Image Recognition Machine Learning](#C09_chapter2.xhtml#secc002_4)

[2.5 Data Augmentation](#C09_chapter2.xhtml#secc002_5)

[2.6 Limitations](#C09_chapter2.xhtml#secc002_6)

[2.7 Future Directions](#C09_chapter2.xhtml#secc002_7)

[2.8 Conclusion](#C09_chapter2.xhtml#secc002_8)

[References](#C09_chapter2.xhtml#references-1)

## [2.1 Background](#C09_chapter2.xhtml#rsecc002_1)

Dermatology is a subject that relies on morphological features and the majority of diagnoses are based on visual pattern recognition. At present, the skin imaging technology is represented by dermoscopy, very high-frequency ultrasound, and reflectance confocal microscopy. Each method of skin imaging equipment has its own advantages and limitations. Dermatologists need to choose different imaging methods according to different conditions of skin lesions. The skin imaging technology has become a vitally important tool for clinical diagnosis of skin diseases and is widely accepted and applied worldwide \[[1](#C09_chapter2.xhtml#ref2_1)\]. As such, dermatology is exceedingly suitable for applying artificial intelligence (AI) image recognition capabilities for assisted diagnosis.

In 2013, one out of every four Americans saw a physician regarding a skin disease \[[2](#C09_chapter2.xhtml#ref2_2)\]. The overall prevalence of skin disease in the U.S. is estimated to be around 27%. In those who are 65 years or older, the prevalence increases to around 49%, and the average number of skin diseases per person increases from 1.6 to 2.2. Furthermore, of the total number of deaths in 2013, skin disease accounted for almost 1 out of every 100. Assuming a potential life expectancy of 75 years, it was found that fatal skin disease resulted in almost 11 years of potential life loss \[[2](#C09_chapter2.xhtml#ref2_2)\]. Melanoma is the most deadly skin cancer, accounting for 75% of all skin cancer-related death, and is responsible for over 10,000 deaths annually in the U.S. \[[3](#C09_chapter2.xhtml#ref2_3)\]. Melanoma is the leading cause of cancer death in 25–30 years old women and the second most commonly diagnosed cancer in those who are 15–29 years of age \[[4](#C09_chapter2.xhtml#ref2_4)\]. The incidence of melanoma doubled from 11.2 per 100,000 people in 1982 to 22.7 per 100,000 people in 2011. Other skin conditions while not being as deadly as melanoma can still have a significant impact on a person. Acne affects about 50 million Americans annually and is the most common skin condition in the U.S. \[[5](#C09_chapter2.xhtml#ref2_5)\]. Rosacea and psoriasis affect about 15 million people and 8 million people in the U.S., respectively \[[6](#C09_chapter2.xhtml#ref2_6),[7](#C09_chapter2.xhtml#ref2_7)\]. Non-melanoma skin cancer and melanoma combine for about $6 billion in medical costs each year. Other skin conditions such as acne, psoriasis, seborrheic dermatitis, and atopic dermatitis account for $846, $737, $339, and $314 million each year, respectively \[[2](#C09_chapter2.xhtml#ref2_2)\]. Therefore, AI implementation in dermatology has the potential to significantly benefit the health and finances of a large part of the population.

AI applies automated learning and provides output based upon large data. Previously, large data were not available or were not assimilated together in a standardized form. The advent and extensive use of computers have helped in assimilating large data sets in many medical fields, including dermatology. AI tries to mimic the human brain in reproducing human cognition and can be an asset in dermatology clinical evaluations.

## [2.2 Melanoma](#C09_chapter2.xhtml#rsecc002_2)

Much of the machine learning implementation in the field of dermatology encompasses the binary classification of malignant melanoma versus benign nevi. One criterion that is often used in the clinical diagnosis of melanoma is the ABCDE criteria – asymmetry, border (irregular), color (two or more colors), diameter greater than 6 mm, and enlargement or evolution in size \[[8](#C09_chapter2.xhtml#ref2_8)\]. The first four criteria are potential criteria that a machine learning algorithm can use during its assessment of the lesion.
