
study. This involves evaluation of the diverse and variable nature in the target subject population, relative to the sampled data. To ensure that the target populations are adequately captured in the datasets, and to avoid bias occasioned by systematic ways of sample selection, tests such as stratified sampling are applied.

To ensure the effectiveness and generalizability of prediction models developed from datasets, proper validation methods are crucial. These models are tested on unseen data to assess their performance. Cross-validation techniques such as k-fold cross-validation and leave-one-out cross-validation split the dataset into training and testing subsets to ensure robustness. The hold-out validation technique divides the dataset into distinct training and validation sets for performance evaluation. By employing appropriate validation methods, researchers can assess the reliability and stability of prediction models and evaluate their generalizability to new, unseen data.

In scaffold design, the data preparation stage includes thorough quality assessment and dataset evaluation. Predictive modeling in scaffold design applications can achieve high credibility and accuracy through rigorous data audits that ensure data integrity, completeness, and representativeness. Careful validation and verification of predictive models using suitable methodologies enhance the trustworthiness of the results.

## 3 Feature selection and engineering

### 3.1 Identification of relevant features in scaffold design

By using the concept of feature selection in scaffold design, auto-identification of important features is an important step in the feature engineering process, with the goal of selecting the right features that characterize scaffold structures and the performance of these structures. Many strategies can be used to determine the suitability of the scaffold in design, and each of them has its advantages and disadvantages.

The first method of feature identification is domain knowledge-driven feature selection, in which practitioners in the fields of tissue engineering and materials science provide their opinions on what features should be important, based on current research and theory. These include material properties for fabrication, fabrication methods, and biological properties about the scaffold, which are believed to affect the performance in terms of porosity, pore size, mechanical properties, and biocompatibility. This is important because by applying domain knowledge, researchers can strategically select features that contribute most toward the goals of scaffold design task.

Filter-based techniques of feature selection are frequently data-based, where decisions about which features to select are based on assessments of mutual relations and correlation of features in the dataset with respect to predictive power. This includes methods like correlational techniques, where the relationships between each of the features are computed with a view to establishing their correlation coefficients.

![](img/18722240e44c225d7ff2f58a10eecb4a_427_0.png)

Figure 3: Methods for feature selection in machine learning models.

model. Although filter techniques can handle high-dimensional datasets and are computationally efficient, they miss feature relationships and interactions.

On the other hand, wrapper approaches measure how well the built predictive models, which include different feature subsets, are, so as to assess the importance of a feature. Such examples of wrapper techniques include recursive feature elimination (RFE), forward selection, and backward elimination. These approaches constantly build predictive models, employing different feature combinations, and select the set with the highest model performance. Despite the fact that they can comprehensively capture feature dependencies and interactions, wrapper approaches are often computationally expensive, especially on large-scale datasets with many features.

In general, feature selection is performed during training, when it is used as an embedded technique, where the training selects the feature. Several modern tree-based models such as random forest, stochastic gradient boosting machines, and linear regression techniques such as LASSO, inherently perform feature selection by penalizing less informative features. The computational efficiency and the quality of the prediction of the result are satisfactory for embedded approaches, but the performance of feature selection is appropriate after adjustment of its hyperparameter.

Hybrid methods use embedded, filter, and wrapper techniques to exploit the benefits that each of the three possess. To enhance the ensemble’s stability and robustness, this work incorporates multiple feature selection algorithms into the ensemble feature selection approach. Filter techniques involve using statistical measures to identify the best set of features for a model from the existing data. While features

Thus, improving feature selection strategies that allow finding a balance between using more computational resources and having more features is one way of solving it. Indeed, filter approaches are relatively easy to use with big datasets with high dimensions and are less computationally demanding, since determining feature importance is beyond the prediction model. Filter techniques select the relevant characteristics, analyzing their correlation using statistical tests, which greatly simplifies the modeling procedure without loss of crucial information.

Only the vital data are retained while using methods such as PCA to reduce the number of features in the feature space. As feature space dimensionality is reduced through the identification of orthogonal linear feature combinations, which are associated with the greatest level of variation in a dataset, PCA does not impact prediction accuracy. Unlike in CCA, where we are forced to stick to the features in two lower dimensions, PCA reaches a middle ground between computation speed and feature expressiveness by preserving only a few of the main components that explain most of the variance. This, in turn, improves the scalability and interpretability of the prediction models.

The ensemble feature selection methodologies employ several feature selection methods and offer increased stability and level of robustness as well as preserving computational efficiency. Ensemble methods of feature selection allow for the use of a wide number of features without the risk of overemphasizing some best-performing features that different algorithms provide. Inexpensive computing techniques, such as random forests and boosting machines, provide stable and easily interpretable results in feature selection.

## 4 Model selection and evaluation

### 4.1 Comparison of machine learning algorithms for scaffold design

To increase the performance of the model in the scaffold design, it is necessary to select the best machine learning algorithm that enables obtaining accurate and reliable modeling results. In scaffold design applications, there is a tendency that numerous machine learning methods are used. Each has its strengths and weaknesses, whereby the performance depends on the properties of the dataset used and the modeling objectives.

Supervised learning algorithms, which operate on labeled data to classify inputs into predetermined categories, are among the most commonly used machine learning techniques in scaffold design. Examples include neural networks, KNN, SVM, decision trees, minimizing the generalization and stability problems. Some of the commonly used ensemble learning techniques include random forests, gradient boosting machines (GBMs), and ensemble neural networks. Ensemble neural networks afford better predictive accuracy and stability, in contrast to single models.

### 4.2 Cross-validation techniques for model evaluation

K-fold cross-validation is commonly used to evaluate model performance. In this method, the dataset was split into K equal subsets, each containing approximately the same number of records. The model is trained and validated K times, with each subset used once as the validation set while the remaining K-1 subsets are used for training. This iterative process helps reduce the variability associated with a single train-test split and provides a more reliable estimate of model performance. The final performance metric was then obtained by averaging the results across all K iterations, yielding a comprehensive assessment of the model's generalization ability.

Another form of cross-validation was Leave-One-Out Cross-Validation (LOOCV), where each observation in the dataset was used once as a validation set, and the remaining observations form the training set. LOOCV was particularly useful for models with small sample sizes, as each individual data point can significantly influence the model. Compared to K-fold cross-validation, LOOCV was more computationally intensive and may result in higher variance in the estimated performance metrics.

To maintain the right distribution of class data when splitting the data, the k-fold cross-validation could be of the stratified type. This is especially true in those cases where there are more samples from one class than from others in a dataset. In this case, since stratification is carried out on classes, it comes up with a reliable estimate of the model as it retains a balance of classes in the folds that are used in the k-fold cross-validation.

k-Times cross-validation means applying the above process more than once with different random partition of the dataset into the k subsets, and then taking the average of the performance measures. In this method, randomness of the data splitting is reduced and the performance measure of the model is less volatile.

In the aspect of model selection, the method mentioned above is called nested cross-validation. Another form of CV, an outer loop CV, is employed to evaluate the models. Here, an inner loop is used to tune the hyperparameters of the model. A more precise indication is given by an outer cross-validation – nested cross-validation, and it also allows avoiding overfitting on the validation sample.

In scaffold design applications, cross-validation methods are essential for the sake of model evaluation as they provide reliable estimates of the predictive performance, and are also useful for determining the appropriate form of model and hyperparameters for use. By a proper choice of cross-validation techniques, the authors
