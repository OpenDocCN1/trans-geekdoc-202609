
## 6.3.3.3 Isomap

- Isomap restores the intrinsic geometrical structure for high-dimensional data in lower-dimensional spaces via Multi-dimensional Scaling (MDS).
- Graphically, it represents data points as nodes and similarities as edges.
- Then, computes the shortest distance between them using specific algorithms or spectral techniques.

## 6.3.3.4 Auto-encoder

- A system that uses ANNs.
- Consists of an encoder network that maps input data to a lower-dimensional latent space and a network of decoders that reassembles the input data from the latent space representation.
- Reduces dimensionality and compresses data.

## 6.4 Semi-supervised Learning

- Aims to enhance the accuracy of the learning algorithm by utilizing the extra information present in unlabeled data.
- Useful in situations where acquiring labeled data is costly or time-consuming.
- Encompasses many approaches that may be used to address data-driven challenges, including SVM, self-training, graph-based techniques, co-training, and generative models.

### 6.4.1 Self-training

- Generates predictions on labeled data is first trained using the labeled data.
- Predicted labels that have a high level of confidence are then included in the labeled dataset.
- Undergoes retraining using the enhanced labeled dataset, and this process continues until convergence is achieved.

### 6.4.2 Co-training

- Entails training several models or perspectives on distinct subsets of characteristics or depictions of the data.
- At first, every model is trained using the labeled data.
- Share reliably predicted labels on the unlabeled data with one another.
- The models undergo retraining using the supplemented labeled data, and this procedure is repeated frequently.

### 6.4.3 Graph-based Methods

- Represents the data instances as nodes in a graph, where edges represent correlations between instances.
- Utilizes the graph structure to propagate label information from labeled to unlabeled nodes through the graph.
- Label propagation algorithms, such as label spreading or label propagation, are commonly used in this approach.

### 6.4.4 Semi-supervised Generative Models

- Integrates unsupervised and supervised learning by including latent variables to represent the underlying data distribution.
- Generative adversarial networks (GANs) or variational autoencoders (VAEs) are capable of generating realistic data samples and predicting labels for labeled instances concurrently.

### 6.4.5 Semi-supervised Support Vector Machines

- Semi-supervised SVMs extend traditional SVMs by incorporating unlabeled data to enforce a smoother decision boundary.
- Enhances classification performance by leveraging the margin between decision boundaries depending on the nature of the data.
- Availability of labeled data.
- The specific learning task at hand.

## 6.5 Reinforcement Learning

- Framework where an agent acquires the ability to make choices through repeated environmental interactions.
- The agent is provided with rewards or penalties as feedback, which are determined by the state it transitions into and the activities it does.
- The agent's goal is to acquire a strategy or policy that maximizes the total reward it gets over some time.

### 6.5.1 Continuous Reinforcement

- Continuous reinforcement learning involves an action space characterized by a continuum of values, allowing actions to span a range within a continuous domain.
- Commonly implemented in tasks where actions are not confined to distinct choices but can instead encompass any value within a specified series.

### 6.5.2 Categorical Reinforcement

Categorical reinforcement learning pertains to tasks where discrete actions are drawn from a finite set of categories.

Provokes the agent to select from a predefined set of actions, where actions could correspond to specific moves or denote choices of items to recommend.

## 6.6 Real-World Applications of Machine Learning Algorithms in Reproductive Health

### 6.6.1 Puberty

The study conducted by Pan et al. (2019) employed multiple ML algorithms to create prediction models. These models were designed to address nonlinear interactions between features, determine feature importance, and provide good interpretability. The researchers utilized Extreme Gradient Boosting (XGBoost) due to its effectiveness in training a sequence of models to minimize errors and its scalability. They also used Random Forests to handle nonlinear data and ensure robustness to noise. The study conducted by Pan et al. (2019) used SVMs and Decision Trees to assess the performance of ensemble models vs nonensemble models. This analysis provided useful insights into the connections between input variables and the output gonadotropin-releasing hormone analogue (GnRHa) test findings in girls with presumed central precocious puberty.

### 6.6.2 Menstrual Cycle Tracking

The study conducted by Yu et al. (2022) revealed that the integration of wearable devices and algorithms for ongoing monitoring of health data might potentially enhance the chances of successful conception in women. The research used a range of ML methodologies, which were implemented and shown using Python. The algorithms were developed using basal body temperature and heart rate data acquired directly from participants. Their performance was assessed based on evaluation metrics and parameters. The objective was to forecast the fertile period and menstruation in individuals with both consistent and inconsistent menstrual cycles. In addition, the researchers (Yu et al., 2022) examined the incorporation of physiological parameters, such as the variability of the low-frequency to high-frequency ratio and normal-to-normal intervals, into predictive models.

### 6.6.3 Family Planning

Kebede et al. (2023) used a range of ML techniques to identify the main factors contributing to the lack of access to family planning services among women in Ethiopia. The selection of these algorithms was based on their distinct strengths and weaknesses to thoroughly analyze and select the most optimal model for predicting this occurrence. The Random Forest technique has the highest accuracy rate of 85%, with an AUC (area under the curve) value of 0.93. The study identified many key factors associated with insufficient resources for family planning, including rejection from husbands/partners, women's educational attainment, geographic region, previous childbirth in a healthcare facility, financial position, and household size (Kebede et al., 2023).

### 6.6.4 Contraceptive Use

ML algorithms and iterative thematic analysis (ITA) were employed to identify the factors influencing the use of intrauterine devices (IUDs) among married women in India. This approach provided valuable insights into the variable constructs derived from a set of regularized models (Dey et al., 2022). The Lasso Logistic Regression method was used to determine the key predictors of IUD usage. This technique reduces the coefficients of extraneous variables to zero, thereby removing unrelated variables from the dataset. This results in a more concise and focused input dataset. Ridge Logistic Regression was used to mitigate multicollinearity among the variables by including a regularization factor in the regression equation. The neural network used variables or characteristics with non-zero coefficient estimates from Lasso as input units, with women's usage of IUD as the output. This was done to consider nonlinear correlations among the predictors. The findings were then compared to those obtained using the iterative theme categorization technique. The algorithms' analysis revealed that several factors strongly influenced the use of IUDs among married women in India. These factors included shared family goals, utilization of family planning services, intention to have or not have children, wealth, education, access to counseling, and availability of maternal and child healthcare services.

### 6.6.5 Unintended Pregnancy

The researchers used several ML methods to forecast instances of unplanned pregnancies among married women in Bangladesh (Hossain et al., 2022). The Elastic Net Regression algorithm demonstrated superior performance in accurately classifying unintended pregnancies and their subsequent interventions among married couples in Bangladesh, achieving an impressive AUC of 74%. Furthermore, it identified age, education, wealth status, and contraceptive intention as the primary factors influencing the occurrence of these pregnancies.

### 6.6.6 Assisted Reproductive Technology

The method used to evaluate individual treatment effects for improving trigger injection time for in vitro fertilization (IVF) results was a T-learner with bagged Light Gradient Boosting Machine (LightGBM) base learners. The technique was selected due to its capacity to handle categorical and continuous covariates, capture nonlinear relationships, efficiently process huge datasets, and consider nonlinear interactions between input variables. The analysis included a range of patient characteristics and stimulation settings. The primary objective was to use ML to assist in making crucial decisions during IVF procedures. This might potentially lead to improved clinical outcomes by optimizing the yield of fertilized oocytes (2PNs) and the total number of viable blastocysts obtained from a specific cohort of stimulated follicles. Hariton et al. (2021) showed that using algorithms to aid doctors in making choices during IVF treatment may lead to a rise of
