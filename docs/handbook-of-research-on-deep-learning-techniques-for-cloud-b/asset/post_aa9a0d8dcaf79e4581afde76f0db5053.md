
## Chapter 6

## Blockchain-Based Deep Learning Approach for Alzheimer’s Disease Classification

V. Sanjay
https://orcid.org/0000-0002-6383-3793
Vellore Institute of Technology, Vellore, India

P. Swarnalatha
Vellore Institute of Technology, Vellore, India

## ABSTRACT

Blockchain is an emerging technology that is now being used to provide novel solutions in several industries, including healthcare. Deep learning (DL) algorithms have grown in popularity in medical image processing research. AD is diagnosed by magnetic resonance imaging (MRI) images. This study investigates the integration of blockchain technology with a DL model for Alzheimer’s disease prediction (AD). This proposed model was used to classify 3182 images from the ADNI collection. The edge-based segmentation algorithm has overcome the segmentation problem. During the investigation’s test stage, the DL-EfficientNetB0 model with blockchain earned the highest accuracy rate of 99.14%. The highest accuracy, sensitivity, and specificity scores were obtained utilizing the confusion matrix during the comparative assessment stage. According to the study’s results, EfficientNetB0 with blockchain model surpassed all other trained models in classification rate. This study will aid clinical research into the early detection and prevention of AD by identifying the sickness before it occurs.

## INTRODUCTION

AD is a kind of dementia that often affects the elderly and is characterized by gradual cognitive impairment and a deterioration in the brain’s functioning skills. According to the 2016 World Alzheimer Report, around 46.8 million individuals have AD and dementias which is illustrated as Figure 1. It is anticipated that the incidence of Alzheimer’s will double every 20 years and that by 2050, the global prevalence of Alzheimer’s will reach around 131.5 million (Ding et al., 2019). Approximately 60% of the brain’s total volume is contained within this area. Grey matter, situated deep inside the brain, performs this crucial processing. This structure consists of the dendrites and nuclei of neurons. It accounts for around 40% of the volume of the brain. The white and grey matter of the central nervous system and spinal cord are protected from mechanical shocks by cerebrospinal fluid. Different hormones released by the hypothalamus facilitate communication between white and grey matter in the central nervous system (Zhang et al., 2019). Artificial Intelligence (AI) encompasses a vast array of algorithms and methodologies, including genetic algorithms (Wang et al., 2019; Alberdi & Weakley, 2018; Li et al., 2019), neural networks (Pavisic et al., 2021), and evolutionary algorithms (López-De-Ipiña et al., 2020; Sapey-Triomphe et al., 2015; Tzimourta, n.d.; Afrantou et al., 2019).

![](img/4a898a1f1442f24bfffba36e7ac62ad8_123_0.png)

The most obvious symptoms include ineffective communication, increased susceptibility to infection, poor judgment, poor sense of direction, short-term memory loss, and visual difficulties. Recent research indicates that approximately 50 million people worldwide have Alzheimer’s (Krishna et al., 2019; Chandra et al., 2019; Ke et al., 2019; Zheng et al., 2019).

However, most existing DL methods train a deep convolutional neural network (CNN) model from scratch and suffer from limitations (Lian et al., 2020). First, it requires a substantial quantity of labeled training data, which may be difficult to acquire in the medical domain. Second, it requires enormous computational and memory resources; training a model would take longer without them. Thirdly, it requires careful optimization of network parameters via regularisation; failure to do so leads to overfitting or underfitting issues. It is also essential to ensure that the trained model generalizes well to unknown data (Maggipinto et al., 2017).

Using functional magnetic resonance imaging (fMRI) images to train a deep neural network with blockchain to detect a wide variety of brain events (Chitradevi & Prabha, 2020; Lu et al., 2018), we achieved this goal. Due to advancements in the scientific and technical sectors, computer-aided diagnostic (CAD) systems have been developed. These systems aid in the analysis of medical imaging by researchers and clinicians.

In the early phases of AD, computerized diagnosis is essential for human health. Because AD is a neurological disorder, its incubation period is lengthy. Consequently, it is essential to monitor AD symptoms at various times. Using a variety of image categorization techniques can improve the accuracy of AD diagnosis.

DL researchers have discovered other ways to identify the severity of AD in individuals using MRI scan images (Gorges et al., 2018; Yu et al., 2020). In terms of image processing and analysis, the higher the image quality, the more accurate the results.

The rest of this article is structured as follows: the “Related Work” section reviews pertinent works. The “Problem Statement and Solution Plan” section summarizes the study’s primary concerns and objectives. The section “Materials and Methods” discusses the proposed method. The section “Experimental Outcomes and Model Evaluation” evaluates the experiments and their results. The section “Conclusion” finalizes the article.

## BACKGROUND STUDY

Neuroimaging data for the early detection of AD may be enhanced by using DL algorithms, which have piqued the attention of researchers interested in identifying hidden features. The authors of Sarraf and Tofighi (2016) successfully employed CNN to separate the functional MRI data of Alzheimer’s patients from those of standard controls in order to differentiate an AD-affected brain from a normal (healthy) brain. A 96 percent accuracy rate was attained. Complex difficulties need a more intricate network design. Using graph theory and ML, the authors of Hojjati et al. (2017) developed a novel classification scheme for MCI (ML). Groups with MCI had altered brain regions exactly identified. The suggested model depicted just the development of MCI; intermediate phases of MCI were not distinguished. ML-based computer-assisted diagnosis may distinguish Alzheimer’s patients from healthy controls, according to Duc et al. (2019). This makes it hard to determine precisely which components of the neural network influenced its decision-making process. Using functional magnetic resonance imaging (fMRI), Pan et al. (2020) propose classifier ensembles constructed using CNN and ensemble learning (EL) to identify individuals with MCI or AD.

A combined CNN and EL approach may determine which brain areas are the most discriminable according to the qualified ensemble model. The authors found that classification accuracy might be enhanced by using optimization methods or other DL techniques. To increase EMCI identification, the authors devised a multi-scale enhanced GCN (MSE-GCN) to study individual differences and knowledge associations among multiple topics (Yu et al., 2020). The suggested model was trained using the picture and population phenotypic data. The accuracy of LMCI vs. NC was 93.46%. The authors proposed more efficient network models for pinpointing precise brain regions. The authors (Guo & Zhang, 2020) suggested an auto encoder-based technique for discriminating between normal aging and disease development.

The suggested technique reliably diagnoses AD by using efficiently biased neural network functionality. The authors of Parmar et al. (2020) employed a three-dimensional convolutional neural network to develop a binary classifier capable of discriminating between AD and CN resting-state fMRI findings.

## Problem Statement and Plan of Solution

In the “Related Work” section, you can find a list of architectures capable of detecting AD and categorizing medical pictures. On the other hand, most of them do not use remote AD monitoring and patient counseling tools like transfer learning algorithms, multi-class medical image categorization, or an AD checking online service. Literature on these subjects has been woefully underwhelming. Medical imaging is hampered by the small size of the data set.

## METHODS AND MATERIALS

Early identification of AD is critical for avoiding and regulating the disease’s progression. Our objective is to develop a framework for the early identification and categorization of AD phases is indicated in Figure 2.

### Dataset

Using T1w MRI, the ADNI dataset gathered all necessary training data. Axial, Sagittal, and Coronal views are all available in DICOM format. Three hundred individuals in the sample have been labeled AD, EMCI, LMCI, or NC. There are 75 patients and 21 to 816 scans each class. The AD class has 3182 pictures, the EMCI class has 1732 images, the LMCI class has 175 images, and the NC class has 1275 images. In a 3182 2D format, all medical data was pulled.

### Preprocessing Step

The collected data comprises not evenly distributed classifications. Oversampling and undersampling were used to overcome this problem. Consequently, the collection has grown to 3182 images. A suitable format has been applied to the dataset after being normalized, resampled, and denoised. The data may be denoised using a non-local method for blurring a picture.

### Edge-Based (EB) Image Segmentation and Clustering

The area of interest’s orchestrated location is determined, and the chosen region is planted and zoomed in. This image is used to modify the pixel’s intensity. Pixels are referred to as white or black for the picture, depending on their brightness. The White Area illustrates living tissue, whereas the Black Area illustrates dead tissue. The number of white and black pixels is computed, and if the black pixel is very small, the patient is OK. According to the Black Pixels ratio, the patient has a slight learning impairment, AD, or healthy. Thresholding is a widely used technique for picture segmentation. The grayscale or pixel power segmentation is achieved in this image segmentation technique. It is two-tier thresholding for classifying pixels into two groups based on the intensity of the image pixels.
