
![](img/46a7ed74d391bf69db3c36e9484e1be4_151_0.png)

FIGURE 6.4 Architecture of data mining.

## 6.5 MACHINE LEARNING (ML) TECHNIQUES FOR DIGITAL FORENSIC

The process of discovering algorithms that have improved as a result of data-driven experience is known as ML. The process of creating, examining, and developing algorithms that allow machines to learn with no need for human involvement is known as algorithm development. ML and DM are both part of data science, making sense considering that they both use data. Many people unintentionally use the phrases interchangeably because both approaches are used to address complex problems, given the fact that ML is occasionally used to undertake useful DM (Mohri et al., 2018). Data from DM, on the other hand, can be utilized to train machines.

Furthermore, both processes employ the same fundamental data pattern detection algorithms. ML teaches a computer how to learn and interpret the parameters that are given to it, whereas DM is used to derive rules from massive amounts of data. Figure 6.5 shows the relationship between AI, statistics, DM, and ML.

![](img/46a7ed74d391bf69db3c36e9484e1be4_152_0.png)

FIGURE 6.5 Relationship between AI, DM, ML, and statistics.

Without being explicitly designed, ML allows a machine to learn from data, improve performance based on previous experiences, and predict future events. ML algorithms create a mathematical model using past data samples, referred to as training data, which helps them make judgments or predictions without being explicitly programmed. The life cycle of ML is a cyclical method for designing and implementing a successful ML project. The primary goal of the life cycle of ML is to find a solution to the problem (Ashmore et al., 2021). Figure 6.6 depicts the seven major steps in the ML life cycle.

Collecting data is the first phase in the life cycle process of ML. Data could be collected from different sources, including mobile devices, the internet, databases, and files. Therefore, we must first find the various data sources. The output’s efficiency will be determined by the quality and quantity of the data collected. The more data there is, the more accurate the prediction will be. This process entails: (a) identifying multiple data sources; (b) collecting data; and (c) combining data from diverse sources. Next, we must prepare the data for further processing after it has been collected. Data preparation comprises storing our data in the right place and preparing it for ML training. That whole phase will get categorized into two different sections. They are Data exploration and data pre-processing.

Data wrangling is the stage of converting and cleaning unstructured and raw data into a useful format. It is the method for extracting data, picking a variable to use, and converting the data into a format appropriate for analysis in the next phase. The data has been cleaned and formatted and is now ready for analysis. This process entails: (a) choosing analytic approaches; (b) creating models; and (c) analyzing the results. The goal of this step is to create a ML model that will analyze data using various analytical approaches and then assess the results. The model is then trained, which involves increasing the model’s performance in order to reach a better solution to the problem. Next, the model is trained to utilize data sets, which are then utilized for training the model using various ML approaches. Finally, we test the developed ML model once it has been trained on a specific data set. The test data is feed into the developed model and make it ensure that it is rightly working.

![](img/46a7ed74d391bf69db3c36e9484e1be4_153_0.png)

FIGURE 6.6 Life cycle of machine learning process.

### 6.5.1 CLASSIFICATION OF MACHINE LEARNING (ML) ALGORITHMS

The ML algorithms are categorized into four different groups. They are (a) regression under supervised learning; (b) classification under supervised learning; (c) dimension reduction under unsupervised learning; and (d) clustering under unsupervised learning. Regression falls under the topic of supervised learning and includes techniques such as linear regression, decision trees, and so on. The classification under the supervised learning category includes various algorithms such as Linear SVM, Naive Bayes, and decision tree types. The category of unsupervised learning-dimension reduction methods includes techniques such as principal component analysis and latent Dirichlet analysis. Finally, there are numerous algorithms described under the Unsupervised learning – clustering domain. They are primarily utilized in applications that make use of clustering. Among these are K-means, K-nodes, and Gaussian mixture models (Raj et al., 2021; Priyadarsini et al., 2020). Figure 6.7 shows the detailed classification of various ML algorithms.

![](img/46a7ed74d391bf69db3c36e9484e1be4_154_0.png)

FIGURE 6.7 Detailed classification of different machine learning algorithms.

In the algorithms mentioned above, a few important algorithms like K-NN algorithm, support vector machine (SVM) are mainly used in digital forensics.

### 6.5.2 K-NN ALGORITHM

The K-NN (Nearest Neighbor) algorithm is a simple and effective ML algorithm based on supervised learning (Khan et al., 2018). This approach considers that the new and old data are similar, and it assigns the new case to the category that is closest to the current categories. Thus, the K-NN approach saves all available data and categorizes new data points depending on their similarity to the current data. It means that by utilizing the K-NN approach, fresh data can be swiftly sorted into a well-defined category. Although this method can be used for both regression and classification, it is most typically employed for classification. Figure 6.8 explains the K-NN algorithm.

![](img/46a7ed74d391bf69db3c36e9484e1be4_155_0.png)

FIGURE 6.8 K-nearest neighbor algorithm.

The working of the K-NN algorithm is explained in the following steps:

- Choose the number K of the neighbors;
- Calculate the Euclidean distance between K of your closest neighbors;
- Based on the Euclidean distance, select the K closest neighbors;
- Count how many data points there are in each category among the k neighbors;
- Assign the newly acquired data points to the category with the most neighbors;
- Finally, our test machine learning model is getting ready.

The K-NN approach is simple to implement and robust to noisy training data. As a result, it may be more successful if the training data is large. However, the main downside of this method is that it requires continual determination of the value of K, which might be challenging at times. Furthermore, the calculation cost is high because it takes time to calculate the distance between data points for all training samples.

### 6.5.3 SVM ALGORITHM

The support vector machine (SVM) algorithm is another important and most frequently used algorithm in many recent machine-learning-based applications. It’s a supervised ML algorithm that can handle regression and classification tasks. However, it is mostly used to tackle classification problems. The value of each feature is the value of a specific coordinate in the SVM methodology, and each data item is represented as a point in n-dimensional space (Zhao et al., 2020), where n is the number of distinct features. Then we locate the hyper-plane that clearly separates the two classes to complete classification. Figure 6.9 shows the graphical representation of the SVM algorithm.

Both linearity and non-linearity input can be classified using the SVM method. It starts by mapping each data point through an n-dimensional attribute vector, with n denoting the total number of attributes. The hyperplane that divides these data components into two groups is then found, with the minimum separation for both categories maximized and classification errors reduced. The selection hyperplane’s length and the class’s neighboring occurrence define the least closeness for a grouped class. Each feature vector is first displayed as a point in an n-dimensional space, with each feature’s value corresponding to a specific coordinate. To finish the categorization, we must first find the hyperplane that divides the two categories by the greatest distance.
