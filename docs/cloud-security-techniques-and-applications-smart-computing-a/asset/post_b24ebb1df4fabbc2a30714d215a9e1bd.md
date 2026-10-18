

## 4 Commercial Web-Based Clouds Based on Machine Learning

Cloud SIEM — Security information and event management system is shown in Fig. 4.

![](img/09fa00ca1419044515be1e45aa422bc8_157_0.png)

Fig. 4: Cloud SIEM — Security information and event management system

### 4.1 Cloud Shell

Cloud Shell is a web-based environment which supports and manages resources by using an online terminal with the aid of utilities, command-line tools, and libraries. Using Cloud Shell, we can create cloud-based applications. Google Cloud Shell includes Cloud Speech-to-Text, App Engine, Data Transfer, and Cloud Build.

### 4.2 Various tools available in Cloud Shell

#### 4.2.1 Persistent disk storage

Google Cloud Storage offers persistent disk storage using virtual machines and virtual machine manager interface on a pay-per-usage basis for every user. The `$HOME` directory is mounted to provide this storage with various files such as home directory, software, scripts, and configuration files.

#### 4.2.2 Authorization

Google Cloud API makes use of command-line tools with authorization using Authorize Cloud Shell’s dialog.

#### 4.2.3 Pre-configured environment variables

When Cloud Shell is initiated, the project will be given to the gcloud configuration system for immediate use. By using the environment variable `GOOGLE_CLOUD_PROJECT`, application default credentials of the library and active project also will be set in console.

#### 4.2.4 Zone selection

Cloud Shell is distributed worldwide through various Google Cloud platforms. Initially, it is assigned to the closest geographical region. Later, based on the workload, it will try to migrate to other VMs.

#### 4.2.5 Image rollout

Latest images of Cloud Shell get updated with Cloud Software Development Kit, Docker, and required runtime utilities and libraries.

#### 4.2.6 Root user

When you create a user account, you have all the privileges on the allocated virtual machine and you can execute workloads on it.

#### 4.2.7 Available tools

These available tools are pre-installed, and additional tools can be installed on a requirement basis. Additional tools which are installed on the virtual machine will not persist after the instance gets terminated.

#### 4.2.8 Language support

Various languages, namely Java, Go, Python, Node.js, Ruby, PHP, and .NET, provide pre-installed language support.

#### 4.2.9 Safe mode

Google Cloud uses `cloudshellsafemode=true` in the URL to ensure safe mode and fix security issues in the files.

### 4.3 Amazon Web Services

Amazon Web Services (AWS) is a web-based cloud platform launched in 2006 and provides various products such as Amazon SageMaker, Amazon Augmented AI, Amazon Forecast, Amazon Translate, Amazon Personalize, AWS Deep Learning AMIs, and Amazon Polly.

#### 4.3.1 Microsoft Azure

Microsoft Azure is a web-based cloud computing platform launched in 2010 and provides various products such as Microsoft Azure Cognitive Service, Microsoft Azure Databricks, Microsoft Azure Bot Service, Microsoft Azure Cognitive Search, and Microsoft Azure Machine Learning.

### 4.4 IBM Cloud

IBM Cloud is a cloud computing platform that provides several types of cloud services such as public, private, and hybrid, with various products, namely IBM Watson Studio, IBM Watson Speech-to-Text, IBM Watson Text-to-Speech, IBM Watson Natural Language Understanding, IBM Watson Visual Recognition, and IBM Watson Assistant.

## 5 State-of-the-Art Machine Learning Algorithms for Cloud Security

Various state-of-the-art machine learning algorithms are listed in Table 1.

Table 1: State-of-the-art machine learning algorithms

| Algorithm | Machine learning algorithm | Remarks |
|---|---|---|
| A Review of Machine Learning Algorithms for Cloud Computing Security | Supervised, unsupervised, semi-supervised and reinforcement | Security threats, issues, and associated solutions of cloud computing are stated |
| Assessment of machine learning algorithms in cloud computing frameworks | Supervised | Powerful analytical methods that allow machines to recognize patterns and facilitate human learning are stated |
| Network based IDS for cloud environment using combination of machine learning algorithms | Deep Neural Network (DNN) based anomaly Network IDS using a hybrid optimization framework (IGASAA) based on Improved Genetic Algorithm (IGA) and Simulated Annealing Algorithm (SAA) | Reduced execution time, convergence time and save processing power |
| Feasibility of Supervised Machine Learning for Cloud Security | Supervised | Demonstrates the effectiveness of these models across multiple datasets by improving cloud security |
| Evaluating machine learning algorithms for anomaly detection in clouds | Supervised and unsupervised | Detects abnormal behaviour of services and hosts by analysing metrics collected from all layers and components of the cloud infrastructure |

Code for machine learning algorithms such as linear regression, support vector machine, and Naive Bayes classification is given below.

Listing 1: Code for machine learning algorithms such as linear regression, support vector machine, and Naive Bayes classification

```
#Linear regression
lin_regr = linear_model.LinearRegression()
lin_regr.fit(X_train, y_train)
print(lin_regr.coef_)
print(lin_regr.score(X_test, y_test))
plt.style.use('fivethirtyeight')
plt.scatter(lin_regr.predict(X_train), lin_regr.predict(X_train) - y_train, color = "yellow", s = 10, label = 'Training data')
plt.scatter(lin_regr.predict(X_test), lin_regr.predict(X_test) - y_test, color = "pink", s = 10, label = 'Testing data')
plt.hlines(y = 0, xmin = 0, xmax = 100, linewidth = 5)
plt.legend(loc = 'upper right')
plt.title("Demo")
plt.show()
#Support vector machine
from sklearn import svm as s
from sklearn import metrics as m
s_class = s.SVC(kernel='linear')
s_class.fit(X_train, y_train)
y_pred = s_class.predict(X_test)
print(m.accuracy_score(y_test, y_pred))
print(m.precision_score(y_test, y_pred))
print(m.recall_score(y_test, y_pred))
#Naive Bayes Classification
import numpy as n
import pandas as p
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import confusion_matrix, accuracy_score
NB_class = GaussianNB()
NB_class.fit(X_train, y_train)
y_pred = NB_class.predict(X_test)
ac_sc = accuracy_score(y_test,y_pred)
cm_ma = confusion_matrix(y_test, y_pred)
```

## 6 Conclusion

Machine learning has currently become a part of our daily lives, and is a new technology endowed to handle security and privacy problems that arise in cloud computing. In recent years, in-depth analysis was administered on the protection and privacy problems of cloud computing. Therefore, security and privacy become terribly essential and vital and are to be addressed. For future work, it’s essential for the researchers to deeply investigate different security primitives' solutions for security attacks in cloud computing. A mixed protocol technique will scale back the computation overhead on the protection and privacy protective solutions. Moreover, customization of the privacy and security protocols for machine learning is additionally a noteworthy and open analysis space to develop a viable resolution. Researchers are looking forward to performing their analysis in various applications of machine learning such as space of astronomy, natural philosophy, nucleonics, physical science, magnetism, machines, technology, mechanics, electrohydrokinetics, signal processing, power, energy, bioinformatics, economy, and finance.

## 7 References

- [1] Dillon T, Wu C, Chang E, Cloud Computing: issues and challenges, 2010 24th IEEE International Conference on Advanced Information Networking and Applications, Perth, WA, Australia, 2010, pp. 27-33, doi: 10.1109/AINA.2010.187
- [2] Wang L, Laszewski V, Young A, Cloud Computing: a perspective study, New Gener. Comput, 2010, 28, 137–146, https://doi.org/10.1007/s00534-008-0081-5
- [3] Naveen G, Ayushi G, Survey on machine learning based scheduling in cloud computing, Proceedings of the 2017 International Conference on Intelligent Systems, Metaheuristics & Swarm Intelligence, Association for Computing Machinery, New York, NY, USA, 2017, 57–61, DOI: https://doi.org/10.1145/3093337.3093532
- [4] Umer A, Muhammad M, Shah S, Amin R, Shaukat W, Syed R, Suh Y, Piran J, A review of machine learning algorithms for cloud computing security, Electronics, 9, 2020, no. 9: 1379, https://doi.org/10.3390/electronics9091379
- [5] Subramanian K, Tamilselvan L, A focus on future cloud: machine learning-based cloud security, SOCA, 2019, 13, 237–249, https://doi.org/10.1007/s11761-019-00270-0
- [6] Bhamare D, Salman T, Samaka M, Erbad A, Jain R, Feasibility of supervised machine learning for cloud security, 2016 International Conference on Information Science and Security (ICISS), Pattaya, Thailand, 2016, pp. 1-5, doi: 10.1109/ICISSEC.2016.7885853
- [7] Nassif A, Talib M, Nasir Q, Albadani H, Dakalbab F, Machine learning for cloud security: a systematic review, IEEE Access, 2021, vol. 9, pp. 20717-20735, doi: 10.1109/ACCESS.2021.3054129
- [8] Han Q, Meikang Q, Zhihui L, Selective encryption on ECG data in body sensor network based on supervised machine learning, Information Fusion, 2020, Volume 55, Pages 59-67, ISSN 1566-2535, https://doi.org/10.1016/j.inffus.2019.07.012
- [9] Potluri S, Mangla M, Satpathy S, Mohanty S N, Detection and prevention mechanisms for DDoS attack in cloud computing environment, 2020 11th International Conference on Computing, Communication and Networking Technologies (ICCCNT), Kharagpur, India, 2020, pp. 1-6, doi: 10.1109/ICCCNT49239.2020.9225936
- [10] Karimipour H, Dehghantanha A, Parizi R, Choo K, Leung H, A deep and scalable unsupervised machine learning system for cyber-attack detection in large-scale smart grids, IEEE Access, 2019, vol. 7, pp. 80778-80788, doi: 10.1109/ACCESS.2019.2920326
- [11] Wu W, Alvarez J, Liu C, et al., Bot detection using unsupervised machine learning, Microsyst Technol, 2018, 24, 209–217, https://doi.org/10.1007/s00542-016-3237-0
- [12] Çavuşoğlu Ü, A new hybrid approach for intrusion detection using machine learning methods, Appl Intell, 2019, 49, 2735–2761, https://doi.org/10.1007/s10489-018-01408-x
- [13] Potluri S, Achyuth S, Elham T, Mohanty S N, IOT enabled cloud based healthcare system using fog computing: a case study, Journal of Critical Reviews ISSN 2394-5125, 2020, Vol 7, Issue 6, pp. 1068-1072, doi: 10.31838/jcr.07.06.186

