![](bbox=[0.11, 0.14, 0.88, 0.36])

FIGURE 8.7 System Flow Diagram.

# 8.3.2.8 Classification Chart

The K-fold cross-validation approach is a statistical tool for estimating the performance of a prediction model in practice (Wolberg et al., 2021).

The mean accuracy scores of cross validation of hard/majority voting, soft voting, and weighted average soft voting using K-fold cross validation (K = 5) were 0.97364 (±0.01110), 0.97188 (±0.01403), and 0.97365 (±0.01466).

# 8.4 PROPOSED WORK

The first step was to identify the problem statement. Then, through a literature review, a research objective was established. The research objective was to develop a prediction system with a higher accuracy.

The dataset used was from the Cleveland Clinic Foundation Dataset available at the UC Irvine Machine Learning Repository. Then, data pre-processing was carried out, and changing the raw data to pre-processed data would have reliable accuracy (Khanh & Khang, 2021).

Feature selection was performed to remove redundant noise from the dataset, leaving only the important attributes, which helped in increasing the accuracy, reducing overfitting, and shortening the training time.

Subsequently, data were split such that 70% of the data were used as a training dataset, and 30% of the data were used as a testing dataset, as shown in Figure 8.7.

# 8.5 ANALYSIS AND COMPARISON

The performances of the four different classification algorithms were evaluated on the WBCD dataset, as shown in Table 8.4. Among these, logistic regression performed better than the other algorithms. The top three high-performance classification models were selected for the ensemble voting classifier: hard voting, soft voting, and weighted average models.