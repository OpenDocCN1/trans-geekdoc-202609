Table 1. Summary of the start-of-the-art works for human emotion recognition using physiological signals.

| Paper | Classifier | Features | Signals |
| --- | --- | --- | --- |
| [25] | SVM | Statistical Features | Facial electromyogram, electrocardiogram, respiration, and electroermal activity |
| [27] | Genetic algorithm and K-NN | Statistical features | EDA |
| [25] | Neuro-fuzzy inference | Statistical Features | Facial electromyogram, electrocardiogram, respiration, and electroermal activity |
| [18] | K-NN | Statistical features | EDA |
| [28] | SVM | Wrapper feature selection (WFS) | EDA |
| [29] | CNN | Raw data | Patient's movements XYZ + EDA |
| [22] | Deep learning (CNN+RNN) | Raw data | AVEC 2016 |
| [26] | ESN-CNN | Statistical features | ECG (Electrocardiogram), EDA (Electrode activity) and ST (Skin Temperature) |
| [30] | Dynamic calibration + K-NN | Statistical features | EDA |

SVM: Support Vector Machine, K-NN: KNearest Neighbor, CNN: Convolutional Neural Network, RNN: Recurrent Neural Network, ESN-CNN: Echo State Network - Cellular Neural Network.

# ## 3. Datasets

This study uses public datasets (MAHOB and DEAP) of physiological signals to test our proposal for a robust emotion recognition system. However, for both the EDA related data will be used in the experiments for this paper.



The dataset is called MAHOB and was collected by Soleymani Mohammad et al. [31]. The data is related to different physiological signals.

The data was collected from 30 healthy young adults who participated in the study. 17 of the participants were female and 13 of them were male. Their age varied from 19 to 40. The participants were 20 emotional video clips which were evaluated in terms of both valence and arousal using the Self-Assessment Manikins (SAM) questionnaire [32]. SAM is a prominent tool that visualizes the degree of valence and arousal by manikins. The participants distinguished a scale from 1 to 9, see Figure 1.

![](bbox=[0.235, 0.55, 0.755, 0.768])

**Figure 1.** Self-assessment manikins scales for valence (above) and arousal (below) [32].

In the experiments for MAHOB, electroencephalogram (EEG), blood volume pulse (BVP), respiration pattern, skin temperature, electromyogram (EMG), electrocogram (EOG), electrocardiogram (ECG), and EDA of 30 participants were collected.



DEAP [33] is a multimodal dataset used to analyze human emotional states.