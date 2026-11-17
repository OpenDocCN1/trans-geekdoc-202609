must store all the model artifacts somewhere, since they will be used by the next pipeline that needs to be developed: the inference pipeline.

The inference pipeline just uses model artifacts to execute the model against brand-new observations (data that has never been seen by the model during the training phase). For example, if the model was trained to identify fraudulent transactions, this is the time when new transactions will pass through the model to be classified.

In general, models are trained once (through the training pipeline) and executed many times (through the inference pipeline). However, after some time, it is expected that there will be some model degradation, also known as model drift. This phenomenon happens because the model is usually trained in a static training set that aims to represent the business scenario at a given point in time; however, businesses evolve, and it might be necessary to retrain the model on more recent data to capture new business aspects. That's why it is important to keep tracking model performance even after model deployment.

The CRISP-DM methodology is so important to the context of the AWS Machine Learning Specialty exam that, if you look at the four domains covered by AWS, you will realize that they were generalized from the CRISP-DM stages: data engineering, exploratory data analysis, modeling, and ML implementation and operations.

You now understand all the key stages of a modeling pipeline and you know that the algorithm itself is just part of a larger process! Next, you will see how to split your data to create and validate ML models.

# # Data splitting

Training and evaluating ML models are key tasks of the modeling pipeline. ML algorithms need data to find relationships among features in order to make inferences, but those inferences need to be validated before they are moved to production environments.

The dataset used to train ML models is commonly called the training set. This training data must be able to represent the real environment where the model will be used; it will be useless if that requirement is not met.

Coming back to the fraud example presented in Table 1.1, based on the training data, you found that e-commerce transactions with a value greater than $5,000 and processed at night are potentially fraudulent cases. With that in mind, after applying the model in a production environment, the model is supposed to flag similar cases, as learned during the training process.