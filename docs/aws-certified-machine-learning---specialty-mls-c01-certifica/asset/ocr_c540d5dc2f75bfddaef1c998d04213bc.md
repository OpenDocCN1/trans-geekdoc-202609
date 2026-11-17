choose from. Each modeling technique might carry some implicit assumptions of which you have to be aware. For example, if you choose a multiple linear regression algorithm to predict house prices, you should be aware that this type of model expects a linear relationship between the variables of your data.

There are hundreds of algorithms out there and each of them might have its own assumptions. After choosing the ones that you want to test in your project, you should spend some time checking their specifics. In later chapters of this book, you will learn about some of them.

# IMPORTANT NOTE

Some algorithms incorporate in their logic a sub-process known as feature selection. This is a step where the most important features will be selected to build your best model. Decision trees are examples of algorithms that perform feature selection automatically. You will learn about feature selection in more detail later on, since there are different ways to select the best variables for your model.

During the modeling phase, you should also design a testing approach for the model, defining which evaluation metrics will be used and how the data will be split. With that in place, you can finally build the model by setting the hyperparameters of the algorithm and feeding the model with data. This process of feeding the algorithm with data to find a good estimator is known as the training process. The data used to feed the model is known as training data. There are different ways to organize the training and testing data, which you will learn about in this chapter.

# IMPORTANT NOTE

ML algorithms are built of parameters and hyperparameters. Parameters are learned from the data; for example: a decision-tree-based algorithm might learn from the training data that a particular feature should compose its root level based on information gain assessments. Hyperparameters, on the other hand, are used to control the learning process. Taking the same example about decision trees, you could specify the maximum allowed depth of the tree (regardless of the training data). Hyperparameter tuning is a very important topic in the exam and will be covered in fine-grained detail later on.

Once the model is trained, you can evaluate and review the results in order to propose the next steps. If the results are not acceptable (based on business success criteria), you should go back to earlier steps to check what else can be done to improve the model's results. It could either be the subtle tuning of the hyperparameters of the algorithm, a new data preparation step, or even the redefinition of business drivers. On the other hand, if the model quality is acceptable, you can move on to the deployment phase.

In this last phase of the CRISP-DM methodology, you have to think about the deployment plan, monitoring, and maintenance of the model. You can look at this step from two perspectives: training and inference. The training pipeline consists of those steps needed to train the model, which include data preparation, hyperparameter definition, data splitting, and model training itself. Somehow, you