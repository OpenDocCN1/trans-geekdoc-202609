
survey summarizing papers that serve as base references, offering a brief overview of implemented techniques. On the other hand, ensemble techniques involve integrating predictions of multiple models to benefit from the superior predictive power of some models; typical methods include gradient boosting and random forests. Deep learning approaches using multilayer neural networks have attracted a lot of attention as they have the capability to learn complex patterns from data automatically.

### 2.1 Traditional Methods

Lakshmi et al. [1] aimed to protect expectant mothers from impending difficulties by assessing their health and keeping an eye on them throughout the course of their pregnancy. Using a C4.5 decision tree and the previously specified rules from the decision tree, the researcher suggests a hybrid framework. The judging panel filled up a scale and used the relevance score to justify feature selection. The final anticipated rule set is then added to the forecast, yielding a 98.5% accuracy rate.

Tiwari et al. [2] employed various techniques to forecast Covid-19 pandemic trends, such as decision tree, Naïve Bayes, Support Vector Machine (SVM), and Linear Regression. The research tries to produce reliable forecasts in the face of uncertainty by evaluating real-time worldwide data on confirmed cases, recoveries, fatalities, and active cases. When it comes to predicting Covid-19 trends, Naïve Bayes seems to be very successful, exhibiting lower Mean Absolute Error (MAE) and Mean Squared Error (MSE). This work establishes a standard for epidemic prediction and highlights an opportunity of machine learning in preemptive responses to pandemics, despite remaining uncertain. Figure 2 gives an extensive examination of traditional machine learning algorithms and their applications.

![](img/a797255277085a0fa8aa2736cb720e31_250_0.png)

### 2.2 Ensemble Methods

Singh et al. [3] developed an ensemble learning method for predicting stillbirths and miscarriages using data from rural areas. This approach combines Adaboost, Random Forest, bagging, and boosting algorithms with a voting classifier, resulting in an accuracy rating of 82%. This method can significantly contribute to preventive health management by identifying potential pregnancy difficulties early on and emphasizing maternal wellness. Song et al. [4] analyzed several characteristics to develop forecasting models for double-high illnesses using artificial intelligence approaches. The study utilized real testing data and the LightGBM and XGBoost algorithms to build these models. Five important biological markers were selected to convert unprocessed data into mathematical vectors. The efficiency of the suggested model in the early diagnosis of cardiovascular and cerebrovascular disorders was demonstrated by the mean square error (MSE) used to measure the efficacy of the prognosis algorithms following logarithmic conversion of the predicted and actual values.

### 2.3 Deep Learning Methods

Wang et al. [5] aimed to investigate the potential of convolutional neural networks (CNNs) in predicting the likelihood of spontaneous miscarriage through the analysis of early ultrasonography embryonic sac pictures. Predicting the course of a pregnancy when the initial fetal cardiac activity is detected is a difficult task, but precise forecasting is essential for obstetricians to provide relevant advice and establish the routine for ultrasound exams. Biswas et al. [6] created prediction models using six sample deep learning and ensemble algorithms: Random Forest (RF), XGBoost, Back Propagation Neural Network (BNN), Decision Tree (DT), Support Vector Machine (SVM), and Logistic Regression (LR). Sensitivity was selected as the assessment criterion, and the prediction accuracy of each method was evaluated in both scenarios, that is, with and without FHR taken into account. This approach aimed to evaluate the importance of similar traits in samples of continuing pregnancies and early pregnancy loss (EPL) cases. Figure 3 is a detailed description of the neural network model to illustrate the functioning of a deep learning algorithm.

![](img/a797255277085a0fa8aa2736cb720e31_251_0.png)

Fig. 3. Description of the neural network model to signify the working of a deep learning algorithm.

## 3. Preliminaries

Decision Tree: A powerful pillar in the supervision-based learning toolbox, the Decision Tree may be applied on Regression and Classification tasks both. It creates the structure as the hierarchical tree, internal node for feature testing, branch for test result and leaf as class label which holds the prediction value. The tree is built over successive data splits relating to the attribute value creating this complex structure from data used to train it in a recursive manner until it reaches predefined stopping criteria such as minimum node size or max tree depth. Decision Trees technique selects the feature which is best for data splitting at each step of its construction (Tree building is greedy), using metrics like entropy or Gini impurity to measure the purity of the sets.

**Random-Forest:** The Name Random-Forest is derived from Random (Random Decision Forest) + (Forest of Random Trees). It is a supervised machine learning algorithm in the field of Machine Learning (Ensemble Learning) used in solving the classification and regression problem [7]. This could mean simply simulating a forest of trees—and the more trees (or forests) there are, the more resilient it is! In parallel to this, adding more trees to a Random Forest Algorithm also can increase its intelligence and thus its capability to solve a task. It is an ensemble classification method in which a group of tree-based decisions are formed, each of which is based on the other database segments. The total mean of these decisions is then increased to increase the anticipated efficiency of the dataset [8]. Microsoft's LightGBM is another well-liked open-source distributed system for precision, scalability, and effectiveness. Decision trees have outstanding model performance and a good memory overhead. LightGBM accomplishes this by integrating bleeding-edge features such as Gradient-based One-Side Sampling (GOSS), which removes samples during training with small gradients, to both vastly reduce memory usage and to speed the training portion. Additionally, it employs some histogram-based techniques to better create trees quickly. To enhance the model sparsity and reduce the number of iterations, LightGBM leverages the structure of histogram where all leaves (to form a single tree) are at the same level so that the calculation can be done

![](img/a797255277085a0fa8aa2736cb720e31_252_0.png)

Fig. 4. Representative structure of classical and advanced tree algorithm.

level-wise, converting the tree structure to level or leaf wise, the benefit of which will be discussed in common parameter realization of gradient boosting tree structure section [9]. Figure 4 is a comprehensive depiction of the structure of both classical and advanced tree algorithms.

## 4. Methodology

A machine learning model that uses traditional and state-of-the-art tree techniques to predict miscarriage in pregnant women is presented. This data set has a lot of characteristics and is very much needed for the accurate prediction. LightGBM uses a conventional tree-based algorithm, the decision tree and random-forest algorithm, with the aid of a comprehensive method. LightGBM to increase accuracy of our process. Figure 5 is a visualization that shows the steps for the Data source gathering → Data Preparation → Suggested LightGBM model using traditional methods like RandomForest and Decision Trees and finally, the comparison has been made to achieve higher accuracy.

![](img/a797255277085a0fa8aa2736cb720e31_253_0.png)

### 4.1 Data Preprocessing

The dataset of the study was precisely selected from a government website in order to maintain a high standard of validity and reliability in the results. At first, the dataset was analyzed using traditional decision tree techniques such as random forest analysis and conventional decision tree. Figure 6 is an elaborate flowchart to help illustrate the true phases of data preprocessing. All the stages that would be used in the generation of raw data for analysis, starting with structured data collection through
