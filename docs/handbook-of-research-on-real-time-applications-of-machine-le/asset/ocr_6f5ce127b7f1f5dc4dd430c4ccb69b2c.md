(Acharya et al., 2017) uses deep learning technique for automatically detection of five distinct groups of heartbeats in ECG signals. Authors used 1D ECG signals as input and designed a 9 layer 1-dimentional CNN model. Proposed approach achieved a classification accuracy of 94.03% with 109,449 beats. Model's generalisation capacity improves as they perform filtration on input signals to filter-out high-frequency noise and then used the model to identify and classify noisy and non-noisy ECG signals.

(Abayarathne et al., 2019) proposed two methods where the first method is a rule based abnormality identification which uses Hamilton-Tompkins algorithm for the calculation of R peaks which achieves 97.55% accuracy with 705,000 beats. Second method uses RNN and LSTM models and classifies 15 classes of cardiac arrhythmias with 94.7% average accuracy with 96,265 beats.

(Kommireddy et al., 2020) proposed a four layered hybrid of CNN with LSTM associated ANN with ReLU and Sigmoid operate with inside the final layer and bought accuracy of 98.64% on MIT-BIH cardiac arrhythmia dataset with 107,620 beats.

(Hasan et al., 2020) provides an methodology with a CNN of sixteen layers with SoftMax activation function withinside the very last layer that classify five arrhythmia sorts (N, F, V, Q, S) of MIT-BIH arrhythmia dataset with 98.28% mean accuracy.

(Izci et al., 2019) proposed a CNN version of 5 layers with ReLU in convolution layers and Softmax within the final layer that performed associate accuracy of 97.42% on comparable dataset with 27,789 beats.

(Ullah et al., 2020) proposed a CNN version of 10 layers which classify eight varieties of cardiac arrhythmias of MIT-BIH arrhythmia dataset with an accuracy of 99.11%.

(Oh et al., 2018) proposed a mix of CNN and LSTM layers with input as one-dimensional ECG signals. By inserting the waveforms within the processing phase, ECG data was separated into several ECG data segments of varying durations, and each data segment was likewise extended to the same length. The designed architecture classifies ECG signals into 5 categories: N (Normal), LBBB (Left Bundle Branch Block), VPC (Ventricular Premature Contraction), RBBB (Right Bundle Branch Block), and APC (Atrial Premature Contraction). The authors used 16,499 ECG beats from MIT-BIH dataset and obtained 98.10% accuracy.

(Mondéjar-Guerra et al., 2019) developed a method that incorporates a number of different types of Support Vector Machines (SVMs). The approach relies on R-R intervals, wavelets, and the HOS (Higher Order Statistics) of the ECG signal. Each sort of feature has its own SVM model (Hiran, K. K.,et.al.). Using the MIT-BIH arrhythmia dataset with 49,691 beats in total, the approach categorised four categories of normal and abnormal beats (N, F, V, and S) with 94.50% accuracy.

(Subramanian et al., 2020) proposed a SVM classifier based model to classify ECG beats with an accuracy of 91% and F1 score of 90.65% with training data and testing data for of 15 and 23 beats respectively. Two types of comparison, beat to beat and beat to bat is performed which depends on QRS variation and P Axis respectively.