
reasonable results, the team wanted to explore deep learning approaches for better performance and adaptability.

The team integrated ChatGPT into their workflow to accelerate development and reduce experimentation time. This AI-powered assistant helped guide architectural decisions, optimization strategies, and model evaluation techniques.

## AI-assisted development workflow

The following steps outline an AI-assisted development workflow where ChatGPT played a key role in guiding design, training optimization, and evaluation:

- 1. **MLP architecture design**: ChatGPT helped the team construct a 3-layer MLP using Keras, incorporating Dropout and batch normalization to enhance generalization and prevent overfitting.

- 2. **Training optimization**: The team implemented EarlyStopping, guided by ChatGPT's suggestion, to monitor validation loss and halt training at the optimal epoch.

- 3. **Model evaluation**: The MLP's performance was measured using ROC-AUC and F1 score, ensuring robust evaluation for the imbalanced dataset typically seen in loan default prediction.

## Outcome

The following outcomes achieved through the AI-assisted MLP implementation compared to the baseline model:

- The MLP outperformed the previous random forest baseline, achieving a 10% improvement in validation metrics.

- The model also demonstrated better generalization on unseen data and reduced overfitting, thanks to dropout, batch normalization, and AI-guided tuning. This use case illustrates the real-world impact of AI-assisted programming, which enables faster iteration, smarter architecture choices, and tangible performance gains in high-stakes domains like finance.

## Building and fine-tuning convolutional neural networks

Convolutional neural networks (CNNs) are the foundation of modern computer vision systems that capture spatial patterns in image data. With their layered architecture and ability to generalize across complex visual tasks, CNNs are ideal for classification, detection, and medical imaging. AI tools like ChatGPT and GitHub Copilot make designing, training, and fine-tuning CNNs faster and more effective, guiding everything from architecture design to transfer learning and hyperparameter tuning. This section explores CNN fundamentals, implementation in Keras and PyTorch, and a real-world healthcare application powered by AI assistance.

Before we explore CNN architectures in code, it is essential to understand how model performance is evaluated, especially in classification tasks.

## Evaluation for classification models

In classification tasks, measuring how often your model is correct is not enough. You need to evaluate how well it distinguishes between classes, handles imbalance, and makes what types of errors. Choosing the right metrics is key to building models that are not only accurate but also trustworthy and effective in real-world deployments. Let us look at some of the key evaluation metrics.

## Accuracy

Accuracy is a widely used evaluation metric, but its effectiveness depends on the data distribution, outlined as follows:

- **What it measures**: The proportion of correct predictions out of all predictions.
- **Caution**: It can be misleading when using imbalanced datasets. For instance, a model that always predicts the majority class can achieve high accuracy but fails to detect minority cases.

**Example:** 95% accuracy on a dataset with 95% negatives tells you nothing about model effectiveness on positives.

## Precision

Precision is a key performance metric in classification tasks, especially when false positives carry significant consequences, described as follows:

- **What it measures**: The proportion of predicted positives that are positive.
- **Why it matters**: High precision minimizes false positives, making it crucial for tasks like spam detection or fraud alerts.

## Recall

Recall, also known as sensitivity, is a crucial metric in classification tasks where identifying all positive cases is a priority, detailed as follows:

- **What it measures**: The proportion of actual positives that are correctly predicted.
- **Why it matters**: High recall reduces false negatives, vital in domains like medical diagnosis, where missing a positive case can be costly.

## F1 score

The F1 score is a balanced evaluation metric that combines precision and recall, making it especially valuable for imbalanced classification problems, outlined as follows:

- **What it measures**: The harmonic mean of precision and recall.
- **Why it matters**: Strikes a balance when both false positives and false negatives are important, making it especially valuable for imbalanced datasets.

## Confusion matrix

The confusion matrix provides a detailed summary of a classification model’s performance by showing how predictions align with actual outcomes, described as follows:

- **What it shows**: A breakdown of:
  - True positives (TP)
  - False positives (FP)
  - False negatives (FN)
  - True negatives (TN)
- **Why it matters**: Offers a clear visual summary of prediction performance by class, helping to identify where the model struggles.

## ROC-AUC

Receiver operating characteristic-area under curve (ROC-AUC) is a widely used metric that evaluates a model’s discriminatory power across various classification thresholds, detailed as follows:

- **What it measures**: The model can distinguish between positive and negative classes at different thresholds.
- **Ideal range**: AUC close to 1.0 indicates strong separability; 0.5 implies random guessing.

We look at a Python example using scikit-learn:
```python
from sklearn.metrics import (
accuracy_score, precision_score, recall_score,
f1_score, confusion_matrix, roc_auc_score)
print("Accuracy:", accuracy_score(y_true, y_pred))
print("Precision:", precision_score(y_true, y_pred))
print("Recall:", recall_score(y_true, y_pred))
print("F1 Score:", f1_score(y_true, y_pred))
print("AUC:", roc_auc_score(y_true, y_prob)) # y_prob = predicted probabilities
print(confusion_matrix(y_true, y_pred))
```

AI tip—Use ChatGPT to:

- Plot a labeled confusion matrix using Seaborn.
- Generate ROC and precision-recall curves with Matplotlib.
- Summarize classification results in a dashboard-like report.

AI tools can also help you interpret trade-offs between precision and recall and adjust thresholds dynamically based on business priorities. While CNNs are typically used for classification tasks, they are also employed in regression-based problems such as age estimation or object localization. Understanding how regression performance is evaluated helps broaden the reader’s perspective on CNN capabilities.

## Evaluation for regression models

In regression tasks, the goal is to predict a continuous value, not a class. Evaluating regression performance involves understanding how off predictions are from the true values, how consistent those errors are, and how well the model explains variability in the target.
Choosing the right metric depends on your use case. Do you care more about absolute error, penalizing large deviations, or explaining overall fit? Let us look at some of the regression metrics.

## Mean absolute error

MAE is a fundamental regression metric that offers an intuitive measure of prediction accuracy, outlined as:

- **What it measures**: The average absolute differences between predicted and actual values.
- **Why it matters**: Easy to interpret, less sensitive to outliers.

## Mean squared error

MSE is a common regression metric that emphasizes larger prediction errors, making it valuable in scenarios where big deviations are critical, explained as:

- **What it measures**: The average squared differences between predicted and actual values.
- **Why it matters**: Penalizes larger errors more heavily than MAE, making it useful in scenarios where significant deviations carry higher consequences.

## Root mean squared error

RMSE is a regression metric that provides error values in the same units as the target, enhancing interpretability.
