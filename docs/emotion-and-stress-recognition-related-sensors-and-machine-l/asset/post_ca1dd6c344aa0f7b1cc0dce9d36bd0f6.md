
Figure 7 shows in practice, the correction of two neuron outputs (top and bottom plot), representing two intensities of emotion outputs. The dotted red line represents the target (emotion detected from face); the blue line represents the corrected output (RTOR); and the dotted green line represents the raw output. The relative output outliers detection and removal are controlled by a batch length, which represents the amount of samples to be treated in reality.

# Emotion Intensity x Model Output + RTOR

![](img/601340ca744b738277eef45ff127492a_100_0.png)

Figure 7. Realistic outlier correction based on RTOR method. Note the corrected output (blue) and the raw output with outliers (green).

Before the metrics presentation to evaluate the emotion recognition, it is extremely important to know that this does not consider one single emotion as the final output, but the intensities of emotional ie, five emotions by time, output outputting each independent output neuron. This is because most human bodies do not usually feel one single emotion at a time, but of them, having different intensities and values. For this reason, the presented evaluation metrics over regression outputs over all output neurons measured separately.

Each output neuron was designed as a regression function and trained to output emotion intensities using the emotion detected from the face as the target. These outputs are measured to analyze how close the outputs are to the targets.

Considering the prior $R^2$, the Root Mean Squared Error (RMSE) or also called, Root Mean Squared Deviation (RMSD), computes the error distance between the estimated values $\hat{y}(n)$, as defined below.

> $RMSE = \sqrt{\frac{\sum_{n=1}^{N}(\hat{y}(n)-y(n))^2}{N}}$

The MAE represents the average of the absolute difference between the predicted values and observed value (prediction). In other words, it is a linear representation, which means that all the single differences are weighted equally in the average as shown in Equation (23):

> $MAE = \frac{1}{N}\sum_{n=1}^{N}|y(n)-\hat{y}(n)|$

# 5. Result Analysis

This work presented a multimodal fusion to recognize emotions from several physiological inputs based on the bio-reactions from beginners users flight simulator. It is an important contribution regarding aviation and a more general perspective of emotion relationship. It was proposed as one to contribute to emotion studies and in this work, the context of application was mainly aviation side of the scope of aviation accidents, which were caused by human failures.

Several tests were executed in this work to find recognition results for each pilot, the best model possible to estimate emotions felt by each pilot during the flight experiment. The cross-validation was the method used to aim the emotions recognition process for each pilot dataset obtained during each flight experiment. The recognition tasks were initially based on two dataset tests: tests without extraction (ie, raw data applied in ANN inputs, with any treatment or processing) and processed with feature extraction. It also considered different ANN architectures, amount of training iteration, amount of inputs hidden, and different flight datasets.

In all emotion recognition tests, the cross validation was applied to recognize the emotions felt by the pilot in a single flight according to the emotions already detected from another. The words was based on 12 datasets (N-1 flights), to recognize the emotions from one single flight. It is important considers, that the dataset having emotions values from the face (5 different emotions), was the reference of the ANN training. For this reason matters from the facial reader software, detecting wrongly several emotions, were not possible to be avoided; the consequence of these wrong matches is several errors under the regression models, outmpped from each output neuron.

# 5.1. Description of the Recognition Tests

The main proceeds by the processing and feature extraction, are shown in the test sequence below. It was based on feature selection and data type of treatment. For most of the tests, at least the data normalization and abrupt data correction were used (Table 2). In these tests, we considered all the features for each data, ie., 11 features from HR, 7 features from GSR and 72 features from EEG (9 x 8), including the best and worst results.

### Table 2. Description of each test execution according to test preprocessing, processing and feature extraction.

| Tests | Preprocessing: Detend | Preprocessing: Outliers | Feature Extraction: FE' | Feature Extraction: SV | Feature Extraction: CC' | Feature Extraction: $\varphi(v_i)$ | Optimization | HR | GSR | EEG |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Test 1 | x | x | | | sigmoid | 'sgd' | | | | |
| Test 2 | x | x | | | sigmoid | 'adam' | | | | |
| Test 3 | x | x | | | ReLU | 'adam' | | | | |
| Test 4 | x | x | | | sigmoid | 'sgd' | x | x | | |
| Test 5 | x | x | | | sigmoid | 'adam' | x | x | | |
| Test 6 | x | x | | | ReLU | 'sgd' | x | x | | |
| Test 7 | x | x | | | ReLU | 'adam' | | | | |
| Test 8 | x | x | | | sigmoid | 'sgd' | | | | |
| Test 9 | x | x | | | sigmoid | 'adam' | x | x | | |
| Test 10 | x | x | | | ReLU | 'sgd' | | | | |
| Test 11 | x | x | | | ReLU | 'adam' | | | | |
| Test 12 | x | x | | | sigmoid | 'sgd' | | | | |
| Test 13 | x | x | | | sigmoid | 'adam' | x | x | | |
| Test 14 | x | x | | | ReLU | 'sgd' | | | | |
| Test 15 | x | x | | | ReLU | 'adam' | | | | |
| Test 16 | x | x | | | sigmoid | 'sgd' | | | | |
| Test 17 | x | x | | | sigmoid | 'adam' | x | x | | |
| Test 18 | x | x | | | ReLU | 'sgd' | | | | |

CC': Column Centering—data centering for each data. FE': Feature Extraction—select all features for each data. Between 19 and 34, we considered the selection based on SVD (it means that, the features are selected in order of importance). There were six features from HR, four features from GSR and (5x8) features from EEG, as presented in Table 3.

### Table 3. Description of each feature test according to preprocessing, processing and selection.

| Tests | Detend | Outliers | Fe | SVD | CC | $\phi(v(n))$ | Optimization | HR | GSR | EEG |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Test 19 | x | x | | | ReLU | 'adam' | x | x | | |
| Test 20 | x | x | | | sigmoid | 'sgd' | x | x | | |
| Test 21 | x | x | | | sigmoid | 'adam' | x | x | | |
| Test 22 | x | x | | | ReLU | 'sgd' | x | x | | |
| Test 23 | x | x | | | ReLU | 'adam' | x | x | | |
| Test 24 | x | x | | | sigmoid | 'sgd' | x | x | | |
| Test 25 | x | x | | | sigmoid | 'adam' | x | x | | |
| Test 26 | x | x | | | ReLU | 'sgd' | x | x | | |
| Test 27 | | | | | ReLU | 'adam' | | | | |
| Test 28 | | | | | sigmoid | 'sgd' | | | | |
| Test 29 | | | | | sigmoid | 'adam' | | | | |
| Test 30 | | | | | ReLU | 'sgd' | | | | |
| Test 31 | | | | | ReLU | 'adam' | | | | |
| Test 32 | | | | | sigmoid | 'sgd' | | | | |
| Test 33 | | | | | sigmoid | 'adam' | | | | |
| Test 34 | | | | | ReLU | 'sgd' | | | | |

In tests of emotion recognition, no feature extra and preprocessing were considered; all raw data were directly processed in the ANN layer. The activation function used two different optimization algorithms: stochastic gradient ('sgd') and 'adam'. Table 4, presents an emotion recognition using a raw data approach and no feature extraction. Its results will recognize more undesirable and high execution time. The RMSE and MAE were used to compare the output models with the flight datasets.

### Table 4. Emotion recognition tests results 1 and 2. ANN with $6 \times 10^3$ train epochs and raw data (no feature-extraction). $\phi_2(v(m)) = Sigmoid, opt + 'sgd', n = 10 \times 10^2, N_a = 5$

| DS | Happy | Surprised | Scared | Match | Accuracy (%) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| | RMSE | MAE | RMSE | MAE | RMSE | MAE | RMSE | MAE | |
| R1 | 0.36 | 0.04 | 4.14 | 0.06 | 3.85 | 0.03 | 5.43 | 0.05 | 50.50 (184/367) |
| R2 | 0.43 | 0.06 | 5.72 | 0.09 | 3.95 | 0.04 | 5.84 | 0.09 | 82.13 (348/423) |
| R3 | 0.38 | 0.05 | 5.93 | 0.08 | 3.68 | 0.06 | 1.64 | 0.03 | 55.57 (225/408) |
| G1 | 0.68 | 0.09 | 7.45 | 0.13 | 7.14 | 0.11 | 5.58 | 0.07 | 23.96 (191/408) |
| G2 | 0.63 | 0.09 | 7.45 | 0.11 | 7.41 | 0.11 | 5.84 | 0.08 | 99.65 (428/435) |
| L1 | 0.51 | 0.20 | 6.28 | 0.06 | 5.14 | 0.04 | 6.18 | 0.02 | 22.49 (120/536) |
| L2 | 0.52 | 0.19 | 6.32 | 0.06 | 5.32 | 0.05 | 6.46 | 0.02 | 49.60 (246/496) |
| V1 | 0.38 | 0.08 | 3.86 | 0.04 | 4.80 | 0.04 | 4.79 | 0.07 | 15.68 (408/261) |
| V2 | 0.36 | 0.09 | 3.88 | 0.08 | 4.27 | 0.09 | 2.53 | 0.05 | 30.12 (615/204) |
| C1 | 0.47 | 0.17 | 7.54 | 0.12 | 5.00 | 0.05 | 1.64 | 0.02 | 92.47 (399/438) |
| C2 | 0.39 | 0.08 | 3.66 | 0.05 | 4.16 | 0.04 | 1.39 | 0.07 | 74.39 (439/457) |
| CLX | 0.45 | 0.16 | 1.00 | 0.04 | 1.73 | 0.07 | 1.47 | 0.06 | 0.54 | 0.02 | 0.00 (5/718) |
| CL3 | 0.27 | 0.04 | 3.07 | 0.05 | 5.05 | 0.07 | 5.29 | 0.09 | 3.76 | 0.05 | 15.57 (735/1722) |
