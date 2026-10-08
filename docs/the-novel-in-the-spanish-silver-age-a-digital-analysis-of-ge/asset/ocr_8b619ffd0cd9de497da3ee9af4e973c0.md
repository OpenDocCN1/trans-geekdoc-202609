Figure 56: Bar plot of number of texts per label

![](bbox=[0.236, 0.187, 0.735, 0.413])

# 5.2.2 Classification Results Comparing First Publication Labels with other Sources

The first hypothesis proposes that the labels printed on the first edition should describe the text more accurately because the process of canonization and social perception had not started when it was assigned. If these labels were assigned by looking more closely at the textual characteristics of the novel and not at external factors, it would imply that these labels should more predictably apply internal features.

To test this, I run several classification tests with two different data sets:

+   1. First, only those novels considered that had a label for their first edition and predict only this label, ignoring the rest of the sources.
2. Second, the entire corpus is considered, predicting the labels obtained in Chapter 5.1. In this case, the information of the first edition is ignored, treating the labels of several editions as one source among others.

The classification set-up relies on the results of Chapter 6.1, which will be used again in Section 5.2.2, and also employed equally in the different tests of this section (see further details in the Jupyter Notebook). In all cases, I only consider labels with more than two texts, obtaining eight subgenres defined