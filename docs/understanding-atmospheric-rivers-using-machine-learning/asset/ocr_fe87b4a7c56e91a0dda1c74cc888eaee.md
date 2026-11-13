![](bbox=[0.13, 0.08, 0.87, 0.25])

Fig. 5.2 The configuration of the proposed convolutional autoencoder

from the ARs frames. and this information was then encoded into a representation within a latent space. The standard configuration of the model comprised: an encoder, a bottleneck, and a decoder [13, 26] (Fig. 5.2).

The input data was prepossessed in a sequence of 11 consecutive images to train the proposed DL model for predicting the 11th AR frame using sequences of 10 AR frames. The objective was to minimize the training loss and further enhance model performance by optimizing the architecture. Additionally, an L2 loss was used as a reconstruction loss. The input data was processed in batches of 10 frames during training. Despite observing an increase in training loss after 23 epochs, we continued training for 30 epochs to ensure comprehensive learning. During the training period, the model achieved a minimum mean squared error loss of 0.025, taking approximately 61 min to complete 30 epochs.

To verify the predictability of the model, commonly used metrics such as Structural Similarity Index (SSIM) and Peak Signal-to-Noise Ratio (PSNR) were used. PSNR assesses picture quality by comparing original and compressed images, while SSIM evaluates the similarity between predicted and original images. Reduced MSE and RMSE alongside elevated PSNR and SSIM indicate the improved predictive capabilities of the proposed model [33].

An illustrative example in Fig. 5.3 showcases the predictive capabilities of the model, depicting the reconstruction of the next from the testing dataset, compared to the original. The evaluation yielded on average RMSE and MSE scores of 0.1552 and 0.0247, along with SSIM and PSNR scores of 0.739 and 64.421, respectively, on the testing dataset [19]. These improved metric scores signify superior prediction performance compared to a related study by [2], focusing on predicting urban expansion using a Conv-LSTM model used similar metrics to evaluate the predictability of the model.

Modeling the intricate and dynamic spatiotemporal features of ARs poses significant challenges, especially in accurately predicting them using NWP models, particularly for extended lead times. This often leads to considerable inaccuracies, especially when forecasting the landfall locations [31]. The potential of sophisticated