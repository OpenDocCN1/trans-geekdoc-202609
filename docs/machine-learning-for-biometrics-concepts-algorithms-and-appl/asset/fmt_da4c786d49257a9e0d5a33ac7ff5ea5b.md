
# Chapter 8: Real-time emotion engagement tracking of students using human biometric emotion intensities

Sumitav Acharya^[a](#B9780323852098000080.xhtml#af0010); Motahar Reza^[b](#B9780323852098000080.xhtml#af0015)  
^a Department of Computer Science and Engineering, National Institute of Science and Technology, Berhampur, India  
^b Department of Mathematics, GITAM Deemed to be University, Hyderabad, India

## Abstract

This chapter spouts the usefulness of using Human Emotion Intensities to track a Student's emotional engagement in a class being part of Behavioral Biometrics. The behavioral biometrics deals with the patterns of human activities. It includes physical and emotional biometrics, which signifies a trait to recognize the behavior. In a classroom, student distraction contributes to being one of the factors of behavioral biometrics. It varies in magnitude and duration. Student engagement is frequently viewed as one of the signs of addressing low performance, apathy and disengagement, and high failure rates. The emotions are intertwined with our facial expressions regulated by 43 facial muscles, which themselves are managed by two facial nerves. The dominant features, which show an absent-minded face present in a class using `FAU` (Facial Action Unit), are examined. This covers multiple aspects of tracking, ranging from the student entering the classroom when the first frame is captured, and then respective structures are differentiated till he/she is present in the class. In our approach, initially, the facial landmarks were recognized by annotating the distracted face dataset. Then, the same is trained with the responsible pixel values and labels to help the machine identify the associated features of a distracted/undistracted face. After processing the dataset, we concatenated two models to train the distracted dataset, one is Custom-Deep Emotion Network using Convolutional Neural Network, and the other one is `Reversed-NN` to maintain the symmetricity. Thus, in the output layer, we have the concatenation of both the outputs to recognize whether a face is distracted/undistracted. The pipeline supports deploying the model in real-time cameras to trace the behavioral biometrics of students. The experiments performed on the database strengthened the "proposed characteristics" that can be used for biometrics intentions.

### Keywords

Behavioral biometrics; Machine learning; `FAU` (Facial Action Units); Computer vision; Deep emotion-CNN; `Reversed-NN` (neural network); Biometric

## 1: Introduction

Knowing human deportment is a token of the judgment that demonstrates the visual evidence of facial movement or expression. Human emotion intensities [^(154)](#fn154)

This chapter derived behavioral attributes from multiple images of our custom-made "Distracted" dataset that uses understanding from `FACS` [^(155)](#fn155)

Although there exist multiple approaches focusing on student engagement tracking given that they are based on part-based methods, i.e., analyzing different movements in a face. Our primary goal is to associate prominent features out of face using Action Units, those contributing a distracted face, and then classifying according to that. Our model's multipurpose methodology supports various booming concerns related to student concentration [^(156)](#fn156)

## 2: Related work

As we know, behavioral biometrics deals with recognizing persons based on their unique behavioral traits. It opens up a horizon of traits like what we see in our day-to-day authentication strategies ranging from voice recognition, keystroke dynamics to human signature recognition. These strategies are majorly equipped in many of the modern applications to track the behavior of their users. But here, we have considered tracking the behavior of an individual through their emotions via facial emotion recognition. Thus, tracking the engagement of students via their emotions is one such application we have discovered. The existing art of methods represents the flow of engagement detection which is being divided into three main categories: Automatic, Semi-Automatic, and Manual. In general, machine-based systems promote observational strength, i.e., through pupil movements, facial emotions features can be extracted to identify an engaged student in a class. Now engagement detection focuses more on the methods like Facial Expression, Part-based methods which states the techniques to analyze a face through different action units also known as `FACS` and appearance-based methods.

The research conducted by Zewe Serpell and Yi-Ching Lin [^(157)](#fn157)

## 3: Methodology

Our workflow revolves around three layers of phases. The initial phase deals with obtaining image data and preprocessing [^(158)](#fn158)

![Fig. 1 Block diagram to explain the methodology.](images/B9780323852098000080/f08-01-9780323852098.jpg)

Fig. 1 Block diagram to explain the methodology.

### 3.1: Preprocessing steps for initial dataset preparation

Preprocessing is an enhancement of images to subdue unwanted damages further increasing the image's feature necessary for further processing [^(159)](#fn159)

The algorithm states that the imperfect pixel is often substituted as an average of nearby pixel values. Given that there exist multiple techniques to preprocess a damaged image ranging from Gaussian Blur technique, Fourier transform (mostly used in image filtering, compression, and reconstruction), to geometric transformation (where the locations of the pixels are altered) etc.

Our dataset consists of multiple 364*321 resolution images based on the input images we performed various preprocessing steps, i.e., Re-sizing, Normalization, Gaussian Blur technique, etc.

1.  **1** Every input image was resized up to 48*48 to maintain uniformity across the model. The background objects under a particular threshold were considered an input for the second stage of preprocessing.
2.  **2** Then we perform normalization on the images that change the range of pixel intensity values.
3.  **3** Then the Gaussian Blur technique was applied to remove unwanted noise.

### 3.2: Feature extraction technique

In our work, we have used Boosted `LBP` (Local Binary Pattern) as the feature extraction technique because it takes less computational time as compared to the standard `LBP` method. In this approach, the Chi-square distance between the corresponding `LBP`s of two facial images is majorly used for classification. This technique gave an accuracy of 96.72% on my dataset.

### 3.3: Interpreting FACS database

Facial Action Coding System is a technique of part-based methods where facial parts are considered to analyze human emotion. Firstly, the standard was revealed by an anatomist Carl-Herman Hjortsjö and later embraced by Ekman and Wallace V. Friesen and declared in 1978 [^(160)](#fn160)

The coding system also helps the interviewers to analyze the facial behaviors while communicating with the candidate. Using `FACS` [^(161)](#fn161)

Let us explore some of those in the database:

Now for the distracted dataset, we used the following action units that dominantly describe a distracted face (Figs. 2 and 3).

![Fig. 2 Sample FACS database.](images/B9780323852098000080/f08-02-9780323852098.jpg)

Fig. 2 Sample FACS database.

![Fig. 3 Distracted dataset sample.](images/B9780323852098000080/f08-03-9780323852098.jpg)

Fig. 3 Distracted dataset sample.

### 3.4: Step-wise algorithm

1.  **1.** Preparing the dataset
    1.  **1.1** Initial Preprocessing
    2.  **1.2** `data[]` <- load from csv with labels
