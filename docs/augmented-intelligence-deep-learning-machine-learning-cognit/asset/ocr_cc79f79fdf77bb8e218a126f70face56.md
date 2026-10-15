# 4.7.3. Evaluation of the Model

The neural network model has been implemented using Keras functional API supported by TensorFlow backend. A split ratio of 0.1 is used to divide the training and the test sets *i.e.*, 10% of the dataset is used for testing and prediction while the remaining 90% of the dataset is used for training the model. The model is trained for 75 epochs at the end of which the model gives a training accuracy of 94.95%, a training loss of 0.1215 and validation accuracy of 83.68%, validation loss of 0.5465. The training *vs.* validation accuracy, training *vs.* validation loss in each epoch for the proposed model has been plotted in Fig. (4.20a) and Fig. (4.20b) for visualization.

![](bbox=[0.221, 0.359, 0.813, 0.508])

**Fig. (4.20).** (a) Training *vs.* Validation Accuracy, (b) Training *vs.* Validation Loss.

# 4.8. DEEP LEARNING IN DETECTION OF BRAIN TUMOURS

Brain is one of the most important organs of our body. Brain cells except nerve cells get replaced when they become old or get damaged. The production of excess of these new cells results in the formation of tumours. Tumours are generally categorized into two groups: benign *i.e.*, non-cancerous and malignant *i.e.*, cancerous.

The detection of brain tumour is hard due to its size, shape and location. Timely detection and treatment of tumour increases the chances of survival of the patient. The detection of tumour is generally done using advanced medical equipment like Magnetic Resonance Imaging (MRI) or Computerized Tomography (CT) scan. MRI imaging is mostly used in the diagnosing brain tumours as it provides better image of brain because of better high contrast image of tissue in human brain as shown in Fig. (4.21) [22]. It is the most important method of detecting and diagnosing brain tumour due to higher accuracy.