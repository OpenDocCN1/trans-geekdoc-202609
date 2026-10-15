
The kind of machine learning algorithm you use will be determined by a number of factors such as input data type, desired output data type, and which tool is being used.

Different tools may provide different types of learning algorithms, so you must carefully research the various tools before proceeding. 

If there is a need for training parameters, you will specify them as part of the transformation instructions step.

If using a neural network machine learning model, for example, you must specify a learning rate along with other parameters meant to control how the learning algorithm works.

1.  The Training Process

This is the step during which the training, using your own uploaded training data, occurs. Most machine learning software will ask you to initiate the training process. 

If you have uploaded multiple datasets to the tool, you may be asked to select the dataset to be use for training. Make sure you have labeled your data correctly to ensure that you use the correct training data.

In most machine learning models, the training is iterative. For a neural network model, for example, a number of iterations will be made in order to produce the training model.

## Validation Phase

Validation is an evaluation of a trained model, through the use of another prepared data set, in order to test its generalized ability. Ability is measured in terms of model’s predictive performance and accuracy. 

The validation process will predict the model’s effectiveness for its intended work.

Validation may be used during multiple stages of our model-building process, then:

*   To determine which algorithm produces the best model for our purposes.

*   To determine which fine-tuning of the chosen algorithm produces the best model for our purposes.

*   To determine the predictive/generalized performance of our model.

The accuracy of the model is also important. We must track the number of predictions in order to determine the prediction accuracy of our model.

The more accurate the model, the better. Since we have both the input and target data, we can compare them in order to determine the degree of error. The goal is to minimize the error in your predictive model. However, very often we will need to experiment multiple times with different parameters to get the most accurate model.  

Experimentation is an integral part of the machine learning process. The necessary experimentation is normally accomplished through the fine-tuning of parameters of the model.

If you run an algorithm on the same dataset but using different parameters, you will end up with different models. Our aim is to choose the model with the best performance, so we should come up with a way of ranking the models based on their performance and then choose the best one.

Experimentation may also involve the training of multiple algorithms (on the same data) and a subsequent comparison of resulting models in terms of their computational and predictive performances.

## Application Phase

With training and validation complete, you should have the best model in terms of performance and accuracy. It is now time for you to apply it. This involves introducing new input data to the model, with targets not given. If you have correctly executed the training and validation phases and obtained acceptable results, the results obtained for the uncharacterized data should be accurate as well.

In our earlier example, a model for classifying emails as spam or not spam, if the model adequately differentiated the two during the testing and validation phases, then it should also produce accurate results during the model application phase.

## How to Avoid Common Problems

A number of problems can occur when training, validating and applying a machine learning model. Let us discuss these problems and how one can avoid them.

## How to Avoid Overfitting

Overfitting occurs when our model conforms too closely to our training data interpreting any random fluctuations or noise as relevant to the predictive process and learning them as concepts during the training and validation phases.

These concepts may not be applicable to generalized data, and if not, the model will perform poorly. There are two techniques which can help you avoid over fitting:

1.  Estimate model accuracy using a resampling technique.

2.  Hold back the validation dataset.

Resampling refers to training and validating using varied partitions of our training data. 

The k-fold cross validation is the most popular resampling technique. It involves dividing the training data into k sets, of which, for each of k iterations of training and validation, a different one of the k sets is reserved for validation and the other K-1 sets are used for training. Predictive error will be computed for each iteration, allowing a much more accurate estimate of expected predictive performance of the machine learning model on generalized data.

A validation dataset refers to a subset of training data which one holds back from the machine learning algorithms to the end of the project. After selecting and tuning the machine learning algorithm on training dataset, the learned model can be evaluated on the validation dataset so as to gain an insight into how it will perform on unseen data.

## How to Avoid Underfitting

Underfitting is the failure of a model to adequately model even the provided training data. The model cannot be used to identify or capture the underlying pattern or trend in a dataset. 

It has poor performance on the training data; hence it isn’t a suitable model.

The remedy to this problem is use a different machine learning algorithm. Simple machine learning models should also be avoided.

## How to Avoid Dirty Data

Dirty data refers to data containing missing values, inconsistencies and noise. Such data has a negative effect on the training, validation and application of machine learning models.

To avoid dirty data, adequate filtering must be implemented. Presence of duplicates of data should also be avoided as this may cause inconsistencies as you will not be sure or certain which data set is the most accurate one.

If you are obtaining all or part of your data from outside sources, be sure that you have verified their processes for ensuring that their data is clean.

Because dirty data may also result from typing errors, you should have a reliable, dedicated data entry person to key data into your systems.

## Data Sampling & Splitting

When it comes to training a machine learning model, it is always best to use the largest possible amount of data. Relying on only a few observations will not give you a good model for prediction. Use of a small data set to train a model will give you a simple model, which can lead to the problem of under fitting. To avoid this, ensure that your training data includes as many observations as possible.

Data normalization is very essential. This should only be done if you realize that there are some inconsistencies in your data. If some of your data values are outside the desired range, normalizing them will improve the algorithm’s learning. 

In machine learning, the dataset should be divided into two sets, the *learning or the training set* and the *validation or test set*.

However, this must be done with great care so as not to introduce systematic differences between training and testing.

For example, you should not reserve the first half of the data as the test data, since it is possible the data might be chronological, or ordered by provider. 

We don’t want to risk biasing our training and test data in any way. The best way to avoid systematic differences is to select the data randomly when creating the *learning* and the *test* sets.

The purpose of the test data set is to help us assess our final model and determine its ability to predict. The test data also helps us make the best decision when it comes to choosing the best machine learning model to use for prediction.
