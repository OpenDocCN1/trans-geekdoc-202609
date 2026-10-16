
We considered the SuriNet architecture for visualizing the learned features. Figures [12.20](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12fig20) and [12.21](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12fig21) represent the extracted features from the control and COVID-19 images. Magenta represents the filter and yellow represents the learned feature. Figures [12.20](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12fig20) and [12.21](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12fig21) show that 256 filters output in a 16 × 16 grid at the eleventh layer and 128 filters in an 8 × 16 grid at the sixteenth layer (before the vectorization) in SuriNet. The grid of the filter output contains mixing of yellow and magenta. Some filter output shows that they are considering the background information of the images. For example, in figure [12.20](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12fig20), the seventh output in the first row shows that the learned region (yellow) is background, similar to the output; we can see a few places like this in figures [12.20](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12fig20) and [12.21](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12fig21). Similarly, the essential features are extracted from the lung CT scans, which will be seen in the dark yellow color inside the lung region, i.e. in figure [12.20](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12fig20) the fourth filter output in row one. These kinds of outputs from the filters are more common in the COVID-19 class than the control class. Visually it is represents that the features extracted for COVID-19 are greater than for the control. The quantification of these features is represented by the MFS.

![Figure 12.20. Sample of control class visualization of SuriNet.](images/bk978-0-7503-2244-7ch12f20_online.jpg)

**Figure 12.20.** Sample of control class visualization of SuriNet.

![Figure 12.21. Sample of COVID-19 class visualization of SuriNet.](images/bk978-0-7503-2244-7ch12f21_online.jpg)

**Figure 12.21.** Sample of COVID-19 class visualization of SuriNet.

### 12.5 Discussion

*Benchmarking*

We compared our proposed AI models to existing works. Table [12.7](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12t7) presents the existing work on COVID-19 using AI models. Column 3 represents the dataset used in the study, and column 4 presents the model used. Columns 5 and 6 provide the accuracy achieved and the performance metrics. Polsinelli *et al* \[[39](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib39)\] proposed the SqueezeNet architecture to classify 360 CT scans in pneumonia and healthy and achieved an accuracy of 0.83 and sensitivity of 0.85. Hasan *et al* \[[40](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib40)\] used a histogram threshold to isolate the background of the CT scans and then extracted features using a Q-deformed entropy algorithm. The extracted features are fed to the long short-term memory (LSTM) neural networks for classifying pneumonia versus health. The authors achieved an accuracy of 99.68%. Ahuja *et al* \[[21](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib21)\] proposed a TL-based ResNet18, 50, 101, and SqueezeNet classifier for classifying the 349 CT scans decomposed into three-level stationary wavelet transformation. Among all the classifiers, ResNet18 achieved an accuracy of 0.99. Singh *et al* \[[41](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib41)\] studied the effect of COVID-19 on the comorbid disease diabetes. The authors used 344 COVID-19 affected CT scans and 358 non-COVID-19 affected CT scans to extract features and fed these to the bagging ensemble for classifying COVID-19 versus non-COVID-19 scans, achieving an accuracy of 0.957 with an AUC of 0.958. Purohit *et al* \[[42](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib42)\] proposed a CNN using the multi-image augmentation technique and classifying COVID-19 versus non-COVID-19 CT scans. The authors achieved an accuracy of 0.95 and a sensitivity of 94.78%. Agarwal *et al* \[[31](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib31)\] proposed nine kinds of classifiers (ANN, DT, RF, CNN, VGG16, Denesenet121, DenseNet169, DenseNet201, and MobileNet) to classify the CT scans into control versus COVID-19 using a novel block imaging technique. The authors achieved an accuracy of 0.994 from both the DCNN and RF. Saba *et al* \[[30](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib30)\] proposed six AI models for classifying the COVID-19 versus control class using 130 CT lung scans. The authors characterized the COVID-19 lungs using a bispectrum. They achieved an accuracy of 0.996 using an improved CNN (modified sigmoid function) classifier.

**Table 12.7.** Benchmarking table.

| Authors || Dataset || Model || Accuracy || Performance |
| --- | --- | --- | --- | --- |
| Polsinelli *et al* (2020) \[[39](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib39)\] || 757 CT scans (COVID-19: 360, pneumonia: 397 || SqueezeNet || 0.83 || F1 score: 0.8333 |
| Hasan *et al* (2020) \[[40](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib40)\] || 321 chest CT scans (COVID-19: 118, pneumonia: 96, healthy: 107) || LSTM || 1.00 || — |
| Ahuja *et al* (2020) \[[21](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib21)\] || 728 lung CT scans (COVID-19: 349, non-COVID-19: 397) || ResNet18 || 0.99 || — |
| Singh *et al* (2020) \[[41](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib41)\] || 702 lung CT scans (COVID-19: 344, non-COVID-19: 358) || Bagging ensemble with SVM || 0.957 || AUC: 0.958, F1 score: 95.3% |
| Purohit *et al* (2020) \[[42](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib42)\] || 690 lung CT scans (COVID-19: 345, non-COVID-19: 345) || Proposed CNN || 0.95 || Sensitivity of 94.78% and specificity of 95.98% |
| Agarwal *et al* (2021) \[[31](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib31)\] || 60 Italian patients’ lung CT scans (control: 30, COVID-19: 30) || CNN, RF || 0.994, 0.994 || 0.991, 0.998 (*p* < 0.0001) |
| Saba *et al* (2021) \[[30](#Chapter_12.xhtml#bk978-0-7503-2244-7ch12bib30)\] || 60 Italian patients’ lung CT scans (non-COVID-19: 30, COVID-19: 100) || iCNN || 0.996 || 0.99 (*p* < 0.0001) |
| **Proposed study** || **5600 cohort (2800 control, 2800 COVID-19)** || **DenseNet121** || **89.75** || **0.902 AUC (*p* < 0.0001)** |

*Strengths, weaknesses, and extensions*

We characterized the COVID-19 tissue using AI based MFS and signal processing based bispectrum. We achieved the best accuracy of 89.75% ± 5.85% using DenseNet121. We compared the efficiency of the TL model with the novel DL architecture SuriNet. The main weakness of this study is that the number of samples required for efficient DL classifiers should be greater. We have moderate samples in our cohort, so we augmented it. The extensive dataset on COVID-19 helps the model to understand more complex patterns and efficiently classify the COVID-19 CT scans. The hybrid DL models are efficient for understanding more complex patterns in the cohort. Big Data with the hybrid model will bring more insight into the detection of COVID-19 from CT scans.

*Conclusion*

We classify and characterize the control versus COVID-19 CT scans successfully using TL and DL classifiers. We have the highest accuracy for DenseNet121 of 89.75% ± 5.85% with an AUC of 0.902 (*p* < 0.0001). Compared to this model, IV3 exhibits 89.54% ± 4.56% accuracy with an AUC of 0.895 *(p* < 0.0001). The DL based SuriNet exhibits a best accuracy of 85.75% ± 9.56%. Among all the combinations of K10, SuriNet shows 98.75%, the best accuracy for a few cases. The bispectrum shows that the COVID-19 mean B value is higher than the control by 2.85%, and using AI based MFS shows 25.09%.

### References

\[1\] WHO 2020 *Coronavirus Disease (COVID-19) Situation Reports* [https://who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports)
