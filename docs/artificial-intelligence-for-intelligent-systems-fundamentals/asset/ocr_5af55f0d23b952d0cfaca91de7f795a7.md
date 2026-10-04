# A step toward the detection of alzheimer's disease 265

![](bbox=[0.136, 0.096, 0.863, 0.339])

Figure 13.2 Training and validation loss and accuracy.

the optimization process. We used three different basic models. ResNet-50, DenseNet-121, and VGG119 are the three networks. Using the stacking approach, we put all these models together in one place. We ran the main model, as well as its majority voting and stacking-based ensemble, in parallel. The precision of the proposed model is 96%, which is 95%, the F-score is 94%, and the total accuracy of the model is 90.15%. While the model's performance for the categorization of non-demented individuals is adequate, it has much scope to improve when it comes to diagnosing demented individuals. It is feasible that training the proposed model on a dataset that contains a greater number of demented patients will aid in overcoming this limitation of the dataset. As evidenced by great results in the classification of different stages of AD when compared to existing baseline models, the proposed model offers hope in the fight against AD. Figure 13.2 shows the graphical representation of training and validation accuracy along with training and validation loss.

# 13.5 CONCLUSION

AD is a progressive neurological brain illness that develops from birth. When AD is detected early, it can assist in avoiding further damage to the brain tissues and aid in the administration of appropriate treatment. A combination of algorithms is used to obtain higher prediction accuracy than any of the algorithms used individually in the ensemble learning process. Because of the increasing popularity of in-depth learning technologies, researchers have begun combining various technologies for a variety of different applications. In this study, we suggested a technique based on profound learning as a method for integrating algorithms