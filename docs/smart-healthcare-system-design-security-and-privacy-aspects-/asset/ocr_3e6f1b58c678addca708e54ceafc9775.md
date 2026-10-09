![](bbox=[0.15, 0.11, 0.87, 0.35])

**Figure 1.9** Graph between TPR vs TFR.

emulate a more realistic scenario. As a sub-study, the stepwise feature optimization algorithm is used in this experiment to determine the feature sets that result in the highest accuracy predicting the preictal state. Within the 100 s prior to seizure onset, time frame was given to localize the preictal state to a region of time that was not unreasonably short or long, but just enough for seizure intervention methods to be successfully executed [54–56].

For this and all subsequent experiments, the data provided by the Seizure Prediction Project in Stanford University is used for testing. In this experiment, the training and testing data were partitioned from the same dataset; 80% was used as training data and 20% was used as testing data. The states were redefined as seen in Table 1.5 for this, and all subsequent experiments.

The epileptic state definitions for all the EEG streams (specifically, States 1, 2, and 4) were defined by the respective researchers who provided the data for this research. State 3, or the preictal state, was initially defined to be one second before State 4. In this experiment, the duration of the preictal state was iteratively increased to 100 s, and a series of classifications were done at each step for each brain wave [57, 58]. The best features for each iteration were saved. This gave an estimate as to how long a feasible preictal state (one that could be predicted) would be for each of the patients, and for each type of epilepsy [59]. Figure 1.9 displays the EEG seizure features prediction for True positive rate vs false positive rate (receiver operating characteristic curve).

# 1.5.2	Discussion

Using the knowledge gained from the previous experiments, a balance of all the algorithms features and other parameters were combined in order