data from the time domain into the frequency domain. It helps in the extraction of relevant frequency-based features that can be transformed into images and processed further by CNNs for applications such as classification or EEG-based emotion recognition. EEG signals contain a range of frequencies that correspond to different types of brain activity. The EEG signal can be broken down into its frequency components using FFT. Better resolution of frequencies in the FFT is made possible by a larger window size (256 in this case). This implies that we will be able to record more precise data regarding the frequency components of our EEG signal. This may be crucial for precisely describing the broad range of content of signals from the EEG associated with various emotions. The amount that the windows overlap is determined by the step size (16 in this case). When windows overlap, brief variations in the EEG signal can be recorded that might otherwise go unnoticed. When the step size is 16, it indicates a large overlap between succeeding windows. Fast Fourier transform technique is used for extracting the features, decreasing them from (40,40,8064) to the final dimensions of (58560,70). This led to faster training and improved accuracy. Figure 4 represents the feature extraction technique.

# # Step 1: Signal decomposition using FFT

+   - Window Size = 256
+   - Sample Rate = 128
+   - Step Size = 16

# # Step 2: Use CNN filters are used to extract the deep features.

![](bbox=[0.5, 0.34, 0.78, 0.52])

**Figure 4.** Technique for feature extraction.

# ## 3.2.2 Emotion classification using CNN model

Convolutional Neural Network (CNN) models can be used for processing EEG signals to extract meaningful features and perform various tasks, such as classification or feature extraction. The CNN model's approach to emotion classification is shown in Figure 5. Our

![](bbox=[0.21, 0.65, 0.81, 0.9])

**Figure 5.** Proposed methodology for CNN model.