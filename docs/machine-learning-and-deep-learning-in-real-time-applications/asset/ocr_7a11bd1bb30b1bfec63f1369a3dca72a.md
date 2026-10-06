# # Chapter 1 Obtaining Deep Learning Models for Automatic Classification of Leukocytes

Pedro João Rodrigues

https://orcid.org/0000-0002-0555-2029

CeDRI, Research Centre in Digitalization and Intelligent Robotics, Instituto Politécnico de Bragança, Portugal

Getúlio Peixito Igrejas

https://orcid.org/0000-0002-6820-8858

CeDRI, Research Centre in Digitalization and Intelligent Robotics, Instituto Politécnico de Bragança, Portugal

Romeu Ferreira Beato

Instituto Politécnico de Bragança, Portugal

# ABSTRACT

In this work, the authors classify leukocyte images using the neural network architectures that won the annual ILSVRC competition. The classification of leukocytes is made using pretrained networks and the same networks trained from scratch in order to select the ones that achieve the best performance for the intended task. The categories used are eosinophils, lymphocytes, monocytes, and neutrophils. The analysis of the results takes into account the amount of training required, the regularization techniques used, the training time, and the accuracy in image classification. The best classification results, on the order of 98%, suggest that it is possible, considering a competent preprocessing, to train a network like the DenseNet with 169 or 201 layers, in about 100 epochs, to classify leukocytes in microscopy images.