
**Table 12.4 Applications and related data mining techniques. Adapted from Shi, Wang, and Fang [SWF20].**

| Applications | Key Data Mining Techniques |
| :--- | :--- |
| Education | Random Forests<br>Logistic Regressions |
| Public Health | Long Short-Term Memory (LSTM)<br>Autoencoder<br>Deep Clustering |
| Combating Information Manipulation | SVM with RBF Kernel Function<br>Markov Random Field (MRF)<br>Graph Attention Network (GAT) |
| Social Care and Urban Planning | Gradient Boosting Decision Trees<br>AdaBoost<br>Transfer Learning |
| Public Safety | Generalized Linear Model (GLM)<br>Naive Bayes (NB) |
| Transportation | Demand and Supplier Modeling<br>Multiagent Reinforcement Learning |

shown to be effective to detect rumors on social media; a multimodal transfer learning method called FLORAL has been developed that is capable of transferring semantically related dictionaries between different cities and enriching feature representations of a target city with knowledge from the source city; generalized linear models including logistic regression have been used to forecast civil protests from multiple data sources such as tweets, news, and blogs; and multiagent reinforcement learning framework has been developed to model the complicated and high-dimensional dynamics between demands and supplies on ride-sharing platforms.

The key challenges of data mining for social good come from the following aspects. First (data scarcity), it is usually difficult to collect large-scale data from real scenarios, which could impair the performance of supervised data mining methods. To tackle this challenge, researchers have used unsupervised learning or transfer learning in some current efforts. Second (evaluation), since the primary goal of data mining for social good is to address real-world problems with significant societal consequence, standard evaluation metrics alone might be insufficient. It is important to develop application domain-specific evaluation metrics. Third (human-in-the-loop), domain experts such as social workers and doctors have many critical knowledge and experiences that should be leveraged to further improve the data mining methods. Hence, how to seamlessly incorporate such human knowledge into the data mining process and build effective interactions between humans and algorithms is another important research challenge. Fourth (sustainable deployment), the ultimate goal of data mining for social good is to develop models that could be deployed in real-world sustainably. However, only a few of the current projects have completely achieved this goal. The reasons include the willingness of collaborating partners and the status of funding.

## Bibliographic notes

Abernethy et al. [ACF+18] develop ActiveRemediation to detect pipes made of hazardous metal. They combine XGBoost with a hierarchical Bayesian spatial model to estimate the probability that a pipe contains hazardous materials and use Importance Weighted Active Learning to select homes for inspection. Lakkaraju et al. [LAS+15] develop a method to identify students who need intervention to graduate high school on time. They present a comprehensive comparison of various data mining models such as Random Forests and AdaBoost on data collected from real scenarios. Baytas et al. [BXZ+17] develop Time-Aware LSTM (T-LSTM), which is able to handle irregular time intervals in patient records. Combining T-LSTM with the autoencoder, they introduce an unsupervised approach that can group patients only by their historical records. Adhikari, Xu, Ramakrishnan, and Prakash [AXRP19] design a novel deep learning approach called EpiDeep that learns embeddings from the historical data to predict the future trend of the epidemic. With the learned embeddings, EpiDeep is capable of finding the closest historical seasons to the current season that improves the performance and interpretability. Fan et al. [LYYY12] employ the SVM classifier with RBF kernel function to detect rumors on a micro-blogging platform. Rayana and Akoglu [RA15] develop a novel approach, SpEagle, to detect spam reviews based on metadata (text, timestamp, rating) and relational data (review network). SpEagle supports both the unsupervised and semisupervised setting, and the performance could be boosted significantly with only limited labeled data. Wei, Zheng, and Yang [WZY16] develop a multimodal transfer learning method called FLORAL to tackle the data insufficiency challenge in urban computing task. FLORAL was evaluated on the air quality prediction problem and exhibits superior performance on data from real scenarios. Avvenuti et al. [ACM+14] propose an emergency management system, EARS, to discover meaningful tweets about outbreaking crisis events such as earthquakes. With careful design of feature extraction and detection rules, EARS is capable of detecting earthquake events with a relatively low false positive and alert interested parties in time. Ramakrishnan et al. [RBM+14] develop the EMBERS system, which aims at forecasting civil protests from multiple data sources such as tweets, news, blogs, and other sources.

A variety of data mining models such as logistic regression and generalized linear models has been employed to make predictions for data from different sources, and these predictions are fused to generate final results. Lin, Zhao, Xu, and Zhou [LZXZ18] propose a multiagent reinforcement learning framework to model the complicated and high-dimensional dynamics between demands and supplies on ride-sharing platforms. With a proper design of action, reward, and state, the framework obtains efficient coordination between different agents in the dynamically changing environment.

## Mathematical background

### Notation naming convention

Unless otherwise stated, we use bold upper-case letters for matrices (e.g., **A**), bold lower-case letters for vectors (e.g., **u**), and lower-case letters for scalars (e.g., c). Regarding matrix indexing conventions, we use rules similar to Numpy. We use **A**[i, j] to represent the entry of matrix **A** at the ith row and the jth column, **A**[i, :] to represent the ith row of matrix **A**, and **A**[:, j] to represent the jth column of matrix **A**. We use superscript $^T$ to represent the transpose of a matrix (i.e., **A**$^T$ is the transpose of matrix **A**) and the superscript plus sign to represent the pseudo-inverse of matrix (i.e., **A**$^+$ is the pseudo-inverse of matrix **A**).

#### A.1 Probability and statistics

##### A.1.1 PDF of typical distributions

For a continuous random variable, its probability density function (PDF) is a function whose value at any given sample is the relative likelihood that the random variable would equal that sample. Any PDF $f(x)$ must satisfy two conditions: (1) $\forall x, f(x) \ge 0$ and (2) $\int_{-\infty}^{+\infty} f(x)dx = 1$. Some PDFs of typical distributions are listed as follows:

- **Uniform Distribution**: $X \sim U(a, b)$, where $a < b$. The mean value of this distribution is $(a + b)/2$ and the variance is $(b - a)^2/12$. The PDF of a uniform distribution is as follows:

```
f(x) = \begin{cases} \frac{1}{b - a}, & a < x < b \\ 0, & \text{others.} \end{cases}
```

- **Exponential Distribution**: $X \sim E(\lambda)$, where $\lambda > 0$. The mean value of this distribution is $1/\lambda$. The variance of this distribution is $1/\lambda^2$. The PDF of an exponential distribution is as follows:

```
f(x) = \begin{cases} \lambda e^{-\lambda x}, & x \ge 0 \\ 0, & \text{others.} \end{cases}
```

- **Normal Distribution**: $X \sim N(\mu, \sigma)$, where $-\infty < \mu < \infty$ and $\sigma > 0$. The mean value of this distribution is $\mu$. The variance of this distribution is $\sigma^2$. The PDF of a normal distribution is $f(x) = \frac{1}{\sqrt{2\pi}\sigma} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$.

- **Gamma Distribution**: \( X \sim Ga(\alpha, \beta) \), where \( \alpha > 0 \) and \( \beta > 0 \) are parameters. The mean value of this distribution is \( \alpha/\beta \). The variance of this distribution is \( \alpha/\beta^2 \). The PDF of a gamma distribution is \( f(x, \beta, \alpha) = \frac{\beta^\alpha}{\Gamma(\alpha)}x^{\alpha-1}e^{-\beta x}, x > 0 \), where \( \Gamma(\alpha) = \int_0^\infty t^{\alpha-1}e^{-t}dt \) is the Gamma function.

- **Beta Distribution**: \( X \sim B(a, b) \), where \( 0 < x < 1, a > 0 \) and \( b > 0 \). The mean value of this distribution is \( a/(a+b) \). The variance of this distribution is \( ab/((a+b)^2(a+b+1)) \). The PDF of a beta distribution is \( f(x, a, b) = \frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}x^{a-1}(1-x)^{b-1}, a > 0, b > 0 \), where \( \Gamma(\cdot) \) is the Gamma function.

##### A.1.2 MLE and MAP

Maximum Likelihood Estimation (MLE) and Maximum A Posteriori (MAP) are two statistical methods for estimating parameters. We have the observed data points \( X = \{x_i\} \), which satisfies the \( i.i.d. \) (independent and identically distributed) condition. The target for both MLE and MAP is to find the best parameter \( \theta \).

In MLE, we assume that there exists a true fixed parameter \( \theta \). The process to obtain \( \theta \) is as follows:

```
\(\theta_{MLE} = \arg \max_\theta P(X|\theta)\)
\( = \arg \max_\theta \prod_i P(x_i|\theta). \tag{A.1}\)
```

Usually, we use the logarithm form for the above equation as follows:

```
\(\theta_{MLE} = \arg \max_\theta \log P(X|\theta)\)
\( = \arg \max_\theta \log \prod_i P(x_i|\theta) \)
\( = \arg \max_\theta \sum_i \log P(x_i|\theta). \tag{A.2}\)
```

For MAP, it regards \( \theta \) as a random variable. By Bayes' rule, we have

```
\( P(\theta|X) = \frac{P(X|\theta)P(\theta)}{P(X)} \)
\( \propto P(X|\theta)P(\theta). \tag{A.3}\)
```

Therefore

```
\(\theta_{MAP} = \arg \max_\theta \log P(X|\theta)P(\theta)\)
\( = \arg \max_\theta \log \prod_i P(x_i|\theta)P(\theta) \)
\( = \arg \max_\theta \sum_i \log P(x_i|\theta) + \log P(\theta). \tag{A.4}\)
```

We can see that the difference between MLE and MAP is the final term \( \log P(\theta) \), which represents the prior distribution of the parameter \( \theta$.
