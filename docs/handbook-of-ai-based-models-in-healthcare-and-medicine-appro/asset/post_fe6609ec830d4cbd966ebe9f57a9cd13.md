
![](img/a2fc2296b12812e9151e817bff1de16d_281_0.png)

## FIGURE 14.12 BPM estimator

dashboard consists of bar graphs representing BPM calculated on a daily basis, to find how BPM varies from day to day, and of medical history, which gives the overall picture of the user’s health. It also enables the user to edit and update previous medical records in order to maintain data integrity.

Figure 14.14 is the BPM bar chart, which shows the daily heartbeat. Figures 14.15 and 14.16 show the list of medical histories.

## 14.6.1.3.5 Chatbot

The chatbot acts as a provider of remedial measures or solutions to users who have a high chance of suffering a heart attack, which is shown in Figures 14.17 and 14.18. Once the predictor module predicts the existence of heart risk for the user, the application redirects the user to the chatbot module. The chatbot is developed using Kommunicate, which provides instant remedies before consulting a medical expert or hospital.

![](img/a2fc2296b12812e9151e817bff1de16d_282_0.png)

## FIGURE 14.13 BPM estimator

## 14.7 EXPERIMENTAL ANALYSIS

### 14.7.1 Comparative Study

A comparative study helps in building an analytical and comprehensive approach for applying legal reasoning. This research helps to find the best approach to deploy the application. Analysis is done on various classification algorithms such as AdaBoost, gradient descent, and random forest. It is evident from Table 14.1 that the random forest classifier outperforms other classification algorithms with a maximum accuracy rate of 96.5% and is therefore adopted for further evaluation.

### 14.7.2 RESULTS AND DISCUSSIONS

### 14.7.2.1 Hyperparameter Tuning using GridSearchCV

GridSearchCV is a hyperparameter tuning process to determine the optimal value for a given model. The performance of the model is highly dependent on the value of the hyperparameters. Note that the best value for the hyperparameter cannot be known in advance; we must try all possible values to find the optimal value. GridSearchCV is used to automate the tuning of hyperparameters. GridSearchCV is a function included in the scikit-learn (or SK-learn) model_selection package. Some arguments used in GridSearchCV are estimator, params_grid, signature, cv, expression, and n_jobs. After running hyperparameter tuning on all three algorithms, the test data accuracy of the random forest classifier model performed better than the other two algorithms, and this model was adopted for the next evaluation step.

![](img/a2fc2296b12812e9151e817bff1de16d_283_0.png)

## FIGURE 14.14 BPM bar chart

### 14.7.3 PERFORMANCE METRICS

### 14.7.3.1 Precision

Precision is defined as the ratio of positive samples classified as correct (true positive) to the total number of positive samples (correct or incorrect). Precision helps to visualize the reliability of machine learning models in classifying the model as positive.

![](img/a2fc2296b12812e9151e817bff1de16d_284_0.png)

## FIGURE 14.15 List of medical histories

### 14.7.3.2 Recall

Recall is calculated as the number of positive samples classified as positive to the total number of positive samples. Recall measures the ability of the model to detect positive samples. The higher the recall, the more positive samples are found. Precision does not depend on the number of negative sample classifications. Additionally, recall will be one if the model classifies all positive samples as positive.

In this model, it is important to remember that there is no error (100% recall) because it helps to predict the heart risk of the user with a better level of accuracy. The recall is 93.4%, which means that there is a 6.6% chance of the user being at risk of heart failure. The system can also adjust the performance evaluation criteria to reduce the error rate and increase the recall rate.

![](img/a2fc2296b12812e9151e817bff1de16d_285_0.png)

## FIGURE 14.16 Medical history

### 14.7.3.3 Precision and Recall Tradeoff

The precision and recall tradeoff is used when changing the threshold to determine whether a class is positive or negative. Remember to increase or decrease to adjust accuracy.

From Figure 14.19, it is evident that when the recall is increased, precision will be decreased. By increasing the recall to one, the precision value is decreased to 0.7. Therefore, the recall is being increased by setting up the right threshold value.

### 14.7.3.4 Setting Threshold Value

In order to increase the recall value, the threshold value needs to be tuned. The current threshold value of the model is 0.2. From Figure 14.20, it is evident that the threshold value should be 0.3 to increase the value back to one. The model is evaluated based on the new threshold value.

![](img/a2fc2296b12812e9151e817bff1de16d_286_0.png)

## FIGURE 14.17 Chatbot home page

## 14.8 EVALUATING METRICS AND RESULTS

### 14.8.1 Confusion Matrix

Confusion matrix is a table used to describe the performance of a classification algorithm. The confusion matrix visualizes and shortens the classification algorithm. Also known as an error matrix, a summary table is used to evaluate the performance of a classification model.

From Figure 14.21, it is known that the presence of a false negative (FN) is zero and it also achieves the recall of one. Hence, the model works error-free and works efficiently for all heart-risk patients.

![](img/a2fc2296b12812e9151e817bff1de16d_287_0.png)

## FIGURE 14.18 Heart query chatbot

## TABLE 14.1

## Comparison Chart

|  | Precision (%) | Recall (%) | Accuracy (%) |
|---|---|---|---|
| AdaBoost | 93.3 | 90.1 | 88.5 |
| Gradient Descent | 91.7 | 87.4 | 92.9 |
| Random Forest | 94.1 | 92.7 | 96.5 |

![](img/a2fc2296b12812e9151e817bff1de16d_288_0.png)

## FIGURE 14.19 Precision and recall tradeoff

### 14.8.2 AREA UNDER CURVE - RECEIVER OPERATING CHARACTERISTIC (AUC-ROC) CURVE

The AUC-ROC curve is a performance measurement graph used in classification problems by adjusting the threshold values. ROC is also referred to as the probability curve and AUC describes the degree or measure of separability. The higher the AUC, the better the model is at binary classification. By analogy, the higher the AUC, the better the model is at distinguishing between users with and without heart risk.

From Figure 14.22 and the AUC score, we can see that the model is excellent and has an AUC near to one, which means it has a good measure of separability.

### 14.8.3 CRMT SYSTEM OUTCOME

The CRMT system provides a valuable solution to the user using the chatbot functionality. A chatbot (conversational AI) is an automated program that generates human conversation through text messages, voice chats, or both. Experts predict that cost savings from healthcare chatbots will reach $11 billion globally by 2023. It learns to do that based on a lot of inputs and natural language processing (NLP) to provide a better user experience. Often referred to as virtual agents or intelligent virtual assistants, these NLP chatbots help human agents by taking over

![](img/a2fc2296b12812e9151e817bff1de16d_289_0.png)

## FIGURE 14.20 Precision and recall curve

![](img/a2fc2296b12812e9151e817bff1de16d_289_1.png)

## FIGURE 14.21 Confusion matrix

![](img/a2fc2296b12812e9151e817bff1de16d_290_0.png)

## FIGURE 14.22 ROC curve and AUC score

![](img/a2fc2296b12812e9151e817bff1de16d_290_1.png)

## FIGURE 14.23 Risk prediction

![](img/a2fc2296b12812e9151e817bff1de16d_291_0.png)

## FIGURE 14.24 Heart query chatbot

repetitive and time-consuming communications. The CRMT system is developed using Kommunicate, which provides instant remedies before consulting a medical expert or hospital.

Once the required details have been filled by the patient, the CRMT System predicts the existence of heart risk for the user who has been redirected to the chatbot for quick remedies.

Figure 14.23 shows the prediction of heart risk by the CRMT system and Figure 14.24 gives us the mobile interface and working of chatbot for a simple query from a user who has been diagnosed with heart risk.

The user can also visit the chatbot interface without being diagnosed as a risk patient [20]. The query window or the chatbot interface starts asking basic questions and will suggest to the user a few tips for being healthy in daily life

Figure 14.25 shows the chatbot window for a user who hasn’t been diagnosed with the presence of heart risk. Chatbots can leverage feedback to make smarter decisions and improve their practices.
