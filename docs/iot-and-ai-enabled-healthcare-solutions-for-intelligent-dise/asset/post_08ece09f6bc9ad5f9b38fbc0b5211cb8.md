
- [80] Al-Thanoon, A., Qasim, S. and Algamal, Y. (2021). Improving nature inspired algorithms for feature selection. J. Ambient Intell Human Comput. https://doi.org/10.1007/s12652-021-03136-6.

- [81] Sasikala, E., Kannani, P., Gopalakrishnan, R. and Radha, R. (2021). Identification of lesion using an efficient hybrid algorithm for MRI brain image segmentation. Journal of Ambient Intelligence and Humanized Computing, (2021): 1–11.

- [82] Priyadharshini, P. and Zoraida, B. S. E. (2021). Bat-inspired metaheuristic convolutional neural network algorithms for CAD-based lung cancer prediction. J. Appl. Sci. Eng., 24(1): 65–71. https://doi.org/10.6180/jase.202102_24(1).0008.

- [83] Sathananthavahi, V. and Indumathi, G. (2020). BAT optimization based retinal artery vein classification. Soft Comput. https://doi.org/10.1007/s00500-020-05339-z.

- [84] Nakamura, R. Y. M., Pereira, L. A. M., Costa, K. A., Rodrigues, D., Papa, J. P. and Yang, X.-S. (2012). BBA: A binary Bat algorithm for feature selection. pp. 291–297. In: Proceedings of the 2012 25th SIBGRAPI Conference on Graphics, Patterns and Images, Ouro Preto, Brazil, 22–25 August 2012. [Google Scholar]

- [85] Bansal, J. C. and Singh, S. (2021). A better exploration strategy in grey wolf optimizer. J. Ambient Intell Humaniz Comput., 12(1): 1099–1118. https://doi.org/10.1016/j.advengsoft.2013.12.007.

- [86] Azlan, H., Zain, M., Sallehuddin, R. and Yusof, Y. (2018). Recent studies on optimization method of Grey Wolf Optimiser (GWO): a review. Artif Intell Rev. https://doi.org/10.1007/s10462-018-9634-2.

- [87] Sahoo, A. and Chandra, S. (2017). Multi-objective grey wolf optimizer for improved cervix lesion classification. Appl Soft Comput J., 52: 64–80. https://doi.org/10.1016/j.asoc.2016.12.022.

- [88] Shankar, K., Lakshmanaprabu, S. K., Ashish Khanna, Sudeep Tanwar, Joel J. P. C. Rodrigues and Nihar Ranjan Roy. (2019). Alzheimer disease detection using Group Grey Wolf Optimization based features with convolutional classifier. Comput. Electr. Eng., 77: 230–243. https://doi.org/10.1016/j.compleleceng.2019.06.001.

- [89] Al-Tashi, Q., Rais, H. and Jadid, S. (2018). Feature selection method based on grey wolf optimization for coronary artery disease classification. pp. 257–266. In: International Conference of Reliable Information and Communication Technology. Springer, Cham. https://doi.org/10.1007/978-3-319-99007-1_25.

- [90] El Bakrawy, L. M. (2017). Grey wolf optimization and naive bayes classifier incorporation for heart disease diagnosis. Aust. J. Basic Appl. Sci., 11(7): 64–70.

- [91] Heidari, A. A., Mirjalili, S. and Faris, H. (2019). Harris hawks optimization: algorithm and applications. Futur Gener Comp Syst., 97: 849–872.

- [92] Kaur, N., Kaur, L. and Cheema, S. S. (2021). An enhanced version of Harris Hawks Optimization by dimension learning-based hunting for Breast Cancer Detection. Sci. Rep., 11: 21933. [Google Scholar]

- [93] Too Jingwei, Abdullah Abdul Rahim, MohdSaad Norhashimah. (2019). A new quadratic binary harris hawk optimization for feature selection. Electronics, 8(10): 1130.

## Chapter 5
## Deep Learning Applications for Chronic Disease Detection and Prevention
Shaheen Layqa¹,* and B. Manjula²

### 1. Introduction

Parkinson disease (PD) is a type of chronic disease which gets worse as time passes. In a survey by World Health Organization, it was found that PD is the second most common neurodegenerative disorder in the United States. PD cannot be trimmed completely by its root but it can be detected and prevented. To prevent and control PD, the Parkinson disease patient has to visit the clinic at regular basis and have medical examinations under supervision of trained medical staff. This is an inconvenient task as it is mostly found in aged people [1–2]. To make it convenient for all age group people, most of the medical doctors are dependent on the telemonitoring applications, which are found to be more reliable decision support systems. Parkinson’s disease patients can now collect data or perform tests at home, and through the internet, this data can be transmitted to a dedicated server.

The cause of Parkinson disease may vary; however, it is mostly related to the genetic disorder, injury in brain, personal stress, nerve injury, life style and environmental related health problems and poor diet. It is observed that Parkinson disease shows impact mostly on speech, handwriting and walking [3]. As it is becoming a burning issue, most of the researchers are working on it and have suggested detection techniques which were dependent on voice data samples. The drawback with voice or speech data is that accuracy is very low and unreliable results were found due to lack of proper validation methodologies. If a patient is suffering with simple cough, cold, throat infection, stammer or dysarthria, then the voice samples are not so efficient to predict PD.

¹ Department of Computer Science, Singareni Women’s Degree & PG College, Kothagudem, Telangana, India.
² Department of Computer Science, Kakatiya University, Warangal, Telangana, India.
* Corresponding author: mdshafeen1905@gmail.com

In this chapter, handwriting of a PD patient is considered as an alternative to voice data samples. The handwriting of a PD patient can be obtained using manual methods (paper and pencil) or computer-based methods. The computer based method is the most appropriate and commonly used nowadays.

Due to the shaking or trembling caused by PD, patients are often unable to write legibly. Their handwriting becomes too small, unclear, and slanted. Therefore, handwritten data samples are more appropriate than the voice samples for PD detection. After collecting the handwritten dataset, the classification is done using one of the popular deep learning techniques known as Neural Network.

Deep Learning Neural Network (DLNN) is based on artificial neural networks, and mimic the structure and function of the human brain. The DLNN is also able to support large amount of data. The block diagram of DLNN is shown in Fig. 1. The DLNN consists of three layers: input layer, hidden layer and output layer.

As the PD cannot be detected using a single layer, multiple hidden layers are required, which can be efficiently done by the DLNN. Consequently, this chapter focuses on deep learning techniques instead of machine learning techniques. Finally, a comparison between machine learning technique and DLNN has been done, revealing that handwritten datasets perform better when analyzed using deep learning techniques.

![](img/a797255277085a0fa8aa2736cb720e31_85_0.png)

### 2. Literature Survey

Mahnaz Behroozi and Ashkan Sami worked on “A Multiple-Classifier Framework for Parkinson’s disease Detection Based on Various Vocal Tests [4]”. They tried to resolve the problems related to summarizing of vocal test data and single classifier. G. Dimauro, V. D. Nicola, V. Bevilacqua, D. Caivano, and F. Girardi proposed “Assessment of Speech Intelligibility in Parkinson’s Disease Using a Speech-To-Text System” [5]. The Google speech is used to convert speech into text but it requires language skills. Md. Tahmid Rahman Laskar, Md. Tahmid Hossain, Abu Raihan Mostofa Kamal, and Nafiul Rashid proposed “Automated Disease Prediction System (ADPS)” [6]. “User Input-based Reliable Architecture for Disease Prediction” completely depends on relevant attributes. L. Berus, S. Klancnik, M. Brezocnik and M. Ficko worked on Classifying Parkinson’s Disease Based on Acoustic Measures Using Artificial Neural Networks [7]. Betul Erdogdu Sakar, M. Erdem Isenkul, C. Okan Sakar, Ahmet Sertbas, Fikret Gurgen, Sakir Delil, Hulya Apaydin, and Olcay Kursun proposed “Collection and Analysis of a Parkinson Speech Dataset with Multiple Types of Sound Recordings [8]”, utilizing central tendency and standard deviation. However, these methods are complex, difficult to understand, and prone to problems with extreme values, failing to cover the full range of data. Yasin Ozkanca, Miraç Göksu Öztürk, Merve Nur Ekmekci, David C. Atkins, Cenk Demiroglu, Reza Hosseini Ghomi worked on “Depression Screening from Voice Samples of Patients Affected by Parkinson’s Disease [9]”. But only a reduced dataset is used to trace the depression. Wojciech Froelich, Krzysztof Wrobel, and Piotr Porwik proposed “Diagnosis of Parkinson’s Disease Using Speech Samples and Threshold-Based Classification [10]”. Savitha S. Upadhyay, and A. N. Cheeran proposed “Discriminating Parkinson and Healthy People Using Phonation and Cepstral Features of Speech [11]”. Ondrej Klempíř, and Radim Krupicka proposed “Machine Learning Using Speech Utterances For Parkinson Disease Detection [12]”. Srishti Grover, Saloni Bhartia, Akshama, Abhilasha Yadav, and Seeja K. R. presented a work “Predicting Severity Of Parkinson’s Disease Using Deep Learning [13]”. But linear algebra knowledge is required and TensorFlow has low computation speed. Aarushi Agarwal, Spriha Chandrayan and Sitanshu S. Sahu presented a work “Prediction of Parkinson’s Disease using Speech Signal with Extreme Learning Machine [14]”. The complete accuracy depends on accurate selection of bias and weight. Muntasir Hoq, Mohammed Nazim Uddin and Seung-Bo Park presented a work related to “Vocal Feature Extraction-Based Artificial Intelligent Model for Parkinson’s Disease Detection” [15] but sparse auto encoder makes it hard to understand the features.

### 3. Proposed Method

The handwritten dataset (HWDS) is used for the PD detection and prevention. In this chapter, DLNN classification method is used to differentiate the values of each text dataset. The overall view of proposed framework can be shown in Fig. 2.

- 1. Data preprocessing: It is the preliminary step by which the quality of data is increased. During this step, HWDS is collected, subsets are created and feature selection is performed.
- Handwritten Dataset extraction: Collecting of HWDS from HWDS repository.
- Subsets: Here subsets of the given HWDS are created by separation. Each subset contains instances of the same type. A total of 77 samples, each with seven instances, are created. Without this step, classification results cannot be obtained.
