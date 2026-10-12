

# Machine Learning Approaches in Biometric Systems: Research Advances and Applications

Biometric systems automatically recognize identities by utilizing human physiological and behavioral characteristics. Advances in sensor technology have attracted the attention of numerous researchers, driving the introduction of a large number of novel biometric traits, providing privacy and security guarantees for various application systems ranging from industry to healthcare. Over the past few decades, to improve recognition performance, a large number of machine learning algorithms have been applied to various biometric scenarios. The core significance of machine learning algorithms lies in determining individual identities by associating biometric patterns with corresponding enrolled users. However, in high-security applications, security and recognition accuracy are the primary concerns, which can be addressed by designing multimodal biometric systems. As the name suggests, multimodal biometrics fuse two or more different biometric traits (e.g., fingerprint, iris, face, palmprint, etc.), and their working principle is similar to unimodal biometrics, with only an added information fusion module. Given the increasing number of biometric systems and their applications, the field still requires extensive in-depth research and development.

Currently, a large number of biometric systems exhibit limited recognition rates or accuracy in unconstrained scenarios due to poor image acquisition quality, including low contrast, large illumination variations, and insufficient user cooperation. These challenges have prompted many researchers to work in multiple sub-fields, such as extracting discriminative features, adopting efficient classifiers, and performing information fusion at different stages of multimodal biometric systems. Additionally, another research direction is to provide security guarantees for biometric information systems to address security requirements in online identification modes in many applications. This book covers the latest research advances in the field of biometrics, aiming to improve recognition performance in various applications and solve security issues, such as online transactions, e-commerce, access control, law enforcement, border security, healthcare, etc.

This book specifically explores current research advances in the field of biometrics and biometric-based applications, aiming to improve personal identification performance. The book consists of 12 chapters, each elaborating on the concepts and fundamentals of recent hot topics in biometrics, reviewing the latest methodologies, revealing experimental results, and comparing them with state-of-the-art technologies to highlight their effectiveness in recognition and future directions. Furthermore, the content of this book is organized according to recognized biometric traits and a few novel traits, combined with biometric security and latest applications, making each chapter independently readable. The content of each chapter is briefly introduced below.

## Chapter “Machine Learning Approach for longitudinal face recognition of children”

This chapter introduces a novel application utilizing face biometrics for children's identity recognition. Face recognition for children under 6 years old helps provide them with medical services and assists in finding missing children. The authors constructed a new face database, collecting individuals' face images over a period of time (specifically intervals of several months), named the Longitudinal Face Database. Experiments extensively used various machine learning classifiers, such as Support Vector Machines (`SVM`), K-Nearest Neighbors (`KNN`), Logistic Regression (`LR`), Decision Trees, Gaussian Naive Bayes, and Convolutional Neural Networks (`CNN`). Comparative experimental results demonstrated the effectiveness and superiority of the proposed `CNN`-based method in improving accuracy. Finally, the authors suggest expanding the database scale and improving the model as possible future research directions.

## Chapter “TBFR: Thermal Biometric Face Recognition—A Noncontact Face Biometry”

This chapter proposes a novel thermal face recognition method aimed at eliminating the effects of illumination intensity variations, pose, accessories, aging, and other factors present in existing face biometric systems. The authors fused facial geometric features with pre-trained `ResNet-50` features to improve recognition performance. Experimental results show that this method is more robust compared to existing methods.

## Chapter “Multimodal Biometric Recognition using Human Ear and Profile Face: An Improved Approach”

This chapter explores an improved ear biometric method based on handcrafted features of the ear and profile face under feature-level fusion and score-level fusion schemes. Recently, Convolutional Neural Network models for ear biometrics have been proposed, with experimental results showing performance comparable to state-of-the-art methods. However, deep learning-based biometric applications require a large number of training images, massive memory for data processing, and huge computational complexity, at the cost of improved recognition rates. The authors of this chapter focus on a multimodal approach based on the ear and profile face, aiming to improve recognition performance by reducing processing complexity. The effectiveness and superiority of the method were verified through multiple sets of comparative experiments.

## Chapter “Statistical Measures for Palmprint Image Enhancement”

This chapter reviews image enhancement methods in palmprint images and their quality assessment metrics. The databases most commonly used in palmprint image enhancement techniques are discussed in detail. Image enhancement plays a key role in the preprocessing step of biometric systems, providing better recognition performance for improving accuracy and recognition rates.

## Chapter “Retina Biometrics for Personal Authentication”

This chapter attempts to explore retina biometrics using the `ANFIS` model. It focuses on discussing the `ANFIS`-based Retina Biometric Authentication System (`ARBAS`) and its significance. Additionally, this chapter provides readers with the knowledge base required to select appropriate feature sets and sufficient techniques to conduct robust research in this field.

## Chapter “Gender Recognition from facial Images using Multi-Channel Deep Learning Framework”

This chapter demonstrates a multi-channel deep learning framework based on an automated gender recognition method. The authors attempt to extract discriminative features from raw face images of `GoogleNet`. They fused feature vectors from two sources: one obtained from feature images generated by `LDP` filters, and the other obtained directly from raw face images, both fed as input into `GoogleNet`. Finally, `CCA/DCA` is used to merge the feature sets as input to the `SVM` classifier to achieve gender recognition for given input images. The book conducts a series of experiments and provides a comprehensive and detailed explanation of the experimental results.

## Chapter “Implementation of Cardiac Signal for Biometric Recognition from Facial Video”

This chapter explores the Heartbeat Signal from Facial Video (`HSFV`) as biological evidence for recognizing individual identities. This chapter provides motivation and knowledge support for researchers to open up novel research directions in the field of biometrics.

