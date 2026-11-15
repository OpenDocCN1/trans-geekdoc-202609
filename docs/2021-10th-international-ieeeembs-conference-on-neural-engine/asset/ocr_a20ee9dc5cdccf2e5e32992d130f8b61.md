+   4. Standard Deviation
+   5. Zero Crossings: Number of times the signal crosses zero
+   6. Slope sign changes: Number of time that the slope of the EMG signal changes sign
+   7. Root Mean Square
+   8. Log detector: \(\frac{1}{e^N} \sum_{i=1}^N log(|x_i|)\) where \(x_i\) is the EMG amplitude at time bin i.
+   9. Frequency spectrums in each frequency bin between 7 and 12 Hz, 12-30, 30-50, 50-100, 100-150 and 150-400 Hz from FFT results.

# C. Hyper-parameter optimization

There is a high number of hyper-parameters to optimize for each paradigm. Among those, we optimized a set of parameters based on the first session of the first subject due to computational power required to perform a hyper-parameter search for each recording. The hypothesis being that the quantity of information is relatively the same for each recording and therefore, the complexity of the dataset is relatively the same, meaning that the best model architecture for one recording is a good model for the other recordings.

For the two DL approaches (RAW and FFT), we started from a VGG-like architecture [24] and optimized the shape of the network: the number of convolutional layers before each average pooling layer (up to 3), the number of pooling layer (up to 5) and the number of filters for each convolutional layer (16, 32, 64, 128). A batch-normalization follows each convolutional layer. Then, the number of fully connected layers (up to two layers) and the number of nodes for each layer (16, 32, 64) were also tuned. Except from the architectural parameter, the drop rate was also optimized (0, 0.2, 0.5) as well as the L2 regularization rate (0, 1e-3, 0.1), the learning rate (0.1, 0.01, 0.001), the convolutional filter size in x dimension, in y dimension (1, 3, 5) and the padding strategy for image border (with or without). The CNN networks were optimized with a batch gradient descent with a batch size of 32 samples, with 50 epochs, a step decay with a drop of \(\frac{1}{2}\) every 10 epochs and an early stopping if the validation loss did not decreased for more than 13 epochs.

For the STD approach, the model was a multi-layer perceptron (MLP) and therefore has less parameters to tune. However, the feature selection is an important process in order not to overfit the data. Therefore the hyper-parameters were the selection or not of a feature, the number of fully connected layers (up to 3 hidden layers), the number of node per layer (16, 32, 64, 128, 256), the drop rate (0, 0.2, 0.5), the L1 and L2 regularization terms (0, 1e-3, 0.1), the learning rate (0.1, 0.01, 0.001) and the optimizer (Adam, RMSprop, batch gradient descent). The MLP was optimized with a batch gradient descent with a batch size of 16 samples, with 100 epochs and similarly to the CNN, a step decay with a drop of \(\frac{1}{6}\) every 10 epochs with an early stopping if the validation loss did not decreased for more than 13 epochs. All the models were trained with a mean squared error loss (MSE).

Due to the high dimensionality of the hyper-parameter space, a grid search was impossible to perform in a reasonable amount of time. Therefore, we opted for a genetic algorithm (GA) parameter optimization approach [25]. The problem was formulated as a genetic representation of the solution domain

where each hyper-parameter was encoded as a gene on a chromosome that could take one of the discrete possible values. The fitness function was encoded as the validation loss of the trained model to evaluate the solution domain. A population of 20 random individual was created and trained for 200 generation using a fitness proportionate (or roulette wheel) offspring selection method. The rate of mutation was set to 0.1 and the selection rate to 0.6.

# D. Performance evaluation of each subject

After hyper-parameter optimization on one session, the same pre-processing steps will be applied on all the available recordings in order to train a model on each recording available. For each recording, the model was trained ten times and the model with the lowest validation loss is kept. This step was necessary to reduce the chances of having the model stuck in a local minimum. Then the best model was evaluated on the testing set.

![](bbox=[0.51, 0.315, 0.91, 0.465])

# III. RESULTS

The best model for the three paradigms obtained with the genetic algorithms was with RAW condition and had a validation loss of 5.34 and a training loss of 2.20. The model architecture is shown in Figure 3. It is strained with a drop rate of 50%, without L2 normalization, a learning rate of 0.01 and the shape of the convolutional mask is (3, 1) with 0 padding to keep the same output dimension.

![](bbox=[0.51, 0.6, 0.91, 0.92])