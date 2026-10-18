
![](img/211c754cd1dd84920a171f497b33b689_576_0.png)

Figure 15: Key challenges in applying machine learning to medical images.

Figure 15：机器学习应用于医学影像的关键挑战。

otherwise possible models develop specific patterns from training sets into memory rather than general features. For a generalizable model, it has to be applicable across different patient types and imaging type scenarios and thereby be useful.

否则模型可能会将训练集中的特定模式记忆下来，而非泛化特征。对于一个可泛化的模型而言，它必须适用于不同患者类型和影像类型场景，从而具有实用性。

Technological problems, as well as issues of practical implementation, make it difficult to incorporate machine learning models into current therapeutic interventions. For the models to deliver valuable information without disrupting existing routines, radiologists’ operations must be seamlessly incorporated into the models. Issues of data security and privacy, and whether and how ML systems meet regulatory requirements, must be addressed in order to ensure the proper use and functioning of systems in clinical practice.

技术问题以及实际实施方面的难题，使得将机器学习模型整合到当前治疗干预中变得困难。为了使模型能够在不扰乱现有流程的情况下提供有价值的信息，放射科医生的操作必须无缝地融入模型中。数据安全和隐私问题，以及 ML 系统是否以及如何满足监管要求，必须得到解决，以确保系统在临床实践中的正确使用和运行。

During both training and inference, AI ML models, especially deep learning networks, are known to require large processing power. These models should be made available and feasible in scaled-up environments due to the high demands in memory and computation – Complexity controllers, though, are a disadvantage in resource-restricted environments. To circumvent these resource constraints, the efficiency of machine learning algorithms must be fully optimized, and in cloud computing and technology, opportunities must be exploited.

在训练和推理期间，AI ML 模型，尤其是深度学习网络，已知需要大量的处理能力。由于内存和计算需求很高，这些模型应在扩展环境中可用且可行——然而，复杂性控制器在资源受限环境中是劣势。为了规避这些资源限制，必须充分优化机器学习算法的效率，并在云计算和技术中利用机会。

There are two types of bias seen in machine learning models: bias in the training data and the bias of the algorithm. There exists inaccuracy in diagnosis and a variation of the same in one population due to the use of biased models in medical imaging. Redressal of the bias and fairness issues was fundamental in the creation of models capable of offering reliable results to patient groups irrespective of diversity.

机器学习模型中存在两种类型的偏差：训练数据中的偏差和算法本身的偏差。由于在医学影像中使用有偏模型，诊断中存在不准确性，且在同一人群中存在差异。纠正偏差和公平性问题是创建能够为不同多样性患者群体提供可靠结果的模型的基础。

## 5 Key components of machine learning systems for medical imaging

## 5 医学影像机器学习系统的关键组成部分

### 5.1 Data acquisition and labeling

### 5.1 数据采集与标注

Data acquisition and labeling are two crucial processes in the creation of machine learning systems in the medical imaging field. These processes are important for preparing the medical images for the machine learning algorithms to learn from them, as well as to correctly interpret the medical images.

数据采集和标注是医学影像领域创建机器学习系统的两个关键过程。这些过程对于准备医学影像以供机器学习算法学习，以及正确解读医学影像非常重要。

![](img/211c754cd1dd84920a171f497b33b689_577_0.png)

Figure 16: Data acquisition and labeling.

Figure 16：数据采集与标注。

Taking portable medical images from various types of imaging techniques, such as MRI, CT, ultrasound, and X-ray images, is referred to as data collection. Each modality produces different image types, which have distinct characteristics and carry various therapeutic applications. The quality and diversification of the obtained data also influence the efficiency of the developed machine learning models.

从各种影像技术获取医学影像，例如 MRI、CT、超声和 X 射线影像，被称为数据收集。每种模态产生不同类型的影像，具有不同的特征并具有各种治疗应用。所获得数据的质量和多样性也会影响所开发机器学习模型的效率。

Imaging techniques: Different imaging methods provide various views and more information regarding the anatomy under consideration and the disease. For instance, MRI yields high-quality images of the soft body tissues, while a CT scan gives detailed cross-sectional pictures of the body structures. They depend on the clinical issue and the type of medical problem under consideration.

影像技术：不同的影像方法提供各种视角，并提供有关所考虑解剖结构和疾病的更多信息。例如，MRI 可产生软组织的高质量图像，而 CT 扫描可提供身体结构的详细横截面图像。它们取决于临床问题和所考虑的医疗问题类型。

Equipment and protocols: Complex differences in imaging systems and acquisition settings could be a source of variation in the projects due to changes in image metrics. Some of the remaining intersurvey variations reflect methodological differences in evaluating comparable types of equipment; standardizing equipment settings and protocols, when feasible, aids in reducing such differences and in making survey results more comparable.

设备和协议：影像系统和采集设置之间的复杂差异可能导致项目中影像指标变化，从而成为变异的来源。剩余的跨调查差异中的一些反映了在评估可比类型的设备时的方法学差异；在可行时标准化设备设置和协议有助于减少此类差异并使调查结果更具可比性。

Data storage and management: Since many images are now generated in the medical world, proper storage and management of medical images are critical. Thus, it's imperative that systems be able to accommodate high-resolution images without compromising their security and usability for processing and analysis applications.

数据存储和管理：由于医学领域现在产生大量影像，妥善存储和管理医学影像至关重要。因此，系统必须能够容纳高分辨率影像，同时不损害其安全性以及用于处理和分析应用的可用性。

Data labeling entails associating medical images with information related to diseases and structures. Accurate labeling of images is important for machine learning models since labeling provides the ground truth for developing supervised learning models.

数据标注涉及将医学影像与疾病和结构相关信息关联起来。准确标注影像对机器学习模型很重要，因为标注为开发监督学习模型提供了真实标签。

Annotation techniques: Annotation can also be done with the assistance of radiologists or semiautomated tools. It was noted that manual annotation provided very high accuracy by construction but required a high amount of time and effort. There are tools available that perform this operation semiautomatically, as these speed up the process, although the results have to be validated for correctness by a professional.

标注技术：标注也可以在放射科医生或半自动化工具的协助下完成。注意到手动标注在构建上提供了非常高的准确性，但需要大量时间和精力。也有工具可以半自动执行此操作，这加快了流程，尽管结果必须由专业人员验证其正确性。

Labeling protocols: As noted earlier, the practice of labeling requires clear protocol guidelines to be set down to avoid confusion. These protocols should determine how various pathological conditions should be annotated and how the margins of the structures being delineated should be drawn.

标注协议：如前所述，标注实践需要制定明确的协议指南以避免混淆。这些协议应确定各种病理状况应如何标注，以及应如何绘制所描绘结构的边界。

Quality assurance: Since these set labels are typically a small sample of all the data it was possible to obtain in the context for which the AI was being designed, quality assurance measures need to be implemented to ensure the labeled data is actually precise and dependable. This requires using various consensus-assembling strategies to resolve conflicts and score comparisons.

质量保证：由于这些设定标签通常是为 AI 设计的上下文中可获得的所有数据中的一小部分，因此需要实施质量保证措施以确保标注数据的精确性和可靠性。这需要使用各种共识汇集策略来解决冲突和评分比较。

Methods for data augmentation are applied in order to expand the amount and the range of the training set. Transformation methods such as rotation, scaling, and flipping give a description that yields modifications of images. The mentioned strategies make machine learning models work with a larger number of different changes in the images, which, in turn, enhances their robustness.

数据增强方法被应用于扩展训练集的数量和范围。诸如旋转、缩放和翻转等转换方法可产生对图像的修改。上述策略使机器学习模型能够处理图像中更多不同的变化，从而增强其鲁棒性。

Methods of augmentation: Examples of basic augmentations include geometric transformations (e.g., rotation and translation), contrast and brightness changes, noise injection, and synthetic data generation (e.g., picture synthesis using GANs).

增强方法：基本增强的示例包括几何变换（例如旋转和平移）、对比度和亮度变化、噪声注入以及合成数据生成（例如使用 GAN 的图像合成）。

Impact on model training: Extended data improves the overall performance of the model by imitating various imagery conditions and patients. It reduces the rate of overfitting and also enhances the model’s performance with actual data.

对模型训练的影响：扩展数据通过模拟各种影像条件和患者来改善模型的整体性能。它降低了过拟合率，并增强了模型对实际数据的性能。

While dealing with medical imaging data, data security and privacy concerns are mandatory. The security of patient data is ensured by legal requirements such as HIPAA and GDPR.

在处理医学影像数据时，数据安全和隐私问题是强制性的。患者数据的安全性由 HIPAA 和 GDPR 等法律要求确保。

Data anonymization: When the photos are stripped of patient information, it is easier to conduct research and build models on them without compromising the patient’s privacy.

数据匿名化：当照片被剥离患者信息时，更容易在不损害患者隐私的情况下对其进行研究和构建模型。

Secure data handling: Performing data handling in a secure manner to avoid breaches was another set up that had to be undertaken when managing patients’ information.

安全数据处理：在管理患者信息时，必须采取另一项措施以安全方式进行数据处理以避免泄露。

Specifying the heterogeneity of the sample was important for building valuable machine learning models for various populations and circumstances. A large pool of data should comprise patients of both genders, different ages, from various geographic locations, with various types of images acquired at different times and through various techniques, and with different pathologies.

明确样本的异质性对于构建适用于各种人群和情况的有价值机器学习模型很重要。大量数据应包括男女患者、不同年龄、来自不同地理位置、通过不同时间和各种技术获取的各种类型影像，以及不同病理。

Addressing bias: It was advisable to search for the prejudices in the given dataset and try to correct them so that the performance of the proposed model was more equal and was not inclined toward some groups and conditions.

解决偏差：建议在给定数据集中查找偏见并尝试纠正它们，以便所提议模型的性能更加公平，不偏向某些群体和状况。

### 5.2 Image preprocessing techniques: normalization, augmentation, noise reduction

### 5.2 图像预处理技术：归一化、增强、降噪

In medical image analysis, normalization has been one of the simplest kinds of preprocessing that manipulates the pixel values of a diverse range of pictures so that their pixel value ranges are the same. The basic objective of normalization is to ensure that the input data is standardized. Consequently, it reduces the contribution of fluctuations in picture contrast and intensity and enhances the models used in machine learning. Typical methods of normalizing consist of:

在医学图像分析中，归一化是最简单的预处理类型之一，它操纵各种图片的像素值，使其像素值范围相同。归一化的基本目标是确保输入数据标准化。因此，它减少了图像对比度和强度波动的影响，并增强了机器学习中使用的模型。典型的归一化方法包括：

![](img/211c754cd1dd84920a171f497b33b689_579_0.png)

**Figure 17:** Image preprocessing techniques: normalization, augmentation, noise reduction.

**Figure 17：** 图像预处理技术：归一化、增强、降噪。

Min-max normalization: Normalizes pixel values to a standard range for ease of computation; it typically scales pixel values to fall within the interval [0,1] by subtracting the minimum of the pixel values of an image and dividing the result by the range of the pixel values. It normalizes the intensity of different images, thus making intensity values comparable with each other.

最小-最大归一化：将像素值归一化到标准范围以便于计算；它通常通过减去图像像素值的最小值并将结果除以像素值的范围，将像素值缩放到 [0,1] 区间内。它归一化不同图像的强度，从而使强度值彼此可比较。

Z-score normalization was concerned with getting pixel values to be approximately normally distributed by centering pixel value means and scaling by standard deviations. This method aids in correcting variations in the intensity of the image due to variations in acquisition conditions.

Z-score 归一化关注通过居中像素值均值并按标准差缩放，使像素值近似正态分布。该方法有助于纠正由于采集条件变化引起的图像强度变化。

Histogram equalization: Improves image density, whereby the pixel intensity values are normalized to increase the equality of the histogram. This technique helps to enhance the contrast of different features in medical images and consequently enhances the algorithm’s ability to identify and study the structures of interest.

直方图均衡化：改善图像密度，其中像素强度值被归一化以增加直方图的均衡性。该技术有助于增强医学图像中不同特征的对比度，从而增强算法识别和研究感兴趣结构的能力。

It was a technique for generating new training sets of the same size as the original data set with different variations of the same image. It also helps in the enhancement of a model’s generalization capability in machine learning and the management of the overfitting problem. Common data augmentation methods include

这是一种生成与原始数据集大小相同但具有相同图像不同变体的新训练集的技术。它还有助于增强机器学习中模型的泛化能力并管理过拟合问题。常见的数据增强方法包括

Geometric transformations: Examples are rotation, scaling, translation, and flipping. These transformations imitate changes within the spatial relations of the bones and organs, assisting models in discriminating elements irrespective of their position.

几何变换：示例包括旋转、缩放、平移和翻转。这些变换模拟骨骼和器官空间关系内的变化，帮助模型在不考虑位置的情况下区分元素。

Intensity variations: Changes in brightness, contrast, and saturation present in images can commence changes in the context in which the images were captured.

强度变化：图像中存在的亮度、对比度和饱和度变化可以启动图像被捕获的上下文中的变化。
