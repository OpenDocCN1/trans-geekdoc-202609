```
scratch_predictions = get_predictions(validation_loader,
scratch_model)
# Get actual targets
targets = [target.cpu().numpy() for _, target in
validation_set]
# Calculate metrics for both models
def calculate_metrics(targets, predictions):
    accuracy = accuracy_score(targets, predictions)
    precision = precision_score(targets, predictions,
    average='macro')
    recall = recall_score(targets, predictions, average='macro')
    f1 = f1_score(targets, predictions, average='macro')
    return accuracy, precision, recall, f1

fine_tuned_metrics = calculate_metrics(targets,
fine_tuned_predictions)
scratch_metrics = calculate_metrics(targets,
scratch_predictions)
# Print A/B Testing Results
print("Fine-Tuned Model Metrics: Accuracy: {:.2f}, Precision:
{:.2f}, Recall: {:.2f}, F1 Score:
{:.2f}".format(*fine_tuned_metrics))
print("Scratch Model Metrics: Accuracy: {:.2f}, Precision:
{:.2f}, Recall: {:.2f}, F1 Score:
{:.2f}".format(*scratch_metrics))
# Evaluate the difference
differences = [ft - sc for ft, sc in zip(fine_tuned_metrics,
scratch_metrics)]
print("\nDifferences (Fine-Tuned - Scratch): Accuracy: {:.2f},
Precision: {:.2f}, Recall: {:.2f}, F1 Score:
{:.2f}".format(*differences))
```

From the previous section, we can compare the different metrics and get a quantitative measure when comparing two models. From the different metrics, it is quite evident that