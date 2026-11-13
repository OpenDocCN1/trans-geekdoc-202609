**Confusion matrix:** a simple pictorial means of representing how well a machine learning model is performing.

The starting point would typically be to produce a confusion matrix. For a binary classification problem, the data forms a two-row, two-column table modelled as follows:

| | Predicted |
|---|---|
| | Predicted positive | Predicted negative |
| Actually positive | True positive | False negative |
| Actually negative | False positive | True negative |

The number of scores that are *true positive*, *false negative*, *false positive* or *true negative* are written into the respective cell (and typically colour coded with dark shading to indicate higher quantities), the idea being that it is a quick visual indicator of the success of your model. If the highest numbers (and dark shading) run down the diagonal of *true positive* and *true negative*, then that is a good sign.

A confusion matrix can also be produced for higher dimensional classification problems. In that instance, each possible classification would be turned into rows and columns. In this case, the diagonal set of cells from top left to bottom right would again represent correct predictions. Using your confusion matrix, you can proceed to calculate the accuracy, precision, recall and F1 scores.

+   **Accuracy**: The fraction or ratio of correct predictions
+   accuracy = correct predictions / total predictions

+   **Precision**: The fraction or ratio of correct positive predictions to total positive predictions
+   For instance, of all images recognized as being "cats", how many of them were correctly classified? Alternatively, of all the "spam" predictions, how many of those were correctly "spam"? This is important when a false positive may have a significant consequence.
+   precision = true positives / (true positives + false positives)

+   **Recall**: The fraction or ratio of correct positive predictions to actual positives
+   For instance, this could be number of patients correctly predicted to have diabetes, out of all the patients who truly have diabetes.
+   recall = true positives / (true positives + false negatives)

+   **F1 score**: The harmonic-mean of precision and recall; it is particularly useful where both false positives and false negatives may carry significant consequence
+   A harmonic-mean is different from an arithmetic mean in that it will always give a score closer to the smaller of the two numbers. The F1 score will range from 0 to 1, with 1 being the best score.
+   F1 score = 2 * (precision * recall) / (precision + recall)

Consider using an F1 score in the criminal justice system, where an algorithm has been devised to predict whether an individual will re-offend if released on parole. (Note that there have been real-world problems in using machine learning modes for this exact scenario; refer to A4.4 Ethical considerations for more.) In this situation, precision measures the correctness of positive predictions. High precision means most individuals predicted to re-offend actually did re-offend. Recall measures how well the model successfully identifies those who will re-offend, so that re-offenders are not being ignored by the system. Both are important for matters of public safety, so combining them through the use of the F1 score is valuable.