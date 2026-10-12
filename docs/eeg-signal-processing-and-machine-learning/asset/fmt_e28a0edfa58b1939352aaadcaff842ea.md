
# Clustering and Classification in EEG Analysis

## Feature Extraction and Traditional Approaches

Clustering and classification become ambiguous when deciding which features to use and how to extract or enhance those features. Principal component analysis (`PCA`) and independent component analysis (`ICA`) are two very common approaches to extract the dominant data features. Traditionally, a wide range of features (such as various orders of statistics) are measured or estimated from the raw data and used by the machine learning algorithms for clustering or classification.

## Human-Related Signal Classification

In the context of human-related signals, classification of the data in feature space is often required. For example, the power of alpha and beta waves in the EEG signals [[3]](#c07.xhtml#c7-bib-0003) may be classified to not only detect brain abnormalities but also determine the stage of the disease. In sleep studies, one can look at the power of alpha and theta waves as well as appearance of spindles and k-complexes to classify the stages of sleep. As another example, in brain-computer interfacing (`BCI`) systems for left and right-finger movement detection one needs to classify the time, frequency, and spatial features.

## Traditional and Modern Classifiers

Traditional methods based on adaptive filters using mean squared error (`MSE`) or least-squares error (`LSE`) minimizations are still in use. Popular examples of such classifiers are linear discriminant analysis (`LDA`), hidden Markov model (`HMM`), Gaussian mixture model (`GMM`), decision tree [[4]](#c07.xhtml#c7-bib-0004), random forest, and support vector machines (`SVM`). `k`-means clustering and fuzzy logic have also been widely used for clustering, pre-classification, and other AI-based applications [[5]](#c07.xhtml#c7-bib-0005). These techniques have been developed and well explained in the literature [[6]](#c07.xhtml#c7-bib-0006). `DNNs` have become even more popular recently mainly due to their feature learning/extracting capability. For `DNNs` the number of layers and neurons highly depends on the data complexity. Detailed explanation of all these methods is beyond the objective of this chapter. Instead, here we provide a summary of the most popular machine learning methods which have been widely used for EEG analysis.

## Training vs. Explicit Formulae

Unlike many mathematical problems in which some forms of explicit formulae based on a number of inputs result in an output, in data classification there is no model or formulation of this kind. Instead, the system should be generally trained (using labelled data) to be able to recognize a new (test) input.

## Handling Outliers

In the case of data with considerable noise or artefacts, successful classifiers are those which can minimize the effect of outliers. Outliers are the data samples or features very different from the class centres and therefore, they do not belong to any class. In many machine learning algorithms, outliers have destructive effect during the classifier training and increase the cross-validation error. Preprocessing (including smoothing and denoising) can significantly reduce the outliers or their impact. More advanced classifiers are able to reject the outliers during the training phase. Therefore, the right choice of classifiers and their associated feature detection systems can also reduce the influence of outliers.

## Importance of Machine Learning for EEG Applications

Machine learning is important and becoming increasingly popular for EEG applications since:

1.  Where `EEG` is used for `BCI` or integrated within a rehabilitation system, the learning block usually monitors dynamic environments which rapidly change over time. It is therefore desirable to develop systems that can adapt and operate efficiently in such environments.

2.  The increase in the data captured from healthy and diseased persons enables the training of machine learning systems and the detection of new abnormal cases. By looking at distinguishing features of `EEG`s for different brain states and abnormalities, the cases such as seizure and Alzheimer disease can be detected easily subject to availability of moderate amount of `EEG` records.

3.  `EEG` patterns for different brain abnormalities and various brain states are significantly different. In the following chapters some of these patterns are demonstrated. One popular example is sleep `EEG` which shows an obvious shift (from high to low) in normal brain rhythms and the rise of distinguishing waveforms such as spindles and k-complexes. The differences between such diverse patterns can be captured by machine learning systems.

4.  New applications, such as in-patient status monitoring, cyber-physical systems (`CPS`), machine-to-machine (`M2M`) communications, and Internet of Things (`IoT`) technologies, have been introduced with a motivation to support more intelligent decision making and autonomous control [[7]](#c07.xhtml#c7-bib-0007). Here, machine learning is important to extract the different levels of abstractions necessary to perform the AI tasks with limited human intervention [[8]](#c07.xhtml#c7-bib-0008).

5.  `EEG` artefact waveforms have different morphology compared to normal brain rhythms and therefore the corrupted `EEG` segments can be detected and removed by means of classifiers [[9](#c07.xhtml#c7-bib-0009), [10](#c07.xhtml#c7-bib-0010)].

## Limitations of Machine Learning Algorithms

Many machine learning algorithms do not perform efficiently when:

*   the number of features or input samples is high
*   there is a limited time to perform the classification
*   there is a non-uniform weighting amongst features
*   there is a nonlinear map between inputs and outputs
*   the distribution of data is not known
*   there are significant number of outliers
*   the algorithm is not convex (monotonic), so it may fall into a local minima.

## Additional Considerations for EEG Analysis

In addition, in using machine learning for EEG analysis:

*   Online learning or testing within a fully AI framework is feasible mainly due to a low sampling frequency of the signals. The sampling rate for `EEG` processing is often selected between 100 to 1000 Hz.
*   As we deal with a multichannel system, time, frequency, and spatial features can be estimated and incorporated into the machine learning algorithms. This benefits from full signal diversity which introduces more efficiency in the overall learning algorithm and inclusiveness of the feature spaces.

## Nonparametric Techniques and Performance Assessment

For the data with unknown distributions often nonparametric techniques are applied. In these techniques a subset of labelled data is used to estimate or model the data distributions through learning before application of any feature selection or classification algorithm.

To assess the performance quality of the classifiers a multifold cross-validation is performed. For this, only the training data are considered. In each fold a percentage of the labelled data is used to train the classifier and the rest used for testing. The cross-validation error is then calculated as the amount of misclassified data over multiple folds, say `k`-fold.
