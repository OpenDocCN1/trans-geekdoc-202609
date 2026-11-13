
Model performance was evaluated on both training and testing sets using the evaluate method:

- **Training accuracy:** Measured to assess model fit to the training data.
- **Testing accuracy:** Measured to assess model generalizability to unseen data.

## 2.3 RESULT AND ANALYSIS

Various metrics, including accuracy, precision, recall, and F1-score, were used to assess the performance of the model. Without the validation split, the training accuracy was determined to be 75.34%, while the testing accuracy reached 74.21%. The precision, recall, and F1-score were all calculated to be 0.7420, with a total support of 21,971 instances. With the validation split, the training accuracy slightly decreased to 74.34%, while the validation accuracy increased to 74.38%. Similarly, the precision, recall, and F1-score were all consistent at 0.7437, with a support of 21,971 instances. The confusion matrix with the validation split parameter revealed that the model had a higher precision for predicting negative instances (0.81) compared to positive instances (0.70), while recall was higher for positive instances (0.85) compared to negative instances (0.64). These metrics collectively demonstrate the model's ability to accurately classify instances of DM, highlighting its effectiveness in disease detection and risk assessment.

The validation split is crucial for evaluating the model's performance on an independent dataset. Without it, the model may overfit, resulting in a decrease in the loss of training data over epochs. Therefore, it's essential to use validation split to measure the model's performance on the independent dataset, preventing overfitting and ensuring accurate training data evaluation (Figures 2.4 and 2.5).

| Actual Label \ Predicted Label | 0 | 1 |
| :--- | :---: | :---: |
| 0 | 7878 | 3166 |
| 1 | 2536 | 8391 |

FIGURE 2.4 Confusion matrix for the model without validation [5].

| Actual Label \ Predicted Label | 0 | 1 |
| :--- | :---: | :---: |
| 0 | 7771 | 3273 |
| 1 | 2373 | 8554 |

FIGURE 2.5 Confusion matrix for the model with validation [5].

## 2.4 DISCUSSION

The results of the deep learning model trained to predict DM based on physiological data exhibit promising performance metrics. Both scenarios, with and without the validation split, achieved comparable accuracies, indicating the robustness of the model. The precision, recall, and F1-score metrics further validate the effectiveness of the model in correctly identifying instances of DM. However, the model exhibited a small decrease in accuracy from training to testing, suggesting some degree of overfitting. This implies that the model might have memorized the training data patterns too well and may not generalize effectively to unseen data. The confusion matrix illustrates the distribution of correct and incorrect predictions, highlighting areas where the model excels and potential areas for improvement. Furthermore, changing hyperparameters, adding or removing layers, and other model adjustments may be required for optimization to achieve results with more promising accuracy.

According to the results, the model may be able to accurately identify DM from BRFSS data. Nonetheless, there exist prospects for additional refinement and enhancement of the model. To improve the model's functionality and generalizability, more feature engineering approaches, different model architectures, and bigger datasets may be investigated in subsequent studies. Furthermore, adding domain-specific information and clinical experience could enhance the model's interpretability and clinical value. This approach ensures robustness and generalizability in the detection of DM using deep learning techniques (Figures 2.6–2.8).

![](img/7df621e14c1a5d96077d3e56e3977008_47_0.png)

FIGURE 2.6 Visual analysis of loss of training without validation [5].

![](img/7df621e14c1a5d96077d3e56e3977008_48_0.png)

FIGURE 2.7 Visual analysis of training loss [5].

![](img/7df621e14c1a5d96077d3e56e3977008_48_1.png)

FIGURE 2.8 Visual analysis of validation loss [5].

## 2.5 CONCLUSION

With approximately 74% training accuracy and 74% testing accuracy, the model with validation split parameter demonstrated a reasonable level of accuracy, indicating its potential utility as a screening tool for preliminary information. The sequential deep learning model with validation for binary classification effectively constructed a deep learning model to identify DM using physiological data. Strong performance measures were demonstrated by the model, including high values for recall, accuracy, precision, and F1-score. The model's ability to rectify class imbalances and produce reliable predictions was greatly enhanced using a balanced dataset and careful preprocessing methods. These results demonstrate the great promise of deep learning approaches in the healthcare domain, especially in applications related to risk assessment and disease detection. To improve the model's functionality and make it easier for it to be integrated into clinical practice, future research may investigate optimizing techniques and adding more features.

## REFERENCES

- 1. International Diabetes Federation. (2021). IDF Diabetes Atlas, 10th edn. Brussels, Belgium: International Diabetes Federation.
- 2. American Diabetes Association. (2022). Diagnosis and classification of diabetes mellitus. Diabetes Care, 45(Suppl 1), S17–S38.
- 3. American Diabetes Association. (2022). Standards of medical care in diabetes: 2022. Diabetes Care, 45(Suppl 1), S1–S236.
- 4. https://www.cdc.gov/brfss/annual_data/2021/pdf/codebook21_llcp-v2-508.pdf
- 5. https://www.kaggle.com/code/muskansah/diabetes-mellitus-detection
- 6. https://www.kaggle.com/code/hakonem/diabetes-health-indicators-dataset-notebook

## Graph-Based Explainable Method for Blood Glucose Prediction through Federated Learning

Chengzhe Piao and Kezhi Li

## 3.1 INTRODUCTION

Type 1 diabetes (T1D) occurs if the pancreas fails to generate sufficient insulin, resulting in elevated blood glucose (BG) levels (hyperglycemia, defined as BG > 180 mg/dL). To manage their condition and maintain BG levels within the normal range (70–180 mg/dL), individuals with T1D rely on insulin delivery methods such as pumps and bolus injections. Without proper management, there is a significant risk of experiencing hypoglycemia (BG < 70 mg/dL) or hyperglycemia, which can lead to severe complications, including kidney issues, vision problems, and even blindness.

To prevent these serious health issues, it is crucial for people with T1D to actively monitor and manage their BG levels. Continuous glucose monitoring (CGM) systems have become a vital tool in this regard, offering the ability to track BG level fluctuations every 5 minutes. Leveraging the detailed data provided by CGM, researchers have developed a variety of predictive models for blood glucose level prediction (BGLP). These models enable individuals with T1D to proactively adjust their insulin dosages and dietary intake, significantly enhancing their ability to maintain stable BG levels and mitigate the risk of complications.

In BGLP, historical data is often structured as multivariate time series (MTS) to incorporate various attributes relevant to the prediction task. Since 2020, neural network (NN)-based methodologies have demonstrated superior performance over traditional non-NN approaches, particularly highlighted during the BGLP 2020 Challenge. Among these advancements, Neural Basis Expansion Analysis for Time Series (N-BEATS) (Oreshkin et al., 2020) has been applied by Rubin-Falcone et al. (2020). N-BEATS was a leading approach for time-series analysis at the time, and their N-BEATS-based solution notably secured first place in the challenge. Despite these achievements, a significant limitation remains: These models offer limited insight into the significance of different attributes, such as glucose levels, bolus, and finger sticks, in the prediction process. This lack of attribute importance explanation is a gap not only in N-BEATS but also in other contemporary BGLP methodologies that rely on recurrent neural network (RNN) architectures like long short-term memory (LSTM; Hochreiter and Schmidhuber, 1997; Yang et al., 2020). These approaches can capture temporal dependencies but fall short in transparently modeling the interconnections among attributes. The importance of this limitation cannot be understood, as many clinicians and healthcare professionals prioritize understanding the decision-making process of predictive models. The ability to interpret how different attributes influence predictions is crucial for clinical acceptance and trust in these technologies.

Therefore, a critical limitation of these approaches is their inability to quantify and explain the significance of each attribute within the BGLP context. To address this gap, advancements in graph neural networks (GNNs) present a promising avenue, particularly those employing dynamic graphs with adaptable edge weights. Graph attention networks (GATs; Velickovic et al., 2018) enable the edge weights, predicated on the adjacent node tensors, to be adjustable during the learning process. Subsequently, Brody et al. (2022) developed an enhanced version, GATv2, which incorporates a more dynamic attention mechanism, offering increased model expressiveness. These innovations in GAT and GATv2 facilitate the explanation of attribute significance in BGLP through the modulation of edge weights.
