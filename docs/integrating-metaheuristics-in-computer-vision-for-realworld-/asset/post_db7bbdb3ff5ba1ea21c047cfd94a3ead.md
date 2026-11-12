
In the unidirectional model since the model was not able to go back and adjust the weights from the future the model was less accurate and also consumed a lot of time. But in the bidirectional approach, we simply took the processed data from the model at the output level and then as there is a threshold for results it recalculates at each level of the model, this produces an output which is far more accurate and better than the before results. Additionally, the entire model will consist of some of the classification techniques which would be useful of the different classification of heart arrhythmia types, the different types of possible heart irregular rhythms or arrhythmias are separated into two classes, tachycardia and bradycardia, tachycardia is termed as fast heartbeat than the regular and bradycardia is termed as slower than usual heartbeat [3-5].

## Tachycardia:

There are several types of tachycardia, which are as follows:

- 1) Atrial fibrillation: everything with atrial in it is related to a stroke and if left untreated it might cause some serious issues, it may be temporary most of the times but there are cases where it becomes chronic. It results in uncoordinated and unorganized heart rate.
- 2) Atrial flutter: as this contains the word Atrial in it, it is also related to stroke but as compared with atrial fibrillation it is more organized and coordinated.
- 3) Supraventricular tachycardia: As the name suggests it begins at the lower chamber of the heart where there are ventricles, unlike atrial which is upper chamber, this tachycardia begins and ends randomly based on the medical condition of the patient.
- 4) Ventricular fibrillation: it occurs when a sudden change in the environment is noticed, usually it is due to any electrical impulse and it can disrupt the normal rhythm massively, if left untreated it can result in death of a person in minutes.
- 5) Ventricular tachycardia: It is a medical condition where the ventricles are not fully filled with blood but the heart continues to beat early than expected which results in rhythm impairment, if not treated early this condition can be deadly.

## Bradycardia:

There are several types of bradycardias, two of which are-

- 1) Sick sinus syndrome: There is a sinus node in the heart which is responsible for the rhythm of the heart, any damage in the form of trauma or tear in the sinus node can cause the heart to beat irregularly which can be in the form of too fast (tachycardia) or too slow (bradycardia). The sick sinus syndrome is usually resulted due to a trauma and hence it is known to block or boost the blood flow and hence messing up the rhythm. It might be also caused due to old age.
- 2) Conduction block: this is the simple block which can be caused by many reasons, due to the blockage in the electrical impulse the heart cannot beat properly, although this can happen any time and the person might not even notice it as it might just feel like a skipped heartbeat.

The aim of the model is to target research groups who want to analyze the different conditions and their association with age and gender of a particular patient.

The model will have two parts:

- 1) The first part of the model will deal with real-time ECG data and detect the irregular heartbeats.
- 2) The second part of the model will then further take into account the different factors like age, gender, weight and height and will aim to identify the further underlying conditions [6, 7].

## 14.2 About the Dataset

This dataset is composed of two collections of heartbeat signals derived from two famous datasets in heartbeat classification, the MIT-BIH arrhythmia dataset [15] and The PTB diagnostic ECG database [16]. The number of samples in both collections is large enough for training a deep neural network.

The dataset considered for this case is cardiac arrhythmia database. The dataset consists of 549 instances and 290 associated subjects. The dataset classifies 16 different heart conditions ranging from premature contraction to blockage which are directly associated with heart arrhythmia. The dataset also consists of information regarding the gender of the patient along with other personal details like weight, height, age, etc. As shown in Figure 14.1 percentage of different beats present in the dataset.

This dataset has been used in exploring heartbeat classification using deep neural network architectures, and observing some of the capabilities of transfer learning on it. The signals

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_259_0.png)

Figure 14.1 Percentage of different beats present in the dataset.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_260_0.png)

Figure 14.2 Percentage of different beats after up-sampling and equalizing the number of samples for each class.

correspond to electrocardiogram (ECG) shapes of heartbeats for the normal case and the cases affected by different arrhythmias and myocardial infarction. These signals are pre-processed and segmented, with each segment corresponding to a heartbeat as shown in Figure 14.2 percentage of different beats after up-sampling and equalizing the number of samples for each class [8-12].

The dataset is in the form of .csv files, and contains data from two datasets - MIT-BIH arrhythmia dataset and The PTB diagnostic ECG database.

The MIT-BIH arrhythmia dataset has 109,500 samples with five categories/classes. These classes are “N”: 0, “S”: 1, “V”: 2, “F”: 3, “Q”: 4 and these stand for-

- 0: "normal beat,"
- 1: "supraventricular premature beat" 2: "premature ventricular contraction,"
- 3: "fusion beats,"
- 4: "unclassifiable/unknown beats."

The PTB diagnostic ECG database contains around 14,500 samples and two categories/classes. This dataset contains information related to height, weight, gender, and age of patients [13, 14].

## 14.3 Flow of the Model

The new and updated model begins with some of the new libraries which were required for the new model, those were, standard scaler from sklearn, preprocessing, and many more from the TensorFlow library which were to support with the confusion matrix and also some of them to support the deep learning model. The dataset used has been explained to the above piece of information to its core details.

The dataset was accessed and then some data exploration was done in the form of splitting, checking the data for errors, checking it for the structure and format, some of the classes were formed which were: normal beat, supraventricular premature beat, premature ventricular contraction, fusion of ventricular and normal beat, unclassified beat and atrial premature. The data visualization was done to check for the possible graphs which would give a vague idea on the actual rhythms of the heartbeat from the ECG records, after all this visualization, it was time for the visualization of the percentage of the irregularities in rhythm of the heartbeat in the records.

Now the idea of the processed dataset was clear and then the individual extraction of class of arrhythmia from each record has to be done, this will give rise to the need of some more data preprocessing which would upsample the class with least records and then equalize the number of records in each class individually and then combine them later through different query. The resulting visualization had some stable results than earlier as the classes were equalized for their combined results. The next step involved in normalizing the training, validation and testing data; reshaping the DataFrame into a 3D numpy array and then with the receiving output, converting it into a categorical array. The similar LSTM bidirectional Sequential model was built which was of 19 layers of processing including the input, as well as the output layer. As shown in Figure 14.3 visualization of first 10 samples in the dataset. To take care of the power failure or any other obstacles that would occur while running the model, there was a checkpoint made, which would make sure that the progress is saved, so even if any interruption is at 99% progress, the next time it resumes, the point

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_261_0.png)

Figure 14.3 Visualization of first 10 samples in the dataset.
