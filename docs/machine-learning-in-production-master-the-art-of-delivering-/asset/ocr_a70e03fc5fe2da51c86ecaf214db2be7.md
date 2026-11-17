# Data poisoning attack

In a data poisoning attack, attackers have access to input or source data. They change the input data in such a way that the model will make incorrect predictions that are unreliable for making any business decisions or taking any action. Attackers can add some noise to the original data to cause alterations in the prediction of the model. This attack targets the training data and modifies it intelligently.

# Distributed Denial of Service attack (DDoS)

It refers to passing complex data to models that will take more time to make predictions. This type of attack limits the use of models for the users. For this, attackers can inject some malware to control the system or server.

# Data privacy attack

Data privacy refers to the confidentiality of Personally Identifiable Information (PII) and Personal Health Information (PHI). Attackers attempt to learn this type of sensitive information through this type of attack. It can be information about the model or training data. ML models like Support Vector Machines (SVMs) may leak the information, as support vectors are data points from training data.

Data privacy attacks can be broadly classified into the following categories:

+   Membership inference attack: The goal of this attack is to determine whether input X is part of the training data. Mostly, shadow models are used in this type of privacy attack. Shadow model training uses a shadow dataset in order to imitate the target model. The output of the shadow models is then passed as an input to the meta-model. Finally, the output of the meta-model is used to extrapolate properties of training data or model. Over-fitted models are prone to data privacy attacks.

+   Input inference attack: It is also known as model inversion or data extraction attack. It is the most common type of attack. The goal of this attack is to extract information from the training dataset by reverse engineering the model. It can also target learning the statistical properties of input data, such as probability distribution. Attackers can attempt to learn the features that are not encoded explicitly while training the model.

+   Model extraction attack: It is also known as a parameter inference attack. The goal of this attack is to learn the hyper-parameters of the model and then reconstruct the model that behaves like the targeted model. Interestingly, over-fitted models are difficult to extract due to high prediction errors based on test data.