# 26 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

fault diagnosis belongs to such a challenging problem since the system itself is a complex electromechanical one. There, some advanced signal processing technologies have been proposed for motor current or vibration signal analysis (Zari and Poshtan 2007; Blölt et al. 2008; Puche-Panadero et al. 2009) as to extract useful features for diagnosis. However, these state-of-the-art methods require the researchers to have a deep understanding of the induction motor and the fault signals. In addition, the required expert knowledge is not easily obtained that those methods are not intelligent enough to the machine learning. In contrast, a deep “autoencoder” (AE) network structure has been trained to learn low-dimensional codes from high-dimensional input vectors in unsupervised manner (Krizhevsky, Sutskeever, and Hinton 2012). Furthermore, sparse AE (SAE) (Ranzato et al. 2007; Wright et al. 2010; Boureau et al. 2010) have been widely studied to realize deep learning, as it is highly effective for finding succinct and high-level representations of complex data.

Inspired by the prior research, this chapter presents SAE-based deep neural network (DNN) approach for induction motor fault diagnosis. The rest of this chapter is organized as AE and its variants, the details of experiments performed on a machine fault simulator and the corresponding results, and some conclusions drawn from this study.

# AUTOENCODER AND ITS VARIANTS

This section is providing systematic introduction for AE, sparse AE, and denoising AE.

# Autoencoder

An AE is a symmetrical neural network that can learn the features in an unsupervised manner by minimizing reconstruction errors (Shin et al. 2013). The basic structure of AE is shown in Figure 2.1, where it tries to learn an approximation in the hidden layer so that the input data can be perfectly reconstructed at the output layer. However, the intrinsic problems of AE, as such simply copying input layer to hidden layer, make ineffective in extracting meaningful features even though its output can be a perfect recovery of input data.

![](bbox=[0.303, 0.00711, 0.692, 0.00893])

FIGURE 2.1 The structure of an autoencoder neural network.