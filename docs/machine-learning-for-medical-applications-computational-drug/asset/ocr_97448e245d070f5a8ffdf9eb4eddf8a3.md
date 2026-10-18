this process is realized through the iterative procedure of integrally combining the results of multiple learners and, as a result, achieving overall enhanced efficiency and robustness in the constructed model.

![](bbox=[0.14, 0.22, 0.93, 0.34])

Figure 12: Boosting.

The boosting algorithm operates in several stages:

Initialization: A base model, often a weak learner, was developed from the original data by building a decision tree with a few levels. The first model was used as the basis for developing the subsequent models.

Error Calculation: After the training of the base model, the errors (or residuals) are computed. For the primary model above, the errors are computed after the base model is trained. These residuals show where the model has underperformed; that is, they reveal the data that needs more focus to be effectively predicted.

Reweighting: As with the previous round, the errors obtained are used to alter the training dataset. Misclassified cases are given higher weight than correctly categorized cases. This change ensures that the successive model gives more focus to the hard cases.

Model Training: As for the reweighted dataset, a new weak learner was built. This learner focuses solely on the cases that the earlier model classified incorrectly to correct its errors.

Aggregation: Of all the learners, it was the final weak learner that was obtained by combining the predictions of all the weak learners. For the aggregate of learners, weighted voting (for classification) and weighted averaging (for regression) can be used, with each learner’s rating being proportional to the accuracy it displayed.

Iteration: When a certain number of rounds have been completed and no further improvement is made, the procedure is repeated. The above model becomes more sophisticated in the way it describes the complexity of the patterns in the data during each iteration.

Several boosting algorithms have been developed, each with unique characteristics: