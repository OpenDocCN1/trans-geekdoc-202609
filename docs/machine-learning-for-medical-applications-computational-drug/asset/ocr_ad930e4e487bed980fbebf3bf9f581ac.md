include inefficient implementations and the inability to handle multiple operations simultaneously.

Interpretability: The combined nature of boosting models complicates interpretation. Methods for displaying models and their assessment are crucial for identifying the individual impact of learners and general model trends.

Boosting is a powerful and flexible technique in the ensemble learning model that significantly improves predictive performance. Thus, when applied to predict drug toxicity, the proposed method enhances the detection of potential side effects and supports the development of safer and more efficient drugs.

# 4.3 Stacking

Stacking generalization is one of the most complex ensemble learning methods, where multiple models are used to enhance the predictive accuracy of a particular model. This method produces the final prediction by utilizing the advantages of many base learners, often surpassing the performance of individual learners. Figure 13 presents the stacking process, where a number of models provide their prediction results, which are then used to formulate the final prediction after aligning with each other. The main concept behind stacking is to achieve better accuracy and robustness of the ensemble by learning the final decision-making process from many base learners.

The stacking process involves two main stages: the basic level and the meta level.

Base Level: At this point, several base models are trained on the same data set. These models consist of different methods, such as decision trees and support vector machines. All base models apply the patterns they have learned to generate outputs.

Subsequently, a meta-learner utilizes predictions as input features of basic models found in the literature. This meta-learner learns how the predictions of such underlying models should be combined to give the final result. It is often a more complex model, such as the logistic regression model. To ensure the meta-learner is well generalized, it is trained on a different validation set.

Stacking employs different training strategies to optimize the ensemble:

Layered Stacking: Includes placing one model on top of another. The first layer is built from the base models learned directly on the original data, while the other layers are built from the predictions of the previous layers. This can reflect the effect of one model on another but creates a high risk of over learning.

Stacked Generalization: This work involves employing base models that were trained with the original dataset to train the meta-learner using the predictions of the base models. To ensure that the meta-learner has an unbiased prediction, cross-validation is often used to partition the data into training and validation sets for both the base and meta-level learners.