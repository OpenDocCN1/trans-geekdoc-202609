# CHAPTER 9 NEURAL NETWORK INTERPRETATION

states that the influence function of the training instance z on the prediction of an instance z_{test} is “how strongly the instance reacts to a change of the model parameters” multiplied by “how much parameters change the instance z”. Another way to reach the formula: Influence is proportional to how large the gradients for the training and test loss are. The higher the gradient of the training loss, the higher its influence on the parameters and the higher the influence on the test prediction. The higher the gradient of the test prediction, the more influential the test. The entire construct can also be seen as a measure of the similarity (as learned by the model) between the training and the test instance.

That is with theory and intuition. The next section explains how influence functions can be applied.

# Application of Influence Functions

Influence functions have many applications, some of which have already been presented in this chapter.

# Understanding model behavior

Different machine models have different ways of making predictions. Even if two models have the same performance, the way they make predictions from the features can be very different and therefore fail in different scenarios. Understanding the particular weaknesses of a model by identifying influential instances helps to form a “mental model” of the machine learning behavior in your mind.

# Handling domain mismatches / Debugging model errors

Domain mismatch is closely related to understand the model behavior. Domain mismatch means that the distribution of training and test data is different, which can cause the model to perform poorly on the test data. Influence functions can identify training instances that caused the error. Suppose you have trained a model for the outcome of patients who underwent surgery. All these patients come from the same hospital. Now you use the model in another hospital and see that it does not work for many patients. Of course, you assume that the two hospitals differ in features. But what are the features or instances that have “broken” the model? Here, influential instances are a good way to answer this question. You take one of the new patients, for whom the model has made a false prediction, and find the most influential instances. For example, this could show that the second hospital has older patients on average and the most influential instances from the training data are-the-are the few older patients from the first hospital and the model simply lacked the data to predict this subgroup well. The conclusion would be that the model needs to be trained on more patients who are in order to work in the second hospital.

# Fixing training data

If you have a limit on how many training instances you can check for correctness, how do you make an efficient selection? The best way is to select the most influential instances, because by definition – they have the most influence on the model. Even if you have an instance with obviously incorrect values, if the instance is not influential and you only need the data