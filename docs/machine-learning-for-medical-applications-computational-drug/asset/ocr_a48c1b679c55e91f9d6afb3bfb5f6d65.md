points 0.75–0.25 of the ROC curve, and AUC are examples of such assessment measures. There is a need to ensure that efforts made to optimize the parameters for the model do not cause overfitting of the validation set. This issue can be corrected by using several test sets to evaluate the final model.

Computational Cost: Optimizing hyperparameters can be very computationally expensive and can take a lot of time, especially if one is carrying out a grid search. To achieve the best tuning, both the extent of the search of the hyperparameter space and the time complexity must be balanced.

Dimensionality of Hyperparameter Space: This makes it almost impossible to determine the best settings, especially with so many hyperparameters to choose from. Some of the approaches include dimensionality reduction techniques and efficient search algorithms to control the complexity.

Overfitting and Model Selection: It was also important to ensure that the model was not overfitting when tuning the hyperparameters for the validation set. We needed two different test sets to determine the final generalization performance of the model and to check that the chosen hyperparameters provide good performance on unseen data.

Hyperparameter optimization was a key driver of the accuracy of an individual machine learning model for drug toxicity predictions. It was, therefore, possible to achieve improved model accuracy and predictability, which, in turn, allowed for improved reliability of insights influencing drug safety assessment.

# 5.4 Model robustness and stability

Other things being equal, model reliability and stability are major areas to consider when evaluating machine learning models, especially in computations for drug toxicity. Robustness refers to performance when exposed to inputs different from the source of training or to changes in the environment, while stability refers to consistent and reliable performance across different periods of time and various datasets.

Sensitivity analysis was the procedure used to examine changes in the mechanisms of defining predictions of the model with regard to changes in input parameters. This method helps in identifying which characteristics have a significant impact and how changes in the above-mentioned aspects affect the overall functioning of the model. Figure 19 shows the model's stability, which can also be characterized as good resistance to initial conditions and input variations. On that note, one learns about sensitivities – that is, how much the model's outputs change when inputs are slightly adjusted – so that their perception of the model's robustness enables them to test how well the model holds up to such treatment and whether minor shifts cause forecasts to vary significantly.

Adversarial Testing: Adversarial testing involves incorporating adversarial examples in an attempt to determine how the model performs under adverse conditions.