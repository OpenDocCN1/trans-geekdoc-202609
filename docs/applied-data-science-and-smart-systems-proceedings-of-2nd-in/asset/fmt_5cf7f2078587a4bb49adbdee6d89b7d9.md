
Deng et al., came up with a proposed model “Improving Accent Identification and Accented Speech Recognition Under a Framework of Selfsupervised Learning”. They used a technique called Self-Supervised Contrastive Learning (SSCL). It is used to learn the representations of speech data. The SSCL framework consists of two main components – a feature encoder and a contrastive loss function. They have also used Automatic Speech Recognition (ASR) model. It is used to learn representations as input features. The limitations of this model are as follows: (i) The system may require computational resources, particularly for training the feature encoder. (ii) The proposed methodology may require large amount of unlabeled speech data for learning feature encoder.

Singh et al., came up with a model know as “Foreign Accent Classification using Deep Neural Nets”. In this paper, they used a deep neural network (DNN) to categorize foreign accents in speech recordings and compare its overall performance to other conventional techniques. The authors educate the DNN at the TIMIT Acoustic-Phonetic Continuous dataset and compare its overall performance using one-of-a-kind class metrics. The results show that the DNN outperforms different methods to classify foreign accents. The most important disadvantages of this device are (i) Training time is massive and need computing assets. (ii) Dataset does not include many accents.

Radzikowski et al., proposed a model called “Accent Modification for Speech Recognition of Non-native Speakers using Neural Style Transfer”. In this model, they have got accrued dataset of speech recordings from each local and non-local speaker and pre-processed the statistics by extracting relevant capabilities along with MFCC. Then they educated a DNN to carry out accent amendment by mapping the features of non-native speaker’s speech to the corresponding capabilities of local speaker’s speech. Disadvantages of this gadget are (i) Accent change can result in a loss of cultural identification for non-local audio system. (ii) Accent change raises moral worries regarding cultural and linguistic range.

Joseph et al., proposed a system known as “Domestic Language Accent Detector Using MFCC and GMM”. Gathering a set of training data from various Malayalam-speaking regions is the initial step. Different Malayalam accents can be distinguished using MFCCs. With the characteristics extracted, a Gaussian Mixture Model (GMM) is constructed. A blend of Gaussian distributions is represented by the probabilistic GMM model. With the assist of the Expectation-Maximization (EM) approach, the model parameters are anticipated. The MFCC features that had been derived from the gathered training information are used to teach the GMM model. With the checking out information, the GMM version’s accuracy is assessed.

## III. Objectives

This paper is geared toward producing a sophisticated machine mastering technique this is capable of classifying three exceptional kinds of English accents: Indian, American and British. Another objective is to enhance speech recognition and language gaining knowledge.

## IV. Problem statement

The problem statement for the paper is to expand an HMM-primarily based model that could appropriately detect specific accents in English speech. Capturing unique phonetic features at same time is difficult because of various different traits. However, the development of a correct dialect detection model has essential realistic programs in numerous fields, together with speech reputation, language teaching, and forensic evaluation.

## V. Proposed Model

The main aim of this proposed model is to find the accents of English language. The model will find the Indian, Britain, and American accent of English. Initially, an audio file in mp3 format has to be provided to the model and then the model finds the loglikelihood value for each of the three accents. After calculating the log-likelihood values, the model displays the accent with high log-likelihood value.

The model is divided into four modules. First module involves pre-processing the input audio file. Second module involves feature extraction using MFCCs. Third module involves training of the HMM using GMM. Forth module involves testing.

Now the model is ready to classify the accents into Indian, Britain, and American accent. Given the audio file in mp3 format to the graphical user interface (GUI), the GUI gives the corresponding accent as output.

### 3.1. Modules

Module 1 – Processing the input. In this module the speech signal is pre-processed to remove noise and converted into suitable format for further processing.

Module 2 – Feature extraction. In this module, the features Mel-Frequency Cepstral Speech signal is given as an input for the HMM which is processed to extract coefficients.

Module 3 – Training the model. In this module the HMM is trained on the dataset of labeled speech samples. GMM algorithm is used to train the HMM model.

Module 4 – Testing. In this module, the model is tested by using some dataset. And finally when the input is given, the output is generated.

[Figure 2.1](#ch2.xhtml#fig2_1) shows the proposed model. The figure shows first the input audio files in mp3 format of the human. It is taken as the input signal and then it is pre-processed. It removes the noise if any present. And then the features of the audio are extracted using MFCCs. The given dataset is divided randomly into training and testing datasets. The HMM is trained with GMM from the training dataset. And then the model is tested using testing dataset and accuracy is calculated. Finally, the model is ready.

![Figure 2.1 Proposed model diagram](images/fig2_1_B.jpg)

[Figure 2.1 Proposed model diagram](#ch2.xhtml#R_fig2_1)

An audio file is given as input to the model. The model calculates the log-likelihood values to each accent. The accent with more log-likelihood value is given as output to the user.

### 3.2. Algorithms

| Algorithm 1: Training the data |

| --- |

| 

1.  Start

2.  Import all the required packages.

3.  Set the number of classes and HMM states.

4.  Define the file paths to the data.

5.  Define the function to extract features using MFCCs from audio files.

6.  Define the function to pre-process the data by computing the mean MFCCs for each audio file in a directory.

7.  Define the training and testing ratios.

8.  Split the data into training and testing sets for each class.

9.  Train a Gaussian HMM for each class on the training data using the HMMlearn library.

10.  Stop

 |

| Algorithm 2: Testing the data |

| --- |

| 

1.  Start

2.  Import all the required packages.

3.  Create a sample data set from the test data set.

4.  Pre-process each file in the dataset that is splitted.

5.  Load the pre-trained HMM models for each class.

6.  For each test audio file, extract its MFCC features.

7.  Compute the log-likelihood of the test audio file for each class HMM.

8.  Choose the class with the highest log-likelihood as the predicted class for the test audio file.

9.  Compare the predicted class to the actual class label for the test audio file to compute accuracy.

10.  Repeat steps 2–5 for all test audio files.

11.  Calculate the test set’s overall accuracy by dividing the number of test files that were successfully categorized by the total number of test files.

12.  Stop

 |

| Algorithm 3: GUI |

| --- |

| 

1.  Start

2.  Import all the required packages.

3.  Create a window with the required title.

4.  Add a label asking the user to choose an audio file.

5.  Now add the button correspondingly.

6.  Define a function that takes the input file from the user and shows the English accent in that file.

7.  In the function defined, pass the input audio file to the model that is built earlier.

8.  Display the English accent to the user.

9.  Stop

 |

## VI. Result and analysis
