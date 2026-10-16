
[43] 列昂·勒库恩、亚尼·本吉奥和金特·欣顿 2015 年《自然》深度学习 *Nature* [`521` 436–44](http://dx.doi.org/10.1038/nature14539)

[44] 黄 G‑B 胡 2012 年 ELM 用于回归和多类分类 `IEEE Trans. Syst. Man Cybern.` B [`42` 513–29](http://dx.doi.org/10.1109/TSMCB.2011.2168604)

[45] 朱 Q‑Y 2005 年演化 ELM *Pattern Recognit.* [`38` 1759–63](http://dx.doi.org/10.1016/j.patcog.2005.03.028)

[46] 毛 L、张 L、刘 X、李 C 和杨 H 2014 年改进的极端学习机及其在图像质量评估中的应用 *Math. Probl. Eng.* [`2014` 426152](http://dx.doi.org/10.1155/2014/426152)

[47] 唐 J、邓 C 和黄 G‑B 2016 年 ELM 用于多层感知器 `IEEE Trans Neural Netw. Learn. Syst.` [`27` 809–21](http://dx.doi.org/10.1109/TNNLS.2015.2424995)

[48] Demuth H B、Beale M H、De Jess O 和 Hagan M T 2014 *Neural Network Design* (Stillwater, OK: Martin Hagan)

[49] El‑Baz A 和 Suri J S 2018 *Big Data in Medical Imaging* (Boca Raton, FL: CRC Press)

[50] El‑Baz A S、Saba L 和 Suri J S 2014 *Abdomen and Thoracic Imaging* (Berlin: Springer)

[51] El‑Baz A、Gimel’farb G 和 Suri J S 2015 *Stochastic Modeling for Medical Image Analysis* (Boca Raton, FL: CRC Press)

[52] Esses S J、Lu X、Zhao T、Shanbhogue K、Dane B、Bruno M 和 Chandarana H 2017 年利用深度学习架构对 T2‑加权肝脏 MRI 进行自动化图像质量评估 *J. Magn. Reson. Imaging* [`47` 723–28](http://dx.doi.org/10.1002/jmri.25779)

[53] Spacek L Face94 数据库 [`http://cswww.essex.ac.uk /mv/allfaces /faces94.html`](http://www.essex.ac.uk)

[54] Kuppili V 2017 用于脂肪肝疾病分层风险的超声组织特征深度学习框架 `J. Med. Syst.` [`41` 1–20](http://dx.doi.org/10.1007/s10916-017-0797-1)

# `IOP` Publishing

# Multimodality Imaging, Volume 1

# Deep learning applications

# Mainak Biswas and Jasjit S Suri

# Chapter 11

## Symtosis: deep learning based liver ultrasound tissue characterisation and risk stratification

# Mainak Biswas and Jasjit S Suri

Fatty liver disease (FLD) is caused by build-up of fat within liver cells which, if left untreated, may lead to life-threatening diseases such as cancer. Machine learning (ML) modules implicitly depend on features extracted manually from ultrasound images, therefore their accuracy is essential for the integrity of healthcare systems.

In this work a deep learning convolutional neural network (CNN) model for FLD detection from ultrasound images is proposed under the class `Symtosis`. The proposed CNN model is 22 layers deep and consists of four types of layers: convolution, pooling, rectified linear unit, and dropout. The DL model uses a special operation called inception which is an amalgamation of multiple convolution filters in one layer which leads to better performance without increasing complexity. The DL based system is compared to the conventional ML models of the support vector machine (`SVM`) and extreme learning machine (`ELM`).

The dataset consists of ultrasound images from 63 patients of which 27 were normal and 36 diseased. The CV protocol for learning was K10 cross-validation, i.e. 90% training and 10% testing. The performance of the DL model was better than that of the ELM and SVM, the performance was 100%, 92%, and 82%, respectively. In the same order the AUC were 1.0, 0.92 and 0.79, respectively.

The DL system shows a better performance for FLD diagnosis and risk characterisation compared to the contemporary ML models of ELM and SVM.

### 11.1 Introduction

Fatty liver disease (FLD) has been identified as one of the top reasons for liver-related deaths among adults in the age group of 45–54 years in the United States in the last two decades [`1`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib1). Steatosis is the build-up of fat in liver cells. FLD can be caused by a multiplicity of factors, including metabolic syndrome, alcohol intake, and obesity owing to insulin resistance [`1`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib1), [`2`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib2). Non-alcoholic FLD (NAFLD) is a frequent cause of chronic liver disease in the Western world, accounting for 19%–46% of all liver illnesses [`2`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib2). The classification of FLD tissue has been studied in a number of ways. A dual energy CT (DECT) based technique was used by Lamb *et al_ [`3`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib3`) for categorisation of computed tomography (CT) images. Artificial neural networks (ANNs) were employed for the categorisation of magnetic resonance imaging (MRI) liver images [`4`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib4). In 2012 Suri and his team [`5`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib5) created a computer-assisted liver data classification model for ultrasound (US). For the classification, they used a logical machine learning (ML) model, i.e. decision tree [`6`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib6), with 93.3% accuracy. In 2016 Suri and his team [`7`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib7) proposed the Levenberg–Marquardt back propagation neural network (BPNN) [`8`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib8) under the class of `Symtosis`^(TM). Ultrasound liver images with FLD are frequently hypoechoic, preventing statistical classifiers from achieving 100% accuracy. There is a strong demand for appropriate tissue feature classification by ML algorithms. Furthermore, during training, CV protocols necessitate several trials per combination, which is time consuming. Convolutional neural networks (CNNs) have recently become popular in classification [`9`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib9). Figure [`11.1`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig1) shows an instance of a CNN model. The CNN uses a series of rectilinear units (ReLus) and pooling operations for feature mining. A convolution kernel is used on an input image to perform a multiplication of the image pixel by the kernel weights block-by-block, and then adding the results to generate feature maps. The ReLu is frequently used in conjunction with convolution. The ReLu performs rectification on feature maps to diminish the issue of vanishing gradient. The down-sampling of input data is accomplished through pooling. CNN now plays a role in a variety of real-world applications that have been buffered with optimisation techniques [`10`](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib10).

``` 
![Figure 11.1. The basic deep learning CNN model. (Reproduced with permission from \[40\]. Copyright 2018 Elsevier.)](images/bk978-0-7503-2244-7ch11f1_online.jpg)
```

**Figure 11.1.** The basic deep learning CNN model. (Reproduced with permission from `\[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]`. Copyright 2018 Elsevier.)

