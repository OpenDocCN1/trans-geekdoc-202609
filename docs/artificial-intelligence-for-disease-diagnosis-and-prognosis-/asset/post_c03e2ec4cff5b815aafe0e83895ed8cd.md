
![](img/bffdb4a72252285ac92f0fad78a7f104_123_0.png)

Figure 6.1 A general explanation for sub-deep learning methods [8].

6.3 explains the COVIDx dataset, Section 6.4 illustrates the related works with DL models. Finally, an outline of future directions are presented in Section 6.5.

## 6.2 DATASET DESCRIPTIONS

Collecting datasets for COVID-19 cases is an important task for helping the research in support of their diagnosing tasks. The COVIDx dataset [10] and COVIDx-CT [11] are presented in this survey to explain their roles in several recent types of research in the COVID-19 pandemic.

## 6.3 COVIDx DATASET

COVIDx is an open-access benchmark dataset comprising 13,975 CXR images from 13,870 patient cases, containing the most publicly available COVID-19 positive examples. A representative X-ray scan from the COVIDx dataset [10] is shown in Figure 6.2.

## 6.4 COVIDx-CT DATASET

It was composed of 104,009 chest CT slices from 1489 patient instances, and it is called COVIDx-CT. This CT imaging data is noteworthy since it was produced from CT imaging data as shown in Figure 6.3. Their contribution includes cleaning and formatting raw data in a format appropriate for benchmarking, as well as giving bounding box annotations for body regions inside CT images [11, 12].

COVIDx has several advantages that make it common and more usable in many types of research that are related to COVID-19 cases. The first advantage is rapid triaging that can be done in parallel with viral testing for helping relieve the high capacities of cases exclusively in zones most affected. Figure 6.4 shows the main categories for the COVIDx dataset, and the needed libraries for implementation. The

![](img/bffdb4a72252285ac92f0fad78a7f104_124_0.png)

Figure 6.2 Examples of X-ray scans from the COVIDx dataset [10].

![](img/bffdb4a72252285ac92f0fad78a7f104_124_1.png)

Figure 6.3 Examples of CT scans of COVID-19 cases [11, 12].

first library utilized in Python is Matplotlib, which visualize and create animated, static, and interactive plots of the applied medical images. Scikit Learn provides all the methodologies that assist the implementation of the applied images. Numpy presents comprehensive mathematical operations and functions, which generate a random number with linear algebra routines. All libraries are grouped in Python version 3.6. In this work, we classify the three well-known categories of COVID-19, which are infected COVID-19, Normal, and Pneumonia. Also, CXR imaging can be quite effective for triaging in geographic areas where patients are instructed to stay home until the onset of advanced symptoms [13]. The second challenge is availability and accessibility where it is considered standard equipment in most healthcare systems. In particular, CXR imaging is much more readily available than CT imaging, especially in developing countries where CT scanners are cost prohibitive due to high equipment and maintenance costs [11]. More specifically, Gunraj et al. [11] combined five data repositories to create the COVIDx dataset by collecting the next categories of cases from each of the data repositories as: Non-COVID-19 pneumonia patient cases and COVID-19 patient cases from the COVID-19 Image Data Collection COVID-19 patient cases COVID-19 Chest X-ray Dataset.

## 6.5 RELATED WORK

This section presents a selection of related works of COVID-19 for classification, segmentation, and other tasks based on DL models. On July 11th, 2020, the most

![](img/bffdb4a72252285ac92f0fad78a7f104_125_0.png)

Figure 6.4 The main categories for the COVIDx dataset and the requirement libraries required for implementation [10].

![](img/bffdb4a72252285ac92f0fad78a7f104_125_1.png)

Figure 6.5 The general architecture of classification of the x-ray/CT images using DL approaches.

recent selection of papers is made using the keywords mentioned. The standard architecture for COVID-19 diagnosis employing DL methods using the COVIDx database is shown in Figure 6.5 [14]. In response to decision-making difficulties, Gunraj et al. [12] introduced the COVID-Net CT-2 dataset that enhanced deep neural network (DNN) architectures for COVID-19 detection from chest CT images trained on the largest quantity and diversity of multinational cases. It consisted of 4501 patients from at least 15 countries, which they used to explain and observed the decision-making behavior of COVIDNet CT. Ebadi et al. [15] introduced COVIDx-US, an open-access dataset of COVID-19-related ultrasound imaging data. The dataset contained ultrasound imaging data. The dataset was collected from a variety of images. It contained 150 lung ultrasound recordings, 12,943 processed images of cases with COVID-19, non-COVID-19 infections, and other lung diseases. Chowdhury et al. [16] proposed an ensemble deep convolutional neural network (ECOVNet) to detect COVID-19 that is implemented on 15,959 CXR images from 15,854 cases, with normal, pneumonia, and COVID-19 patients. They described the predictions in a way that is understandable. The method can distinguish COVID-19 with a positive predictive value of precision 91.6% for COVID-19 cases. Ambati et al. [17] proposed an AC-COVIDNet model by computing the sensitivity of the proposed method over the publicly available COVID-19 dataset. It is observed that the proposed AC-COVIDNet exhibits very promising performance as compared to the existing methods even with limited training data. Cherti et al. [18] introduce a pretraining model on a large-scale dataset using ImageNet with a range 21K/1K depending on X-ray chest images as well as comparing the full transfer learning applied on various objective datasets in mutually physical and medical domains.

Qi et al. [19] incorporate the local phase of X-ray image features into a multi-CNN feature architecture. The mathematical evaluation is performed on a dataset containing 8851 normal, 6045 types of pneumonia, and 3795 COVID-19 X-ray scan images. Only 7.06% of the labeled data and 16.48% of unlabeled data for training are utilized. Moreover, 5.53% of the data were used for validation purposes. Their method reached 93.61% with a mean accuracy value applied on a large-scale dataset of the tested 70.93% data. Celaya et al. [25] showed that the PocketNet architecture produces results comparable to traditional NN when performing various segmentation and classification tasks, while reducing the number of parameters by several orders of magnitude, reducing the GPU memory used by up to 90%, and speeding up data processing. The training time is as high as 40%, enabling such models to be trained in resource-limited environments.

Yang et al. [26] explored this difficult topic by showing a simple but successful technique in which the server and client share only a part of the model. Extensive testing using real-world healthcare tasks and baseline data shows that their method provides equivalent or better results while reducing privacy and security issues. They tested the FLOP algorithm on the COVID-19 dataset and demonstrated that it enables different institutions to collaborate and effectively train partially shared models without the need to disclose local patient data for federated learning.

Ali et al. [27] achieved a 5% rise in the F1-Score and a gap twice as great for general classification using CNN architecture to learn the optimum embedding space. Dong et al. [20] proposed a deep model for robust COVID-19 detection that employs Mixed High-Order Moment Feature (MHMF) and Multi-Expert Uncertainty-Aware Learning to capture compact and disentangled representational characteristics. MHMF can fully explore the benefits of using high-order statistics and extracting discriminative features of complex distributions in medical imaging. Hao et al. [21] used the innovative combination to classify COVID-19 chest radiographs which is rich in data but extremely unbalanced. They showed that by training all available tags, only 10% of the labeled data is needed to achieve accuracy. Its use of COVID-19 data in a fully supervised classification scenario demonstrates its model, which uses a generic ResNet backbone. They explored the benefits of using high-order statistics and extracted discriminative features from the complex distribution of medical images. Zhang et al. [33] suggested a new unsupervised method for learning medical visual representations directly from naturally occurring image-textual data pairs. They used a domain-agnostic strategy of pretraining and encoding the medical image with related data
