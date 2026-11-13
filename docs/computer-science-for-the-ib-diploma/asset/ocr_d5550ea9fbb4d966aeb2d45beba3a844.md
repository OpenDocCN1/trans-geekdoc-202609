+   ## See also
+   Reference the scikit-learn documentation for decision trees by searching online for scikit-learn’s section 1.10 “Decision Trees” (https://scikit-learn.org/stable/modules/tree.html).

The iris data set csv file can be downloaded from https://github.com/paulbaumgarten/hodder-ibdp-computerscience

One real-world application of decision trees is to assist with patient diagnosis. The features (variables) at issue in such a model may include demographic information (age, sex, height, weight); clinical measurements (blood pressure, glucose levels, haemoglobin, cholesterol); lifestyle factors (such as smoking status and alcohol consumption); along with symptoms, conditions, medical history and test results. It is easy to envisage such a model having dozens of features.

> ## ACTIVITY
> **Thinking skills: Classification with KNN or decision trees?**
> 
> Select a classification problem and perform a comparison analysis of both KNN and decision trees to solve the problem. Evaluate the trade-offs between the two approaches and create a decision matrix based on criteria such as ease of understanding, computational efficiency, performance on small vs large data sets, and so on.

+   ## Top tip!
+   When choosing between k-nearest neighbours (KNN), decision trees and artificial neural networks for a supervised learning classification scenario, consider the following:
+   
+   - KNN suits moderate data sizes and low dimensions; decision trees handle mixed data sizes well; neural networks excel with large, complex data sets.
+   - KNN requires normalization; decision trees need minimal preprocessing; neural networks often require extensive preprocessing.
+   - KNN and decision trees are highly interpretable; neural networks are less so, and are often considered “black boxes”.
+   - KNN are slow at prediction; decision trees offer fast predictions but can overfit easily; neural networks require significant computational power but handle non-linear data well.
+   - KNN easily integrate new data; decision trees and neural networks most often require retraining.

# # A4.3.3 Supervised learning: evaluation and tuning

# ## Evaluation metrics

> ## TOK
> **How can we know that current knowledge is an improvement upon past knowledge?**
> 
> Machine learning requires evaluating the performance of new algorithms against benchmarks or previous models.
> 
> In the context of machine learning, improvement is often quantified in terms of performance on specific tasks. However, Theory of Knowledge invites you to question deeper aspects of this improvement: Does performing better on a task, like object recognition, necessarily mean the algorithm has gained more “knowledge”? Is the understanding deeper or merely more functional?
> 
> Additionally, metrics can sometimes be misleading. For example, an algorithm might score very highly on accuracy but fail in particular scenarios that weren’t well represented in the training data.

Within supervised learning, there are several important, established metrics that can be used to evaluate the effectiveness of your model.