Total 13,416 138M 12,416

TABLE 9.3: Incomplete listing of the of the VGG19 architecture

+   1 * Describe how the VGG19 CNN may be used as fixed FE for a 
. classification task. In your answer be as detailed as possible 
regarding the stages of FE and the method used for classification .

+   2 Referring to Table (9.3), suggest three different ways in which 
. features can be extracted from a trained VGG19 CNN model. In 
each case, state the extracted feature layer name and the size of the 
resulting FE .

+   3 After successfully extracting the features for the 4k images from the 
. dataset, how can you now classify the images into their respective 
categories?

# 9.1.6 Bayesian deep learning

# PRB-275 ? CH.PR-9.9. [BAYESIAN DEEP LEARNING]

A recently published paper presents a new layer for Bayesian 
neural networks (BNNs). The layer behaves as follows. During the 
feed-forward operation, each of the hidden neurons Hn, n ∈ {1, 2,} in 
the neural network in (Fig. 9.8) may, or may not fire, independently 
of each other, according to a known prior distribution .

![](bbox=[0.43, 0.69, 0.61, 0.78])

FIGURE 9.8: Likelihoid in a BNN model .

The chance of firing , $\gamma$, is the same for each hidden neuron. Using 
the formal definition, calculate the likelihood function of each of the 
following cases: