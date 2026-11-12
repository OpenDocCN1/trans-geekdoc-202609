categorical classification systems, that categorize instances as correct or incorrect, and is frequently more helpful than precision, in particular, if your class distribution is unequal.

$$F1 - score = 2 \times \frac{Precision \times Recall}{Precision + Recall}$$ (13.4)

# ### 13.3.4.5 Accuracy

The accuracy of classification is essentially the rate of proper classification, for either an independent test set or with a change in the idea of cross-validation, and has been used to evaluate which model identifies connections and correlations between variables in a dataset based on data input as well as training.

$$Accuracy = \frac{TP + TN}{TP + FP + TN + FN}$$ (13.5)

# ### 13.3.5 Results

All models perform well with 84% accuracy after fine-tuning in evaluation matrices, however, DenseNet201 is our best model for this job with 85% test accuracy, 1.12 test loss, 84% precision accuracy, 84% recall accuracy, and 84% F1-Score accuracy. The DenseNet201 model has a training accuracy of 99%. There isn't much of a distinction between train and test accuracy. As a result, we may conclude that our model is neither underfitting nor overfitting. DenseNet201 has a total of 201 layers, but the first 30 layers were fine-tuned in this study, leaving only 171 layers to be trained. This model uses the Adam optimizer, which has a batch size of 64, 50 epochs, a learning rate of 0.0001, and a total trainable parameter count of 17,936,064.

# ### 13.3.6 Discussion

On the HAM10000 dataset, we trained deep learning models to identify skin lesions on IoT based on security. Four classification models were trained, and the accuracy of these models was good. The main focus of this research is on ensuring sufficient security for IoT-based skin lesion detection. Models were tested, however, we recommend using “IoT based on security” because the experiment was too costly. However, a method based on references is proposed. The main architecture of this project is depicted in Figure 13.1. Patients’ data is shown in Figure 13.2 as it travels through a gateway, past security, and into cloud computing storage. Figure 13.3 depicts the security measures used to gain access to a patient’s results. In this study, models were able to categorize skin lesions using a five-step process called CAD, as shown in Figure 13.4. The result will be ready in cloud computing after encryption and decryption, and then it will be transferred to the patient, as shown in the diagram in Figure 13.5. In our work, we’ve used CNN models with fine-tuning, and the architecture is depicted in Figure 13.6. Figure 13.7 depicts images of seven different forms of skin lesions. To understand the performance of all models, accuracy, loss, parameters, and hyperparameters are reported in Tables 13.1 and 13.2.