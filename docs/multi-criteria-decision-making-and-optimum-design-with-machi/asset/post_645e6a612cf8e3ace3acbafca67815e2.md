
![](img/62c36bee0e5ae6b397770e7de372b0e7_285_0.png)

FIGURE 19.2 Flow chart of the model development process.

### 19.4.1 DATA REQUIREMENTS

Common supervised learning algorithms include logistic regression, which uses the logistic function to model a binary variable, and naïve Bayes classifier; naïve Bayes is rooted in Bayes’ theorem, which provides full freedom to agents. A common unsupervised learning technique is hierarchical clustering, which creates a hierarchical structure of clusters with the help of any kind of tree. Another is k-Means clustering, which divides data into k different clusters concerning the centroid.

### 19.4.2 DATA PREPARATION

Preparing the data identified errors in the collected data sets, removing missing, invalid, and duplicate values and ensuring that it is properly formatted for modeling.

### 19.4.3 MODEL DEVELOPMENT

We used two distinct data sets for experimentation: one for binary classification (city vs. sell) and another for multiclass classification of cell types. We first developed a custom three-layer convolutional neural network that demonstrated impressive accuracy in binary classification. Then, we pretrained models DenseNet, ResNet, VGG16, and VGG19 for the more intricate task of tumor type classification. Then, we implemented an algorithm.

In this phase, we were determining how the data could be visualized to obtain the required result; we designed and tested all the algorithms in this stage. We used a training set for the prediction systems because this allowed for determining if the system needs to be computed. However, our developed module would help process various data sets by using algorithms available in the interface.

### 19.4.4 MODEL EVALUATION

During this phase we tested the module algorithms to determine the correct analytical approach or method to solve the problem and determine if the model met the initial objective of building the research groundwork. We determined that the model generated the required results.

### 19.4.5 BUILDING THE INTERFACE

The model has a front-end that helps in determining the result. We will establish a connection between the interface and the systems built in historical steps.

### 19.4.6 MODEL DEPLOYMENT

Once the back was complete and the complete model was tested, the model provided at least 90% accuracy and provided different results for deep analytics. We used the following technology stack to design the interface: Node.js, React, MongoDB, Python, Canvas.js. We provided the application with data on 25,000 sales transactions after processing the data using ML models with supervised and unsupervised learning. The front end of the application showed the factors that were being measured with the application: item sales data, sales locations for multiple stores, comparison of algorithms, the accuracy of the model, and server performance while processing data.

### 19.5 RESULTS AND DISCUSSION

The user selects unsupervised learning and from unsupervised learning as shown in Figure 19.3. After the user has selected both algorithms, the user can move forward to compare the models.

## Select Algorithm to Compare

| Supervised Learning | Unsupervised Learning |
|--- |--- |
| Logistic Regression | Hierarchical Clustering |
| Naive Bayes Classifier | k-Means Clustering |

FIGURE 19.3 Selection of algorithms for comparison.

## Artificial Intelligence Algorithms for Better Decision-Making

## ITEM SOLD

![](img/62c36bee0e5ae6b397770e7de372b0e7_287_0.png)

FIGURE 19.4 Visualization of the data from the sales data set: a) items sold; b) sales locations.

Figure 19.4a graphically displays the sales item data set, and Figure 19.4b displays the sales locations for the attributes. Visualization helps the user gain a different understanding of the data.

Attributes and other details from the data are shown in Table 19.1. We used 5,000 records with 15 attributes per record, and we found 95% accuracy with a 95% confidence interval. Figure 19.5 shows the model accuracy before (a) and after (b) data is provided to the model; accuracy increases as more data is provided.

We also compared the per-user deviation within the models, graphed in Figure 19.6.

## Multi-Criteria Decision-Making with Machine Learning

We also examined server performance for each model. Because not users performed the experiments using different hardware, the graph in Figure 19.6 shows estimated response times, which we used to determine the hardware required for the specific model. In Figure 19.7, we graphed overall server performance compared with response time. The new interface we developed empirically analyzes different algorithms based on such combinations of parameters, which automatically provides the user with the best algorithm for their data set.

## TABLE 19.1
Attributes and Other Features of the Sample Data

| Store Location | Sale Date | Payment | Customer Email | Gender | Satisfaction | age | Item Bought | Coupon Used |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | London | 4/24/2015 | Online | Instore | beme@ganee.kw | F | 20 | 5 |
| 2 | Denver | 11/6/2013 | Instore | hol@12guami12.li | M | 47 | 5 | 1 |
| 3 | Seattle | 5/30/2013 | Instore | amis@lof.vn | M | 41 | 4 | 8 |
| 4 | Denver | 4/16/2016 | Instore | kiEa@zutbe.ae | F | 46 | 3 | 10 |
| 5 | San Francisco | 8/4/2013 | Instore | fofadoca@alvoog.sv | M | 20 | 5 | 5 |
| 6 | London | 10/25/2013 | Instore | beme@ganee.kw | F | 49 | 9 | 9 |
| 7 | Seattle | 12/26/2017 | Instore | zoz@awjaw.to | M | 57 | 4 | 9 |
| 8 | Seattle | 11/26/2017 | Instore | fi12@lu.jo | F | 27 | 4 | 9 |
| 9 | Denver | 1/11/2015 | Online | kofa112ub@duwar.mo | F | 31 | 4 | 2 |
| 10 | Austin | 3/31/2013 | Instore | ga@siw.sr | M | 65 | 3 | 5 |

![](img/62c36bee0e5ae6b397770e7de372b0e7_288_0.png)

**FIGURE 19.5** Mean predictions from the data.

## Artificial Intelligence Algorithms for Better Decision-Making

259

![](img/62c36bee0e5ae6b397770e7de372b0e7_289_0.png)

FIGURE 19.5 (Continued)

![](img/62c36bee0e5ae6b397770e7de372b0e7_289_1.png)

FIGURE 19.6 Deviation in values.

### 19.6 CONCLUSION

The algorithms we compared in the research for this chapter provide enough information to determine what could be expected from the model. We compared one supervised and one unsupervised learning based on attributes provided to the algorithm. The interface we developed provided empirical analysis on the following factors: attributes, data visualization, mean sales prediction, model accuracy and deviation from real values. The proposed interface provides better accuracy for decision-making.

## Multi-Criteria Decision-Making with Machine Learning

## SERVER PERFORMANCE

![](img/62c36bee0e5ae6b397770e7de372b0e7_290_0.png)

FIGURE 19.7 The performance of the tested servers.

Based on our experiment and analyses, we concluded that the proposed system allows for the desired analysis of data sets in machine learning. This research will save time for researchers seeking the optimal algorithms for analyzing their data sets. New features can be added per end-user requirements and remain as a future scope.

## REFERENCES

Boutabba, R., Salahuddin, M.A., Limam, N. et al. (2018). A Comprehensive Survey on Machine Learning for Networking: Evolutions, Applications and Research Opportunities. J Internet Serv Appl., vol. 9, no. 16. https://doi.org/10.1186/s13174-018-0087-2.

Duns, G., Hamen, M. C., Ouquaima, K., & Vasslev, V. (2024). A Comprehensive Analysis of the Role of Artificial Intelligence and Machine Learning in Modern Digital Frontiers and Incident Report. Forensic Scientific Intelligence: Digital Navigation, vol. 48, p. 301675, ISSN 2666-2817. https://doi.org/10.1016/j.fsidi.2023.301675.

Ganesh Keshekare, P. K., Prasanthi, K., Godla, S. R., Rachuti, V., Al Ansari, M. S., & El-Yubary, Y. A. B. (2023). Optimizing Network Security and Performance through the Integration of GAN-RNN Models in SDN-based Access Control and Traffic Engineering. International Journal of Advanced Computer Science and Applications (IJACSA), vol. 14, no. 12. http://doi.org/10.14569/IJACSA.2023.0214262.

Gonalves, A. R., Pinto, D. C., Shuqair, D., Martins, Mattila, S. (2024). Artificial Intelligence vs. Autonomous Decision-Making in Streaming Platforms: A Mixed-Method Approach. International Journal of Information management, p.102748, ISSN 0268-0412, https://doi.org/10.1016/j.ijinfomgt.2023.102748.

Gustavo, N., Mbunge, E., Belo, M., Fasotho, S. G., Pronto, J. M., Metful, A. S., Carvalho, L. C., Akinwusu, B. A., & Shiremba, T. R. (2022). Emphasizing the Digital Shift of Hospitals toward Personalization: Application of Machine Learning.
