# 9

# NOISE FILTER WITH WAVELET ANALYSIS IN ARTIFICIAL
NEURAL NETWORKS (NOWANN) FOR FLOW TIME
SERIES PREDICTION

**Daniel A. Vázquez¹, Gerald A. Corzo Perez¹, and Dimitri P. Solomatine¹,²,³**

*¹ IHE Delft Institute for Water Education, Delft, The Netherlands*
*² Water Resources Section, Delft University of Technology, Delft, The Netherlands*
*³ Water Problems Institute of the Russian Academy of Sciences, Moscow, Russia*

A data preprocessing technique, known as Wavelet Analysis from the field of signal processing, was used to enhance an artificial neural network (ANN) model by addressing its primary drawbacks, notably nonstationarity and noise. Wavelet transforms are well-suited for handling time series contaminated by nonstationary traits and can extract relevant information at various time series frequencies. To improve the model’s performance, the ANN calibration weighting scheme assigns more weight to representative subseries and reduces the impact of noisy data on the rest. Noise filtering techniques (soft/hard single threshold) were applied to manipulate the subseries, further enhancing the model’s predictive skill. This approach resulted in the creation of a Noise Filter with Wavelet Analysis in Artificial Neural Network (NOWANN) scheme. To identify the best model, a model-based approach was used for input variable selection, k-fold cross-validation to determine the