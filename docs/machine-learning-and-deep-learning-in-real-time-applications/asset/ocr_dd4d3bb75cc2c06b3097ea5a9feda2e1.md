# Text Separation From Document Images

for transfer learning. As the architecture of both models is standard, it is pre-designed with different layers.

3. Use loss function as Binary Cross-entropy.
$binaryCE(p, \hat{p}) = -log(\hat{p})+(1-p)\log(1-\hat{p})$

4. Set the hyperparameters:

+   * Minimum learning rate as 1e-4
* Patience parameter as 3
* Epochs equal to 100
* Batch size is 32
* Dropout as regularization

5. Retrain and compile the models by using Adam as optimizer (learning rate = 0.001) and metrics using accuracy, precision, recall, and F1 measure.

6. Save the model.

7. Monitor the validation loss, the training loss, and the accuracy of the models.

8. Evaluate the model using the test dataset

9. Plot the training and test accuracies with loss.

End

# Results and Discussions

The results on the test dataset obtained after training the base deep learning models (i. U-Net and ResU-Net) are discussed in this section. Semantic segmentation of Devanagari document images using the second method of transfer learning (i.e., fine-tuning) is performed and discussed. Fine-tuning of the whole model is required for the dataset as the model is different from the Devanagari dataset. Fine-tuning the models, which is a model of transfer learning, takes less time than learning the network from scratch. U-Net and ResU-Net are trained using the training dataset and tested on images other than the training dataset. The result shown in the chart is on the test dataset. Training any deep learning model requires a lot of time, while testing is completed in a very short amount of time. The encoder of the model learns the features and parameters of the network, locates the features learned by the encoder to generate the output as required. The lower layer of the encoder learns the low-level features like edge detection. As we go deeper into the network, the layers learn the high-level features like localization, etc.

# a. U-Net Results

Figures 14 and 15 demonstrate the results of the U-Net after fine-tuning the model to extract text from the Devanagari document images. Figure 1 (a) is the test input image and Figure 15 (b) shows text-segmented output image. Figures 14 (a), (b) and Figure 15 (a) show the U-Net's feature map visualization at the intermediate layers of the model. Figure 14 (a) is the output of the feature map of the model at the starting layer which indicates the low-level features of the input image. Figure 14 (b) and Figure 15 (a) represent the mid-level and high-level features of the input image respectively.