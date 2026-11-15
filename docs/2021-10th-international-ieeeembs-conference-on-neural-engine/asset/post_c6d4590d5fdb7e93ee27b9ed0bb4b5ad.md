
- 4. Standard Deviation
- 5. Zero Crossings: Number of times the signal crosses zero
- 6. Slope sign changes: Number of times that the slope of the EMG signal changes sign
- 7. Root Mean Square
- 8. Log detector: \(\frac{1}{e^N} \sum_{i=1}^N log(|x_i|)\) where \(x_i\) is the EMG amplitude at time bin i.
- 9. Frequency spectrums in each frequency bin between 7 and 12 Hz, 12-30, 30-50, 50-100, 100-150 and 150-400 Hz from FFT results.

### C. Hyper-parameter optimization

There is a high number of hyper-parameters to optimize for each paradigm. Among those, we optimized a set of parameters based on the first session of the first subject due to computational power required to perform a hyper-parameter search for each recording. The hypothesis being that the quantity of information is relatively the same for each recording and therefore, the complexity of the dataset is relatively the same, meaning that the best model architecture for one recording is a good model for the other recordings.

For the two DL approaches (RAW and FFT), we started from a VGG-like architecture [24] and optimized the shape of the network: the number of convolutional layers before each average pooling layer (up to 3), the number of pooling layer (up to 5) and the number of filters for each convolutional layer (16, 32, 64, 128). A batch-normalization follows each convolutional layer. Then, the number of fully connected layers (up to two layers) and the number of nodes for each layer (16, 32, 64) were also tuned. Except from the architectural parameter, the drop rate was also optimized (0, 0.2, 0.5) as well as the L2 regularization rate (0, 1e-3, 0.1), the learning rate (0.1, 0.01, 0.001), the convolutional filter size in x dimension, in y dimension (1, 3, 5) and the padding strategy for image border (with or without). The CNN networks were optimized with a batch gradient descent with a batch size of 32 samples, with 50 epochs, a step decay with a drop of \(\frac{1}{2}\) every 10 epochs and an early stopping if the validation loss did not decreased for more than 13 epochs.

For the STD approach, the model was a multi-layer perceptron (MLP) and therefore has less parameters to tune. However, the feature selection is an important process in order not to overfit the data. Therefore the hyper-parameters were the selection or not of a feature, the number of fully connected layers (up to 3 hidden layers), the number of node per layer (16, 32, 64, 128, 256), the drop rate (0, 0.2, 0.5), the L1 and L2 regularization terms (0, 1e-3, 0.1), the learning rate (0.1, 0.01, 0.001) and the optimizer (Adam, RMSprop, batch gradient descent). The MLP was optimized with a batch gradient descent with a batch size of 16 samples, with 100 epochs and similarly to the CNN, a step decay with a drop of \(\frac{1}{6}\) every 10 epochs with an early stopping if the validation loss did not decreased for more than 13 epochs. All the models were trained with a mean squared error loss (MSE).

Due to the high dimensionality of the hyper-parameter space, a grid search was impossible to perform in a reasonable amount of time. Therefore, we opted for a genetic algorithm (GA) parameter optimization approach [25]. The problem was formulated as a genetic representation of the solution domain where each hyper-parameter was encoded as a gene on a chromosome that could take one of the discrete possible values. The fitness function was encoded as the validation loss of the trained model to evaluate the solution domain. A population of 20 random individual was created and trained for 200 generation using a fitness proportionate (or roulette wheel) offspring selection method. The rate of mutation was set to 0.1 and the selection rate to 0.6.

### D. Performance evaluation of each subject

After hyper-parameter optimization on one session, the same pre-processing steps will be applied on all the available recordings in order to train a model on each recording available. For each recording, the model was trained ten times and the model with the lowest validation loss is kept. This step was necessary to reduce the chances of having the model stuck in a local minimum. Then the best model was evaluated on the testing set.

![](img/d2423e8420ae194bb21d641517122d0f_2_0.png)

## III. RESULTS

The best model for the three paradigms obtained with the genetic algorithms was with RAW condition and had a validation loss of 5.34 and a training loss of 2.20. The model architecture is shown in Figure 3. It is trained with a drop rate of 50%, without L2 normalization, a learning rate of 0.01 and the shape of the convolutional mask is (3, 1) with 0 padding to keep the same output dimension.

![](img/d2423e8420ae194bb21d641517122d0f_2_1.png)

For the FFT condition, the minimum validation loss was 6.41 with a training loss of 4.82 and for STD, the minimum validation loss was 9.14 with a training loss of 9.43. For the STD model, features from all channels were extracted and the final model used all the features except the slope sign change for a total of 46 features.

The average test loss, meaning the performance on unseen data, per condition is shown in Figure 4 for the 11 sessions. The STD test loss is significantly different from the two other conditions (t-test, p < 0.05) but the FFT and RAW conditions are not different.

The test loss for each subject is shown in Figure 5, each subject recorded 3 sessions except S2 who did only two calibration sessions. An example of the predicted angles versus the target labels is shown in Figure 6 for the RAW condition on the test set of subject S1. It consist of one repetition of each movement and lasts for 56 seconds. The angles correspond to the sequence: Index Flexion, Middle Finger Flexion, Ring Finger Flexion, Ulnar Grasp, Open, Tridigital Grasp, Power Grasp, Thumb opposition and Thumb opposition + flexion. It corresponds to a loss of 7.36. The baseline loss corresponding to a model outputting only the mean value of the targets was ~19.

![](img/d2423e8420ae194bb21d641517122d0f_3_0.png)

## IV. DISCUSSION

This work aimed at quantifying the performance of DL compared to a STD feature extraction approach. The results showed that both DL conditions (RAW and FFT) are performing better than STD. However, it is not possible to conclude on which approach between RAW and FFT is best suited for single finger proportional control. For simplicity, one could argue to keep the RAW condition to avoid computing the FFT and therefore reduce the computational time for real time applications. A possible optimization is the combination of time-frequency information merging the RAW and FFT approaches, increasing the amount of information that inputs the model.

However, the amount of data per session in these experiments is relatively low (3 repetitions for the train set) which create uncertainty during the training of the different models and high differences between the validation and testing losses.

![](img/d2423e8420ae194bb21d641517122d0f_3_1.png)

Another limitation to take into account is that the dataset comprised only fully open and closed positions held for several seconds without any real “rest/middle” position. or other arbitrary angles. Indeed, when the users follow movements shown on a screen, there are intrinsic delays due to their reaction time that create jitter between expected kinematics and actual finger positions. In the case of single finger proportional control, exact finger position is paramount. Therefore, obtaining synchronized middle values is challenging and may be obtained using a kinematic glove for example.

Deep networks like CNNs need a huge amount of data to reach their maximum accuracy (e.g. ImageNet Challenge [26]) which means that increasing the amount of data could play a significant role in the performances obtained. However, a subject cannot reasonably record tens of hours of data in a single sitting. One possible solution is to leverage the information of several subjects to pre-train a general network that could be fine-tuned for the subject’s specific EMG activity. Several authors [13], [27], [28] investigated this approach and showed promising results for grasp classification, this strategy could be applied to single finger proportional control.

## V. CONCLUSION

To conclude, we showed that deep learning is a promising approach for proportional EMG decoding. Due to the placement of the electrodes on the forearm, these results obtained on healthy subjects could apply for trans-radial amputees or amputations that are more distal. On the decoding side, we cannot conclude on the best DL approach between raw signals or spectrogram as input since both outperformed the standard state-of-the-art approach but were not statistically different.

For future developments, increasing the amount of data should be the main objective. Leveraging open access EMG databases like NinaPro [29], [30] to improve performances of DL for single-finger regression. The feasibility of this DL approach in real time to control a real prosthesis or any microprocessor should also be addressed due to the high computational cost of the models used.
