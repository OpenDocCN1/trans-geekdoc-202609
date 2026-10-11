
*   [`http://homepages.engineering.auckland.ac.nz/~pkel015/SolidMechanicsBooks/Part_III/Chapter_1_Vectors_Tensors/Vectors_Tensors_15_Tensor_Calculus_2.pdf`](http://homepages.engineering.auckland.ac.nz/~pkel015/SolidMechanicsBooks/Part_III/Chapter_1_Vectors_Tensors/Vectors_Tensors_15_Tensor_Calculus_2.pdf)

*   [`http://cs231n.stanford.edu/vecDerivs.pdf`](http://cs231n.stanford.edu/vecDerivs.pdf)

*   [`https://numpy.org/doc/stable/reference/generated/numpy.einsum.html`](https://numpy.org/doc/stable/reference/generated/numpy.einsum.html)

*   [`https://www.tensors.net/p-tutorial-1`](https://www.tensors.net/p-tutorial-1)

# CHAPTER 4

# Basic Statistics and Probability Theory

Probability theory provides us the mathematical tools to quantify the uncertainty of decision-making where we have incomplete information. In machine learning, uncertainty naturally arises from noisy data or incomplete information about the problem domain. With such given uncertainties, we must come up with a predictive model that can estimate the outcome of an unseen event. There are a range of ML models that are completely built on probabilistic settings, like Bayesian nets, generative models, linear and logistic regression. Most objective functions used in training deep neural net models are derived using a probabilistic framework. However, even before we attempt to quantize the uncertainty in information, we must collect and organize information associated with a given problem. Thereafter, we can draw conclusions and make inferences or predictions based on these data. The science that deals with the collection, organization, analysis, interpretation, and inference of numerical facts or data by applying mathematical theories of probability is known as statistics. Statistics has a wide range of applications in almost every field of study, like medicine, economics, sociology, psychology and astronomy. However, the laws of statistics are true on aggregate of facts and cannot be applied for single observation, that is, statistics does not study individuals. Unlike the laws of physics, the laws of statistics are not exact but are approximate.

## Structure

In this chapter, we will cover the following topics:

*   Basic statistics
*   Probability theory
*   Introduction to Bayesian decision theory
*   Random variable and probability density function
*   Expectation, correlation, and covariance
*   Information theory

## Objectives

Probability theory is one of the foundational pillars of ML and AI, which are one of the applications of inferential statistics. This is the preparatory chapter for understanding inferential statistics and probabilistic interpretation of ML and AI problems covered in the next chapter.

## Basic statistics

The science of collecting, organizing, analyzing, and inferencing from data for the purpose of effective decision-making is called statistics. Statistics has following two major branches:

*   **Descriptive statistics**: Collecting and organizing data
*   **Inferential statistics**: Drawing conclusions from data

Here, `data` can be defined as a collection of facts or information from which conclusions can be drawn. Data can be of various types:

*   **Qualitative (Categorical)**:
    *   **Nominal**: Unordered categorical data like color, gender, location, ethnicity, marital status, weather.
    *   **Ordinal**: Ordered categorical data for example, level of education, economic status, designation in a corporate ladder, knowledge level in a technology.
*   **Quantitative (Numerical)**:
    *   **Discrete**: Integral values that can be finite or countably infinite, like counts of vehicles at a traffic crossing
    *   **Continuous**: Any real value within a defined range, which can be infinite as well; for example, room temperature, blood pressure, height of a person, and stock price
*   **Unstructured**: Text, image, audio, video

Quantitative data can exhibit certain general characteristics. The very first step to study such quantitative data is to compute the `frequency distribution` that graphically represents the number of observations taking a particular value or number of observations in a certain interval. We may observe some larger frequencies for certain values or for certain range of values, that is, a tendency to concentrate at certain values. This is known as `central tendency`. There are various ways to compute this central value, which are collectively known as `measures of central tendency`. The data about the measure of central tendency can vary, and this measure of deviation is called a `measure of dispersion`. The data may show a symmetrical distribution about the central value or show asymmetry. The metrics to measure these degrees of symmetry is called the `measure of skewness`. Also, data may sometimes show a peak at certain central values, and the degree of sharpness of the peak can be measured by `measures of kurtosis`.

Qualitative data can also show central tendency, which is nothing but the most popular category. There are measures of dispersion for qualitative data as well. Unstructured data needs to be converted to structured data, which can be numeric or categorical, before being analyzed further. Text can be viewed as a bag of words where each word is a category. Digital image is a matrix of numeric pixel values.

### Measures of central tendency

There are three types of central tendency measures, which are discussed in detail below.

### Mean

For a set of n observations, ![](images/886.jpg)

*   **Arithmetic Mean** of `S` denoted by ![](images/887.jpg) and defined as ![](images/888.jpg). We call the quantity ![](images/889.jpg) as the *deviation* of the point ![](images/890.jpg) from the point a. Two simple but useful properties of deviation are as follows:
    *   Sum of all deviations about mean is zero or ![](images/891.jpg).
    *   The sum square of deviations is minimum when deviations are computed about the arithmetic mean.

    Proof of 1 is trivial, and we can use differential calculus for 2.

*   **Geometric Mean** of `S` is denoted by `G` and is defined as:

    ![](images/892.jpg)

    For `G` to be well defined, we must have all ![](images/893.jpg). `G` gives comparatively more importance to smaller values and is robust to small fluctuations or noise in data.

*   **Harmonic Mean** of `S` is denoted by `H` and is defined as

    ![](images/894.jpg)

    For `H` to be well defined ![](images/895.jpg). Harmonic mean gives greater importance to small numbers. Like geometric mean `G`, `H` is also not affected by small fluctuations of data.

Among these three means, the arithmetic mean is greater than the geometric mean, and the geometric mean is greater than the harmonic mean.

### Median

The **median** **m** of a dataset is a value that divides the data set in two equal parts such that number of points more than m is the same as the number of points less than m. So, if we have an odd number of points ![](images/896.jpg), we can sort the points and take the middle value m from ordered points with `k` points on either side of m. If n is even, then there are two middle points, and we can take the arithmetic mean of the two. Median is very robust to outliers or extreme values, which may be introduced due to experimental error or mistakes while noting observations or some rare anomaly. Arithmetic mean of data will move toward such extreme values, but median will be robust and does not change in the presence of a few outliers.

### Mode
