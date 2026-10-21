
**TABLE 10.4** State-Channel Table

| Sl. No. | Current State | Electrode | Old Value (Time: 0.005 min) | New Value (Time: 1.005 min) | Next State |
|---|---|---|---|---|---|
| 1 | Neutral | T7 | -861 | -706 | Positive |
| 2 | Neutral | FP1 | -840 | -657 | Negative |
| 3 | Neutral | F3 | -628 | -851 | Depressed |
| 4 | Neutral | PO7 | 193 | 202 | Harmony |
| 5 | Negative | F3 | 147 | 319 | Positive |
| 6 | Positive | F4 | 246 | 412 | Negative |
| 7 | Neutral | F7 | 298 | 197 | Depressed |
| 8 | Neutral | PO7 | 202 | 193 | Harmony |
| 9 | Neutral | T8 | 378 | 653 | Positive |
| 10 | Neutral | FP2 | 103 | 263 | Negative |
| 11 | Negative | F7 | -177 | -113 | Positive |
| 12 | Positive | F8 | 600 | 717 | Negative |
| 13 | Positive | (F4, F8) | {511, 471} | {356, 128} | Positive |
| 14 | Negative | (F3, F7) | {319, 424} | {105, 295} | Negative |
| 15 | Neutral | T7 | 175 | 102 | Neutral |

![](img/5025594f89449de2a74e5b325b1e84ef_258_0.png)

Σ = T7  
Γ_old = T7.oldvalue(-861.501)  
Γ_new = T7.newvalue(-706.549)  
T = time(1 min)  
Transition Function(F) = F(q1 * Σ * Γ_old * Γ_new * T) => q2  
Present State(q1) = “Neutral” and Final State (q2) = “Positive”

**FIGURE 10.9** State transition from neutral (starting) state to positive (final) state with correct inputs.

![](img/5025594f89449de2a74e5b325b1e84ef_258_1.png)

Σ = FP1  
Γ_old = FP1.oldvalue(-840.365)  
Γ_new = FP1.newvalue(-657.527)  
T = time(1 min)  
Transition Function(F) = F(q1 * Σ * Γ_old * Γ_new * T) => q2  
Present State(q1) = “Neutral” and Final State (q2) = “Negative”

**FIGURE 10.10** State transition from neutral (starting) state to negative (final) state with correct inputs.

![](img/5025594f89449de2a74e5b325b1e84ef_259_0.png)

Σ = F3  
Γ_old = F3.oldvalue(-628.257)  
Γ_new = F3.newvalue(-851.477)  
T = time(1 min)  
Transition Function(F) = F(q1 * Σ * Γ_old * Γ_new * T) => q2  
Present State(q1) = “Neutral” and Final State (q2) = “Depressed”

**FIGURE 10.11** State transition from neutral (starting) state to depressed (final) state with correct inputs.

![](img/5025594f89449de2a74e5b325b1e84ef_259_1.png)

Σ = PO7  
Γ_old = PO7.oldvalue(193)  
Γ_new = PO7.newvalue(202)  
T = time(1 min)  
Transition Function(F) = F(q1 * Σ * Γ_old * Γ_new * T) => q2  
Present State(q1) = “Neutral” and Final State (q2) = “Harmony”

**FIGURE 10.12** State transition from neutral (starting) state to harmony (final) state with correct inputs.

![](img/5025594f89449de2a74e5b325b1e84ef_259_2.png)

Σ = T7  
Γ_old = T7.oldvalue(-861.501)  
Γ_new = T7.newvalue(-706.549)  
T = time(1 min)  
Transition Function(F) = F(q1 * Σ * Γ_old * Γ_new * T) => q2  
Present State(q1) = “Neutral” and Final State (q2) = “No Final State”

**FIGURE 10.13** State transition from neutral (starting) state to the same state with wrong inputs.

We execute our transition function algorithm. The next-state function of the finite machine is verified using the prediction of the classification algorithm. We describe the state-channel table using both initial and final values of the machine in Table 10.4 and illustrate the process of state transition in Figures 10.9–10.13. The state-transition machine (M) is described using a six-tuple mentioned in the proposed work section.

```
M = [Q, Σ, Γ_old, Γ_new, F, T]
```

In Figures 10.9–10.13, we have shown how the different emotional states are classified based on different electrode values discussed in Table 10.4. From Table 10.4, we can conclude that increased value of channel (PO7) placed over parietooccipital area leads to harmony emotions from the neutral state. Harmony emotions have a high correlation in alpha band power over the parietooccipital area [27]. A depressed subject has less activation in the left frontal area than the normal subject [28]. An increase in the value of the frontopolar area leads to negative emotions (anger, fear, sad, etc.). The EEG activity in the frontal area and frontopolar cortex is strongly correlated to adjust emotion regulation [29]. Hence, negative emotions and depressed states are highly correlated. An increase in the value of channels placed over a temporal area leads to positive emotions. In paper [30], the author describes that stable patterns of positive emotions exhibited due to an increased value of lateral temporal area for beta and gamma bands and stable pattern of higher gamma response in frontocortex leads to negative emotions. The state-transition diagram has been drawn using “JFLAP” software [31]. From Figures 10.9, 10.10, and 10.12, we have observed that the subject’s emotion has changed from neutral to positive, negative and harmony states due to the increased value of specific channels, but the emotion of the subject has changed to a depressed state due to the decreased value of channel, as shown in Figure 10.11. All the inputs are taken from Table 10.4. Here we assume that, initially, all the subjects are in “Neutral” state, so we consider “Neutral” state as a starting state in our machine. Though we have captured the brain signal through various channels, the machine moves to only one destination state at a fixed time interval after taking the user inputs, so we only consider one specific channel value (T7/FP1/F3/PO7, etc.) as input at a fixed time interval. For wrong inputs (T7.oldvalue and T7.newvalue), machine does not move to the final emotional state (positive), but it only loops back within the same starting state (Figure 10.13). In Figure 10.14, we have plotted the state transition based on the changed value of different electrodes, and increased channel value of FP1, T8, and PO7 indicate negative, positive, and harmony emotions, respectively, whereas decreased channel value of F3 indicates a depressed state.

![](img/5025594f89449de2a74e5b325b1e84ef_260_0.png)

Neutral state (starting state in emotional state-transition machine) of the machine shows no change in the channel’s value. Figure 10.15 (3D plot) describes the different emotional states based on the corresponding electrodes with their amplitude/channel value.

![](img/5025594f89449de2a74e5b325b1e84ef_261_0.png)

**FIGURE 10.15** 3D plotting of emotions and corresponding electrodes with the amplitude value of those electrodes.

## 10.4.5 COMPARISON WITH PREVIOUS WORKS

In Figure 10.16, we have made a comparison of our proposed work with other models (in Table 10.5) based on the accuracy factor and showed that our work stands apart from all other previous works. The model referred by [20] has an accuracy of 82% for four emotions, more than the model referred by [28], but the number of emotions recognized by our model is four, which is greater than that of [28]. So, considering all the parameters, we can conclude that our proposed classification work stands apart from the other models of emotion detection.

![](img/5025594f89449de2a74e5b325b1e84ef_261_1.png)

**FIGURE 10.16** Accuracy comparison of the proposed approach with some popular approaches.

**TABLE 10.5** Comparison of Proposed Model with Other Popular Models

| Study | Number of Electrodes | Sampling Frequency (Hz) | Classifier | Number of Emotions | Stimuli | Accuracy |
|---|---|---|---|---|---|---|
| Proposed | 13 | 512 | SVM | 4 | Video | 90 |
| Wang et al., 2014 | 128 | 200 | SVM | 3 | Music, video | 90 |
| Bastos-Filho et al., 2012 | 32 | 256 | kNN | 2 | Video | 69.5 |
| D. Chakladar, S. Chakrobarty | 4 | 512 | LDA | 4 | Video | 82 |
| Chanel et al., 2011 | 19 | 256 | LDA | 3 | Video, games | 63 |

## 10.4.6 COMPUTATIONAL COMPLEXITY

In case of classification, training of dataset using SVM will execute with time complexity, which depends on both training set and support vectors, and can be bounded by a function n³ approximately, hence, O(n³). For state-transition process, the algorithm will run with linear time complexity O(n), for n input size, each input takes a constant time for execution.

## 10.5 CONCLUSION

In this chapter, we have done a comprehensive survey of various classification methods used in BCI research as well as investigated different emotional states of humans. SVM, KNN, and random forest are the techniques that we have been specifically interested in and worked on. The classification accuracy has been computed using the confusion matrix and different statistical parameters (sensitivity, specificity, prevalence, and precision). After comparing with other well-known models, we can conclude that our proposed model outperforms others. The classification process for a large number of nonlinear data using different SVM kernels and features shows that the efficient kernel for emotion classification is the polynomial kernel. After achieving 90% accuracy in classification, we use the state-transition model for different emotional states. For performance analysis of the classifier, we have used a confusion matrix, and based on different parameters (sensitivity, specificity, prevalence, precision), we measure the accuracy and prediction of the classification.
