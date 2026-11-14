
subtype identification, and survival probability estimation. Frontiers in Plant Science. 13, 1–15 (2022). https://doi.org/10.3389/fpls.2022.1095547.
[74] Wu, J., Wen, C., Chen, H., Ma, Z., Zhang, T., Su, H., Yang, C.: DS-DETR: A model for tomato leaf disease segmentation and damage evaluation. Agronomy. 12, 1–16 (2022). https://doi.org/10.3390/agronomy12092023.

## Artificial Intelligence-Based Smart Identification System Using Herbal Images

### Decision Making Using Various Machine Learning Models

Sanyam Sharma,1,2 Subh Naman,1,3 Jayesh Dwivedi2 and Ashish Baldi1*

1 Pharma Innovation Lab, Department of Pharmaceutical Sciences and Technology, Maharaja Ranjit Singh Punjab Technical University, Bathinda, 15001, Punjab 2 Pacific Academy of Higher Education and Research University, Udaipur, Rajasthan 3 School of Pharmaceutical Sciences, CT University, Ferozepur Road, Ludhiana

* Corresponding author: +91-8968423848, baldiashish@gmail.com

### 9.1 INTRODUCTION

Ayurveda, the oldest and most conventional practice of Indian medicine, is essential for establishing specialized remedies and therapies. Drugs used in ayurveda are made of botanical ingredients and substances from animals, metals or minerals. India is a rich source of traditional medicines and medicinal herbs, making it an ideal place to look for new ones. Contemplate ayurveda is an Indian traditional medical system that is still utilized today due to its effectiveness in treating a variety of disorders holistically. It emphasizes total unification of consciousness, mind, body and soul [1, 2].

Herbs differ from other plants in their color, texture, and odor. Herb identification is typically done using organoleptic techniques, which mainly rely on botanists. Based only on their unique characters, distinct herb species belonging to the same family become harder to distinguish as a result of their identical physical characteristics. Contrary to humans, artificial-intelligence-assisted technology is supposed to be able to accurately distinguish various species [3].

Bioactive substances such as phenolics, anthocyanins, carotenoids and tocopherols can be derived through aromatic and medicinal plants with multiple therapeutic benefits and pharmacological effects [4]. However, just like other plant recognition, the work of physically recognizing medicinal and aromatic plants is challenging and time-consuming due to the inaccessibility of expert opinions. Many automatic plant or leaf recognition systems have been developed as a result of these issues, with the majority of them using machine learning techniques [5–7].

A branch of computer science called “artificial intelligence” aims to give machines additional intelligence. Learning is one of the fundamental prerequisites for any cognitive conduct. Most scientists today concur that intellect cannot exist without learning. Therefore, machine learning (ML) is one of the main subfields of artificial intelligence (AI) study and is really one of the fastest growing areas of the research [8]. Artificial intelligence was used by the system to start learning that anticipates new objects after learning based on previously trained/learned experience. It learns by extracting features, referring to particular quantifiable characteristics like more illuminating and exclusionary features [9]. Figure 9.1 depicts the basic steps of identification through machine learning models.

### 9.2 PRIOR ART

A mobile application called “MedLeaf” was developed by Laxmi and authors to help identify Indonesian plants based on their leaves. The feature extraction from the leaves from the library of 3502 photos from the 85 distinct species of Indonesian plants used geometrical characteristics and LBP. This model was developed using a PNN classifier. The accuracy of using a composite of features (85%) was shown to be superior to using a single feature alone [10].

By analyzing the photos of the leaves, Culman and coauthors developed an automated program for identifying nutrient deficiencies in oil palm plants. To create the datasets, they used 52 tagged photos of palm oil plant leaves. The datasets were then separated in a ratio of 6:1:2 into three categories: training datasets, model selection datasets, and test datasets. The development identification model has been used with ANN classification approaches. The performance matrices that the authors utilized to evaluate the effectiveness of the identification model included recall, precision, F1 score and accuracy. The authors came to the conclusion that the constructed model produced positive results in the performance metric tests. For improved use of the developed identification model, an android application has also been created based on this model [11].

![](img/9c1422d4c6a10143e1802787075307de_143_0.png)

FIGURE 9.1 Workflow of machine learning models.

Based on photographs of the tomato leaves, Elhassouny and Smarandache developed an automated tool for diagnosing tomato diseases. This identification model, which was developed using CNN classification techniques and was trained on 7176 photos of tomato leaves, was created. Ten distinct tomato plant diseases have been recognized by the model. Accuracy, the average loss curve and other performance matrices were used, and the results were reported to be satisfactory [12].

A mobile-based application was developed for plant leaf identification by Akiyama and coworkers where they examined three CNN models, namely MobileNetV2, MobileNet and VGG19. Images of 33 different categories were used to build the database for the model development. For comparing the three CNN models, various performance metrics including F1 score, drop-out rate and calculation time were used. In all performance metrics, authors found that the MobileNetV2 CNN model was the best of the three [13].

Tang and his group proposed a CNN-based model for diagnosing grape diseases. A unique technique comprised of lightweight CNN and the channel-wise attention (CA) mechanism is proposed for tiny and low-latency models. The backbones are ShuffleNet V1 and V2, with squeeze-and-excitation (SE) blocks employed as a CA technique to improve the ShuffleNet design. The proposed model is supported by an available dataset of 4062 photographs of grape leaves divided into four classes—three healthy and one diseased class. The experiments’ findings demonstrated that the suggested technique has been successful and accurate to an acceptable degree [14].

On the basis of a leaf analysis, Yang and Guo compared various ML models for the diagnosis of plant disease. The authors came to the conclusion that machine learning models are a crucial and effective technique for obtaining results that can be verified quickly after analyzing a significant quantity of data [15].

Ferentinos presented a deep CNN model for disease identification of plants through analysis of leaves of plants. The training and development of the model was done on a freely available database of approximately 89,000 images. The photographs in the database consists of both types of images, i.e., in laboratory setting and under original cultivation conditions. Results of the developed model showed an accuracy of 99.71% with VGG CNN techniques [16].

De Luna and co-workers proposed an automatic system for the identification of plants of the Philippine region. Datasets were created from 12 different species of herbal plants. The ANN-based neural network was utilized for the development of this automated system for identification. For training the datasets, 50 images were used. The datasets were trained with the developed neural network with the aid of Python and reached an accuracy of 98.16% identification of whole datasets. For testing the datasets, about 72 sample images were utilized. The trained neural network with the help of MATLAB® achieved an accuracy of 98.61% in identification of an unknown sample [17].

On datasets related to plants, Joseph and colleagues did a comparison study of a few traditional features extracted and deep CNN approaches. The HOG feature descriptor combined with KNN and the HOG-BOW mixed with SVM and MLP classifiers were contrasted against AlexNet and GoogleNet, respectively trained at scratch as well as utilizing fine-tuned variations as deep CNN architectures. Three plant-datasets-based picture identification systems were tested and found that they performed admirably. The authors came to the conclusion that enhanced deep CNN architectures routinely outperform conventional feature descriptor methods [18].

Based on the analysis of leaf pictures taken in their natural habitat, which can be subjected to a variety of lighting conditions and complex backgrounds, Putzu and coauthors presented a mobile app for the computerized identification of plant species. The main goal of this research was to construct and design a system that could recognize and segment the target leaf automatically. It is focused on saliency extraction to choose the targeted leaf and classification employing the region growing methodology, which utilizes both the data from the saliency map and the color features of every individual pixel [19].

A machine learning model, built on the k-NN technique, was developed by Munisami and his group. With an accuracy of 83.5%, the created system was evaluated on 640 leaves from 32 different species groups. Using color histogram approaches, accuracy was further raised to 87.3%. The developed model is also very user-friendly and robust [20].

For unsupervised feature visualizations of 44 plant species acquired at the Royal Botanic Gardens in Kew, England, Lee and his team created a CNN model. Instead of using a box approach, a deconvolutional network-based visualization technique (DN) was employed to gain understanding of the extracted features through the CNN model. It has been found that different order venations have been used to represent each type of plant. The authors came to the conclusion that experimental results employing these CNN features with different classifiers showed consistency and superiority as contrasted to state-of-the-art approaches that depend on hand-crafted characteristic [21].
