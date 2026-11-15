Additionally, techniques for hyperparameter optimization have been applied to fine-tune the hyperparameters of the methods. These hyperparameter values are adjusted during the training phase to maximize the accuracy of the ML method. The hyperparameters subjected to optimization encompass variables such as apprentices, neighbors, distance metric, distance weight, kernel, box constraint level, and multiclass method, each tailored to the specific requirements of the method in use. Bayesian optimization was chosen as the technique to enhance the performance of the various methods by optimizing the selection of diverse hyperparameters. Recall value and AUC were utilized as performance metrics. The entire study was iterated 100 times to obtain mean values and standard deviations for the process. Importantly, it should be emphasized that data used in each iteration were randomized, mitigating noise in the samples and ensuring the acquisition of results with statistically valid values [29].

# 2.3. Performance Evaluation

For this study, the most well-known metrics in artificial intelligence were implemented to test the performance of the methods [29]: balanced accuracy (BA), recall, precision, specificity (SP), degenerated Younden's index (DYI) [29], receiver operating characteristic (ROC) and area under the curve (AUC). The F1 score is established as:

$$F_{1score} = 2\frac{Precision \cdot Recall}{Precision + Recall}$$ (3)

To test the classification performance of the model, the Matthew correlation coefficient (MCC) has been used, which is described as follows:

$$MCC = \frac{TP \cdot TN - FP \cdot FN}{\sqrt{(TP + FP)(TP + FN)(TN + FP)(TN + FN)}}$$ (4)

where TP is the number of true positives, FP the number of false positives, TN the number of true negatives and FN the number of false negatives. And finally, Cohen’s Kappa (CK), CK is another metric that estimates the performance of the model [29].

# 3. Results

The study was conducted on a group of 125 patients diagnosed with SLE. Out of these, 94 patients met the specific criteria of having a SLEDAI-2K score of less than four points, and were thus included in the study. Further analysis revealed that 77 of these 94 patients showed signs of immunodeficiency. This means that approximately 81.9% of the patients with a SLEDAI-2K score less than four exhibited signs of immunodeficiency.

The cohort of patients had a median age of 52 years, whilst the median age at diagnosis was 38 years. The group was predominantly female, with 68 female patients compared to 9 male patients. The median duration of the disease among these patients was 14 years. At the time of data collection (see Table 1), 50 patients (64.9%) were being treated with corticosteroids at an average daily dose of 2.57 mg. In addition, 25 patients (34.9%) were receiving immunosuppressants such as azathioprine, methotrexate, and mycophenolate. Two patients were on belimumab treatment. Notably, none of the patients were undergoing treatment with rituximab.

In turn, 41 patients (53.2%) exhibited patterns of immunodeficiency. Among these patients, there were a total of 51 episodes of severe infections. The breakdown of these infections is as follows:

+   • 17 patients were hospitalized due to lower respiratory infections.
+   • 4 patients were hospitalized for upper respiratory infections.
+   • 9 patients were treated for urinary infections.
+   • 10 patients had soft tissue infections.
+   • 4 patients suffered from digestive infections.
+   • 1 patient was diagnosed with tuberculous lymphadenitis.