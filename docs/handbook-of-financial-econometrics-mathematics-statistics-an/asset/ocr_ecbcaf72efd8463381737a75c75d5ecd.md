+   44.3.2 ES-based ALqG-SVM . . . . . . . . . . . . . . . . 1683
+   44.3.3 Algorithm . . . . . . . . . . . . . . . . . . . . . 1684
+   44.4 Experiment Results . . . . . . . . . . . . . . . . 1686
+   44.4.1 Experiment results — UCI credit datasets . . . . . 1687
+   44.4.2 Experiment results of the real-life US commercial bank credit dataset . . . . . . . . . . . . . . . . 1689
+   44.4.3 ES-based experimental results compared with GS . . 1689
+   44.5 Conclusions and Future Research . . . . . . . . . . . 1691
+   Bibliography . . . . . . . . . . . . . . . . . . . . . . . 1691

# Abstract

Credit risk analysis has long attracted great attention from both academic researchers and practitioners. However, the recent global financial crisis has made the issue even more important because of the need for further enhancement of accuracy of classification of borrowers. In this study, an evolution strategy (ES)-based adaptive Lq SVM model with Gauss kernel (ES-ALqG-SVM) is proposed for credit risk analysis. Support vector machine (SVM) is a classification method that has been extensively studied in recent years. Many improved SVM models have been proposed, with non-adaptive and pre-determined penalties. However, different credit data sets have different structures that are suitable for different penalty forms in real life. Moreover, the traditional parameter search methods, such as the grid search method, are time consuming. The proposed ES-based adaptive Lq SVM model with Gauss kernel (ES-ALqG-SVM) aims to solve these problems. The non-adaptive penalty is extended to (0, 2] to fit different credit data structures, with the Gauss kernel, to improve classification accuracy.

For verification purpose, two UCI credit datasets and a real-life credit dataset are used to test our model. The experiment results show that the proposed approach performs better than See5, DT, MCCQP, SVM light and other popular algorithms listed in this study, and the computing speed is greatly improved, compared with the grid search method.

# Keywords

Adaptive penalty • Support vector machine • Credit risk classification • Evolution strategy.

# 44.1 Introduction

Ever since the subprime mortgage crisis hit the United States and affected the whole world, deepening the global economic crisis further, credit risk has received increasing attention from both industry and academia. Numerous methodologies have been introduced for addressing the challenge and importance of credit risk analysis, risk evaluation, and risk management. Statistical and neural network-based approaches are among the most popular paradigms (e.g., see Abdou and Pointon, 2008; Angelini et al., 2008; Laha, 2007; Lin, 2009; Yu et al., 2008).

Support vector machines (SVMs) have been used for credit risk analysis in the last few decades, as a promising credit risk analysis approach. It