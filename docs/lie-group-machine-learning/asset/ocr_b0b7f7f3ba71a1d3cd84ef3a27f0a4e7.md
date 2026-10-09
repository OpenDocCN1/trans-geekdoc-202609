**Algorithm 8.1: Self-training algorithm processing**

**Input:** feature set $V$; training has been marked sample set $L$; unmarked sample set $U$; Self-training cycle number $T$, sample confidence threshold $T_w$

For $t = 1, 2, \dots, T$

(1) Using the annotation sample set $T$ to train the classifier $C$ on the feature set $V$;

(2) Use the classifier $C$ to predict all unlabeled samples $u \in U$, calculate their predictive confidence, determine whether $T_w$ is greater than $T_w$, if less than $T_w$, discard the forecast;

(3) Add a higher confidence sample to the trained marker set $L$.

End for

**Output:** classification result and final classifier $C$.

Note that the classifier uses its own predictions to learn; hence, this process is called self-teaching or bootstrapping. To avoid a classifier in order to eliminate its errors, some algorithms try to use the method in which unmarked points are not learnt if the confidence is lower than a threshold value. In general, EM algorithms with the generation of mixed models can be seen as a special case of soft self-training. Self-training has been used for real-world natural language processing tasks. Yarowsky (1995) used self-training to disambiguate word meanings, e.g., the determination of whether the word ‘plant’ refers to an ‘organism’ or a ‘factory’ in a given context [9].

The advantage of self-training lies in its simplicity. It is a wrapping algorithm that takes advantage of existing classifiers; however, early errors are enhanced, resulting in poor algorithm performance.

# 8.1.1.2 Generative model algorithm

Generative models are commonly used for semi-supervised learning. It is assumed that the model satisfies the probabilistic condition $p(x, y) = p(y)p(x|y)$, where $p(x|y)$ is a recognisable mixed distribution, such as a Gaussian mixture model. This algorithm uses the generative model as a classifier, treating the probability that a large number of unmarked data belongs to each category as a set of missing parameters. Then, maximum likelihood estimation (MLE), maximum a posteriori estimation (MAP), or the Bayes algorithm is used to estimate the makers and model parameters, so that the mixed components can be determined. In ideal cases, the mixed distribution can be fully determined using only a marked example of a component. This algorithm can be seen to cluster around a small number of marked data, which is similar to a previous method that directly uses clustering assumptions.

For semi-supervised classification, the generative model can describe the identified categories that the data points belong to, rather than identifying the category by estimating the joint probability distribution of the data points. Commonly generated models include Gaussian distribution, Gaussian mixture model, EM algorithm (commonly used in image classification), polynomial distribution, naive Bayes model (e.g., EM algorithm and commonly used in text classification), and hidden Markov models