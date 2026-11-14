
## E.7 Exercise

### E.7.1 Suggested Activities

*   **E.7.1.1** Use the `Weka` tool for spam filtering using the `naïve Bayes` classifier. Use the spam base data set, which can be obtained from the `UCI machine learning repository`.
*   **E.7.1.2** Design a business application using the `Bayesian framework`. Outline the assumptions made.
*   Take an example of university results and formulate at least five aspects using the `naïve Bayes` classifier. Clearly state any assumptions made.
*   **E.7.1.4** Design a business application using the `Bayesian network` having at least seven nodes and seven edges. Outline the assumptions made.
*   **E.7.1.5** Design a healthcare application using the `Bayesian network` having at least seven nodes and seven edges. Outline the assumptions made (including `CPTs`) and all inferences possible. Implement the application using `Python`.

### E.7.2 Multiple Choice Questions

Give answers with justification for correct and wrong choices:

*   **E.7.2.1** `Gaussian distribution` is associated with a
    1.  `S shaped curve`
    2.  `Q shaped curve`
    3.  `Bell shaped curve`

*   **E.7.2.2** `____` uses probability to model data and quantify uncertainty of predictions.
    1.  `Linear regression`
    2.  `Bayesian learning`
    3.  `SVM`

*   **E.7.2.3** `____` of a hypothesis reflects any background knowledge or evidence we have about the chance that `h` is a correct hypothesis.
    1.  `Prior probability`
    2.  `Post probability`
    3.  `Marginal probability`

*   **E.7.2.4** `Likelihood` is the
    1.  `Marginal probability of data`
    2.  `Conditional probability of an observation`
    3.  `Posterior probability of a hypothesis`

*   **E.7.2.5** `Bayesian decision theory` is the basis of
    1.  `SVM`
    2.  `Logistic regression`
    3.  `Expectation maximization algorithm`

*   **E.7.2.6** Finding the hypothesis `h` that maximizes the likelihood of the data `d` for a given hypothesis `h` and the prior probability of `h` is called
    1.  `Maximum a posteriori (MAP)`
    2.  `Maximum likelihood (ML)`
    3.  `Maximum prior (MP)`

*   **E.7.2.7** The method by which the posterior `p(class|data)` directly which is then used to make predictions of class for new values of `x` is called a
    1.  `Generative model`
    2.  `Probabilistic model`
    3.  `Discriminative model`

*   **E.7.2.8** An important assumption that the `naïve Bayes` method makes is that
    1.  All input attributes are conditionally independent
    2.  All input attributes are conditionally independent
    3.  All input attributes are conditionally dependent

*   **E.7.2.9** A `Bayesian network` is a graphical model that efficiently encodes
    1.  The conditional probability distribution for a large set of variables
    2.  The joint probability distribution for a large set of variables
    3.  The prior probability distribution for a large set of variables

*   **E.7.2.10** If the problem is defined as the probability of the cause given the symptom, it is called
    1.  `Prediction`
    2.  `Classification`
    3.  `Diagnosis`

*   **E.7.2.11** The conditional probability table (`CPT`) of a node
    1.  Is given for each value of each of its parents
    2.  Is given for each value of each of its children
    3.  Is given for each value of each of its siblings

*   **E.7.2.12** Given the following figure,
    ![](images/figu7_4_B.jpg)
    1.  `C` is independent of `D` given `A` and `B`
    2.  `D` is independent of `A` and `B` given `C`
    3.  `D` is independent of `C` given `A` and `B`

*   **E.7.2.13** Given the following figure,
    ![](images/figu7_5_B.jpg)
    1.  `A` is dependent on `B` given `C`
    2.  `A` is dependent on `B` given `D`
    3.  `A` is independent of `B` given `C`

*   **E.7.2.14** Given the figure,
    ![](images/figu7_6_B.jpg)
    1.  Knowing `C` or `D` makes `A` and `B` independent
    2.  Not knowing `C` or `D` makes `A` and `B` independent
    3.  Not knowing `C` or `D` makes `A` and `B` dependent

*   **E.7.2.15** Fitting a model containing all `p` predictors using a technique that constrains or regularizes the coefficient estimates towards zero is called
    1.  `Convergence`
    2.  `Shrinkage`
    3.  `Gradient descent`

*   **E.7.2.16** The `logistic regression` uses a
    1.  `Bell shaped function`
    2.  `S shaped function`
    3.  `Spiked function`

### E.7.3 Match the Columns

| No. | Term | Key | Description |
| --- | --- | --- | --- |
| E.7.3.1 | `Posterior probability` | A | States that given its parents, a random variable `X` is conditionally independent of its nondescendants |
| E.7.3.2 | `Maximum likelihood estimate` | B | Choosing a higher degree polynomial as a model |
| E.7.3.3 | `Generative models are used for` | C | Require initial knowledge of many probabilities |
| E.7.3.4 | `Naïve Bayes` | D | `Bayesian learning` |
| E.7.3.5 | `Text classification based on naïve Bayes` | E | The probability of the symptom given the cause |
| E.7.3.6 | `Prediction is defined as finding` | F | Assume that all hypotheses are equally likely a priori |
| E.7.3.7 | `Bayesian network is associated with Markov condition` | G | Probability of observing the conjunction of attributes is equal to the product of the individual probabilities |
| E.7.3.8 | `Bayesian networks` | H | Vector space representation to represent documents |
| E.7.3.9 | `Lead to overfitting.` | I | Is a classification model |
| E.7.3.10 | `Logistic regression` | J | Modelling observations drawn from a probability density function |

### E.7.4 Problems

*   **E.7.4.1** Ram is a `CS 6310` student; recently his mood has been highly influenced by three factors: the weather (`W`), his study habits (`S`), and whether his friend talks to him (`F`). Predict his happiness (`H`) based on these factors, given observations in the table shown.
    ![](images/figu7_7_B.jpg)
    On a new day when weather is `Good`, `S = Pass`, and `F = No talk`, predict the student’s happiness using a `naïve Bayes classifier`. Show all calculations.

*   **E.7.4.2** Given the following table, find if the car will be stolen if it is `yellow` in colour, is a `sports car`, and is of `domestic` origin. Show all calculations.
    ![](images/figu7_8_B.jpg)

*   **E.7.4.3** Given the following table,
    ![](images/figu7_9_B.jpg)
    Given New Sample `X'` = {Weather = `Winter`, Housing = `Bungalow`, Company = `Friend`, Weekend = `Yes`}, find whether `Barbeque` is yes or no.

*   **E.7.4.4** In a medical study, 100 patients all fell into one of three classes: `Pneumonia`, `Flu`, or `Healthy`. The following database indicates how many patients in each class had `fever` and `headache`. Consider a patient with a `fever` but no `headache`.
    ![](images/figu7_10_B.jpg)
    1.  What values would a `Bayes optimal classifier` assign to the three diagnoses? (A `Bayes optimal classifier` does not make any independence assumptions about the evidence variables.) Again, your answers for this question need not sum to 1.
    2.  What values would a `naïve Bayes classifier` assign to the three possible diagnoses? Show your work. (For this question, the three values need not sum to 1. Recall that the `naïve Bayes classifier` drops the denominator because it is the same for all three classes.)
    3.  What probability would a `Bayes optimal classifier` assign to the proposition that a patient has `Pneumonia`? Show your work. (For this question, the three values should sum to 1.)
    4.  What probability would a `naïve Bayes classifier` assign to the proposition that a patient has `Pneumonia`? Show your work. (For this question, the three values should sum to 1.)
