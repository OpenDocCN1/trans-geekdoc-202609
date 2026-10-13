
*   Predict human body conditions such as strokes using wearable devices.
*   Identify the behavior of pedestrians and other vehicles in self-driving vehicles.
*   Robo automation consists of NLP models that use data from different locations.
*   Credit card fraud detection systems in financial organizations.
*   Recommender and personalization systems that use data from different consumers.
*   Computer-vision-based healthcare diagnostics systems in different hospitals.
*   Enhancements in Apple’s Face ID and Siri voice recognition.

### 5.3.5 Challenges of Federated Learning

Generally, aspects such as data privacy preservation, optimizing distributed processing, and handling large-scale model training are some of the challenges associated with federated learning. Other than that, federated learning raises several challenges as listed below.

*   **Expensive communication:** Since federated networks comprise many devices, network communication can be slower and more expensive than local computation. Thus, communication-efficient methods need to be developed for the repeating transmission of small messages or model updates, instead of transmitting the entire dataset during model training.
*   **Systems heterogeneity:** Aspects such as the hardware configuration, power, and network strength of each local device differ. This results in different storage capacities, communication, and computational capabilities in each device. Based on these constraints, only a set of devices are active during one iteration. These settings are more error-prone, and device failures can happen, which leads to loss of model updates during training.
*   **Statistical heterogeneity:** Data is created and acquired by different distributed devices. Consider the NLP task of predicting the next word among mobile phone users with different languages. Although different data points exist among devices, there is a method to identify the relationship among the devices and the distributions as the basis. This can result in issues such as insufficient data labels in the client machines and processing complexities. The data heterogeneity can result in bias and different sizes in local data. Therefore, preserving data privacy is hard to achieve with the statistical discrepancy in the data and the configuration constraints in the local devices. Since the local data can change over time, it may result in temporal heterogeneity and may require interoperability and regular curation.
*   **Privacy concerns:** Federated learning protects data by sharing the knowledge learned from the model and related updates, such as gradients, without sending the original data. This communication may result in identifying local information, such as location and IP address, by the central device. Also, the performance of the model may decrease by using privacy-preserving methods, such as secure multi-party computation or differential privacy. Therefore, a balance is needed between privacy and performance aspects.

## 5.4 Multi-modeling with Ensemble Learning

### 5.4.1 Overview of Ensemble Learning

Ensemble learning combines multiple machine learning algorithms into a reliable model to improve the performance of existing models. Although individual models perform well, in some scenarios the integration of a set of models produces better results using an ensemble approach for a given task. Overall, in ensemble learning the models are stacked together to perform multi-layer processing to obtain a robust model, as shown in Figure 5.11. It integrates the results of a set of models to decrease the prediction variance and the generalization error, thereby increasing the precision of learning and discovering a new architecture.

![Figure 5.11 Overview of ensemble learning.](html/images/9781032473246_C005_011.jpg)

Figure 5.11 Overview of ensemble learning.

Let us distinguish ensemble learning from traditional deep learning. In general, the concept of fusion combines different embeddings to produce a single entity. The integration of data from different sources and generating specific results is known as data fusion. We learnt that neural networks are non-linear methods and CNN is an efficient model. They are flexible and scalable with the size of the dataset. However, since they train with stochastic learning algorithms, most of the time these models may highly depend on the considered data type resulting in high variance. Also, the weight assignments may change in each training process, which will result in varying predictions. Accordingly, when the process is based on one model and sensitive to the training data, it does not generate high prediction results.

This can be addressed by training the data using a set of models to decrease the variance and integrate the results. Those base learner models can follow different procedures of mapping the features with variant decision boundaries. Thus ensemble learning can produce better results. This improvement occurs by combining multiple features with heterogeneous large datasets, which are extracted from multiple classifiers.

### 5.4.2 Ensemble Learning Process

Ensemble learning uses a set of models to train a given dataset and combines the results of each model to generate the final prediction. Let us consider an example as shown in Figure 5.12. Here, the four main layers of a CNN, namely the convolution, activation, pooling, and fully connected layer, work together to provide a prediction. Three-dimensional images are input to the model and the CNN groups the pixels and processes using filters. Based on the complexity of the dataset, we can decide the number of filters to be used. The pooling layer is used to decrease the parameter space of the input through regression. This process is applied repeatedly on a given dataset to produce a reliable result.

![Figure 5.12 Process overview of ensemble learning.](html/images/9781032473246_C005_012.jpg)

Figure 5.12 Process overview of ensemble learning.

Generally, we use a small set of models such as three, five, or ten trained models, to avoid unnecessary computational expense and decline in performance. The weight initialization of the ensemble model is proportionate to the prediction accuracy of the individual models. These weights are assigned in a way that reduces the MSE of the total of weighted models, for each iteration. Equation (5.1) states the production of the ensemble model, where `w[i]` and `y[i]` denote the calculated weight and result of model `i`, respectively. Then the weights are tuned to obtain the minimum MSE for the ensemble model (`w[1]y[1] + w[2]y[2] + ... + w[j]y[j]`), which denotes the addition of bias and the variance of the models.

```
EM = \sum_{i = 1}^{n} (w_i . y_i) (5.1)
```

The bias is defined as the deviation between the expected prediction and the actual values as stated in (5.2). The variance and the total expected prediction error (MSE) are defined in (5.3) and (5.4), respectively.

```
Bias[m'(x)] = E[m'(x)] - m(x) (5.2)
Var[m'(x)] = E[m'(x)^2] - E[m'(x)]^2 (5.3)
E[m(x) - m'(x)^2] = (Bias[m'(x)])^2 + Var[m'(x)] = Var(\epsilon) (5.4)
```

Where:

*   `m'(x)`: output of a base model `m(x)`
*   `E[m'(x)]`: expected output error of model `m`
*   `m(x)`: actual class values
*   `Var(\epsilon)`: obvious error based on the noise variance

The ensemble learning process can be designed by changing the following elements.

*   Changing training data
