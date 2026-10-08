+   - Model quality monitoring metrics: These model quality metrics provide visibility into model performance deviation from the original benchmark. These metrics can include regression metrics (such as MAE and RMSE) and classification metrics (such as confusion matrix, F1, precision, recall, and accuracy).

+   - Model inference explainability: This model provides explainability on a prediction basis to help you understand what features had the most influence on the decision that was made by the prediction.

+   - Model bias monitoring metrics: Similar to bias detection for training, the bias metrics help us understand model bias at inference time.

The model monitoring architecture relies on many of the same AWS services, including CloudWatch, EventBridge, and SNS. The following diagram shows an architecture pattern for a SageMaker-based model solution:

![](bbox=[0.14, 0.375, 0.86, 0.715])