
## 1. Introduction

Every internet service providers (ISPs) have their own DNS server to provide the name resolve and reverse lookup services to the clients. DNS servers uses port `53` both User Datagram Protocol (`UDP`) and Transmission Control Protocol (`TCP`) to perform their activities. As a DNS request destination port is `53` and source port is any port above port `1023` in case of DNS response source port is `53` and destination port is any port above port `1023`. When the two DNS server transfer their zone file then both source and destination ports are port `53` (`TCP`).

Internet is growing exponent, and it is a big challenge to all system and network administrator to achieve the information security goal, confidentiality, integrity and availability. That’s why continuous network monitoring, classification and security analysis is required. Intrusion detection system (`IDS`) and Intrusion prevention system (`IPS`) either are content-based or behavior-based can’t defend the various attack [[1](#ch10.xhtml#ref10_1), [2](#ch10.xhtml#ref10_2), [3](#ch10.xhtml#ref10_3) and [4](#ch10.xhtml#ref10_4)].

Now-a-days most of the researcher used the net flow traffic to mitigate or combat the various type of attacks and malicious traffic. A net flow record contains various information that can be used for various purposes from which an important purpose is the analysis of the network for its security. We capture the net flow data for the time period of 1 month. Then applied the data visualization to obtain certain patterns from the dataset. After applying the machine learning (`ML`) models, compared the individual performance between K-nearest neighbors (`KNN`) and Naive Bayes (`NB`) ML classifiers to find out accuracy [[5](#ch10.xhtml#ref10_5), [6](#ch10.xhtml#ref10_6), [7](#ch10.xhtml#ref10_7) and [8](#ch10.xhtml#ref10_8)].

## 2. Problem Statement

To identify the benign and malicious traffic towards the DNS service for improving the quality of services, security and efficiency, we have to analysis the patterns in network. Amount of traffic, type of traffic, source and destination of traffic, etc.

Our focus is to develop a working model using data science and various ML language to visualize, analysis and predict the type of traffic in the network and impact of these traffic in the ISPs network.

To an insurance policy against potential dangers. Utilizing a range of vendors offers an extra layer of protection, which is one of its benefits. This leads in the network having enhanced levels of protection because an attack that might be able to get through the security devices given by one vendor owing to a known fault would not be able to get through the security devices provided by the other suppliers.

## 3. Working

Our working model is divided into three major parts – data collection (net flow), sampling of data and classification of the data ([Figure 10.1](#ch10.xhtml#fig10_1)).

![Figure 10.1: Flow diagram.](images/fig10_1_C.jpg)

[Figure 10.1: Flow diagram.](#ch10.xhtml#R_fig10_1)

## 4. Database Used to Store the Net Flow Data (Captured Records)

Here we have the details of source address destination address, Source port destination port and time stamp. We store these details in a `.csv` file (net flow dataset) and import it in `Jupyter` and applying some sorting and condition to visualize the dataset ([Figure 10.2](#ch10.xhtml#fig10_2)).

![Figure 10.2: Captured dataset through net flow.](images/fig10_2_B.jpg)

[Figure 10.2: Captured dataset through net flow.](#ch10.xhtml#R_fig10_2)

First we sorted our dataset based on time stamp and applying the conditions with respect to our DNS server (`203.190.128.141` and `8.8.8.8`) and DNS port `53`. The conditions were as follow `DNSREQ` -IF Source port is greater than `1023` & destination IP equals DNS server IP & destination port equals `53` then it is DNS request (`DNSREQ`), IF source IP equals DNS server IP & source port equals `53` & destination IP equals which send the DNS request then it is DNS response (`DNSRES`). It set a flag in dataset.

Based on the specific ports which are used in organization for day to day activities like https (`443`), http (`80`), DNS (`53`) and customized port for specific services allowed by network administrator. We considered as a benign traffic and rest considered as malicious traffic. So, to distinguish between them a function was defined in which a new column was added that would tell was whether the user that initiated the request was genuine traffic or malicious traffic and function defined also calculated the number and the percentage of the type of traffic present ([Figure 10.3](#ch10.xhtml#fig10_3)).

![Figure 10.3: Dataset after set flags and traffic type.](images/fig10_3_B.jpg)

[Figure 10.3: Dataset after set flags and traffic type.](#ch10.xhtml#R_fig10_3)

After this analysis was done it was time for visualization of the data for which `Matplotlib` was imported and for that we plotted the graphs for top 30 values of the port counts without separating them on the basis of malicious or genuine traffic. But for better visualization a pivot table was created in which all the genuine traffic ports were separated from the malicious traffic ports. All the malicious traffic ports were combined into a single column and a function was made to count the number of occurrence of the ports requested by the host. Now the visualization was done with the new table with only genuine traffic ports and one port with all the malicious traffic port ([Figure 10.4](#ch10.xhtml#fig10_4), [Figure 10.5](#ch10.xhtml#fig10_5), [Figure 10.6](#ch10.xhtml#fig10_6) and [Figure 10.7](#ch10.xhtml#fig10_7)).

![Figure 10.4: Visualization of the port address count.](images/fig10_4_C.jpg)

[Figure 10.4: Visualization of the port address count.](#ch10.xhtml#R_fig10_4)

![Figure 10.5: Visualization of benign and malicious traffic separately.](images/fig10_5_C.jpg)

[Figure 10.5: Visualization of benign and malicious traffic separately.](#ch10.xhtml#R_fig10_5)

![Figure 10.6: Horizontal bar graph of the benign and malicious traffic ports separately.](images/fig10_6_C.jpg)

[Figure 10.6: Horizontal bar graph of the benign and malicious traffic ports separately.](#ch10.xhtml#R_fig10_6)

![Figure 10.7: Line plots of the benign and malicious traffic ports separately.](images/fig10_7_C.jpg)

[Figure 10.7: Line plots of the benign and malicious traffic ports separately.](#ch10.xhtml#R_fig10_7)

## 5. Application of Machine Learning Part on the Dataset

### 5.1 Naïve Bayes (NB)

Naive Bayes classifiers are a collection of classification algorithms based on `Bayes’ Theorem`. It is not a single algorithm but a family of algorithms where all of them share a common principle, i.e., every pair of features being classified is independent of each other. It is a simple but surprisingly powerful algorithm for predictive modeling. The model is comprised of two types of probabilities that can be calculated directly from your training data: (1) The probability of each class; and (2) The conditional probability for each class given each x value. Once calculated, the probability model can be used to make predictions for new data using Bayes’ Theorem. The NB classifier is specially designed for binary classification problems. It is very easy to construct and in many cases it outperforms some sophisticated methods when dealing with huge data [[9](#ch10.xhtml#ref10_9)].

### 5.2 K-nearest neighbors (KNN)
