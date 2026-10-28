the domain knowledge to enhance performance on the text data.

# Question 2: How do you approach handling imbalanced classes in sentiment analysis or other classification tasks in NLP?

Answer: Dealing with uneven classes in NLP Classification is just like any other category of machine learning, where we are required to do either data resampling in one of the following ways: oversampling, where more samples are generated for the minority class or undersampling, where there are fewer samples selected from the majority class, class weighting, where more weight is given to the minority class during the training of the model. They impact the misclassified instances in the minority class more to force the model to mine for improvement in that class. Data augmentation can, therefore, be used as a technique to come up with more samples for the minority class.

From modeling perspective, we can apply ensemble, cost-sensitive learning, transfer learning to make use of more trained models or embeddings, select fitted evaluation metric, F1 score or area underneath precision recall curve, to give a more comprehensive performance measure of the model in imbalance situations.

Thus, the choice of the method or several methods all together for classification depends on the nature of the problems or dataset in question. It is therefore very important to devote some time and thought to the nature of the imbalanced classes and the likely effects on the observed outcome, so that handling imbalanced datasets in NLP classification such as sentiment analysis can be addressed adequately.

# Question 3: Discuss the advantages and disadvantages of pre-trained language models (for