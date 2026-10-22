
### 9.3.3. K-Fold Cross-Validation

The basic idea behind k-fold cross-validation is to reduce the bias associated with the chosen training set and the remaining samples. To do this, k subsets of equal size are selected (randomly or continuously). In each model, the partition consists of k-1 subsets for training and a single subset for validation. The validation set is rotated k times so that the k subsets are used exactly once; in consequence, k different models (folds) are built. For this study, the first 85% of the data was used for the 10-fold cross-validation, and the rest for testing. For each model, an early stopping criterion was used to avoid overfitting.

### 9.3.4. Wavelet Decompositions as an Input Preprocessor of an Artificial Neural Network

The a-trous wavelet transform algorithm was applied to the input data set; the resulting time series replaces the original. Figure 9.2 and Figure 9.3 show the traditional ANN and wavelet-ANN schematizations, respectively. In the latter, the simple procedure of decomposing signals already brings benefits to the model performance.

The ANN model assigns bigger weights to subseries with more relevant information for the modeling purpose. This is done by assigning different weights to each subcomponent during the training process.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_274_0.png)

Figure 9.2 Traditional ANN approach.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_275_0.png)

Figure 9.3 WANN approach. In order to create this model, we use the multiresolution representation of the time series signal: each input data set is decomposed in its smooth (average) version known as approximation (first series); and in its details, in this schematization, a second level decomposition with Haar wavelet as a mother wavelet (last two series) is shown.

### 9.3.5. Levels of Decompositions and ANN Structure as Decision Variables in an Optimization Routine

Since decomposition analysis can be performed using the multiresolution algorithm in an iterative process, it can be performed at any desired level of decomposition. However, for practical reasons, you can continue only until one detail value covers the entire sample. Furthermore, the modeler can select an appropriate number of levels according to the nature of the signal or a criterion such as entropy. If little knowledge is available to perform the above actions, this difficulty can be overcome by optimizing the number of decomposition levels and hidden nodes with an intensive search (see section 9.5.2). This is feasible due to the limited space of decision variables (levels of decomposition × hidden nodes).

### 9.3.6. Wavelet Decompositions as an Input Preprocessor of Other Data-Driven Models

Here the same procedure as explained above is followed, but now with different DDMs. To proceed with the simulations, it was considered convenient to make use of the data mining software called Weka, developed by the University of Waikato (http://www.cs.waikato.ac.nz/ml/weka/). With this software, a collection of machine learning techniques is available, which can be executed in Matlab, thanks to developments by Corzo Perez.

### 9.3.7. The Noise Filtering Process in Wavelets Analysis

An alternative option is to de-noise the signal. Once the decomposition of the signal is performed, it is possible to alter these resultant coefficients according to our needs. Several methods are recommended in literature such as Universal Threshold, Visu Shrink, Sure Shrink, Bayes Shrink, Normal Shrink, and so forth. For details, the reader can refer to Ruikar and Doye (2011) and Donoho and Johnstone (1994). In the present study, the threshold is found via optimization, and soft thresholding is applied for each decomposition level and again for each input series in the ANN model, so a number of (decomposition levels × ANN inputs) threshold coefficients were calculated.

Then the calculated thresholds can be treated as follows in the detail representation. In soft thresholding, all coefficients below a certain threshold are set to zero, and those whose magnitude are greater than the threshold are shrunk by that amount. This method recognizes that the coefficients contain both signal and noise, and attempts to isolate them.

$$W_i^{soft} = \begin{cases} 0 & |W_i| < \lambda \\ sign(W_i)(|W_i| - \lambda) & |W_i| > \lambda \end{cases} \quad (9.9)$$

In comparison, hard thresholding retains only the values above the threshold and is considered to correspond to the coherent part of the signal. The rest corresponds to the random or noisy part of the signal (Addison, 2010). Graphic illustrations of the filtering effect are shown in Figure 9.4.

$$W_i^{hard} = \begin{cases} 0 & |W_i| < \lambda \\ W_i & |W_i| > \lambda \end{cases} \quad (9.10)$$

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_277_0.png)

Figure 9.4 Soft and hard threshold for de-noising the signal source (http://nl.mathworks.com/help/wavelet/ref/wthresh.html).

Some authors (Okkan, 2012; Okkan & Serbes, 2013) affirmed that some subseries are ineffective and must be removed to improve the generalization capability of the model. On the contrary, Adamowski and Sun (2010) have used the complete subseries as inputs to the ANN model, stating that averaging or optimizing the selection of only certain subseries could generate undesired results. The latter stated that all subseries are equally important and contain some information about the original signal. For the present work, and according to the way ANN operates (by assigning different weights to each input series during the training process), it can be said that ANN by itself is selecting which subseries are more significant than others. In the case of doing it with the detail coefficients, to some extent, a noise elimination process is being carried out. For the present study, the statements made previously by the different authors are thought of as partial truths. Every subseries contains some important information about the signal and is relevant to the model (no subseries were discarded). However, many factors can introduce errors in our measurements (errors in the instruments, human error, etc.). Even after quality checks, there are still some errors in the data, so this noise can also be eliminated.

To illustrate how threshold de-noising works, it will be briefly introduced below. Let us start from the basis that the noise is present on fine scales (detailed subseries), contrary to the trends or the main body (coherent part) of a time series, which can be seen in the approximation subseries. The filtering is only done on the detailed subseries. The threshold limits were intentionally chosen as large, to illustrate how the signal transforms (see Fig. 9.5). In practice, and for the present study, these values are much smaller in magnitude; therefore, when reconstructing the signal (inverse wavelet transform), the resulting time series would not be so different from the original (let’s remember that this is obtained via optimization). This follows the key idea that it will not remove important information during the process.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_278_0.png)

Figure 9.5 De-noising process in the details of the signal.

Brief analysis:

Thresholds for the detail sub-series:

- Segment 1: If we look at the original signal along this segment [140, 260], the discharge increases in response to rain somewhere. Errors are more likely to occur during this period and will be of greater magnitude. Now it is time to define the threshold (high on purpose), where what is within this range will be interpreted as noise and eliminated.

- Segment 2: During low and zero flow rates, the noises will be lower and also reflected in the details, the threshold criterion will find little or no noise to eliminate.

### 9.3.8. Error Metrics

There is no one best error metric for evaluating model performance. Some are better suited for certain circumstances than others. In our case, it is considered important to capture peaks and high flows, so RMSE was used to penalize a large variance. Nevertheless, other error metrics are also calculated and evaluated and are listed below.

- 1. Root mean square error (RMSE): RMSE is the standard deviation of the residual errors (the difference between prediction and observation).
