learning methods. The proposed technique had the highest accuracy when compared to other strategies, with a score of 92.39%.

In recent years, machine learning-based approaches such as supervised machine learning have become more widely applied in the field of healthcare. Heart disease, diabetes, lung cancer, breast cancer, and other diseases have been successfully detected using computer-assistive detection systems that use learning-based methodologies. Both clinicians and patients can benefit from this information if it is discovered early enough.

# METHODOLOGY

The goal is to develop and validate an effective approach using Machine Learning to assist in the initial diagnosis of dementia.

To develop and evaluate the proposed system, following steps are used:

+   1. Data collection: In this step, we have collected data on dementia prediction.

+   2. Clean and Analyse Data: filtered the necessary (useful) data so that our model could predict dementia efficiently and effectively.

+   3. Training Algorithm: An appropriate training algorithm, algorithm we have used to predict dementia is CNN & RFA.

+   4. Evaluate: The test of our model falls into this category.

# Proposed Model for Predicting Dementia using Patient Record and MRI

Fig. (1) depicts the proposed model for predicting dementia using patient records. The following is the flow chart of this model’s working. Also, the Deep Learning based model proposed for predicting dementia is shown in Fig. (2).

In the first step, the model creates new datasets from the given data, a technique known as bootstrapping. In the second step, it creates multiple decision trees based on the new datasets, the results of which will be our predictions, and the result will be the average of those predictions, a technique known as aggregation.When aggregation and bootstrap both occur, the technique is known as bagging.