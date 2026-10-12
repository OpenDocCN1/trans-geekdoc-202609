
## Building a Bayesian Network

### 1. Identify Variables and Dependencies

*   Identify the variables of interest for building the Bayesian network. Domain knowledge and expertise play a crucial role in selecting relevant variables.
*   Understand the relationships and dependencies between variables, which can guide the network's structure.

### 2. Structure Learning

*   Determine the network's structure by learning the probabilistic dependencies between variables from the data.
*   Methods such as constraint-based algorithms or score-based algorithms can be used for structure learning.

### 3. Parameter Estimation

*   Estimate the CPTs for each node in the network. This involves calculating the probabilities of each variable, given its parent variables.
*   Maximum likelihood estimation (MLE) or Bayesian parameter estimation can be used for parameter estimation.

### 4. Model Evaluation and Validation

*   Split the data into training and testing sets for model evaluation.
*   Use appropriate model fit metrics to evaluate the model performance on the test set.

### 5. Model Interpretation and Visualization

*   Interpret the Bayesian network's structure to understand the relationships and dependencies between variables.
*   Visualize the network graphically to aid in model interpretation and communication.

### 6. Inference and Predictions

*   Perform probabilistic inference using Bayes’ theorem to compute the probabilities of specific events or variables, given evidence (observed data).
*   Use the Bayesian network to make predictions or decisions based on the inferred probabilities.

### 7. Model Refinement and Iteration

*   Refine the Bayesian network by making adjustments to the structure or parameters based on feedback, domain knowledge, or additional data.
*   Iterate through the process to improve the model performance and ACC.

It's important to note that constructing a Bayesian network requires a combination of domain knowledge, data analysis, and expert judgment. The iterative nature of the process allows for continuous refinement and improvement of the model ACC and performance. I developed a more general process for the so-called causal mining. It is the USELEI process. I will present this process later in this chapter.

## Differences Between Bayesian Network and Frequentist Statistics

![](images/ufig16_10.jpg)

Bayesian network methods and frequentist methods are two different approaches to statistical inference. It is important to understand these differences because you are likely much more familiar and experienced with frequentist statistics (even though you may not have heard of this term before).

So, what is frequentist statistics? Frequentist statistics, also known as frequentist inference, is a statistical framework and approach to data analysis that focuses on the concept of repeated sampling and long-run frequencies of events. The name comes from the method's emphasis on analyzing the frequency or proportion of events occurring in repeated experiments or observations. In frequentist statistics, the key idea is that probabilities are interpreted as limiting frequencies. It treats the parameters of a statistical model as fixed and unknown quantities that do not have probability distributions. Instead, the focus is on estimating these fixed parameters using observed data and making inferences based on the observed frequencies. Essentially, the statistics-based methods we covered earlier, including linear regression, logistic regression, cluster analysis, principal components, and other statistical methods you may be familiar with (such as t-tests, analysis of variance [ANOVA], multivariate analysis of variance [MANOVA], and discriminant analysis), are all frequentist statistics.

Since frequentist statistics focuses on frequencies rather than probability distributions, it differs from Bayesian networks. [Table 16.2](#chapter16.xhtml#tbl16_2) highlights the key differences between these two methods.

**TABLE 16.2 Differences between Bayesian Networks and Frequentist Statistics** [Return to text.⏎](#chapter16.xhtml#b16tbl16_2)

| Items | Bayesian Networks | Frequentist Statistics |
| :--- | :--- | :--- |
| Philosophy | Bayesian networks view probability as a measure of subjective belief or degree of uncertainty, incorporating prior knowledge and updating it based on observed data using Bayes’ theorem. | Frequentist methods consider probability as the long-run frequency of an event occurring over repeated trials, focusing solely on the properties of the observed data. |
| Handling uncertainty | Bayesian networks explicitly model and reason uncertainty by assigning prior probabilities to uncertain quantities and updating them based on observed data. | Frequentist methods do not directly incorporate prior beliefs or quantify uncertainty but rely on the concept of sampling variability and estimate parameters based solely on observed data. |
| Parameter estimation | Bayesian networks estimate parameters by specifying prior probabilities and updating them with observed data to obtain posterior probabilities. The posterior distribution reflects the combined information from the prior knowledge and data. | Frequentist methods estimate parameters using techniques such as maximum likelihood estimation, which aims to find the parameter values that maximize the likelihood of the observed data. |
| Inference | Bayesian networks provide a framework for probabilistic inference, which enables the computation of various probabilities of interest, such as posterior probabilities, conditional probabilities, and predictions. | Frequentist methods focus on point estimation and hypothesis testing. They provide estimates and tests based on the observed data without quantifying probabilities directly. |
| Sample size | Bayesian networks can handle small sample sizes effectively by incorporating prior knowledge into the analysis. Prior information can act as a regularizer, helping to stabilize estimates and avoid overfitting. | Frequentist methods typically require larger sample sizes for reliable estimation and hypothesis testing due to their reliance on observed data. |
| Interpretability | Bayesian networks provide a natural framework for interpreting results in terms of probabilities, making it easier to communicate uncertainty and make informed decisions based on the posterior distribution. | Frequentist methods tend to focus more on correlation estimates and p-values, which can sometimes be misinterpreted or lead to binary decisions without explicit consideration of uncertainty. |

## Bayesian Network and Causal Inference

![](images/ufig16_11.jpg)

One common question when implementing the Bayesian network method is whether it allows for making causal inferences based on the results. As previously discussed, Bayesian networks provide valuable insights into the dependencies and conditional relationships between variables. They represent causal relationships through probabilistic relationships. However, it's important to understand that Bayesian networks alone cannot establish strict causality without prior domain knowledge or a theoretical foundation. While they do not explicitly prove causation, they can infer causal relationships based on the probabilistic dependencies modeled in the network. Let's explore this further.
