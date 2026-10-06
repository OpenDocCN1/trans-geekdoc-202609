puts are continuous, they are called target values, and a machine learning algorithm that finds a model to predict continuous target values from a set of features is called a regression.

Prediction of the brain volume from the gestational age is an example of a regression task. In this case, the feature is the gestational age, and the target value is the brain volume. In a research setting we are able to accurately calculate brain volumes from segmented high-resolution volumetric magnetic resonance images (MRI). Fig. 2.1 shows the prediction of the brain volume from the gestational age in scans of preterm neonates using linear regression.

# Regression

![](bbox=[0.213, 0.311, 0.725, 0.574])

**Figure 2.1** Example of a regression problem: prediction of brain volume from gestational age in preterm neonates.

If the expected outputs are discrete, they are called labels, and the machine learning task is called a classification. Diagnosis of heart failure using ultrasound or magnetic resonance imaging is an example of the classification task. Diagnostic measurements include the percentage of blood that the left ventricle can inject at each heartbeat and the global longitudinal strain between diastole and systole, two features per sample (or a two-dimensional feature vector). Our aim is to find a model to predict whether the patient is healthy or has heart failure, which we call a label. In this case the labels take only two values: label 0 for the healthy patient and 1 for the patient with heart failure. Our example classification problem is illustrated in Fig. 2.2.

# 2.1.2 Unsupervised learning: clustering and dimensionality reduction

In unsupervised problems the training samples are also characterized by the feature vectors, but outputs are not known, and we look for hidden patterns in the data instead.