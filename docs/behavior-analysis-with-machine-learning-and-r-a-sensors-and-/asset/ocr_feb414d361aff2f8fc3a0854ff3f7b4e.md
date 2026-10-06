# # Chapter 10

# ## Detecting Abnormal Behaviors

Abnormal data points are instances that are rare or do not occur very often. They are also called outliers. Some examples include illegal bank bank transactions, defective products, natural disasters, etc. Detecting abnormal behaviors is an important topic in the fields of health care, ecology, economy, psychology, and so on. For example, abnormal behaviors in wildlife creatures can be an indication of abrupt changes in the environment and rare behavioral patterns in a person may be an indication of health deterioration.

Anomaly detection can be formulated as a binary classification task and solved by training a classifier to distinguish between normal and abnormal instances. The problem with this approach is that anomalous points are rare and there may not be enough to train a classifier. This can also lead to class imbalance problems. Furthermore, the models should be able to detect abnormal points even if they are very different from the training data. To address these issues, several anomaly detection methods have been developed over the years and this chapter introduces two of them: Isolation Forests and Autoencoders.

This chapter starts by explaining how Isolation Forests work and then, an example of how to apply them for abnormal trajectory detection is presented. Next, a method (ROC curve) to evaluate the performance of such models is described. Finally, another called autoencoder can be used for anomaly detection is explained and applied to the abnormal trajectory detection problem.

# ### 10.1 Isolation Forests

As its name implies, an isolation forest identifies anomalous points by explicitly 'isolating' them. In this context isolation means separating an instance from the others. This approach is different from many other anomaly detection algorithms where they first build a profile of normal instances and mark an instance as an anomaly if it does not conform to the