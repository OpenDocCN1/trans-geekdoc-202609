# TABLE 3.4
OVERVIEW OF DL TECHNIQUES

| Supervised | Attack Type | Proposed Solution | ML-Aided Technique | Dataset | Performance Evaluation Matrix | Result |
| --- | --- | --- | --- | --- | --- | --- |
| [87] | Denial of service (DoS), user to root (U2R), probe (probing), root to local (R2L) | The objective function for a single training pair in RNNs is defined as $f(	heta)=L(y,y\_i)$ [26], where L is a distance function that measures the deviation between predictions $(y\_i)$ and actual labels $y_i$, using a learning rate $\eta$ and the number of iterations k, given a sequence of labels $y (i = 1, \dots, m)$. | Recurrent neural networks (RNN-IDS) | NSL-KDD | FPR for DoS: 2.06 R2L: 0.07 Probe: 2.16 | Accuracy of binary classification: 83.228% Accuracy of multiclassification: 81.29% |
| [88] | Known genuine and malicious behavior as an attack | By modeling network traffic as time series based on known genuine and malicious behavior, authors improve intrusion detection, as demonstrated through training long short-term memory (LSTM) recurrent neural networks with DARPA/KDD Cup '99. | Long short-term memory (LSTM) | DARPA/KDD Cup '99 | | Accuracy: 93.82% and cost: 22.13 |
| [89] | Spam images | This paper focuses on identifying specific categories of images (e.g., adult content and political images) in email for classification. | CNN, SVM | Customized | | Accuracy: 75.10% |
| [90] | Email spam | Comparing DNN architectures on classification problems, CA showed higher accuracy. | Deep belief network (DBN) | Spambase | Accuracy: 96.40% |