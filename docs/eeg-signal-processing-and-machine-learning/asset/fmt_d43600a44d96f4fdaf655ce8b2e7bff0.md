
## 神经网络映射头皮 EEG 到颅内 EEG

To achieve this, the neural network in [Figure 11.22](#c11.xhtml#c11-fig-0022) is used. The network comprises of a fully connected network with different numbers of inputs and outputs in the left and an autoencoder (AE) in the right. During the training the scalp EEG segments are applied to the left and the corresponding segments of intracranial signals (iEEG) to the right. The middle layer then learns how to map the scalp data (in the left) to the patterns similar to the iEEGs in the right. The fundamental idea behind this design is that a new scalp EEG test pattern is first projected (mapped) to the iEEG domain and then classified. [Figure 11.23](#c11.xhtml#c11-fig-0023) represents the concept.

Statistical tests and qualitative analysis have revealed that the generated pseudo‐intracranial data are highly correlated with the true intracranial data. This facilitated the detection of IEDs in scalp recordings where such waveforms are not easily visible. The IED detection accuracy of above 70% for over 80% of the subjects has been achieved. [Figure 11.24](#c11.xhtml#c11-fig-0024) shows how accurately the intracranial waveforms can be learned from the scalp EEGs.

As a real‐world clinical application, these pseudo‐iEEG are then used by a CNN for the automated classification of IED and non‐IED waveforms. This circumvents the unavailability of iEEG and the limitations of scalp EEG in IED visualization.

In another attempt by the same research group a CNN has been designed to perform feature learning and detect the IEDs [\[130\]](#c11.xhtml#c11-bib-0130). The CNNs are trained in a subject independent fashion to demonstrate how meaningful features are automatically learned in a hierarchical process. They illustrate how the convolved filters in the deepest layers provide insight towards the different types of IEDs within the group, as confirmed by expert clinicians. The IED morphologies found in the filters can help evaluate the treatment of a patient. To improve the learning of the deep model, moderately different score classes are utilized as opposed to binary IED and non‐IED labels. The resulting model achieves state of the art classification performance and is also invariant to time differences between the IEDs. This study suggests that deep learning is suitable for automatic feature generation from iEEG data, while also providing insight into the data.

### Figure 11.21

![Figure 11.21 Examples of single‐channel reconstructed intracranial signals for four different subjects. Averaging the obtained time courses over trials we get waveforms for the true test signal, the CDLSA method, the method in \[128\] and the DLSA+C method.](images/c11f021.gif)

[**Figure 11.21**](#c11.xhtml#R_c11-fig-0021) Examples of single‐channel reconstructed intracranial signals for four different subjects. Averaging the obtained time courses over trials we get waveforms for the true test signal, the CDLSA method, the method in [\[128\]](#c11.xhtml#c11-bib-0128) and the DLSA+C method.

### Figure 11.22

![Figure 11.22 Topology of the DNN for mapping scalp to iEEGs. X is the scalp EEG, y 1 is the hidden layer of the asymmetric fully connected network in the left, z 1; z 2 are the estimated sources of iEEG, y 2 is the hidden layer of the AE, We , and Wd are the weights of the AE and W are the tied weights of the AE.](images/c11f022.gif)

[**Figure 11.22**](#c11.xhtml#R_c11-fig-0022) Topology of the DNN for mapping scalp to iEEGs. **X** is the scalp EEG, **y** [1] is the hidden layer of the asymmetric fully connected network in the left, **z** [1]; **z** [2] are the estimated sources of iEEG, **y** [2] is the hidden layer of the AE, **W**^(*e*) , and **W**^(*d*) are the weights of the AE and **W** are the tied weights of the AE.

### Figure 11.23

![Figure 11.23 A schematic comparison between the proposed method (left) and an ensemble model (right). In this scenario, consider X2 to be more similar to X3 than X1. On the right side, both X1 and X2 are used to train the classifiers in order to predict X3. Whereas, the left model only uses the estimator trained with X2 to generate the unknown signal S3. This estimation (S23) is used to predict the classes of Y3.](images/c11f023.gif)

[**Figure 11.23**](#c11.xhtml#R_c11-fig-0023) A schematic comparison between the proposed method (left) and an ensemble model (right). In this scenario, consider X2 to be more similar to X3 than X1. On the right side, both X1 and X2 are used to train the classifiers in order to predict X3. Whereas, the left model only uses the estimator trained with X2 to generate the unknown signal S3. This estimation (S23) is used to predict the classes of Y3.

### Figure 11.24

![Figure 11.24 Estimation of iEEG for two IED segments and a non‐IED segment (averaged over all channels) using the fully connected DNN only and the DNN‐AE. In the latter case the additional symmetric layer led to a smoother estimation of the intracranial data.](images/c11f024.gif)

[**Figure 11.24**](#c11.xhtml#R_c11-fig-0024) Estimation of iEEG for two IED segments and a non‐IED segment (averaged over all channels) using the fully connected DNN only and the DNN‐AE. In the latter case the additional symmetric layer led to a smoother estimation of the intracranial data.

## 11.7 Fusion of EEG–fMRI Data for Seizure Prediction

Clinical MRI has been of primary importance for visualization/detection of brain tumours, stroke, and multiple sclerosis. In 1990, Ogawa [\[131\]](#c11.xhtml#c11-bib-0131) showed that MRI can be sensitized to cerebral oxygenation, using deoxyhaemoglobin as an endogenous susceptibility contrast agent. Using gradient‐echo imaging, a form of MRI image encoding sensitive to local inhomogeneity of the static magnetic field, he demonstrated (for an animal) that the appearance of the blood vessels of the brain changed with blood oxygenation. In some later papers published by his group they presented the detection of human brain activations using this BOLD \[[132](#c11.xhtml#c11-bib-0132), [133](#c11.xhtml#c11-bib-0133)\] by performing so‐called fMRI. Now, it is established that by an increase in neuronal activity, local blood flow increases. The increase in perfusion, in excess of that needed to support the increased oxygen consumption due to neuronal activation, results in a local decrease in the concentration of deoxyhaemoglobin. Since deoxyhaemoglobin is paramagnetic, a reduction in its concentration results in an increase in the homogeneity of the static magnetic field, which yields an increase in the gradient‐echo MRI signal. Although the BOLD fMRI does not measure brain activity directly, it relies on neurovascular coupling to encode the information about the brain function into detectible hemodynamic signals. It will clearly be useful to exploit this information in localization of seizure during the ictal period.

As will be stated in [Chapter 10](#c10.xhtml), brain sources can be localized within the brain. The seizure signals however, are primarily not known either in time or in space. Therefore, if the onset of seizure is detected within one ictal period, the location of the source may be estimated and the source which originates from that location tracked. Using fMRI it is easy to detect the BOLD regions corresponding to the seizure sources. Therefore, in separation of the sources using BSS, it can be established that the source signals originated from those regions which represent seizure signals. This process can be repeated for all the estimated source segments and thereby the permutation problem can be solved and the continuity of the signals maintained.
