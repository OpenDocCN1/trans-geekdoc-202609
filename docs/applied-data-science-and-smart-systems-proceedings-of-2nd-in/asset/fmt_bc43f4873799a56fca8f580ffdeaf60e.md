
The admission predictor first takes all the required values from the user who wants to check their admission probability. These inputs are divided into four sections which are personal details (name, age, e-mail, country), academic details (CGPA, work experience, number of papers published), GRE scores (AWA, Quant, verbal), TOEFL/IELTS score (reading, writing, listening, speaking). After which, based on these values the best model will predict the probability of getting admitted into a specific university selected by the user.

## 4.1 Algorithms used in each subdomain

### a. Logistic regression (LR)

Logistic regression (LR) is a statistical technique employed in binary classification tasks. It estimates the probability of an input sample being associated with a specific class using a logistic function. In the context of graduate admission prediction, LR can be utilized to model the likelihood of an applicant being admitted or rejected based on the input features (`[Sulock et al., 2009](#ch1.xhtml#ref1_16)`). It enables the prediction of admission outcomes based on the learned probabilities, aiding in the decision-making process for admission committees.

### b. Support vector machine (SVM) classifier

Support vector machine (SVM) is a managed ML algorithm utilized for both binary and multi-class organization tasks (`[Andris et al., 2016](#ch1.xhtml#ref1_17)`). It identifies an optimal hyperplane that effectively separates data points of distinct classes in a feature-rich space. In the context of graduate admission prediction, SVM can be employed to categorize applicants as admitted or not admitted based on the contribution landscapes. Leveraging the discriminative capabilities of SVM, enables accurate classification of applicants, aiding in the prediction of admission outcomes.

### c. K-nearest neighbors (KNN)

K-nearest neighbors (KNN) procedure is a nonparametric algorithm that can be used for organization and reversion tasks. It assigns labels to a new data point by finding the KNN in the feature space and assigning the label that appears most frequently among the k neighbors (`[Nunsina et al., 2020](#ch1.xhtml#ref1_18)`). In the context of graduate admission prediction, KNN can be rummage-sale to classify new applicants into different categories based on the resemblance of their features to those of the labeled samples. The value of k is an important hyperparameter that can significantly affect the performance of the KNN algorithm (`[R. Gill et al., 2020](#ch1.xhtml#ref1_9)`). A higher value of k results in a smoother decision boundary but may lead to misclassification of some points, while a lower worth of k can lead to over fitting and high alteration in the predictions.

### d. Decision tree (DT)

The decision tree (DT) algorithm is a straightforward and interpretable method that recursively partitions the information into subsections based on the standards of input landscapes and allocates a lesson label to each foliage node. In the context of graduate admission, it provides a clear method to model the decision-making process and identify key characteristics for prediction (`[Pandey et al., 2013](#ch1.xhtml#ref1_20)`). The DT is an effective tool for prediction and explanation because it provides significant insights into the variables that affect the admission outcome by evaluating its splits and leaf nodes.

### e. Random forest (RF)

The Random forest (RF) algorithm, a collaborative knowledge technique, combines the predictions of various DTs to increase prediction reliability and accuracy (`[Batool et al., 2021](#ch1.xhtml#ref1_21)`). It does this by randomly selecting a subset of features and generating the final forecast. The accuracy of forecasts is increased in the context of graduate admission prediction by the ability of RF to capture complex interactions between input features.

### f. Gradient boosting (GB)

Gradient boosting (GB) is a particular type of collaborative learning algorithm that builds numerous weak learners in turn, each one seeking to correct the errors made by its forerunners (`[Saidani et al., 2022](#ch1.xhtml#ref1_22)`), and creates a final forecast by merging all of the learners’ predictions. By iteratively improving the predictions based on the errors produced by earlier models, GB can increase the accuracy of forecasts in the context of graduate admission prediction.

### g. XGBoost

The GB algorithm is implemented in XGBoost, which is well-known for its effectiveness, scalability, and speed. In applications where performance and scalability are crucial, it excels at processing huge datasets (`[Asselman et al., 2021](#ch1.xhtml#ref1_23)`). XGBoost can be used in the context of graduate admission prediction to produce precise forecasts while quickly processing and analyzing enormous volumes of data. When it comes to graduate admission prediction tasks, where accuracy and scalability are crucial factors, it excels in performance and efficiency.

### h. AdaBoost (AB)

A well-known EL approach called AB iteratively modifies the weights of samples that were incorrectly classified in order to increase the precision of succeeding models (`[ElDen et al., 2013](#ch1.xhtml#ref1_24)`). The findings of all the models are combined to get the final projection. When employed in the context of graduate admission prediction, AB can be utilized to boost prediction accuracy by giving misclassified applicants more weight in later rounds. For graduate admissions problems, this adaptive technique can improve prediction accuracy and help the model forecast more accurately. To avoid plagiarism and keep the intended meaning while still creating original content, sentences might be rephrased.

### i. Bagging classifier

The bagging classifier is an EL method that averages or votes among the predictions made by various base classifiers to get the final prediction. By utilizing the combined output of several base classifiers, it is a strategy that may be used in graduate admission prediction to reduce over fitting and improve the accuracy of predictions. The model may become more robust and generalizable as a result of this technique of combining the predictions of various classifiers, leading to predictions for graduate admission problems that are more precise. Original content must be produced by rephrasing sentences in order to prevent plagiarism and ensure that the information is presented in a distinctive manner.

## 4.2 Data collection techniques

The research paper focuses on the data collection process for graduate admission prediction from various websites of the top 20 US Colleges/Universities named “Arizona State University, Boston University, Georgia Institute of Technology, New Jersey Institute of Technology, University of North Carolina, North Carolina State University, New York University, Purdue University, University of California, University of Cincinnati, University of Texas, University of South Florida, University of Maryland, Carnegie Mellon University, Texas A&M University, University of Illinois, University at Buffalo, Columbia University, University of Washington, University of Michigan”, for admission in computer science. The paper outlines the steps of web scraping and data extraction, data validation, organization, and storage while ensuring compliance with ethical and legal considerations. Various attributes of data were the CGPA, course name, work experience, number of research paper written, GRE score, IELTS/TOFEL score, etc. The collected data will be used to develop predictive models and provide insights into the factors influencing graduate admissions in computer science programs, offering valuable implications for students and aspirants who want to study abroad.
