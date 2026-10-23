![](bbox=[0.17, 0.12, 0.45, 0.51])

![](bbox=[0.45, 0.12, 0.75, 0.51])

# FIGURE 9.14

SL-touch Product Feature. The product of stromal adjacency (S-touch) and lumen adjacency (L-touch) scores, with low value in red, high value in green (better prognosis) (compare segmentations in Figs. 9.6 and 9.8), showing similar results for IF and H&E images of the same tissue. Gray lines show the Voronoi diagram, the zone of influence around each epithelial nucleus.

or some other aggregation function. More sophisticated aggregation can use support vector machines (SVMs) learning (see Modeling section) with graph kernels [95], or deep graph neural networks [96].

# Modeling

Modeling as the final computational step in creating improved grading schemes combines the output of image-derived features as well as clinically derived features to predict the probability of survival or the expected time until significant progression of the disease in a cohort of patients with known clinical outcome. Standard clinical features that go into models include age, race, sex, etc. as well as pathologic stage, laboratory values, features from radiology and genetic testing [97]. Machine learning algorithms learn the most relevant feature combinations (imaging and clinically derived) and quantify the relative importance of each feature in a model that