
# Employee Churn Management Using AI

# 191

![](img/9665bc5b38d724f414bf1c78dda7410a_211_0.png)

FIGURE 11.13 ROC Curve of Random Forest.

```python
auc_score1 = roc_auc_score(y_test, pred_prob1[:,1])
auc_score2 = roc_auc_score(y_test, pred_prob2[:,1])
print(auc_score1, auc_score2)
```

0.9791176023517265 0.9877824238680089

FIGURE 11.14 ROC Score KNN and random forest.

We have also done the ROC-AUC analysis of XGBoost model to know the performance of the model and we got a relatively good score in comparison to both.
ROC Curve of XGBoost is shown in Figure 11.15.
ROC Score of XGBoost is shown in Figure 11.16.
For XGBoost the AUC score is 0.99403091 which is a good score. We have also plotted a single ROC–AUC graph for all the model under different model.
ROC Curve of KNN random forest vs XGBoost is shown in Figure 11.17.

## 11.5 CONCLUSION

In this chapter, we have used three different Machine Learning algorithms on the employee churn dataset, and observe that XGBoost has better performance in comparison to random forest and KNN. There exist other algorithms and deep learning techniques which can be applied to this dataset to check the performance. We can use different types of hyperparameter tuning methods to get better results. By using this kind of model an organization can keep track of their human resources and which can also help them plan better strategy to keep their assets and collect better performance from the employees. By using AI in HR, it will improve

# Artificial Intelligence and Machine Learning in Business Management

![](img/9665bc5b38d724f414bf1c78dda7410a_212_0.png)

FIGURE 11.15 ROC Curve of XGBoost.

```python
auc_score1 = roc_auc_score(y_test, pred_prob1[:,1])
print(auc_score1)
0.9940309153384559
```

FIGURE 11.16 ROC Score of XGBoost.

![](img/9665bc5b38d724f414bf1c78dda7410a_212_1.png)

FIGURE 11.17 ROC Curve of KNN vs random forest vs XGBoost.

# Employee Churn Management Using AI

193

The HRM system and will result in better performance to the organization in terms of managing their employees. For any organization, a skilled workforce can increase performance and reduce product or service delivery time. Hence, no organization would want to lose those employees, and this is why organizations try to find employee satisfaction and reduce the pressure on their employees. Some organizations create different types of interactive fun based on the work environment so that employees are not under work pressure. At last, we can say that for any employee in any organization, salary, promotion, work pressure and work environment matters to decide whether to stay in that organization or leave. Therefore, to predict these types of behaviour of these employees will hit lot and organization act actively to improve their work culture and other associated activities.

# REFERENCES

- 1. Jauhari, A. "How AI and Machine learning will impact HR practices", News corp Vccle partners summit, 2017.
- 2. Matsa, P. and Gummajji, K. "To study the impact of Artificial Intelligence on Human Resource Management" IRIJET(6), 2019.
- 3. Nunn, J. "Emerging impact of AI on HR" Forbes Technology Council, February 6, 2019.
- 4. Milani, L., et. al. "Exploring the Impact of AI on HRM", London School of Economics, 2017.
- 5. Verma, R., Bandi, S. "Artificial Intelligence & human resources management in Indian IT Sector, Proceeding of 10th International Conference on Digital Strategies for Organizational Success, 2019.
- 6. Ahmed, O., (2018) Artificial intelligence in HR, JRAR December 2018, 5(4) pp 971–978.
- 7. Cappilli, P., Tambe, P. and Yakubovich, V. "Artificial Intelligence in Human Resource Management: Challenges and a path forward" SSRN Electronics Journal, 2018 doi:10.2.139/smm.3263878
- 8. Saklani, P. Sometimes small data is enough to create small product" Harvard Business Review, 2019 available at https://hbr.org/2017/07/sometimes-small-data-is-enough-to-create-small-products
- 9. Pfe, J. and Sutton, R. “Evidence-based Management", 2019. Available at https://hbr.org/2006/01/evidence-based-management
- 10. Meskő, B., Hétényi, G., and Györőfi, Z. “Will Artificial Intelligence solve the Human Resource crisis in healthcare?" BMC Health Services Research, 18(1), 2018.

![](img/9665bc5b38d724f414bf1c78dda7410a_214_0.png)

# Machine Learning
Beginning of a New Era in the Dominance of Statistical Methods of Forecasting

Vijay Shankar Pandey
Assistant Professor, Institute of Management Sciences,
University of Lucknow, Lucknow, India

# CONTENTS

- 12.1 Introduction........................................................................................... 195
- 12.2 Analyzing Prominent Studies.................................................................. 196
- 12.3 Tabulation of Prominent Studies Forecasting Time Series Data Using Machine Learnings Techniques.................................................................. 199
- 12.4 Conclusion...................................................................................................... 203
- References......................................................................................................................... 203

## 12.1 INTRODUCTION

Robotics and robots have intelligence to sense like human beings. The algorithm-based AI in these machines brings a new era of scientific journey. From recognition of voice to sensing of human emotions and working somehow beyond systematic patterns have completely changed the outcomes predicted with the help of statistical modelling. AI techniques based on trial and error are consistently changing, with outcomes improved each time (Hamzaeeebi et al. [1], Deng [2], and Suganthan [3], Salaken et al. [4]).

In line with the above outcomes, the use of AI for the forecasting of time series data became a peculiar subject attracting attractions. The use of ML in form of eural network gained momentum. A number of research papers based on MLS suggested methodological advancement to improve accuracy in the forecasting of the future. In recent years, forecasting of stock gained momentum and dominated the field of forecasting. The forecasting of stock prices is classified into two branches: one called fundamental analysis, and the other technical analysis. The concept of fundamental analysis is based on a company’s financial statement analysis, while technical analysis incorporates past historical data to find future trends. The accuracy of forecasted results depends on the modelling of data with appropriate models. In

DOI: 10.1201/9781003125129-12

# Artificial Intelligence and Machine Learning in Business Management

line of this author analyzed some of the prominent under the aegis Science Direct, Elsevier, Francis & Taylor,

## 12.2 ANALYZING PROMINENT STUDIES

Hansen et al. [5] analyzed time series data with the help of exponential smoothing, auto regressive moving average (ARIMA), partial adaptive ARIMA models and ML models to capture the trends, cycles, seasonal components. The results show that support vector weakly dominates other models and achieved best results.

Carbonneau et al. [6] used advanced Machine Learning techniques including work, recurrent neural network and support vector machine for the purpose demand distorted by bullwhip effect. They made comparison of results with traditional models, i.e., naive forecasting, moving average and linear regression. Their findings suggest that Machine techniques are superior to traditional but the difference in results is statistically significant.

Choudhary and Garg [7] used hybrid ML based on Genetic Algorithm (GA) and Support Vector Machine (SVM) to forecast stock market data. Their findings show that GA-SVM outperforms the standalone SVM system. The continuous success of technical analyst to gain from market strategies raised the question against Efficient Market Hypothesis (EMH). In the current decade, there is increasing momentum of the use of AI techniques for the purpose of forecasting successful results. By these consequences, in the present scenario, EMH is used by researchers as null hypothesis.

Tsai and Wang [8] tried to forecast stock prices of the Taiwan stock exchange listed companies using hybrid ML techniques. The use of decision tree (DT) and artificial neural network (ANN) had better predictive ability. The hybrid model (DT+ANN) gave 77% forecasting accuracy. Their findings suggest that it is based on biological nervous system like human brain has good forecasting ability but lacking explanatory outputs. Their suggestion is to model stock prices using SVMs, GA can be used to obtain better prediction.

Ahmed et al. [9] tried to forecast M3 data consisting of 3,003 daily, quarterly and monthly time series. The data set was generated to organize a competition by the International Journal of Forecasting [10]. The models used for comparison were multilayer percept, Bayesian neural network, Radial basis functions, generalized regression network (also called Kernel Regression), Classification and Regression Trees (CART) regression trees, support vector regression and Gaussian processes. These methods are used in conjunction with the ML forecasting models. The findings suggest that two models as multilayer perceptron (MLP) and Gaussian Propagation (GP) are better performer to others.

Cheangga [11] tried to improve wind forecasting with the help of neural networks. The characteristic of this technique is that it is able to map random input vectors to corresponding output without assuming any fixed relationship.
