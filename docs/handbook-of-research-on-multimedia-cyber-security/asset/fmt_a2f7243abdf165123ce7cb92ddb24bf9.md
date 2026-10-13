
# A Scaled Conjugate Gradient (SCG) Backpropagation learning algorithm was used in the artificial neural network learning process. This algorithm provides the best performance and is fast convergence over other algorithms such as Levenberg Marquardt algorithm which consumes computing resources greedily (Matlab guide (2019)). In our work, we have tested different learning algorithms, however, the SCG backpropagation algorithm results were the best in performance and speed considering our experiment specifications and conditions.

We used ready built ANN Modeling tool presented by MATLAB MathWorks. We used a PC laptop equipped with Intel core i5 processor, 6GB of RAM and Nvidia Geforce 520m GPU with MATLAB 2017a version. It saves a lot of time implementing ANN, training and deploying. Neural Network toolbox in MATLAB presents an application with a graphical user interface in which every user can provide input samples and desired output samples easily by following some sequential steps to provide inputs, outputs, learning algorithm, and number of hidden neurons and also an activation function that is needed for activating every single neuron in the neural network.

## Support Vector Machine

MATLAB MathWorks also provides a graphical user interface application to classify data using different types of classifiers. Here, we used SVM classifiers with different kernels to find the best one for our application (Matlab guide, 2019). The same data samples which we used before in ANN classifier are used here. The types of SVMs were: linear, Quadratic, Cubic, Fine Gaussian, Medium Gaussian and Coarse Gaussian. The results of the classification and identification will be discussed later.

## Session-Level Model Feature Selection Results

In this section, we introduce the results of searching user-feature consistency and feature-discrimination applied to the high-level session features model (see Table 6). We can here also use any choosing criteria to select the best features. In this features model, we considered the previously mentioned method in section 4.4 of features selection. We use all the features but we assign each a weight number to amplify the effect of the best features and damp the effect of the worst features in the classification stage.

In session-level model, the best features were related to the user behavior in multi-touch strokes mainly Zoom-in and Zoom-out timing. Also, flicking speed was the best feature. This behavior may be due to the different hand geometry between the different users in our experiment. When we used principal component analysis in MATLAB, these 35 features were reduced to 21 features; in other words, PCA algorithms transferred data of 35 dimensions to new 21 dimensions or spaces to reduce complexity and remove redundant information in these features.

### Table 6. Session-level consistency discrimination values

| Feature | Sum of Variances (Consistency) | Variance (Discrimination) | Normalized Sum of Variances | Normalized Variance |
| --- | --- | --- | --- | --- |
| AverageTapPressure | 0.935454918 | 0.0317629 | 0 | 0.370576219 |
| RotationAvragePressureAtFocalPoint | 0.941972536 | 0.030645399 | 0.016246158 | 0.352349274 |
| ScrllftAverageVelocityAtLast3Points | 0.970368406 | 0.022546893 | 0.087027202 | 0.220258995 |
| ScrlupAverageVelocityAtLast3Points | 0.972349357 | 0.018102023 | 0.091965025 | 0.147761164 |
| ScrllftAverageDistance | 0.976429909 | 0.03102865 | 0.102136424 | 0.35860027 |
| ScrlupAverageDirection | 0.9782688 | 0.036290528 | 0.106720141 | 0.44442387 |
| ZinDistanceBetweenLiftingPoints | 0.982755983 | 0.03430992 | 0.11790513 | 0.412119261 |
| ScrllftAverageVelocity | 0.988857071 | 0.032667095 | 0.133113024 | 0.385324046 |
| TapTime | 1.000697871 | 0.037244976 | 0.162628027 | 0.459991346 |
| FlickingAverageDirection | 1.007975099 | 0.023170917 | 0.180767629 | 0.230437107 |
| ScrlupAverageVelocity | 1.008596165 | 0.028823075 | 0.182315731 | 0.322626349 |
| ScrlrghtAverageDistance | 1.012578397 | 0.038585207 | 0.192242053 | 0.481851117 |
| ScrldwnAverageVelocity | 1.018875299 | 0.009639019 | 0.207938043 | 0.009725758 |
| ScrldwnAverageDirection | 1.021380252 | 0.016335433 | 0.214182021 | 0.118947286 |
| ZoutZoomingTime | 1.024730234 | 0.043670717 | 0.222532363 | 0.564798075 |
| ZinZoomingTime | 1.03930496 | 0.031730664 | 0.258862093 | 0.370050435 |
| ScrlrghtAverageDirection | 1.04155984 | 0.009042729 | 0.264482726 | 0 |
| ZinDistanceBetweenLandingPoints | 1.050980586 | 0.029852361 | 0.287965375 | 0.339414467 |
| ScrlrghtAverageVelocity | 1.052226046 | 0.039409691 | 0.291069874 | 0.495298823 |
| ScrlupAverageDistance | 1.055615215 | 0.027538978 | 0.299517896 | 0.301682149 |
| LongTapAveragePressure | 1.056163214 | 0.024239621 | 0.300883867 | 0.247868151 |
| RotationAverageRadius | 1.06462446 | 0.033319379 | 0.321974815 | 0.395963092 |
| ScrldwnAverageDistance | 1.079791013 | 0.021464011 | 0.359779765 | 0.202596702 |
| ScrldwnAverageVelocityAtLast3Points | 1.099246635 | 0.020324903 | 0.408275875 | 0.184017338 |
| ScrlrghtAverageVelocityAtLast3Points | 1.104491914 | 0.026062204 | 0.421350534 | 0.2775953 |
| ZinTwoLeftingLatency | 1.11474821 | 0.021940877 | 0.446915919 | 0.210374601 |
| ZoutDistanceBetweenLiftingPoints | 1.122617174 | 0.035174115 | 0.466530513 | 0.426214671 |
| TapMaxDistance | 1.125634365 | 0.043033319 | 0.474051323 | 0.554401827 |
| ZoutDistanceBetweenLandingPoints | 1.142329203 | 0.045892838 | 0.515665757 | 0.601041869 |
| ScrllftAverageDirection | 1.184228311 | 0.070353115 | 0.620105684 | 1 |
| AverageTapArea | 1.199902944 | 0.054531073 | 0.659177101 | 0.741935371 |
| ZoutTwoLandingLatency | 1.233478428 | 0.013970284 | 0.742869124 | 0.080370641 |
| FlickingAverageVelocity | 1.240893604 | 0.027310432 | 0.761352583 | 0.297954461 |
| ZoutTwoLeftingLatency | 1.253710473 | 0.052696271 | 0.793300586 | 0.712008925 |
| ZinTwoLandingLatency | 1.336633942 | 0.048222567 | 1 | 0.639040798 |

## Session-Level Classification

An artificial neural network classifier was also employed to classify the input samples of all the touch sessions. The same ANN construction shown in Figure 6 was used with 35 input features instead of 27 input features. The input samples were divided randomly into:

*   65% for training.
*   15% for validation
*   20% for testing.

We have divided the data samples in this manner because we have a few number of samples in the session level model.

# PERFORMANCE EVALUATION AND RESULTS DISCUSSION

In this section, we introduce the results of our experiments using both classification and identification algorithms; ANN and SVM with both features selection methods: weighted features using discrimination and consistency values and principal component analysis (PCA) method.

## Artificial Neural Network

After performing 10 training sessions in the stroke-level features model, we have obtained 14% - 16% misclassification error of training samples and 25% - 30% misclassification error of testing samples, while in the session-level features model, we have obtained 0% misclassification error of training samples and 16% - 20% misclassification error of testing samples. Using this session-level features model, we got more efficient classifier than we had in the stroke-level features model.

Figure 7 shows the error histogram of the classifier training of session-level model. This figure shows the number of samples that result in a specific error value.

### Figure 7. Histogram of Session-Level Classification Error

![Figure978-1-7998-2701-6.ch013.f07](i/ch013.f07.png)
