
The ideal gold standard test offers 100% sensitivity and specificity. In practice, however, a gold standard test is less accurate. For example, to diagnose a brain tumor, you can perform a biopsy or an MRI. A biopsy test is regarded as the gold standard for diagnosing a brain tumor, but since the MRI test is less accurate but a practical substitute, it’s regarded as an “imperfect gold standard” or an “alloyed gold standard” ([Spiegelman, Schneeweiss, McDermott 1996](#bibliography.xhtml#b_9781547401567-016_ref_073)). Gold standard tests vary over time for each disease as the state-of-the art methods of diagnostic tests improve over time.

### 9.3 Vote-based Schema

A *voting approach* selects the final results based on majority vote on a specific accuracy dimension or result category. For example, if the goal is to minimize FN, then you must consider a voting schema that produces the lowest FN among the four models on a given new case data set. The voting schema works as follows: Run all four models on the new data set. Select the lowest FN count, or select a weighted sum of models that produce the lowest FN+FP count.

A hybrid schema can work by defining a relative preference ratio. The assumption is that models with more correct predictions are preferred over the other models. The relative preference of a model is determined by the number of correct predictions minus incorrect predictions. This schema was used for Ensemble #1. The mathematical representation of schema for Ensemble#1 is shown in (79) and (80). This ensemble assumes *n* data cases and *K* models in the ensemble:

```
(79) model j score = \sum_{i = 1}^{n}(correct predictions - incorrect predictions)
(80) W_{j} = \frac{model\; j\; score}{\sum_{i = 1}^{K}{model\; i\; score}}
```

As shown in this equation, the intent is to find the weights according to the ratio of preference for a model that provides higher accuracy (lower FN count).

### 9.4 Accuracy-based Ensemble Schema

An accuracy-based ensemble seeks to find a weighted sum of algorithms that minimize error. For example, if the intent is to find the lowest FN, you can define the error for each validation case as follows. Let’s assume that *T[i]* is the truth of a particular validation case, and *p[ij]* is the prediction rendered by algorithm *j* for case *i*. Also assume that there are a total of *K* different algorithms. Ensemble #2, attempts to increase the number of the TP count by defining the number of errors for each model *j*:

Then you can define the total error count by:

```
\varepsilon_{j} = \sum_{i = 1}^{n}\varepsilon\left( {p_{ij}\ , T_{i}} \right)
```

where *ε*(*p*[*i**j*], *T*[*i*]) equals to 1 if *p[ij]* does not match the truth *T[i]*, or equals zero if prediction matches the truth.

Then you can define the weight of algorithm *j* for ensemble #1 with the goal of increasing the quantity of TP. Assuming that the total number of TP from a model *j* is shown by *TP[j]*, it’s possible to define the weights by:

```
W_{j} = \frac{(TP_{j})}{\sum_{j = 1}^{m}{(TP_{j})}}
```

For ensemble#3, you can define the weight of algorithm j with the goal of reducing the quantity of FN error:

```
W_{j} = \frac{{(\varepsilon_{j})}^{- 1}}{{\sum_{j = 1}^{K}{(\varepsilon_{j})}}^{- 1}}
```

In this framework, two ensembles, Ensemble#2 and Ensemble#3 use an accuracy-based scheme to determine the weights. The results are discussed and compared in Chapter 5.

### 9.5 Diversity-based Schema

The accuracy-based weighted sum formulation exclusively relies on accuracy to compute the weights. However, it could be argued that accuracy is not the only factor that affects ensemble performance. The diversity-based schema measures the extent to which the predictions by one model are distinguishable from predictions by other models. The diversity-based schema increases the robustness performance of the ensemble. Said differently, this ensemble assigns higher weight to the model with higher prediction diversity because it offers higher ensemble robustness. Let’s assume that *n* data sets are employed to train and validate all *k* models. You can compute a prediction error term *u[j]* to correspond to the uniqueness of the model *j*:

```
\theta[j] = (p[j1] - T[1], ..., p[jn] - T[n])
```

Given k algorithms, it’s possible to define the error vector of *θ*[1], *θ*[2], ..., *θ*[*K*]. The diversity of the *j*th model can be computed as the sum of the Euclidean distances between the vector *θ*[*j*] and all other error vectors, defined by:

```
D_{j} = \sum\limits_{i = 1;j \neq i}^{K}\theta_{j} - \theta_{i}
```

The prediction diversity determines how a model’s result is distinguishable from those of other models. Let’s compute a normalized weight *w[j]* for the *j*th model in the ensemble by:

```
W_{j} = \frac{D_{j}}{\sum_{i = 1}^{K}D_{j}}
```

Ensemble#4 uses diversity-based schema.

### 9.6 Optimization-based Schema

One proposal in this book is to define the oracle (meta-classifier) as an optimization model. The optimization-based schema can take into account both the accuracy-based as well as the diversity-based weighting scheme to improve accuracy and robustness. This method is adapted from Hu et al. ([Hu, Youn, Wang 2010](#bibliography.xhtml#b_9781547401567-016_ref_032)). In an optimization-based schema you can write Equation (78) as:

```
(78) minimize \varepsilon\left( {\sum\limits_{j = 1}^{K}(w_{j}p_{ij}),T_{i}} \right)
\sum_{j = 1}^{K}W_{j} = 1., {and} W_{j} \geq 0\; for\; all\; j = 1,\,... K
```

Where *w[j]* is the weight of model *p[j]* and *T[i]* is the expected result for the *i*^(th) data set. The objective function attempts to minimize the difference between the expected result and the weighted sum of each model’s result. Ensemble#5 uses an optimization-based schema. The weights *w[1]*, *w[2]*, *w[3]* and *w[4]* corresponding to each of the four analytical models can be determined according to this optimization-based schema.

# Part III: Case Study—Prediction and Advanced Analytics in Practice

## Chapter 10 Ensemble of Models—Medical Prediction Case Study: Data Types, Data Requirements and Data Pre-Processing

In our case study, the application of prognostics health management (PHM) to human physiological measurement data promises to conceptually deliver several benefits such as:

1. By continuously and iteratively assessing the physiological and biological input data, it can provide predictions and advanced warning of medical complications.
2. A localized prediction tool that incorporates nuances of local populations and clinical environments.
3. Ability to analyze large data sets and provide trained models for prediction.

Continuous and periodic monitoring of key metrics and KPI’s involves collecting historical data from a wide range of internal and external business systems, sensors and streams. The PHM method considers prognostic models built upon prior data from retrospective cases and current data streams in order to make predictions.

Researchers have studied machine learning, classification, adaptive learning methods, and have identified two approaches to machine learning: *programmed* and *concept attainment*. Programmed learning is applicable when the researcher knows the underlying causal relationships in the system and the data.

Concept attainment is an adaptive learning approach where a system learns from an *a priori* set of examples and thus retains concepts from prior data sets. In other words, it learns by classifying patterns in the input data. A concept can be described as a mapping between an input data set and a clinical outcome.

Some interesting research questions arise that merit a full investigation elsewhere, but are discussed briefly here:

1. How much data is adequate for learning to predict a given disease?
