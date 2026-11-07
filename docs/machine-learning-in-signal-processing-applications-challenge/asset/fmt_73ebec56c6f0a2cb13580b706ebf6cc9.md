
In a classification problem, the output variable is a category. It involves assembling the data into classes. In an organization, if a person has to be given the appraisal, classification is used to know whether or not he would be the best appraisal taker. Two types of classification called binary classification and multiple classifications are considered. In binary classification, supervised learning algorithm labels input data into two distinct classes. Dividing data into more than two classes is termed as multiple classifications.

### 3.2.2 Regression Problems

In a regression problem, the output variable is an actual value. In regression, with the use of training data, a single output value is generated. These data are a probabilistic clarification, which is determined after seeing the strong point of association among the input data. Regression helps to predict the house price centered on its size, locality, etc. Recommendation and time-series prediction are the general types of difficulties built on top of cataloguing and regression. The discrete values of output data based on a group of independent variables are termed as logistic regression. This process can thrash when performing with nonlinear and numerous decision boundaries. It has no flexibility enough to arrest complex associations in datasets.

Few examples of supervised-machine learning algorithms are as follows:

* For solving regression problems, usage of linear regression.
* For solving classification and regression problems, usage of random forest.
* For solving classification problems, usage of support vector machines.

In the presence of a supervisor, supervised learning involves the usage of machine learning algorithms. Proper guidance in a proper direction gives proper feedback in the process; hence, it is termed as learning under supervision. Supervised learning goes through the reference of various categories of methods \[[11](#ch03.xhtml#r3_11), [12](#ch03.xhtml#r3_12), [13](#ch03.xhtml#r3_13) and [14](#ch03.xhtml#r3_14)\]. Training or teaching an algorithm uses information data and guiding a model by means of labels related with the data. Being humans, consumption of more information or data takes place, but noticing of these data points doesn’t happen. When an image of a bird is shown, it is instantaneously known what the bird is centered on previous involvement. The scenario changes if the learner doesn’t instantaneously identify the bird.

When the learner brands a guess and forecasts what the bird might be, it shows an opportunity to quantitatively appraise the learner for correct or wrong answer. It is likely because it has the correct labels of input.

Machine learning algorithm is commonly referred to as the model. If the model is giving a correct response, then there is nothing to do. The work comes into picture only when the response of the model is incorrect. The work is to exact the model when the response of the model is incorrect.

If the scenario continues, the model needs to be updated with necessary changes. If the hen image is shown, it recognizes it in a correct way. The presence of the input variable `x` and the output variable `y` and usage of algorithm help to learn the representing function w.r.t the input and output. The output `y` is shown as a dependent variable of input `x` as represented in equation 3.2.

`Y = f(x)`

(3.2)

Approximation of the mapping function (`f`) leads to the prediction of the output variables (`y`) through the input data `x` ([Figure 3.4](#ch03.xhtml#f3_4)).

![FIGURE 3.4 Approximating the mapping function \[see Ref. 15\].](images/Fig03_04.jpg)

[**FIGURE 3.4**](#ch03.xhtml#f3_4b) Approximating the mapping function \[see [Ref. 15](#ch03.xhtml#r3_15)\].

### 3.2.3 Examples of Supervised Learning

The machine learning model learns to fit planning between the examples of input topographies with their related labels. When models are proficient with these examples, usage of new forecasts on unseen data is done.

The forecast labels can be both numbers and categories. For example, if the prediction of house fare is taken, then the yield is a number which gives rise to regression model. If we are forecasting if an e-mail is spam or not, the yield is a category giving rise to classification model \[[16](#ch03.xhtml#r3_16), [17](#ch03.xhtml#r3_17) and [18](#ch03.xhtml#r3_18)\].

> **Example: House Prices**
>
> Prediction of house fare is a bigger task which includes the process of machine learning. The information or properties which depict the complete information about the houses are number of rooms, square footage, features, whether a house has more rooms, and so on. The corresponding labels can be known by leveraging data coming from the numerous houses, their features, and prices. Hence, training a supervised machine learning model predicts a new house’s fare based on the previous examples perceived by the model.
>
> **Scenario: a Cat or a Dog?**
>
> In the computer vision field, image classification is an important issue. The intension is to forecast which class an image fits to. Among several problems, the aim is to find the class label of an image. Does the image indicate an image of a cat or a dog?
>
> **Scenario: Weather Condition?**
>
> Considering various parameters forecasting weather in a specific location is a tough task. To do right forecasts for the weather, it is necessary to take into account numerous parameters as well as historical temperature data, precipitation, wind, and humidity. It is seen to be an interesting and very challenging issue required in developing the right answer by developing composite supervised models that comprise multiple tasks. Forecasting temperature every time is a reversion problem, in which the output labels are unremitting variables. By divergence forecasting it, is it successful to know snow or not is a binary classification problem?
>
> **Example: Text Classification**
>
> The data points are considered as meaningful structure and patterns in the annotations. Unsupervised learning is generally exploited for finding significant patterns and groupings innate in data, mining generative features, and investigative purposes \[[19](#ch03.xhtml#r3_19),[20](#ch03.xhtml#r3_20)\].

## 3.3 Unsupervised Learning Method

In an unsupervised method, the input data `x` will be present, and the corresponding output variables will be absent. In some pattern recognition glitches, the training of data consists of a set of input vectors `x` without any of the consistent target values. The intension of unsupervised learning glitches may be to find groups of redundant examples within the data, which is termed as clustering, or to find how the data is spread in the space, called density estimation

The aim of unsupervised learning is ideal to the fundamental construction or distribution in the data suitable to learn about the data. It has different characteristics compared to supervised learning as it does not have educator or supervisor. Algorithms are permitted to realize its plans by bestowing the interested structure in the information.
