to come up with a prediction model capable of detecting the EEG state in Table 1.5 is discussed. In its fundamental form, this last experiment is an emulation of what would happen in a real situation and designed with a realistic point of view to make sure that the feasibility of constructing such a device with this algorithm would be preserved. In addition, the seizure prediction was empirically defined as seconds to safely provide enough preictal data for all of the seizure cases. This seizure prediction horizon was dynamically defined as each of the training sets were constructed for each case that was real time data tested. For each testing case, the training data consisted of all other seizure cases from the same patient.

All of the algorithm feature sets results described in Table 1.6 is extracted from the signals as the testing sample. Since there are feature sets that compare each of the channels to each other, the emulator is supplied data segments from all of the channels at once for each 3-second segment. The performance analysis of Hybrid Artificial Neural Network with Support Vector Machine (HANNNSVM) is compared with the existent methods. Such methods used for analysis are one-class SVM method [12], neural network [13]. The one-class SVM classifiers are then executed with the respective training and testing sets described, and their predictions are given to the decision fusion based module. The neural network algorithm

Table 1.6 Feature sets that resulted in the highest prediction accuracy for patient dataset.

| ID | HANNNSVM | SVM | Neural network |
|:---|:---|:---|:---|
| **1** | 77 | 74 | 72 |
| **2** | 69 | 66 | 63 |
| **3** | 58 | 59 | 57 |
| **4** | 77 | 74 | 71 |
| **5** | 76 | 71 | 64 |
| **6** | 81 | 76 | 71 |
| **7** | 83 | 79 | 77 |
| **8** | 79 | 71 | 69 |
| **9** | 84 | 77 | 73 |
| **10** | 81 | 78 | 77 |