
## Table 1.4 EEG signal seizures proposed HANNSVM system result. (Continued)

| Objectives | Results |
| :--- | :--- |
| Apply fast Fourier transform | |
| Apply HANNNSVM algorithm | Brain Waves: EEG Tracings |
| - classification | Beta (β) 13-30 Hz |
| | Alpha (α) 8-13 Hz |
| | Theta (θ) 4-8 Hz |
| | Delta (δ) 0.5-4 Hz |
| | 4 |
| | 3 |
| | 2 |
| | 1 |
| | Time (Secs.) |
| | 0 |

A number of states based on the predictions of HANNSVM classification algorithms [35–37]. This initial testing was done using the EEG data provided by the Stanford University Kaggle dataset. All subsequent experiments use the data provided by the Freiburg Seizure Prediction Project. This was done because it was easier to assess the accuracy of the system using several cases of seizure from the same patient. The second phase experiment focused on determining a feasible duration of the preictal state that best expose EEG characteristics that lead up to the ictal state.

In this experiment, training and testing data are unrelated and from different seizure cases, but all recorded and find the optimal feature sets that maximize the accuracy of the prediction. These experiments show the relative strength of each of the classification algorithms and also approximate the behavior of the state transitions [38, 39]. Tonic-clonic seizure activity is generally easy to see visually in an EEG as the amplitudes of the signal start to peak and a different set of frequencies are prevalent [40–42]. This served as an easy indicator of the workings of the seizure predictions system. Since there is no gold standard number of unique states to distinguish between in ictal pattern recognition, an initial guess of 5 states were defined in Table 1.5. This guess was made by visually determining sections of EEG signal that were most unique [43]. To keep any confounding variables constant, the training and testing data used were taken from the same seizure case where 80% was used as training, and 20% was used as testing (random new permutations for every classification) [44–46]. The distinction made between the Seizure Onset Period and the Preictal Period was done to determine if there was a more gradual transition between the preictal and ictal seizure states [47–49].

The results of this experiment were able to show the efficacy of the state decision neurons for making state transitions and the decision fusion which was used to improve the classification [50–53]. Also, a module was created to segment the multichannel EEG signal, apply a window function, and pass it on to the system at the appropriate time intervals. This made it possible to

### Table 1.5 Initially defined epileptic states.

| State | Epileptic state |
| :--- | :--- |
| 1 | Normal, calm |
| 2 | Seizure onset period |
| 3 | Preictal |
| 4 | Medium seizure state |
| 5 | Full seizure state |

![](img/bb4a43d3cc1537c84f048d14c493ee68_44_0.png)

**Figure 1.9** Graph between TPR vs TFR.

emulate a more realistic scenario. As a sub-study, the stepwise feature optimization algorithm is used in this experiment to determine the feature sets that result in the highest accuracy predicting the preictal state. Within the 100 s prior to seizure onset, time frame was given to localize the preictal state to a region of time that was not unreasonably short or long, but just enough for seizure intervention methods to be successfully executed [54–56].

For this and all subsequent experiments, the data provided by the Seizure Prediction Project in Stanford University is used for testing. In this experiment, the training and testing data were partitioned from the same dataset; 80% was used as training data and 20% was used as testing data. The states were redefined as seen in Table 1.5 for this, and all subsequent experiments.

The epileptic state definitions for all the EEG streams (specifically, States 1, 2, and 4) were defined by the respective researchers who provided the data for this research. State 3, or the preictal state, was initially defined to be one second before State 4. In this experiment, the duration of the preictal state was iteratively increased to 100 s, and a series of classifications were done at each step for each brain wave [57, 58]. The best features for each iteration were saved. This gave an estimate as to how long a feasible preictal state (one that could be predicted) would be for each of the patients, and for each type of epilepsy [59]. Figure 1.9 displays the EEG seizure features prediction for True positive rate vs false positive rate (receiver operating characteristic curve).

### 1.5.2 Discussion

Using the knowledge gained from the previous experiments, a balance of all the algorithms features and other parameters were combined in order to come up with a prediction model capable of detecting the EEG state in Table 1.5 is discussed. In its fundamental form, this last experiment is an emulation of what would happen in a real situation and designed with a realistic point of view to make sure that the feasibility of constructing such a device with this algorithm would be preserved. In addition, the seizure prediction was empirically defined as seconds to safely provide enough preictal data for all of the seizure cases. This seizure prediction horizon was dynamically defined as each of the training sets were constructed for each case that was real time data tested. For each testing case, the training data consisted of all other seizure cases from the same patient.

All of the algorithm feature sets results described in Table 1.6 is extracted from the signals as the testing sample. Since there are feature sets that compare each of the channels to each other, the emulator is supplied data segments from all of the channels at once for each 3-second segment. The performance analysis of Hybrid Artificial Neural Network with Support Vector Machine (HANNNSVM) is compared with the existent methods. Such methods used for analysis are one-class SVM method [12], neural network [13]. The one-class SVM classifiers are then executed with the respective training and testing sets described, and their predictions are given to the decision fusion based module. The neural network algorithm

### Table 1.6 Feature sets that resulted in the highest prediction accuracy for patient dataset.

| ID | HANNNSVM | SVM | Neural network |
| :--- | :--- | :--- | :--- |
| 1 | 77 | 74 | 72 |
| 2 | 69 | 66 | 63 |
| 3 | 58 | 59 | 57 |
| 4 | 77 | 74 | 71 |
| 5 | 76 | 71 | 64 |
| 6 | 81 | 76 | 71 |
| 7 | 83 | 79 | 77 |
| 8 | 79 | 71 | 69 |
| 9 | 84 | 77 | 73 |
| 10 | 81 | 78 | 77 |

reduction of a new permutation of the training data is done where the training data used is a combination of all the seizure cases from the same patient except for the case being used as testing. neural network algorithm is also applied to the testing sample using the same parameters so that the testing data is properly scaled with the training data. The parameters used for performance analysis are classification accuracy and running time. Accuracy is measured where is perfectly identified count of true positive records and is the absolute count of positive records for infected person category. The combination average value of NIMH patients' data and MIT-CHB patient data average values are shown in Table 1.6 and Figure 1.10. The performance analysis in Table 1.6 exhibits the enhanced accuracy based on patient EEG features of Hybrid Artificial Neural Network with Support Vector Machine (HANNNSVM) over other existent methods. The pictorial representation of performance analysis is shown in Figure 1.10.

The combination average value of NIMH type of epilepsy data and MIT-CHB type of epilepsy data average and calculate the total averages. The performance analysis in Table 1.7 exhibits the type of epilepsy based accuracy values of Hybrid Artificial Neural Network with Support Vector Machine (HANNNSVM) over other existent methods. The pictorial representation of performance analysis is shown in Figure 1.11.

The research has been tested perfectly and successful results are achieved. These results are successfully uploaded to the cloud using Raspberry Pi. Protocols like SPI have been understood and verified its functionality with

![](img/bb4a43d3cc1537c84f048d14c493ee68_46_0.png)

**Figure 1.10** Output result accuracy predictions for based on patient EEG data.
