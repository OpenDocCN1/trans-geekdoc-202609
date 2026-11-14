The first step is called bootstrap sampling, where N sub-datasets are created. These new datasets are called bootstrapped datasets. The sampling used in each sub-dataset will be done using replacement. Each sub-dataset may also contain duplicate datasets due to the replacement method. The training process starts for each sub-dataset independently. A base classifier is chosen for each sub-dataset; this classifier is called a weak learner (e.g., a DT). These classifiers are purposefully left unpruned to increase diversity among them. The final step is to classify the instance into a class. Once all the classifiers complete the training stage, they are used to predict the given instance, with the results of all the models being recorded, and the final class is decided by the majority vote among all the classifiers [18].

The bagging method will reduce the variance of the model [19]. Each model will have different variances as they are trained using completely different training data; the combined model will have lower variances due to averaging. The following lists the advantages of bagging ensemble learning:

+   1. There is less chance of overfitting as the bagging will combine multiple models, which tends to reduce the chance of overfitting. The bagging is used specifically in a few models with high variance by nature, for example, DTs.
+   
+   2. The combined model produces higher accuracy than a single model, as the aggregated model reduces the data from becoming noisy or complex by distributing it across the models.
+   
+   3. The combined model is more robust, and it makes it less sensitive to noise.
+   
+   4. The training of the bagging ensemble model is easy, as all the independent base learners can be trained in parallel, which makes the computational resource usage optimal.

A good example of a bagging ensemble model is RF, where each DT is trained on the bootstrapped datasets. Bagging will primarily reduce the variance but not the bias. Bagging models are less interpretable, for some applications where transparency is required, than the bagging model will fail to provide explanations.

# 3.3 Boosting-Based Ensemble Model

Boosting is also an ensemble method that converts a set of weak learners into a single strong learner that is designed to improve the overall accuracy of the machine learning classification task. It is completely different from bagging, where bagging allows models to train independently, but boosting trains the model sequentially. At each step, one model is trained, and the errors made by the model are noted. When training the next model, these errors are corrected. Boosting is used for reducing both bias and variance; hence, it is more popular than the bagging method, and this is suitable for a wide range of applications in classification and regression problems [20].